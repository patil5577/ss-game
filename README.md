<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SS GAME - Color Prediction</title>
  <style>
    body {
      background-color: #121212;
      color: white;
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }
    h1 {
      color: #00ffff;
    }
    .color-buttons button {
      margin: 10px;
      padding: 15px 30px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      color: white;
    }
    .red { background-color: #e74c3c; }
    .green { background-color: #2ecc71; }
    .violet { background-color: #9b59b6; }
    .result-box {
      margin-top: 20px;
      font-size: 24px;
    }
    .history {
      margin-top: 30px;
    }
  </style>
</head>
<body>
  <h1>SS GAME</h1>
  <p>Guess the next color!</p>
  <div class="color-buttons">
    <button class="red" onclick="makePrediction('Red')">Red</button>
    <button class="green" onclick="makePrediction('Green')">Green</button>
    <button class="violet" onclick="makePrediction('Violet')">Violet</button>
  </div>  <div class="result-box" id="result"></div>
  <div class="history" id="history"></div>  <script>
    let userCoins = 1000;
    let userPrediction = null;
    let history = [];

    function makePrediction(color) {
      userPrediction = color;
      document.getElementById("result").innerHTML = `Prediction: <strong>${color}</strong> <br> Result in 5 seconds...`;
      setTimeout(generateResult, 5000);
    }

    function generateResult() {
      const colors = ["Red", "Green", "Violet"];
      const result = colors[Math.floor(Math.random() * colors.length)];

      if (userPrediction === result) {
        userCoins += 100;
        document.getElementById("result").innerHTML = `Result: <strong>${result}</strong><br> You WON! Coins: ${userCoins}`;
      } else {
        userCoins -= 50;
        document.getElementById("result").innerHTML = `Result: <strong>${result}</strong><br> You lost. Coins: ${userCoins}`;
      }

      history.unshift(result);
      if (history.length > 10) history.pop();
      document.getElementById("history").innerHTML = `<h3>Last Results:</h3> ${history.join(" | ")}`;
    }
  </script></body>
</html>
