title: Main Tank Helper
id: 635
categories:
  - Lua in WOW
date: 2005-05-30 03:12:03
tags:
---

<div id="msgcns!9697D6160EFEBC17!129" class="bvMsg">

这个Addon添加了一个小巧的可移动框体在屏幕上能显示你的队员正准备攻击的怪物。如果只有一个玩家攻击这个怪物那这个框体显示绿色并且显示出正在攻击的怪物名称。如果另一个队员也使用近战伤害了这个怪物那这个框体就会显示红色并且显示攻击该怪物的玩家的所有名字

![](http://www.wowui.cn/upload/20054263224516.jpg)

This addon adds a small movable bar to your UI that shows who in your party is being attacked by mobs. If the player is the only party member being hit (melee) the bar is green and shows the names of mobs hitting the character. If another member of the party is taking melee damage the bar turns red and shows the party member's name and what is hitting them.

This addon was designed to help tanks easier tell if they have complete aggro on a group of mobs and alert them when a party member is taking damage.

-- v1.1 - 4/24/05
-- * settings such as on/off and enemy names on/off are now saved across sessions
-- * added chat commands /mth onoffenemy onenemy off
-- * resized window to half it's original size &amp; reduced font size

-- Main Tank Helper 
-- Faylin - [www.wow-ni.com](http://www.wow-ni.com)

-- v1.1 - 4/24/05
-- * settings such as on/off and enemy names on/off are now saved across sessions
-- * added chat commands /mth on|off|enemy on|enemy off
-- * resized window to half it's original size &amp; reduced font size

-- v1.0 - 4/21/05

function MTHelper_OnLoad()

 RegisterForSave(&quot;mthenabled&quot;);
 RegisterForSave(&quot;mthenemy&quot;);

 this:RegisterEvent(&quot;PLAYER_REGEN_DISABLED&quot;);
 this:RegisterEvent(&quot;PLAYER_REGEN_ENABLED&quot; );
 this:RegisterEvent(&quot;UNIT_COMBAT&quot;);
 this:RegisterEvent(&quot;CHAT_MSG_COMBAT_CREATURE_VS_SELF_HITS&quot;);
 this:RegisterEvent(&quot;CHAT_MSG_COMBAT_CREATURE_VS_SELF_MISSES&quot;);
 this:RegisterEvent(&quot;CHAT_MSG_COMBAT_CREATURE_VS_PARTY_HITS&quot;);
 this:RegisterEvent(&quot;CHAT_MSG_COMBAT_CREATURE_VS_PARTY_MISSES&quot;);
 this:Hide();

 SLASH_MTHELPER1 = &quot;/mthelper&quot;;
 SLASH_MTHELPER2 = &quot;/mth&quot;;
 SlashCmdList[&quot;MTHELPER&quot;] = function (msg)
  MTHelper_SlashCmd(msg);
 end

end

function MTHelper_SlashCmd(arg)

  if ( arg == &quot;&quot; ) then
 DEFAULT_CHAT_FRAME:AddMessage(&quot;Use: /mth on|off|enemy on| enemy off&quot;);
  end

  if ( arg == &quot;on&quot; ) then
 mthenabled = 1;
 DEFAULT_CHAT_FRAME:AddMessage(mthenabled..&quot; - MTHelper *ON*&quot;);
  end

  if ( arg == &quot;off&quot; ) then
 mthenabled = 0;
 DEFAULT_CHAT_FRAME:AddMessage(mthenabled..&quot; - MTHelper *OFF*&quot;);
  end

  if ( arg == &quot;enemy on&quot; ) then
 mthenemy = 1;
 DEFAULT_CHAT_FRAME:AddMessage(&quot;MTHelper: Showing enemy names&quot;);
  end

  if ( arg == &quot;enemy off&quot; ) then
 mthenemy = 0;
 DEFAULT_CHAT_FRAME:AddMessage(&quot;MTHelper: Hiding enemy names&quot;);
  end

end

function MTHelper_OnEvent(event)
  if ( event == &quot;PLAYER_REGEN_DISABLED&quot; ) then
   if ( mthenabled == 0 ) then
    return;
   else
    this:Show();
    return;
   end
  end
  if ( event == &quot;CHAT_MSG_COMBAT_CREATURE_VS_SELF_HITS&quot; or event == &quot;CHAT_MSG_COMBAT_CREATURE_VS_SELF_MISSES&quot; ) then
   textll = arg1;
   if string.find(textll, &quot;hits&quot;) then
    hitpos = string.find(textll, &quot;hits&quot;);
    MTHelperBackdrop:SetBackdropColor(0, 1, 0, .75);
   elseif string.find(textll, &quot;crits&quot;) then
    hitpos = string.find(textll, &quot;crits&quot;);
    MTHelperBackdrop:SetBackdropColor(0, 1, 0, .75);
   elseif string.find(textll, &quot;attacks&quot;) then
    hitpos = string.find(textll, &quot;attacks&quot;);
    MTHelperBackdrop:SetBackdropColor(0, 1, 0, .75);
   elseif string.find(textll, &quot;misses&quot;) then
    hitpos = string.find(textll, &quot;misses&quot;);
    MTHelperBackdrop:SetBackdropColor(0, 1, 0, .75);
   end

   enemy = string.sub(textll, 1, hitpos - 2);
   ttarget:SetText(enemy)
   return;
  end
  if ( event == &quot;CHAT_MSG_COMBAT_CREATURE_VS_PARTY_HITS&quot; or event == &quot;CHAT_MSG_COMBAT_CREATURE_VS_PARTY_MISSES&quot; ) then
   if ( mthenemy == 1 ) then
    textll = arg1;
    --all victim searches have 1 extra added on for the space
    if string.find(textll, &quot;hits&quot;) then
     hitpos = string.find(textll, &quot;hits&quot;);
     victim = string.sub(textll, hitpos + 5);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;crits&quot;) then
     hitpos = string.find(textll, &quot;crits&quot;);
     victim = string.sub(textll, hitpos + 6);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;attacks&quot;) then
     hitpos = string.find(textll, &quot;attacks&quot;);
     victim = string.sub(textll, hitpos + 9);
     -- have to +9 because there is a . after &quot;attacks&quot;
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;misses&quot;) then
     hitpos = string.find(textll, &quot;misses&quot;);
     victim = string.sub(textll, hitpos + 6);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    end

    enemy = string.sub(textll, 1, hitpos - 2);
    namepos = string.find(victim, &quot; &quot;);
    victim = string.sub(victim, 1, namepos);
    ttarget:SetText(victim..&quot; - &quot;..enemy)
    return;
   else
    textll = arg1;
    --all victim searches have 1 extra added on for the space
    if string.find(textll, &quot;hits&quot;) then
     hitpos = string.find(textll, &quot;hits&quot;);
     victim = string.sub(textll, hitpos + 5);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;crits&quot;) then
     hitpos = string.find(textll, &quot;crits&quot;);
     victim = string.sub(textll, hitpos + 6);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;attacks&quot;) then
     hitpos = string.find(textll, &quot;attacks&quot;);
     victim = string.sub(textll, hitpos + 9);
     -- have to +9 because there is a . after &quot;attacks&quot;
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    elseif string.find(textll, &quot;misses&quot;) then
     hitpos = string.find(textll, &quot;misses&quot;);
     victim = string.sub(textll, hitpos + 6);
     MTHelperBackdrop:SetBackdropColor(1, 0, 0, .75);
    end
    namepos = string.find(victim, &quot; &quot;);
    victim = string.sub(victim, 1, namepos);
    ttarget:SetText(victim);
    return;
   end
  end
  if ( event == &quot;PLAYER_REGEN_ENABLED&quot; ) then
   this:Hide();
   return;
  end
  if ( event == &quot;UNIT_COMBAT&quot; ) then
   -- MTHelper_Update();
   return;
  end
end
</div>