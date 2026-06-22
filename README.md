<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flashcards</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #0f172a;
    color: white;
    text-align: center;
    padding: 40px;
}

.card {
    width: 500px;
    max-width: 90%;
    min-height: 250px;
    margin: 30px auto;
    padding: 30px;
    background: #1e293b;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    cursor: pointer;
    box-shadow: 0 0 20px rgba(0,0,0,0.4);
}

button {
    padding: 12px 24px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    background: #2563eb;
    color: white;
    cursor: pointer;
}

button:hover {
    background: #1d4ed8;
}
</style>
</head>
<body>

<h1>Flashcards</h1>

<div class="card" id="card"></div>

<button onclick="nextCard()">Next Card</button>

<script>

const cards = [
    {
        question: "What is HTML?",
        answer: "HyperText Markup Language"
    },
    {
        question: "What is CSS?",
        answer: "Cascading Style Sheets"
    },
    {
        question: "What is JavaScript?",
        answer: "A programming language for web applications"
    },
    {
        question: "What is an API?",
        answer: "Application Programming Interface"
    },
    {
        question: "What is JSON?",
        answer: "JavaScript Object Notation"
    },
    {
        question: "What is Git?",
        answer: "A version control system"
    },
    {
        question: "What is GitHub?",
        answer: "A platform for hosting code repositories"
    },
    {
        question: "What is a Function?",
        answer: "A reusable block of code"
    },
    {
        question: "What is an Array?",
        answer: "A collection of values"
    },
    {
        question: "What is an Object?",
        answer: "A collection of key-value pairs"
    }
];

let currentCard = null;
let showingAnswer = false;

const card = document.getElementById("card");

function nextCard() {
    currentCard = cards[Math.floor(Math.random() * cards.length)];
    showingAnswer = false;
    card.textContent = currentCard.question;
}

card.addEventListener("click", () => {
    if (!currentCard) return;

    if (showingAnswer) {
        card.textContent = currentCard.question;
    } else {
        card.textContent = currentCard.answer;
    }

    showingAnswer = !showingAnswer;
});

nextCard();

</script>

</body>
</html>
