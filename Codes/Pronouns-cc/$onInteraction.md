# Code
```
$nomention
$textSplit[$message;_]
$if[$splitText[1]==pcc-user]
$defer
$var[user;$splitText[2]]
$var[act;$splitText[3]]
$if[$var[act]==names]
$var[n;0]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$if[$jsonArrayCount[names]==0]
$description[**@$json[name]** haven't set any names yet]
$color[#FF9CFB]
$else
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[names];]]
$var[names;$eval[$replaceText[$var[a];a;**%{DOL}%json[names\;%{DOL}%var[n\]\;value\]** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[names\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[custom_preferences\;%{DOL}%json[names\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Names]
$description[$var[names]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$endif
$elseif[$var[act]==pronouns]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$if[$jsonArrayCount[pronouns]==0]
$description[**@$json[name]** haven't set any names yet]
$color[#FF9CFB]
$else
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[pronouns];]]
$var[pronouns;$eval[$replaceText[$var[a];a;**[%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\](https://pronouns.cc/pronouns/%{DOL}%json[pronouns\;%{DOL}%var[n\]\;pronouns\],%{DOL}%url[encode\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;display_text\]\])** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[custom_preferences\;%{DOL}%json[pronouns\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$ephemeral $removeAllComponents
$title[@$json[name]'s Pronouns]
$description[$var[pronouns]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$endif
$elseif[$var[act]==links]
$ephemeral $removeAllComponents
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$if[$jsonArrayCount[profiles;en;names]==0]
$description[**@$json[name]** haven't set any names yet]
$color[#FF9CFB]
$else
$title[@$json[name]'s Links]
$description[**$jsonJoinArray[links;**$url[decode;%0A]**]**]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$endif
$elseif[$var[act]==fields]
$ephemeral $removeAllComponents
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$if[$jsonArrayCount[fields]==0]
$description[**@$json[name]** haven't set any names yet]
$color[#FF9CFB]
$else
$title[@$json[name]'s Fields]
$description[Please select a field from below to view]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$newSelectMenu[pcc-user-info;1;1]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[fields];]]
$var[n;0]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[pcc-user-info\;%{DOL}%json[fields\;%{DOL}%var[n\]\;name\]\;pcc-user-fields_%{DOL}%json[id\]_%{DOL}%var[n\]\;Select to view this field\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$endif
$endif
$endif
$if[$splitText[1]==pcc-user-fields]
$var[user;$splitText[2]]
$var[field;$splitText[3]]
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$title[@$json[name] | $json[fields;$var[field];name]]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[fields;$var[field];entries];]]
$var[value;$eval[$replaceText[$var[a];a;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;value\] (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[custom_preferences\;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\]\]==\] %{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\] %{DOL}%else %{DOL}%json[custom_preferences\;%{DOL}%json[fields\;%{DOL}%var[field\]\;entries\;%{DOL}%var[n\]\;status\]\;tooltip\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$description[$var[value]]
$color[#FF9CFB]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$endif
```
> **[Tap to view the main code](/Codes/Pronouns-cc/pronouns-cc.md)**
