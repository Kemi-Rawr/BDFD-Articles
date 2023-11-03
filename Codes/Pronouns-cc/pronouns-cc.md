# Command Information
Allows you to view information about users of the **[Pronouns.cc](https://pronouns.cc/)** website. Viewing the user's members information is possible aswell

## Command Usage
+ `<prefix>pronouns-cc <User>`

## Previews
<details><summary>Preview 1</summary>

  ![Screenshot_20231027-012422~2](https://github.com/Kemi-Rawr/BDFD-Articles/assets/111205130/666f5969-6dc2-4ce8-b229-16249ad313e5)
</details>
<details><summary>Preview 2</summary>

  ![Screenshot_20231027-042555~2](https://github.com/Kemi-Rawr/BDFD-Articles/assets/111205130/1a6a79c6-27b1-462f-8720-a31fbc67b5c8)

</details>
<details><summary>Preview 4</summary>

  ![Screenshot_20231027-042655~2](https://github.com/Kemi-Rawr/BDFD-Articles/assets/111205130/3620cebf-dde2-42e4-b65e-e390ad230fdf)

</details>
<details><summary>Preview 3</summary>

  ![Screenshot_20231027-042902~2](https://github.com/Kemi-Rawr/BDFD-Articles/assets/111205130/932f1c9d-3d4b-4d24-a638-0abf9a8c50b7)


</details>

# Code
> [!NOTE]
> Press the copy button to immediately copy all the code

> [!IMPORTANT]
> Join the [Official BDFD Server](https://discord.gg/botdesigner) for support in case of errors
```
$nomention
$var[user;$message]
$if[$var[user]==]
$title[Incorrect Command Usage]
$description[Provide the user you want to get information from]
$footer[!pronounscc <username/user ID>]
$color[#FF9CFB]
$else
$httpGet[https://pronouns.cc/api/v1/users/$url[encode;$var[user]]]
$jsonParse[$httpResult]
$if[$httpStatus!=200]
$title[User not Found]
$description[Could not find any user for **$var[user]**]
$color[#FF9CFB]
$else
$title[@$json[name] $if[$json[display_name]!=]($json[display_name])$endif]
$description[$trimSpace[$if[$json[bio]==] _User has no biography set_ $else $replaceText[$json[bio];$url[decode;%0A+];$url[decode;%0A]] $endif]]
$thumbnail[https://cdn.pronouns.cc/users/$json[id]/$json[avatar].webp]
$footer[User ID | $json[id]]
$if[$or[$jsonArrayCount[names]>0;$jsonArrayCount[pronouns]>0;$jsonArrayCount[links]>0;$jsonArrayCount[fields]>0]==true]
$newSelectMenu[pcc-user-info;1;1;User Information]
$if[$jsonArrayCount[names]>0]
$addSelectMenuOption[pcc-user-info;Names;pcc-user_$json[id]_names;View $json[name]'s names]
$endif
$if[$jsonArrayCount[pronouns]>0]
$addSelectMenuOption[pcc-user-info;Pronouns;pcc-user_$json[id]_pronouns;View $json[name]'s pronouns]
$endif
$if[$jsonArrayCount[links]>0]
$addSelectMenuOption[pcc-user-info;Links;pcc-user_$json[id]_links;View $json[name]'s links]
$endif
$if[$jsonArrayCount[fields]>0]
$addSelectMenuOption[pcc-user-info;Fields;pcc-user_$json[id]_fields;View fields set by $json[name]]
$endif
$endif
$addButton[no;pcc-user_$json[id]_members;Members;secondary;$checkCondition[$jsonArrayCount[members]==0]]
$color[#FF9CFB]
$endif
$endif
```
> View the first **[$onInteraction code](/Codes/Pronouns-cc/$onInteraction.md)** and the second **[$onInteraction code](/Codes/Pronouns-cc/$onInteraction-2.md)**
