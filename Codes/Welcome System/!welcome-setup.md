# Command Information
The main page of the welcome system, which leads to the other properties of the system
### Usage
+ `!welcome-setup`
# Command Preview
<details><summary>Click to view preview</summary>
  
![Screenshot_20231109-235504~2](https://github.com/Kemi-Rawr/BDFD-Articles/assets/111205130/456649ec-a9f5-44f8-bf46-59036d107a8b)
</details>

# Command Script

> [!NOTE]
> Press the copy button to immediately copy all the code at once

> [!IMPORTANT]
> Join the **[Official BDFD Server](https://discord.gg/botdesigner)** in case of any issues/questions

<details><summary>Click to view the code</summary>
  
```
$nomention
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
```
</details>
