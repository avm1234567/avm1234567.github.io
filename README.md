<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Cloud Switch Button</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(to top right, #89f7fe, #66a6ff);
      margin: 0;
      font-family: sans-serif;
    }
    .shadow {
      filter: drop-shadow(0 5px 8px rgba(0, 0, 0, 0.3));
    }
    .switch {
      position: relative;
      width: 140px;
      height: 70px;
      border: none;
      outline: none;
      background: linear-gradient(to bottom, #b4e1ff, #ffffff);
      border-radius: 50px;
      cursor: pointer;
      overflow: hidden;
      transition: background 0.6s ease;
    }
    .switch__inner {
      position: relative;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: all 0.6s ease;
    }
    .switch__cloud {
      position: absolute;
      width: 60px;
      opacity: 0.9;
      transition: transform 0.8s ease, opacity 0.6s ease;
    }
    .switch__cloud.--1 {
      top: 10px;
      left: 15px;
    }
    .switch__cloud.--2 {
      bottom: 10px;
      right: 15px;
    }
    .switch-globe {
      position: relative;
      width: 40px;
      height: 40px;
      background: #f5f5f5;
      border-radius: 50%;
      box-shadow: inset -5px -5px 15px rgba(0, 0, 0, 0.1);
      transition: all 0.6s ease;
    }
    .switch-globe__circle {
      position: absolute;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: #ffd97d;
      transition: all 0.6s ease;
    }
    .switch-globe__moon {
      position: absolute;
      width: 30px;
      top: 5px;
      left: 5px;
      opacity: 0;
      transition: opacity 0.6s ease;
    }
    .switch__stars {
      position: absolute;
      width: 100%;
      opacity: 0;
      transition: opacity 0.6s ease;
    }
    /* --- Active (Night) Mode --- */
    .switch.active {
      background: linear-gradient(to top, #202020, #3b3b98);
    }
    .switch.active .switch__cloud {
      opacity: 0;
      transform: translateY(-15px);
    }
    .switch.active .switch-globe__circle {
      background: #555;
    }
    .switch.active .switch-globe__moon {
      opacity: 1;
    }
    .switch.active .switch__stars {
      opacity: 1;
    }
  </style>
</head>
<body>

  <span class="shadow">
    <button type="button" class="switch" id="themeSwitch">
      <img class="switch__cloud --2" src="https://assets.codepen.io/58281/cloud-1.svg" />
      <img class="switch__cloud --1" src="https://assets.codepen.io/58281/cloud-2.svg" />
      <div class="switch__inner">
        <div class="switch-globe">
          <img class="switch-globe__moon" src="https://assets.codepen.io/58281/moon_1.png" />
          <div class="switch-globe__circle"></div>
        </div>
        <img class="switch__stars" src="https://assets.codepen.io/58281/stars.svg" />
      </div>
    </button>
  </span>

  <script>
    const switchBtn = document.getElementById('themeSwitch');
    switchBtn.addEventListener('click', () => {
      switchBtn.classList.toggle('active');
      document.body.style.background = switchBtn.classList.contains('active')
        ? 'linear-gradient(to top, #0f2027, #203a43, #2c5364)'
        : 'linear-gradient(to top right, #89f7fe, #66a6ff)';
    });
  </script>

</body>
</html>

