<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vocabulary Flashcards</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #111827;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 40px;
}

h1 {
    margin-bottom: 20px;
}

.card {
    width: 90%;
    max-width: 600px;
    min-height: 250px;
    background: #1f2937;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 30px;
    font-size: 2rem;
    cursor: pointer;
    box-shadow: 0 10px 25px rgba(0,0,0,0.3);
}

.controls {
    margin-top: 20px;
}

button {
    padding: 12px 24px;
    margin: 5px;
    border: none;
    border-radius: 10px;
    background: #2563eb;
    color: white;
    font-size: 1rem;
    cursor: pointer;
}

button:hover {
    background: #1d4ed8;
}

.stats {
    margin-top: 20px;
    font-size: 1rem;
}
</style>
</head>
<body>

<h1>Vocabulary Flashcards</h1>

<div class="card" id="card"></div>

<div class="controls">
    <button onclick="markKnown()">Known</button>
    <button onclick="markUnknown()">Unknown</button>
    <button onclick="nextCard()">Next</button>
</div>

<div class="stats">
    Known: <span id="known">0</span> |
    Unknown: <span id="unknown">0</span>
</div>

<script>
const cards = [
    { word: "apple", meaning: "a fruit" },
    { word: "book", meaning: "a set of written pages" },
    { word: "computer", meaning: "an electronic machine" },
    { word: "library", meaning: "a place with books" },
    { word: "airport", meaning: "a place for airplanes" },
    { word: "hospital", meaning: "a place for medical care" },
    { word: "teacher", meaning: "a person who teaches" },
    { word: "student", meaning: "a person who learns" },
    { word: "language", meaning: "a system of communication" },
    { word: "travel", meaning: "to go from one place to another" }
];

let current = null;
let showingMeaning = false;
let knownCount = 0;
let unknownCount = 0;

const card = document.getElementById("card");

function nextCard() {
    current = cards[Math.floor(Math.random() * cards.length)];
    showingMeaning = false;
    card.textContent = current.word;
}

card.addEventListener("click", () => {
    if (!current) return;

    if (showingMeaning) {
        card.textContent = current.word;
    } else {
        card.textContent = current.meaning;
    }

    showingMeaning = !showingMeaning;
});

function markKnown() {
    knownCount++;
    document.getElementById("known").textContent = knownCount;
    nextCard();
}

function markUnknown() {
    unknownCount++;
    document.getElementById("unknown").textContent = unknownCount;
    nextCard();
}

nextCard();
</script>

</body>
</html>
