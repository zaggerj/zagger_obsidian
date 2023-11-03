本文为快速搭建 vite4项目，一些插件的详情就不做过多的解释，都放有官网链接，需要深入了解的小伙伴可自行查看。至于为什么选择使用[vite]( https://vitejs.cn/ "vite")，因为它具备着快速启动、按需编译、模块[热更新](https://so.csdn.net/so/search?q=%E7%83%AD%E6%9B%B4%E6%96%B0&spm=1001.2101.3001.7020)的亮点。归根结底最大的特点就是**快**。vue 的创始人是[尤雨溪](https://so.csdn.net/so/search?q=%E5%B0%A4%E9%9B%A8%E6%BA%AA&spm=1001.2101.3001.7020)大佬，vite 也是他。所以放心大胆的用吧。

## 壹、初始化项目 😆😆😆😆

#### 1️⃣ 通过yarn初始化项目

![](https://img-blog.csdnimg.cn/912453fd3da44d86bc0c96a4ecbe70ad.png)

`yarn create vite 你的项目名称 --template vue-ts`

注：如果没有yarn的可通过npm执行命令**npm install -g yarn**进行安装

#### 2️⃣ 如下图，到这里我们的vite项目就初始化好了，跟着提示，进入ts-super-web(自己的项目名)根目录下执行yarn，下载完依赖后执行yarn dev就可以启动项目。

![](https://img-blog.csdnimg.cn/cc53bdf954f341518ec3486f1f91fae7.png)

![](https://img-blog.csdnimg.cn/2c6d0faae57b4f39844d446d2674afd6.png)

![](https://img-blog.csdnimg.cn/00df347d3dde49a59bdaaf24e90c5abc.png)

3️⃣ **启动成功以后浏览器访问[http://127.0.0.1:5173/](http://127.0.0.1:5173/ "http://127.0.0.1:5173/")** 👇👇👇👇

![](https://img-blog.csdnimg.cn/eaff9b1b618043d58339c22435bfdfe6.png)

## 贰、安装相关依赖 😜😜😜😜

#### 1️⃣ element-plus为UI框架。pinia和vuex一样为状态管理。vue-router路由。nprogress顶部进度条。animate.css一个跨浏览器的动画库。

`yarn add element-plus pinia vue-router nprogress animate.css`

#### 2️⃣ 安装图标库

`yarn add @iconify-json/carbon @iconify-json/ep @iconify-json/noto -D`

#### 3️⃣ 按需引入涉及到的依赖安装

`yarn add unplugin-vue-components unplugin-auto-import unplugin-icons -D`

#### 4️⃣ 其他依赖安装，支持sass，jsx等等

`yarn add sass sass-loader @types/node @vitejs/plugin-vue-jsx -D`

#### 5️⃣ 项目根目录下修改tsconfig.json

`   1. {      2.   "compilerOptions": {      3.     "target": "esnext", // 目标语言的版本      4.     "useDefineForClassFields": true,      5.     "module": "esnext", // 生成代码的模板标准      6.     "moduleResolution": "node", // 模块解析策略，ts默认用node的解析策略，即相对的方式导入      7.     "strict": true, // 开启所有严格的类型检查      8.     "jsx": "preserve", // 指定将 JSX 编译成什么形式      9.     "jsxFactory": "h", // 当使用经典的JSX运行时编译JSX元素时，更改.js文件中调用的函数，默认：React.createElement 。      10.     "jsxFragmentFactory": "Fragment",      11.     "sourceMap": true, // 生成目标文件的sourceMap文件      12.     "resolveJsonModule": true, // 指定 JSX 片段工厂函数在指定了 jsxFactory 编译器选项的情况下针对 react JSX 发出时使用。      13.     "esModuleInterop": true, // 允许export=导出，由import from 导入      14.     // TS需要引用的库，即声明文件，es5 默认引用dom、es5、scripthost,如需要使用es的高级版本特性，通常都需要配置，如es8的数组新特性需要引入"ES2019.Array"      15.     "lib": ["esnext", "dom"],      16.     "types": ["vite/client", "element-plus/global", "unplugin-icons/types/vue"], // 加载的声明文件包      17.     "baseUrl": ".", // 解析非相对模块的基地址，默认是当前目录      18.     "skipLibCheck": true, // 忽略所有的声明文件（ *.d.ts）的类型检查。      19.     "paths": { // 路径映射，相对于baseUrl      20.       "@/*": [      21.         "src/*"      22.       ]      23.     }      24.   },      25.   // 指定一个匹配列表（属于自动指定该路径下的所有ts相关文件）      26.   "include": ["src/**/*.ts", "**/*.d.ts", "src/**/*.tsx", "src/**/*.vue", "src/autoImport/*.d.ts"],      27.   "exclude": [      28.     "node_modules"      29.   ]      30. }        `

## 叁、配置ElementPlus、图标库，vueAPI等按需引入，支持jsx、tsx等 😉😉😉😉

为什么做按需引入，相对于全局引入来说很大程度上的减少了代码体积。

#### 1️⃣ 在项目根目录下修改vite.config.ts

**注：**按需引入这里需要在src文件夹下新建一个autoImport的文件夹存在按需引入生成的文件。这样做的目的是，后期如果传git，可以屏蔽这个文件夹。

`   1. import { defineConfig } from 'vite'      2. import path from 'path'      3. import vue from '@vitejs/plugin-vue'      4. import Icons from 'unplugin-icons/vite'      5. import IconsResolver from 'unplugin-icons/resolver'      6. import AutoImport from 'unplugin-auto-import/vite'      7. import Components from 'unplugin-vue-components/vite'      8. import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'      9. import vueJsx from '@vitejs/plugin-vue-jsx';      10. const pathSrc = path.resolve(__dirname, 'src')       12. export default defineConfig({      13.   resolve: {      14.     alias: {      15.       '@': pathSrc, // 文件系统路径别名      16.     }      17.   },      18.   plugins: [      19.     vue(),      20.     vueJsx(), // 支持jsx、tsx的写法      21.     AutoImport({      22.       imports: ['vue'],      23.       resolvers: [      24.         ElementPlusResolver(),      25.         IconsResolver({      26.           prefix: 'Icon'      27.         })      28.       ],      29.       dts: path.resolve(pathSrc + '/autoImport', 'auto-imports.d.ts')      30.     }),      31.     Components({      32.       resolvers: [      33.         ElementPlusResolver(),      34.         IconsResolver({      35.           enabledCollections: ['ep', 'carbon', 'noto']      36.         })      37.       ],      38.       dts: path.resolve(pathSrc + '/autoImport', 'components.d.ts')      39.     }),      40.     Icons({      41.       autoInstall: true,      42.       compiler: 'vue3'      43.     })      44.   ],      45.   server: {      46.     host: '0.0.0.0', // 指定服务器应该监听哪个 IP 地址      47.     port: 9527, // 指定开发服务器端口      48.     strictPort: true, // 若端口已被占用则会直接退出      49.     https: false, // 启用 TLS + HTTP/2      50.     open: false, // 启动时自动在浏览器中打开应用程序      51.   }      52. })        `

#### 2️⃣ 测试ElementPlus、图标以及vue3API等按需引入情况。修改App.vue文件。

`1. <template>      2.   <el-row :gutter="20">      3.     <el-col :span="6">      4.       <el-button type="primary">Primary</el-button>      5.     </el-col>      6.     <el-col :span="6">      7.       <el-button type="success">Success</el-button>      8.     </el-col>      9.     <el-col :span="6">      10.       <el-button type="info">Info</el-button>      11.     </el-col>      12.     <el-col :span="6">      13.       <el-button type="warning"><i-ep-delete />Warning</el-button>      14.     </el-col>      15.   </el-row>      16.   <br/>      17.   <br/>      18.   <br/>      19.   <el-button type="primary" @click="changeCount">++++</el-button>      20.   <br/>      21.   <br/>      22.   <br/>      23.   <span style="color: red;font-size: 22px;">{{ count }}</span>      24. </template>       26. <script lang="ts">      27. export default defineComponent({      28.   setup() {       30.     let data = reactive({      31.       count: 1,      32.     })       34.     const changeCount = () => {      35.       data.count++      36.     }       38.     return {      39.       changeCount,      40.       ...toRefs(data)      41.     }      42.   }      43. })      44. </script>` 

#### 3️⃣ 成功运行至下列效果表示按需引入没有任何问题 👇👇👇👇

![](https://img-blog.csdnimg.cn/505f8aac217f441ebb033d4e3c6d7ffb.png)

## 肆、vue-router路由以及路由拦截器配置 😋😋😋😋

至于[vue-router](https://router.vuejs.org/zh/ "vue-router")的话，在vue2大家应该已经很熟悉了，vue全家桶必备知识。

#### 1️⃣ src文件夹下新建router文件夹。接着新建index.ts和permission.ts两个文件。前者是路由，后面是路由拦截器，我喜欢放在一块。你可以根据自己的情况放到其他位置也行。

#### 2️⃣ index.ts 路由配置

`   1. import { createRouter, createWebHashHistory, RouteRecordRaw } from 'vue-router'       3. export const asyncRoutes: RouteRecordRaw[] = [      4.     {      5.         path: '/',      6.         name: 'home',      7.         meta: {      8.             title: 'home'      9.         },      10.         component: () => import('@/views/home.vue')      11.     },      12.     {      13.         path: '/home1',      14.         name: 'home1',      15.         meta: {      16.             title: 'home1'      17.         },      18.         component: () => import('@/views/home1.vue')      19.     }      20. ]       22. const router = createRouter({      23.     history: createWebHashHistory(),      24.     routes: asyncRoutes,      25.     scrollBehavior: () => ({ left: 0, top: 0 })      26. })       28. export default router        `

#### 3️⃣ permission.ts路由拦截器,这里面使用到了nprogress顶部加载效果

`   1. import router from '@/router'      2. // @ts-ignore      3. import NProgress from 'nprogress'      4. import 'nprogress/nprogress.css'       6. NProgress.configure({      7.     easing: 'ease', // 动画方式      8.     showSpinner: true, // 是否显示加载ico      9.     trickleSpeed: 200, // 自动递增间隔      10.     minimum: 0.4, // 更改启动时使用的最小百分比      11. })       13. const whiteList = ['/login', '/redirect']       15. router.beforeEach((to, form, next) => {      16.     // 这里处理自己的逻辑,比如需要登录以后才能访问其他页面等等      17.     NProgress.start()      18.     next()      19.     NProgress.done()      20. })        `

#### 4️⃣ src下main.ts 文件修改

`1. import { createApp } from 'vue'       3. import App from './App.vue'      4. import 'animate.css'      5. import router from '@/router';      6. import '@/router/permission'      7. import 'element-plus/theme-chalk/dark/css-vars.css'       9. const app = createApp(App);       11. app.use(router)       13. app.mount('#app')` 

#### 5️⃣ src下新建views文件夹,文件夹下新建home.vue和home1.vue两个文件

**home.vue**

`1. <template>      2.   <div style="background: rgb(217, 217, 217);height: 100vh;width: 100%;display: flex;align-items: center;justify-content: center;">      3.     <el-button type="primary" @click="goHome">去home</el-button>      4.     <el-button type="primary" @click="changeCount">++++</el-button>      5.     <div style="color: red;font-size: 22px;">{{ count }}</div>      6.   </div>      7. </template>       9. <script lang="ts">      10. import {useRouter} from "vue-router";       12. export default defineComponent({      13.   setup() {       15.     const router = useRouter();       17.     let data = reactive({      18.       count: 1,      19.     })       21.     const changeCount = () => {      22.       data.count++      23.     }       25.     const goHome = () => {      26.       router.push({      27.         path: '/home1'      28.       })      29.     }       31.     return {      32.       changeCount,      33.       goHome,      34.       ...toRefs(data)      35.     }      36.   }      37. })      38. </script>` 

**hom1.vue**

`1. <template>      2.   <div style="background: #ffffff;height: 100vh;width: 100%;display: flex;align-items: center;justify-content: center;">      3.     <el-button type="primary" @click="goHome1">回home</el-button>      4.     <el-button type="primary" @click="changeCount">++++</el-button>      5.     <div style="color: red;font-size: 22px;">{{ count }}</div>      6.   </div>      7. </template>       9. <script lang="ts">      10. import {useRouter} from "vue-router";       12. export default defineComponent({      13.   setup() {       15.     const router = useRouter();       17.     let data = reactive({      18.       count: 1,      19.     })       21.     const changeCount = () => {      22.       data.count++      23.     }       25.     const goHome1 = () => {      26.       router.push({      27.         path: '/'      28.       })      29.     }       31.     return {      32.       changeCount,      33.       goHome1,      34.       ...toRefs(data)      35.     }      36.   }      37. })      38. </script>` 

#### 6️⃣ App.vue修改,这里就使用到了animate.css,给切换路由增加一些动画

`   1. <template>      2.   <router-view #default="{route, Component}">      3.     <transition leave-from-class="ts-web-fade--leave-to" enter-active-class="animate__animated animate__bounceInRight">      4.       <component :is="Component"></component>      5.     </transition>      6.   </router-view>      7. </template>        `

#### 7️⃣ 项目目录

![](https://img-blog.csdnimg.cn/780b5bec6fb044f2b984d17a958f2418.png)

#### 8️⃣ 最终的效果，可以看到切换路由的时候右上角有个圈圈在转动，因为截屏的原因，看不到顶部的加载条。还可以看到切换路由时的动画。

![](https://img-blog.csdnimg.cn/10b6876bd9a14b0ab7f0b0c0cce36fdd.gif)

 注：这里只是一个简单的搭建demo，所以拦截器没有做过多的扩展。我的另一篇文章有详细讲解动态路由的实现，但是建议先把本篇文章走完以后再去看。[Vite4 + Vue3 + vue-router4 动态路由](https://blog.csdn.net/qq_19991931/article/details/129300550 "Vite4 + Vue3 + vue-router4 动态路由")如果有问题的话可以联系我👉👉SH--TS。

## 伍、pinia状态管理 😱😱😱😱

为啥没有使用vuex而选择[pinia](https://pinia.web3doc.top/ "pinia")来实现状态管理。相对于vuex来说，它更好的支持TypeScript、非常轻巧(体积约 1KB)等等优势。而且尤雨溪大佬也推荐使用。至于它俩如何做选择。可以根据自己的项目情况，如果是中小型项目的话推荐pinia。如果大规模、高复杂度的话就选vuex。

#### 1️⃣ src文件夹下新建pinia，以及文件夹下新建index.ts等等。如下图

![](https://img-blog.csdnimg.cn/cff7301899ae4cedbdacd10ae25bff42.png)

#### 2️⃣ /pinia/modules/views.ts

``   1. import { defineStore } from 'pinia'       3. export interface IViewsState {      4.     count?: number      5.     title?: string      6. }       8. // 创建一个pinia, defineStore接受两个参数，第一个是id(唯一的)。参数二是配置项      9. export const viewsModule = defineStore('VIEWS',{      10.     state(): IViewsState {      11.         return {      12.             count: 1,      13.             title: 'Etc.End'      14.         }      15.     },      16.     //可以操作异步 和 同步提交state      17.     actions:{      18.         // 这里因为我的count定义的类型不是必有参数,所有它会存在空的情况.      19.         // 后面只需要加个!让编译器知道它不会未定义或不会为null      20.         // 也可以把上面的count?: number更改为count: number,下面就不用加!了      21.         incremental() {      22.             this.count!++      23.         },      24.         getCount() {      25.             return this.count      26.         }      27.     },      28.     // 类似于computed 可以帮我们去修饰我们的值      29.     getters:{      30.         newCount ():number | string {      31.             return this.count = 0      32.         },      33.         newTitle ():string {      34.             return `$-${this.title}`      35.         }      36.     },      37. })        ``

#### 3️⃣ /pinia/index.ts

`   1. import { viewsModule } from './modules/views';       3. export interface IAppStore {      4.     viewsModule: ReturnType<typeof viewsModule>;      5. }       7. const appStore: IAppStore = {} as IAppStore;       9. export const registerStore = () => {      10.     appStore.viewsModule = viewsModule();      11. };       13. export default appStore;        `

#### 4️⃣ main.ts

`   1. import { createApp } from 'vue'       3. import App from './App.vue'      4. import 'animate.css'      5. import { createPinia } from 'pinia';      6. import { registerStore } from '@/pinia';      7. import router from '@/router';      8. import '@/router/permission'      9. import 'element-plus/theme-chalk/dark/css-vars.css'       11. const app = createApp(App);       13. app.use(router)      14. app.use(createPinia())      15. // 这里是进行一个注册，不然的话页面上是拿不到值的      16. registerStore()       18. app.mount('#app')        `

#### 5️⃣ 修改之前的home.vue页面

`1. <template>      2.   <div style="background: rgb(217, 217, 217);height: 100vh;width: 100%;padding-top: 100px;">      3.     <div style="text-align: center;margin-top: 50px;">      4.       <el-button type="primary" @click="goHome">去home1</el-button>      5.     </div>      6.     <div style="text-align: center;margin-top: 50px;">      7.       <el-button type="primary" @click="directChange">直接修改count的值</el-button>      8.       <el-button type="primary" @click="batchChange">批量修改pinia的值</el-button>      9.       <el-button type="primary" @click="callAction">actions修改pinia的值</el-button>      10.     </div>      11.     <div style="text-align: center;margin-top: 50px;color: red;font-size: 22px;">      12.       <div>{{ count }}</div>      13.       <div>{{ title }}</div>      14.     </div>      15.   </div>      16. </template>       18. <script lang="ts">      19. import {useRouter} from "vue-router";      20. import { storeToRefs } from 'pinia';      21. import appStore from '@/pinia';       23. export default defineComponent({      24.   setup() {       26.     const router = useRouter();       28.     // 这里是个小知识点,因为pinia不允许直接解构,比如下面      29.     // const { count, title } = appStore.viewsModule      30.     // 这样写的话会失去响应式,所以得使用storeToRefs      31.     const { count, title } = storeToRefs(appStore.viewsModule)       33.     // 直接修改views里面的count值      34.     const directChange = () => {      35.       appStore.viewsModule.count!++      36.     }       38.     // 批量修改views的值      39.     const batchChange = () => {      40.       appStore.viewsModule.$patch({      41.         count: 100,      42.         title: 'Etc-End'      43.       })      44.       // 还可以这样写,和上面一样的效果      45.       // appStore.viewsModule.$state = {      46.       //   count: 100,      47.       //   title: 'Etc-End'      48.       // }      49.     }       51.     const callAction = () => {      52.       appStore.viewsModule.incremental()      53.     }       55.     const goHome = () => {      56.       router.push({      57.         path: '/home1'      58.       })      59.     }       61.     return {      62.       directChange,      63.       batchChange,      64.       callAction,      65.       goHome,      66.       count,      67.       title      68.     }      69.   }      70. })      71. </script>` 

#### 6️⃣ 修改之前的home1.vue页面

`1. <template>      2.   <div style="background: rgb(217, 217, 217);height: 100vh;width: 100%;padding-top: 100px;">      3.     <div style="text-align: center;margin-top: 50px;">      4.       <el-button type="primary" @click="goHome">回home</el-button>      5.     </div>      6.     <div style="text-align: center;margin-top: 50px;">      7.       <el-button type="primary" @click="directChange">直接修改count的值</el-button>      8.       <el-button type="primary" @click="batchChange">批量修改pinia的值</el-button>      9.       <el-button type="primary" @click="callAction">actions修改pinia的值</el-button>      10.     </div>      11.     <div style="text-align: center;margin-top: 50px;color: red;font-size: 22px;">      12.       <div>{{ count }}</div>      13.       <div>{{ title }}</div>      14.     </div>      15.   </div>      16. </template>       18. <script lang="ts">      19. import {useRouter} from "vue-router";      20. import { storeToRefs } from 'pinia';      21. import appStore from '@/pinia';       23. export default defineComponent({      24.   setup() {       26.     const router = useRouter();       28.     // 这里是个小知识点,因为pinia不允许直接解构,比如下面      29.     // const { count, title } = appStore.viewsModule      30.     // 这样写的话会失去响应式,所以得使用storeToRefs      31.     const { count, title } = storeToRefs(appStore.viewsModule)       33.     // 直接修改views里面的count值      34.     const directChange = () => {      35.       appStore.viewsModule.count!++      36.     }       38.     // 批量修改views的值      39.     const batchChange = () => {      40.       appStore.viewsModule.$patch({      41.         count: 100,      42.         title: 'Etc-End'      43.       })      44.       // 还可以这样写,和上面一样的效果      45.       // appStore.viewsModule.$state = {      46.       //   count: 100,      47.       //   title: 'Etc-End'      48.       // }      49.     }       51.     const callAction = () => {      52.       appStore.viewsModule.incremental()      53.     }       55.     const goHome = () => {      56.       router.push({      57.         path: '/'      58.       })      59.     }       61.     return {      62.       directChange,      63.       batchChange,      64.       callAction,      65.       goHome,      66.       count,      67.       title      68.     }      69.   }      70. })      71. </script>` 

#### 7️⃣ 最终效果，下图中可以看到，状态管理已经到达效果。切换路由后，拿到的count和title值都是更改后的。

![](https://img-blog.csdnimg.cn/61523e5c0b904f01bb8c9f088fa10555.gif)

 注：切换路由是没有问题，但页面刷新状态就会丢失。解决这个问题的话也很简单，搭配localStorage写一个插件就可以达到持久化。这里就不做演示了，自行研究一下。

## 陆、国际化

[Vite4 + Vue3 + ElementPlus 实现国际化包括表单校验(超详细)](https://blog.csdn.net/qq_19991931/article/details/129517219?spm=1001.2014.3001.5502 "Vite4 + Vue3 + ElementPlus 实现国际化包括表单校验(超详细)")

**我是Etc.End。如果文章对你有所帮助，能否帮我点个免费的赞和收藏😍。**

![](https://img-blog.csdnimg.cn/22c8b504f38f4dca92e4933f041cbd23.jpeg)

👇 👇 👇 👇 👇 👇 👇 👇 👇 👇 👇 👇