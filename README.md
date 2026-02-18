
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: pink;
    }

    /* SLAYT ARKA PLAN */
    body::before {
      content: "";
      position: absolute;
      inset: 0;
      background: url("foto1.jpg") center/cover no-repeat;
      animation: slide 12s infinite;
      z-index: -2;
      filter: blur(3px) brightness(0.7);
    }

    @keyframes slide {
      0%   { background-image: url("foto1.jpg"); }
      33%  { background-image: url("foto2.jpg"); }
      66%  { background-image: url("foto3.jpg"); }
      100% { background-image: url("foto1.jpg"); }
    }

    .card {
      background: rgba(255,255,255,0.9);
      padding: 35px;
      border-radius: 25px;
      text-align: center;
      max-width: 500px;
      box-shadow: 0 0 25px rgba(255, 0, 120, 0.4);
    }

    h1 {
      color: #ff2f87;
      font-size: 28px;
    }

    p {
      font-size: 18px;
      color: #444;
      line-height: 1.6;
    }

    button {
      margin-top: 20px;
      padding: 12px 25px;
      border: none;
      border-radius: 20px;
      font-size: 18px;
      cursor: pointer;
      background: #ff2f87;
      color: white;
      transition: 0.2s;
    }

    button:hover {
      transform: scale(1.05);
    }

    /* FINAL YAZI */
    #finalText {
      display: none;
      font-size: 28px;
      font-weight: bold;
      color: #ff0066;
      margin-top: 25px;
      animation: shake 0.3s infinite alternate;
    }

    @keyframes shake {
      from { transform: translateX(-3px); }
      to   { transform: translateX(3px); }
    }

    /* KAYAN YAZI */
    #marquee {
      display: none;
      margin-top: 20px;
      font-size: 22px;
      color: purple;
      font-weight: bold;
      white-space: nowrap;
      overflow: hidden;
    }

    #marquee span {
      display: inline-block;
      padding-left: 100%;
      animation: move 6s linear infinite;
    }

    @keyframes move {
      from { transform: translateX(0); }
      to   { transform: translateX(-100%); }
    }

    /* KALPLER */
    .heart {
      position: absolute;
      font-size: 25px;
      animation: fall 4s linear forwards;
    }

    @keyframes fall {
      from { transform: translateY(-50px); opacity: 1; }
      to   { transform: translateY(100vh); opacity: 0; }
    }

    /* KONFETİ */
    .confetti {
      position: absolute;
      width: 10px;
      height: 10px;
      animation: confettiFall 3s linear forwards;
    }

    @keyframes confettiFall {
      from { transform: translateY(0); opacity: 1; }
      to   { transform: translateY(100vh); opacity: 0; }
    }
  </style>
</head>

<body>

  <!-- 🎶 MÜZİK -->
  <audio id="music" src="muzik.mp3"></audio>

  <div class="card">
    <h1>💖 Sana Bir Şey Söylemek İstiyorum 💖</h1>

    <p id="text">
      Her şeyi bir kenara bırakıp benimle tekrardan sevgili olur musun?
    </p>

    <button onclick="nextStep()">Devam Et 💗</button>

    <div id="finalText">SENİİİ SEVİYORUMMMM AŞKIMMMM HELELELELE 💘💘💘</div>

    <div id="marquee">
      <span>SENİ SEVİYORUMMMM 💖 SENİ SEVİYORUMMMM 💖 SENİ SEVİYORUMMMM 💖</span>
    </div>
  </div>

  <script>
    let step = 0;

    function nextStep() {

      // 🎵 Butona basınca müzik başlar
      document.getElementById("music").play();

      const text = document.getElementById("text");

      step++;

      if(step === 1){
        text.innerHTML =
          "Kendimi daha fazla tutamadım... Kıskanıyordum, aklıma gelince deli oluyordum.";
      }

      else if(step === 2){
        text.innerHTML =
          "Daha fazla uzatmadan söylemek istedim... Kalbim hala sende 💗";
      }

      else if(step === 3){
        text.innerHTML =
          "Eğer sen de istiyorsan sadece 'ben de seni seviyorum' demen yeterli 💞";
      }

      else if(step === 4){
        document.getElementById("finalText").style.display = "block";
        document.getElementById("marquee").style.display = "block";

        startHearts();
        startConfetti();
      }
    }

    function startHearts(){
      setInterval(() => {
        let heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "💖";
        heart.style.left = Math.random() * 100 + "vw";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 4000);
      }, 300);
    }

    function startConfetti(){
      for(let i=0;i<40;i++){
        let conf = document.createElement("div");
        conf.className = "confetti";
        conf.style.left = Math.random() * 100 + "vw";
        conf.style.top = "-20px";
        conf.style.background = "white";
        document.body.appendChild(conf);

        setTimeout(() => conf.remove(), 3000);
      }
    }
  </script>

</body>
</html>
