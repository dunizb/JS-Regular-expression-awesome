# JS-Regular-expression-awesome
:page_facing_up:我收藏的正则表达式大全，欢迎补充

## 验证微信号
微信账号仅支持6-20个字母、数字、下划线或减号，以字母开头
```js
/^[a-zA-Z]{1}[-_a-zA-Z0-9]{5,19}$/.test(value)
```

## JS替换字符串中的空格
```js
var reg = /([^\s])\s+([^\s\b])/g;
var str = " 中国  北京   朝阳区  df "; 
str = str.replace(reg, "$1%$2")
```

## 检查用户名：只能输入1-30个以字母开头的字串
```js
function isPasswd(s) { 
    var patrn=/^(w){6,20}$/; 
    if (!patrn.exec(s)) return false 
    return true 
}
```

## 检查密码：只能输入6-20个字母、数字、下划线 
```js
function isPasswd(s) { 
    var patrn=/^(w){6,20}$/; 
    if (!patrn.exec(s)) return false 
    return true 
} 
```

## 检查手机号码：必须以数字开头，除数字外，可含有“-”
```js
function isMobil(s) { 
    var patrn=/^[+]{0,1}(d){1,3}[ ]?([-]?((d)|[ ]){1,12})+$/;
    if (!patrn.exec(s)) return false
    return true
} 
if(mobilephone!=""&&!/^1[358][0-9]{9}$/.test(mobilephone)){
     alert("移动号码是11个数字");
     return false;
}
//判断是否手机号
function isPhoneNumber(value){
    var flag=false;    
    if(/^(133|153|18[0169])+[0-9]{8}$/.test(value)){
        flag=true;
    }
    return flag;
}

function checkPhone(){ 
    var phone = document.getElementById('phone').value;
    if(!(/^1[34578]\d{9}$/.test(phone))){ 
        alert("手机号码有误，请重填");  
        return false; 
    } 
}
```

## 校验普通电话、传真号码：可以“+”开头，除数字外，可含有“-” 
```js
function isTel(s) { 
    //var patrn=/^[+]{0,1}(d){1,3}[ ]?([-]?(d){1,12})+$/;
    var patrn=/^[+]{0,1}(d){1,3}[ ]?([-]?((d)|[ ]){1,12})+$/;
    if (!patrn.exec(s)) return false
    return true
}
```

## 只能输入英文、数字和下划线
```js
/^[A-Za-z0-9_]+$/
```

## 只能输入数字、判断字符串是不是纯数字
```js
if(isNaN(parentId.val()) || !/^\d+$/.test(parentId.val())){
     msg += "上一级ID只能输入数字!";
     parentId.focus();
}
//判断字符串是否是纯数字
function isAllNumber(value){
    var flag=false;
    if(/^\d+$/.test(value) == true){
        flag=true;
    }
    return flag;
}
```

## 检查邮箱、判断是否是邮箱
```js
function isEmail(value){
    var flag=false;    
    if(/^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/.test(value)){
        flag=true;
        
    }
    return flag;
}
```

## 检查身份证
```js
if(!/^[0-9]{6}[1,2][0-9]{3}[0-1][0-9][0-3][0-9]{4}[0-9|x]$/.test(phoneOwnerCard)){
     alert("请输入合法的18位身份证号码");
     return false;
}
```

## 检查邮编
```js
function isPostalCode(s) { 
    //var patrn=/^[a-zA-Z0-9]{3,12}$/; 
    var patrn=/^[a-zA-Z0-9 ]{3,12}$/; 
    if (!patrn.exec(s)) return false 
    return true 
} 
if(zipcode.length>0&&!/^[0-9]{6}$/.test(zipcode)){
    alert("邮政编码是6个数字");
    return false;
}
```

## 检查是否是IP地址
```js
function isIP(s) { 
    var patrn=/^[0-9.]{1,20}$/; 
    if (!patrn.exec(s)) return false 
    return true 
} 
```

## 不允许输入如下字符: (像 !@#$%^&* 等)
```js
var userName = $("#userRegistName").val(); 
var first = userName.charCodeAt(0); 
function CheckUserNameFormat(){
    if ((first>=65 && first <= 90)||(first>=97 && first <=122)){
    var pattern =/^[A-Za-z0-9_]+$/;  //首字母必须是A-Z或者a-z
    if(pattern.test(userName)){ 
         ......
    }
} 
```
