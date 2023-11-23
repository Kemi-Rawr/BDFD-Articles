# Loop Information
As the name suggests, `forEach` loop is a loop that does something for each element in a list
> The "list" must a separator to separate each element
## Main Syntax
```
$textSplit[%{DOL}%var[this\;ELEMENT\]...escaped code here...;ELEMENT]
$eval[$splitText[1]$replaceText[LIST;LIST'S SEPARATOR;$splitText[2]Separator$splitText[1]]$splitText[2]]
```
+ ELEMENT is the current element from the list that the escaped code is doing something with
+ LIST can be anything that has a separator
+ LIST'S SEPARATOR is the LIST's separator
+ Separator is the separator for the code output (optional) (see example)
## Example
Let's say we have a string with letters and numbers separated by " " and we want to use the `$isNumber[]` on each argument of the string, we can do:<br>
```
$var[input;xyz 18 abc -25 56 str int]
// The string
$var[lsep; ]
// Var input is being separated by a space
$var[sep;, ]
// Output will be separated by ", "

$textSplit[%{DOL}%var[this\;ELEMENT\]%{DOL}%isNumber[%{DOL}%var[this\]\];ELEMENT]
$eval[$splitText[1]$replaceText[$var[input];$var[lsep];$splitText[2]$var[sep]$splitText[1]]$splitText[2]]
```
