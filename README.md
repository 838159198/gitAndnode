# 学习笔记
跟着王哥的学习angular之路，防后人掉坑a

# nodejs安装脚手架

npm --registry=https://registry.npm.taobao.org --cache=$HOME/.npm/.cache/cnpm --disturl=https://npm.taobao.org/dist --userconfig=$HOME/.cnpmrc install -g @angular/cli

#python下载地址

https://www.python.org/ftp/python/2.7.14/python-2.7.14.msi

#安装.netframework 2.0 SDK

http://dlsw.baidu.com/sw-search-sp/soft/2c/24588/Framework2.0SDK.1393828197.exe


# node请求php后台跨域头部问题


header('Access-Control-Allow-Origin: *');

header("Access-Control-Allow-Headers: Content-Type, Access-Control-Allow-Headers, Authorization, X-Requested-With");

header('Access-Control-Allow-Methods: POST,GET,HEAD,OPTIONS,PUT,DELETE,TRACE,CONNECT');

# git下载安装

1,下载地址 https://git-scm.com/downloads

2,安装教程 https://jingyan.baidu.com/article/ae97a646fb29ffbbfd461d1f.html

3,$ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"

4,生成pub_ssh   $ ssh-keygen -t rsa -C "email@example.com"

5，git pull 远程主机名 远程分支：本地分支

6，git push 远程主机名 本地分支：远程分支、

7，git log 查看历史提交 

8，git reset --hard commit_id  版本退回

9，git remote add sp git@gitee.com:zhanglibin/spoa2.git 添加远程分支。可以添加好多分支。

# git远程分支合并

1，git fetch origin 

2, git merge origin/master 合并mater分支，此时在master分支，需要合并 b20180115分支，git merge origin/b20180115

3, 然后再解决冲突

## 组件弹窗

    <div style="background-color:aquamarine;position:fixed;top:0px;bottom:0px;left:0px;right:0px;z-index:1000">
    <div style="position:relative;margin:30px auto;background-color:blueviolet;width:500px;height:200px;overflow: auto">
    </div>
    </div>

# angular笔记

1，跳转都封装在,以route-service.ts结尾的文件里，里面封装了跳转路径。

2，set ComSpec=

3，模板引用变量  

4，事件  keyup click  blur  keyup.enter

5, 创建模型类

6，[(ngModel)]="name"  双向绑定

7，ngForm指令  ngForm.reset();

8, super()用法。继承父类super调用父类的属性和方法。

9，promise()用法？

10 json 地址  http://www.runoob.com/try/angularjs/data/sites.php

11，**http用法和创建服务**

1. [创建service引入 injectable和http和import 'rxjs/add/operator/map';](http://https://www.w3cschool.cn/angular/angular-4wgi2530.html)
2. 在组件中引入service 。constructor(private appService: AppSservice) {    
  }
 ngOnInit(){
  this.appService.subscribe(data=>{if(data){console.log(data);}})
 }
3. 在模块中providers[]引入

12，**路由**

1. 在模块中引入 import {RouterModule, Routers} from '@angular/router',在imports中写入RouterModule.forRoot()
2. 在appModule模块中 写入 export const ROUTERS: Routers = [
        {path:'', pathMatch:'full',redirectTo:'user'},
        {path:'user', component: 'UserComponent'}
    ];

## 3. 在 app.component.html中写入  
    <nav>
        <a routerLink="/">首页</a>
        <a routerLink="/user">我的</a>
    </nav>
此时点击url在地址栏中改变，页面不会被加载。当我们在app.component.html中加上<router-outlet></router-outer>,此时点击对应的页面的内容会显示在这个标签里面。

点击按钮，根据路由，找到相应的组件，该组件在<router-outlet></router-outlet>中显示。

## 4.当url中有参数时。比如

    <nav>
        <a routerLink="/">首页</a>
        <a routerLink="/user/111">我的</a>
    </nav>

   

-appModule中修改const ROUTERS: Routers = [{path:'user/:id',component:'Usercomponent'}];

-在UserComponent中引入 import { ActivatedRoute } from '@angular/router';在NgOnInit中加上一句 this.route.params.subscribe((params) => this.number= params.id);

此时number就是url中的参数

## 5.子url子路由

以user为例，有useradd和usermodify两个子页面。

在appmodule中修改  **export const ROUTERS:Routers=
[
    {path: 'user', component: 'UserComponent',children:[
       {path:'useradd', component: 'UseraddComponent'},
       {path: 'usermodify', component: 'UsermodifyComponent'}
      ]}

];**

## 6.navigate跳转

this.router.navigate(['/app']);

13， **表单**

[详细表单用法链接](https://segmentfault.com/a/1190000009652980)

14，[title]="'username'" 等价于  title="username"       [title]="username"  等价于  bind-title="username"
  
 