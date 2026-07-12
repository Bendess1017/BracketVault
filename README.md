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
