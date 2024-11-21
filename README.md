<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bức Thư Bí Mật</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      text-align: center;
      background: linear-gradient(to top, #87CEFA, #FFB6C1);
      overflow: hidden;
      height: 100vh;
    }

    .container {
      position: absolute;
      top: 30%;
      left: 50%;
      transform: translate(-50%, -50%);
      padding: 20px;
      background: rgba(255, 255, 255, 0.7);
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
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

    /* Bao thư */
    .envelope {
      width: 300px;
      height: 150px;
      background-color: #ffebcd;
      border-radius: 15px;
      position: relative;
      margin: 0 auto;
      overflow: hidden;
      transition: all 1s ease;
      transform-origin: top;
    }

    .envelope .flap-top,
    .envelope .flap-bottom {
      position: absolute;
      width: 100%;
      height: 50%;
      background-color: #dcdcdc;
      z-index: 1;
      transition: all 1s ease;
    }

    .envelope .flap-top {
      top: 0;
      clip-path: polygon(0% 100%, 100% 100%, 100% 0%, 0% 0%);
    }

    .envelope .flap-bottom {
      bottom: 0;
      clip-path: polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%);
    }

    /* Lá thư */
    .letter {
      width: 260px;
      height: 100px;
      background-color: #fff;
      border-radius: 5px;
      position: absolute;
      top: 25%;
      left: 50%;
      transform: translateX(-50%);
      padding: 20px;
      box-sizing: border-box;
      display: none;
      z-index: 2;
      opacity: 0;
      transition: opacity 1s ease-in-out;
    }

    /* Nội dung thư */
    #message {
      font-size: 1.2em;
      color: #333;
      line-height: 1.6;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>Nhập mật khẩu để mở bức thư</h2>
    <input type="password" id="password" placeholder="Nhập mật khẩu">
    <button onclick="unlockLetter()">Mở thư</button>
  </div>

  <!-- Bao thư -->
  <div class="envelope" id="envelope">
    <div class="flap-top"></div>
    <div class="flap-bottom"></div>
    <div class="letter" id="letter">
      <div id="message">
        Ngày hôm nay, anh muốn viết cho em những lời này. Đây là một bức thư mà anh đã chuẩn bị từ lâu, nhưng chỉ muốn em nhận được khi chúng ta thật sự sẵn sàng cho điều đó.

Nếu em đang đọc những dòng này, điều đó có nghĩa là em đã nhập đúng mật khẩu – giống như chúng ta đã đi qua rất nhiều thử thách và giờ là lúc bắt đầu một hành trình mới cùng nhau. Anh rất vui vì em đã đến bên anh, và cảm ơn em vì đã cho anh cơ hội để yêu thương, chia sẻ và đồng hành với em.

Anh biết rằng tình yêu không phải lúc nào cũng dễ dàng. Sẽ có những lúc chúng ta không đồng quan điểm, sẽ có những vấn đề không thể tránh khỏi. Nhưng anh mong rằng mỗi khi điều đó xảy ra, chúng ta sẽ không để những bất đồng làm tổn thương nhau. Hãy luôn nhớ rằng anh ở đây, sẵn sàng lắng nghe và chia sẻ với em.

Đôi khi, cuộc sống sẽ không thuận lợi, công việc, học tập hay những áp lực từ bên ngoài có thể khiến chúng ta cảm thấy mệt mỏi. Nhưng thay vì để những cảm xúc đó ảnh hưởng đến mối quan hệ của mình, anh hy vọng chúng ta có thể cùng nhau vượt qua tất cả. Anh luôn ở bên em, sẵn sàng chia sẻ và đồng hành cùng em qua từng khó khăn.

Cảm ơn em vì đã kiên nhẫn đến đây. Anh yêu em, và sẽ luôn ở đây, bên em, dù có chuyện gì xảy ra.!
      </div>
    </div>
  </div>

  <script>
    function unlockLetter() {
      const correctPassword = "iuemnhieu";  // Thay mật khẩu tại đây
      const inputPassword = document.getElementById("password").value;
      const envelope = document.getElementById("envelope");
      const letter = document.getElementById("letter");

      if (inputPassword === correctPassword) {
        // Mở bao thư
        envelope.style.transform = "rotateX(180deg)";
        envelope.style.transition = "transform 2s ease-in-out";

        // Hiển thị lá thư
        setTimeout(function() {
          letter.style.display = "block";
          letter.style.opacity = "1";
        }, 2000); // Đợi 2 giây để bao thư mở ra
      } else {
        alert("Sai mật khẩu! Vui lòng thử lại.");
      }
    }
  </script>

</body>
</html>
