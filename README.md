﻿<div align="center">

## Scientific Calculator


</div>

### Description

A calculator with all the usual functions, plus: help, memory, Exp, sqrt, log, abs, atan,tan, cos,acos, sin, asin, pi , ln10, ln2,sqrt 1/2, e
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mike McGrath](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mike-mcgrath.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |
**Category**       |[Calculators & Science](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/calculators-science__2-71.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mike-mcgrath-scientific-calculator__2-1749/archive/master.zip)





### Source Code

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<HTML>
<HEAD>
<TITLE>Calculator</TITLE>
<!-- THREE STEPS TO INSTALL CALCULATOR:
 1. Copy the coding into the HEAD of your HTML document
 2. Copy the coding into the BODY TAG of your document
 3. Put the last coding into the BODY of your HTML document -->
<!-- STEP ONE: Paste this code into the HEAD of your HTML document -->
<SCRIPT LANGUAGE="javascript">
<!-- Original: Mike McGrath (mike_mcgrath@lineone.net) -->
<!-- Web Site: http://website.lineone.net/~mike_mcgrath/index.htm -->
<!-- BEGIN --
var computed = false;
var memory = 0;
var	bin = 0;
function addChar(input, character)
{
	if (computed) reset();
	if (input.value == null || input.value == '0') input.value = character;
	else
	{
	input.value += character;
	computed = false;
	}
}
function reset()
{
	document.f.display.value=0;
	document.f.stack.value=0;
	computed = false;
}
function swipe()
{
	document.f.stack.value=0;
	computed=true;
}
function wipe()
{
	document.f.display.value='';
	computed=false;
}
function newSlate()
{
	reset();
	memory=0;
	bin=0;
}
function deleteChar(input)
{
	input.value = input.value.substring(0, input.value.length - 1);
	computed = false;
}
function changeSign(input)
{
	if(input.value.substring(0, 1) == '-')
	input.value = input.value.substring(1, input.value.length);
 else
 input.value = '-' + input.value;
	computed = false;
}
function testFirst()
{
	var a = (document.f.stack.value.substring(0,1));
	if (a == '-' || a == '.' || a == '0' || a== '1' || a == '2' || a =='3' || a == '4' || a == '5' || a == '6' || a == '7' || a == '8' || a == '9')
	testLast()
	else
	alert('Error...\n\nEnter Number First!');
	computed = true;
}
function testLast()
{
	var b = (document.f.stack.value.substring(document.f.stack.value.length,document.f.stack.value.length-1))
	if (b == '0' || b == '1' || b == '2' || b =='3' || b == '4' || b == '5' || b == '6' || b == '7' || b == '8' || b == '9')
	goOperation()
	else
	alert('Error...\n\nEntry Incomplete!');
	computed = true;
}
function goOperation()
{
	document.f.display.value=eval(document.f.stack.value) * 100.00 /100.00;
	computed = true;
}
function cos()
{
	document.f.display.value=Math.cos(document.f.display.value);
	swipe();
	computed=true;
}
function acos()
{
	document.f.display.value=Math.acos(document.f.display.value);
	swipe();
	computed=true;
}
function sin()
{
	document.f.display.value=Math.sin(document.f.display.value);
	swipe();
	computed=true;
}
function asin()
{
	document.f.display.value=Math.asin(document.f.display.value);
	swipe();
	computed=true;
}
function tan()
{
	document.f.display.value=Math.tan(document.f.display.value);
	swipe();
	computed=true;
}
function atan()
{
	document.f.display.value=Math.atan(document.f.display.value);
	swipe();
	computed=true;
}
function log()
{
	document.f.display.value=Math.log(document.f.display.value);
	swipe();
	computed=true;
}
function exp()
{
	document.f.display.value=Math.exp(document.f.display.value);
	swipe();
	computed=true;
}
function sqrt()
{
	document.f.display.value=Math.sqrt(document.f.display.value);
	swipe();
	computed=true;
}
function abs()
{
	document.f.display.value=Math.abs(document.f.display.value);
	swipe();
	computed=true;
}
function square()
{
	document.f.display.value=Math.pow((document.f.display.value), 2);
	swipe();
	computed=true;
}
function cube()
{
	document.f.display.value=Math.pow((document.f.display.value), 3);
	swipe();
	computed=true;
}
function perCent()
{
	addChar(document.f.stack,'/100');
	wipe();
	computed=false;
}
function round()
{
	document.f.display.value=Math.round(document.f.display.value);
	swipe(this.form);
	computed=true;
}
random.m=714025; random.a=4096; random.c=150889;
random.seed= (new Date()).getTime()%random.m;
function random()
{
	random.seed = (random.seed*random.a + random.c) % random.m;
	mikesnum=(random.seed/random.m);
	computed=true;
}
function mem(c)
{
	if (c == 1)
	{
		memory =(document.f.display.value * 1);
		document.f.display.value='';
		swipe(this.form);
		computed = false;
	}
	if (c == -1)
	{
		document.f.display.value = memory ;
		document.f.stack.value = document.f.display.value;
		computed = false;
	}
	if (c == 0)
	{
		document.f.display.value = 0;
		document.f.stack.value=0; memory = 0;
		computed = false;
	}
	if (c == 2)
	{
		bin = (document.f.display.value * 1);
		document.f.display.value='';
		swipe(this.form);
		computed = false;
	}
	if (c == -2)
	{
		document.f.display.value = bin ;
		document.f.stack.value = document.f.display.value; bin = 0;
		computed = false;
	}
	if (c == 3)
	{
		document.f.display.value = 0;
		document.f.stack.value=0;
		bin = 0;
		computed = false;
	}
}
function onlyTwo()
{
	document.f.display.value=(document.f.display.value * 100);
	document.f.display.value=Math.round(document.f.display.value)/100;
	swipe();
	computed=true;
}
function helpFile()
{
 var content="KEY FEATURES\n\n"+
  "< - > Rounds up or down to nearest integer\n"+
  "<00> Rounds up or down to 2 decimal places\n"+
  "Num Generates psuedo-random non-cryptograhic number\n"+
  "M+ Adds single entry only to memory bin no.1\n"+
  "MR Recalls stored single item from memory bin no.1\n"+
  "MC Clears item from memory bin no.1\n"+
  "M2+ Adds single entry only to memory bin no.2\n"+
  "M2R Recalls single item from memory bin no.2\n"+
  "M2C Clears item from memory bin no.2\n"+
  "C  Clears all, except memory no.1 and memory no.2\n"+
  "Clear Resets all features to zero\n"+
  "+-  Inverts value positive/negative of current display value \n"+
  "<-  Deletes last digit of current display\n"+
  "X2 Returns value of current display to power 2\n"+
  "X3 Returns value of current display to power 3\n"+
  "%  Divides entry by 100 to return per centage\n"+
  "Sqrt Returns the square root of display value\n\n"+
  "E1/2 Pi Ln2 Ln10 Return Mathematic constants\n\n"+
  "Log Abs Atan Tan\n"+
  "Acos Cos Asin Sin Return Math calculation of display value:"
 alert(content);
}
//-- END -->
</SCRIPT>
</HEAD>
<!-- STEP TWO: Paste this code into the BODY TAG of your HTML document -->
<BODY onload="reset();">
<!-- STEP THREE: Paste this code into the BODY of your HTML document -->
<CENTER>
<P>
<FORM NAME="f">
<TABLE BGCOLOR=#000000 WIDTH=400 BORDER=5 CELLSPACING=2 CELLPADDING=2>
 <TR>
 <TD BGCOLOR=#C0C0C0 COLSPAN=7 ALIGN=RIGHT>
	 <INPUT NAME="display" TYPE=TEXT VALUE=0 SIZE=25>
	 <INPUT NAME="stack" TYPE=HIDDEN VALUE=0>
 </TD>
 </TR>
 <TR>
 <TD BGCOLOR=#FF0000><INPUT TYPE=BUTTON VALUE=" Help " onclick="helpFile();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Num " onclick="random()+addChar(display,mikesnum)+addChar(stack,mikesnum);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" <00> " onclick="onlyTwo();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" <-> " onclick="round();"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE=" M2+ " onclick="mem(2);"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE="M2R " onclick="mem(-2);"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE=" M2C" onclick="mem(3);"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#FF0000><INPUT TYPE=BUTTON VALUE=" Clear" onclick="newSlate();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" x ³ " onclick="addChar(display.value)+cube();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" x ² " onclick="addChar(display.value)+square();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" % " onclick="perCent();"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE=" M+ " onclick="mem(1);"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE=" MR " onclick="mem(-1);"></TD>
 <TD BGCOLOR=#800080><INPUT TYPE=BUTTON VALUE=" MC " onclick="mem(0);"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#000080><INPUT TYPE=BUTTON VALUE=" E " onclick="wipe()+addChar(display,Math.E)+addChar(stack,Math.E);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Exp " onclick="addChar(display.value)+exp();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Sqrt " onclick="addChar(stack)+sqrt();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" ÷ " onclick="addChar(stack,'/')+wipe()+addChar(display,'/');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 7 " onclick="addChar(display,'7')+addChar(stack,'7');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 8 " onclick="addChar(display,'8')+addChar(stack,'8');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 9 " onclick="addChar(display,'9')+addChar(stack,'9');"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#000080><INPUT TYPE=BUTTON VALUE="Sqrt½" onclick="wipe()+addChar(display,Math.SQRT1_2)+addChar(stack,Math.SQRT1_2);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Log " onclick="addChar(display.value)+log();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Abs " onclick="addChar(display.value)+abs();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" × " onclick="addChar(stack,'*')+wipe()+addChar(display,'*');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 4 " onclick="addChar(display,'4')+addChar(stack,'4');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 5 " onclick="addChar(display,'5')+addChar(stack,'5');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 6 " onclick="addChar(display,'6')+addChar(stack,'6');"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#000080><INPUT TYPE=BUTTON VALUE=" Ln2 " onclick="wipe()+addChar(display,Math.LN2)+addChar(stack,Math.LN2);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE="ATan" onclick="addChar(display.value)+atan();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Tan " onclick="addChar(display.value)+tan();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" - " onclick="addChar(stack,'-')+wipe()+addChar(display,'-');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 1 " onclick="addChar(display,'1')+addChar(stack,'1');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 2 " onclick="addChar(display,'2')+addChar(stack,'2');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 3 " onclick="addChar(display,'3')+addChar(stack,'3');"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#000080><INPUT TYPE=BUTTON VALUE=" Ln10 " onclick="wipe()+addChar(display,Math.LN10)+addChar(stack,Math.LN10);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE="ACos" onclick="addChar(display.value)+acos();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Cos " onclick="addChar(display.value)+cos();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" + " onclick="addChar(stack,'+')+wipe()+addChar(display,'+');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" ± " onclick="changeSign(display)+changeSign(stack);"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" . " onclick="addChar(display,'.')+addChar(stack,'.');"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" 0 " onclick="addChar(display,'0')+addChar(stack,'0');"></TD>
 </TR>
 <TR>
 <TD BGCOLOR=#000080><INPUT TYPE=BUTTON VALUE=" Pi " onclick="wipe()+addChar(display,Math.PI)+addChar(stack,Math.PI);"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" ASin " onclick="addChar(display.value)+asin();"></TD>
 <TD BGCOLOR=#0000FF><INPUT TYPE=BUTTON VALUE=" Sin " onclick="addChar(display.value)+sin()+swipe();"></TD>
 <TD BGCOLOR=#008000><INPUT TYPE=BUTTON VALUE=" <- " onclick="deleteChar(display)+deleteChar(stack);"></TD>
 <TD BGCOLOR=#FFA500 COLSPAN='2'><INPUT TYPE=BUTTON VALUE="  =  " onclick="testFirst()+swipe();"></TD>
 <TD BGCOLOR=#FFA500><INPUT TYPE=BUTTON VALUE=" C " onclick="reset();"></TD>
 </TR>
</TABLE>
</FORM>
</CENTER>
</BODY>
</HTML>
```

