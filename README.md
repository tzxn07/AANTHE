[aanthe.html](https://github.com/user-attachments/files/22129916/aanthe.html)
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>เกมทดสอบ A, An, The</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
       
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
       
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }
       
        header {
            text-align: center;
            margin-bottom: 40px;
        }
       
        h1 {
            color: white;
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
       
        .subtitle {
            color: #f0f0f0;
            font-size: 1.2em;
        }
       
        .menu-card {
            background: white;
            border-radius: 20px;
            padding: 40px;
            margin: 20px 0;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            text-align: center;
        }
       
        .btn {
            background: linear-gradient(45deg, #ff6b6b, #ffa500);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2em;
            border-radius: 50px;
            cursor: pointer;
            margin: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
       
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
        }
       
        .btn.secondary {
            background: linear-gradient(45deg, #4ecdc4, #44a08d);
        }
       
        .quiz-container, .lesson-container {
            display: none;
        }
       
        .question-card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            margin: 20px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
       
        .question-number {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            display: inline-block;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            margin-bottom: 15px;
        }
       
        .question-text {
            font-size: 1.3em;
            margin-bottom: 20px;
            line-height: 1.5;
            color: #333;
        }
       
        .options {
            display: grid;
            gap: 10px;
        }
       
        .option {
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            padding: 15px 20px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.1em;
        }
       
        .option:hover {
            background: #e3f2fd;
            border-color: #2196F3;
        }
       
        .option.selected {
            background: #e3f2fd;
            border-color: #2196F3;
        }
       
        .option.correct {
            background: #d4edda !important;
            border-color: #28a745 !important;
            color: #155724;
        }
       
        .option.wrong {
            background: #f8d7da !important;
            border-color: #dc3545 !important;
            color: #721c24;
        }
       
        .feedback {
            margin-top: 15px;
            padding: 15px;
            border-radius: 10px;
            display: none;
        }
       
        .feedback.correct {
            background: #d4edda;
            border: 1px solid #c3e6cb;
            color: #155724;
        }
       
        .feedback.wrong {
            background: #f8d7da;
            border: 1px solid #f5c6cb;
            color: #721c24;
        }
       
        .progress-bar {
            width: 100%;
            height: 10px;
            background: #e9ecef;
            border-radius: 5px;
            overflow: hidden;
            margin: 20px 0;
        }
       
        .progress-fill {
            height: 100%;
            background: linear-gradient(45deg, #ff6b6b, #ffa500);
            width: 0%;
            transition: width 0.3s ease;
        }
       
        .results {
            text-align: center;
            padding: 30px;
            background: white;
            border-radius: 20px;
            margin: 20px 0;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
        }
       
        .score {
            font-size: 3em;
            font-weight: bold;
            margin: 20px 0;
        }
       
        .score.excellent { color: #28a745; }
        .score.good { color: #17a2b8; }
        .score.fair { color: #ffc107; }
        .score.poor { color: #dc3545; }
       
        .lesson-content {
            background: white;
            border-radius: 20px;
            padding: 40px;
            margin: 20px 0;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            line-height: 1.8;
        }
       
        .lesson-content h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 1.8em;
        }
       
        .lesson-content h3 {
            color: #764ba2;
            margin: 25px 0 15px 0;
            font-size: 1.4em;
        }
       
        .example {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            border-left: 4px solid #667eea;
        }
       
        .trick-box {
            background: linear-gradient(45deg, #fff3e0, #ffe0b2);
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
            border: 2px solid #ff9800;
        }
       
        .back-btn {
            position: fixed;
            top: 20px;
            left: 20px;
            background: rgba(255,255,255,0.2);
            color: white;
            border: 2px solid white;
            padding: 10px 20px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
       
        .back-btn:hover {
            background: white;
            color: #667eea;
        }
       
        .credits {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(255,255,255,0.9);
            border-radius: 15px;
            padding: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }
       
        .credits:hover {
            background: white;
            transform: scale(1.05);
        }
       
        .credits-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
        }
       
        .credits-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            max-width: 500px;
            width: 90%;
        }
       
       
       
       
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
           
            h1 {
                font-size: 2em;
            }
           
            .menu-card {
                padding: 20px;
            }
           
            .question-card {
                padding: 20px;
            }
        }
        .team-container {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  justify-content: center;
  margin-top: 20px;
}


/* กล่องบุคคล */
.team-member {
  background: #fff;
  border-radius: 12px;
  padding: 15px;
  width: 200px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0,0,0,0.15);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}


.team-member:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.25);
}


/* รูปโปรไฟล์ */
.member-photo {
  width: 100px;
  height: 100px;
  background: #ccc;
  border-radius: 50%;
  margin: 0 auto 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  font-weight: bold;
  color: #fff;
  background: linear-gradient(135deg, #6a11cb, #2575fc);
}


.member-info p {
  margin: 5px 0;
}
    </style>
</head>
<body>
    <div class="container">
        <!-- หน้าแรก -->
        <div id="home-page">
            <header>
                <h1>🎓 เกมทดสอบ A, An, The</h1>
                <p class="subtitle">เรียนรู้และทดสอบความรู้เรื่อง Articles ในภาษาอังกฤษ</p>
            </header>
           
            <div class="menu-card">
                <h2>เลือกกิจกรรมที่ต้องการ</h2>
                <button class="btn" onclick="startQuiz()">📝 ทำข้อสอบ</button>
                <button class="btn secondary" onclick="showLesson()">📚 ให้ความรู้</button>
            </div>
        </div>
       
        <!-- หน้าข้อสอบ -->
        <div id="quiz-page" class="quiz-container">
            <button class="back-btn" onclick="goHome()">← กลับหน้าแรก</button>
           
            <header>
                <h1>📝 ข้อสอบ A, An, The</h1>
                <div class="progress-bar">
                    <div class="progress-fill" id="progress"></div>
                </div>
            </header>
           
            <div id="question-container"></div>
           
            <div id="results-container" style="display: none;">
                <div class="results">
                    <h2>🎉 ผลการทดสอบ</h2>
                    <div class="score" id="final-score"></div>
                    <p id="score-message"></p>
                    <button class="btn" onclick="showAnswers()">ดูเฉลย</button>
                    <button class="btn secondary" onclick="restartQuiz()">ทำใหม่</button>
                </div>
            </div>
           
            <div id="answers-container" style="display: none;"></div>
        </div>
       
        <!-- หน้าบทเรียน -->
        <div id="lesson-page" class="lesson-container">
            <button class="back-btn" onclick="goHome()">← กลับหน้าแรก</button>
           
            <header>
                <h1>📚 บทเรียน A, An, The</h1>
            </header>
           
            <div class="lesson-content">
                <h2>🔹 1. A / An (ไม่เจาะจง)</h2>
                <p>ใช้กับ <strong>สิ่งของที่พูดถึงครั้งแรก</strong> หรือ <strong>ไม่ได้ระบุชัดเจนว่าอันไหน</strong></p>
               
                <h3>A → ใช้หน้าคำนามที่ขึ้นเสียงพยัญชนะ</h3>
                <div class="example">
                    <strong>ตัวอย่าง:</strong><br>
                    • a cat, a book, a university (ออกเสียง "ยู" → ถือเป็นพยัญชนะ)<br>
                    • a one-hour meeting (one ออกเสียง "วัน")
                </div>
               
                <h3>An → ใช้หน้าคำนามที่ขึ้นเสียงสระ (a, e, i, o, u)</h3>
                <div class="example">
                    <strong>ตัวอย่าง:</strong><br>
                    • an apple, an elephant, an hour (h ไม่ออกเสียง → ถือเป็นสระ)<br>
                    • an honest person (h ไม่ออกเสียง)
                </div>
               
                <h2>🔹 2. The (เจาะจง)</h2>
                <p>ใช้เมื่อ <strong>ทุกคนรู้ว่าพูดถึงสิ่งไหนแน่ๆ</strong> หรือ <strong>พูดถึงสิ่งนั้นเป็นครั้งที่สองขึ้นไป</strong></p>
               
                <div class="example">
                    <strong>การใช้ The:</strong><br>
                    • สิ่งที่มีอันเดียวในโลก → the sun, the moon, the Earth<br>
                    • พูดถึงสิ่งที่เคยเอ่ยไปแล้ว → I saw a dog. The dog was very cute.<br>
                    • สถานที่สำคัญ → the Great Wall, the Eiffel Tower<br>
                    • คำขั้นสูงสุด → the best, the most beautiful<br>
                    • ทิศทาง → the east, the west<br>
                    • เครื่องดนตรี → play the guitar, the piano
                </div>
               
                <div class="trick-box">
                    <h3>🎯 ทริคจำง่ายๆ</h3>
                    <p><strong>1. a / an = ใหม่ ไม่เจาะจง</strong></p>
                    <p><strong>2. the = รู้แล้ว เจาะจงแน่ๆ</strong></p>
                    <p><strong>3. เวลาสงสัยว่าใช้ a หรือ an → ฟังเสียงตัวแรก ไม่ใช่ดูตัวสะกด</strong></p>
                    <div class="example">
                        • "an hour" (h ไม่ออกเสียง → เสียงสระ)<br>
                        • "a university" (ยู = เสียงพยัญชนะ)
                    </div>
                </div>
               
                <h2>🔹 3. เมื่อไหร่ที่ไม่ใช้ Article</h2>
                <div class="example">
                    • คำนามนามธรรม → Knowledge is power<br>
                    • คำนามทั่วไป (uncountable) → I like milk<br>
                    • ชื่อประเทศส่วนใหญ่ → Thailand, Japan<br>
                    • ชื่อคน → John, Mary<br>
                    • มื้ออาหาร → have breakfast, lunch, dinner
                </div>
            </div>
        </div>
    </div>
   
    <!-- ปุ่มผู้จัดทำ -->
    <div class="credits" onclick="showCredits()">
        👥 ผู้จัดทำ
    </div>
   
    <!-- Modal ผู้จัดทำ -->
<div id="credits-modal" class="credits-modal" onclick="hideCredits()">
  <div class="credits-content" onclick="event.stopPropagation()">
    <h2>👥 ผู้จัดทำ</h2>
   
    <!-- กล่องใหญ่ที่รวมทั้งหมด -->
    <div class="team-container">


      <!-- กล่องรายบุคคล -->
      <div class="team-member">
  <div class="member-photo">
    <img src="data:image/jpeg;base64,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"
         alt="Profile"
         style="width:100%; height:100%; border-radius: 50%; object-fit: cover;">
  </div>
  <div class="member-info">
    <p><strong>นายปัณณธร คงเอียด</strong></p>
    <p>ชั้น ม.6/6 เลขที่ 3</p>
  </div>
</div>


     
      <!-- <div class="team-member">
        <div class="member-photo">B</div>
        <div class="member-info">
          <p><strong>นาย ข นามสกุล</strong></p>
          <p>ชั้น ม.4/1 เลขที่ 2</p>
        </div>
      </div>


      <div class="team-member">
        <div class="member-photo">C</div>
        <div class="member-info">
          <p><strong>นาย ค นามสกุล</strong></p>
          <p>ชั้น ม.4/1 เลขที่ 3</p>
        </div>
      </div> -->


    </div>


    <button class="btn" onclick="hideCredits()" style="margin-top: 20px;">ปิด</button>
  </div>
</div>




    <script>


       
        // ข้อมูลข้อสอบ
        const questions = [
            {
                question: "She is ___ honest student who always tells the truth.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 1,
                explanation: "ใช้ 'an' หน้าคำขึ้นต้นด้วยเสียงสระ → honest ออกเสียง /ɒnɪst/ (h ไม่ออกเสียง)"
            },
            {
                question: "We stayed at ___ hotel near the Eiffel Tower last summer.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 0,
                explanation: "ใช้ 'a' เพราะ hotel เริ่มด้วยเสียงพยัญชนะ /h/ และเป็นการพูดถึงครั้งแรก"
            },
            {
                question: "I need ___ hour to finish my homework.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 1,
                explanation: "ใช้ 'an' เพราะ hour ออกเสียง /aʊər/ ไม่มีเสียง h (เริ่มด้วยเสียงสระ)"
            },
            {
                question: "He wants to buy ___ new car that can run faster than his old one.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 0,
                explanation: "ใช้ 'a' เพราะ new ขึ้นต้นด้วยเสียงพยัญชนะ /n/ และเป็นรถยนต์คันหนึ่งที่ไม่เจาะจง"
            },
            {
                question: "My father reads ___ Times every morning.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ Times เป็นชื่อหนังสือพิมพ์ที่เฉพาะเจาะจง"
            },
            {
                question: "Do you know ___ man who is standing at the door?",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะเป็นการระบุเจาะจงชายคนที่ยืนอยู่หน้าประตู"
            },
            {
                question: "Mount Everest is ___ highest mountain in the world.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ highest เป็น superlative (ขั้นสูงสุด) ต้องใช้ the เสมอ"
            },
            {
                question: "She doesn't like to drink ___ milk, but she likes coffee.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 3,
                explanation: "ไม่ต้องใส่ เพราะ milk เป็น uncountable noun ที่ใช้ในความหมายทั่วไป"
            },
            {
                question: "I saw ___ university student carrying books in the library.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 0,
                explanation: "ใช้ 'a' เพราะ university ขึ้นต้นด้วยเสียง /juː/ ซึ่งเป็นเสียงพยัญชนะ"
            },
            {
                question: "They are going to build ___ bridge over the river.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 0,
                explanation: "ใช้ 'a' เพราะ bridge เป็นคำนามนับได้ที่ยังไม่เฉพาะเจาะจง"
            },
            {
                question: "There is ___ apple and two oranges on the table.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 1,
                explanation: "ใช้ 'an' เพราะ apple เริ่มด้วยเสียงสระ /æ/"
            },
            {
                question: "Yesterday I met ___ European businessman at the airport.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 0,
                explanation: "ใช้ 'a' เพราะ European ขึ้นต้นด้วยเสียง /juː/ ซึ่งเป็นเสียงพยัญชนะ"
            },
            {
                question: "The teacher told us to open our books at page 45 in ___ middle of the lesson.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ 'in the middle of' เป็น expression ที่ใช้ the เสมอ"
            },
            {
                question: "We don't usually watch TV in ___ evening.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ evening เป็น time expression ที่ใช้กับ the"
            },
            {
                question: "This is ___ most interesting story I've ever read.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ 'the most' เป็น superlative form ที่ต้องใช้ the"
            },
            {
                question: "The sun rises in ___ east and sets in ___ west.",
                options: ["a, a", "an, an", "the, the", "ไม่ต้องใส่, ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the, the' เพราะทิศทางต้องใช้ the เสมอ (the east, the west)"
            },
            {
                question: "She works in ___ office near the train station.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 1,
                explanation: "ใช้ 'an' เพราะ office เริ่มด้วยเสียงสระ /ɒ/"
            },
            {
                question: "They went to ___ church to attend a wedding.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะไปโบสถ์เฉพาะแห่งหนึ่งเพื่อจุดประสงค์เฉพาะ (เข้าร่วมงานแต่ง)"
            },
            {
                question: "He is ___ best player in our football team.",
                options: ["a", "an", "the", "ไม่ต้องใส่"],
                correct: 2,
                explanation: "ใช้ 'the' เพราะ 'the best' เป็น superlative ที่ต้องใช้ the"
            },
            {
                question: "___ knowledge is power.",
                options: ["A", "An", "The", "ไม่ต้องใส่"],
                correct: 3,
                explanation: "ไม่ต้องใส่ เพราะ knowledge เป็น abstract noun ที่ใช้ในความหมายทั่วไป"
            }
        ];


        let currentQuestion = 0;
        let score = 0;
        let userAnswers = [];
        let isAnswered = false;


        function goHome() {
            document.getElementById('home-page').style.display = 'block';
            document.getElementById('quiz-page').style.display = 'none';
            document.getElementById('lesson-page').style.display = 'none';
        }


        function startQuiz() {
            document.getElementById('home-page').style.display = 'none';
            document.getElementById('quiz-page').style.display = 'block';
            currentQuestion = 0;
            score = 0;
            userAnswers = [];
            showQuestion();
        }


        function showLesson() {
            document.getElementById('home-page').style.display = 'none';
            document.getElementById('lesson-page').style.display = 'block';
        }


        function showQuestion() {
            if (currentQuestion >= questions.length) {
                showResults();
                return;
            }


            isAnswered = false;
            const question = questions[currentQuestion];
            const progress = ((currentQuestion) / questions.length) * 100;
            document.getElementById('progress').style.width = progress + '%';


            const questionHTML = `
                <div class="question-card">
                    <div class="question-number">คำถามข้อที่ ${currentQuestion + 1} จาก ${questions.length}</div>
                    <div class="question-text">${question.question}</div>
                    <div class="options">
                        ${question.options.map((option, index) =>
                            `<div class="option" onclick="selectAnswer(${index})">${option}</div>`
                        ).join('')}
                    </div>
                    <div class="feedback" id="feedback"></div>
                    <button class="btn" id="next-btn" onclick="nextQuestion()" style="display: none; margin-top: 20px;">คำถามต่อไป</button>
                </div>
            `;
           
            document.getElementById('question-container').innerHTML = questionHTML;
        }


        function selectAnswer(selectedIndex) {
            if (isAnswered) return;
           
            isAnswered = true;
            const question = questions[currentQuestion];
            const options = document.querySelectorAll('.option');
            const feedback = document.getElementById('feedback');
           
            userAnswers[currentQuestion] = selectedIndex;
           
            options.forEach((option, index) => {
                if (index === question.correct) {
                    option.classList.add('correct');
                } else if (index === selectedIndex) {
                    option.classList.add('wrong');
                }
                option.style.pointerEvents = 'none';
            });


            if (selectedIndex === question.correct) {
                score++;
                feedback.className = 'feedback correct';
                feedback.innerHTML = `✅ ถูกต้อง! <br><strong>เหตุผล:</strong> ${question.explanation}`;
            } else {
                feedback.className = 'feedback wrong';
                feedback.innerHTML = `❌ ผิด! คำตอบที่ถูกต้องคือ "${question.options[question.correct]}" <br><strong>เหตุผล:</strong> ${question.explanation}`;
            }
           
            feedback.style.display = 'block';
            document.getElementById('next-btn').style.display = 'inline-block';
        }


        function nextQuestion() {
            currentQuestion++;
            showQuestion();
        }


        function showResults() {
            const progress = 100;
            document.getElementById('progress').style.width = progress + '%';
           
            const percentage = (score / questions.length) * 100;
            const scoreElement = document.getElementById('final-score');
            const messageElement = document.getElementById('score-message');
           
            scoreElement.textContent = `${score}/${questions.length}`;
           
            if (percentage >= 90) {
                scoreElement.className = 'score excellent';
                messageElement.textContent = '🌟 ยอดเยี่ยม! คุณเข้าใจการใช้ a, an, the เป็นอย่างดี!';
            } else if (percentage >= 70) {
                scoreElement.className = 'score good';
                messageElement.textContent = '👍 ดีมาก! คุณมีความรู้ดีแล้ว แต่ยังต้องฝึกฝนอีกนิดนึง';
            } else if (percentage >= 50) {
                scoreElement.className = 'score fair';
                messageElement.textContent = '📚 พอใช้ ควรอ่านบทเรียนเพิ่มเติมและฝึกฝนต่อไป';
            } else {
                scoreElement.className = 'score poor';
                messageElement.textContent = '💪 ต้องฝึกฝนมากกว่านี้ แนะนำให้อ่านบทเรียนก่อนทำข้อสอบใหม่';
            }
           
            document.getElementById('question-container').style.display = 'none';
            document.getElementById('results-container').style.display = 'block';
        }


        function showAnswers() {
            let answersHTML = '<div class="results"><h2>📋 เฉลยข้อสอบ</h2></div>';
           
            questions.forEach((question, index) => {
                const userAnswer = userAnswers[index];
                const isCorrect = userAnswer === question.correct;
               
                answersHTML += `
                    <div class="question-card">
                        <div class="question-number">ข้อที่ ${index + 1}</div>
                        <div class="question-text">${question.question}</div>
                        <p><strong>คำตอบที่ถูก:</strong> <span style="color: #28a745;">${question.options[question.correct]}</span></p>
                        <p><strong>คำตอบของคุณ:</strong> <span style="color: ${isCorrect ? '#28a745' : '#dc3545'};">${userAnswer !== undefined ? question.options[userAnswer] : 'ไม่ได้ตอบ'}</span> ${isCorrect ? '✅' : '❌'}</p>
                        <div class="feedback correct" style="display: block;">
                            <strong>เหตุผล:</strong> ${question.explanation}
                        </div>
                    </div>
                `;
            });
           
            answersHTML += `
                <div style="text-align: center; margin: 30px 0;">
                    <button class="btn" onclick="restartQuiz()">ทำข้อสอบใหม่</button>
                    <button class="btn secondary" onclick="goHome()">กลับหน้าแรก</button>
                </div>
            `;
           
            document.getElementById('answers-container').innerHTML = answersHTML;
            document.getElementById('results-container').style.display = 'none';
            document.getElementById('answers-container').style.display = 'block';
        }


        function restartQuiz() {
            document.getElementById('results-container').style.display = 'none';
            document.getElementById('answers-container').style.display = 'none';
            document.getElementById('question-container').style.display = 'block';
            currentQuestion = 0;
            score = 0;
            userAnswers = [];
            showQuestion();
        }


        function showCredits() {
            document.getElementById('credits-modal').style.display = 'block';
        }


        function hideCredits() {
            document.getElementById('credits-modal').style.display = 'none';
        }


        // เพิ่ม event listener สำหรับปิด modal เมื่อกด Escape
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                hideCredits();
            }
        });
    </script>
</body>
</html>

