<!DOCTYPE html>
<html>
<head>
<title>Applicant Case Tracker</title>
<style>
body{
font-family:Arial,sans-serif;
background:#f4f4f4;
padding:40px;
}

.container{
max-width:600px;
margin:auto;
background:white;
padding:20px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
}

input{
width:100%;
padding:12px;
margin-top:10px;
}

button{
padding:12px 20px;
margin-top:10px;
cursor:pointer;
}

#result{
margin-top:20px;
}
</style>
</head>

<body>

<div class="container">

<h2>Applicant Case Tracker</h2>

<input
type="text"
id="caseId"
placeholder="Enter Case ID">

<button onclick="checkStatus()">
Check Status
</button>

<div id="result"></div>

</div>

<script>
async function checkStatus(){

const caseId =
document.getElementById("caseId").value.trim();

const response =
await fetch("applicant.json");

const data =
await response.json();

const applicant =
data.find(
x => x.caseId === caseId
);

if(applicant){

document.getElementById("result").innerHTML =
`
<h3>${applicant.name}</h3>
<p><b>Status:</b> ${applicant.status}</p>
<p><b>Destination:</b> ${applicant.destination}</p>
<p><b>Note:</b> ${applicant.note}</p>
`;

}else{

document.getElementById("result").innerHTML =
"<p>Case ID not found.</p>";

}

}
</script>

</body>
</html>
