<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>+2 उत्क्रमित माध्यमिक विद्यालय भाल पट्टी</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      margin: 0;
      padding: 0;
    }
    header {
      text-align: center;
      background-color: #0056b3;
      color: white;
      padding: 20px;
    }
    .container {
      width: 300px;
      margin: 50px auto;
      padding: 20px;
      background-color: white;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
    }
    h2 {
      text-align: center;
      color: #0056b3;
    }
    form {
      display: flex;
      flex-direction: column;
    }
    input {
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      padding: 10px;
      background-color: #0056b3;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #003d80;
    }
    .link {
      text-align: center;
      margin-top: 10px;
    }
    .link a {
      text-decoration: none;
      color: #0056b3;
    }
    .link a:hover {
      text-decoration: underline;
    }
    .school-info {
      text-align: center;
      margin-top: 20px;
      font-size: 16px;
    }
    .school-info h3 {
      color: #0056b3;
    }
    .school-info ul {
      list-style-type: none;
      padding: 0;
    }
    .school-info li {
      margin: 10px 0;
    }timetable {
      background-color: #f9f9f9;
      padding: 10px;
      margin-top: 20px;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }
    #timetable ul {
      padding: 0;
    }
    #timetable li {
      margin: 10px 0;
    }
    section#contact {
      margin-top: 20px;
    }timetable {
      background-color: #f9f9f9;
      padding: 10px;
      margin-top: 20px;
      border-radius: 8px;
      box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }
    #timetable ul {
      padding: 0;
    }
    #timetable li {
      margin: px 0;
    }
    section#contact {
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <!-- School Info Section (Hidden Initially) -->
  <header id="school-info-header" style="display: none;">
    <h1>+2 उत्क्रमित माध्यमिक विद्यालय भालपट्टी</h1>
    <p>गुणवत्तापूर्ण शिक्षा के लिए समर्पित</p>
  </header>

                <!--Scrooling -->

<marquee behavior="scroll" direction="left" scrollamount="8" style="font-size: 20px; text-align: center; color: #ffffff; text-shadow: 0 0 5px #ff0000, 0 0 10px #ff0000, 0 0 15px #ff0000">
     ~~ Created By Ajit Kumar ~~
</marquee>
  <!-- Login/Register Section -->
  <div class="container" id="login-container">
    <h2>लॉगिन / रजिस्टर</h2>
    


    <!-- Login Form -->
    <form id="login-form">
      <input type="text" id="username" placeholder="उपयोगकर्ता नाम" required>
      <input type="password" id="password" placeholder="पासवर्ड" required>
      <button type="submit">लॉगिन करें</button> 
      <div class="link">
        <a href="#" id="forgot-password-link">पासवर्ड भूल गए?</a>
        <p>नया खाता बनाई ? <a href="#" id="register-link">रजिस्टर करें</a></p>
      </div>
    </form>

    <!-- Register Form (Initially Hidden) -->
    <form id="register-form" style="display: none;">
      <input type="text" id="new-username" placeholder="उपयोगकर्ता नाम" required>
      <input type="email" id="new-email" placeholder="ईमेल" required>
      <input type="password" id="new-password" placeholder="पासवर्ड" required>
      <button type="submit">रजिस्टर करें</button>
      <div class="link">
        <p>पहले से खाता है? <a href="#" id="login-link">लॉगिन करें</a></p>
      </div>
    </form>

  <!-- Display School Information After Login/Register -->
  <div id="school-info-container" style="display: none;">
    <div class="school-info">
      <h3>स्कूल के बारे में:</h3>
      <p>+2 उत्क्रमित माध्यमिक विद्यालय भालपट्टी शिक्षा के क्षेत्र में एक प्रतिष्ठित नाम है। यहां विद्यार्थियों को उत्कृष्ट शिक्षा, आधुनिक सुविधाएं, और एक सुरक्षित वातावरण मिलता है।</p>
      
      <h3>लाइब्रेरी:</h3>
      <p>हमारी लाइब्रेरी में एनसीईआरटी की सभी ऑफिशियल किताबें उपलब्ध हैं। विद्यार्थियों को इन किताबों के डिजिटल संस्करण भी मिलते हैं, जो वे ऑनलाइन पढ़ सकते हैं।</p>
      
      <a href="https://ncert.nic.in/textbook.php" target="_blank">यहां आपको Ncert की सभी बुक मिल जाएगी</a>
      <h4>बुक कैसे डाउनलोड करें</h4>
<ul>
      <li> पहले आप इस वेबसाइट पर जाएं </li>
      <li>वहां पर बहुत सारे ऑप्शन देखेंगेउनमें सेक्लास वाले ऑप्शन पर क्लिक करें और अपना क्लास सिलेक्ट करें</li>
      <li>फिर विषय ( Subject ) सेलेक्ट करें</li>
      <li>आपकी क्लास की बुक आएंगे उसमें से अपना एक बुक जो बुक आपको चाहिए वह सेलेक्ट करें</li>
      <li>फिर Go बटन को क्लिक करें और देखिए आपका बुक आ गया है</li>
      <li>जो  चैप्टर देखना है उसको ओपन करके देख सकते हैंऔर डाउनलोड भी कर सकते हैं</li>
</ul>
      
       

     
     
      <h3>एडमिशन प्रक्रिया:</h3>
      <p>विद्यालय में एडमिशन के लिए विद्यार्थियों को एक प्रवेश परीक्षा पास करनी होती है।
<li> परीक्षा का आयोजन प्रत्येक वर्ष जून महीने में होता है|</li>
 <li>परीक्षा के बाद मेरिट लिस्ट जारी की जाती है, और चयनित विद्यार्थियों को शिक्षा के लिए आमंत्रित किया जाता है।</li></p>

      <h3>कोर्स और विषय:</h3>
      <ul>
        <li>विज्ञान: गणित, भौतिकी, रसायन विज्ञान, जीवविज्ञान</li>
        <li>कला: भूगोल, राजनीति विज्ञान, इतिहास, मनोविज्ञान</li>
        <li>व्यवसाय: लेखा, अर्थशास्त्र, वाणिज्य</li>
        <li>भाषाएं: हिंदी, अंग्रेजी</li>
      </ul>

      <h3>स्कूल की विशेषताएँ:</h3>
      <ul>
        <li>समय-समय पर आयोजित होने वाले कार्यशाला और सेमिनार</li>
        <li>सुरक्षित और स्वच्छ विद्यालय परिसर</li>
        <li>सभी विद्यार्थियों के लिए कंप्यूटर लैब की सुविधा</li>
        <li>अच्छी खेल सुविधाएं और वार्षिक खेल कूद प्रतियोगिता</li>
      </ul>

<h2 style="text-aling: center;
font-family: arial, sans-serif;"></h2>
<table border="3" style="width: 100%;
border-collapse: collapse; text-align: center; font-size:19px;">
<thead style="background-color: #4CAF50;">
<tr>
<th>peiod</th>
<th>Time</th>
<th>Subject</th>
<th>teacher</th>
</tr>
</thead>
<thody>
<tr>
<td>1</td>
<td>12:20 PM - 1:00 PM</td>
<td>Geographt</td>
<td>Santosh sir</td>
</tr>
<tr style="background-color: #f2f2f2;">
<td>2</td>
<td>1:00 PM - 1:40 PM</td>
<td>computer science</td>
<td>DN sir</td>
</tr>
<td>3</td>
<td>1:40 PM - 2:20 PM</td>
<td>History</td>
<td>Ranjeet sir</td>
<tr style="background-color: #f2f2f2;">
<td>4</td>
<td>2:20 PM - 3:00 PM</td>
<td>political science</td>
<td>priya mam</td>
<tr>

</tr>
<td>5</td>
<tr style="background-color: #f2f2f2;">
<td>2</td>
<td>3:30 PM - 4:10 PM</td>
<td>English</td>
<td>Rakhi mam</td>
<tr style="background-color: #f2f2f2;">
<td>6</td>
<td>4:10 PM - 4:50 PM</td>
<td>Hindi</td>
<td>Asha Mam</td>
</tr>
</thody>
</table>
</section>
      <section id="contact">
            <h2>संपर्क करें</h2>
            <li>पता: भालपट्टी, दरभंगा, बिहार - 847239</li>
            <li>फोन: 9999999999</li>
            <li>ईमेल: ajit@gmail.com</li>
        </section>
           
    
    
<section id="teachers-info">
<h2 style="text-aling: center;
font-family: arial, sans-serif;"></h2>
<table border="3" style="width: 100%;
border-collapse: collapse; text-align: center; font-size:16px;">
<thead style="background-color: #4CAF50;"><section id="timetable">
<tr>
<th>teachers</th>
<th>subject</th>
<th>Experiennce</th>
<th>Qualification</th>
</tr>
</thead>
<thody>
<tr>
<td>Santosh sir</td>
<td>Geography</td>
<td>3 year</td>
<td>...?</td>
</tr>
<tr>
<td>Sonu sir</td>
<td>Psychology</td>
<td>2 year</td>
<td>...?</td>
</tr>
<tr>
<td>Ranjeet sir</td>
<td>History</td>
<td>5 year</td>
<td>...?</td>
</tr>
<tr>
<td>D. N. sir</td>
<td>Computer science</td>
<td>...?</td>
<td>...?</td>
</tr>
<tr>
<td>Priya mam</td>
<td>Political</td>
<td>...?</td>
<td>...?</td>
</tr>
<tr>
<td>Rakhi mam</td>
<td>English</td>
<td>...?</td>
<td>...?</td>
</tr>
<tr>
<td>Aasha mam</td>
<td>Hindi</td>
<td>...?</td>
<td>...?</td>
</tr>
</thody>
 </table>
</section>
 




    <!-- Add this inside your HTML body -->

<button id="toggleButton">Open Notepad</button>

<!-- Notepad container -->
<div id="notepad" style="display:none;">
    <textarea id="notes" placeholder="Write your notes here..."></textarea>
    <br>
    <button id="saveButton">Save Note</button>
    <button id="closeButton">Close Notepad</button>
</div>

<style>
    /* Notepad styling */
    #notepad {
        width: 300px;
        height: 200px;
        border: 1px solid #000;
    }
    /* Button styling */
    button {
        padding: 10px;
        background-color: #4CAF50;
        color: white;
        border: none;
        cursor: pointer;
    }
    textarea {
        width: 100%;
        height: 100%;
        border: none;
        padding: 10px;
        box-sizing: border-box;
    }
</style>

    
    
      
  <script>
    const loginForm = document.getElementById("login-form");
    const registerForm = document.getElementById("register-form");
    const registerLink = document.getElementById("register-link");
    const loginLink = document.getElementById("login-link");
    const forgotPasswordLink = document.getElementById("forgot-password-link");
    const loginContainer = document.getElementById("login-container");
    const schoolInfoContainer = document.getElementById("school-info-container");
    const schoolInfoHeader = document.getElementById("school-info-header");

    // Show the register form
    registerLink.addEventListener("click", () => {
      loginForm.style.display = "none";
      registerForm.style.display = "block";
    });

    // Show the login form
    loginLink.addEventListener("click", () => {
      registerForm.style.display = "none";
      loginForm.style.display = "block";
    });

    // Handle forgot password
    forgotPasswordLink.addEventListener("click", () => {
      alert("पासवर्ड रिसेट लिंक भेजा जाएगा।");
    });

    // Handle successful login or registration
    loginForm.addEventListener("submit", (e) => {
      e.preventDefault();
      loginContainer.style.display = "none";
      schoolInfoContainer.style.display = "block";
      schoolInfoHeader.style.display = "block";
    });

    registerForm.addEventListener("submit", (e) => {
      e.preventDefault();
      loginContainer.style.display = "none";
      schoolInfoContainer.style.display = "block";
      schoolInfoHeader.style.display = "block";
    });

// JavaScript code to handle notepad functionality
document.addEventListener("DOMContentLoaded", function() {
    const toggleButton = document.getElementById("toggleButton");
    const notepad = document.getElementById("notepad");
    const saveButton = document.getElementById("saveButton");
    const closeButton = document.getElementById("closeButton");
    const notesTextArea = document.getElementById("notes");

    // Check if there is any saved note in localStorage
    if (localStorage.getItem("savedNote")) {
        notesTextArea.value = localStorage.getItem("savedNote");
    }

    // Toggle the visibility of the notepad
    toggleButton.addEventListener("click", function() {
        if (notepad.style.display === "none") {
            notepad.style.display = "block";
            toggleButton.textContent = "Close Notepad"; // Change button text to "Close Notepad"
        } else {
            notepad.style.display = "none";
            toggleButton.textContent = "Open your Notepad"; // Change button text to "Open Notepad"
        }
    });

    // Save the note to localStorage
    saveButton.addEventListener("click", function() {
        localStorage.setItem("savedNote", notesTextArea.value);
        alert("Note Saved!");
    });

    // Close the notepad (hide it)
    closeButton.addEventListener("click", function() {
        notepad.style.display = "none";
        toggleButton.textContent = "Open Notepad"; // Change button text to "Open Notepad"
    });
});
  </script>

</body>
</html>
