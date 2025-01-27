<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Progress Tracker</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to right, #6a11cb, #2575fc);
            color: #fff;
        }
        .container {
            max-width: 800px;
            margin: 30px auto; 
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }
        h1 {
            text-align: center;
            font-size: 28px;
            margin-bottom: 20px;
        }
        .input-group {
            margin-bottom: 15px;
        }
        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        .input-group input, .input-group textarea, .input-group select {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 5px;
            outline: none;
            background: rgba(255, 255, 255, 0.8);
            color: #333;
            font-size: 16px;
        }
        .button {
            text-align: center;
            margin-top: 20px;
        }
        .button button {
            background-color: #00c853;
            color: #fff;
            border: none;
            padding: 12px 30px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
            font-weight: 500;
            transition: background 0.3s;
        }
        .button button:hover {
            background-color: #00a347;
        }
        .message, .calendar-container {
            margin-top: 20px;
            padding: 15px;
            border-radius: 5px;
            font-size: 16px;
        }
        .calendar-container {
            background: rgba(255, 255, 255, 0.8);
            color: #333;
        }
        .message.good { background-color: #81c784; color: #1b5e20; }
        .message.average { background-color: #fff176; color: #f57f17; }
        .message.bad { background-color: #e57373; color: #b71c1c; }
        footer {
            text-align: center;
            margin-top: 30px;
            font-size: 14px;
            color: #ccc;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📚 Student Progress Tracker with Calendar</h1>
        <div class="input-group">
            <label for="name">अपना नाम दर्ज करें:</label>
            <input type="text" id="name" placeholder="अपना नाम लिखें">
        </div>
        <div class="input-group">
            <label for="hours">आज आपने कितने घंटे पढ़ाई की?</label>
            <input type="number" id="hours" placeholder="घंटों की संख्या दर्ज करें">
        </div>
        <div class="input-group">
            <label for="school-hours">स्कूल के घंटे (12:00 PM - 5:00 PM)आपने कितने घंटे पढ़ाई की?</label>
            <select id="school-hours">
                <option value="5">5 घंटे</option>
                <option value="4">4 घंटे</option>
                <option value="3">3 घंटे</option>
                <option value="2">2 घंटे</option>
                <option value="1">1 घंटे</option>
                <option value="0">0 घंटे</option>
            </select>
        </div>
        <div class="input-group">
            <label for="comments">आज का अनुभव कैसा रहा?</label>
            <textarea id="comments" rows="4" placeholder="अपना अनुभव साझा करें..."></textarea>
        </div>
        <div class="button">
            <button onclick="trackProgress()">सबमिट करें</button>
        </div>
        <div id="message" class="message"></div>
        <div class="calendar-container" id="calendar">
            <h2>प्रोग्रेस कैलेंडर</h2>
            <ul id="progress-list">
                <!-- Data will be appended here -->
            </ul>
        </div>
    </div>

    <footer>
        © 2025 Student Progress Tracker | प्रेरणा के साथ पढ़ाई करें!
    </footer>

    <script>
        let progressData = [];

        function trackProgress() {
            const name = document.getElementById('name').value.trim();
            const hours = document.getElementById('hours').value;
            const schoolHours = document.getElementById('school-hours').value;
            const comments = document.getElementById('comments').value.trim();
            const message = document.getElementById('message');

            if (!name || !hours) {
                message.innerHTML = 'कृपया अपना नाम और पढ़ाई के घंटे दर्ज करें।';
                message.className = 'message bad';
                return;
            }

            const totalHours = parseInt(hours) + parseInt(schoolHours);
            const date = new Date().toLocaleDateString();
            const newData = { date, name, totalHours, comments };

            // डेटा को डुप्लिकेशन से बचाने के लिए फ़िल्टर करें
            const existingData = progressData.find(data => data.date === date && data.name === name);
            if (!existingData) {
                progressData.push(newData);
                saveProgressToLocalStorage();
            }

            let feedback;
            if (totalHours >= 8) {
                feedback = `शानदार काम, ${name}! आपने कुल ${totalHours} घंटे पढ़ाई की। ऐसे ही मेहनत करते रहें!`;
                message.className = 'message good';
            } else if (totalHours >= 6) {
                feedback = `अच्छा प्रयास, ${name}! आपने कुल ${totalHours} घंटे पढ़ाई की। लेकिन और मेहनत करें!`;
                message.className = 'message average';
            } else {
                feedback = `काफी कम पढ़ाई की, ${name}. आपको ${totalHours} घंटे से ज्यादा पढ़ाई करनी चाहिए।`;
                message.className = 'message bad';
            }

            message.innerHTML = `
                <p>${feedback}</p>
                <p>आपका अनुभव: ${comments || 'कोई अनुभव साझा नहीं किया गया।'}</p>
            `;

            updateCalendar();
        }

        function updateCalendar() {
            const list = document.getElementById('progress-list');
            list.innerHTML = '';
            progressData.forEach(data => {
                const listItem = document.createElement('li');
                listItem.innerText = `${data.date} - ${data.name}: ${data.totalHours} घंटे (अनुभव: ${data.comments || 'नहीं दिया गया'})`;
                list.appendChild(listItem);
            });
        }

        // लोकल स्टोरेज में डेटा स्टोर करें
        function saveProgressToLocalStorage() {
            localStorage.setItem('progressData', JSON.stringify(progressData));
        }

        // लोकल स्टोरेज से डेटा लोड करें
        function loadProgressFromLocalStorage() {
            const storedData = localStorage.getItem('progressData');
            if (storedData) {
                progressData = JSON.parse(storedData);
                updateCalendar();
            }
        }

        // पेज लोड होने पर पुराना डेटा लोड करें
        document.addEventListener('DOMContentLoaded', loadProgressFromLocalStorage);
    </script>
</body>
</html>
