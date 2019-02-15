# JS-Regular-expression-awesome
:page_facing_up:我收藏的、开发中用过的正则表达式，欢迎补充

## 最新
- 匹配2018-10-10格式的日期：`^[1-9]\d{3}-([1-9]|1[0-2])-([1-9]|[1-2]\d|3[01])$`
- 验证文件扩展名:`^.*?\.(html|css|jpg)$`

## 密码验证类
- 6-16位字符，区分大小写（不能是9位以下的纯数字，不含空格）:`^(?!\d{6,8}$)(?! )(?=.*[a-z])(?=.*[0-9])[a-zA-Z0-9_]{6,16}$`
- 6-16位字符，区分大小写（不能是9位以下的纯数字，不含空格），必须包含大写字母:`^(?!\d{6,8}$)(?! )(?=.*[A-Z])(?=.*[a-z])(?=.*[0-9])[a-zA-Z0-9_]{6,16}$`
- 密码不能为纯数字或字母，不少于6位:`^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z]{6,}$`

## 号码验证类
- 验证微信号:`^[a-zA-Z]{1}[-_a-zA-Z0-9]{5,19}$`
- 腾讯QQ号码:`[1-9][0-9]{4,}`
- 国内电话号码:`\d{3}-\d{8}|\d{4}-\{7,8}`
- 带中划线的手机号码:`^[+]{0,1}(d){1,3}[ ]?([-]?((d)|[ ]){1,12})+$`
- 普通手机号码:`^1[34578]\d{9}$`
- 普通电话、传真号码：可以“+”开头，除数字外，可含有“-”:`^[+]{0,1}(d){1,3}[ ]?([-]?((d)|[ ]){1,12})+$`
- 18位身份证号码:`^(\d{6})(\d{4})(\d{2})(\d{2})(\d{3})([0-9]|X|x)$`
- 中国邮政编码:`[1-9]\d{5}(?!\d)`

## 地址类
- IP地址：`(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d).(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d).(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d).(25[0-5]|2[0-4]\d|[0-1]\d{2}|[1-9]?\d)`
- URL:`[a-zA-z]+://[^\s]*`
- Email地址:`[\w!#$%&'*+/=?^_`{|}~-]+(?:\.[\w!#$%&'*+/=?^_`{|}~-]+)*@(?:[\w](?:[\w-]*[\w])?\.)+[\w](?:[\w-]*[\w])?`



## 其他
**手机号码中间四位用*代替**
```js
function encryptPhone(val){
    if(!val) return;
    return val.replace(/^(\d{3})(\d{4})(\d+)/, '$1****$3')
}

encryptPhone('13173786224'); // 131****6224
```

**格式化金额**
```js
var money = 1003450.89;
console.log(money.toString().replace(/(?=\B(?:\d{3})+\b)(\d{3}(?:\.\d+$)?)/g,',$1'));
// 1,003,450.89
```

**JS替换字符串中的空格**
```js
var reg = /([^\s])\s+([^\s\b])/g;
var str = " 中国  北京   朝阳区  df "; 
str = str.replace(reg, "$1%$2")
```

**不允许输入如下字符: (像 !@#$%^&* 等)**
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

## tips
匹配中文字符：`[\u4e00-\u9fa5]`

匹配数字类型
```js
//匹配正整数
^[1-9]\d*$
//匹配负数
^-[1-9]\d*$
//正数
^-?[1-9]\d*$
//匹配非负正数（正整数 + 0）
^[1-9]\d*|0$
//匹配非正负数（负整数 + 0）
^-[1-9]\d*|0$
//匹配正浮点数
^[1-9]\d*\.\d*|0\.\d*[1-9]\d*$
//匹配负浮点数
^-[1-9]\d*\.\d*|-0\.\d*[1-9]\d*$
```
