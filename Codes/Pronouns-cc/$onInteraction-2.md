# Code
```
$nomention
$textSplit[$customID;_]
$if[$splitText[1]==pcc-user]
$var[user;$splitText[2]]
$if[$splitText[3]==members]
$ephemeral $removeAllComponents
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$title[Select a Member]
$description[Select a member below to view information from]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$newSelectMenu[pcc-member-select;1;1]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[members];]]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-member-select\;@%{DOL}%json[members\;%{DOL}%var[n\]\;name\] (%{DOL}%json[members\;%{DOL}%var[n\]\;display_name\])\;pcc-member_%{DOL}%json[members\;%{DOL}%var[n\]\;id\]_select\;Select to view this member\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$endif
$endif
$textSplit[$message;_]
$if[$splitText[1]==pcc-member]
$if[$splitText[3]==select]
$var[member;$splitText[2]]
$removeAllComponents[$messageID]
$removeAllComponents
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$var[u;$json[user;id]]
$title[@$json[name] ($json[display_name])]
$description[$replaceText[$json[bio];$url[decode;%0A+];$url[decode;%0A]]]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$footer[Member ID | $json[id]]
$newSelectMenu[pcc-member-info;1;1;Member Information]
$addSelectMenuOption[pcc-member-info;Names;pcc-member_$json[id]_names;View $json[name]'s names]
$addSelectMenuOption[pcc-member-info;Pronouns;pcc-member_$json[id]_pronouns;View $json[name]'s pronouns]
$addSelectMenuOption[pcc-member-info;Links;pcc-member_$json[id]_links;View $json[name]'s links]
$addSelectMenuOption[pcc-member-info;Fields;pcc-member_$json[id]_fields;View fields set by $json[name]]
$jsonClear
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[u]]]
$jsonParse[$httpResult]
$newSelectMenu[pcc-member-select;1;1;Select a Member]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[members];]]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-member-select\;@%{DOL}%json[members\;%{DOL}%var[n\]\;name\] (%{DOL}%json[members\;%{DOL}%var[n\]\;display_name\])\;pcc-member_%{DOL}%json[members\;%{DOL}%var[n\]\;id\]_select\;Select to view this member\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$addButton[no;pcc-back_$var[u];Go Back;secondary]
$color[#FF9CFB]
$endif
$endif
$textSplit[$message;_]
$if[$splitText[1]==pcc-member]
$defer
$var[member;$splitText[2]]
$var[act;$splitText[3]]
$if[$var[act]==names]
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
$var[pronouns;$eval[$replaceText[$var[a];a;**[%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]!=\] %{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\] %{DOL}%else %{DOL}%json[pronouns\;%{DOL}%var[n\]\;pronouns\] %{DOL}%endif\]\](https://pronouns.cc/pronouns/%{DOL}%json[pronouns\;%{DOL}%var[n\]\;pronouns\]%{DOL}%if[%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]!=\]%{DOL}%url[encode\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\]%{DOL}%endif)** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[user\;custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[user\;custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Pronouns]
$description[$var[pronouns]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$elseif[$var[act]==links]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$ephemeral $removeAllComponents
$title[@$json[name]'s Links]
$description[**$jsonJoinArray[links;**$url[decode;%0A]**]**]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$elseif[$var[act]==fields]
$ephemeral $removeAllComponents
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$title[@$json[name]'s Fields]
$description[Please select a field from below to view]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$newSelectMenu[pcc-member-info;1;1]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[fields];]]
$var[n;0]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-member-info\;%{DOL}%json[fields\;%{DOL}%var[n\]\;name\]\;pcc-member-fields_%{DOL}%json[id\]_%{DOL}%var[n\]\;Select to view this field\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$endif
$endif
$if[$splitText[1]==pcc-member-fields]
$var[member;$splitText[2]]
$var[field;$splitText[3]]
$httpGet[https://pronouns.cc/api/v1/members/$url[encode;$var[member]]]
$jsonParse[$httpResult]
$title[@$json[name] | $json[fields;$var[field];name]]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[fields;$var[field];entries];]]
$var[value;$eval[$replaceText[$var[a];a;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;value\] (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[user\;custom_preferences\;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[user\;custom_preferences\;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$description[$var[value]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/members/$json[id]/$json[avatar].webp]
$endif
```
> View the **[Main](Codes/Pronouns-cc/pronouns-cc.md)** and the other **[$onInteraction](Codes/Pronouns-cc/$onInteraction.md)** code here
