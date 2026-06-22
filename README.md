<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>英文單字卡</title>
    <style>
        body{
            font-family:Arial;
            text-align:center;
            margin-top:100px;
        }
        .card{
            width:300px;
            margin:auto;
            padding:30px;
            border:1px solid #ccc;
            border-radius:10px;
            cursor:pointer;
        }
    </style>
</head>
<body>

<div class="card" onclick="flip()">
    <h1 id="word">apple</h1>
    <p id="meaning" style="display:none;">蘋果</p>
</div>

<script>
function flip(){
    let meaning=document.getElementById("meaning");
    meaning.style.display=
        meaning.style.display==="none"
        ?"block":"none";
}
</script>

</body>
</html>
