# Project-1.1

###html code

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GreenIQ - Carbon Footprint Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: url('https://images.unsplash.com/photo-1501004318641-b39e6451bec6') no-repeat center center/cover;
      color: #fff;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container {
      background: rgba(0, 0, 0, 0.7);
      padding: 30px;
      border-radius: 12px;
      width: 400px;
      text-align: center;
    }

    h2 {
      margin-bottom: 20px;
      color: #90ee90;
    }

    label {
      display: block;
      text-align: left;
      margin: 10px 0 5px;
    }

    input {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 6px;
      margin-bottom: 15px;
    }

    button {
      background: #28a745;
      color: white;
      padding: 12px;
      width: 100%;
      border: none;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #218838;
    }

    .result {
      margin-top: 20px;
      padding: 15px;
      background: #222;
      border-radius: 8px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>🌱 Carbon Footprint Calculator</h2>
    <form id="footprintForm">
      <label for="electricity">Monthly Electricity Usage (kWh):</label>
      <input type="number" id="electricity" required>

      <label for="car">Weekly Car Travel (km):</label>
      <input type="number" id="car" required>

      <label for="flights">Flights Taken per Year:</label>
      <input type="number" id="flights" required>

      <button type="submit">Calculate</button>
    </form>

    <div id="result" class="result"></div>
  </div>

  <script>
    document.getElementById("footprintForm").addEventListener("submit", function(e) {
      e.preventDefault();

      const electricity = parseFloat(document.getElementById("electricity").value) || 0;
      const car = parseFloat(document.getElementById("car").value) || 0;
      const flights = parseFloat(document.getElementById("flights").value) || 0;

      // Conversion factors
      const electricityFactor = 0.92; // kg CO₂ / kWh
      const carFactor = 0.21;         // kg CO₂ / km
      const flightFactor = 250;       // kg CO₂ / flight

      const monthlyFootprint = (electricity * electricityFactor) + (car * 4 * carFactor) + (flights * (flightFactor / 12));
      const yearlyFootprint = monthlyFootprint * 12;

      document.getElementById("result").innerHTML = `
        <h3>🌍 Your Carbon Footprint:</h3>
        <p><strong>${monthlyFootprint.toFixed(2)}</strong> kg CO₂ / month</p>
        <p><strong>${yearlyFootprint.toFixed(2)}</strong> kg CO₂ / year</p>
      `;
    });
  </script>

</body>
</html>
```


###css

```css
/* ===== General Page Styling ===== */
body {
    margin: 0;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    background: url('https://images.unsplash.com/photo-1503264116251-35a269479413') no-repeat center center/cover;
    color: #222;
    line-height: 1.6;
}

/* Dark overlay for readability */
body::before {
    content: "";
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.7);
    z-index: -1;
}

/* ===== Layout ===== */
.container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding: 40px;
    max-width: 1200px;
    margin: auto;
}

/* ===== Left Side: Form ===== */
.form-section {
    flex: 1;
    max-width: 400px;
    background: #ffffffcc;
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0px 6px 15px rgba(0, 0, 0, 0.15);
}

.form-section h2 {
    text-align: center;
    margin-bottom: 20px;
    color: #2e7d32;
}

label {
    display: block;
    font-weight: bold;
    margin: 12px 0 6px;
}

input {
    width: 100%;
    padding: 10px;
    border: 1px solid #bbb;
    border-radius: 8px;
    outline: none;
    transition: 0.3s;
}

input:focus {
    border-color: #2e7d32;
    box-shadow: 0 0 6px rgba(46, 125, 50, 0.4);
}

button {
    display: block;
    width: 100%;
    margin-top: 20px;
    padding: 12px;
    border: none;
    border-radius: 8px;
    background: #2e7d32;
    color: #fff;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    background: #1b5e20;
}

/* ===== Right Side: Info ===== */
.info-section {
    flex: 1.5;
    margin-left: 40px;
    background: #ffffffcc;
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0px 6px 15px rgba(0, 0, 0, 0.15);
}

.info-section h3 {
    color: #2e7d32;
    margin-bottom: 12px;
}

.info-section p {
    margin-bottom: 15px;
}

/* Links */
a {
    color: #2e7d32;
    font-weight: bold;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}
```

###js

```js
console.log("script.jsis connected");
document.getElementById("carbonForm").addEventListener("submit", function(e) {
    e.preventDefault(); // stop page reload

    // Get input values
    const electricity = parseFloat(document.getElementById("electricity").value) || 0;
    const car = parseFloat(document.getElementById("car").value) || 0;
    const flights = parseFloat(document.getElementById("flights").value) || 0;

    // Simple carbon footprint formula (example multipliers)
    const electricityFactor = 0.92; // kg CO2 per kWh
    const carFactor = 0.21; // kg CO2 per km
    const flightFactor = 250; // kg CO2 per flight

    // Calculate footprint
    const monthlyFootprint = (electricity * electricityFactor) + (car * 4 * carFactor) + (flights * (flightFactor / 12));
    const yearlyFootprint = monthlyFootprint * 12;

    // Display result
    const resultBox = document.getElementById("resultBox");
    const resultText = document.getElementById("resultText");

    resultText.innerHTML = `
        🌍 <strong>${monthlyFootprint.toFixed(2)}</strong> kg CO₂ per month 
        <br> 📅 <strong>${yearlyFootprint.toFixed(2)}</strong> kg CO₂ per year
    `;

    resultBox.style.display = "block";
});

```
