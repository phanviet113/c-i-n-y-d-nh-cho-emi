<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hiệu Ứng 3D Cảnh Hoa</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      overflow: hidden;
      height: 100vh;
      background: url('YOUR_IMAGE_PATH') no-repeat center center fixed;
      background-size: cover;
    }

    .container {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px;
      background: rgba(255, 255, 255, 0.8);
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
      text-align: center;
    }

    input[type="password"] {
      padding: 10px;
      width: 80%;
      margin: 10px 0;
      border: 2px solid #d81b60;
      border-radius: 5px;
    }

    button {
      padding: 10px 20px;
      border: none;
      background-color: #d81b60;
      color: white;
      border-radius: 5px;
      font-size: 1em;
      cursor: pointer;
    }

    button:hover {
      background-color: #ad1457;
    }

    #message {
      margin-top: 20px;
      font-size: 1.5em;
      color: #d81b60;
      display: none;
    }

    .scene {
      display: none;
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
      perspective: 1000px;
      overflow: hidden;
    }

    .hill {
      position: absolute;
      bottom: -50px;
      width: 150%;
      height: 300px;
      background: linear-gradient(to top, #228B22, #32CD32);
      border-radius: 50%;
      transform: translateZ(-200px) rotateX(20deg);
      box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.2);
    }

    .flower {
      position: absolute;
      width: 30px;
      height: 30px;
      transform-style: preserve-3d;
      animation: floatFlower 5s ease-in-out infinite;
    }

    .flower .petal {
      position: absolute;
      width: 20px;
      height: 40px;
      background: pink;
      border-radius: 50%;
      transform-origin: bottom center;
    }

    .flower .petal:nth-child(1) { transform: rotateX(0deg) translateZ(15px); }
    .flower .petal:nth-child(2) { transform: rotateX(90deg) translateZ(15px); }
    .flower .petal:nth-child(3) { transform: rotateX(180deg) translateZ(15px); }
    .flower .petal:nth-child(4) { transform: rotateX(270deg) translateZ(15px); }

    @keyframes floatFlower {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Nhập mật khẩu để mở bí mật</h2>
    <input type="password" id="password" placeholder="Nhập mật khẩu">
    <button onclick="unlockMessage()">Mở khóa</button>
    <p id="message">Chúc bạn ngày vui vẻ!</p>
  </div>

  <div class="scene">
    <div class="hill"></div>
  </div>

  <script>
    function unlockMessage() {
      const correctPassword = "iuemnhieu";
      const inputPassword = document.getElementById("password").value;
      const message = document.getElementById("message");
      const scene = document.querySelector(".scene");

      if (inputPassword === correctPassword) {
        message.style.display = "block";
        scene.style.display = "block";
        createFlowers();
      } else {
        alert("Sai mật khẩu! Vui lòng thử lại.");
      }
    }

    function createFlowers() {
      const scene = document.querySelector(".scene");
      for (let i = 0; i < 50; i++) {
        const flower = document.createElement("div");
        flower.className = "flower";
        flower.style.left = ${Math.random() * 100}%;
        flower.style.bottom = ${Math.random() * 50}%;
        
        for (let j = 0; j < 4; j++) {
          const petal = document.createElement("div");
          petal.className = "petal";
          flower.appendChild(petal);
        }

        scene.appendChild(flower);
      }
    }
  </script>
</body>
</html>
