<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>SIP vs Car Loan EMI – Smart Comparison Tool</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Compare SIP investment vs car loan EMI. Find out if you should invest or buy now.">
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f8;
      padding: 20px;
      color: #333;
    }
    .calculator {
      max-width: 700px;
      margin: auto;
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      color: #0077cc;
    }
    label {
      margin-top: 15px;
      display: block;
      font-weight: bold;
    }
    input {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 6px;
    }
    button {
      margin-top: 20px;
      padding: 12px;
      background: #0077cc;
      color: white;
      font-weight: bold;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      width: 100%;
    }
    #output {
      margin-top: 25px;
      padding: 15px;
      background: #e6f2ff;
      border-left: 5px solid #0077cc;
      font-size: 16px;
    }
  </style>
</head>
<body>

<div class="calculator">
  <h2>SIP vs Car Loan EMI Comparison</h2>

  <label for="monthlyAmount">Monthly SIP or EMI (₹):</label>
  <input type="number" id="monthlyAmount" placeholder="e.g. 10000">

  <label for="loanYears">Loan Duration (Years):</label>
  <input type="number" id="loanYears" placeholder="e.g. 5">

  <label for="sipRate">SIP Return Rate (% per annum):</label>
  <input type="number" id="sipRate" placeholder="e.g. 12">

  <label for="loanRate">Loan Interest Rate (% per annum):</label>
  <input type="number" id="loanRate" placeholder="e.g. 9">

  <button onclick="calculateComparison()">Compare Now</button>

  <div id="output"></div>
</div>

<script>
  function calculateComparison() {
    const monthlyAmount = parseFloat(document.getElementById("monthlyAmount").value);
    const loanYears = parseFloat(document.getElementById("loanYears").value);
    const sipRate = parseFloat(document.getElementById("sipRate").value);
    const loanRate = parseFloat(document.getElementById("loanRate").value);

    const months = loanYears * 12;
    const r_sip = sipRate / 100 / 12;
    const r_loan = loanRate / 100 / 12;

    // SIP Future Value Calculation
    const sipFutureValue = monthlyAmount * ((Math.pow(1 + r_sip, months) - 1) / r_sip) * (1 + r_sip);

    // Loan Principal Calculation
    const emi = monthlyAmount;
    const principal = emi * ((1 - Math.pow(1 + r_loan, -months)) / r_loan);
    const totalPayment = emi * months;
    const totalInterest = totalPayment - principal;

    // Output
    document.getElementById("output").innerHTML = `
      <strong>💰 SIP Investment Result:</strong><br>
      Future Value after ${loanYears} years: <b>₹${sipFutureValue.toFixed(0)}</b><br><br>
      <strong>🚗 Car Loan Result:</strong><br>
      You can borrow up to: <b>₹${principal.toFixed(0)}</b><br>
      Total Interest Payable: <b>₹${totalInterest.toFixed(0)}</b><br><br>
      🧠 <i>Conclusion:</i> SIP gives you returns, loan costs you interest. Choose smart!
    `;
  }
</script>

</body>
</html>
