# Vikhroli-SDM-Count
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vikhroli SDM Count Leaderboard</title>
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 10px;
      }

      .leaderboard-container {
        background: rgba(255, 255, 255, 0.95);
        border-radius: 20px;
        padding: 20px;
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        backdrop-filter: blur(10px);
        max-width: 600px;
        width: 100%;
        animation: fadeInUp 0.6s ease-out;
      }

      @keyframes fadeInUp {
        from {
          opacity: 0;
          transform: translateY(30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      .title {
        text-align: center;
        font-size: 2.2em;
        font-weight: 700;
        color: #2c3e50;
        margin-bottom: 8px;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        line-height: 1.2;
      }

      .subtitle {
        text-align: center;
        color: #7f8c8d;
        font-size: 1.1em;
        margin-bottom: 25px;
        font-weight: 500;
      }

      .leaderboard {
        list-style: none;
      }

      .leaderboard-item {
        display: flex;
        align-items: center;
        padding: 12px 15px;
        margin-bottom: 10px;
        border-radius: 15px;
        transition: all 0.3s ease;
        animation: slideIn 0.5s ease-out;
        animation-fill-mode: both;
        position: relative;
        overflow: hidden;
      }

      .leaderboard-item:hover {
        transform: translateY(-2px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
      }

      .leaderboard-item:nth-child(1) {
        background: linear-gradient(135deg, #ffd700, #ffed4a);
        animation-delay: 0.1s;
      }

      .leaderboard-item:nth-child(2) {
        background: linear-gradient(135deg, #c0c0c0, #e5e5e5);
        animation-delay: 0.2s;
      }

      .leaderboard-item:nth-child(3) {
        background: linear-gradient(135deg, #cd7f32, #daa520);
        animation-delay: 0.3s;
      }

      .leaderboard-item:nth-child(n + 4) {
        background: linear-gradient(135deg, #f8f9fa, #e9ecef);
        animation-delay: calc(0.1s * var(--index));
      }

      @keyframes slideIn {
        from {
          opacity: 0;
          transform: translateX(-50px);
        }
        to {
          opacity: 1;
          transform: translateX(0);
        }
      }

      .rank {
        font-size: 1.3em;
        font-weight: 700;
        width: 40px;
        text-align: center;
        color: #2c3e50;
        flex-shrink: 0;
      }

      .rank.gold {
        color: #b8860b;
      }
      .rank.silver {
        color: #708090;
      }
      .rank.bronze {
        color: #8b4513;
      }

      .trophy {
        font-size: 1.5em;
        margin-right: 8px;
        flex-shrink: 0;
      }

      .name {
        flex: 1;
        font-size: 1.1em;
        font-weight: 600;
        color: #2c3e50;
        padding-left: 10px;
        word-wrap: break-word;
        min-width: 0;
      }

      .score {
        font-size: 1.2em;
        font-weight: 700;
        color: #27ae60;
        padding: 6px 12px;
        background: rgba(255, 255, 255, 0.8);
        border-radius: 20px;
        min-width: 60px;
        text-align: center;
        flex-shrink: 0;
      }

      .status {
        font-size: 0.8em;
        color: #e74c3c;
        font-style: italic;
        margin-left: 8px;
        flex-shrink: 0;
      }

      .update-date {
        text-align: center;
        color: #95a5a6;
        font-size: 0.9em;
        margin-top: 20px;
        padding-top: 15px;
        border-top: 1px solid #ecf0f1;
      }

      /* Mobile Styles */
      @media (max-width: 600px) {
        body {
          padding: 5px;
        }

        .leaderboard-container {
          padding: 15px;
          border-radius: 15px;
        }

        .title {
          font-size: 1.8em;
          margin-bottom: 6px;
        }

        .subtitle {
          font-size: 1em;
          margin-bottom: 20px;
        }

        .leaderboard-item {
          padding: 10px 12px;
          margin-bottom: 8px;
          border-radius: 12px;
        }

        .rank {
          font-size: 1.1em;
          width: 35px;
        }

        .trophy {
          font-size: 1.3em;
          margin-right: 6px;
        }

        .name {
          font-size: 1em;
          padding-left: 8px;
        }

        .score {
          font-size: 1.1em;
          padding: 5px 10px;
          min-width: 50px;
        }

        .status {
          font-size: 0.75em;
          margin-left: 6px;
        }

        .update-date {
          font-size: 0.85em;
          margin-top: 15px;
          padding-top: 12px;
        }
      }

      /* Extra small screens */
      @media (max-width: 400px) {
        .title {
          font-size: 1.6em;
        }

        .leaderboard-item {
          padding: 8px 10px;
          flex-wrap: wrap;
        }

        .rank {
          font-size: 1em;
          width: 30px;
        }

        .trophy {
          font-size: 1.2em;
          margin-right: 5px;
        }

        .name {
          font-size: 0.95em;
          padding-left: 6px;
        }

        .score {
          font-size: 1em;
          padding: 4px 8px;
          min-width: 45px;
        }

        .status {
          font-size: 0.7em;
          margin-left: 4px;
          width: 100%;
          margin-top: 2px;
          padding-left: 46px;
        }
      }

      /* Very small screens - status on new line */
      @media (max-width: 320px) {
        .leaderboard-item {
          flex-direction: column;
          align-items: flex-start;
        }

        .leaderboard-item > div {
          display: flex;
          align-items: center;
          width: 100%;
          justify-content: space-between;
        }

        .status {
          width: 100%;
          margin-left: 0;
          margin-top: 4px;
          padding-left: 0;
          text-align: center;
        }
      }
    </style>
  </head>
  <body>
    <div class="leaderboard-container">
      <h1 class="title">🏆 Vikhroli SDM Count</h1>
      <p class="subtitle">Leadership Board</p>

      <ul class="leaderboard">
        <li class="leaderboard-item" style="--index: 1">
          <span class="rank gold">1</span>
          <span class="trophy">🥇</span>
          <span class="name">Divyam Patel</span>
          <span class="score">315</span>
        </li>

        <li class="leaderboard-item" style="--index: 2">
          <span class="rank silver">2</span>
          <span class="trophy">🥈</span>
          <span class="name">Tirth Panchal</span>
          <span class="score">315</span>
          <span class="status">(Adhiveshan Pending)</span>
        </li>

        <li class="leaderboard-item" style="--index: 3">
          <span class="rank bronze">3</span>
          <span class="trophy">🥉</span>
          <span class="name">Shubhan Dhume</span>
          <span class="score">315</span>
          <span class="status">(Adhiveshan Pending)</span>
        </li>

        <li class="leaderboard-item" style="--index: 4">
          <span class="rank">4</span>
          <span class="name">Sanjeev Konar</span>
          <span class="score">273</span>
        </li>

        <li class="leaderboard-item" style="--index: 5">
          <span class="rank">5</span>
          <span class="name">Vraj Panchal</span>
          <span class="score">200</span>
        </li>

        <li class="leaderboard-item" style="--index: 6">
          <span class="rank">6</span>
          <span class="name">Vibhu Kariya</span>
          <span class="score">130</span>
        </li>

        <li class="leaderboard-item" style="--index: 7">
          <span class="rank">7</span>
          <span class="name">Avyan Panchal</span>
          <span class="score">125</span>
        </li>

        <li class="leaderboard-item" style="--index: 8">
          <span class="rank">8</span>
          <span class="name">Smith Vadoliya</span>
          <span class="score">115</span>
        </li>

        <li class="leaderboard-item" style="--index: 9">
          <span class="rank">9</span>
          <span class="name">Mayank Vadoliya</span>
          <span class="score">115</span>
        </li>

        <li class="leaderboard-item" style="--index: 10">
          <span class="rank">10</span>
          <span class="name">Kushal Wala</span>
          <span class="score">105</span>
        </li>

        <li class="leaderboard-item" style="--index: 11">
          <span class="rank">11</span>
          <span class="name">Mayank Patel</span>
          <span class="score">100</span>
        </li>

        <li class="leaderboard-item" style="--index: 12">
          <span class="rank">12</span>
          <span class="name">Girish Deshmukh</span>
          <span class="score">55</span>
        </li>

        <li class="leaderboard-item" style="--index: 13">
          <span class="rank">13</span>
          <span class="name">Daiwik Jadeja</span>
          <span class="score">45</span>
        </li>
      </ul>

      <div class="update-date">📅 Last Updated: July 6th, 2025</div>
    </div>
  </body>
</html>
