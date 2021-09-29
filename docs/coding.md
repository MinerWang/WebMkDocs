# Coding

### ...展开

---

- 展开语法
  </br>构造新数组

        var parts = ['shoulders', 'knees'];
        var lyrics = ['head', ...parts, 'and', 'toes'];
        // ["head", "shoulders", "knees", "and", "toes"]

### vue keep-alive 缓存页面

---

- `keep-alive` 是 vue 内置组件，可以使被包含的组件保留状态不被重新渲染。
  `router-view` 也是一个组件，如果直接被包在 `keep-alive` 里面，所有路径匹配到的视图组件都会被缓存：

        <keep-alive>
            <router-view>
                <!-- 所有路径匹配到的视图组件都会被缓存！ -->
            </router-view>
        </keep-alive>

---

- 生命周期变化
  </br>1.不使用 keep-alive 的情况：beforeRouteEnter --> created --> mounted --> destroyed
  </br>2.使用 keep-alive 的情况：beforeRouteEnter --> created --> mounted --> activated --> deactivated
  </br>3.使用 keep-alive，并且再次进入了缓存页面的情况：beforeRouteEnter -->activated --> deactivated

---

- router 文件下的 index.js 配置

        export default [
        {
            path: '/',
            name: 'home',
            component: Home,
            meta: {
                keepAlive: true // 需要被缓存
            }
        }, {
            path: '/:id',
            name: 'edit',
            component: Edit,
            meta: {
                keepAlive: false // 不需要被缓存
            }
        }

---

- 海康 vessels 脚手架中使用

在 App.vue 中添加

    <keep-alive>
        <router-view v-if="$route.meta.keepAlive" />
    </keep-alive>
        <router-view v-if="!$route.meta.keepAlive" />

在 router 文件下的 index.js 添加

    const processRouteObj = ({ menuCode, 《keepAlive》, breadcrumb, children, component, ...args }) => {
        return Object.assign({
            meta: { menuCode, 《keepAlive》 },
            props: {
            breadcrumbObj: {
                content: breadcrumb,
                menuCode: menuCode
            }
        },

在 router.config.js 中配置

    keepAlive: true

### VUEX 保存全局变量的使用

---

Vessels 脚手架中存入变量

    this.$store.commit('setColumnIndex', row.id)

在 store->mutations.js 中添加

    setColumnIndex (state, columnIndex) {
        state.columnIndex = columnIndex
    }

在 stire->index 的 state 中添加

    const state = {
    columnIndex: null
    }

取出变量

    ...mapState(['columnIndex'])

### 路由传参

---

跳转时传入

    this.$router.push({
    path: '/AssetDetailView',
    query: { rowId: row.id}
    })

取出

    this.$route.query.rowId

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

### 语法糖

---

vue .sync

    父组件：
        <comp :show.sync="visible"></comp>
    子组件：里面用update的方法，通知父组件，此属性值被修改了
        close () {
            this.$emit('update:show', is_show)
        }

数据类型

    a-0或者a*1，把a转成数字
    a+""，把a转成字符串

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

### 添加回车监听事件

---

写在 mounted 中

    mounted() {
        // 监听回车方法
        document.onkeydown = e => {
        if (e.code === 'Enter') {
            // 做点击回车后的事件，回车的键值是enter
            this.onSearch()
        }
        }
    },

### var \_this = this

---

\_this 是一个变量名，this 代表父函数，如果在子函数还用 this，this 的指向就变成子函数了，\_this 就是用来存储指向的。

### HTML DOM setInterval() 方法

---

</br> setInterval() 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。
</br> setInterval() 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval() 方法的参数。

    this.timer = setInterval(function () {
                        _this.DataNow = new Date(); //修改数据date
                    }, 1000);

### lodash 中 pick 和 omit 函数介绍

---

[lodash](https://blog.csdn.net/suwu150/article/details/75250749)
