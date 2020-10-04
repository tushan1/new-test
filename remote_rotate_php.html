<!DOCTYPE html>
<html>
<head>
<title>PHPoC Shield - Web Remote Control for Arduino</title>
<meta name="viewport" content="width=device-width, initial-scale=0.7, maximum-scale=0.7">
<style>
body { text-align: center; font-size: 15pt; }
h1 { font-weight: bold; font-size: 25pt; }
h2 { font-weight: bold; font-size: 15pt; }
button { font-weight: bold; font-size: 15pt; }
</style>
<script>
var canvas_width = 400, canvas_height = 400;
var plate_radius = 160;
var click_state = 0;
var last_plate_angle = 0
var plate_angle = 0, last_angle = 0;
var ws;
function init()
{
	var canvas = document.getElementById("remote");
 
	canvas.addEventListener("touchstart", mouse_down);
	canvas.addEventListener("touchend", mouse_up);
	canvas.addEventListener("touchmove", mouse_move);
	canvas.addEventListener("mousedown", mouse_down);
	canvas.addEventListener("mouseup", mouse_up);
	canvas.addEventListener("mousemove", mouse_move);
 
	var ctx = canvas.getContext("2d");
 
	ctx.translate(canvas_width / 2, canvas_height / 2);
 
	rotate_plate(0);
}
function connect_onclick()
{
	if(ws == null)
	{
		var ws_host_addr = "<?echo _SERVER("HTTP_HOST")?>";
		var debug = document.getElementById("debug");
		if((navigator.platform.indexOf("Win") != -1) && (ws_host_addr.charAt(0) == "["))
		{
			// network resource identifier to UNC path name conversion
			ws_host_addr = ws_host_addr.replace(/[\[\]]/g, '');
			ws_host_addr = ws_host_addr.replace(/:/g, "-");
			ws_host_addr += ".ipv6-literal.net";
		}
		//debug.innerHTML = "<br>" + navigator.platform + " " + ws_host_addr;
		ws = new WebSocket("ws://" + ws_host_addr + "/remote_slide", "text.phpoc");
		document.getElementById("ws_state").innerHTML = "CONNECTING";
		ws.onopen = ws_onopen;
		ws.onclose = ws_onclose;
		ws.onmessage = ws_onmessage;
	}
	else
		ws.close();
}
function ws_onopen()
{
	document.getElementById("ws_state").innerHTML = "<font color='blue'>CONNECTED</font>";
	document.getElementById("bt_connect").innerHTML = "Disconnect";
}
function ws_onclose()
{
	document.getElementById("ws_state").innerHTML = "<font color='gray'>CLOSED</font>";
	document.getElementById("bt_connect").innerHTML = "Connect";
	ws.onopen = null;
	ws.onclose = null;
	ws.onmessage = null;
	ws = null;
}
function ws_onmessage(e_msg)
{
	e_msg = e_msg || window.event; // MessageEvent
	alert("msg : " + e_msg.data);
}

function rotate_plate(angle)
{
	var canvas = document.getElementById("remote");
	var ctx = canvas.getContext("2d");
 
	ctx.clearRect(-canvas_width / 2, -canvas_height / 2, canvas_width, canvas_height);
	ctx.rotate(angle / 180 * Math.PI);
 
	ctx.strokeStyle="red";
	ctx.fillStyle="red";
	ctx.beginPath();
	ctx.arc(0, 0, plate_radius, Math.PI, Math.PI * 1.5);
	ctx.lineTo(0, 0);
	ctx.lineTo(-plate_radius, 0);
	ctx.fill();
	ctx.stroke();
 
	ctx.strokeStyle="blue";
	ctx.fillStyle="blue";
	ctx.beginPath();
	ctx.arc(0, 0, plate_radius, 0, Math.PI / 2);
	ctx.lineTo(0, 0);
	ctx.lineTo(plate_radius, 0);
	ctx.fill();
	ctx.stroke();
 
	ctx.strokeStyle="black";
	ctx.arc(0, 0, plate_radius, 0, Math.PI * 2);
	ctx.stroke();
 
	ctx.rotate(-angle / 180 * Math.PI);
}
function mouse_down()
{
	if(ws == null)
		return;
	
	var dist_min, dist_max, dist;
 
	event.preventDefault();
 
	if(event.offsetX)
	{
		x = event.offsetX - canvas_width / 2;
		y = canvas_height / 2 - event.offsetY;
		dist_min = 40;
		dist_max = plate_radius;
	}
	else if(event.layerX)
	{
		x = event.layerX - canvas_width / 2;
		y = canvas_height / 2 - event.layerY;
		dist_min = 40;
		dist_max = canvas_width / 2;
	}
	else
	{
		x = (Math.round(event.touches[0].pageX - event.touches[0].target.offsetLeft)) - canvas_width / 2;
		y = canvas_height / 2 - (Math.round(event.touches[0].pageY - event.touches[0].target.offsetTop));		 
		dist_min = 40;
		dist_max = canvas_width / 2;
	}
 
	var dist = Math.round(Math.sqrt(x * x + y * y));
	if((dist > dist_min) && (dist < dist_max))
	{
		click_state = 1;
		last_angle = Math.round(Math.atan2(y, x) / Math.PI * 180);
	}
}
function mouse_up()
{
	if(ws == null)
		return;
	
	event.preventDefault();
 
	click_state = 0;
}
function mouse_move()
{
	if(ws == null)
		return;
	
	var dist_min, dist_max, angle, dist;
 
	event.preventDefault();
 
	if(!click_state)
		return;
 
	if(event.offsetX)
	{
		x = event.offsetX - canvas_width / 2;
		y = canvas_height / 2 - event.offsetY;
		dist_min = 40;
		dist_max = plate_radius;
	}
	else if(event.layerX)
	{
		x = event.layerX - canvas_width / 2;
		y = canvas_height / 2 - event.layerY;
		dist_min = 40;
		dist_max = canvas_width / 2;
	}
	else
	{
		x = (Math.round(event.touches[0].pageX - event.touches[0].target.offsetLeft)) - canvas_width / 2;
		y = canvas_height / 2 - (Math.round(event.touches[0].pageY - event.touches[0].target.offsetTop));		 
		dist_min = 40;
		dist_max = canvas_width / 2;
	}
 
	angle = Math.round(Math.atan2(y, x) / Math.PI * 180);
	dist = Math.round(Math.sqrt(x * x + y * y));
 
	if((dist < dist_min) || (dist > dist_max))
	{
		click_state = 0;
		return;
	}
 
	if((Math.abs(angle) > 90) && (angle * last_angle < 0))
	{
		if(last_angle > 0)
			last_angle = -180;
		else
			last_angle = 180;
	}
 
	plate_angle += (angle - last_angle);
	last_angle = angle;
 
	if(plate_angle > 180)
		plate_angle = 180;
 
	if(plate_angle < 0)
		plate_angle = 0;
 
	rotate_plate(-plate_angle);
	
	if(plate_angle != last_plate_angle)
	{
		if(ws && ws.readyState)
		{
			ws.send("C" + plate_angle.toString() + "\r\n");
			last_plate_angle = plate_angle;
			debug = document.getElementById("debug");
			debug.innerHTML = plate_angle;
			//console.log(plate_angle);
		}
	}
}
window.onload = init;
</script>
</head>

<body>

<p>
<h1>Web Remote Control / Rotate</h1>
</p>

<canvas id="remote" width="400" height="400"></canvas>

<h2>
<p>
WebSocket : <span id="ws_state">null</span><br>
Angle : <span id="debug">0</span>
</p>
<button id="bt_connect" type="button" onclick="connect_onclick();">Connect</button>
</h2>

</body>
</html>