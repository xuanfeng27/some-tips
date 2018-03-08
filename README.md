# some-tips

```
function foo(x) {
	x.push( 4 );
	x; // [1,2,3,4]

	// later
	x.length = 0; // empty existing array in-place
	x.push( 4, 5, 6, 7 );
	x; // [4,5,6,7]
}

var a = [1,2,3];

foo( a );

a; // [4,5,6,7]  not  [1,2,3,4]
```
```
function foo() {
	var arr = Array.prototype.slice.call( arguments );//var arr = Array.from( arguments );
	arr.push( "bam" );
	console.log( arr );
}
foo( "bar", "baz" ); // ["bar","baz","bam"]
```
### number
```
if (!Number.isNaN) {
	Number.isNaN = function(n) {
		return (
			typeof n === "number" &&
			window.isNaN( n )
		);
	};
}

if (!Number.isNaN) {
	Number.isNaN = function(n) {
		return n !== n;
	};
}


var a = 2 / "foo";
var b = "foo";
```
#### note
```
inline-block
<div style="background-color:green;font-size:0;-webkit-text-size-adjust:none;">

        <div style="width:40px;height:30px;background-color:red;display:inline-block;">

        </div>

        <div style="width:40px;height:30px;background-color:red;display:inline-block;">

        </div>

        <div style="width:40px;height:30px;background-color:red;display:inline-block;">

</div>


display:inline-block;
*display:inline;
*zoom:1;


1. 删除git的文件跟踪缓存，然后添加.gitignore规则：
git rm --cached FILENAME


1 npm install -g cnpm --registry=https://registry.npm.taobao.org
2 cnpm install node-sass

```

```
终端命令
sudo lsof -i:8080

COMMAND   PID    USER   FD      TYPE             DEVICE                      SIZE/OFF      NODE       NAME
Java              716      a           313u   IPv6               0x1111111111111     0t0                    TCP        *:cslistener (LISTEN)

然后根据PID杀进程：
sudo kill -9 716

getParameterByName: function (name, url) {
    if (!url) url = window.location.href;
    name = name.replace(/[\[\]]/g, "\\$&");
    var regex = new RegExp("[?&]" + name + "(=([^&#]*)|&|#|$)"),
        results = regex.exec(url);
    if (!results) return null;
    if (!results[2]) return '';
    return decodeURIComponent(results[2].replace(/\+/g, " "));
},

```
```

如果希望保留生产服务器上所做的改动,仅仅并入新配置项, 处理方法如下:
git stash 
git pull 
git stash pop
然后可以使用git diff -w +文件名 来确认代码自动合并的情况. 
 
反过来,如果希望用代码库中的文件完全覆盖本地工作版本. 方法如下:
git reset --hard 
git pull
其中git reset是针对版本,如果想针对文件回退本地修改,使用 
 git checkout HEAD file/to/restore  
```

```
// object validation rules
const schema = {
  first: {
    required:true
  },
  last: {
    required:true
  }
}

// universal validation function
const validate = (schema, values) => {
  for(field in schema) {
    if(schema[field].required) {
      if(!values[field]) {
        return false;
      }
    }
  }
  return true;
}
console.log(validate(schema, {first:'Bruce'})); // false
console.log(validate(schema, {first:'Bruce',last:'Wayne'})); // true


var a = $.extend( {}  ,{ a: 1 , b: 2 } , { a: 2 } )
console.log(a)//{a: 2, b: 2}

数组平均数
使用reduce（）将每个值添加到累加器，初始值为0，总和除以数组长度。

const average = arr => arr.reduce((acc, val) => acc + val, 0) / arr.length;
// average([1,2,3]) -> 2
function average(arr) {
    return arr.reduce(function (acc, val) {
        return acc + val
    },0)/arr.length;
}

const capitalizeEveryWord = str => str.replace(/\b[a-z]/g, char => char.toUpperCase());
// capitalizeEveryWord('hello world!') -> 'Hello World!'

//const filterNonUnique = arr => arr.filter(i => arr.indexOf(i) === arr.lastIndexOf(i));
 //filterNonUnique([1,2,2,3,4,4,5]) //-> [1,3,5]

const scrollToTop = _ => {
  const c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};
// scrollToTop()


const unique = arr => [...new Set(arr)];

// unique([1,2,2,3,4,4,5]) -> [1,2,3,4,5]


(!(~+[])+{})[--[~+""][+[]]*[~+[]] + ~~!+[]]+({}+[])[[~!+[]]*~+[]]


```
```
/**
获取一个元素的距离文档(document)的位置，类似jQ中的offset()
@param {HTMLElement} ele
@returns { {left: number, top: number} }
 **/
function offset(ele) {
    var pos = {
        left: 0,
        top: 0
    };
    while (ele) {
        pos.left += ele.offsetLeft;
        pos.top += ele.offsetTop;
        ele = ele.offsetParent;
    };
    return pos;
}


/**
 * @desc   判断`obj`是否为空
 * @param  {Object} obj
 * @return {Boolean}
 */
function isEmptyObject(obj) {
    if (!obj || typeof obj !== 'object' || Array.isArray(obj))
        return false
    return !Object.keys(obj).length
}
Object.keys({a:1,b:2})//[a,b]
Object.values({a:1,b:2})//[1,2]

/*
* @desc 随机生成颜色
* @return {String}
    */
    function randomColor() {
        return '#' + ('00000' + (Math.random() * 0x1000000 <<0).toString(16)).slice(-6);
    }

/**
 *
 * @desc 生成指定范围随机数
 * @param  {Number} min
 * @param  {Number} max
 * @return {Number}
 */
function randomNum(min, max) {
    return Math.floor(min + Math.random() * (max - min));
}

/**
 *
 * @desc   判断是否为邮箱地址
 * @param  {String}  str
 * @return {Boolean}
 */
function isEmail(str) {
    return /\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*/.test(str);
}

/**
 *
 * @desc  判断是否为身份证号
 * @param  {String|Number} str
 * @return {Boolean}
 */
function isIdCard(str) {
    return /^(^[1-9]\d{7}((0\d)|(1[0-2]))(([0|1|2]\d)|3[0-1])\d{3}$)|(^[1-9]\d{5}[1-9]\d{3}((0\d)|(1[0-2]))(([0|1|2]\d)|3[0-1])((\d{4})|\d{3}[Xx])$)$/.test(str)
}

/**
 *
 * @desc   判断是否为手机号
 * @param  {String|Number} str
 * @return {Boolean}
 */
function isPhoneNum(str) {
    return /^(0|86|17951)?(13[0-9]|15[012356789]|17[678]|18[0-9]|14[57])[0-9]{8}$/.test(str)
}

/**
 *
 * @desc   判断是否为URL地址
 * @param  {String} str
 * @return {Boolean}
 */
function isUrl(str) {
    return /[-a-zA-Z0-9@:%._\+~#=]{2,256}\.[a-z]{2,6}\b([-a-zA-Z0-9@:%_\+.~#?&//=]*)/i.test(str);
}

/**
 *
 * @desc   现金额转大写
 * @param  {Number} n
 * @return {String}
 */
function digitUppercase(n) {
    var fraction = ['角', '分'];
    var digit = [
        '零', '壹', '贰', '叁', '肆',
        '伍', '陆', '柒', '捌', '玖'
    ];
    var unit = [
        ['元', '万', '亿'],
        ['', '拾', '佰', '仟']
    ];
    var head = n < 0 ? '欠' : '';
    n = Math.abs(n);
    var s = '';
    for (var i = 0; i < fraction.length; i++) {
        s += (digit[Math.floor(n * 10 * Math.pow(10, i)) % 10] + fraction[i]).replace(/零./, '');
    }
    s = s || '整';
    n = Math.floor(n);
    for (var i = 0; i < unit[0].length && n > 0; i++) {
        var p = '';
        for (var j = 0; j < unit[1].length && n > 0; j++) {
            p = digit[n % 10] + unit[1][j] + p;
            n = Math.floor(n / 10);
        }
        s = p.replace(/(零.)*零$/, '').replace(/^$/, '零') + unit[0][i] + s;
    }
    return head + s.replace(/(零.)*零元/, '元')
            .replace(/(零.)+/g, '零')
            .replace(/^整$/, '零元整');
}


/**
 * @desc   格式化${startTime}距现在的已过时间
 * @param  {Date} startTime
 * @return {String}
 */
function formatPassTime(startTime) {
    var currentTime = Date.parse(new Date()),
        time = currentTime - startTime,
        day = parseInt(time / (1000 * 60 * 60 * 24)),
        hour = parseInt(time / (1000 * 60 * 60)),
        min = parseInt(time / (1000 * 60)),
        month = parseInt(day / 30),
        year = parseInt(month / 12);
    if (year) return year + "年前"
    if (month) return month + "个月前"
    if (day) return day + "天前"
    if (hour) return hour + "小时前"
    if (min) return min + "分钟前"
    else return '刚刚'
}

/**
 *
 * @desc   格式化现在距${endTime}的剩余时间
 * @param  {Date} endTime
 * @return {String}
 */
function formatRemainTime(endTime) {
    var startDate = new Date(); //开始时间
    var endDate = new Date(endTime); //结束时间
    var t = endDate.getTime() - startDate.getTime(); //时间差
    var d = 0,
        h = 0,
        m = 0,
        s = 0;
    if (t >= 0) {
        d = Math.floor(t / 1000 / 3600 / 24);
        h = Math.floor(t / 1000 / 60 / 60 % 24);
        m = Math.floor(t / 1000 / 60 % 60);
        s = Math.floor(t / 1000 % 60);
    }
    return d + "天 " + h + "小时 " + m + "分钟 " + s + "秒";
}

/**
 *
 * @desc   url参数转对象
 * @param  {String} url  default: window.location.href
 * @return {Object}
 */
function parseQueryString(url) {
    url = url == null ? window.location.href : url
    var search = url.substring(url.lastIndexOf('?') + 1)
    if (!search) {
        return {}
    }
    return JSON.parse('{"' + decodeURIComponent(search).replace(/"/g, '\\"').replace(/&/g, '","').replace(/=/g, '":"') + '"}')
}


/**
 *
 * @desc   对象序列化
 * @param  {Object} obj
 * @return {String}
 */
function stringfyQueryString(obj) {
    if (!obj) return '';
    var pairs = [];
    for (var key in obj) {
        var value = obj[key];
        if (value instanceof Array) {
            for (var i = 0; i < value.length; ++i) {
                pairs.push(encodeURIComponent(key + '[' + i + ']') + '=' + encodeURIComponent(value[i]));
            }
            continue;
        }
        pairs.push(encodeURIComponent(key) + '=' + encodeURIComponent(obj[key]));
    }
    return pairs.join('&');
}
````

```
git checkout branch -- filename  //把branch的filename覆盖当前；
dev   modified:   src/js/news/lists.js
	modified:   src/js/dataCenter/daZongJiaoYi.js

git pull <远程主机名> <远程分支名>:<本地分支名>
比如，取回origin主机的develop分支，与本地的master分支合并，需要写成下面这样。
git pull origin develop:master

git pull origin develop

http://idea.iteblog.com/key.php

git checkout 1220 -- h5/whiteLesson/oneAppointNewStock

```

```
http://mp.weixin.qq.com/s/704rUV3U0BwQuVea1Iwe4Q
禁止蒙层底部页面跟随滚动

let bodyEl = document.body  let top = 0
 
function stopBodyScroll(isFixed) { 
    if (isFixed) {
        top = window.scrollY
        bodyEl.style.position = 'fixed'
        bodyEl.style.top = -top + 'px'
    } else {
        bodyEl.style.position = ''
        bodyEl.style.top = ''
        window.scrollTo(0, top) // 回到原先的top  	} }

http://mp.weixin.qq.com/s/_rt-c6U596IUIbAcZ9Kd0Q
3. 工资的数组 [1500, 1200, 2000, 2100, 1800], 把工资超过 2000 的删除
*    var arr = [1500, 1200, 2000, 2100, 1800]; 
*    //利用filter()形成一个数组;return true;组成的数组; 
*    var newArr = arr.filter(function (ele, i, array) { 
*        //2000以上返回false; 
*        if(ele<2000){ 
*            return true; 
*        }else{ 
*            return false; 
*        } 
*    }); 
*    console.log(newArr); // [1500, 1200, 1800] 

 
```

```
git clone https://github.com/remy/jsconsole
cd jsconsole
npm install
node .
打开http://10.199.73.23:8000
输入:listen
拷贝<script></script>放到需要调试的html页面中；
发布开发环境后，用手机可以调试console；

arr2 = arr1.slice(0);
arr2 = arr1.concat();
从上面两个例子可以看出，由于数组内部属性值为引用对象，因此使用slice和concat对对象数组的拷贝，整个拷贝还是浅拷贝，拷贝之后数组各个值的指针还是指向相同的存储地址。
因此，slice和concat这两个方法，仅适用于对不包含引用对象的一维数组的深拷贝
```
```
删除h5
cd src

fis3 release prod
 找到dest文件夹h5, 压缩成zip文件
cd  ../dest
拷贝到服务器上:
scp h5.zip root@10.199.101.221:/usr/local/nginx/html      13579
 登录服务器: 
ssh root@10.199.101.221 
 进入服务器文件夹 
cd /usr/local/nginx/html  

 rm -rf h5

unzip -o h5.zip


uat:scp h5.zip appcheck@10.199.103.148:/srv/static   appcheck


http://ws.webdev.wang:66

http://note.youdao.com/share/?id=0c76e3901ba16f76f1bd2a95ee6a5b13&type=note

 git checkout master -- src/js/newList/newList.js
git checkout branch -- filename
```
```
倒序排序对象
function sortObj(obj) {
        var arr = [];
        for (var i in obj) {
            arr.push([obj[i],i]);
        };
        arr.reverse();
        var len = arr.length;
        var obj = {};
        for (var i = 0; i < len; i++) {
            obj[arr[i][1]] = arr[i][0];
        }
        return obj;
    }

原理是先转成了数组，对数组进行一系列排序操作，再赋值给对象返回
```
```
关闭当前端口号：

1.    lsof -i:端口号
会有类似下面的结果：  
1. kill -9 42624
结束进程就搞定了
```
```
sort 排列
function   compare(value1,value2) {
	if(value1 < value2)  {
		return  -1;
	}  else   if (value1 > value2)  {
		return    1;
	}else {
		return   0;
	}
}

arr.sort(compare);

concat()  ,  slice()  ,  substr()   ,  substring()  trim()这几个方法不会修改字符串本身的值——他们只是返回一个基本类型的字符串值，对原始字符串没有任何影响。



function arrcompare(prop){
        return function (obj1, obj2) {
            var val1 = obj1[prop];
            var val2 = obj2[prop];
            if (!isNaN(Number(val1)) && !isNaN(Number(val2))) {
                val1 = Number(val1);
                val2 = Number(val2);
            }
            if (val1 < val2) {
                return 1;
            } else if (val1 > val2) {
                return -1;
            } else {
                return 0;
            }
        }
    };
 arr.sort(arrcompare(“age"));
 ```
 ```
 证券用户名
xuanfeng27
daydayup27
倩女幽魂
```
```
如何让2个并列的div根据内容自动保持同等高度
function $(id){ 
	return document.getElementById(id) 
} 
function getHeight() { 
	if ($("left").offsetHeight>=$("right").offsetHeight){
		$("right").style.height=$("left").offsetHeight + "px";
	}
	else{
		$("left").style.height=$("right").offsetHeight + "px";
	}	
}
window.onload = function() {
	getHeight();
}


css也可以实现等高的需求
.module{
overflow:hidden;
}
.module-a,.module-b{
float:left;
width:400px;
padding-bottom:200em;
margin-bottom:-200em;
background:red;}
.module-b{
background:green;
}
```
```
input输入框的change事件，要在input失去焦点的时候才会触发
$('input[name=myInput]').change(function() { 

 });
在输入框内容变化的时候不会触发change，当鼠标在其他地方点一下才会触发用下面的方法会生效，input

$('textarea').bind('input propertychange', function() {
    $('.msg').html($(this).val().length + ' characters');
});

$("#input_id").on('input',function(e){  
	 alert('Changed!')  
});  
```
```
jQuery全选与反选，且解决点击只执行一次的问题
<html>
<head>
　　<script src="jquery-1.11.1.min.js" type="text/javascript"></script>
</head>
<body>
　　<input type="checkbox" name="chk_list[]" value="1" />1
　　<input type="checkbox" name="chk_list[]" value="2" />2
　　<input type="checkbox" name="chk_list[]" value="3" />3
　　<input type="checkbox" name="chk_list[]" value="4" />4
　　<input type="checkbox" name="chk_all" id="chk_all" />全选/取消全选

<script type="text/javascript">
　　$("#chk_all").click(function(){
    　　// 使用attr只能执行一次
    　　$("input[name='chk_list[]']").attr("checked", $(this).attr("checked")); 
    
    　　// 使用prop则完美实现全选和反选
    　　$("input[name='chk_list[]']").prop("checked", $(this).prop("checked"));

　　　　// 获取所有选中的项并把选中项的文本组成一个字符串
    　　var str = '';
    　　$($("input[name='chk_list[]']:checked")).each(function(){
        　　str += $(this).next().text() + ',';
    　　});
    　　alert(str);
　　});
</script>

</body>
</html>
```
```
git 命令

项目
1： git pull
2:    git status  用于查看项目的当前状态
3:    git add - - 提交的文件
4:    git commit — “提交的信息”
5:    git push
git config --global user.name “zll”
git config --global user.email 82825287@qq.com

http://192.168.20.238/shhxzq/recruitment.git

git remote set-url origin http://10.199.101.162/shhxzq/shhxzq-enterprise.git

http://192.168.20.162
zhaoliangliang
82825287@qq.com
daydayup
```
gongjijinzhanghao
xuanfeng27
892657zll27

apple store
82825287@qq.com
web_developer_zll@163.com
DayDayUp27
zhaoliangliang
```
```
http-server

sudo  npm   install   http-server   -g
password    zll
cd  work
cd rec
http-server启动
http://192.168.20.17:8080
```
