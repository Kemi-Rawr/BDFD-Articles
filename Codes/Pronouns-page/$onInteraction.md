# Code
```
$nomention
$textSplit[$message;_]
$if[$splitText[1]==ppg-user]
$var[user;$splitText[2]]
$var[act;$splitText[3]]
$if[$var[act]==names]
$ephemeral $removeAllComponents
$httpGet[https://en.pronouns.page/api/profile/get-id/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$if[$jsonArrayCount[profiles;en;names]==0]
$description[**@$json[username]** haven't set any names yet]
$color[#FF9CFB]
$else
$title[@$json[username]'s Names]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[profiles;en;names];]]
$var[names;$eval[$replaceText[$var[a];a;**%{DOL}%json[profiles\;en\;names\;%{DOL}%var[n\]\;value\]** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;names\;%{DOL}%var[n\]\;opinion\]\]==\] %{DOL}%json[profiles\;en\;names\;%{DOL}%var[n\]\;opinion\] %{DOL}%else %{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;names\;%{DOL}%var[n\]\;opinion\]\;description\] %{DOL}%endif\])
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$description[$var[names]]
$color[#FF9CFB]
$thumbnail[$json[avatar]]
$endif
$elseif[$var[act]==pronouns]
$httpGet[https://en.pronouns.page/api/profile/get-id/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$ephemeral $removeAllComponents
$if[$jsonArrayCount[profiles;en;pronouns]==0]
$description[**@$json[username]** haven't set any pronouns yet]
$color[#FF9CFB]
$else
$title[@$json[username]'s Pronouns]
$thumbnail[$json[avatar]]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[profiles;en;pronouns];]]
$var[pronouns;$eval[$replaceText[$var[a];a;%{DOL}%trimSpace[%{DOL}%var[p\;%{DOL}%json[profiles\;en\;pronouns\;%{DOL}%var[n\]\;value\]\] %{DOL}%async[%{DOL}%var[n\]\]%{DOL}%trimSpace[ %{DOL}%httpGet[https://en.pronouns.page/api/pronouns/%{DOL}%url[encode\;%{DOL}%var[p\]\]\] %{DOL}%try %{DOL}%httpResult[name\] %{DOL}%catch %{DOL}%var[p\] %{DOL}%endtry \]%{DOL}%endasync %{DOL}%trimSpace[%{DOL}%if[%{DOL}%checkContains[%{DOL}%var[p\]\;http\;://\]%{DOL}%checkContains[%{DOL}%var[p\]\;pronouns.page\]==truetrue\] **[%{DOL}%await[%{DOL}%var[n\]\]\\](https://en.pronouns.page/%{DOL}%url[encode\;%{DOL}%replaceText[%{DOL}%var[p\]\;https://en.pronouns.page/\;\]\])** %{DOL}%elseif[%{DOL}%checkContains[%{DOL}%var[p\]\;http\;://\]==true\] **%{DOL}%var[p\]** %{DOL}%else **[%{DOL}%await[%{DOL}%var[n\]\]\\](https://en.pronouns.page/%{DOL}%url[encode\;%{DOL}%await[%{DOL}%var[n\]\]\])** %{DOL}%endif\] (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;pronouns\;%{DOL}%var[n\]\;opinion\]\]==\] %{DOL}%json[profiles\;en\;pronouns\;%{DOL}%var[n\]\;opinion\] %{DOL}%else %{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;pronouns\;%{DOL}%var[n\]\;opinion\]\;description\] %{DOL}%endif\])\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$description[$replaceText[$var[pronouns];$url[decode;++];]]
$color[#FF9CFB]
$endif
$elseif[$var[act]==links]
$httpGet[https://en.pronouns.page/api/profile/get-id/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$ephemeral $removeAllComponents
$if[$jsonArrayCount[profiles;en;links]==0]
$description[**@$json[username]** haven't set any pronouns yet]
$color[#FF9CFB]
$else
$title[@$json[username]'s Links]
$thumbnail[$json[avatar]]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[profiles;en;links];]]
$var[links;$eval[$replaceText[$var[a];a;**%{DOL}%json[profiles\;en\;links\;%{DOL}%var[n\]\]**
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]]
$description[$var[links]]
$color[#FF9CFB]
$endif
$elseif[$var[act]==fields]
$ephemeral $removeAllComponents
$httpGet[https://en.pronouns.page/api/profile/get-id/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$if[$jsonArrayCount[profiles;en;words]==0]
$description[**@$json[username]** haven't set any fields yet]
$color[#FF9CFB]
$else
$title[@$json[username]'s Fields]
$description[Please select a field from below to view]
$color[#FF9CFB]
$thumbnail[$json[avatar]]
$newSelectMenu[ppg-user-info;1;1]
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[profiles;en;words];]]
$eval[$replaceText[$var[a];a;%{DOL}%addSelectMenuOption[ppg-user-info\;%{DOL}%json[profiles\;en\;words\;%{DOL}%var[n\]\;header\]\;ppg-user-fields_%{DOL}%json[id\]_%{DOL}%var[n\]\;View "%{DOL}%json[profiles\;en\;words\;%{DOL}%var[n\]\;header\]" field\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$endif
$endif
$elseif[$splitText[1]==ppg-user-fields]
$ephemeral $removeAllComponents
$var[user;$splitText[2]]
$var[field;$splitText[3]]
$httpGet[https://en.pronouns.page/api/profile/get-id/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$if[$jsonArrayCount[profiles;en;words;$var[field];values]==0]
$description[**@$json[username]** haven't set any fields yet]
$color[#FF9CFB]
$else
$var[n;0]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;$repeatMessage[10;a]]];$jsonArrayCount[profiles;en;words;$var[field];values];]]
$title[@$json[username] | $json[profiles;en;words;$var[field];header]]
$var[list;]
$eval[$replaceText[$var[a];a;%{DOL}%var[list\;%{DOL}%var[list\]%{DOL}%url[decode\;%0A\]**%{DOL}%json[profiles\;en\;words\;%{DOL}%var[field\]\;values\;%{DOL}%var[n\]\;value\]** (%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;words\;%{DOL}%var[field\]\;values\;%{DOL}%var[n\]\;opinion\]\]==\] %{DOL}%json[profiles\;en\;words\;%{DOL}%var[field\]\;values\;%{DOL}%var[n\]\;opinion\] %{DOL}%else %{DOL}%json[profiles\;en\;opinions\;%{DOL}%json[profiles\;en\;words\;%{DOL}%var[field\]\;values\;%{DOL}%var[n\]\;opinion\]\;description\] %{DOL}%endif\])\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$description[$var[list]]
$color[#FF9CFB]
$thumbnail[$json[avatar]]
$endif
$endif
```
