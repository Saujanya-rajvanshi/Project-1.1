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
