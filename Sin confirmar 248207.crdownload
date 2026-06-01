
let currentQuestion = 0;
let score = 0;
let answered = false;

const questionContainer = document.getElementById('question-container');
const nextBtn = document.getElementById('next-btn');

function renderQuestion() {
    answered = false;

    const q = questions[currentQuestion];

    questionContainer.innerHTML = `
        <h2>Pregunta ${currentQuestion + 1} de ${questions.length}</h2>
<h3>${q.q}</h3>
        <div class="options">
            ${q.options.map((option, index) => `
                <button class="option-btn" onclick="selectAnswer(${index}, this)">
                    ${option}
                </button>
            `).join('')}
        </div>
    `;

    updateProgress();
}

window.selectAnswer = function(index, element) {
    if(answered) return;

    answered = true;

    const q = questions[currentQuestion];
    const buttons = document.querySelectorAll('.option-btn');

    buttons[q.correct].classList.add('correct');

    if(index === q.correct) {
        score++;
    } else {
        element.classList.add('incorrect');
    }

    document.getElementById('score').innerText =
        `Puntuación: ${score} / ${questions.length}`;
}

nextBtn.addEventListener('click', () => {
    if(!answered){
        alert('Selecciona una respuesta');
        return;
    }

    currentQuestion++;

    if(currentQuestion >= questions.length){
        showFinalResult();
        return;
    }

    renderQuestion();
});

function updateProgress() {
    const progress = ((currentQuestion) / questions.length) * 100;
    document.getElementById('progress-bar').style.width = progress + '%';
}

function showFinalResult() {
    questionContainer.innerHTML = `
        <div class="final-card">
            <h2>Examen finalizado</h2>
            <p>Resultado final:</p>
            <div class="final-score">${score} / ${questions.length}</div>
        </div>
    `;

    nextBtn.style.display = 'none';

    document.getElementById('progress-bar').style.width = '100%';
}

renderQuestion();
