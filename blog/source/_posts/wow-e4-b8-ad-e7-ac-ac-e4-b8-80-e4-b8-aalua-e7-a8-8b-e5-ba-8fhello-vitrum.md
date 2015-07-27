title: 'wow 中第一个LUA程序,HELLO VITRUM'
id: 641
categories:
  - 计算机与 Internet
date: 2005-05-16 06:16:40
tags:
---

<div id="msgcns!9697D6160EFEBC17!114" class="bvMsg">function hello_world_initialize() 
-- add our very first chat command! 
SlashCmdList[&quot;HELLOW&quot;] = hello_world_command; 
SLASH_HELLOW1 = &quot;/hellow&quot;; 
SLASH_HELLOW2 = &quot;/hw&quot;; 
end 

function hello_world_command(msg) 
-- this function handles our chat command 
message(msg); 
end 
 </div>