---
title: vue常用
date: 2018-06-01 16:09:38
tags: vue
---
# vue2 + elementUI


## vue子父类传值

### 父传子

* 子组件(接收方)在vue对象中，通过props属性声明，声明他期待获得的数据
	* props:["commentId"],

* 父组件(发送方)注册子组件，在使用子组件的时候，以键值对的方式传递给子组件，
	* :commentId="commentId"
	* 然后再data里面定义commentId的值，

<!-- more -->

### 子传父

* 子组件(发送方)以某种方式触发一个自定义事件，在事件中通过
	* $emit("listToChild",this.value)
* 父组件(接收方)在引用子组件标签中监听该自定义事件，并添加一个响应该事件的方法
	* v-on:listToChild="showMsgFun"
	* 在方法中调用此方法 showMsgFun(val){ console.log(val); }



## vue路由跳转 


发送方路由跳转方法时
```

	  clickRowValFun(data){
        this.$router.push({path:'/pending-particulars/'+data.id});
      },
```
在需要跳转的路由后面加上你需要传递的参数

设置路由时
```

	     {
          path: '/pending-particulars/:projectId',
          name: 'pendingParticulars',
          component: PendingParticulars
        },
```

接收方接收时
```

 	created(){
      this.projectId = this.$route.params.projectId;
    }
```

### vue+elementUI

当导航栏有折叠面板时使用更佳

##### 点击跳转代码示例：

```

	<el-menu  background-color="#293646" text-color="#fff" router :default-active="$route.path">
		<el-menu-item index="/work" class="nav_menu_item">
		  <i class="el-icon-refresh"></i>
		  <span class="title">工作台</span>
		</el-menu-item>
		<el-menu-item index="/financial-analysis" class="nav_menu_item">
		  <i class="el-icon-edit"></i>
		  <span class="title">统计分析</span>
		</el-menu-item>
		<el-submenu index="/bid-management">
	    <template slot="title">
	      <i class="el-icon-document"></i>
	      <span class="group_title">招投标管理</span>
	    </template>
	  	<el-menu-item-group>
	      <el-menu-item index="/bid-management" class="group_item">
	      	<div class="line"></div>
	      	<div class="circle"></div>
	     	<span class="item_title">招投标进程</span>
	      </el-menu-item>
	      <el-menu-item index="/license-management" class="group_item">
	     	 <div class="line"></div>
	     	 <div class="circle"></div>
	    	 <span class="item_title">证照管理</span>
	   	  </el-menu-item>
	    </el-menu-item-group>
    <el-menu>
```

1.要实现路由跳转，先要在el-menu标签上添加router属性，然后只要在每个el-menu-item标签内的index属性设置一下url即可实现点击el-menu-item实现路由跳转。

2.导航当前项，在el-menu标签中绑定  :default-active="$route.path",注意是绑定属性，不要忘了加“:”,当$route.path等于el-menu-item标签中的index属性值时则该item为当前项。

注意： 

* router模式：激活导航时以 index 字段作为 path 进行路由跳转。 
* default-active：当前激活的导航，以index字段为值。如果组件渲染前有默认值，则渲染后会按照该值来展开的导航。 
* unique-opened：保证只有一个子菜单展开。同样以index字段作为索引，如果某些菜单的index重复或者没有则会使该功能失效

##### 路由规则代码示例：

```

	//引入vue及vue-router
	import Vue from 'vue'
	import Router from 'vue-router'

	//引入跳转的项目地址
	import BidManagement from '../components/bidManagement/bidManagement.vue'
	import newProject from '../components/bidManagement/marketingDepartment/newProject/newProject.vue'
	import tempProject from '../components/bidManagement/marketingDepartment/newProject/tempProject.vue'
	import stayPickBid from '../components/bidManagement/businessDepartment/pickBid/stayPickBid.vue'
	import pickedBidOthers from '../components/bidManagement/businessDepartment/pickBid/pickedBidOthers.vue'

	Vue.use(Router)

	//设置路由跳转
	routes: [
	    {
	      path: '/',
	      redirect: '/bid-management'
	    },
	    {
	      path: '/bid-management',
	      name: 'BidManagement',
	      component: BidManagement
	    },
	    {
	      path: '/new-project',
	      name: 'newProject',
	      component: newProject
	    }
	]

```

## vuex

## axios 



## 生命周期钩子

声明周期钩子包含：

## 