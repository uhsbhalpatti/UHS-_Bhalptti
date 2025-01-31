<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Attendance System</title>

    <!-- Firebase SDK -->
    <script type="module">
        import { initializeApp } from 'https://www.gstatic.com/firebasejs/9.19.1/firebase-app.js';
        import { getDatabase, ref, set, push, get, child } from 'https://www.gstatic.com/firebasejs/9.19.1/firebase-database.js';

        // Firebase Configuration
        const firebaseConfig = {
            apiKey: "AIzaSyDrd-WaRLM6C2Z5ZlCkhN20sXUObxUUYX0",
            authDomain: "edugine-01.firebaseapp.com",
            databaseURL: "https://edugine-01-default-rtdb.asia-southeast1.firebasedatabase.app",
            projectId: "edugine-01",
            storageBucket: "edugine-01.firebasestorage.app",
            messagingSenderId: "556004873116",
            appId: "1:556004873116:web:e1a41b28052a88d0432e59",
            measurementId: "G-MVSWT657FP"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const database = getDatabase(app);

        // 1️⃣ **नया स्टूडेंट जोड़ना**
        window.addStudent = () => {
            const name = document.getElementById('student-name').value;
            const rollNumber = document.getElementById('student-roll-number').value;
            const section = document.getElementById('student-section').value;

            if (!name || !rollNumber || !section) {
                alert("कृपया सभी फ़ील्ड भरें!");
                return;
            }

            const studentRef = push(ref(database, 'students/11'));
            set(studentRef, {
                name: name,
                rollNumber: rollNumber,
                section: section
            }).then(() => {
                alert("स्टूडेंट जोड़ा गया!");
                document.getElementById('student-form').reset();
            }).catch(error => {
                alert("Error: " + error.message);
            });
        };

        // 2️⃣ **अटेंडेंस दर्ज करना**
        window.submitAttendance = () => {
            const rollNumber = document.getElementById('attendance-roll-number').value;
            const section = document.getElementById('attendance-section').value;
            const date = document.getElementById('attendance-date').value;
            const status = document.querySelector('input[name="attendance"]:checked');

            if (!rollNumber || !section || !date || !status) {
                alert("सभी फ़ील्ड भरें!");
                return;
            }

            const studentRef = ref(database, 'students/11');
            get(studentRef).then(snapshot => {
                let found = false;
                snapshot.forEach(childSnapshot => {
                    const student = childSnapshot.val();
                    if (student.rollNumber == rollNumber && student.section == section) {
                        found = true;
                        const attendanceRef = ref(database, `attendance/11/${date}/${childSnapshot.key}`);
                        set(attendanceRef, {
                            rollNumber: rollNumber,
                            section: student.section,
                            status: status.value,
                            name: student.name
                        }).then(() => {
                            alert("अटेंडेंस दर्ज किया गया!");
                            document.getElementById('attendance-form').reset();
                        }).catch(error => {
                            alert("Error: " + error.message);
                        });
                    }
                });
                if (!found) alert("स्टूडेंट नहीं मिला!");
            });
        };

        // 3️⃣ **स्टूडेंट को सर्च करना (अटेंडेंस के साथ)**
        window.searchStudent = () => {
            const rollNumber = document.getElementById('search-roll-number').value;
            const section = document.getElementById('search-section').value;

            if (!rollNumber || !section) {
                alert("कृपया रोल नंबर और सेक्शन भरें!");
                return;
            }

            const studentRef = ref(database, 'students/11');
            get(studentRef).then(snapshot => {
                let found = false;
                snapshot.forEach(childSnapshot => {
                    const student = childSnapshot.val();
                    if (student.rollNumber == rollNumber && student.section == section) {
                        found = true;
                        document.getElementById('student-details').innerHTML = `
                            <h3>Student details</h3>
                            <p><strong>Name:</strong> ${student.name}</p>
                            <p><strong>Roll no:</strong> ${student.rollNumber}</p>
                            <p><strong>Section:</strong> ${student.section}</p>
                        `;
                    }
                });

                if (!found) {
                    alert("स्टूडेंट नहीं मिला!");
                    document.getElementById('student-details').innerHTML = "";
                }
            });
        };

        // 4️⃣ **तारीख के हिसाब से अटेंडेंस सर्च करना**
        window.searchAttendanceByDate = () => {
            const date = document.getElementById('search-date').value;

            if (!date) {
                alert("कृपया तारीख भरें!");
                return;
            }

            const attendanceRef = ref(database, `attendance/11/${date}`);
            get(attendanceRef).then(snapshot => {
                let found = false;
                let attendanceHTML = "<h3>अटेंडेंस रिकॉर्ड</h3>";
                snapshot.forEach(childSnapshot => {
                    const attData = childSnapshot.val();
                    found = true;
                    attendanceHTML += `<p><strong>${attData.name}:</strong> ${attData.status} 
                                        (रोल नंबर: ${attData.rollNumber}, सेक्शन: ${attData.section})</p>`;
                });
                if (!found) {
                    attendanceHTML = "<p>इस दिन के लिए कोई अटेंडेंस रिकॉर्ड नहीं मिला!</p>";
                }
                document.getElementById('attendance-results').innerHTML = attendanceHTML;
            }).catch(error => {
                alert("Error: " + error.message);
            });
        };
    </script>

    <style>
        body { font-family: Arial, sans-serif; background-color: #f4f4f9; padding: 20px; }
        #content { max-width: 600px; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); }
        h2 { text-align: center; }
        input, select, button { width: 100%; padding: 10px; margin: 10px 0; }
        button { background: #3498db; color: white; border: none; }
        button:hover { background: #2980b9; }
    </style>
</head>
<body>

    <div id="content">
        <h2>Student Attendance System</h2>

        <h3>New Student Add</h3>
        <input type="text" id="student-name" placeholder="Name">
        <input type="number" id="student-roll-number" placeholder="Roll number">
        <select id="student-section">
            <option value="">Select section</option>
            <option value="A">A</option>
            <option value="B">B</option>
        </select>
        <button onclick="addStudent()">Submit</button>

        <hr>

        <h3>Add attendance</h3>
        <input type="number" id="attendance-roll-number" placeholder="Roll no ....">
        <select id="attendance-section">
            <option value="">section</option>
            <option value="A">A</option>
            <option value="B">B</option>
        </select>
        <input type="date" id="attendance-date">
        <label><input type="radio" name="attendance" value="Present"> Present</label>
        <label><input type="radio" name="attendance" value="Absent"> Absent</label>
        <button onclick="submitAttendance()"> Submit attendance</button>

        <hr>

        <h3>Search attendance by date</h3>
        <input type="date" id="search-date">
        <button onclick="searchAttendanceByDate()">Search</button>

        <div id="attendance-results"></div>

        <hr>

        <h3>Student details search by roll number and section</h3>
        <input type="number" id="search-roll-number" placeholder="Roll no..">
        <select id="search-section">
            <option value="">Select section</option>
            <option value="A">A</option>
            <option value="B">B</option>
        </select>
        <button onclick="searchStudent()">Search</button>

        <div id="student-details"></div>
    </div>

</body>
</html>
