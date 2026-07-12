# BracketVault
<style>

:root {
    --primary: #12355b;
    --secondary: #1e88e5;
    --accent: #f4b942;
    --background: #eef3f8;
    --card: #ffffff;
    --text: #1f2937;
}

* {
    box-sizing: border-box;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    background: var(--background);
    margin: 0;
    color: var(--text);
}

.container {

    max-width: 500px;
    margin: 20px auto;
    padding: 20px;

}

.header {

    background: var(--primary);
    color:white;
    padding:25px;
    border-radius:15px;
    text-align:center;
    margin-bottom:20px;

}

.header h1 {

    margin:0;
    font-size:32px;

}

.header p {

    margin:8px 0 0;
    opacity:.8;

}


.card {

    background:var(--card);
    padding:20px;
    border-radius:15px;
    margin-bottom:20px;
    box-shadow:0 4px 12px rgba(0,0,0,.08);

}


label {

    display:block;
    margin-top:15px;
    font-weight:bold;

}


input, select {

    width:100%;
    padding:14px;
    margin-top:8px;
    border-radius:8px;
    border:1px solid #ccc;
    font-size:16px;

}


.floor-buttons {

    display:flex;
    gap:10px;
    margin-top:10px;

}


.floor-buttons label {

    flex:1;
    background:#e5e7eb;
    padding:12px;
    text-align:center;
    border-radius:8px;
    cursor:pointer;

}


button {

    width:100%;
    padding:15px;
    margin-top:20px;
    background:var(--secondary);
    color:white;
    border:none;
    border-radius:10px;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;

}


button:hover {

    background:var(--primary);

}


.history-title {

    font-size:22px;
    margin-top:25px;

}


.inspection {

    background:white;
    border-left:5px solid var(--accent);
    padding:15px;
    border-radius:10px;
    margin-top:10px;

}


</style>


<div class="header">

<h1>BracketVault</h1>

<p>Construction Inspection Tracker</p>

</div>


<div class="card">

<!DOCTYPE html>
<html>
<head>

<title>BracketVault</title>

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>

:root {
    --primary:#12355b;
    --secondary:#1e88e5;
    --accent:#f4b942;
    --background:#eef3f8;
}

*{
    box-sizing:border-box;
}

body{

    font-family:Arial, sans-serif;
    background:var(--background);
    margin:0;

}


.container{

    max-width:500px;
    margin:auto;
    padding:20px;

}


.header{

    background:var(--primary);
    color:white;
    padding:25px;
    border-radius:15px;
    text-align:center;

}


.card{

    background:white;
    padding:20px;
    margin-top:20px;
    border-radius:15px;
    box-shadow:0 4px 12px rgba(0,0,0,.1);

}


label{

    display:block;
    margin-top:15px;
    font-weight:bold;

}


input, select, textarea{

    width:100%;
    padding:12px;
    margin-top:8px;
    border-radius:8px;
    border:1px solid #ccc;
    font-size:16px;

}


.floor{

    display:flex;
    gap:10px;
    margin-top:10px;

}


.floor label{

    flex:1;
    background:#eee;
    padding:10px;
    text-align:center;
    border-radius:8px;

}


button{

    width:100%;
    padding:15px;
    margin-top:20px;
    background:var(--secondary);
    color:white;
    border:0;
    border-radius:10px;
    font-size:18px;
    cursor:pointer;

}


button:hover{

    background:var(--primary);

}


.inspection{

    background:white;
    padding:15px;
    margin-top:15px;
    border-left:5px solid var(--accent);
    border-radius:10px;

}


.delete{

    background:#c62828;

}

</style>

</head>


<body>


<div class="container">


<div class="header">

<h1>BracketVault</h1>

<p>Construction Inspection Tracker</p>

</div>



<div class="card">


<label>Site</label>

<select id="site">

<option value="">Select Site</option>

<option>Site 1</option>

<option>Site 2</option>

<option>Site 3</option>

</select>



<label>Lot Number</label>

<input id="lot" placeholder="Enter Lot Number">



<label>Floor</label>

<div class="floor">

<label>
<input type="radio" name="floor" value="A">
A
</label>


<label>
<input type="radio" name="floor" value="B">
B
</label>


<label>
<input type="radio" name="floor" value="B2">
B2
</label>

</div>



<label>Notes</label>

<textarea id="notes"
placeholder="Inspection notes..."></textarea>



<button onclick="saveInspection()">

Save Inspection

</button>


</div>



<div class="card">

<h2>Inspection History</h2>

<div id="history"></div>


</div>



</div>



<script>


loadHistory();



function saveInspection(){


let site=document.getElementById("site").value;

let lot=document.getElementById("lot").value;

let floor=document.querySelector(
'input[name="floor"]:checked'
);


let notes=document.getElementById("notes").value;



if(!site || !lot || !floor){

alert("Please complete all fields");

return;

}



let inspection={

id:Date.now(),

site:site,

lot:lot,

floor:floor.value,

notes:notes,

date:new Date().toLocaleString()

};



let inspections=

JSON.parse(localStorage.getItem("inspections")) || [];



inspections.unshift(inspection);



localStorage.setItem(

"inspections",

JSON.stringify(inspections)

);



loadHistory();



}



function loadHistory(){


let history=document.getElementById("history");


history.innerHTML="";



let inspections=

JSON.parse(localStorage.getItem("inspections")) || [];



if(inspections.length===0){

history.innerHTML="<p>No inspections yet.</p>";

return;

}



inspections.forEach(item=>{


history.innerHTML+=`

<div class="inspection">

<b>${item.site}</b><br>

Lot: ${item.lot}<br>

Floor: ${item.floor}<br>

Notes: ${item.notes || "None"}<br>

<small>${item.date}</small>


<button class="delete"

onclick="deleteInspection(${item.id})">

Delete

</button>


</div>


`;

});


}



function deleteInspection(id){


let inspections=

JSON.parse(localStorage.getItem("inspections")) || [];



inspections=

inspections.filter(

item=>item.id!==id

);



localStorage.setItem(

"inspections",

JSON.stringify(inspections)

);



loadHistory();


}


</script>


</body>

</html>
