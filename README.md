<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>無限單字卡</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial,sans-serif;
    background:#f4f7fb;
    display:flex;
    flex-direction:column;
    align-items:center;
    min-height:100vh;
    padding:30px;
}

h1{
    margin-bottom:20px;
}

.stats{
    display:flex;
    gap:20px;
    margin-bottom:20px;
    font-size:18px;
}

.card{
    width:350px;
    height:220px;
    perspective:1000px;
    cursor:pointer;
}

.card-inner{
    position:relative;
    width:100%;
    height:100%;
    transition:transform 0.6s;
    transform-style:preserve-3d;
}

.card.flip .card-inner{
    transform:rotateY(180deg);
}

.face{
    position:absolute;
    width:100%;
    height:100%;
    backface-visibility:hidden;
    border-radius:16px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:32px;
    font-weight:bold;
    box-shadow:0 4px 12px rgba(0,0,0,.15);
}

.front{
    background:white;
}

.back{
    background:#4f46e5;
    color:white;
    transform:rotateY(180deg);
    padding:20px;
    text-align:center;
    font-size:24px;
}

.buttons{
    margin-top:20px;
    display:flex;
    gap:10px;
    flex-wrap:wrap;
}

button{
    border:none;
    border-radius:10px;
    padding:12px 18px;
    font-size:16px;
    cursor:pointer;
}

.correct{
    background:#16a34a;
    color:white;
}

.wrong{
    background:#dc2626;
    color:white;
}

.next{
    background:#2563eb;
    color:white;
}
</style>
</head>
<body>

<h1>無限城市單字卡</h1>

<div class="stats">
    <div>答對：<span id="correctCount">0</span></div>
    <div>答錯：<span id="wrongCount">0</span></div>
</div>

<div class="card" id="card">
    <div class="card-inner">
        <div class="face front" id="front"></div>
        <div class="face back" id="back"></div>
    </div>
</div>

<div class="buttons">
    <button class="correct" onclick="markCorrect()">答對</button>
    <button class="wrong" onclick="markWrong()">答錯</button>
    <button class="next" onclick="nextCard()">下一題</button>
</div>

<script>

const cards = [

{word:"Taipei",answer:"台北"},
{word:"Kaohsiung",answer:"高雄"},
{word:"Taichung",answer:"台中"},
{word:"Tainan",answer:"台南"},
{word:"Hsinchu",answer:"新竹"},
{word:"Tokyo",answer:"東京"},
{word:"Osaka",answer:"大阪"},
{word:"Kyoto",answer:"京都"},
{word:"Seoul",answer:"首爾"},
{word:"Busan",answer:"釜山"},
{word:"Bangkok",answer:"曼谷"},
{word:"Singapore",answer:"新加坡"},
{word:"Hong Kong",answer:"香港"},
{word:"Paris",answer:"巴黎"},
{word:"London",answer:"倫敦"},
{word:"Berlin",answer:"柏林"},
{word:"Rome",answer:"羅馬"},
{word:"Madrid",answer:"馬德里"},
{word:"New York",answer:"紐約"},
{word:"Los Angeles",answer:"洛杉磯"},
{word:"Chicago",answer:"芝加哥"},
{word:"Sydney",answer:"雪梨"},
{word:"Melbourne",answer:"墨爾本"}

];

let currentIndex = -1;
let correct = 0;
let wrong = 0;

const front = document.getElementById("front");
const back = document.getElementById("back");
const card = document.getElementById("card");

card.addEventListener("click",()=>{
    card.classList.toggle("flip");
});

function randomIndex(){
    let newIndex;

    do{
        newIndex = Math.floor(Math.random()*cards.length);
    }
    while(newIndex===currentIndex);

    return newIndex;
}

function loadCard(){

    currentIndex = randomIndex();

    front.textContent = cards[currentIndex].word;
    back.textContent = cards[currentIndex].answer;

    card.classList.remove("flip");
}

function nextCard(){
    loadCard();
}

function markCorrect(){
    correct++;
    document.getElementById("correctCount").textContent = correct;
    nextCard();
}

function markWrong(){
    wrong++;
    document.getElementById("wrongCount").textContent = wrong;
    nextCard();
}

loadCard();

</script>

</body>
</html>
