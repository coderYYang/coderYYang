# 8.15至9.15学习笔记

# Vue

### 父组件传值给子组件

- props

  - ```javascript
    props: {
        list: Number,
        data: {
            数组/对象的默认值应当由一个工厂函数返回
            type: Array,
            default() {
                return [];
            }
        }
    }
    ```

  - 在 props 中接收数据，注意props对象里面 键值 是对改数据的 数据类型 的规定。做了规范，使用者就只能传输指定类型的数据，否则报警告

### 子组件传给父组件

- this.$emit()

  - ```html
    <button @click="btnClick">按钮</button>
    ```

    ```javascript
    methods: {
        btnClick(data) {
            // 传递一个名为 childrenClick 的点击事件给父级
            this.$emit('childrenClick', data);
        }
    }
    //传给父组件
    <children-item @childrenClick="childrenClick"></children-item>
    childrenClick(data) {
        console.log(data);
    }
    ```

### vue中的方法和函数

```javascript
methods: {},    // 定义事件方法

filters: {},    // 定义私有的过滤器

directives: {},    // 定义私有的指令

components: {},    // 定义实例内部私有的组件

watch:{},    // 监听值的变化，然后执行相对应的函数（或者步骤）

beforeCreate() {},    // 实例刚在内存中被创建出来，还没初始化好data和methods 属性之前调用此函数

created() {},    // 实例已经在内存中创建完成，此时 data 和 methods 属性初始化完成，页面（HTML）加载完成之前（未开始编译模板）调用此函数。执行顺序：父组件 -> 子组件

beforeMount() {},    // 此时已经完成了模板的编译，但是还没有挂载到页面中，在挂载开始之前调用此函数

mounted() {},    // 此时已经将编译好的模板，挂载到了页面指定的容器中显示。页面（HTML）加载完成之后调用此函数。执行顺序：子组件 -> 父组件

beforeUpdate() {},    // 状态更新之前调用此函数，此时 data 中的状态值是最新的，但是界面上显示的数据还是旧的，因为此时还没有开始重新渲染 DOM 节点

 updated() {},    // 状态更新完成之后调用此函数，此时 data 中的状态值和界面上显示的数据，都已经完成了更新，界面已经被重新渲染好了

beforeDestroy() {},    // 实例销毁之前调用此函数。在这一步，实例仍然完全可用

destroyed() {},    // 实例销毁后调用此函数。该钩子被调用后，对应 Vue 实例的所有指令都被解绑，所有的事件监听器被移除，所有的子实例也都被销毁
```

### vue3.0创建项目

- **`vue creat`** 项目名

### 跨域配置(开发换环境proxy)

```javascript
module.exports = {
    lintOnSave: false,
    outputDir: 'dist', //build输出目录
    assetsDir: 'assets', //静态资源目录（js, css, img）
    lintOnSave: false, //是否开启eslint
    devServer: {
        open: true, //是否自动弹出浏览器页面
        host: "localhost", //表示启动的时候使用的域名，默认可以不写，则是使用localhost和本机IP
        port: '1001', // 设置端口号
        https: false, //是否使用https协议
        hotOnly: false, //是否开启热更新
        proxy: {
            '/api': {
                target: 'http://10.10.2.135:9000', //API服务器的地址
                // ws: true, //代理websockets
                changeOrigin: true, // 是否跨域，虚拟的站点需要更管origin
                pathRewrite: {
                    '^/api': '/api',
                }
            },
        },
    }
}
```

### Vue-router 路由

##### 路由在index.js中的配置

```javascript
{
  path: '', //跳转路径
  name: '', //跳转名字
  component: () => import (''), //vue文件存在路径
  children: [{}] ,//子集路由,配置与路由配置一样
}
```

##### 路由跳转

```javascript
this.$router.push({path: '跳转路径'});
```

##### 路由传参

1. query传参：

   ```javascript
   getData(id) {
     this.$router.push({
       path: '/跳转路径',
       query: {
         id: id.id //需要传递过去的参数
       }
     }) 
   }
   ```

2. params传参： 

   ```javascript
   getData(id) {
     this.$router.push({
       name: '/跳转路径',
       params: {
         id: id.id //需要传递过去的参数
       }
     })
   }
   ```

3. 直接调用`$router.push`实现携带参数的跳转

   ```javascript
   getData(id) {
     this.$router.push({
        path: '/跳转路径/${id}',
     })
   }
   //对应路由配置
   {
      path: '/跳转路径/:id',
      name: 'name',
      component: Path
     }
   ```

   

4. 接收参数 

   ```javascript
   this.$route.query.id; //query参数
   this.$route.params.id; //params参数
   ```


### keep-alive的两个属性

- include: 字符串或正则表达式，**只有匹配的组件会被缓存**

- exclude:字符串或正则表达式，**任何匹配的组件都不会被缓存**

***



# WebStorage提供的两种API

### localStorage（本地存储）

- localStorage的生命周期是永久的，关闭页面或浏览器之后localStorage中的数据也不会消失。localStorage除非主动删除数据，否则数据永远不会消失
- 数据保存在客户端本地的硬件设备(通常指硬盘，也可以是其他硬件设备)中，即使浏览器被关闭了，该数据仍然存在，下次打开浏览器访问网站时仍然可以继续使用

1. **保存数据**

   - ​	`localStorage.setItem (key, value)` 保存数据，以键值对的方式储存信息。

   - ```javascript
     localStorage.setItem("key","value");
     //或者写成
     localStorage.key="value";
     ```

2. **读取数据**

   - `localStorage.getItem (key)` 获取数据，将键值传入，即可获取到对应的value值。

   - ```javascript
     变量=localStorage.getItem("key");
     //或者写成
     变量=localStorage.key;
     ```

### sessionStorage（会话存储）

- sessionStorage的生命周期是在仅在当前会话下有效。sessionStorage引入了一个“浏览器窗口”的概念，sessionStorage是在同源的窗口中始终存在的数据。只要这个浏览器窗口没有关闭，即使刷新页面或者进入同源另一个页面，数据依然存在。但是sessionStorage在关闭了浏览器窗口后就会被销毁。同时独立的打开同一个窗口同一个页面，sessionStorage也是不一样的

- 数据保存在session对象中。所谓session，是指用户在浏览某个网站时，从进入网站到浏览器关闭所经过的这段时间，也就是用户浏览这个网站所花费的时间。session对象可以用来保存在这段时间内所要求保存的任何数据。

1. **保存数据**

   - `sessionStorage.setItem (key, value)` 保存数据，以键值对的方式储存信息

   - ```javascript
     sessionStorage.setItem("key","value");
     //或者写成
     sessionStorage.key="value";
     ```

2. **读取数据**

   - `sessionStorage.getItem (key) `获取数据，将键值传入，即可获取到对应的value值。

   - ```javascript
     变量=sessionStorage.getItem("key");
     //或者写成
     变量=sessionStorage.key;
     ```

### 共性

1. **存储大小：**
   - localStorage和sessionStorage的存储数据大小一般都是：5MB

2. **存储位置：**

   - localStorage和sessionStorage都保存在客户端，不与服务器进行交互通信

3. **存储内容类型：**

   - localStorage和sessionStorage只能存储字符串类型，对于复杂的对象可以使用ECMAScript提供的JSON对象的stringify和parse来处理

4. **获取方式**

   - localStorage：window.localStorage;
   - sessionStorage：window.sessionStorage;

5. **应用场景：**

   - localStoragese：常用于长期登录（+判断用户是否已登录），适合长期保存在本地的数据
   - sessionStorage：敏感账号一次性登录

6. **方法**

   1. **删除单个**
      - `localStorage.removeItem (key)` 删除单个数据，根据键值移除对应的信息。

   2. **删除所有**
      - `localStorage.clear ()` 删除所有的数据

   3. **获取某个索引的key **
      - `localStorage.key` (index) 获取某个索引的key

### 区别

sessionStorage为临时保存，而localStorage为永久保存。

### cookie 、sessionStorage与localStorage的区别

![cookie](E:\WLK\MyNote\Study\cookie.png)

***

# UI 框架

1. **Element UI**
   - [https://element.eleme.cn/#/zh-CN]
2. **Vant**
   - [https://vant-contrib.gitee.io/vant/#/zh-CN/]
3. **iView**
   - [https://iview.github.io/]
4. **ECharts**
   - [https://echarts.apache.org/zh/index.html]
5. **vxe-table**
   - [https://xuliangzhan_admin.gitee.io/vxe-table/#/table/start/install]

# 工具类函数

1. **xe-utils**
   - [https://github.com/xuliangzhan/xe-utils]

# Axios获取数据参数类型

### params

1. **get 请求**
2. **delete 请求**

### data

1. **post 请求**
2. **put 请求**





# 7.15至8.15学习笔记

***

## 门禁卡项目和角色管理项目

***

1. 

***

### Vant 移动端组件库

##### 通过npm安装Vant

**npm install vant -S**

##### 组件

1. **button 组件**

2. **Layout 布局组件**

3. **Cell 单元格**

4. **Toast 提示**

5. **Checkbox 复选框**

6. **Field 输入框**

7. **Dialog 弹出框**

   - Dialog 是一个函数，调用后会直接在页面中弹出相应的模态框。

   - 通过组件调用 Dialog 时，可以通过下面的方式进行注册

     - 

       ```javascript
       import Vue from 'vue';
       import { Dialog } from 'vant';
       // 全局注册
       Vue.use(Dialog);
       // 局部注册
       export default {
         components: {
           [Dialog.Component.name]: Dialog.Component,
         },
       };
       ```

       

8. **PullRefresh 下拉刷新**

   - 下拉刷新时会触发 `refresh` 事件，在事件的回调函数中可以进行同步或异步操作，操作完成后将 `v-model` 设置为 `false`，表示加载完成。

   - ```html
     <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
       <p>刷新次数: {{ count }}</p>
     </van-pull-refresh>
     ```

   - ```javascript
     import { Toast } from 'vant';export default {  data() {    return {      count: 0,      isLoading: false,    };  },  methods: {    onRefresh() {      setTimeout(() => {        Toast('刷新成功');        this.isLoading = false;        this.count++;      }, 1000);    },  },};
     ```

     

9. **Collapse 折叠面板**

10. **List 列表**

    - List 组件通过 `loading` 和 `finished` 两个变量控制加载状态，当组件滚动到底部时，会触发 `load` 事件并将 `loading` 设置成 `true`。此时可以发起异步操作并更新数据，数据更新完毕后，将 `loading` 设置成 `false` 即可。若数据已全部加载完毕，则直接将 `finished` 设置成 `true` 即可。

    - ```html
      <van-list v-model="loading" :finished="finished" finished-text="没有更多了" @load="onLoad">  <van-cell v-for="item in list" :key="item" :title="item" /></van-list>
      ```

    - ```javascript
      methods: {    onLoad() {      // 异步更新数据      // setTimeout 仅做示例，真实场景中一般为 ajax 请求      setTimeout(() => {        for (let i = 0; i < 10; i++) {          this.list.push(this.list.length + 1);        }        // 加载状态结束        this.loading = false;        // 数据全部加载完成        if (this.list.length >= 40) {          this.finished = true;        }      }, 1000);    },  },};
      ```

      

11. **Popup 弹出层**

***

### Element UI

##### 通过npm安装Element UI

**npm install element-ui -S**

##### 组件

1. **Button 按钮**

2. **Input 输入框**

3. **Select 选择器**

   - change 事件

4. **Table 表格**

5. **Tree 树形控件**

   - node-click 事件
   - check-change 事件

6. **Alert 警告**

7. **Message 消息提示**

8. **Dialog 对话框**

9. **Collapse 折叠面板**

10. **Pagination 分页**

    **属性**

    -  每页显示条目个数，支持 .sync 修饰符
    -  total 总条目数
    -  current-page 当前页数，支持 .sync 修饰符
    -  prev-text 替代图标显示的上一页文字
    -  next-text 替代图标显示的下一页文字

    **事件**

    - size-change --> pageSize改变时会触发
    - current-change --> currentPage 改变时会触发
    - prev-click 用户点击上一页按钮改变当前页后触发
    - next-click 用户点击下一页按钮改变当前页后触发

***

### axios 请求数据

##### 通过npm安装axios

 **npm install axios**

##### axios 请求

```javascript
//axios 默认为get请求//get请求axios({    method: 'get', //请求为get请求    url: '请求数据地址', //请求数据的地址    params: {        key: value, //请求参数    },}).then(res => {    //成功执行then    console.log(res);}).catch(err => {    //失败执行catch    console.log(err);})//post请求axios({    method: 'post', //请求为get请求    url: '请求数据地址', //请求数据的地址    data: {        key: value, //请求参数    },}).then(res => {    //成功执行then    console.log(res);}).catch(err => {    //失败执行catch    console.log(err);})
```

##### axios 拦截器

```javascript
//axios 拦截器import axios from 'axios'; //导入axios// 创建request函数并导出export function request(config) {  // 1.创建axios的实例  const instance = axios.create({    baseURL: "请求地址", //设置请求地址    timeout: 5000, //设置超时时间  })  // 2. axios的拦截器  // 2.1 请求拦截  instance.interceptors.request.use(config => {    return config  }, err => {    // console.log(err);    // 返回错误信息  })  // 2.2 响应拦截  instance.interceptors.response.use(res => {    return res.data  }, err => {    // console.log(err);    // 返回错误信息  })  // 3. 发送真正的网络请求  return instance(config)}// 使用拦截器，在需要使用的地方导入
```

***

### Less

##### 通过npm安装Less

最好是指定版本：**npm install less@3.9.0 less-loader@4.1.0 --save-dev**

使用的Less时在 **`style`**标签内加上**`lang="less"`**

#####  变量(Variables)写法

```less
@width: 10px;@height: @width + 10px;.header {  width: @width;  height: @height;}
```

##### 混合(Mixins)写法

```less
.border {    border-top: 1px solid #000;    border-bottom: 1px solid #000;}.left {    color: #1890ff;    .border();}.right {    color: #f00;    .border();}// .border 类所包含的属性将同时出现在.left和.right中
```



##### 嵌套(Nesting)写法

```less
.header {    color: #000;    .left {        font-size: 16px;    }    .right {        font-weight: bold;    }    // 为元素写法    &:before {        // Your code...    }}
```

***

### Git

##### 常用命令

克隆： **git clone 克隆地址**

提交代码：

1. 更新一下代码：**git pull**
2. 提交代码：**git add** 需要提交的文件或文件夹
3. 提交代码备注：**git commit -m 'message'**
4. 提交更改：**git push**

