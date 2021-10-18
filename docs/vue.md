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

### 