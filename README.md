# BINDHUEEE18
<!DOCTYPE html5>

<html>

<head>
<title>CONTROL PANEL</title>
</head>

<script type="text/javascript">
window.onload=Pinstatus;
function Pinstatus(){
morestatus();
}

function morestatus(){
setTimeout(morestatus, 4000);
server = "STATUS/99";
request = new XMLHttpRequest();
request.onreadystatechange = updateasyncstatus;
request.open("GET", server, true);
request.send(null);
}
function updateasyncstatus(){
if ((request.readyState == 4) && (request.status == 200))
{
result = request.responseText;
document.getElementById("description1").innerHTML = result;
fullset = result.split("#");
document.getElementById("description1").innerHTML = fullset;
if(fullset[0]=="STATUS"){
document.getElementById("OutLuxId").value=fullset[1];
document.getElementById("LightsWorking").value=fullset[2];
}
}}


function ButtonClick(){
document.getElementById("description2").innerHTML = "Processing Status";
server = document.getElementById("ModeId").value+"/"+document.getElementById("TimeId").value+"/"+document.getElementById("LuxId").value;
request = new XMLHttpRequest();
request.onreadystatechange = UpdateStatus;
request.open("GET", server, true);
request.send(null);
}

function UpdateStatus(){
if ((request.readyState == 4) && (request.status == 200))
{
result = request.responseText;
document.getElementById("description2").innerHTML = "Present Status"+result;
}
}


</script>

<body bgcolor="#E69B84">

<table cellpadding="20"  align="center"  >

<caption><h2>STREET LIGHT CONTROL PANEL</h2></caption>

<tr>
<th align="center" colspan="6"   >SELECT MODE:</th>
<th><select id="ModeId" name="Mode" style="width: 100px;">
  <option value="ON">ON ALL</option>
  <option value="OFF">OFF ALL</option>
  <option value="AUTO">AUTO</option>
  <option value="SERIES_1">SERIES_1</option>
  <option value="SERIES_2">SERIES_2</option></select></th>
<th align="center" colspan="6"   >OUTDOOR LIGHT LUX:</th>
<th><input type="text" style="text-align: center;" style="width: 100px;" name="analog" id="OutLuxId" value="0" size="6" readonly/></th>
</tr>
<tr>
<th align="center" colspan="6" >SELECT TIMER:</th>
<th><select id="TimeId" name="Time" style="width: 100px;">
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
<option value="5">5</option>
<option value="6">6</option>
<option value="7">7</option>
<option value="8">8</option>
<option value="9">9</option>
<option value="10">10</option>
                        </select></th>
<th align="center" colspan="6" >LIGHTS WORKING:</th>
<th><input type="text" style="text-align: center;" style="width: 100px;" name="analog" id="LightsWorking" value="0" size="6" readonly/></th>
</tr>
<tr>
<th align="center" colspan="6" >THRESHOLD LUX LEVEL:</th>
<th><select id="LuxId" name="Lux" style="width: 100px;">
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
<option value="5">5</option>
<option value="6">6</option>
<option value="7">7</option>
<option value="8">8</option>
<option value="9">9</option>
<option value="10">10</option>
                        </select></th>
<th align="center" colspan="6" >FAULT LIGHTS:</th>
<th><input type="text" style="text-align: center;" style="width: 100px;" name="analog" id="FaultLights" value="0" size="6" readonly/></th>
<th align="center" colspan="6" >VEHICLES PASSED:</th>
<th><input type="text" style="text-align: center;" style="width: 100px;" name="analog1" id="VehiclesPassed" value="0" size="6" readonly/></th>
</tr>

<th><button style="width: 100px;"  align="center" onclick="ButtonClick();" >APPLY</button></th>
</table>
<p  id="description1"> - </p>
<br>
<p  id="description2"> - </p>
</body>
</html>
