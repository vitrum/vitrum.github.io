title: Nodejs项目中用到的用户权限管理系统
date: 2015-08-03 18:26:02
tags: nodejs, node, permission, 权限管理
---

权限管理，是管理系统中的常见组件。通常需要定义资源，把资源调配给用户，通过判断用户是否有权限增删改查来实现。

[ACL](https://en.wikipedia.org/wiki/Access_control_list)：Access Control List，访问控制列表，是比较流行的设计方式。通过吧用户和权限挂钩来实现。

[RBAC](https://en.wikipedia.org/wiki/Role-based_access_control)：Role Based Access Control，角色访问控制系统，是另一个实现思路。提炼出角色对象，把用户和角色绑定，角色来对应权限，角色和权限没有直接关联，对复杂的系统来说，更加容易管理。

##RBAC 



![wiki](https://upload.wikimedia.org/wikipedia/en/c/c3/RBAC.jpg)

![](http://dl.iteye.com/upload/attachment/425543/d2573c4d-dca7-380f-b2fc-6cda19d6eaf5.jpg)


##资料


[扩展RBAC用户角色权限设计方案](http://rongxh2010.iteye.com/blog/930648)

[基于AOP实现权限管理：访问控制模型RBAC和ACL](http://blog.csdn.net/tch918/article/details/18449043)

[基于RBAC模型的权限管理系统的设计和实现](http://blog.csdn.net/gxp/article/details/6741652)


## node 实现

源自：[这篇](https://gist.github.com/facultymatt/6370903)

https://github.com/seeden/rbac
Hierarchical Role Based Access Control for NodeJS

https://github.com/djvirgen/virgen-acl
Simple and elegant, create your own checks. No middleware? 

https://github.com/OptimalBits/node_acl
Use as middleware, create your own roles and access. Great choice. 

https://github.com/tschaub/authorized
Similar to connect roles... but a bit more robust? you can create roles and action, and associate many roles with that action

https://github.com/scottkf/ability-js
Like canCan for rails. This is a traditional controller / function type permission system. May be too abstract. 

https://github.com/dresende/node-roles
More traditional setRole() hasRole() based checking. Last activity 2 years ago. 

https://github.com/carlos8f/node-relations 
Natural language style roles. Looks very promising and is in active development

https://github.com/ForbesLindesay/connect-roles
Simple and closer to action / natural language based. Requires writing your own checks for each. 

https://github.com/ajlopez/SimplePermissions
Maybe too simple? Makes sense for assigning roles but then its hard to check against roles! 

https://npmjs.org/package/entitlement
Not ideal but here for reference sake.

## Mongoose Field Access Control

https://github.com/codedoctor/mongoose-plugins-accessible-by Set access per field of mongoose Schema. Not supported or maintained, and noted as not a perfect fit in all cases... but worth considering as a simple way to control access to fields. 



