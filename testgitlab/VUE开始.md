

# 1

## 1.1

### 	1.1.1

#### 	mvvm模型 

 		1.M:模型(Model):data中的数据

​		2.V:视图(view):模板代码

​		3.VM视图模型(ViewModel):Vue的实例

#### 	观察发现：

​		1.data中的所有属性 最后都出现在了VM上

​		2.vm身上所有的属性，以及Vue原型上的所有属性，在Vue模板中都可以直接使用

### 	1.1.2

#### 		事件的基本使用

​				1. 使用v-on:xxx 或者 @xxx  绑定事件 其中xxx是事件名称

​				2.事件的回调需要配置在methods对象中，最终会在vm上；

​				3.methods中配置的函数不要用箭头函数！！！ 否则this就不是vm

​				4.methods中配置的函数，都是被Vue所管理的函数this的指向是vm

​					或者组件实例对象；

​				5.@click=“demo” 和@click=“demo($event)” 效果一致，但是后者可以传参；

​				6. 

​				

### 	1.1.3

### 	Vue中的事件修饰符

​		1.prevent：阻止默认的事件（常用）

​		2.stop： 阻止事件的冒泡（常用）

​		3.once： 事件只触发一次（常用）

​		4.capture： 使用事件的捕获模式

​		5 .self ：只有事件对象（event.target）是当前的元素时才会触发事件

​		6.passive：事件的默认行为立即执行，无需等待事件回调执行完毕



### 1.2.1

### Vue中常用的按键别名：

​	回车 => enter

​	删除 => delete(捕获“删除” 和 “退格”键)

​	退出 => esc

​	空格 => space

​	换行 => tab

​	上 => up

​	下 => down

​	左 => left

​	右 => right

2.未提供别名的按键可以使用按键原始的key值去绑定，但是注意要转为kabab-case(短横线命名)

3.系统修饰符(用法特殊)：ctrl、alt、shift、meta、capslock等

​	(1).配合keyup使用：按下修饰符的同时，再按下其他键，随后释放其他键，事件才会被触发

​	(2).配合keydown使用：正常触发事件。

4.也可以使用keycode去指定具体的按键(不推荐)



### 1.2.2

组件的自定义事件
	1.一种组件之间的通信方式，适用于 子组件 ===> 父组件

​	2.

​	3.绑定自定义事件：

​			1.第一种方式：在父组件中<Demo @atguigu="test"></Demo> 或者  <Demo v-on:atguigu="test"></Demo>

​			2.第二种方式：在父组件中：

​		<Demo ref="demo">

​				....

​				mounted(){

​					this.$refs.xxx.$on('atguigu', this.test)

​			}

​			</Demo>

​		3.想让自定义事件只触发一次可以使用once修饰符 或者 $once方法

​		4.触发自定义事件this.$emit('atguigu', 数据)

​		5.解绑自定义事件 this.$off('atguigu')

​		6.组件上可以绑定原生的Dom事件 ，需要使用native 修饰符

​		7.注意通过this.$refs.xxx.$on('atguigu',回调)绑定自定义事件 回调要么配置在methods中 要么用箭头函数，否则 this的指向会出现问题

​		

​		

## 2.1

### 	2.1.1 计算属性

​			1. 定义：要用的属性不存在，要通过已有属性计算得来

​			2. 借助了 Object.defineproperty 方法提供的 geTter 和 setter

​			3. getter 函数什么时候更新

​				(1). 初次读取时 会执行一次。

​				(2). 当依赖的数据发生变化时会再次被调用

​			4.优势：与method相比内部有缓存机制效率更高、调试方便。

​			5.备注：

​				1.计算属性最终会出现在 vm 上，直接读取使用即可

​				2.如果计算属性被修改，那必须写set去响应数据，并且set中要引起计算时依赖的数据发生变化

​		

## 3.1.Vue-cli开始

​	一般来说vue脚手架只用最新版本，新的版本会向下兼容，

​	Vue版本

​	Vue 1.X

​	Vue 2.X  ====>>> 主流应用

​	Vue 3.X

Vue脚手架的版本

​	Vue-cli 1.X

​	Vue-cli 2.X

​	Vue-cli 3.X

​	Vue-cli 4.X  ===> 新的版本会向下兼容



### 3.1.1 说明

​		1.Vue脚手架是Vue官方提供的标准化开发工具（开发平台）

​		2.最新的版本是4.X

​		3.官方文档链接：https://cli.vuejs.org/zh/

### 3.1.2具体的步骤

​		第一步(仅仅是第一次执行)：全局的安装@vue/cli。

​				npm install -g @vue/cli   === >(默认会安装最新版本的脚		手架)

​		第二步：切换到想要创建项目的目录，然后使用命令创建项目

​				vue create XXX

​		第三步：启动项目

​				npm run server

​		备注：

​		1.下载缓慢建议配置国内的镜像：npm淘宝镜像

​			npm config set registry https://registry.npm.taobao.org

​		2.Vue的脚手架隐藏了所有webpack相关的配置，若想查看具体的配置请执行: 

​			vue inspect > output.js 



脚手架的文件结构

​	node_module 项目依赖

​	public

​			--favicon.ico  ：页签的图标

​			--index.html  ：主页面

​	src

​		--assets ：静态资源

​				logo.png

​		--components ：存放组件

​				HelloWorld.vue

​		-- --App.vue ：汇总所有的组件

​		-- --main.js：入口文件

​		.gitignore：git版本管制忽略的配置

​		babel.config.js： bable的配置文件

​		package.json：应用包的配置文件

​		README.md：应用描述文件

​		package-lock.json 包版本的控制文件

### 3.1.3 关于不同版本的Vue:

​		1.vue.js与vue.runtime.xxx.js的区别

​			(1).vue.js是完整版的Vue,包含：核心功能+模块解析器

​			(2)vue.runtime.js是运行版本的Vue,其中只包含：Vue的核心功能；

​				没有模板解析器。

​		2.因为vue.runtime.xxx.js，没有模板解析器，所以不能使用template配置项，需			要使用render函数接收到的			createElement函数去指定具体内容。

### 3.1.4

​		vue.config.js是对webpack的核心配置补充，是一个可选的配置文件，如果项目的 (和package.json同级的）根目录中存在这个文件那么他会被@vue/cli-service自动加载。也可以使用package.json中的vue字段，但是注意这种写法要严格遵照JSON的格式来写

​		主要是由于官方不允许修改其默认的核心配置，用户只可以在  vue.config.js  自定义配置信息，

覆盖掉原先的默认配置 

### 3.1.5



### 3.1.6



### 3.1.7

​		

### 3.1.7

## 4.1 ref属性

​		1.被用来给元素和子组件注册引用信息(id替代者)

​		2.应用在HTML标签上获取的是真实Dom, 应用在组件上获取的是组件实例对象(vc)

​		3.使用方式:

​				打标识：原生Dom写法 <h1 ref="xxx"></h1> 或者 组件写法： <School ref="xxx"></School>

​		获取：this.$refs.xxx

## 5.1

### 	5.1.1 

#### 			关于prop中的配置声明

​			1.

​			2. prop中的声明都是只读的, vue底层会监测开发人员对props的修改，如果进行				了修改就会发出警告，如果确实业务需求修改，那么请复制props的内				容到data中一份，然后去修改data中的数据。

### 	5.1.2

​			1.

​			2.

​			3.

​			4.	

​			5.

​			

### 	5.1.3

​		

###     5.1.4

​		

### 	5.1.5



# 	6

## 	 6.1 混入

​			

### 	  6.1.1

​		功能：可以把多个组件共用的配置提取成一个混入对象

​		使用方式：

​			第一步定义混合，例如:

​				{

​					data(){

​						a: "XXX"

​					},

​					method:{

​						a(){}

​						b(){}

​					},

​					prop:{

​					}

​					........

​				}

​				第二步使用混入，例如:

​					import XXX from "../mixin";

​					(1)全局混入：Vue.mixin(XXX );

​					(2)局部混入：mixins:['XXX '];

### 		6.1.2

​	



#### vue-router

​	npm init --yes  ===> 初始化 

​	npm install vue-router -S ===>  安装 vue-router

​	

​		

