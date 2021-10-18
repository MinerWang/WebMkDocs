### ...展开

---

展开语法
</br>构造新数组

    var parts = ['shoulders', 'knees'];
    var lyrics = ['head', ...parts, 'and', 'toes'];
    // ["head", "shoulders", "knees", "and", "toes"]

### HTML DOM setInterval() 方法

---

</br> setInterval() 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。
</br> setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval() 方法的参数。

    this.timer = setInterval(function () {
                        _this.DataNow = new Date(); //修改数据date
                    }, 1000);

### 去除数组重复成员

---

    [...new Set(array)]

### 去除字符串重复字符

---

    [...new Set('ababbc')].join('')

### lodash 中 pick 和 omit 函数介绍

---

[lodash](https://blog.csdn.net/suwu150/article/details/75250749)

### 对象数组转枚举

---

[{name:'Arvin'}]---[{prop：'name',label:'名字'}]>>>>[{名字:'Arvin'}]

    for (const key in this.list[0]) {
                this.DetailData.forEach(item => {
                if (key === item.prop) {
                    console.log(key, '----', item.prop)
                    const arrItem = {}
                    arrItem.value = this.list[0][key]
                    arrItem.label = item.label
                    this.DetailViewList.push(arrItem)
                }
                })
            }

### JS 字符串操作

---

</br> 函数：substring()
</br> 定义：substring(start,end)表示从 start 到 end 之间的字符串，包括 start 位置的字符但是不包括 end 位置的字符。
</br> 功能：字符串截取，比如想从"MinidxSearchEngine"中得到"Minidx"就要用到 substring(0,6)
</br> 例子：

    var src="images/off_1.png";
    alert(src.substring(7,10));
    //弹出值为：off

</br> 函数：substr()
</br> 定义：substr(start,length)表示从 start 位置开始，截取 length 长度的字符串。
</br> 功能：字符串截取
</br> 例子：

    var src="images/off_1.png";
    alert(src.substr(7,3));
    //弹出值为：off

</br> 函数：split()
</br> 功能：使用一个指定的分隔符把一个字符串分割存储到数组
</br> 例子：

    str="jpg|bmp|gif|ico|png";
    arr=theString.split("|");
    //arr是一个包含字符值"jpg"、"bmp"、"gif"、"ico"和"png"的数组

</br> 函数：John()
</br> 功能：使用您选择的分隔符将一个数组合并为一个字符串
</br> 例子：

    var delimitedString=myArray.join(delimiter);
    var myList=new Array("jpg","bmp","gif","ico","png");
    var portableList=myList.join("|");
    //结果是jpg|bmp|gif|ico|png

</br> 函数：indexOf()
</br> 功能：返回字符串中匹配子串的第一个字符的下标

    var myString="JavaScript";
    var w=myString.indexOf("v");//w will be 2
    var x=myString.indexOf("S");//x will be 4
    var y=myString.indexOf("Script");//y will also be 4
    var z=myString.indexOf("key");//z will be -1

</br> 函数：lastIndexOf()
</br> 定义：lastIndexOf()方法返回从右向左出现某个字符或字符串的首个字符索引值（与 indexOf 相反）
</br> 功能：返回字符串索引值
</br> 例子：

    var src="images/off_1.png";
    alert(src.lastIndexOf('/'));
    alert(src.lastIndexOf('g'));
    //弹出值依次为：6,15

</br> 补充：substr 和 substring 方法的区别
</br> substr 方法
</br> 返回一个从指定位置开始的指定长度的子字符串。
</br> stringvar.substr(start [, length ])
</br> 参数
</br> stringvar
</br> 必选项。要提取子字符串的字符串文字或 String 对象。
</br> start
</br> 必选项。所需的子字符串的起始位置。字符串中的第一个字符的索引为 0。
</br> length
</br> 可选项。在返回的子字符串中应包括的字符个数。
</br> 说明
</br> 如果 length 为 0 或负数，将返回一个空字符串。如果没有指定该参数，则子字符串将延续到 stringvar 的最后。
</br> 示例

</br> 下面的示例演示了 substr 方法的用法。

    function SubstrDemo(){
        var s, ss;        // 声明变量。
        var s = "The rain in Spain falls mainly in the plain.";
        ss = s.substr(12, 5); // 获取子字符串。
        return(ss);        // 返回 "Spain"。
    }

</br> substring 方法
</br> 返回位于 String 对象中指定位置的子字符串。
</br> strVariable.substring(start, end)
</br> "String Literal".substring(start, end)
</br> 参数
</br> start
</br> 指明子字符串的起始位置，该索引从 0 开始起算。
</br> end
</br> 指明子字符串的结束位置，该索引从 0 开始起算。
</br> 说明
</br> substring 方法将返回一个包含从 start 到最后（不包含 end ）的子字符串的字符串。
</br> substring 方法使用 start 和 end 两者中的较小值作为子字符串的起始点。例如， strvar.substring(0, 3) 和 strvar.substring(3, 0) 将返回相同的子字符串。
</br> 如果 start 或 end 为 NaN 或者负数，那么将其替换为 0。
</br> 子字符串的长度等于 start 和 end 之差的绝对值。例如，在 strvar.substring(0, 3) 和 strvar.substring(3, 0) 返回的子字符串的的长度是 3。

</br> 示例
</br> 下面的示例演示了 substring 方法的用法。

    function SubstringDemo(){
        var ss; // 声明变量。
        var s = "The rain in Spain falls mainly in the plain..";
        ss = s.substring(12, 17); // 取子字符串。
        return(ss); // 返回子字符串。
    }

### JS 中的闭包和高阶函数

---

- 高阶函数满足
  </br>1.函数可以作为参数传入另一个函数
  </br>2.函数也可以作为另一个函数的返回值

### JS 函数式编程实现代理模式

- 原始函数

        const clusterExapnd = () => {
        console.log("集群扩容操作");
        }

        const clusterReboot = () => {
        console.log("集群重启");
        }

        const clusterClean = () => {
        console.log("集群清理");
        }

        const clusterShrink = () => {
        console.log("集群减容");
        }

        const backUpFile = () => {
        console.log("备份文件");
        }

        const toggleClusterWhiteList = () => {
        console.log("开启/关闭集群白名单");
        }

- 给每一个都加操作权限

        const clusterExapnd = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("集群扩容操作");
        }

        const clusterReboot = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("集群重启");
        }

        const clusterClean = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("集群清理");
        }

        const clusterShrink = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("集群减容");
        }

        const backUpFile = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("备份文件");
        }

        const toggleClusterWhiteList = () => {
        if (loginUser !== "admin") {
            console.log("当前用户没有操作权限！");
            return;
        }
        console.log("开启/关闭集群白名单");
        }

- 为了实现权限逻辑的复用 不用给每一个方法都添加判断 使用代理模式实现</br>定义一个高阶函数**valid**作为代理，接收函数作为参数，后返回一个函数，返回函数中进行权限校验，校验通过，调用传入的函数。

- 给需要加权限校验的方法外面包裹一层 valid

        let loginUser = "admin";

        const valid = (cb: () => void) => {
        return () => {
            if (loginUser === "admin") {
            cb.apply(this);
            } else {
            console.log("当前用户没有操作权限！");
            }
        }
        }

        const clusterExapnd = valid(() => {
        console.log("集群扩容操作");
        })

        const clusterReboot = valid(() => {
        console.log("集群重启");
        })

        const clusterClean = valid(() => {
        console.log("集群清理");
        })

        const clusterShrink = valid(() => {
        console.log("集群减容");
        })

        const backUpFile = valid(() => {
        console.log("备份文件");
        })

        const toggleClusterWhiteList = valid(() => {
        console.log("开启/关闭集群白名单");
        })

        let func = [clusterExapnd, clusterReboot, clusterClean, clusterShrink, backUpFile, toggleClusterWhiteList];

        func.forEach(f => f());

### Set 和 Map 数组

- new Set(); 非重复数组
- 数组去重

        function dedupe(array) {
        return Array.from(new Set(array));
        }

        dedupe([1, 1, 2, 3]) // [1, 2, 3]

- new WeakSet(); 成员只能是对象
- new Map(); 键值对
- new WeakMap(); 只接受对象键名

### Proxy 拦截器

- 常用的拦截 `get` 和 `set` 等操作

### Proxy 观察者模式

- 函数自动观察数据对象，对象有变化数据就会执行

        const person = observable({
        name: '张三',
        age: 20
        });

        function print() {
        console.log(`${person.name}, ${person.age}`)
        }

        observe(print);
        person.name = '李四';
        // 输出
        // 李四, 20

- Proxy 写一个观察者模式，实现`observable`和`observe`两个函数

          const queuedObservers = new Set();

          const observe = fn => queuedObservers.add(fn);
          const observable = obj => new Proxy(obj, {set});

          function set(target, key, value, receiver) {
          const result = Reflect.set(target, key, value, receiver);
          queuedObservers.forEach(observer => observer());
          return result;
          }

  上面代码中，先定义了一个 Set 集合，所有观察者函数都放进这个集合。然后，observable 函数返回原始对象的代理，拦截赋值操作。拦截函数 set 之中，会自动执行所有观察者。

### Promise 对象

- 是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果
- 从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。
- Promise 对象代表一个异步操作，有三种状态：`pending`（进行中）、`fulfilled`（已成功）和 `rejected`（已失败）。

### async 异步函数

- 指定多少毫秒后输出一个值

        function timeout(ms){
            return new Promise((resolve) => {
            setTimeout(resolve, ms);
        });
        }
        async function asyncPrint(value,ms){
            await timeout(ms);
            console.log(val)
        }
        asyncPrint('xxx',50)
