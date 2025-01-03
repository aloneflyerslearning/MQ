<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>कक्षा 10 गणित प्रश्नोत्तरी</title>
    <style>
        body {
            font-family: sans-serif;
            background-color: #f0f8ff;
            color: #333;
        }
        h1 {
            text-align: center;
            color: #2196F3;
        }
        .quiz-container {
            width: 80%;
            margin: 20px auto;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
             max-width: 700px;
        }
        .question {
            margin-bottom: 20px;
            border: 1px solid #ddd;
            padding: 15px;
            border-radius: 5px;
             background-color: #e6f7ff;
        }
        .question p {
             font-weight: bold;
             color: #2196F3;
         }
        label {
             display: block;
             margin-bottom: 8px;
             font-size: 16px;
             color: #444;
          }
        input[type="text"] {
             padding: 10px;
             margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
              width: calc(100% - 22px);
        }
        button {
           padding: 12px 20px;
            background-color: #4CAF50;
           color: white;
           border: none;
           border-radius: 5px;
            cursor: pointer;
           margin-top: 15px;
             transition: background-color 0.3s;
           margin-right: 10px;
         }
        button:hover {
            background-color: #367c39;
        }
       .nav-buttons {
            margin-top: 20px;
            text-align: center;
        }
       .results-container, .score-item {
            margin-top: 30px;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
             box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .score-item {
             border: 1px solid #ccc;
            margin-bottom: 10px;
        }
       .hidden { display: none; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>कक्षा 10 गणित प्रश्नोत्तरी</h1>
        <form id="quiz-form">
            <label for="username">नाम:</label>
            <input type="text" id="username" required><br><br>
            <div id="question-container"></div>
            <div class="nav-buttons">
                <button type="button" id="prev-btn" class="hidden">पिछला</button>
                <button type="button" id="next-btn">अगला</button>
            </div>
            <button type="submit" class="hidden" id="submit-btn">उत्तर सबमिट करें</button>
        </form>
         <div id="results" class="results-container hidden"></div>
         <div id="all-scores" class="results-container hidden"></div>
    </div>
    <script>
          const questions = [
            {
              question: "यदि एक द्विघात समीकरण के मूल 2 और 3 हैं, तो समीकरण क्या होगा?",
              options: ["x² - 5x + 6 = 0", "x² + 5x + 6 = 0", "x² - 5x - 6 = 0", "x² + 5x - 6 = 0"],
              correctAnswer: "x² - 5x + 6 = 0"
            },
            {
              question: "एक वृत्त की त्रिज्या 7 सेमी है। वृत्त का क्षेत्रफल ज्ञात कीजिए।",
              options: ["22 वर्ग सेमी", "44 वर्ग सेमी", "154 वर्ग सेमी", "156 वर्ग सेमी"],
              correctAnswer: "154 वर्ग सेमी"
            },
            {
              question: "यदि एक त्रिभुज के कोण 30°, 60°, और 90° हैं, तो यह कौन सा त्रिभुज है?",
              options: ["समबाहु त्रिभुज", "समद्विबाहु त्रिभुज", "विषमबाहु त्रिभुज", "समकोण त्रिभुज"],
              correctAnswer: "समकोण त्रिभुज"
            },
            {
              question: "यदि एक बेलन की त्रिज्या 5 सेमी है और ऊँचाई 10 सेमी है, तो उसका आयतन ज्ञात कीजिए।",
              options: ["500 घन सेमी", "785 घन सेमी", "250 घन सेमी", "100 घन सेमी"],
              correctAnswer: "785 घन सेमी"
            },
            {
              question: "एक समकोण त्रिभुज में, यदि कर्ण 13 सेमी है और एक भुजा 5 सेमी है, तो दूसरी भुजा की लंबाई ज्ञात कीजिए।",
              options: ["8 सेमी", "12 सेमी", "15 सेमी", "18 सेमी"],
              correctAnswer: "12 सेमी"
            },
             {
              question: "यदि एक शंकु की त्रिज्या 3 सेमी और ऊँचाई 4 सेमी है, तो शंकु का आयतन कितना होगा? (π = 3.14 लें)",
              options: ["37.68 घन सेमी", "18.84 घन सेमी", "150.72 घन सेमी", "50.24 घन सेमी"],
              correctAnswer: "37.68 घन सेमी"
             },
             {
              question: "दो समरूप त्रिभुजों की संगत भुजाओं का अनुपात 3:5 है। उनके क्षेत्रफलों का अनुपात क्या होगा?",
              options: ["3:5", "9:25", "5:3", "25:9"],
               correctAnswer: "9:25"
            },
           {
              question: "यदि एक समांतर चतुर्भुज का आधार 10 सेमी और ऊँचाई 8 सेमी है, तो उसका क्षेत्रफल कितना होगा?",
              options: ["40 वर्ग सेमी", "80 वर्ग सेमी", "160 वर्ग सेमी", "100 वर्ग सेमी"],
               correctAnswer: "80 वर्ग सेमी"
            },
           {
                question: "यदि किसी वृत्त की परिधि 44 सेमी है, तो उसका व्यास कितना होगा? (π = 22/7 लें)",
                options: ["7 सेमी", "14 सेमी", "28 सेमी", "21 सेमी"],
                correctAnswer: "14 सेमी"
           },
           {
                question: "एक घनाभ की लम्बाई 6 सेमी, चौड़ाई 4 सेमी, और ऊँचाई 2 सेमी है। उसका कुल पृष्ठीय क्षेत्रफल ज्ञात कीजिए।",
                options: ["48 वर्ग सेमी", "88 वर्ग सेमी", "72 वर्ग सेमी", "100 वर्ग सेमी"],
                correctAnswer: "88 वर्ग सेमी"
            },
            {
                question: "यदि sin A = 3/5, तो cos A का मान ज्ञात कीजिए।",
                 options: ["4/5", "5/3", "3/4", "5/4"],
                 correctAnswer: "4/5"
             },
            {
                question: "बिंदु (2, -3) किस चतुर्थांश में स्थित है?",
                options: ["प्रथम", "द्वितीय", "तृतीय", "चतुर्थ"],
                 correctAnswer: "चतुर्थ"
            },
           {
              question: "एक रेखाखंड के मध्यबिंदु के निर्देशांक (5, 2) हैं। यदि एक अंत बिंदु (2, -1) है, तो दूसरा अंत बिंदु ज्ञात कीजिए।",
              options: ["(8, 5)", "(3, 1)", "(12, 5)", "(5, 3)"],
               correctAnswer: "(8, 5)"
            },
           {
                question: "यदि एक समांतर श्रेणी का पहला पद 5 और सार्वअंतर 3 है, तो 10वां पद ज्ञात कीजिए।",
                options: ["32", "35", "23", "30"],
                correctAnswer: "32"
            },
            {
               question: "यदि दो सिक्कों को एक साथ उछाला जाता है, तो दोनों पर हेड आने की प्रायिकता क्या है?",
                options: ["1/2", "1/3", "1/4", "1/6"],
                 correctAnswer: "1/4"
            },
            {
               question: "यदि 2x + 3y = 12 और x - y = 1, तो x और y का मान ज्ञात कीजिए।",
                 options: ["x=3, y=2", "x=2, y=3", "x=4, y=1", "x=5, y=0"],
                  correctAnswer: "x=3, y=2"
            },
            {
                question: "यदि एक घन का आयतन 64 घन सेमी है, तो उसकी भुजा की लंबाई ज्ञात कीजिए।",
                options: ["4 सेमी", "8 सेमी", "16 सेमी", "2 सेमी"],
                correctAnswer: "4 सेमी"
            },
            {
                question: "एक लंब वृत्तीय बेलन में, यदि त्रिज्या 7 सेमी और ऊँचाई 10 सेमी है, तो वक्र पृष्ठीय क्षेत्रफल ज्ञात कीजिए।",
                options: ["440 वर्ग सेमी", "4400 वर्ग सेमी", "1540 वर्ग सेमी", "308 वर्ग सेमी"],
                correctAnswer: "440 वर्ग सेमी"
            },
           {
               question: "एक वृत्त की त्रिज्या 14 सेमी है। वृत्त का क्षेत्रफल ज्ञात कीजिए।",
               options: ["616 वर्ग सेमी", "154 वर्ग सेमी", "196 वर्ग सेमी", "88 वर्ग सेमी"],
               correctAnswer: "616 वर्ग सेमी"
            },
            {
                question: "यदि 10, 12, 15, x और 20 का माध्य 15 है, तो x का मान ज्ञात कीजिए।",
                 options: ["18", "15", "20", "13"],
                correctAnswer: "18"
            },
            {
                question: "यदि एक वृत्त का व्यास 28 सेमी है, तो वृत्त का क्षेत्रफल ज्ञात कीजिए।",
                options: ["616 वर्ग सेमी", "2464 वर्ग सेमी", "1232 वर्ग सेमी", "396 वर्ग सेमी"],
                 correctAnswer: "616 वर्ग सेमी"
            },
            {
                question: "यदि cos A = 12/13, तो tan A का मान ज्ञात कीजिए।",
                options: ["5/12", "13/5", "12/5", "5/13"],
                 correctAnswer: "5/12"
            },
           {
               question: "यदि एक घन का कुल पृष्ठीय क्षेत्रफल 216 वर्ग सेमी है, तो उसकी भुजा की लंबाई ज्ञात कीजिए।",
                options: ["6 सेमी", "9 सेमी", "12 सेमी", "10 सेमी"],
                 correctAnswer: "6 सेमी"
            },
           {
              question: "एक बेलन की त्रिज्या 3 सेमी और ऊँचाई 7 सेमी है, तो उसका वक्र पृष्ठीय क्षेत्रफल कितना होगा?",
               options: ["132 वर्ग सेमी", "66 वर्ग सेमी", "198 वर्ग सेमी", "264 वर्ग सेमी"],
                 correctAnswer: "132 वर्ग सेमी"
            },
           {
              question: "यदि A(2,3) और B(5,6) दो बिंदु हैं, तो उनके बीच की दूरी ज्ञात कीजिए।",
               options: ["√18", "√34", "√25", "√20"],
                 correctAnswer: "√18"
            },
           {
              question: "यदि एक समांतर चतुर्भुज का क्षेत्रफल 60 वर्ग सेमी है और आधार 12 सेमी है, तो ऊँचाई कितनी होगी?",
                options: ["5 सेमी", "10 सेमी", "15 सेमी", "20 सेमी"],
                  correctAnswer: "5 सेमी"
            },
           {
              question: "एक ठोस गोले की त्रिज्या 6 सेमी है, तो उसका आयतन कितना होगा?",
              options: ["904.32 घन सेमी", "150.72 घन सेमी", "113.04 घन सेमी", "56.52 घन सेमी"],
               correctAnswer: "904.32 घन सेमी"
             },
             {
                question: "यदि एक वृत्त का क्षेत्रफल 154 वर्ग सेमी है, तो उसकी त्रिज्या कितनी होगी?",
                options: ["7 सेमी", "14 सेमी", "21 सेमी", "3.5 सेमी"],
               correctAnswer: "7 सेमी"
             },
            {
                question: "यदि दो लंबवत रेखाओं के ढाल m1 और m2 हैं, तो उनके बीच का संबंध क्या होगा?",
                options: ["m1 * m2 = 1", "m1 + m2 = 0", "m1 * m2 = -1", "m1 = m2"],
                correctAnswer: "m1 * m2 = -1"
            },
           {
               question: "एक त्रिभुज के शीर्ष (1, 2), (3, 4), और (5, 1) हैं, तो त्रिभुज का क्षेत्रफल ज्ञात कीजिए।",
               options: ["4 वर्ग इकाई", "5 वर्ग इकाई", "6 वर्ग इकाई", "7 वर्ग इकाई"],
               correctAnswer: "5 वर्ग इकाई"
             }
        ];
        const quizForm = document.getElementById('quiz-form');
        const usernameInput = document.getElementById('username');
        const questionContainer = document.getElementById('question-container');
        const resultsDiv = document.getElementById('results');
        const allScoresDiv = document.getElementById('all-scores');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const submitBtn = document.getElementById('submit-btn');
        let currentQuestion = 0;
        let userScores = [];
        let userAnswers = {}; // Store user answers

      function renderQuestion(index) {
          let html = "";
          html += `<div class="question">
                  <p>${index + 1}. ${questions[index].question}</p>`;
            questions[index].options.forEach(option => {
                const isChecked = userAnswers[`question${index}`] === option ? "checked" : "";
                html += `
                   <input type="radio" name="question${index}" value="${option}" ${isChecked}>
                   <label>${option}</label><br>`;
            });
            html += `</div>`;
            questionContainer.innerHTML = html;

            if(index === 0){
                prevBtn.classList.add('hidden');
           } else {
                prevBtn.classList.remove('hidden');
          }
           if(index === questions.length-1){
              nextBtn.classList.add('hidden');
               submitBtn.classList.remove('hidden')
          }else {
             nextBtn.classList.remove('hidden');
             submitBtn.classList.add('hidden')
          }
      }

      renderQuestion(currentQuestion);

       nextBtn.addEventListener('click', function() {
            const selectedAnswer = document.querySelector(`input[name="question${currentQuestion}"]:checked`);
             if(selectedAnswer){
              userAnswers[`question${currentQuestion}`] = selectedAnswer.value;
             }
           if(currentQuestion < questions.length - 1) {
               currentQuestion++;
             renderQuestion(currentQuestion);
           }
       });
      prevBtn.addEventListener('click', function() {
         const selectedAnswer = document.querySelector(`input[name="question${currentQuestion}"]:checked`);
        if(selectedAnswer){
           userAnswers[`question${currentQuestion}`] = selectedAnswer.value;
       }
          if(currentQuestion > 0){
               currentQuestion--;
               renderQuestion(currentQuestion);
          }
      });

     quizForm.addEventListener('submit', function(event) {
          event.preventDefault();
          const username = usernameInput.value;

        let score = 0;
        let incorrectAnswers = [];
        questions.forEach((q, index) => {
           const userAnswer = userAnswers[`question${index}`];
            if (userAnswer === q.correctAnswer) {
              score++;
            } else if (userAnswer) {
                incorrectAnswers.push({
                     question: q.question,
                     userAnswer: userAnswer,
                     correctAnswer: q.correctAnswer
                   });
             }
        });
        let resultHTML = `<h2>परिणाम</h2><p>नमस्कार, ${username}!</p>`;
        resultHTML += `<p>आपका स्कोर: ${score} / ${questions.length}</p>`;
         if (incorrectAnswers.length > 0) {
           resultHTML += `<h3>गलत उत्तर</h3>`;
           incorrectAnswers.forEach((ans, index) => {
                resultHTML += `<p><b>प्रश्न:</b> ${ans.question}<br>
                   <b>आपका जवाब:</b> ${ans.userAnswer}<br>
                <b>सही जवाब:</b> ${ans.correctAnswer}</p>`;
             });
        }

          resultsDiv.innerHTML = resultHTML;
          resultsDiv.classList.remove('hidden');
           // Store User Data
          userScores.push({ username: username, score: score, incorrect:incorrectAnswers });
           // Display All Scores
           displayAllScores();
          allScoresDiv.classList.remove('hidden');
      });

     function displayAllScores() {
          let allScoresHTML = `<h2>सभी स्कोर</h2>`;
          if (userScores.length === 0) {
               allScoresHTML += `<p>कोई स्कोर उपलब्ध नहीं</p>`;
         } else {
            userScores.forEach(user => {
                  allScoresHTML += `<div class="score-item">
                     <p><b>नाम:</b> ${user.username}</p>
                       <p><b>स्कोर:</b> ${user.score} / ${questions.length}</p>`;
                   if (user.incorrect.length > 0) {
                       allScoresHTML += `<h3>गलत उत्तर</h3>`;
                     user.incorrect.forEach(ans => {
                        allScoresHTML += `<p><b>प्रश्न:</b> ${ans.question}<br>
                        <b>आपका जवाब:</b> ${ans.userAnswer}<br>
                        <b>सही जवाब:</b> ${ans.correctAnswer}</p>`;
                        });
                    }
                   allScoresHTML += `</div>`;
                });
         }
         allScoresDiv.innerHTML = allScoresHTML;
     }
 </script>
</body>
</html>