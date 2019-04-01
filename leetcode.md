

# leetcode题解（JS）

```js
//#7 
//整数反转 tips： 去0，支持负数，溢出2^32 返回0
var reverse = function(x) {
    let [abs,pow] = [Math.abs,Math.pow];
    let res = String(abs(x % 10 === 0 ? x/=10 : x)).split('').reverse().join('');
    x < 0 ? res*=-1 : +res;
    return (res > pow(-2,31) && res < pow(2,31) -1) ? res:  0;
}
```

```javascript
//#9
//回文数
//1. 转字符串
var isPalindrome = function(x) {
    let num = x+ '';
    const y = num.split('').reverse().join('');
    if (num === y) {
        return true;
    } else {
        return false;
    }
};
//2. 算法
var isPalindrome = function(x) {
    if (x < 0 || x % 10 === 0 && x != 0) return false;
    let n = 0;
    while (x > n) {
        n = n * 10 + x % 10;
        x = parseInt(x / 10);
    }
    return x == n || x == parseInt(n / 10);
};
```

```javascript
//#9
//罗马数字转整数
// 1. obj + reduce
var romonToInt = function (x) {
    let data = {"M":1000, "D":500, "C":100, "L":50, "X":10, "V":5, "I":1};
    return s.split('').reduce((total,cur,i,arr) => {
        //这里 total + ('''''')中的('''''') 表现为：cur+= ('''''')
        return total + (data[cur] < data[arr[i+1]] ? -data[cur] : data[cur]);
    }, 0);
}
// 2. map + 循环
var romanToInt = function (s) {
    let num = 0
    const dataMap = new Map([
        ['I', 1],
        ['V', 5],
        ['X', 10],
        ['L', 50],
        ['C', 100],
        ['D', 500],
        ['M', 1000],
    ])
    for (let i = 0; i < s.length; i++) {
        if (s[i + 1] && dataMap.get(s[i]) < dataMap.get(s[i + 1])) {
            num = num - dataMap.get(s[i])
        } else {
            num = num + dataMap.get(s[i])
        }
    }
    return num
};
```

