> [!IMPORTANT]
> Make sure you've set up the **[variables](/Codes/Welcome-System/variables.md)** and created the **[!welcome-setup](/Codes/Welcome-System/!welcome-setup.md)** command

> [!NOTE]
> Press the copy button to immediately copy all the code at once
# Command Script


<details><summary>Click to view code</summary>

  > ⚠️ Script Language: BDScript 2
  
  ```
$nomention
$textSplit[$customID;_]
$if[$splitText[1]==wlc-toggle]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set;$botID]]
$if[$json[e]==0]
$jsonSetString[e;1]
$setUserVar[wlc-set;$jsonStringify;$botID]
$else
$jsonSetString[e;0]
$setUserVar[wlc-set;$jsonStringify;$botID]
$endif
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$c[0==false, 1==true]
$title[Welcome System Setup]
$description[Setup the welcome system on **$serverName[$guildID]**
Welcome module: $trimSpace[$if[$json[e]==0] Disabled $else Enabled $endif]]
$addField[Welcome Channel;The channel where the **Welcome Message** will be sent]
$addField[Welcome Message;The welcome message, which supports embed and is fully customizable]
$addField[Additional Features;Other features such as autoroles, ignore bots, dm user, etc]
$footer[Welcome module: $trimSpace[$if[$json[e]==0] 🔴 disabled $else 🟢 enabled $endif]]
$color[#2E9CFF]
$addButton[no;wlc-toggle_$authorID;$if[$json[e]==0] Enable $else Disable $endif;$if[$json[e]==0] success $else danger $endif]
$addButton[no;wlc-view_$authorID;View Setup;secondary]
$addButton[no;wlc-reset_$authorID;Reset;danger]
$newSelectMenu[wlc-setup-uwu;1;1]
$addSelectMenuOption[wlc-setup-uwu;Welcome Channel;wlc-chan_$authorID;Interact to set/edit the Welcome Channel]
$addSelectMenuOption[wlc-setup-uwu;Welcome Message;wlc-msg_$authorID;Interact to set/edit the Welcome Message]
$addSelectMenuOption[wlc-setup-uwu;Additional Features;wlc-misc_$authorID;Interact to view the Additional Features page]
$endif
$endif
$if[$splitText[1]==wlc-view]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$title[Welcome System: Setup View (System)]
$description[Welcome Module: $trimSpace[$if[$json[e]==0] Disabled $else Enabled $endif]]
$addField[Welcome Channel;$if[$getServerVar[wlc-chan]==] _No welcome channel has been set yet._ $else <#$getServerVar[wlc-chan]> \`($getServerVar[wlc-chan])\` $endif]
$newSelectMenu[wlc-view-prop;1;1;Select a system property]
$addSelectMenuOption[wlc-view-prop;Welcome Message;wlc-view-msg_$authorID;View the setup of the Welcome Message page]
$addSelectMenuOption[wlc-view-prop;Additional Features;wlc-view-af_$authorID;View the setup of the Additional Features page]
$addButton[no;wlc-back_$authorID_main;Go Back;secondary]
$color[#2e9cff]
$endif
$endif
$textSplit[$message;_]
$if[$splitText[1]==wlc-view-msg]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$title[Welcome System: Setup View (Message)]
$addField[Content;$trimSpace[$if[$json[msg;0]==] _Content property not set_ $else $json[msg;0] $endif]]
$addField[Author;$trimSpace[$if[$json[msg;1]==] _Author property not set_ $else $json[msg;1] $endif]]
$addField[Author Icon;$trimSpace[$if[$json[msg;2]==] _Author Icon property not set_ $else $json[msg;2] $endif]]
$addField[Title;$trimSpace[$if[$json[msg;3]==] _Title property not set_ $else $json[msg;3] $endif]]
$addField[Title URL;$trimSpace[$if[$json[msg;4]==] _Title URL property not set_ $else $json[msg;4] $endif]]
$addField[Description;$trimSpace[$if[$json[msg;5]==] _Description property not set_ $else $json[msg;5] $endif]]
$addField[Color;$trimSpace[$if[$json[msg;6]==] _Color property not set_ $else $json[msg;6] $endif]]
$addField[Footer;$trimSpace[$if[$json[msg;7]==] _Footer property not set_ $else $json[msg;7] $endif]]
$addField[Footer Icon;$trimSpace[$if[$json[msg;8]==] _Footer Icon property not set_ $else $json[msg;8] $endif]]
$addField[Thumbnail;$trimSpace[$if[$json[msg;9]==] _Thumbnail property not set_ $else $json[msg;9] $endif]]
$addField[Image;$trimSpace[$if[$json[msg;10]==] _Image property not set_ $else $json[msg;10] $endif]]
$color[#406ecf]
$newSelectMenu[wlc-view-prop;1;1;Select a system property]
$addSelectMenuOption[wlc-view-prop;Welcome System;wlc-view-sys_$authorID;View the setup of the Welcome System page]
$addSelectMenuOption[wlc-view-prop;Welcome Message;wlc-view-msg_$authorID;View the setup of the Welcome Message page]
$addSelectMenuOption[wlc-view-prop;Additional Features;wlc-view-af_$authorID;View the setup of the Additional Features page]
$endif
$endif
$if[$splitText[1]==wlc-view-af]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeComponent[wlc-back_$authorID_main]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$var[mins;$replaceText[$json[del;mins];#;]]
$var[secs;$replaceText[$json[del;secs];#;]]
$var[formatted;$trimSpace[$if[$var[mins]>0] $var[mins] minute(s) $endif]]
$var[formatted;$trimSpace[$if[$var[formatted]!=] $if[$var[secs]>0] $var[formatted] and $var[secs] second(s) $endif $else $if[$var[secs]>0] $var[secs] second(s) $endif $endif]]
$var[formatted;$trimSpace[$if[$var[formatted]==] Never $else $var[formatted] $endif]]
$var[ar;$replaceText[<@&$replaceText[$replaceText[$jsonJoinArray[ar;$url[decode;%0A]];#;];$url[decode;%0A];> <@&]>;<@&>;]]
$title[Welcome System: Setup View (Additional Features)]
$description[>>> **DM Member:** $json[dm]
**Auto Delete:** $var[formatted]
**Trigger Type:** $json[tt]]
$addField[Autoroles;$trimSpace[$if[$var[ar]==] _Autorole feature not set_ $else $var[ar] $endif]]
$color[#2e9cff]
$endif
$endif
$if[$splitText[1]==wlc-view-sys]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$title[Welcome System: Setup View (System)]
$description[Welcome System: $trimSpace[$if[$json[e]==0] Disabled $else Enabled $endif]]
$addField[Welcome Channel;$if[$getServerVar[wlc-chan]==] _No welcome channel has been set yet._ $else <#$getServerVar[wlc-chan]> \`($getServerVar[wlc-chan])\` $endif]
$newSelectMenu[wlc-view-prop;1;1;Select a system property]
$addSelectMenuOption[wlc-view-prop;Welcome Message;wlc-view-msg_$authorID;View the setup of the Welcome Message page]
$addSelectMenuOption[wlc-view-prop;Additional Features;wlc-view-af_$authorID;View the setup of the Additional Features page]
$addButton[no;wlc-back_$authorID_main;Go Back;secondary]
$color[#2e9cff]
$endif
$endif

$nomention
$textSplit[$message;_]
$if[$splitText[1]==wlc-chan]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$newModal[wlc-chan-modal;Welcome Channel]
$addTextInput[wlc-chan-inp;short;Welcome Channel;1;100;no;$if[$getServerVar[wlc-chan]!=] $channelName[$getServerVar[wlc-chan]] $endif;Input a Channel Name/ID
Input nothing to reset]
$endif
$endif
$if[$customID==wlc-chan-modal]
$ephemeral $removeAllComponents
$var[chan;$input[wlc-chan-inp]]
$if[$var[chan]==]
$title[Channel Reset]
$description[The welcome channel has been successfully reset.]
$color[#2e9cff]
$setServerVar[wlc-chan; ]
$elseif[$findChannel[$var[chan]]==]
$title[Channel Not Found]
$description[Could not find the channel you provided
double-check the Name/ID and try again]
$color[#2e9cff]
$elseif[$channelType[$findChannel[$var[chan]]]!=text]
$title[Invalid Channel Type]
$description[The channel you provide must be of the type **Text**]
$color[#2e9cff]
$else
$if[$getServerVar[wlc-chan]==]
$var[msg;Successfully set the welcome channel to <#$findChannel[$var[chan]]> \`($findChannel[$var[chan]])\`]
$else
$var[msg;Successfully updated the welcome channel
**Before:** <#$getServerVar[wlc-chan]> \`($getServerVar[wlc-chan])\`
**After:** <#$findChannel[$var[chan]]> \`($findChannel[$var[chan]])\`]
$endif
$title[Welcome System: Channel]
$description[$var[msg]]
$color[#2e9cff]
$setServerVar[wlc-chan;$findChannel[$var[chan]]]
$endif
$endif
$textSplit[$message;_]
$if[$splitText[1]==wlc-msg]
$defer
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$defer
$title[Welcome System: Welcome Message]
$description[Use the select-menu below to set the properties your welcome message will have]
$addField[Tags/Preview/Reset;You can press the **View Tags** button to view the available tags you can use on your welcome message

You can press the **Preview** button to see and test your Welcome Message
> ⚠️ You must preview after setting up a property, to make sure everything is alright with no errors

You can press the **Reset** button to reset all the properties of your Welcome Message
> ⚠️ This action is irreversible, no recover can be made on accidental press.]
$removeAllComponents
$addButton[no;wlc-back_$authorID_main;Go Back;secondary]
$addButton[no;wlc-msg-tags_$authorID;View Tags;primary]
$addButton[no;wlc-msg-preview_$authorID;Preview;success]
$newSelectMenu[wlc-msg-set-menu;1;1;View properties]
$addSelectMenuOption[wlc-msg-set-menu;Content;wlc-msg-cont_$authorID;set/edit the content message (discord normal message)]
$addSelectMenuOption[wlc-msg-set-menu;Author;wlc-msg-author_$authorID;set/edit the embed's author/author icon]
$addSelectMenuOption[wlc-msg-set-menu;Title;wlc-msg-title_$authorID;set/edit the embed's title/title URL]
$addSelectMenuOption[wlc-msg-set-menu;Description;wlc-msg-desc_$authorID;Set/edit the embed's description]
$addSelectMenuOption[wlc-msg-set-menu;Color;wlc-msg-color_$authorID;set/edit the embed's color]
$addSelectMenuOption[wlc-msg-set-menu;Footer;wlc-msg-footer_$authorID;set/edit the embed's footer/footer icon]
$addSelectMenuOption[wlc-msg-set-menu;Thumbnail;wlc-msg-thumb_$authorID;set/edit the embed's thumbnail]
$addSelectMenuOption[wlc-msg-set-menu;Image;wlc-msg-img_$authorID;set/edit the embed's image]
$addButton[yes;wlc-msg-reset_$authorID;Reset;danger]
$color[#2E9CFF]
$endif
$endif


$nomention
$textSplit[$customID;_]
$if[$splitText[1]==wlc-msg-tags]
$defer
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$ephemeral $removeAllComponents
$title[Welcome Message: Tags List]
$description[List of tags you can use on your Welcome Message
Example: {member(name)} returns $username[$randomText[$botID;$authorID]]]
$addField[Member Based Tags;>>> \`\`\`
{member(name)} member's username
{member(displayName)} member's displayName
{member(id)} member's user ID
{member(tag)} member's username#0000
{member(mention)} returns member mention (@member)
{member(avatar)} member's avatar URL
{member(creation)} member's account relative creation
\`\`\`]
$addField[Guild Based Tags;>>> \`\`\`
{guild(name)} server's name
{guild(id)} server's ID
{guild(icon)} server's icon URL
{guild(members)} total count of members
{guild(membersOrd)} ordinal total count of members
\`\`\`]
$color[#2e9cff]
$endif
$endif
$if[$splitText[1]==wlc-msg-reset]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$ephemeral $removeAllComponents
$title[Welcome Message: Reset]
$description[> ⚠️ As stated previously, ALL the properties of your welcome message will be reset, no recover can be made on accidental press.

**Are you ABSOLUTELY sure you want to reset?**]
]
$color[#2e9cff]
$addButton[no;wlc-msg-reset-1_$authorID;Confirm;success]
$addButton[no;wlc-msg-reset-2_$authorID;Nevermind;secondary]
$endif
$endif
$endif
$if[$splitText[1]==wlc-msg-reset-1]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$title[Action Confirmed]
$description[All properties of your welcome message has been reset]
$color[#2e9cff]
$jsonParse[$getUserVar[wlc-set;$botID]]
$jsonSet[msg;["", "", "", "", "", "", "", "", "", "", ""\]]
$setUserVar[wlc-set;{"msg": ["", "", "", "", "", "", "", "", "", "", ""\], "e": "$json[e]"};$botID]
$endif
$endif
$if[$splitText[1]==wlc-msg-reset-2]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$title[Action Forgotten]
$description[_let's just forget what just happened._]
$color[#2e9cff]
$endif
$endif
$textSplit[$customID;_]
$if[$splitText[1]==wlc-reset]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$ephemeral $removeAllComponents
$title[Welcome System: __RESET__]
$description[> ⚠️ ALL the properties of the welcome system will be reset to their default values
this includes:
- Welcome System
- Welcome Message
- Additional Features

**Are you ABSOLUTELY sure you want to reset? This action is irreversible.**]
$color[#2e9cff]
$addButton[no;wlc-reset-con_$authorID;Confirm;success]
$addButton[no;wlc-reset-nev_$authorID;Nevermind;secondary]
$endif
$endif
$if[$splitText[1]==wlc-reset-con]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$title[Action Confirmed]
$description[All the properties of the welcome system has been reset.]
$color[#2e9cff]
$removeAllComponents
$setServerVar[wlc-chan; ]
$setUserVar[wlc-set;{"msg": ["", "", "", "", "", "", "", "", "", "", ""\], "e": "0"};$botID]
$setUserVar[wlc-set-2;{"dm": "false", "ar": [\], "del": {"flags": "never", "mins": "0", "secs": "0"}, "tt": "all"};$botID]
$endif
$endif
$if[$splitText[1]==wlc-reset-nev]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$title[Anything Happened?]
$description[_Alright. Let's pretend this interaction never happened._]
$color[#2e9cff]
$removeAllComponents
$endif
$endif

$nomention
$textSplit[$customID;_]
$if[$splitText[1]==wlc-back]
$if[$splitText[3]==main]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$title[Welcome System Setup]
$description[Setup the welcome system on **$serverName[$guildID]**]
$addField[Welcome Channel;The channel where the **Welcome Message** will be sent]
$addField[Welcome Message;The welcome message, which supports embed and is fully customizable]
$addField[Additional Features;Other features such as autoroles, ignore bots, dm user, etc]
$footer[Welcome module: $trimSpace[$if[$json[e]==0] 🔴 disabled $else 🟢 enabled $endif]]
$color[#2E9CFF]
$addButton[no;wlc-toggle_$authorID;$if[$json[e]==0] Enable $else Disable $endif;$if[$json[e]==0] success $else danger $endif]
$addButton[no;wlc-view_$authorID;View Setup;secondary]
$addButton[no;wlc-reset_$authorID;Reset;danger]
$newSelectMenu[wlc-setup-uwu;1;1]
$addSelectMenuOption[wlc-setup-uwu;Welcome Channel;wlc-chan_$authorID;Interact to set/edit the Welcome Channel]
$addSelectMenuOption[wlc-setup-uwu;Welcome Message;wlc-msg_$authorID;Interact to set/edit the Welcome Message]
$addSelectMenuOption[wlc-setup-uwu;Additional Features;wlc-misc_$authorID;Interact to view the Additional Features page]
$endif
$elseif[$splitText[3]==view-main]
$removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$title[Welcome System: Setup View (System)]
$description[Welcome System: $trimSpace[$if[$json[e]==0] Disabled $else Enabled $endif]]
$addField[Welcome Channel;$if[$getServerVar[wlc-chan]==] _No welcome channel has been set yet._ $else <#$getServerVar[wlc-chan]> \`($getServerVar[wlc-chan])\` $endif]
$newSelectMenu[wlc-view-prop;1;1;Select a system property]
$addSelectMenuOption[wlc-view-prop;Welcome Message;wlc-view-msg_$authorID;View the setup of the Welcome Message page]
$addSelectMenuOption[wlc-view-prop;Additional Features;wlc-view-af_$authorID;View the setup of the Additional Features page]
$addButton[no;wlc-back_$authorID_main;Go Back;secondary]
$color[#2e9cff]
$endif
$endif

$nomention
$textSplit[$customID;_]
$if[$splitText[1]==wlc-msg-set]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set;$botID]]
$var[x;$splitText[>]]
$if[$var[x]==cont]
$var[inp;$input[wlc-msg-inp_cont]]
$removeAllComponents $ephemeral
$title[Welcome Message: Content Updated]
$description[Successfully updated the Content property of your welcome message]
$addField[Before;>>> **Content:** $if[$json[msg;0]==] Empty (not set) $else $json[msg;0] $endif]
$addField[After;>>> **Content:** $if[$var[inp]==] Empty (property reset) $else $var[inp] $endif]
$color[#2e9cff]
$jsonSetString[msg;0;$var[inp]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==author]
$var[inp1;$input[wlc-msg-inp_auth]]
$var[inp2;$input[wlc-msg-inp_authic]]
$ephemeral $removeAllComponents
$title[Welcome Message: Author/Author Icon Update]
$description[Successfully updated the Author/Author Icon property of your welcome message]
$addField[Before;>>> **Author:** $if[$json[msg;1]==] Empty (not set) $else $json[msg;1] $endif
**Author Icon:** $if[$json[msg;2]==] Empty (not set) $else $json[msg;2] $endif]
$addField[After;>>> **Author:** $if[$var[inp1]==] Empty (property reset) $else $var[inp1] $endif
**Author Icon:** $if[$var[inp2]==] Empty (property reset) $else $var[inp2] $endif]
$color[#2e9cff]
$jsonSetString[msg;1;$var[inp1]]
$jsonSetString[msg;2;$var[inp2]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==title]
$var[inp1;$input[wlc-msg-inp_title]]
$var[inp2;$input[wlc-msg-inp_titleurl]]
$ephemeral $removeAllComponents
$title[Welcome Message: Title/Title URL Update]
$description[Successfully updated the Title/Title URL property of your welcome message]
$addField[Before;>>> **Title:** $if[$json[msg;3]==] Empty (not set) $else $json[msg;3] $endif
**Title URL:** $if[$json[msg;4]==] Empty (not set) $else $json[msg;4] $endif]
$addField[After;>>> **Title:** $if[$var[inp1]==] Empty (property reset) $else $var[inp1] $endif
**Title URL:** $if[$var[inp2]==] Empty (property reset) $else $var[inp2] $endif]
$color[#2e9cff]
$jsonSetString[msg;3;$var[inp1]]
$jsonSetString[msg;4;$var[inp2]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==desc]
$var[inp;$input[wlc-msg-inp_desc]]
$ephemeral $removeAllComponents
$title[Welcome Message: Description Update]
$description[Successfully updated the Description property of your welcome message]
$addField[Before;>>> **Description:** $if[$json[msg;5]==] Empty (not set) $else $json[msg;5] $endif]
$addField[After;>>> **Description:** $if[$var[inp]==] Empty (property reset) $else $var[inp] $endif]
$color[#2e9cff]
$jsonSetString[msg;5;$var[inp]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==color]
$var[inp;$input[wlc-msg-inp_color]]
$ephemeral $removeAllComponents
$title[Welcome Message: Color Update]
$description[Successfully updated the Color property of your welcome message]
$addField[Before;>>> **Color:** $if[$json[msg;6]==] Empty (not set) $else $json[msg;6] $endif]
$addField[After;>>> **Color:** $if[$var[inp]==] Empty (property reset) $else $var[inp] $endif]
$color[#2e9cff]
$jsonSetString[msg;6;$var[inp]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==footer]
$var[inp1;$input[wlc-msg-inp_footer]]
$var[inp2;$input[wlc-msg-inp_footeric]]
$ephemeral $removeAllComponents
$title[Welcome Message: Footer/Footer Icon Update]
$description[Successfully updated the Footer/Footer Icon property of your welcome message]
$addField[Before;>>> **Footer:** $if[$json[msg;7]==] Empty (not set) $else $json[msg;7] $endif
**Footer Icon:** $if[$json[msg;8]==] Empty (not set) $else $json[msg;8] $endif]
$addField[After;>>> **Footer:** $if[$var[inp1]==] Empty (property reset) $else $var[inp1] $endif
**Footer Icon:** $if[$var[inp2]==] Empty (property reset) $else $var[inp2] $endif]
$color[#2e9cff]
$jsonSetString[msg;7;$var[inp1]]
$jsonSetString[msg;8;$var[inp2]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==thumb]
$var[inp;$input[wlc-msg-inp_thumb]]
$ephemeral $removeAllComponents
$title[Welcome Message: Thumbnail Update]
$description[Successfully updated the Thumbnail property of your welcome message]
$addField[Before;>>> **Thumbnail:** $if[$json[msg;9]==] Empty (not set) $else $json[msg;9] $endif]
$addField[After;>>> **Thumbnail:** $if[$var[inp]==] Empty (property reset) $else $var[inp] $endif]
$color[#2e9cff]
$jsonSetString[msg;9;$var[inp]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$elseif[$var[x]==img]
$var[inp;$input[wlc-msg-inp_img]]
$ephemeral $removeAllComponents
$title[Welcome Message: Image Update]
$description[Successfully updated the Image property of your welcome message]
$addField[Before;>>> **Image:** $if[$json[msg;10]==] Empty (not set) $else $json[msg;10] $endif]
$addField[After;>>> **Image:** $if[$var[inp]==] Empty (property reset) $else $var[inp] $endif]
$color[#2e9cff]
$jsonSetString[msg;10;$var[inp]]
$setUserVar[wlc-set;$jsonStringify;$botID]
$endif
$endif
$endif

$nomention
$textSplit[$message;_]
$if[$checkContains[%$splitText[1]%;%wlc-msg-cont%;%wlc-msg-author%;%wlc-msg-title%;%wlc-msg-desc%;%wlc-msg-color%;%wlc-msg-footer%;%wlc-msg-thumb%;%wlc-msg-img%]]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set;$botID]]
$if[$splitText[1]==wlc-msg-cont]
$newModal[wlc-msg-set_$authorID_cont;Content]
$addTextInput[wlc-msg-inp_cont;paragraph;Welcome Message: Content;1;1250;no;$json[msg;0];Welcome to {guild(name)}, {member(mention)}!]
$elseif[$splitText[1]==wlc-msg-author]
$newModal[wlc-msg-set_$authorID_author;Author/Author Icon]
$addTextInput[wlc-msg-inp_auth;paragraph;Welcome Message: Author;1;256;no;$json[msg;1];$if[$json[msg;1]==] New member: {member(name)} $else $json[msg;1] $endif]
$addTextInput[wlc-msg-inp_authic;short;Welcome Message: Author Icon;1;150;no;$json[msg;2];$if[$json[msg;2]==] {member(avatar)} $else $json[msg;2] $endif]
$elseif[$splitText[1]==wlc-msg-title]
$newModal[wlc-msg-set_$authorID_title;Title/Title URL]
$addTextInput[wlc-msg-inp_title;paragraph;Welcome Message: Title;1;256;no;$json[msg;3];Welcome to {guild(name)}]
$addTextInput[wlc-msg-inp_titleurl;short;Welcome Message: Title URL;1;150;no;$json[msg;4];https://discord.com/users/{member(id)}]
$elseif[$splitText[1]==wlc-msg-desc]
$newModal[wlc-msg-set_$authorID_desc;Description]
$addTextInput[wlc-msg-inp_desc;paragraph;Welcome Message: Description;1;1250;no;$json[msg;5];Welcome to {guild(name)}, {member(mention)}!$url[decode;%0A]You are our {guild(membersOrd)} member!]
$elseif[$splitText[1]==wlc-msg-color]
$newModal[wlc-msg-set_$authorID_color;Color]
$addTextInput[wlc-msg-inp_color;short;Welcome Message: Color ;1;30;no;$json[msg;6];Must be a valid hex code]
$elseif[$splitText[1]==wlc-msg-footer]
$newModal[wlc-msg-set_$authorID_footer;Footer/Footer Icon]
$addTextInput[wlc-msg-inp_footer;paragraph;Welcome Message: Footer;1;1250;no;$json[msg;7];{guild(name)}
use {timestamp} to add footer timestamp]
$addTextInput[wlc-msg-inp_footeric;short;Welcome Message: Footer Icon;1;150;no;$json[msg;8];{guild(icon)}]
$elseif[$splitText[1]==wlc-msg-thumb]
$newModal[wlc-msg-set_$authorID_thumb;Thumbnail]
$addTextInput[wlc-msg-inp_thumb;short;Welcome Message: Thumbnail;1;150;no;$json[msg;9];URL must be direct (ends with .png, .gif, etc)]
$elseif[$splitText[1]==wlc-msg-img]
$newModal[wlc-msg-set_$authorID_img;Image]
$addTextInput[wlc-msg-inp_img;short;Welcome Message: Image;1;150;no;$json[msg;10];URL must be direct (ends with .png, .gif, etc)]
$endif
$endif
$endif

$nomention

$textSplit[$customID;_]

$if[$splitText[1]==wlc-msg-preview]
$defer
$var[n;$url[decode;%0A]]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set;$botID]]
$if[$getServerVar[wlc-chan]==]
$ephemeral $removeAllComponents
$title[No Welcome Channel]
$description[No welcome channel has been set yet.]
$color[#2e9cff]
$elseif[$json[msg]==[, , , , , , , , , , \]]
$ephemeral $removeAllComponents
$title[No Welcome Message]
$description[You have not set any properties of the Welcome Message yet]
$color[#2e9cff]
$else
$var[chan;$trimSpace[$if[$json[dm]==false] $getServerVar[wlc-chan] $elseif[$json[dm]$isUserDMEnabled[$authorID]==truetrue] $dmChannelID[$authorID] $else $getServerVar[wlc-chan] $endif ]]
$ephemeral $removeAllComponents
$jsonParse[$getUserVar[wlc-set;$botID]]
$httpGet[https://gist.githubusercontent.com/Kemi-Rawr/4c3aa5ed48008bef09ce1dbf91ae04b7/raw/0d20da693963050ec001ef1a85c7e328046bc58d/preview.js]
$eval[$httpResult]
$title[Sending preview of the Welcome Message]
$color[#ffffff]
$var[rawContent;$jsonArrayShift[msg]]
$if[$json[msg]==[, , , , , , , , , \]]
$async[cont]
$useChannel[$var[chan]]
$var[id;$sendMessage[$var[content];yes]]
$endasync
$else
$jsonClear
$jsonParse[$getUserVar[wlc-set;$botID]]
$jsonUnset[msg;6]
$if[$json[msg]==[, , , , , , , , , \]]
$ephemeral $removeAllComponents
$title[Invalid Embed]
$description[Your welcome message cannot only have \`color\` property as embed]
$color[#406ecf]
$else
$jsonClear
$jsonParse[$getUserVar[wlc-set;$botID]]
$async[1]
$if[$var[titleurl]!=]
$try
$httpGet[$var[titleurl]]
$catch
$var[err;true]
$var[errm;\`Title URL\` property value is a **invalid** URL]
$endtry
$endif
$endasync
$await[1]
$async[2]
$if[$var[color]!=]
$if[$isValidHex[$var[color]]==false]
$var[err;true]
$var[errm;\`Color\` property value is a **invalid** HEX code]
$endif
$endif
$endasync
$await[2]
$async[3]
$if[$var[footerurl]!=]
$try
$httpGet[$var[footerurl]]
$catch
$var[err;true]
$var[errm;\`Footer Icon\` property value is a **invalid** URL]
$endtry
$endif
$endasync
$await[3]
$async[4]
$if[$var[thumb]!=]
$try
$httpGet[$var[thumb]]
$catch
$var[err;true]
$var[errm;\`Thumbnail\` property value is a **invalid** URL]
$endtry
$endif
$endasync
$await[4]
$async[5]
$if[$var[img]!=]
$try
$httpGet[$var[img]]
$catch
$var[err;true]
$var[errm;\`Image\` property value is a **invalid** URL]
$endtry
$endif
$endasync
$await[5]
$async[send]
$replyIn[1s]
$if[$var[err]==true]
$sendEmbedMessage[$channelID;;Error Occurred;;$var[errm];#406ecf]
$else
$async[emb]
$var[id;$sendEmbedMessage[$var[chan];$var[content];$var[title];$var[titleurl];$var[desc];$var[color];$var[author];$json[authorurl];$var[footer];$var[footerurl];$var[thumb];$var[img];$checkContains[$var[footer];{timestamp}];true]]
$endasync
$endif
$endasync
$async[delete]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$var[del;$calculate[($json[del;mins] * 60) + $json[del;secs]]]
$if[$var[del]>0]
$replyIn[$var[del]]
$deleteMessage[$channelID;$var[id]]
$endif
$endasync
$endif
$endif
$endif
$endif
$endif

$nomention
$textSplit[$message;_]
$if[$splitText[1]==wlc-misc]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents[$messageID]
$removeAllComponents
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$title[Welcome System: Additional Features]
$description[Some other features which the welcome system provides]
$addField[Autorole;Immediately give the member role(s) upon joining]
$addField[Auto-delete;Immediately delete the welcome message after the specified time
Supports only **minutes** and **seconds**. Max time is 15 minutes]
$addField[Trigger Type;Able to specify whether the welcome system should be triggered by **bots** | **humans** | **all**]
$addField[DM member;If set to \`true\`, the welcome message will be sent to the member's DM.
if set to \`false\`, the welcome message will be sent to the welcome channel
> ⚠️ DMing will only work if the member has their DM enabled]
$color[#2e9cff]
$addButton[no;wlc-back_$authorID_main;Go back;secondary]
$newSelectMenu[wlc-setup-owo;1;1;Select a feature...]
$addSelectMenuOption[wlc-setup-owo;Autorole;wlc-ar_$authorID;Set/edit the roles given by autorole feature]
$addSelectMenuOption[wlc-setup-owo;Auto Delete;wlc-ad_$authorID;Set/edit the Auto-delete feature]
$addSelectMenuOption[wlc-setup-owo;DM Member;wlc-dm_$authorID;Enable/disable the DM Member feature]
$addSelectMenuOption[wlc-setup-owo;Trigger Type;wlc-tt_$authorID;Set/edit the Trigger Type feature]
$endif
$endif
$if[$splitText[1]==wlc-ad]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$newModal[wlc-ad-modal;Welcome System: Auto Delete]
$addTextInput[wlc-ad-inp1;short;Minutes;1;2;no;$if[$replaceText[$json[del;mins];#;]>0] $replaceText[$json[del;mins];#;] $endif]
$addTextInput[wlc-ad-inp2;short;Seconds;1;2;no;$if[$replaceText[$json[del;secs];#;]>0] $replaceText[$json[del;secs];#;] $endif]
$endif
$endif
$if[$splitText[1]==wlc-ar]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$removeAllComponents[$messageID]
$removeAllComponents
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$textSplit[%{DOL}%var[this\;%{DOL}%findRole[ELEMENT\]\]%{DOL}%if[%{DOL}%var[this\]!=\]%{DOL}%roleName[%{DOL}%var[this\]\]%{DOL}%endif;ELEMENT]
$var[place;$eval[$splitText[1]$replaceText[$jsonJoinArray[ar;$url[decode;%0A]];$url[decode;%0A];$splitText[2]$splitText[1]]$splitText[2]]]
$newModal[wlc-ar-modal;Welcome System: Autoroles]
$addTextInput[wlc-ar-inp;paragraph;Autoroles;1;4000;no;$if[$json[ar]!=[\]] $var[place] $endif;Input role names/IDs
separate each role with a new line]
$endif
$endif
$if[$customID==wlc-ar-modal]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$var[inp;$input[wlc-ar-inp]]
$textSplit[$var[inp];$url[decode;%0A]]
$if[$getTextSplitLength>15]
$ephemeral $removeAllComponents
$title[Limit Exceeded]
$description[The max amount of roles you can provide is **15 roles**]
$color[#2e9cff]
$else
$var[before;$if[$json[ar]!=[\]] <@&$replaceText[$replaceText[$jsonJoinArray[ar;$url[decode;%0A]];#;];$url[decode;%0A];> <@&]> $else _No roles to show here_ $endif]
$if[$var[inp]==]
$title[Welcome System: Autoroles Reset]
$description[Successfully reset the Autorole feature to it's default value]
$addField[Before;$var[before]]
$addField[After;_No roles to show here_]
$color[#2e9cff]
$else
$var[roles;]
$var[list;]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$getTextSplitLength;]]
$var[n;1]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$jsonParse[{"ar": [\], "del": {"flags": "$json[del;flags]", "mins": "$json[del;mins]", "secs": "$json[del;secs]"}, "dm": "$json[dm]", "tt": "$json[tt]"}]
$eval[$replaceText[$var[a];a;%{DOL}%if[%{DOL}%findRole[%{DOL}%splitText[%{DOL}%var[n\]\]\]==\]
%{DOL}%var[err\;true\]
%{DOL}%var[errm\;%{DOL}%var[errm\]
_Could not find the role at line %{DOL}%var[n\]: %{DOL}%splitText[%{DOL}%var[n\]\]_\]
%{DOL}%var[list\;%{DOL}%var[list\]
%{DOL}%var[n\]. %{DOL}%splitText[%{DOL}%var[n\]\] ⚠️\]
%{DOL}%else
%{DOL}%jsonArrayAppend[ar\;#%{DOL}%findRole[%{DOL}%splitText[%{DOL}%var[n\]\]\]\]
%{DOL}%var[roles\;%{DOL}%var[roles\]
%{DOL}%findRole[%{DOL}%splitText[%{DOL}%var[n\]\]\]\]
%{DOL}%var[list\;%{DOL}%var[list\]
%{DOL}%var[n\]. %{DOL}%splitText[%{DOL}%var[n\]\]\]
%{DOL}%endif
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$if[$var[err]==true]
$ephemeral $removeAllComponents
$title[Error Occured]
$description[$var[errm]]
$addField[Your Input;$var[list]]
$color[#2e9cff]
$else
$ephemeral $removeAllComponents
$title[Welcome System: Autoroles Update]
$description[Successfully made changes to the Autorole feature!]
$addField[Before;$var[before]]
$addField[After;$replaceText[<@&$replaceText[$var[roles];$url[decode;%0A];> <@&]>;<@&>;]]
$color[#2e9cff]
$setUserVar[wlc-set-2;$jsonStringify;$botID]
$endif
$endif
$endif
$endif

$nomention
$textSplit[$message;_]
$if[$splitText[1]==wlc-dm]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$newModal[wlc-dm-modal;DM Member]
$addTextInput[wlc-dm-inp;short;Welcome system: DM Member;4;5;yes;$json[dm]]
$endif
$endif
$if[$customID==wlc-dm-modal]
$var[inp;$toLowercase[$input[wlc-dm-inp]]]
$if[$checkContains[%$var[inp]%;%true%;%false%]==false]
$ephemeral $removeAllComponents
$title[Error Occurred]
$description[The input's value provided is not **true** or **false**]
$color[#2e9cff]
$else
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$ephemeral $removeAllComponents
$title[Welcome System: DM Member Update]
$description[Successfully made changes to the DM Member feature

**Before:** \`$json[dm]\`
**After:** \`$var[inp]\`]
$color[#2e9cff]
$jsonSetString[dm;$var[inp]]
$setUserVar[wlc-set-2;$jsonStringify;$botID]
$endif
$endif
$if[$customID==wlc-ad-modal]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$var[mins;$replaceText[$json[del;mins];#;]]
$var[secs;$replaceText[$json[del;secs];#;]]
$var[min;$trimSpace[$if[$input[wlc-ad-inp1]==] 0 $else $input[wlc-ad-inp1] $endif]]
$var[sec;$trimSpace[$if[$input[wlc-ad-inp2]==] 0 $else $input[wlc-ad-inp2] $endif]]
$var[formatted;$trimSpace[$if[$var[mins]>0] $var[mins] minute(s) $endif]]
$var[formatted;$trimSpace[$if[$var[formatted]!=] $if[$var[secs]>0] $var[formatted] and $var[secs] second(s) $endif $else $if[$var[secs]>0] $var[secs] second(s) $endif $endif]]
$var[formatted;$trimSpace[$if[$var[formatted]==] Never $else $var[formatted] $endif]]
$if[$or[%$var[min]$var[sec]%==%%;$var[min]$var[sec]==00]]
$ephemeral $removeAllComponents
$title[Welcome System: Auto Delete Update]
$description[Successfully made changes to the Auto Delete feature]
$addField[Before;Auto delete: $var[formatted]]
$addField[After;Auto delete: Never]
$jsonSetString[del;mins;#0]
$jsonSetString[del;secs;#0]
$jsonSetString[del;flags;never]
$setUserVar[wlc-set-2;$jsonStringify;$botID]
$color[#2e9cff]
$elseif[$or[$isNumber[$var[min]$var[sec]]==false;$var[min]<0;$var[sec]<0;$checkContains[$var[min]$var[sec];,;.]==true]==true]
$title[Invalid Time Given]
$description[The **MINUTES** and **SECONDS** input field values must be a positive integer number]
$ephemeral $removeAllComponents
$color[#2e9cff]
$elseif[$or[$var[min]>15;$var[sec]>59]==true]
$ephemeral $removeAllComponents
$title[Time Limits Exceeded]
$description[the **MINUTES** input field value must be 15 or less
the **SECONDS** input field value must be 59 or less]
$color[#2e9cff]
$else
$ephemeral $removeAllComponents
$var[format;$trimSpace[$if[$var[min]>0] $var[min] minute(s) $endif]]
$var[format;$trimSpace[$if[$var[format]!=] $var[format] and $var[sec] second(s) $else $var[sec] second(s) $endif]]
$title[Welcome System: Auto Delete Update]
$description[Successfully made changes to the Auto Delete feature]
$addField[Before;Auto delete: $var[formatted]]
$addField[After;Auto delete: $var[format]]
$color[#2e9cff]
$jsonSetString[del;mins;#$var[min]]
$jsonSetString[del;secs;#$var[sec]]
$jsonSetString[del;flags;none]
$setUserVar[wlc-set-2;$jsonStringify;$botID]
$endif
$endif
$if[$splitText[1]==wlc-tt]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Access]
$description[This component doesn't belong to you]
$color[#2E9CFF]
$elseif[$checkUserPerms[$authorID;manageserver]==false]
$ephemeral $removeAllComponents
$title[Missing Permissions]
$description[You're missing the **Manage Server** permission]
$color[#2E9CFF]
$else
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$newModal[wlc-tt-modal;Welcome System: Trigger to]
$addTextInput[wlc-tt-inp1;short;Trigger to;3;30;yes;$json[tt];Input "bots" | "humans" | "all"]
$endif
$endif
$if[$customID==wlc-tt-modal]
$var[inp1;$toLowercase[$input[wlc-tt-inp1]]]
$if[$checkContains[%$var[inp1]%;%bots%;%humans%;%all%]==false]
$ephemeral $removeAllComponents
$title[An Error Occured: Invalid Value]
$description[The value for the **TRIGGER TO** field must be either:
**bots**, **humans**, **all**]
$color[#2e9cff]
$else
$ephemeral $removeAllComponents
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$title[Welcome System: Trigger Type Update]
$description[Successfully made changes to the Trigger Type feature]
$addField[Before;> **Trigger to:** \`$json[tt]\`]
$addField[After;> **Trigger to:** \`$var[inp1]\`]
$jsonSetString[tt;$var[inp1]]
$setUserVar[wlc-set-2;$jsonStringify;$botID]
$color[#2e9cff]
$endif
$endif
```
</details>
