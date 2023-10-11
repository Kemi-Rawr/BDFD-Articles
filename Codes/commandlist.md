# Command Info
Allows you to view all BDFD functions (10 per page)

## Command usage
`<prefix>commandlist (Page)`

### Preview
![Screenshot_20231010-231735~2](https://github.com/Kemi-Rawr/bdfd-codes/assets/111205130/bbf189d2-80ea-4899-9fdb-8361a5645317)

### Code

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
$title[BDFD Functionlist]
$description[$replaceText[$jsonJoinArray[funcs;$url[decode;%0A]];**[\](https://nilpointer-software.github.io/bdfd-wiki/nightly/bdscript/)**;]]
$jsonClear
$jsonParse[{"data": $httpResult}]
$footer[Page: $var[msg]/$sum[$round[$calculate[$jsonArrayCount[data] / 10]];1]]
$color[#406ecf]
$endif
$endif
```
