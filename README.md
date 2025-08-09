<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Raksha Bandhan Trisha 💙</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="lights"></div>

    <!-- Gift Box -->
    <div id="gift-box">
        <img src="images/gift-box.png" alt="Gift Box">
    </div>

    <!-- Slap Hand -->
    <div id="slap-hand">
        <img src="images/slap-hand.png" alt="Hand">
    </div>

    <!-- Monkey -->
    <div id="monkey">
        <img src="images/monkey.png" alt="Monkey">
    </div>

    <!-- Letter -->
    <div id="letter">
        <p id="letter-text"></p>
    </div>

    <!-- Final Message -->
    <div id="final-message">
        <h2>From your Brother, Naman 💙✨</h2>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    margin: 0;
    padding: 0;
    background-color: #0a1a3b;
    font-family: 'Segoe UI', sans-serif;
    color: white;
    overflow: hidden;
}

.lights {
    position: fixed;
    width: 100%;
    height: 100%;
    background: url('images/rakhi-lights.png') repeat;
    animation: floatLights 10s linear infinite;
    opacity: 0.4;
}

@keyframes floatLights {
    0% { background-position: 0 0; }
    100% { background-position: 100px 100px; }
}

#gift-box, #slap-hand, #monkey, #letter, #final-message {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
}

#gift-box img {
    width: 200px;
    cursor: pointer;
    margin-top: 30vh;
}

#slap-hand {
    top: 20vh;
    display: none;
}

#slap-hand img {
    width: 150px;
}

#monkey {
    top: -200px;
    display: none;
}

#monkey img {
    width: 200px;
}

#letter {
    width: 60%;
    margin-top: 20vh;
    display: none;
    text-align: center;
    font-size: 18px;
    line-height: 1.6;
}

#final-message {
    display: none;
    margin-top: 40vh;
    text-align: center;
}
const letterText = `
My Dearest Sister Trisha,  

Happy Rakshabandhan to my *sister from another mother*! 💖  

It’s still crazy to me that we’ve known each other for only two months, because honestly, it feels like a lifetime. In such a short time, you’ve become my safe space, my gossip partner, my cheerleader, my partner-in-crime, and my personal “therapist” when I overthink everything.  

We didn’t grow up together, we didn’t share the same childhood, but somehow the universe decided we needed each other now — and I’m so grateful it did. The way we clicked instantly, the way we understand each other’s unspoken words, and the way we can laugh at the most random things… it’s something rare.  

On Rakshabandhan, people celebrate the bond between a brother and sister, but I believe the heart chooses its own family — and you are my family. Even without tying a rakhi, I promise you my protection, loyalty, and unconditional support in every chapter of your life. I’ll be there to hype you up in your wins and hold you through your losses.  

Thank you for accepting me as I am, for listening when I rant, for making me laugh when I’m low, and for trusting me with your own stories. Our bond is proof that time doesn’t define relationships — connection does.  

So here’s to our inside jokes, our endless chats, our deep talks at random hours, and the unshakable bond we’ve built in just two months. I’m lucky to have you in my life, and I know this is just the start of a lifelong *siblinghood*.  

Love you loads, my sistern.  
Your partner in crime,  
Naman 💙✨
`;

const giftBox = document.getElementById('gift-box');
const slapHand = document.getElementById('slap-hand');
const monkey = document.getElementById('monkey');
const letter = document.getElementById('letter');
const letterTextElem = document.getElementById('letter-text');
const finalMessage = document.getElementById('final-message');

giftBox.addEventListener('click', () => {
    slapHand.style.display = 'block';
    new Audio('sounds/slap.mp3').play();

    setTimeout(() => {
        giftBox.style.display = 'none';
        slapHand.style.display = 'none';
        monkey.style.display = 'block';
        monkey.style.transition = 'top 1s ease';
        monkey.style.top = '100px';
    }, 1000);

    setTimeout(() => {
        monkey.style.display = 'none';
        letter.style.display = 'block';
        typeWriter(letterText, 0);
        new Audio('sounds/paper-open.mp3').play();
    }, 3000);
});

function typeWriter(text, i) {
    if (i < text.length) {
        letterTextElem.innerHTML += text.charAt(i);
        setTimeout(() => typeWriter(text, i + 1), 30);
    } else {
        setTimeout(() => {
            letter.style.display = 'none';
            finalMessage.style.display = 'block';
        }, 3000);
    }
}

