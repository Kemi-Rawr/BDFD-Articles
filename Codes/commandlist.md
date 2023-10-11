# Command Info
Allows you to view all BDFD functions (10 per page)

## Command usage
+ `<prefix>commandlist (Page)`
+ `<prefix>commandlist (Function Query)`
## Preview
![Screenshot_20231010-231735~2](https://github.com/Kemi-Rawr/bdfd-codes/assets/111205130/bbf189d2-80ea-4899-9fdb-8361a5645317)
![Screenshot_20231011-184245~2](https://github.com/Kemi-Rawr/bdfd-codes/assets/111205130/db242cb0-ce07-4de9-b049-b384820693dd)

# Code
> [!NOTE]
> Press the copy button to immediately copy all the code
> 
> Join the [Official BDFD Server](https://discord.gg/botdesigner) for support in case of errors
```
$nomention
$var[msg;$trimSpace[$message]]
$if[$or[$isNumber[$var[msg]]==true;$var[msg]==]]
$if[$var[msg]==]
$var[msg;1]
$endif
$httpGet[https://botdesignerdiscord.com/public/api/function_tag_list]
$jsonParse[{"data": $httpResult}]
$if[$or[$var[msg]>$sum[$round[$calculate[$jsonArrayCount[data] / 10]];1];$var[msg]<1]]
$title[Invalid Page Number]
$description[Provide a number between 1 and $sum[$round[$calculate[$jsonArrayCount[data] / 10]];1]]
$color[#406ecf]
$else
$var[n;$sub[$multi[$var[msg];10];10]]
$var[a;aaaaaaaaaa]
$eval[$replaceText[$var[a];a;%{DOL}%jsonArrayAppend[funcs\;**[%{DOL}%httpResult[%{DOL}%var[n\]\]\\\](https://nilpointer-software.github.io/bdfd-wiki/nightly/bdscript/%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%httpResult[%{DOL}%var[n\]\]\;[\\\]\;\]\;%{DOL}%\;\])**\]
%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\];-1]]
$title[BDFD Commandlist]
$description[$replaceText[$jsonJoinArray[funcs;$url[decode;%0A]];**[\](https://nilpointer-software.github.io/bdfd-wiki/nightly/bdscript/)**;]]
$jsonClear
$jsonParse[{"data": $httpResult}]
$footer[Page: $var[msg]/$sum[$round[$calculate[$jsonArrayCount[data] / 10]];1] | use !commandlist (function query)]
$color[#406ecf]
$endif
$else
$httpGet[https://botdesignerdiscord.com/public/api/function_tag_list]
$textSplit[$httpResult;"$var[msg]]
$textSplit[$splitText[2];"]
$var[func;$var[msg]$splitText[1]]
$jsonParse[{"funcs": $httpResult}]
$if[$jsonArrayIndex[funcs;$var[func]]==-1]
$title[Function not Found]
$description[Could not find a function for: **$var[msg]**]
$addField[Command Usage;`!commandlist (Function Query)`]
$color[#406ecf]
$else
$var[i;0]
$httpGet[https://botdesignerdiscord.com/public/api/function/$var[func]]
$jsonParse[{"data": $httpResult}]
$title[Commandlist | $var[func]]
$embeddedURL[https://nilpointer-software.github.io/bdfd-wiki/nightly/bdscript/$replaceText[$replaceText[$var[func];$;];[\];]]
$description[```
$httpResult[tag]
\`\`\`
$httpResult[shortDescription]]
$var[a;$cropText[$repeatMessage[10;$repeatMessage[10;a]];$jsonArrayCount[data;arguments];]]
$eval[$replaceText[$var[a];a;%{DOL}%var[enum\;%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;enumData\;0\]!=\] (%{DOL}%jsonJoinArray[data\;arguments\;%{DOL}%var[i\]\;enumData\;, \]) %{DOL}%endif\]\]
%{DOL}%var[flags\;%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;required\]==true\] ⚠️ Required  %{DOL}%endif\]\]
%{DOL}%var[flags\;%{DOL}%var[flags\]
%{DOL}%trimSpace[%{DOL}%if[%{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;empty\]==true\] ❕ Emptiable %{DOL}%endif\]\]
%{DOL}%textSplit[%{DOL}%var[flags\]\;%{DOL}%url[decode\;%0A\]\]
%{DOL}%var[flags\;%{DOL}%trimSpace[%{DOL}%if[%{DOL}%joinSplitText[, \]!=\] Flags: `%{DOL}%joinSplitText[, \]` %{DOL}%endif\]\]
%{DOL}%addField[%{DOL}%sum[%{DOL}%var[i\]\;1\]. %{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;name\]\;%{DOL}%if[%{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;description\]!=\]> %{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;description\] %{DOL}%endif
Type: `%{DOL}%json[data\;arguments\;%{DOL}%var[i\]\;type\]` %{DOL}%var[enum\]
%{DOL}%var[flags\]\]
%{DOL}%var[i\;%{DOL}%sum[%{DOL}%var[i\]\;1\]\];-1]]
$color[#406ecf]
$addButton[no;https://nilpointer-software.github.io/bdfd-wiki/nightly/bdscript/$replaceText[$replaceText[$var[func];$;];[\];];Wiki of $replaceText[$var[func];[\];];link;no;📔]
$endif
$endif
```
