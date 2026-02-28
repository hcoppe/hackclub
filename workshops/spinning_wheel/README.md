<!DOCTYPE html>
<html>
<head>
  <title>Spinning Wheel</title>
  <style>
    body {
      text-align: center;
      font-family: Arial, sans-serif;
    }

    #wheel {
      margin: 30px auto;
      width: 300px;
      height: 300px;
      border-radius: 50%;
      border: 10px solid #333;
      position: relative;
      overflow: hidden;
      transition: transform 4s ease-out;
    }

    .slice {
      position: absolute;
      width: 50%;
      height: 50%;
      top: 50%;
      left: 50%;
      transform-origin: 0% 0%;
      text-align: right;
      padding-right: 10px;
      font-weight: bold;
      font-size: 16px;
    }

    #pointer {
      width: 0;
      height: 0;
      border-left: 20px solid transparent;
      border-right: 20px solid transparent;
      border-bottom: 40px solid red;
      margin: 0 auto;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<h2>Spinning Name Wheel</h2>

<div id="pointer"></div>
<div id="wheel"></div>

<button onclick="spinWheel()">Spin</button>

<script>
  const names = ["Abby", "Hannah", "Olivia", "Jordan"];
  const wheel = document.getElementById("wheel");
  let currentSpin = 0;

  // Create slices
  names.forEach((name, i) => {
    const slice = document.createElement("div");
    slice.className = "slice";
    slice.style.transform = `rotate(${i * 90}deg) skewY(-45deg)`;
    slice.style.background = i % 2 === 0 ? "#f8b400" : "#6a67ce";
    slice.innerHTML = `<span style="display:block; transform: skewY(45deg) rotate(45deg);">${name}</span>`;
    wheel.appendChild(slice);
  });

  function spinWheel() {
    if (currentSpin >= names.length) {
      alert("All names have been picked!");
      return;
    }

    const predeterminedAngles = [
      360 * 3 + 0,     // Abby
      360 * 3 + 90,    // Hannah
      360 * 3 + 180,   // Olivia
      360 * 3 + 270    // Jordan
    ];

    wheel.style.transform = `rotate(-${predeterminedAngles[currentSpin]}deg)`;
    currentSpin++;
  }
</script>

</body>
</html>
