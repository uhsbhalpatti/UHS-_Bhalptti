<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Attendance System</title>
    <!-- Firebase SDK -->
    <script type="module">
        import { initializeApp } from 'https://www.gstatic.com/firebasejs/9.19.1/firebase-app.js';
        import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword, sendPasswordResetEmail, signOut } from 'https://www.gstatic.com/firebasejs/9.19.1/firebase-auth.js';
        import { getDatabase, ref, set, push, get } from 'https://www.gstatic.com/firebasejs/9.19.1/firebase-database.js';

        // Firebase Configuration
        const firebaseConfig = {
            apiKey: "AIzaSyDNvb3-UdC61ojcTrIVnVWwEFeH82OIX_g",
            authDomain: "edugine-1.firebaseapp.com",
            databaseURL: "https://edugine-1-default-rtdb.firebaseio.com",
            projectId: "edugine-1",
            storageBucket: "edugine-1.firebasestorage.app",
            messagingSenderId: "859662404389",
            appId: "1:859662404389:web:1e80d9ec06d300e30168cc",
            measurementId: "G-LY01R016PN"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const database = getDatabase(app);

        // Function to save student data
        window.submitStudentData = () => {
            const studentName = document.getElementById('student-name').value;
            const studentSection = document.getElementById('student-section').value;
            const rollNumber = document.getElementById('roll-number').value;

            if (!studentName || !studentSection || !rollNumber) {
                alert("Please fill in all fields.");
                return;
            }

            const studentRef = ref(database, 'students/11'); // Only 11th class students
            const newStudentRef = push(studentRef);
            set(newStudentRef, {
                name: studentName,
                rollNumber: rollNumber,
                section: studentSection
            }).then(() => {
                alert("Student Data Saved Successfully");
                document.getElementById('student-form').reset();
            }).catch((error) => {
                alert("Error: " + error.message);
            });
        };

        // Function to submit attendance
        window.submitAttendance = () => {
            const rollNumber = document.getElementById('attendance-roll-number').value;
            const attendanceSection = document.getElementById('attendance-section').value;
            const attendanceDate = document.getElementById('attendance-date').value;
            const attendanceStatus = document.querySelector('input[name="attendance"]:checked').value;

            if (!rollNumber || !attendanceSection || !attendanceDate || !attendanceStatus) {
                alert("Please fill in all fields.");
                return;
            }

            // Searching for student based on roll number and section
            const studentRef = ref(database, 'students/11');
            get(studentRef).then((snapshot) => {
                let studentFound = false;
                snapshot.forEach((childSnapshot) => {
                    const studentData = childSnapshot.val();
                    if (studentData.rollNumber == rollNumber && studentData.section == attendanceSection) {
                        studentFound = true;
                        const attendanceRef = ref(database, `attendance/11/${attendanceDate}/${childSnapshot.key}`);
                        set(attendanceRef, {
                            rollNumber: rollNumber,
                            section: studentData.section,
                            attendanceStatus: attendanceStatus,
                            name: studentData.name
                        }).then(() => {
                            alert("Attendance Submitted Successfully");
                            document.getElementById('attendance-form').reset();
                        }).catch((error) => {
                            alert("Error: " + error.message);
                        });
                    }
                });
                if (!studentFound) {
                    alert("Student not found");
                }
            }).catch((error) => {
                alert("Error: " + error.message);
            });
        };

    </script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            color: #333;
        }

        #content {
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            font-size: 32px;
            color: #2C3E50;
        }

        input, select, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 16px;
        }

        button {
            background-color: #3498db;
            color: white;
            font-size: 18px;
            cursor: pointer;
            border: none;
        }

        button:hover {
            background-color: #2980b9;
        }

        .attendance-options {
            display: flex;
            justify-content: space-between;
        }

        .attendance-options input {
            margin-right: 10px;
        }
    </style>
</head>
<body>

    <div id="content">
        <h2>Student Attendance System</h2>

        <!-- Student Data Entry Form -->
        <form id="student-form">
            <h3>Enter Student Data</h3>
            <input type="text" id="student-name" placeholder="Enter Student Name" required>
            <select id="student-section" required>
                <option value="">Select Section</option>
                <option value="A">A</option>
                <option value="B">B</option>
            </select>
            <input type="number" id="roll-number" placeholder="Enter Roll Number" required>
            <button type="button" onclick="submitStudentData()">Submit Student Data</button>
        </form>

        <hr>

        <!-- Attendance Submission Form -->
        <form id="attendance-form">
            <h3>Submit Attendance</h3>
            <select id="attendance-section" required>
                <option value="">Select Section</option>
                <option value="A">A</option>
                <option value="B">B</option>
            </select>
            <input type="number" id="attendance-roll-number" placeholder="Enter Roll Number" required>
            <input type="date" id="attendance-date" required>
            <div class="attendance-options">
                <label><input type="radio" name="attendance" value="Present"> Present</label>
                <label><input type="radio" name="attendance" value="Absent"> Absent</label>
            </div>
            <button type="button" onclick="submitAttendance()">Submit Attendance</button>
        </form>
    </div>

</body>
</html>
