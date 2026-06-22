<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Vocabulary Flashcards</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 100px;
        }

        .card {
            width: 300px;
            margin: auto;
            padding: 30px;
            border: 1px solid #ccc;
            border-radius: 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="card" onclick="flip()">
    <h1 id="front">APPLE</h1>
    <p id="back" style="display:none;">A FRUIT</p>
</div>

<script>
function flip() {
    const back = document.getElementById("back");
    back.style.display =
        back.style.display === "none"
        ? "block"
        : "none";
}
</script>

</body>
</html>
