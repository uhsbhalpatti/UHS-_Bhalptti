<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>School Attendance System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 600px;
            margin: auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            color: #333;
        }

        h2 {
            color: #333;
            margin-top: 20px;
        }

        form {
            display: flex;
            flex-direction: column;
        }

        label {
            margin: 10px 0 5px;
        }

        input, select {
            padding: 8px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        button {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #45a049;
        }

        #studentProfile, #attendanceStatus, #attendanceDetails {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>School Attendance System</h1>

        <!-- स्टूडेंट डाटा एंट्री -->
        <div class="student-entry">
            <h2>Enter Student Details</h2>
            <form id="studentForm">
                <label for="name">Student Name:</label>
                <input type="text" id="name" required>

                <label for="class">Class:</label>
                <select id="class" required>
                    <option value="11th">11th</option>
                </select>

                <label for="stream">Stream:</label>
                <select id="stream" required>
                    
                    <option value="Arts">Arts</option>
                  
                </select>

                <label for="section">Section:</label>
                <select id="section" required>
                    <option value="A">A</option>
                    <option value="B">B</option>
                    <option value="C">C</option>
                    <option value="D">D</option>
                </select>

                <label for="rollNo">Roll Number:</label>
                <input type="number" id="rollNo" required>

                <button type="submit">Submit</button>
            </form>
        </div>

        <!-- अटेंडेंस रिकॉर्ड -->
        <div class="attendance">
            <h2>Attendance Record</h2>
            <form id="attendanceForm">
                <label for="searchRollNo">Search by Roll No:</label>
                <input type="number" id="searchRollNo" placeholder="Enter Roll Number" required>

                <label for="searchSection">Select Section:</label>
                <select id="searchSection" required>
                    <option value="A">A</option>
                    <option value="B">B</option>
                    <option value="C">C</option>
                    <option value="D">D</option>
                </select>

                <button type="button" onclick="searchStudent()">Search</button>
            </form>

            <div id="studentProfile"></div>

            <div id="attendanceStatus" style="display:none;">
                <label for="status">Attendance:</label>
                <select id="status">
                    <option value="Present">Present</option>
                    <option value="Absent">Absent</option>
                </select>
                <label for="date">Date:</label>
                <input type="date" id="date">
                <button type="button" onclick="submitAttendance()">Submit Attendance</button>
            </div>
        </div>

        <!-- अटेंडेंस डिटेल्स -->
        <div class="attendance-details">
            <h2>Attendance Records</h2>
            <form id="recordSearchForm">
                <label for="searchName">Search by Student Name:</label>
                <input type="text" id="searchName" placeholder="Enter Student Name">
                <button type="button" onclick="searchAttendance()">Search</button>
            </form>

            <div id="attendanceDetails"></div>
        </div>
    </div>

    <script>
        // लोकल स्टोरेज से स्टूडेंट डेटा लोड करें, यदि पहले से मौजूद हो
        let studentData = JSON.parse(localStorage.getItem('studentData')) || [];

        // स्टूडेंट डेटा सबमिट करना
        document.getElementById('studentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            let name = document.getElementById('name').value;
            let className = document.getElementById('class').value;
            let stream = document.getElementById('stream').value;
            let section = document.getElementById('section').value;
            let rollNo = document.getElementById('rollNo').value;

            // चेक करें कि क्लास 11th है या नहीं
            if(className === '11th') {
                let student = {
                    name: name,
                    class: className,
                    stream: stream,
                    section: section,
                    rollNo: rollNo,
                    attendance: []
                };

                studentData.push(student);
                localStorage.setItem('studentData', JSON.stringify(studentData)); // डेटा को लोकल स्टोरेज में सेव करें
                alert("Student Data Submitted Successfully!");
                document.getElementById('studentForm').reset();
            } else {
                alert("Only 11th class is allowed.");
            }
        });

        // स्टूडेंट सर्च करना
        function searchStudent() {
            let rollNo = document.getElementById('searchRollNo').value;
            let section = document.getElementById('searchSection').value;
            
            // रोल नंबर और सेक्शन के आधार पर स्टूडेंट ढूंढना
            let student = studentData.find(s => s.rollNo == rollNo && s.section == section);
            
            if(student) {
                let profile = `
                    <h3>Student Profile</h3>
                    <p>Name: ${student.name}</p>
                    <p>Class: ${student.class}</p>
                    <p>Stream: ${student.stream}</p>
                    <p>Section: ${student.section}</p>
                    <p>Roll No: ${student.rollNo}</p>
                `;
                document.getElementById('studentProfile').innerHTML = profile;
                document.getElementById('attendanceStatus').style.display = 'block';
            } else {
                document.getElementById('studentProfile').innerHTML = "<p>Student not found!</p>";
            }
        }

        // अटेंडेंस सबमिट करना
        function submitAttendance() {
            let rollNo = document.getElementById('searchRollNo').value;
            let section = document.getElementById('searchSection').value;
            let status = document.getElementById('status').value;
            let date = document.getElementById('date').value;

            let student = studentData.find(s => s.rollNo == rollNo && s.section == section);

            if(student) {
                student.attendance.push({ date: date, status: status });
                localStorage.setItem('studentData', JSON.stringify(studentData)); // अपडेटेड डेटा को लोकल स्टोरेज में सेव करें
                alert("Attendance Submitted Successfully!");
                document.getElementById('attendanceStatus').style.display = 'none';
            }
        }

        // अटेंडेंस रिकॉर्ड सर्च करना
        function searchAttendance() {
            let searchName = document.getElementById('searchName').value;
            let student = studentData.find(s => s.name.toLowerCase().includes(searchName.toLowerCase()));

            if(student) {
                let attendanceDetails = `
                    <h3>Attendance Record for ${student.name}</h3>
                    <ul>
                        ${student.attendance.map(att => `<li>${att.date}: ${att.status}</li>`).join('')}
                    </ul>
                `;
                document.getElementById('attendanceDetails').innerHTML = attendanceDetails;
            } else {
                document.getElementById('attendanceDetails').innerHTML = "<p>Student not found!</p>";
            }
        }
    </script>
</body>
</html>
