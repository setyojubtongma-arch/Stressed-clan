<!DOCTYPE html>
<html>
<head>

<title>Stressed Clan</title>

<style>

body{
background:#f4f6f9;
font-family:Arial;
text-align:center;
color:#1f2937;
}

.header{
background:#2563eb;
color:white;
padding:20px;
font-size:24px;
}

.card{
background:white;
width:350px;
margin:auto;
margin-top:20px;
padding:20px;
border-radius:10px;
box-shadow:0 2px 8px rgba(0,0,0,0.1);
}

button{
background:#2563eb;
color:white;
border:none;
padding:10px;
margin:5px;
border-radius:6px;
}

input{
padding:8px;
margin:5px;
}

table{
margin:auto;
border-collapse:collapse;
width:320px;
}

td,th{
border:1px solid #ddd;
padding:8px;
}

th{
background:#e5e7eb;
}

.admin{
display:none;
}

</style>

</head>

<body>

<div class="header">
👑 Stressed Clan System
</div>

<div class="card">

<h3>🔐 Login</h3>

<input id="email" placeholder="Email">

<br>

<input id="password" type="password" placeholder="Password">

<br>

<button onclick="login()">Login</button>

<p id="loginStatus"></p>

</div>

<div class="card">

<h3>🔎 ดูแต้มตัวเอง</h3>

<input id="playerName" placeholder="ใส่ชื่อ">

<button onclick="checkPoint()">ดูแต้ม</button>

<p id="pointResult"></p>

</div>

<div class="card">

<h3>📊 ตารางคะแนน</h3>

<table id="table">

<tr>
<th>ชื่อ</th>
<th>แต้ม</th>
<th>Rank</th>
</tr>

</table>

</div>

<div class="card">

<h3>💰 ระบบแลกแต้ม</h3>

<p>150 = QUICK Roll</p>
<p>300 = เปลี่ยนรูปแคลน</p>
<p>400 = VIP</p>
<p>700 = Chroma Pack</p>
<p>900 = Starter Pack</p>
<p>1100 = Water Doge Pack</p>
<p>1400 = Lucky Pack</p>
<p>1800 = Gwa Pack</p>
<p>2500 = Gubby Pack</p>

<h4>🔒 Secret Reward</h4>

<p>25,000 = หัวแคลนแต่งหญิง 1 วัน</p>

</div>

<div class="card">

<h3>🏆 ระดับแรงค์</h3>

<p>0 - 299 = Member</p>
<p>300 - 699 = Elite</p>
<p>700 - 1499 = Pro</p>
<p>1500+ = Legend</p>

</div>

<div class="card">

<h3>📜 กฎแคลน</h3>

<p>กิจกรรมทุกวันศุกร์ 19:00 - 23:00</p>
<p>ต้อง AFK รวมกัน</p>

<p>มาไม่ทันต้องแจ้งล่วงหน้า</p>

<p>ไม่แจ้ง = -5 แต้ม</p>

<p>หัวแคลนและรองตัดสินถือว่าสิ้นสุด</p>

</div>

<div class="card admin" id="adminPanel">

<h3>👑 Admin Panel</h3>

<input id="adminName" placeholder="ชื่อสมาชิก">

<input id="adminPoint" placeholder="แต้ม">

<br>

<button onclick="addPoint()">เพิ่มแต้ม</button>

<button onclick="removePoint()">ลดแต้ม</button>

</div>

<script>

let members = {

"ออม":770,
"ต้น":827,
"โอ๊ค":550,
"บิว":0

}

function getRank(point){

if(point >= 1500){
return "Legend"
}

if(point >= 700){
return "Pro"
}

if(point >= 300){
return "Elite"
}

return "Member"

}

function render(){

let table = document.getElementById("table")

table.innerHTML = `
<tr>
<th>ชื่อ</th>
<th>แต้ม</th>
<th>Rank</th>
</tr>
`

for(let name in members){

table.innerHTML += `
<tr>
<td>${name}</td>
<td>${members[name]}</td>
<td>${getRank(members[name])}</td>
</tr>
`

}

}

function checkPoint(){

let name = document.getElementById("playerName").value

if(members[name] !== undefined){

document.getElementById("pointResult").innerText =
name + " มี " + members[name] + " แต้ม (" + getRank(members[name]) + ")"

}else{

document.getElementById("pointResult").innerText =
"ไม่พบชื่อ"

}

}

function login(){

let email = document.getElementById("email").value
let password = document.getElementById("password").value

if(email === "setyojubtongma@gmail.com" && password === "stressed123"){

document.getElementById("loginStatus").innerText = "Admin Login สำเร็จ"

document.getElementById("adminPanel").style.display = "block"

}else{

document.getElementById("loginStatus").innerText = "Login ไม่ถูกต้อง"

}

}

function addPoint(){

let name = document.getElementById("adminName").value
let point = Number(document.getElementById("adminPoint").value)

if(members[name] !== undefined){

members[name] += point

}else{

members[name] = point

}

render()

}

function removePoint(){

let name = document.getElementById("adminName").value
let point = Number(document.getElementById("adminPoint").value)

if(members[name] !== undefined){

members[name] -= point

}

render()

}

render()

</script>

</body>
</html>