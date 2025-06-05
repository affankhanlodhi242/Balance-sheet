# Balance-sheet
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Balance Sheet - Affan Enterprises</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f4f4f9;
    }
    h1, h2 {
      text-align: center;
    }
    table {
      width: 60%;
      margin: 20px auto;
      border-collapse: collapse;
      background: #fff;
      box-shadow: 0 0 10px #ccc;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 10px;
      text-align: left;
    }
    th {
      background: #f0f0f0;
    }
    input {
      width: 100%;
      border: none;
      background: transparent;
      font-size: 1em;
    }
    .total {
      font-weight: bold;
      background: #e8f8e8;
    }
  </style>
</head>
<body>

  <h1>Balance Sheet</h1>
  <h2>Student: Affan | Business: Affan Enterprises</h2>

  <table>
    <tr><th colspan="2">Assets</th></tr>
    <tr><td>Cash</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
    <tr><td>Accounts Receivable</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
    <tr><td>Inventory</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
    <tr><td class="total">Total Assets</td><td class="total" id="totalAssets">0</td></tr>

    <tr><th colspan="2">Liabilities</th></tr>
    <tr><td>Accounts Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
    <tr><td>Loan Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
    <tr><td class="total">Total Liabilities</td><td class="total" id="totalLiabilities">0</td></tr>

    <tr><th colspan="2">Equity</th></tr>
    <tr><td>Owner's Capital</td><td><input type="number" value="0" class="equity" oninput="calculateTotals()"></td></tr>
    <tr><td class="total">Total Equity</td><td class="total" id="totalEquity">0</td></tr>

    <tr><td class="total">Liabilities + Equity</td><td class="total" id="liabEquity">0</td></tr>
  </table>

  <script>
    function calculateTotals() {
      let assetTotal = sumValues('.asset');
      let liabilityTotal = sumValues('.liability');
      let equityTotal = sumValues('.equity');
      let totalLE = liabilityTotal + equityTotal;

      document.getElementById('totalAssets').textContent = assetTotal;
      document.getElementById('totalLiabilities').textContent = liabilityTotal;
      document.getElementById('totalEquity').textContent = equityTotal;
      document.getElementById('liabEquity').textContent = totalLE;
    }

    function sumValues(selector) {
      const fields = document.querySelectorAll(selector);
      let total = 0;
      fields.forEach(field => {
        total += parseFloat(field.value) || 0;
      });
      return total.toFixed(2);
    }

    window.onload = calculateTotals;
  </script>
</body>
</html>
