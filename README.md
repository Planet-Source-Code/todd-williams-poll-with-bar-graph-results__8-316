<div align="center">

## Poll With Bar Graph Results


</div>

### Description

It is a Poll script all in 1 page. I didn't add a vote limit per person, because I couldn't find a secure way to do it. IP block isn't good because people can re-sign on and their IP will change. Cookies block isn't good because if they disable cookies they can vote as many times as they want. If you know another way please let me know.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Todd Williams](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/todd-williams.md)
**Level**          |Beginner
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__8-7.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/todd-williams-poll-with-bar-graph-results__8-316/archive/master.zip)





### Source Code

```
//#####!!!!!!!!resource.inc!!!!!!!!!!!!####
<?php
$item = array("1", "1", "1");
?>
//#########################################
//#########################################
//#########################################
//######!!!!!!!!poll.php4!!!!!!!!!!!!######
<html>
<head>
<title>Graphical Poll - By: Todd Williams</title>
</head>
<body text="white">
<table border="1" bordercolor="red" cellspacing="0" bgcolor="black">
<tr><td colspan="3" align="center">Title of Poll</td></tr>
<tr>
<td colspan="3">
<?php
include("resource.inc");
$name = array ("Item 1", "Item 2", "Item 3");
$percent = array ("","","");
$total = $item[0] + $item[1] + $item[2];
if ($addto)
{
 switch ($addto)
 {
 case "item0":
 $item[0] = $item[0] + 1;
 break;
 case "item1":
 $item[1] = $item[1] + 1;
 break;
 case "item2":
 $item[2] = $item[2] + 1;
 break;
 }
 $fp = fopen ("resource.inc", "wb");
 $string = "<?php\n\$item = array(\"$item[0]\", \"$item[1]\", \"$item[2]\");\n?>";
 fwrite($fp, $string);
 fclose ($fp);
}
for ($i=0; $item[$i]; $i++)
{
$percent[$i] = ($item[$i] * 100) / $total;
		//list ($before, $after) = split (".",$temp) //before now contains everything before the decimal
		//$percent[$i] = $before
}
echo "Current Results:";
echo "</td></tr>\n";
echo "<tr><td>$name[0]</td><td>$name[1]</td><td>$name[2]</td></tr>\n";
echo "<tr align=\"center\" valign=\"bottom\" height=\"100\">\n";
for ($i=0; $item[$i]; $i++)
{
echo "<td>$item[$i]";
echo "<table><tr height=\"$percent[$i]\" width=\"20\" bgcolor=\"red\"><td> </td></tr></table></td>\n";
}
echo "</tr>\n";
?>
<tr>
<td colspan="3">
<form action="poll.php4">
<?php
for ($i=0; $name[$i]; $i++)
{
echo "<input type=\"radio\" name=\"addto\" value=\"item$i\">$name[$i]</input><br>\n";
}
?>
<input type="submit" value="send">
</td>
</form>
</table>
</body>
</html>
```

