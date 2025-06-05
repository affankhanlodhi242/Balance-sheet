<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Balance Sheet - Affan Enterprises</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            background: linear-gradient(135deg, #f0f4f8 0%, #d9e2ec 100%); /* Soft gradient background */
            display: flex;
            flex-direction: column;
            align-items: center; /* Center horizontally */
            justify-content: center; /* Center vertically */
            min-height: 100vh;
            color: #333;
            overflow-x: hidden; /* Prevent horizontal scroll on animations */
        }
        h1, h2 {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 10px;
        }
        h1 {
            font-size: 2.5em;
            font-weight: 600;
        }
        h2 {
            font-size: 1.5em;
            font-weight: 400;
            color: #555;
        }
        table {
            width: 80%; /* Increased width for better readability */
            max-width: 700px; /* Max width to prevent stretching on large screens */
            margin: 30px auto; /* Center table */
            border-collapse: separate; /* Use separate for rounded corners on cells */
            border-spacing: 0;
            background: #ffffff;
            border-radius: 12px; /* More rounded corners */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); /* Softer, larger shadow */
            overflow: hidden; /* Ensures rounded corners apply to content */
            opacity: 0; /* Start hidden for animation */
            animation: fadeInScale 0.8s ease-out forwards; /* Table animation */
        }
        th, td {
            border: 1px solid #e0e6ed; /* Lighter border */
            padding: 15px 20px; /* More padding */
            text-align: left;
            transition: background-color 0.3s ease;
        }
        th {
            background: #e9eff6; /* Lighter header background */
            color: #34495e;
            font-weight: 600;
            font-size: 1.1em;
            position: sticky;
            top: 0;
            z-index: 1;
        }
        tr:hover td {
            background-color: #f8fbfd; /* Subtle hover effect */
        }
        input {
            width: calc(100% - 2px); /* Adjust for border */
            padding: 8px;
            border: 1px solid #cdd5df; /* Soft border for inputs */
            background: #fdfefe;
            font-size: 1em;
            border-radius: 6px; /* Rounded input fields */
            box-sizing: border-box; /* Include padding and border in width */
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        input:focus {
            outline: none;
            border-color: #4a90e2; /* Highlight on focus */
            box-shadow: 0 0 0 3px rgba(74, 144, 226, 0.2);
        }
      .total {
            font-weight: bold;
            background: #e0f7fa; /* Light blue for totals */
            color: #00796b; /* Darker text for contrast */
            font-size: 1.1em;
        }
      .total-final {
            background: #c8e6c9; /* Light green for final balance */
            color: #2e7d32;
            font-size: 1.2em;
        }
        /* Specific rounded corners for table headers/footers */
        table tr:first-child th:first-child { border-top-left-radius: 12px; }
        table tr:first-child th:last-child { border-top-right-radius: 12px; }
        table tr:last-child td:first-child { border-bottom-left-radius: 12px; }
        table tr:last-child td:last-child { border-bottom-right-radius: 12px; }

        /* Animations */
        @keyframes fadeInScale {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        @keyframes slideInFromLeft {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
        }

       .animated-row {
            opacity: 0;
            animation: slideInFromLeft 0.5s ease-out forwards;
        }
       .animated-row:nth-child(1) { animation-delay: 0.1s; }
       .animated-row:nth-child(2) { animation-delay: 0.2s; }
       .animated-row:nth-child(3) { animation-delay: 0.3s; }
       .animated-row:nth-child(4) { animation-delay: 0.4s; }
       .animated-row:nth-child(5) { animation-delay: 0.5s; }
       .animated-row:nth-child(6) { animation-delay: 0.6s; }
       .animated-row:nth-child(7) { animation-delay: 0.7s; }
       .animated-row:nth-child(8) { animation-delay: 0.8s; }
       .animated-row:nth-child(9) { animation-delay: 0.9s; }
       .animated-row:nth-child(10) { animation-delay: 1.0s; }
       .animated-row:nth-child(11) { animation-delay: 1.1s; }
       .animated-row:nth-child(12) { animation-delay: 1.2s; }
       .animated-row:nth-child(13) { animation-delay: 1.3s; }
       .animated-row:nth-child(14) { animation-delay: 1.4s; }
       .animated-row:nth-child(15) { animation-delay: 1.5s; }
    </style>
</head>
<body>

    <h1>Balance Sheet</h1>
    <h2>For the Period Ending May 31, 2025 | Affan Enterprises</h2>

    <table>
        <tr class="animated-row"><th colspan="2">Assets</th></tr>
        <tr class="animated-row"><td>Cash</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Accounts Receivable</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Inventory</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Property, Plant & Equipment (Net)</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td class="total">Total Assets</td><td class="total" id="totalAssets">0.00</td></tr>

        <tr class="animated-row"><th colspan="2">Liabilities</th></tr>
        <tr class="animated-row"><td>Accounts Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Loan Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Salaries Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td class="total">Total Liabilities</td><td class="total" id="totalLiabilities">0.00</td></tr>

        <tr class="animated-row"><th colspan="2">Equity</th></tr>
        <tr class="animated-row"><td>Owner's Capital</td><td><input type="number" value="0" class="equity" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td>Retained Earnings</td><td><input type="number" value="0" class="equity" oninput="calculateTotals()"></td></tr>
        <tr class="animated-row"><td class="total">Total Equity</td><td class="total" id="totalEquity">0.00</td></tr>

        <tr class="animated-row"><td class="total total-final">Liabilities + Equity</td><td class="total total-final" id="liabEquity">0.00</td></tr>
    </table>

    <script>
        function calculateTotals() {
            let assetTotal = sumValues('.asset');
            let liabilityTotal = sumValues('.liability');
            let equityTotal = sumValues('.equity');
            let totalLE = parseFloat(liabilityTotal) + parseFloat(equityTotal);

            document.getElementById('totalAssets').textContent = parseFloat(assetTotal).toFixed(2);
            document.getElementById('totalLiabilities').textContent = parseFloat(liabilityTotal).toFixed(2);
            document.getElementById('totalEquity').textContent = parseFloat(equityTotal).toFixed(2);
            document.getElementById('liabEquity').textContent = totalLE.toFixed(2);
        }

        function sumValues(selector) {
            const fields = document.querySelectorAll(selector);
            let total = 0;
            fields.forEach(field => {
                total += parseFloat(field.value) |
| 0;
            });
            return total.toFixed(2);
        }

        // Initialize totals on page load
        window.onload = calculateTotals;
    </script>
</body>
</html>
