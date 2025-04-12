# ONO-GAME
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ONO Card Game</title>
  <style>
    body {
      background-color: #222;
      color: #fff;
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .card {
      width: 80px;
      height: 120px;
      border-radius: 10px;
      margin: 10px;
      display: inline-flex;
      justify-content: center;
      align-items: center;
      font-weight: bold;
      font-size: 18px;
      color: #000;
      cursor: pointer;
    }
    #player-hand {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 20px;
    }
    #top-card {
      width: 100px;
      height: 140px;
      border-radius: 10px;
      background-color: #eee;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      color: #000;
      margin: 20px;
    }
    .red { background-color: red; }
    .green { background-color: green; }
    .blue { background-color: blue; }
    .yellow { background-color: yellow; }
    .wild { background-color: gray; color: white; }
  </style>
</head>
<body>
  <h1>ONO Web Game</h1>
  <div id="top-card">Top Card</div>
  <h2>Your Hand</h2>
  <div id="player-hand"></div>

  <script>
    const colors = ['red', 'green', 'blue', 'yellow'];
    const specialCards = ['Skip', 'Reverse', 'Draw Two', 'Wild'];

    function getRandomCard() {
      const isSpecial = Math.random() < 0.2;
      const color = colors[Math.floor(Math.random() * colors.length)];
      const value = isSpecial ? specialCards[Math.floor(Math.random() * specialCards.length)] : Math.floor(Math.random() * 9) + 1;
      return { color, value };
    }

    function createCardElement(card) {
      const div = document.createElement('div');
      div.classList.add('card', card.color);
      div.innerText = card.value;
      div.onclick = () => alert(`Played ${card.value} of ${card.color}`);
      return div;
    }

    function displayHand() {
      const handDiv = document.getElementById('player-hand');
      handDiv.innerHTML = '';
      for (let i = 0; i < 7; i++) {
        const card = getRandomCard();
        const el = createCardElement(card);
        handDiv.appendChild(el);
      }
    }

    function showTopCard() {
      const top = getRandomCard();
      const topDiv = document.getElementById('top-card');
      topDiv.className = '';
      topDiv.classList.add(top.color);
      topDiv.innerText = top.value;
    }

    displayHand();
    showTopCard();
  </script>
</body>
</html>
