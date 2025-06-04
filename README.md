a<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Currency Converter</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f2f5f8;
      color: #333;
      padding: 30px;
      text-align: center;
    }

    h1 {
      margin-bottom: 30px;
    }

    .converter {
      max-width: 400px;
      margin: auto;
      padding: 30px;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }

    select, input {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      font-size: 1rem;
    }

    button {
      width: 100%;
      padding: 12px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
    }

    button:hover {a
      background-color: #0056b3;
    }

    .result {
      margin-top: 20px;
      font-size: 1.3rem;
      font-weight: bold;
    }

    footer {
      margin-top: 30px;
      color: #888;
      font-size: 0.9rem;
    }
  </style>
</head>
<body>

  <h1>Currency Converter</h1>

  <div class="converter">
    <input type="number" id="amount" placeholder="Enter amount" />

    <select id="fromCurrency">
      <option value="USD">USD - US Dollar</option>
      <option value="EUR">EUR - Euro</option>
      <option value="INR">INR - Indian Rupee</option>
      <option value="GBP">GBP - British Pound</option>
      <option value="CAD">CAD - Canadian Dollar</option>
      <option value="JPY">JPY - Japanese Yen</option>
      <option value="AUD">AUD - Australian Dollar</option>
      <option value="CNY">CNY - Chinese Yuan</option>
      <option value="CHF">CHF - Swiss Franc</option>
      <option value="BRL">BRL - Brazilian Real</option>
    </select>

    <select id="toCurrency">
      <option value="INR">INR - Indian Rupee</option>
      <option value="USD">USD - US Dollar</option>
      <option value="EUR">EUR - Euro</option>
      <option value="GBP">GBP - British Pound</option>
      <option value="CAD">CAD - Canadian Dollar</option>
      <option value="JPY">JPY - Japanese Yen</option>
      <option value="AUD">AUD - Australian Dollar</option>
      <option value="CNY">CNY - Chinese Yuan</option>
      <option value="CHF">CHF - Swiss Franc</option>
      <option value="BRL">BRL - Brazilian Real</option>
    </select>

    <button onclick="convertCurrency()">Convert</button>

    <div class="result" id="resultText">Converted amount will appear here</div>
  </div>

  <footer>Simple Currency Converter Web App</footer>

  <script>
    const exchangeRates = {
      USD: { USD: 1, EUR: 0.92, INR: 83.2, GBP: 0.79, CAD: 1.36, JPY: 155.2, AUD: 1.51, CNY: 7.24, CHF: 0.90, BRL: 5.24 },
      EUR: { USD: 1.09, EUR: 1, INR: 90.5, GBP: 0.86, CAD: 1.48, JPY: 169.3, AUD: 1.64, CNY: 7.9, CHF: 0.98, BRL: 5.7 },
      INR: { USD: 0.012, EUR: 0.011, INR: 1, GBP: 0.0095, CAD: 0.016, JPY: 1.87, AUD: 0.018, CNY: 0.087, CHF: 0.011, BRL: 0.069 },
      GBP: { USD: 1.26, EUR: 1.16, INR: 105.3, GBP: 1, CAD: 1.72, JPY: 196.7, AUD: 1.91, CNY: 9.2, CHF: 1.14, BRL: 6.55 },
      CAD: { USD: 0.74, EUR: 0.67, INR: 61.4, GBP: 0.58, CAD: 1, JPY: 114.3, AUD: 1.11, CNY: 5.36, CHF: 0.66, BRL: 3.8 },
      JPY: { USD: 0.0064, EUR: 0.0059, INR: 0.53, GBP: 0.0051, CAD: 0.0088, JPY: 1, AUD: 0.0097, CNY: 0.047, CHF: 0.0058, BRL: 0.033 },
      AUD: { USD: 0.66, EUR: 0.61, INR: 55.3, GBP: 0.52, CAD: 0.90, JPY: 103.2, AUD: 1, CNY: 4.85, CHF: 0.59, BRL: 3.45 },
      CNY: { USD: 0.14, EUR: 0.13, INR: 11.3, GBP: 0.11, CAD: 0.19, JPY: 21.4, AUD: 0.21, CNY: 1, CHF: 0.12, BRL: 0.71 },
      CHF: { USD: 1.11, EUR: 1.02, INR: 91.5, GBP: 0.88, CAD: 1.52, JPY: 171.3, AUD: 1.68, CNY: 8.4, CHF: 1, BRL: 5.9 },
      BRL: { USD: 0.19, EUR: 0.18, INR: 14.4, GBP: 0.15, CAD: 0.26, JPY: 30.1, AUD: 0.29, CNY: 1.41, CHF: 0.17, BRL: 1 }
    };

    function convertCurrency() {
      const amount = parseFloat(document.getElementById('amount').value);
      const from = document.getElementById('fromCurrency').value;
      const to = document.getElementById('toCurrency').value;

      if (isNaN(amount) || amount <= 0) {
        document.getElementById('resultText').textContent = "Please enter a valid amount.";
        return;
      }

      const rate = exchangeRates[from][to];
      const converted = (amount * rate).toFixed(2);
      document.getElementById('resultText').textContent = `${amount} ${from} = ${converted} ${to}`;
    }
  </script>

</body>
</html>
