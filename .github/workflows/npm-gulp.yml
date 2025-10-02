<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Catch the Ball 🎮</title>
  <style>
    body {
      margin: 0;
      background: #222;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      color: white;
      font-family: sans-serif;
    }
    canvas {
      background: #333;
      border: 3px solid #fff;
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <canvas id="gameCanvas" width="400" height="500"></canvas>
  <script>
    const canvas = document.getElementById("gameCanvas");
    const ctx = canvas.getContext("2d");

    let paddle = { x: 160, y: 460, width: 80, height: 15, speed: 20 };
    let ball = { x: Math.random() * 380, y: 0, radius: 10, dy: 3 };
    let score = 0;

    function drawPaddle() {
      ctx.fillStyle = "cyan";
      ctx.fillRect(paddle.x, paddle.y, paddle.width, paddle.height);
    }

    function drawBall() {
      ctx.beginPath();
      ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2);
      ctx.fillStyle = "orange";
      ctx.fill();
      ctx.closePath();
    }

    function drawScore() {
      ctx.fillStyle = "white";
      ctx.font = "20px Arial";
      ctx.fillText("Score: " + score, 10, 25);
    }

    function updateBall() {
      ball.y += ball.dy;
      if (ball.y > canvas.height) {
        // Reset ball if missed
        ball.x = Math.random() * (canvas.width - ball.radius*2) + ball.radius;
        ball.y = 0;
        score = Math.max(0, score - 1); // lose point if missed
      }

      // Check collision with paddle
      if (
        ball.y + ball.radius >= paddle.y &&
        ball.x >= paddle.x &&
        ball.x <= paddle.x + paddle.width
      ) {
        score++;
        ball.x = Math.random() * (canvas.width - ball.radius*2) + ball.radius;
        ball.y = 0;
      }
    }

    function gameLoop() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      drawPaddle();
      drawBall();
      drawScore();
      updateBall();
      requestAnimationFrame(gameLoop);
    }

    document.addEventListener("keydown", (e) => {
      if (e.key === "ArrowLeft" && paddle.x > 0) {
        paddle.x -= paddle.speed;
      } else if (e.key === "ArrowRight" && paddle.x + paddle.width < canvas.width) {
        paddle.x += paddle.speed;
      }
    });

    gameLoop();
  </script>
</body>
</html>
