## 方法/步骤

1.  使用xshell连接上安装nexus的服务器，使用find / -name 'security.xml'命令查找nexus的安全配置文件位置![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112127-33f90a40-5c95-4e40-8556-b8309dbd61a2.png)
2.  找到nexus的security.xml文件之后，使用vi security.xml进入文件，使用“/admin”查找管理员用户节点![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112099-99811731-99cc-49bc-997a-3d66f6d85265.png)
3.  然后将<password>密码节点使用"f865b53623b121fd34ee5426c792e5c33af8c227"字符串替换![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112117-fc9f578b-fb28-4243-be2b-efefc77f717f.png)
4.  替换完成之后，使用:wq对文件进行保存退出。找到nexus的bin目录，重启nexus服务"./nexus restart",重启完成之后admin用户的密码就重置成了admin123了![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112128-f03bc7bd-2ed1-4f2e-9a79-3d50ffa4c405.png)
5.  另一种方法，我们还可以通过修改用户角色来获取管理员权限，然后通过匿名用户修改管理员密码，还是使用vi命令修改security.xml文件，找到anonymous的权限配置节点，添加<role>nx-admin</role>![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112136-9e752164-ff4e-40aa-89a6-f1963f2e4db0.png)
6.  然后重启nexus服务，这个时候打开nexus前端页面，在没有登录的情况下，发现之前看不到的菜单都可以看到了。和管理员登录状态下看到的一样，在页面选择security菜单的users，重置密码，密码设置之后，再把上面添加的<role>nx-admin</role>节点删除，再重启服务![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135112921-2f305450-993b-4ec8-818b-524c6165993a.png)![](https://cdn.nlark.com/yuque/0/2022/png/25612577/1654135113469-5f8fb45d-5169-438f-bd13-f76fb1e8cbcc.png)END

## 注意事项

-   第二种方法给匿名用户添加的nx-admin，在修改完密码之后一定要把刚刚添加的角色删除，再重启，否则任何人都可以修改nexus服务器配置和文件了