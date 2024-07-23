# background-generator
<!DOCTYPE html>
<html>
<head>
  <title>Gradient Background Generator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
    #gradient-preview {
      width: 100%;
      height: 300px;
      border: 1px solid #ccc;
      border-radius: 10px;
      margin: 20px;
      
      
    }
   .color-picker {
      width: 100px;
      height: 100px;
      border: 1px solid #ccc;
      border-radius: 10px;
      cursor: pointer;
    }
   .color-picker:hover {
      border-color: #aaa;
    }
    
  </style>
</head>
<body>
  <h1>Gradient Background Generator</h1>
  <div id="gradient-preview"></div>
  <div>
    <label for="color1" style="color: green; ">Color 1:</label>
    <input type="color" id="color1" value="#ff69b4">
    <div class="color-picker" id="color-picker-1" style="background-color: #ff69b4;"></div>
  </div>
  <div>
    <label for="color2" style="color: red;">Color 2:</label>
    <input type="color" id="color2" value="#33ccff">
    <div class="color-picker" id="color-picker-2" style="background-color: #33ccff;"></div>
  </div>
  <div>
    <label for="gradient-type" style="color:black;">Gradient Type:</label>
    <select id="gradient-type">
      <option value="linear">Linear</option>
      <option value="radial">Radial</option>
    </select>
  </div>
  <div>
    <label for="angle">Angle:</label>
    <input type="range" id="angle" min="0" max="360" value="45">
  </div>
  <script>
    const gradientPreview = document.getElementById('gradient-preview');
    const color1Input = document.getElementById('color1');
    const color2Input = document.getElementById('color2');
    const gradientTypeSelect = document.getElementById('gradient-type');
    const angleInput = document.getElementById('angle');

    function updateGradient() {
      const color1 = color1Input.value;
      const color2 = color2Input.value;
      const gradientType = gradientTypeSelect.value;
      const angle = angleInput.value;

      let gradientString = '';
      if (gradientType === 'linear') {
        gradientString = `linear-gradient(${angle}deg, ${color1}, ${color2})`;
      } else if (gradientType === 'radial') {
        gradientString = `radial-gradient(${color1}, ${color2})`;
      }

      gradientPreview.style.backgroundImage = gradientString;
    }

    color1Input.addEventListener('input', updateGradient);
    color2Input.addEventListener('input', updateGradient);
    gradientTypeSelect.addEventListener('change', updateGradient);
    angleInput.addEventListener('input', updateGradient);

    updateGradient();
  </script>
</body>
</html>
