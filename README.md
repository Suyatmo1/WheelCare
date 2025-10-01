# WheelCare
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>HD785-7 Splash Preview</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      overflow: hidden;
      font-family: Arial, sans-serif;
    }

    /* Background gradasi animasi */
    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .splash {
      height: 100%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background: linear-gradient(-45deg, #FF9800, #F44336, #3F51B5, #4CAF50);
      background-size: 400% 400%;
      animation: gradientBG 8s ease infinite;
      color: white;
    }

    .logo {
      width: 200px;
      height: 200px;
      opacity: 0;
      animation: fadeIn 3s forwards;
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    .title {
      margin-top: 20px;
      font-size: 22px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="splash">
    <!-- Ganti src dengan logo HD785-7 (PNG) -->
    <img src="ic_hd7857.png" alt="HD785-7 Logo" class="logo">
    <div class="title">HD785-7 WA Sender</div>
  </div>
</body>
</html>
