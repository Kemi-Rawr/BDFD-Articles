# Code
```
$nomention
$textSplit[$customID;_]
$if[$splitText[1]==pcc-user]
$defer
$var[user;$splitText[2]]
$var[act;$splitText[3]]
$if[$var[act]==names]
$var[n;0]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[names];]]
$var[names;$eval[$replaceText[$var[a];a;**%{DOL}%json[names\;%{DOL}%var[n\]\;value\]** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[names\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Names]
$description[$var[names]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$elseif[$var[act]==pronouns]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[pronouns];]]
$var[pronouns;$eval[$replaceText[$var[a];a;**[%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\](https://pronouns.cc/pronouns/%{DOL}%json[pronouns\;%{DOL}%var[n\]\;pronouns\],%{DOL}%url[encode\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\])** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Pronouns]
$description[$var[pronouns]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$elseif[$splitText[3]==members]
$removeAllComponents
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$title[@$json[members;0;name] ($json[members;0;display_name])]
$description[$replaceText[$json[members;0;bio];$url[decode;%0A+];$url[decode;%0A]]]
$thumbnail[https://cdn.pronouns.cc/members/$json[members;0;id]/$json[members;0;avatar].webp]
$footer[User ID | $json[members;0;id]]
$addButton[no;pcc-member_$json[members;0;id]_names;View Names;secondary]
$addButton[no;pcc-member_$json[members;0;id]_pronouns;View Pronouns;secondary]
$newSelectMenu[pcc-members;1;1;Select a member]
$addButton[no;pcc-back_$authorID;Go Back;primary]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[members];]]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-members\;@%{DOL}%json[members\;%{DOL}%var[n\]\;name\] (%{DOL}%json[members\;%{DOL}%var[n\]\;display_name\])\;pcc-member_%{DOL}%json[members\;%{DOL}%var[n\]\;id\]_$authorID\;View %{DOL}%json[members\;%{DOL}%var[n\]\;name\]'s profile\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$color[#FF9CFB] 
$endif
$endif
$textSplit[$customID;_]
$if[$splitText[1]==pcc-member]
$defer
$var[member;$splitText[2]]
$var[act;$splitText[3]]
$if[$var[act]==names]
$ephemeral
$var[n;0]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[names];]]
$var[names;$eval[$replaceText[$var[a];a;**%{DOL}%json[names\;%{DOL}%var[n\]\;value\]** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[user\;custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[names\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[user\;custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Names]
$description[$var[names]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$elseif[$var[act]==pronouns]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[pronouns];]]
$var[pronouns;$eval[$replaceText[$var[a];a;**[%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\](https://pronouns.cc/pronouns/%{DOL}%json[pronouns\;%{DOL}%var[n\]\;pronouns\],%{DOL}%url[encode\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\])** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[user\;custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[user\;custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Pronouns]
$description[$var[pronouns]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$endif
$endif
$textSplit[$message;_]
$if[$splitText[1]==pcc-member]
$defer
$if[$splitText[3]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Component]
$description[This component doesn't belong to you]
$color[#FF9CFB]
$else
$removeAllComponents
$var[member;$splitText[2]]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$title[@$json[name] ($json[display_name])]
$description[$replaceText[$json[bio];$url[decode;%0A+];$url[decode;%0A]]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$var[member]/$json[avatar].webp]
$footer[User ID | $json[id]]
$addButton[no;pcc-member_$var[member]_names;View Names;secondary]
$addButton[no;pcc-member_$var[member]_pronouns;View Pronouns;secondary]
$newSelectMenu[pcc-members;1;1;Select a member]
$addButton[no;pcc-back_$authorID;Go Back;primary]
$var[n;0]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$json[user;id]]]
$jsonParse[$httpResult]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[members];]]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-members\;@%{DOL}%json[members\;%{DOL}%var[n\]\;name\] (%{DOL}%json[members\;%{DOL}%var[n\]\;display_name\])\;pcc-member_%{DOL}%json[members\;%{DOL}%var[n\]\;id\]_$authorID\;View %{DOL}%json[members\;%{DOL}%var[n\]\;name\]'s profile\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$endif
$endif
$textSplit[$customID;_]
$if[$splitText[1]==pcc-back]
$if[$splitText[2]!=$authorID]
$ephemeral $removeAllComponents
$title[Missing Component]
$description[This component doesn't belong to you]
$color[#FF9CFB]
$else
$removeAllComponents
$var[member;$trimSpace[$replaceText[$getEmbedData[$channelID;$messageID;1;footer];User ID |;]]]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$var[user;$httpResult[user;id]]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$title[@$json[name] ($json[display_name])]
$description[$replaceText[$json[bio];$url[decode;%0A+];$url[decode;%0A]]]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$footer[User ID | $json[id]]
$addButton[no;pcc-user_$json[id]_names;View Names;secondary]
$addButton[no;pcc-user_$json[id]_pronouns;View Pronouns;secondary]
$addButton[no;pcc-user_$json[id]_members;View Members;secondary]
$color[#FF9CFB]
$endif $endif
```
> **[Tap to view the main code](/pronouns-cc.md)**
