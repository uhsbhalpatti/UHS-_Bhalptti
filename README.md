<!DOCTYPE html>
<html lang="hi">
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
  </div>


