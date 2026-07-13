# apquize.com
My first project on Github
<br>
Author- Alok Patel

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EcoTech Quiz 🌍</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&amp;family=Roboto:wght@400;500&amp;display=swap');
        
        :root {
            --primary: #10b981;
            --secondary: #059669;
            --light: #ecfdf5;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #10b981, #065f46);
            color: #fff;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .quiz-container {
            background: white;
            color: #1f2937;
            max-width: 700px;
            width: 100%;
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgb(0 0 0 / 0.25);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            color: white;
            padding: 25px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 2.2rem;
            margin-bottom: 8px;
        }
        
        .header p {
            opacity: 0.9;
            font-size: 1.1rem;
        }
        
        .progress {
            height: 6px;
            background: #10b981;
            transition: width 0.4s ease;
        }
        
        .quiz-body {
            padding: 40px;
        }
        
        .question-number {
            font-size: 1rem;
            color: #6b7280;
            margin-bottom: 10px;
            font-weight: 500;
        }
        
        .question {
            font-size: 1.5rem;
            line-height: 1.4;
            margin-bottom: 30px;
            font-weight: 600;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .option {
            padding: 16px 20px;
            background: #f8fafc;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .option:hover {
            border-color: var(--primary);
            background: #ecfdf5;
            transform: translateX(8px);
        }
        
        .option.selected {
            border-color: var(--primary);
            background: #ecfdf5;
            font-weight: 500;
        }
        
        .btn {
            margin-top: 30px;
            padding: 14px 32px;
            font-size: 1.1rem;
            font-weight: 600;
            border: none;
            border-radius: 9999px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn-next {
            background: var(--primary);
            color: white;
            width: 100%;
        }
        
        .btn-next:hover {
            background: #059669;
            transform: scale(1.02);
        }
        
        .btn-restart {
            background: #64748b;
            color: white;
        }
        
        .results {
            text-align: center;
            padding: 40px 20px;
        }
        
        .score-circle {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 20px auto;
            font-size: 3rem;
            font-weight: 700;
            position: relative;
        }
        
        .score-circle::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 12px solid #10b981;
            border-top-color: #e2e8f0;
        }
        
        .feedback {
            font-size: 1.3rem;
            margin: 20px 0;
            color: var(--secondary);
        }
        
        .eco-icon {
            font-size: 3rem;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <!-- Header -->
        <div class="header">
            <h1>🌱 EcoTech Quiz</h1>
            <p>Test your knowledge of eco-friendly technology</p>
        </div>
        
        <!-- Progress Bar -->
        <div id="progress" class="progress" style="width: 0%"></div>
        
        <!-- Quiz Content -->
        <div id="quiz-body" class="quiz-body">
            <!-- Dynamic content injected by JS -->
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Which of the following is a major renewable energy source?",
                options: [
                    "Coal",
                    "Natural Gas",
                    "Solar Power",
                    "Diesel"
                ],
                correct: 2
            },
            {
                question: "What does the term 'carbon footprint' refer to?",
                options: [
                    "The size of your shoe",
                    "Total greenhouse gas emissions caused by an individual or activity",
                    "The area of forest needed to absorb CO₂",
                    "A type of shoe made from recycled materials"
                ],
                correct: 1
            },
            {
                question: "Which technology helps reduce emissions in transportation?",
                options: [
                    "Gasoline engines",
                    "Electric Vehicles (EVs)",
                    "Diesel trucks",
                    "Steam engines"
                ],
                correct: 1
            },
            {
                question: "What is the primary benefit of green roofs on buildings?",
                options: [
                    "They look pretty",
                    "They reduce urban heat island effect and improve insulation",
                    "They increase building height",
                    "They block sunlight"
                ],
                correct: 1
            },
            {
                question: "Which of these is an example of circular economy in tech?",
                options: [
                    "Buying a new phone every year",
                    "Recycling old electronics and recovering rare metals",
                    "Throwing away broken devices",
                    "Using single-use plastic packaging"
                ],
                correct: 1
            },
            {
                question: "What does LED stand for in energy-efficient lighting?",
                options: [
                    "Light Emitting Diode",
                    "Low Energy Device",
                    "Long-lasting Electric Display",
                    "Light Energy Distributor"
                ],
                correct: 0
            },
            {
                question: "How do smart grids contribute to sustainability?",
                options: [
                    "By increasing electricity consumption",
                    "By optimizing energy distribution and integrating renewables",
                    "By shutting down power plants",
                    "By using more fossil fuels"
                ],
                correct: 1
            },
            {
                question: "What is the main advantage of vertical farming?",
                options: [
                    "It requires more land",
                    "It uses significantly less water and land while reducing transport emissions",
                    "It grows only one type of crop",
                    "It increases pesticide use"
                ],
                correct: 1
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let selectedAnswer = null;

        const quizBody = document.getElementById('quiz-body');
        const progressBar = document.getElementById('progress');

        function renderQuestion() {
            const q = questions[currentQuestion];
            
            let html = `
                <div class="question-number">Question ${currentQuestion + 1} of ${questions.length}</div>
                <div class="question">${q.question}</div>
                <div class="options" id="options">
            `;
            q.options.forEach((option, index) => {
                html += `
                    <div class="option" data-index="${index}">
                        ${String.fromCharCode(65 + index)}. ${option}
                    </div>
                `;
            });
            html += `</div>`;
            
            if (currentQuestion < questions.length - 1) {
                html += `
                    <button class="btn btn-next" id="next-btn" disabled>Next Question →</button>
                `;
            } else {
                html += `
                    <button class="btn btn-next" id="next-btn" disabled>Finish Quiz</button>
                `;
            }
            
            quizBody.innerHTML = html;
            
            // Add click handlers
            const options = document.querySelectorAll('.option');
            options.forEach(option => {
                option.addEventListener('click', () => {
                    options.forEach(opt => opt.classList.remove('selected'));
                    option.classList.add('selected');
                    selectedAnswer = parseInt(option.getAttribute('data-index'));
                    document.getElementById('next-btn').disabled = false;
                });
            });
            
            // Next button
            document.getElementById('next-btn').addEventListener('click', () => {
                if (selectedAnswer === q.correct) {
                    score++;
                }
                
                currentQuestion++;
                
                if (currentQuestion < questions.length) {
                    renderQuestion();
                } else {
                    showResults();
                }
                
                updateProgress();
            });
            
            updateProgress();
            selectedAnswer = null;
        }

        function updateProgress() {
            const progress = ((currentQuestion) / questions.length) * 100;
            progressBar.style.width = `${progress}%`;
        }

        function showResults() {
            const percentage = Math.round((score / questions.length) * 100);
            
            let feedback = '';
            if (percentage >= 80) {
                feedback = "🌟 Outstanding! You're a true Eco-Warrior!";
            } else if (percentage >= 60) {
                feedback = "👏 Great job! You know your green tech well.";
            } else if (percentage >= 40) {
                feedback = "👍 Not bad! Keep learning about sustainable technology.";
            } else {
                feedback = "🌱 There's room to grow! Every small step counts.";
            }
            
            quizBody.innerHTML = `
                <div class="results">
                    <div class="eco-icon">🌍</div>
                    <h2>Your Eco Score</h2>
                    <div class="score-circle" style="background: conic-gradient(#10b981 ${percentage * 3.6}deg, #e2e8f0 0deg);">
                        <span>\( {score}/ \){questions.length}</span>
                    </div>
                    <div class="feedback">${percentage}%</div>
                    <p style="font-size: 1.3rem; margin: 15px 0;">${feedback}</p>
                    <button class="btn btn-restart" onclick="restartQuiz()">Restart Quiz</button>
                    
                    <div style="margin-top: 40px; font-size: 0.95rem; color: #64748b;">
                        Share your score and spread awareness about eco-friendly technology!
                    </div>
                </div>
            `;
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            renderQuestion();
        }

        // Initialize the quiz
        renderQuestion();
    </script>
</body>
</html>