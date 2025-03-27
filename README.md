<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background: linear-gradient(to bottom, pink, white);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            font-family: Arial, sans-serif;
        }
        canvas {
            position: absolute;
            display: none;
        }
        #startText {
            font-size: 24px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            animation: blink 1s infinite alternate;
        }
        @keyframes blink {
            from { opacity: 1; }
            to { opacity: 0.5; }
        }
        .balloon {
            width: 20px;
            height: 30px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
            bottom: -50px;
            animation: float 5s linear infinite;
        }
        @keyframes float {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-100vh); opacity: 0; }
        }
        .confetti {
            width: 8px;
            height: 8px;
            position: absolute;
            top: -10px;
            border-radius: 50%;
            animation: fall 3s linear infinite;
        }
        @keyframes fall {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(100vh); opacity: 0; }
        }
        .snowflake {
            position: absolute;
            top: -10px;
            width: 10px;
            height: 10px;
            background-color: white;
            border-radius: 50%;
            opacity: 0.8;
            animation: snowfall 5s linear infinite;
        }
        @keyframes snowfall {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(100vh); opacity: 0; }
        }
        /* Hiệu ứng ngọn lửa dao động */
@keyframes flameFlicker {
    0% { transform: scale(1) translateY(0); opacity: 1; }
    50% { transform: scale(1.1) translateY(-2px); opacity: 0.8; }
    100% { transform: scale(1) translateY(0); opacity: 1; }
}

.flame {
    position: absolute;
    width: 12px;
    height: 18px;
    background: orange;
    border-radius: 50%;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    animation: flameFlicker 0.3s infinite alternate;
    display: none;
}

/* Hiệu ứng xuất hiện dần */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

#birthdayMessage {
    position: absolute;
    font-size: 24px;
    font-weight: bold;
    color: red;
    bottom: 250px; /* Đặt vị trí dưới tầng 3 */
    left: 38%;
    
    opacity: 0;
    animation: fadeIn 3s forwards;
    display: none;
}
.wish-box {
            display: none;
            width: 300px;
            height: 150px;
            background: white;
            border: 2px solid black;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }
        .wish-box textarea {
            width: 100%;
            height: 70px;
        }
         /* Hiệu ứng chung cho bảng */
    #honestBox {
        display: none;
        position: absolute;
        top: 40%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        padding: 20px;
        text-align: center;
        border-radius: 15px;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
        width: 300px;
    }

    /* Văn bản câu hỏi */
    #honestBox p {
        font-size: 18px;
        font-weight: bold;
        color: #333;
        margin-bottom: 20px;
    }

    /* Nút bấm */
    #yesBtn, #noBtn {
        background-color: #4CAF50;
        color: white;
        border: none;
        padding: 10px 20px;
        font-size: 16px;
        margin: 5px;
        border-radius: 5px;
        cursor: pointer;
        transition: background 0.3s ease;
    }

    #noBtn {
        background-color: red;
    }

    #yesBtn:hover, #noBtn:hover {
        background-color: darkgreen;
    }
    .wish-box {
        width: 300px;
        padding: 20px;
        background: linear-gradient(135deg, #ff9a9e, #fad0c4);
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        text-align: center;
        font-family: Arial, sans-serif;
    }
    .wish-title {
        font-size: 18px;
        font-weight: bold;
        color: #fff;
        margin-bottom: 10px;
    }
    .wish-input {
        width: 100%;
        height: 80px;
        padding: 10px;
        border-radius: 8px;
        border: none;
        outline: none;
        resize: none;
        font-size: 14px;
    }
    .wish-button {
        margin-top: 10px;
        padding: 8px 16px;
        background: #ff6b81;
        color: white;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        font-size: 14px;
        transition: 0.3s;
    }
    .wish-button:hover {
        background: #ff4757;
    }
    
    #likeBox, #honestBox {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
    z-index: 10000; /* Luôn nằm trên cùng */
    width: 300px;
    font-family: Arial, sans-serif;
}



/* Hiệu ứng hover */
#yesLikeBtn:hover, #yesBtn:hover {
    background-color: #388E3C;
}

#noLikeBtn:hover, #noBtn:hover {
    background-color: darkred;
}
#likeBox, #honestBox {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
    z-index: 10000;
    width: 320px;
    font-family: Arial, sans-serif;
}

#likeBox p, #honestBox p {
    font-size: 18px;
    font-weight: bold;
    color: #333;
    margin-bottom: 20px;
}

.button-container {
    display: flex;
    justify-content: space-around; /* Đảm bảo nút OK và Không nằm ngang */
    position: relative;
}

#likeBox button, #honestBox button {
    padding: 12px 20px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    border-radius: 8px;
    transition: 0.3s;
    width: 100px;
    position: relative; /* Đảm bảo nút "Không" không che mất "OK" */
}

#yesLikeBtn, #yesBtn {
    background-color: #4CAF50;
    color: white;
}

#noLikeBtn, #noBtn {
    background-color: red;
    color: white;
}

/* Hiệu ứng hover */
#yesLikeBtn:hover, #yesBtn:hover {
    background-color: #388E3C;
}

#noLikeBtn:hover, #noBtn:hover {
    background-color: darkred;
}
.button-container {
    display: flex;
    justify-content: center; /* Căn giữa hai nút */
    gap: 15px; /* Điều chỉnh khoảng cách giữa nút "OK" và "Không" */
    position: relative;
}
.button-container {
    display: flex;
    justify-content: center;
    gap: 20px; /* Điều chỉnh khoảng cách giữa hai nút */
    position: relative;
    width: 100%; /* Giữ hai nút trong khung */
}

button {
    padding: 10px 20px;
    border: none;
    border-radius: 10px;
    font-size: 16px;
    cursor: pointer;
}

#yesBtn {
    background-color: green;
    color: white;
}

#noBtn {
    background-color: red;
    color: white;
    position: absolute;
}
#questionBox {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
    text-align: center;
}

#answerInput {
    width: 80%;
    padding: 5px;
    margin: 10px 0;
}

#submitAnswer {
    padding: 5px 15px;
    background: green;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
}

#submitAnswer:hover {
    background: darkgreen;
}
/* Bảng câu hỏi */
#questionBox {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: linear-gradient(135deg, #ff9a9e, #fad0c4); /* Màu giống likeBox */
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
    z-index: 10000;
    width: 320px;
    font-family: Arial, sans-serif;
}

/* Tiêu đề câu hỏi */
#questionBox p {
    font-size: 18px;
    font-weight: bold;
    color: #333;
    margin-bottom: 15px;
}

/* Ô nhập câu trả lời */
#answerInput {
    width: 90%;
    height: 40px;
    border-radius: 8px;
    border: 1px solid #ddd;
    padding: 10px;
    font-size: 16px;
    outline: none;
    font-family: Arial, sans-serif;
    box-shadow: inset 0px 3px 6px rgba(0, 0, 0, 0.1);
}

/* Nút gửi */
#submitAnswer {
    margin-top: 15px;
    padding: 10px 15px;
    border: none;
    cursor: pointer;
    font-size: 18px;
    border-radius: 8px;
    background-color: #4CAF50;
    color: white;
    transition: 0.3s;
}

/* Hiệu ứng hover */
#submitAnswer:hover {
    background-color: #388E3C;
}

    </style>
</head>
<body>
    <div id="startText">Hãy nhấp vào đây</div>
    <canvas id="birthdayCanvas"></canvas>
    <div class="flame" id="candleFlame"></div>
<div id="birthdayMessage">Chúc mừng sinh nhật bạn Thư </div>
<!-- <div class="wish-box" id="wishBox">
    <p>Hãy ghi điều ước của bạn và đây đi bạn iu :>></p>
    <textarea placeholder="Nhập điều ước..."></textarea>
</div> -->
<div class="wish-box" id="wishBox">
    <p>Hãy ghi điều ước của bạn và đây đi bạn iu :>></p>
    <textarea id="wishInput" placeholder="Nhập điều ước..."></textarea>
    <button id="confirmWish">✔</button>
    
</div>
<button id="blowCandleBtn" style="display: none; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: green; color: white; padding: 10px 20px; font-size: 16px; border: none; cursor: pointer;">Thổi nến</button>

<div id="candleFlame" style="width: 20px; height: 30px; background-color: orange; position: absolute; top: 50px; left: 50px;"></div>


<div id="honestBox">
    <p>1 phút thật lòng nhé?</p>
    <button id="yesBtn">OK</button>
    <button id="noBtn">Không</button>
</div>
<div id="likeBox" style="display: none;">
    <p>Cậu có quý tớ không?</p>
    <button id="yesLikeBtn">Có</button>
    <button id="noLikeBtn">Không</button>
</div>
<div id="questionBox" style="display: none;">
    <p>Cậu thấy tớ là con người như thế nào?</p>
    <input type="text" id="answerInput" placeholder="Nhập câu trả lời...">
    <button id="submitAnswer">Gửi</button>
</div>
    <script>
        
        const canvas = document.getElementById("birthdayCanvas");
const ctx = canvas.getContext("2d");
const startText = document.getElementById("startText");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const cakeX = (canvas.width - 200) / 2;  // Đặt bánh vào giữa màn hình
const cakeY = (canvas.height - 150) / 2; // Đặt bánh vào giữa màn hình

const tier1 = [
    {x: cakeX, y: cakeY + 150},
    {x: cakeX + 200, y: cakeY + 150},
    {x: cakeX + 200, y: cakeY + 110},
    {x: cakeX, y: cakeY + 110},
    {x: cakeX, y: cakeY + 150},
];

const tier2 = [
    {x: cakeX + 25, y: cakeY + 110},
    {x: cakeX + 175, y: cakeY + 110},
    {x: cakeX + 175, y: cakeY + 70},
    {x: cakeX + 25, y: cakeY + 70},
    {x: cakeX + 25, y: cakeY + 110},
];

const tier3 = [
    {x: cakeX + 50, y: cakeY + 70},
    {x: cakeX + 150, y: cakeY + 70},
    {x: cakeX + 150, y: cakeY + 30},
    {x: cakeX + 50, y: cakeY + 30},
    {x: cakeX + 50, y: cakeY + 70},
];

let step = 0;
let tierStep = 0;
let drawing = true;

function drawCakeOutline() {
    if (!drawing) return;  // Ngừng vẽ nếu không cần vẽ thêm

    ctx.strokeStyle = "black";
    ctx.lineWidth = 3;
    ctx.beginPath();

    let path;
    if (tierStep === 0) path = tier1;
    else if (tierStep === 1) path = tier2;
    else if (tierStep === 2) path = tier3;

    // Vẽ dần dần các điểm của mỗi tầng
    for (let i = 0; i <= step; i++) {
        if (i === 0) {
            ctx.moveTo(path[i].x, path[i].y);
        } else {
            ctx.lineTo(path[i].x, path[i].y);
        }
    }

    ctx.stroke();

    if (step < path.length - 1) {
        step++;
        setTimeout(drawCakeOutline, 100);  // Vẽ từ từ với thời gian mỗi lần là 100ms
    } else if (tierStep < 2) {
        tierStep++;
        step = 0;  // Reset lại bước vẽ cho tầng tiếp theo
        setTimeout(drawCakeOutline, 500);  // Thời gian nghỉ giữa các tầng
    } else {
        fillCake();  // Khi vẽ xong, đổ màu bánh
    }
}

function fillCake() {
    ctx.fillStyle = "#f4c2c2";  // Màu của bánh
    ctx.fillRect(cakeX, cakeY + 110, 200, 40);  // Đổ màu phần bánh tầng 1
    ctx.fillRect(cakeX + 25, cakeY + 70, 150, 40);  // Đổ màu phần bánh tầng 2
    ctx.fillRect(cakeX + 50, cakeY + 30, 100, 40);  // Đổ màu phần bánh tầng 3

    ctx.fillStyle = "#d2691e";  // Màu kem
    ctx.fillRect(cakeX, cakeY + 110, 200, 20);  // Phần kem tầng 1
    ctx.fillRect(cakeX + 25, cakeY + 70, 150, 20);  // Phần kem tầng 2
    ctx.fillRect(cakeX + 50, cakeY + 30, 100, 20);  // Phần kem tầng 3

  

    // Vẽ nến tại tầng 3, cao hơn một chút
    ctx.fillStyle = "yellow";
    ctx.fillRect(cakeX + 95, cakeY + -2, 10, 30);  // Vị trí của nến đã được nâng lên
    ctx.fillStyle = "red";
    ctx.beginPath();
    let flame = document.getElementById("candleFlame");
flame.style.left = (cakeX + 94) + "px";
flame.style.top = (cakeY - 20) + "px";
flame.style.display = "block";
let message = document.getElementById("birthdayMessage");
message.style.display = "block";
setTimeout(function() {
   document.getElementById("wishBox").style.display = "block";
}, 3000);
document.getElementById("confirmWish").addEventListener("click", function () {
    document.getElementById("wishBox").style.display = "none"; // Ẩn bảng nhập điều ước
    document.getElementById("blowCandleBtn").style.display = "block"; // Hiện nút thổi nến
});

document.getElementById("blowCandleBtn").addEventListener("click", function () {
    document.getElementById("candleFlame").style.display = "none"; // Tắt nến
    this.style.display = "none"; // Ẩn nút thổi nến sau khi bấm
});
document.getElementById("blowCandleBtn").addEventListener("click", function () {
    document.getElementById("candleFlame").style.display = "none"; // Tắt nến
    this.style.display = "none"; // Ẩn nút thổi nến sau khi bấm

    // Hiển thị bảng honestBox sau 2 giây
    setTimeout(function () {
        document.getElementById("honestBox").style.display = "block";
    }, 2000);
});
document.getElementById("noBtn").addEventListener("click", function () {
    this.style.display = "none"; // Ẩn nút "Không"

    let messageBox = document.createElement("div");
    messageBox.innerText = "Ô hình như nút không chạy mất rồi, sao cậu không thử bấm nút OK xem có chuyện gì không :))";
    
    // Định dạng hộp thông báo mà không làm ảnh hưởng layout
    Object.assign(messageBox.style, {
        position: "fixed",
        top: "30%", // Điều chỉnh vị trí cao hơn
        left: "50%",
        transform: "translate(-50%, -50%)",
        background: "rgba(0, 0, 0, 0.8)",
        color: "white",
        padding: "15px 20px",
        borderRadius: "10px",
        fontSize: "16px",
        textAlign: "center",
        zIndex: "9999",
        maxWidth: "80%",
        whiteSpace: "pre-wrap"
    });

    document.body.appendChild(messageBox);

    // Tự động ẩn sau 5 giây
    setTimeout(function () {
        messageBox.remove();
    }, 5000);
});

document.getElementById("yesBtn").addEventListener("click", function () {
    document.getElementById("honestBox").style.display = "none"; // Ẩn bảng hiện tại
    document.getElementById("likeBox").style.display = "block"; // Hiện bảng "Cậu có quý tớ không?"
});


document.getElementById("noLikeBtn").addEventListener("mouseover", function () {
    let box = document.getElementById("likeBox"); // Lấy vùng bảng
    let maxX = box.offsetWidth - this.offsetWidth - 20; // Giới hạn chiều ngang
    let maxY = box.offsetHeight - this.offsetHeight - 20; // Giới hạn chiều dọc

    let randomX = Math.random() * maxX;
    let randomY = Math.random() * maxY;

    this.style.left = randomX + "px";
    this.style.top = randomY + "px";
});
document.getElementById("noLikeBtn").addEventListener("mouseover", function () {
    let box = document.getElementById("likeBox");
    let btnYes = document.getElementById("yesLikeBtn");
    
    let maxX = box.offsetWidth - this.offsetWidth - 20; // Giới hạn chiều ngang
    let maxY = box.offsetHeight - this.offsetHeight - 20; // Giới hạn chiều dọc

    let randomX, randomY;
    do {
        randomX = Math.random() * maxX;
        randomY = Math.random() * maxY;
    } while (
        randomX > btnYes.offsetLeft - 50 && randomX < btnYes.offsetLeft + btnYes.offsetWidth + 50 &&
        randomY > btnYes.offsetTop - 50 && randomY < btnYes.offsetTop + btnYes.offsetHeight + 50
    );

    this.style.position = "absolute";
    this.style.left = randomX + "px";
    this.style.top = randomY + "px";
});
document.getElementById("yesLikeBtn").addEventListener("click", function () {
    let message = document.createElement("div");
    message.innerText = "chùii tớ cảm ơn :)))";
    message.style.position = "fixed";
    message.style.top = "20%";
    message.style.left = "50%";
    message.style.transform = "translateX(-50%)";
    message.style.background = "rgba(0, 0, 0, 0.8)";
    message.style.color = "white";
    message.style.padding = "10px 20px";
    message.style.borderRadius = "5px";
    message.style.fontSize = "18px";
    document.body.appendChild(message);

    setTimeout(() => {
        message.remove();
    }, 2000);
});

document.getElementById("noLikeBtn").addEventListener("mouseover", function () {
    let box = document.getElementById("likeBox");
    let btnYes = document.getElementById("yesLikeBtn");

    let maxX = box.offsetWidth - this.offsetWidth - 10;
    let maxY = box.offsetHeight - this.offsetHeight - 10;

    let randomX, randomY;
    do {
        randomX = Math.random() * maxX;
        randomY = Math.random() * maxY;
    } while (
        Math.abs(randomX - btnYes.offsetLeft) < 60 &&
        Math.abs(randomY - btnYes.offsetTop) < 60
    );

    this.style.left = randomX + "px";
    this.style.top = randomY + "px";
});
document.getElementById("yesLikeBtn").addEventListener("click", function () {
    // Ẩn bảng "Cậu có quý tớ không?"
    document.getElementById("likeBox").style.display = "none";

    // Hiện bảng câu hỏi "Cậu thấy tớ là người như thế nào?"
    document.getElementById("questionBox").style.display = "block";
});

document.getElementById("answerInput").addEventListener("input", function () {
    let correctText = "1 người tốt bụng, dz, thông minh, đúng mẫu của tớ :))";
    let currentLength = this.value.length;
    this.value = correctText.substring(0, currentLength);

    // Kiểm tra nếu có nội dung thì bật nút gửi
    document.getElementById("submitAnswer").disabled = currentLength === 0;
});

document.getElementById("submitAnswer").addEventListener("click", function () {
    if (document.getElementById("answerInput").value.trim() === "") {
        alert("Cậu phải nhập gì đó chứ! 😠");
        return;
    }

    // Ẩn bảng câu hỏi
    document.getElementById("questionBox").style.display = "none";

    // Hiện thông báo
    let message = document.createElement("div");
    message.innerText = "trời tớ thấy rồi đấy , iu thế 🙈";
    message.style.position = "fixed";
    message.style.top = "30%";
    message.style.left = "50%";
    message.style.transform = "translateX(-50%)";
    message.style.background = "rgba(0, 0, 0, 0.8)";
    message.style.color = "white";
    message.style.padding = "10px 20px";
    message.style.borderRadius = "5px";
    message.style.fontSize = "18px";
    message.style.zIndex = "9999";
    document.body.appendChild(message);

    // Tự động ẩn thông báo sau 5 giây và hiện bảng chúc mừng
    setTimeout(() => {
        message.remove();
        showBirthdayBox();
    }, 1500);
});

function showBirthdayBox() {
    let birthdayBox = document.createElement("div");
    birthdayBox.id = "birthdayBox";
    birthdayBox.innerHTML = `
        <p>Điều quan trọng nhắc lại nhiều lần,<br> chúc Bạn Thư sinh nhật vui vẻ nhé :))</p>
        <button id="heartBtn">❤️</button>
    `;
    birthdayBox.style.position = "fixed";
    birthdayBox.style.top = "50%";
    birthdayBox.style.left = "50%";
    birthdayBox.style.transform = "translate(-50%, -50%)";
    birthdayBox.style.background = "linear-gradient(135deg, #ff758c, #ff7eb3)";
    birthdayBox.style.padding = "25px";
    birthdayBox.style.borderRadius = "12px";
    birthdayBox.style.boxShadow = "0px 5px 15px rgba(0, 0, 0, 0.2)";
    birthdayBox.style.textAlign = "center";
    birthdayBox.style.zIndex = "10000";
    birthdayBox.style.width = "320px";
    birthdayBox.style.fontFamily = "Arial, sans-serif";
    birthdayBox.style.color = "white";
    birthdayBox.style.fontSize = "18px";

    document.body.appendChild(birthdayBox);

    // Xử lý khi bấm nút ❤️
    document.getElementById("heartBtn").addEventListener("click", function () {
        birthdayBox.remove();
    });
}

}


function addBalloons(count) {
    for (let i = 0; i < count; i++) {
        let balloon = document.createElement('div');
        balloon.classList.add('balloon');
        balloon.style.left = (Math.random() * 80 + 10) + 'vw';
        balloon.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 50%)`;
        balloon.style.animationDuration = (Math.random() * 2 + 4) + 's';
        document.body.appendChild(balloon);
        setTimeout(() => balloon.remove(), 6000);
    }
}

function createConfetti() {
    for (let i = 0; i < 50; i++) {
        let confetti = document.createElement('div');
        confetti.classList.add('confetti');
        confetti.style.left = `${Math.random() * 100}vw`;
        confetti.style.top = `${-Math.random() * 20}vh`;
        confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 70%)`;
        confetti.style.animationDuration = `${Math.random() * 3 + 2}s`;
        document.body.appendChild(confetti);
        setTimeout(() => confetti.remove(), 5000);
    }
}

startText.addEventListener("click", () => {
    startText.style.display = "none";
    canvas.style.display = "block";
    drawing = true;  // Bắt đầu vẽ
    drawCakeOutline();  // Bắt đầu vẽ bánh từ từ
    setTimeout(() => addBalloons(20), 2000);
    setTimeout(createConfetti, 2000);
});

    </script>

</body>
</html>
