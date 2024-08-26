> [!IMPORTANT]
> Make sure you've set up the **[variables](/Codes/Welcome-System/variables.md)** and the **[!welcome-setup](/Codes/Welcome-System/!welcome-setup.md)**, **[$onInteraction](/Codes/Welcome-System/$onInteraction.md)** commands

# Command Script

<details><summary>Click to view the code</summary>

> ⚠️ Script Language: BDScript 2
  
```
$nomention
$try
$jsonParse[$getUserVar[wlc-set;$botID]]
$httpGet[https://gist.githubusercontent.com/Kemi-Rawr/d50a9774db85600363d5f0a80cd0c950/raw/65c6f280b2edddc018919adad92cc2660eaf7325/$onJoined.js]
$eval[$httpResult]
$onlyIf[$json[e]==1;]
$jsonParse[$getUserVar[wlc-set-2;$botID]]
$if[$json[tt]==bots]
$onlyIf[$isBot[$authorID]==true;]
$elseif[$var[tt]==humans]
$onlyIf[$isBot[$authorID]==false;]
$endif

$var[chan;$trimSpace[$if[$and[$json[dm]==true;$isUserDMEnabled[$authorID]==true]] $dmChannelID[$authorID] $else $getServerVar[wlc-chan] $endif]]
$useChannel[$var[chan]]
$var[id;$sendEmbedMessage[$var[chan];$var[content];$var[title];$var[titleurl];$var[desc];$var[color];$var[author];$var[authorurl];$replaceText[$var[footer];{timestamp};];$var[footerurl];$var[thumb];$var[image];$checkContains[$var[footer];{timestamp}];yes]]

$if[$json[ar;0]!=]
$roleGrant[$authorID;$unescape[+$replaceText[+$replaceText[$jsonJoinArray[ar;$url[decode;%0A]];#;];$url[decode;%0A];\;+]]]
$endif
$if[$replaceText[$json[del;secs]$json[del;mins];#;]!=00]
$async[del]
$replyIn[$calculate[($replaceText[$json[del;mins];#;]*60) + $replaceText[$json[del;secs];#;]]]
$deleteMessage[$var[chan];$var[id]]
$endasync
$endif
$catch
$endtry
```
</details>
