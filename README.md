<!-- Add this CSS to your stylesheet or in <style> tags -->
<style>
  /* Toggle Switch - Position in top right */
  .theme-toggle-wrapper {
    position: fixed;
    top: 20px;
    right: 20px;
    z-index: 1000;
  }

  .toggle-checkbox {
    display: none;
  }

  .toggle-switch {
    position: relative;
    width: 80px;
    height: 40px;
    background: linear-gradient(180deg, #4FC3F7 0%, #03A9F4 100%);
    border-radius: 50px;
    cursor: pointer;
    transition: background 0.3s ease;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
    overflow: hidden;
  }

  .toggle-checkbox:checked + .toggle-switch {
    background: linear-gradient(180deg, #1a237e 0%, #303f9f 100%);
  }

  .toggle-slider {
    position: absolute;
    top: 4px;
    left: 4px;
    width: 32px;
    height: 32px;
    background: white;
    border-radius: 50%;
    transition: transform 0.3s ease;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .toggle-checkbox:checked + .toggle-switch .toggle-slider {
    transform: translateX(40px);
  }

  .sun-icon {
    position: absolute;
    width: 20px;
    height: 20px;
    transition: opacity 0.3s ease, transform 0.3s ease;
  }

  .sun-icon::before {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle, #FDD835 40%, #FBC02D 100%);
    border-radius: 50%;
  }

  .sun-icon::after {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: 
      linear-gradient(0deg, transparent 45%, #FDD835 45%, #FDD835 55%, transparent 55%),
      linear-gradient(90deg, transparent 45%, #FDD835 45%, #FDD835 55%, transparent 55%),
      linear-gradient(45deg, transparent 45%, #FDD835 45%, #FDD835 55%, transparent 55%),
      linear-gradient(-45deg, transparent 45%, #FDD835 45%, #FDD835 55%, transparent 55%);
    transform: scale(1.5);
    animation: rotate 20s linear infinite;
  }

  @keyframes rotate {
    to { transform: scale(1.5) rotate(360deg); }
  }

  .toggle-checkbox:checked + .toggle-switch .sun-icon {
    opacity: 0;
    transform: scale(0);
  }

  .moon-icon {
    position: absolute;
    width: 20px;
    height: 20px;
    opacity: 0;
    transform: scale(0);
    transition: opacity 0.3s ease, transform 0.3s ease;
  }

  .moon-icon::before {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: #f5f5f5;
    border-radius: 50%;
    box-shadow: inset -4px -2px 0 0 #e0e0e0;
  }

  .toggle-checkbox:checked + .toggle-switch .moon-icon {
    opacity: 1;
    transform: scale(1);
  }

  .toggle-switch::before {
    content: '';
    position: absolute;
    width: 3px;
    height: 3px;
    background: white;
    border-radius: 50%;
    top: 10px;
    right: 50px;
    opacity: 0;
    transition: opacity 0.3s ease;
    box-shadow: 
      -8px 8px 0 white,
      -5px -5px 0 white,
      -12px 15px 0 white;
  }

  .toggle-checkbox:checked + .toggle-switch::before {
    opacity: 0.8;
  }

  .toggle-switch::after {
    content: '';
    position: absolute;
    width: 15px;
    height: 6px;
    background: white;
    border-radius: 10px;
    top: 12px;
    left: 50px;
    opacity: 1;
    transition: opacity 0.3s ease;
    box-shadow: 
      -5px 0 0 3px white,
      5px 0 0 3px white,
      -20px 10px 0 2px white,
      -25px 10px 0 4px white;
  }

  .toggle-checkbox:checked + .toggle-switch::after {
    opacity: 0;
  }

  .toggle-switch:hover {
    transform: scale(1.05);
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

<!-- Add this HTML where you want the toggle (or keep wrapper in top right) -->
<div class="theme-toggle-wrapper">
  <label>
    <input type="checkbox" class="toggle-checkbox" id="themeToggle">
    <div class="toggle-switch">
      <div class="toggle-slider">
        <div class="sun-icon"></div>
        <div class="moon-icon"></div>
      </div>
    </div>
  </label>
</div>

<!-- Add this JavaScript before closing </body> tag -->
<script>
  const toggle = document.getElementById('themeToggle');
  const body = document.body;

  // Load saved theme
  const currentTheme = localStorage.getItem('theme') || 'light-mode';
  body.classList.add(currentTheme);
  
  if (currentTheme === 'dark-mode') {
    toggle.checked = true;
  }

  // Toggle theme
  toggle.addEventListener('change', () => {
    if (toggle.checked) {
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
