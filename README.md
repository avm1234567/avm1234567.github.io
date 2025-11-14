
<!-- Add this CSS to your stylesheet -->
<style>
  /* Toggle Switch - Position in top right */
  .theme-toggle-wrapper {
    position: fixed;
    top: 20px;
    right: 20px;
    z-index: 1000;
  }

  button {
    outline: 0;
    background: transparent;
    border-radius: 0;
    border: 0;
    appearance: none;
    box-shadow: none;
    cursor: pointer;
  }

  .switch {
    --font-size: 10px;
    
    --height: 5em;
    --width: 12em;
    --margin: 0.1em;
    
    --color-night: rgba(15, 64, 91, 1);
    --color-day: rgba(91, 169, 211, 1);
    --color-sun: rgba(246, 211, 90, 1);
    
    --ease: cubic-bezier(0.770, 0.000, 0.175, 1.000);
    --duration: .85s;
    
    font-size: var(--font-size);
    position: relative;
    width: var(--width);
    height: var(--height);
    border-radius: 999px;
    background-color: var(--color-day);
    overflow: hidden;
    z-index: 2;
  }

  .switch:after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: var(--color-night);
    transition: opacity var(--duration) var(--ease);
    opacity: 0;
    z-index: 1;
  }

  .switch.is-active:after {
    opacity: 1;
  }

  .switch__inner {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    transform-origin: right;
    transform: translate3d(calc(var(--width) - var(--height)), 0, 0);
    transition: transform var(--duration) var(--ease);
    z-index: 2;
  }

  .is-active .switch__inner {
    transform: translate3d(0, 0, 0);
  }

  .switch-globe {
    --size: calc(var(--height) - (var(--margin) * 2));
    
    position: relative;
    height: var(--size);
    width: var(--size);
    margin: var(--margin) 0 0 var(--margin);
    border-radius: 999px;
    background-color: var(--color-sun);
    transform: rotate(90deg);
    transition: transform var(--duration) var(--ease);
    z-index: 1;
  }

  .is-active .switch-globe {
    transform: rotate(0);
  }

  .switch-globe__circle {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 50%;
    width: 100%;
    border-radius: 999px;
    background-color: var(--color-day);
    transform: translate3d(50%, 0, 0);
    transition: 
      transform var(--duration) var(--ease), 
      background-color var(--duration) var(--ease);
  }

  .is-active .switch-globe__circle {
    background-color: var(--color-night);
    transform: translate3d(-10%, 0, 0);
  }

  .switch-globe__moon {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    border-radius: 999px;
    object-fit: cover;
    transform: scaleX(-1);
    opacity: 0;
    transition: opacity var(--duration) var(--ease);
  }

  .is-active .switch-globe__moon {
    opacity: 1;
  }

  .switch__stars {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    transform-origin: right;
    transform: scale(.25);
    transition: transform var(--duration) var(--ease);
    z-index: 2;
    pointer-events: none;
  }

  .switch__stars::before {
    content: '';
    position: absolute;
    width: 0.3rem;
    height: 0.3rem;
    background: white;
    border-radius: 50%;
    top: 2rem;
    right: 3rem;
    box-shadow: 
      1rem 1.5rem 0 0.1rem white,
      -0.5rem 1rem 0 0.05rem white,
      2rem 3rem 0 0.15rem white,
      -1rem 2.5rem 0 0.08rem white,
      1.5rem 0.5rem 0 0.12rem white,
      2.5rem 2rem 0 0.1rem white;
  }

  .is-active .switch__stars {
    transform: scale(0.9);
  }

  .switch__cloud {
    position: absolute;
    transition: transform var(--duration) var(--ease);
    bottom: 1rem;
  }

  .switch__cloud.--1 {
    left: 0.5rem;
    width: 4rem;
    height: 1.5rem;
    background: white;
    border-radius: 50px;
    opacity: 0.9;
  }

  .switch__cloud.--1::before {
    content: '';
    position: absolute;
    width: 2rem;
    height: 2rem;
    background: white;
    border-radius: 50%;
    top: -0.8rem;
    left: 0.5rem;
  }

  .switch__cloud.--1::after {
    content: '';
    position: absolute;
    width: 1.5rem;
    height: 1.5rem;
    background: white;
    border-radius: 50%;
    top: -0.5rem;
    right: 0.5rem;
  }

  .is-active .switch__cloud.--1 {
    transform: translate3d(-3rem, 1rem, 0);
  }

  .switch__cloud.--2 {
    left: 4rem;
    width: 3rem;
    height: 1.2rem;
    background: white;
    border-radius: 50px;
    opacity: 0.85;
  }

  .switch__cloud.--2::before {
    content: '';
    position: absolute;
    width: 1.5rem;
    height: 1.5rem;
    background: white;
    border-radius: 50%;
    top: -0.6rem;
    left: 0.5rem;
  }

  .switch__cloud.--2::after {
    content: '';
    position: absolute;
    width: 1.2rem;
    height: 1.2rem;
    background: white;
    border-radius: 50%;
    top: -0.4rem;
    right: 0.5rem;
  }

  .is-active .switch__cloud.--2 {
    transform: translate3d(-1rem, 3rem, 0);
  }

  .shadow {
    box-shadow: 2px 4px 12px -2px rgba(0, 0, 0, 0.25);
    border-radius: 999px;
  }

  /* Theme styles for your body */
  body {
    transition: background-color 0.3s ease, color 0.3s ease;
  }

  body.light-mode {
    background-color: #ffffff;
    color: #333333;
  }

  body.dark-mode {
    background-color: #1a1a2e;
    color: #f0f0f0;
  }
</style>

<!-- Add this HTML in your body -->
<div class="theme-toggle-wrapper">
  <span class="shadow">
    <button type="button" class="switch" id="themeToggle">
      <div class="switch__cloud --2"></div>
      <div class="switch__cloud --1"></div>
      <div class="switch__inner">
        <div class="switch-globe">
          <img class="switch-globe__moon" src="https://assets.codepen.io/58281/moon_1.png" />
          <div class="switch-globe__circle"></div>
        </div>
        <div class="switch__stars"></div>
      </div>
    </button>
  </span>
</div>

<!-- Add this JavaScript before closing </body> tag -->
<script>
  const toggle = document.getElementById('themeToggle');
  const body = document.body;

  // Load saved theme
  const currentTheme = localStorage.getItem('theme') || 'light-mode';
  body.classList.add(currentTheme);
  
  if (currentTheme === 'dark-mode') {
    toggle.classList.add('is-active');
  }

  // Toggle theme
  toggle.addEventListener('click', () => {
    toggle.classList.toggle('is-active');
    
    if (toggle.classList.contains('is-active')) {
      body.classList.remove('light-mode');
      body.classList.add('dark-mode');
      localStorage.setItem('theme', 'dark-mode');
    } else {
      body.classList.remove('dark-mode');
      body.classList.add('light-mode');
      localStorage.setItem('theme', 'light-mode');
    }
  });
</script>
