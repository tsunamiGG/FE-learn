# css垂直居中

```html
<div class="box">
        <span>垂直居中</span>
</div>
```

**方法1：table-cell**

```css
.box{
    display: table-cell;
    vertical-align: middle;
    text-align: center;        
}
```

**方法2：display:flex**

```css
.box{
    display: flex;
    justify-content:center;
    align-items:Center;
}
```

**方法3：绝对定位和0**

```css
.box{
    position:relative;
}
.box span{
  width: 50%; 
  height: 50%;
  overflow: auto; 
  margin: auto; 
  position: absolute; 
  top: 0; left: 0; bottom: 0; right: 0; 
}
```

**方法4：translate**

```css
.box span{
            position: absolute;
            top:50%;
            left:50%;
            transform:translate(-50%,-50%);
        }
```

常用2，4

