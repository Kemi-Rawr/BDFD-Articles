# Command Information
Allows you to view information about users from the **[Pronouns.page](https://en.pronouns.page)** website

 ## Command Usage
 * Usage: `<prefix>pronouns-page <Username>`

# Command Code
> [!NOTE]
> Press the copy button to immediately copy all the code

> [!IMPORTANT]
> Join the [Official BDFD Server](https://discord.gg/botdesigner) for support in case of errors
```
$nomention
$var[user;$message]
$httpGet[https://en.pronouns.page/api/profile/get/$url[encode;$var[user]]?version=2]
$jsonParse[$httpResult]
$if[$json[profiles]==]
$title[User not Found]
$description[Could not find any user for **$var[user]**]
$color[#FF9CFB]
$else
$title[@$json[username]]
$description[$json[profiles;en;description]]
$color[#FF9CFB]
$thumbnail[$json[avatar]]
$if[$or[$jsonArrayCount[profiles;en;names]>0;$jsonArrayCount[profiles;en;pronouns]>0;$jsonArrayCount[profiles;en;links]>0;$jsonArrayCount[profiles;en;words]>0]==true]
$newSelectMenu[ppg-user-info;1;1]
$if[$jsonArrayCount[profiles;en;names]>0]
$addSelectMenuOption[ppg-user-info;Names;ppg-user_$json[id]_names;View $json[username]'s names]
$endif
$if[$jsonArrayCount[profiles;en;pronouns]>0]
$addSelectMenuOption[ppg-user-info;Pronouns;ppg-user_$json[id]_pronouns;View $json[username]'s pronouns]
$endif
$if[$jsonArrayCount[profiles;en;links]>0]
$addSelectMenuOption[ppg-user-info;Links;ppg-user_$json[id]_links;View $json[username]'s links]
$endif
$if[$jsonArrayCount[profiles;en;words]>0]
$addSelectMenuOption[ppg-user-info;Fields;ppg-user_$json[id]_fields;View fields set by $json[username]]
$endif
$endif
$endif
```
> View the **[$onInteraction](/Codes/Pronouns-page/$onInteraction.md)** code
