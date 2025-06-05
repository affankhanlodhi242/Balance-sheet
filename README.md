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
            background: #1a1a2e; /* Dark background */
            display: flex;
            flex-direction: column;
            align-items: center; /* Center horizontally */
            justify-content: center; /* Center vertically */
            min-height: 100vh;
            color: #e0e0e0; /* Light text color */
        }
        h1, h2 {
            text-align: center;
            color: #e0e0e0; /* Light text for headings */
            margin-bottom: 10px;
        }
        h1 {
            font-size: 2.5em;
            font-weight: 600;
        }
        h2 {
            font-size: 1.5em;
            font-weight: 400;
            color: #b0b0b0; /* Slightly darker light text */
        }
        table {
            width: 80%; /* Increased width for better readability */
            max-width: 700px; /* Max width to prevent stretching on large screens */
            margin: 30px auto; /* Center table */
            border-collapse: separate;
            border-spacing: 0;
            background: #2a2a4a; /* Darker background for table */
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3); /* More pronounced shadow */
            overflow: hidden;
        }
        th, td {
            border: 1px solid #3a3a5a; /* Darker border */
            padding: 15px 20px;
            text-align: left;
            transition: background-color 0.3s ease;
        }
        th {
            background: #3a3a5a; /* Darker header background */
            color: #f0f0f0;
            font-weight: 600;
            font-size: 1.1em;
            position: sticky;
            top: 0;
            z-index: 1;
        }
        tr:hover td {
            background-color: #353555; /* Subtle hover effect */
        }
        input {
            width: calc(100% - 2px);
            padding: 8px;
            border: 1px solid #5a5a7a; /* Soft border for inputs */
            background: #3a3a5a; /* Darker input background */
            color: #f0f0f0; /* Light text in inputs */
            font-size: 1em;
            border-radius: 6px;
            box-sizing: border-box;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        input:focus {
            outline: none;
            border-color: #8a2be2; /* Purple highlight on focus */
            box-shadow: 0 0 0 3px rgba(138, 43, 226, 0.3);
        }
       .total {
            font-weight: bold;
            background: #4a2a6a; /* Dark purple for totals */
            color: #c080ff; /* Lighter purple text for contrast */
            font-size: 1.1em;
        }
       .total-final {
            background: #2a6a4a; /* Dark green for final balance */
            color: #80ffc0; /* Lighter green text for contrast */
            font-size: 1.2em;
        }
        /* Specific rounded corners for table headers/footers */
        table tr:first-child th:first-child { border-top-left-radius: 12px; }
        table tr:first-child th:last-child { border-top-right-radius: 12px; }
        table tr:last-child td:first-child { border-bottom-left-radius: 12px; }
        table tr:last-child td:last-child { border-bottom-right-radius: 12px; }
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
        <tr><td>Property, Plant & Equipment (Net)</td><td><input type="number" value="0" class="asset" oninput="calculateTotals()"></td></tr>
        <tr><td class="total">Total Assets</td><td class="total" id="totalAssets">0.00</td></tr>

        <tr><th colspan="2">Liabilities</th></tr>
        <tr><td>Accounts Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr><td>Loan Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr><td>Salaries Payable</td><td><input type="number" value="0" class="liability" oninput="calculateTotals()"></td></tr>
        <tr><td class="total">Total Liabilities</td><td class="total" id="totalLiabilities">0.00</td></tr>

        <tr><th colspan="2">Equity</th></tr>
        <tr><td>Owner's Capital</td><td><input type="number" value="0" class="equity" oninput="calculateTotals()"></td></tr>
        <tr><td>Retained Earnings</td><td><input type="number" value="0" class="equity" oninput="calculateTotals()"></td></tr>
        <tr><td class="total">Total Equity</td><td class="total" id="totalEquity">0.00</td></tr>

        <tr><td class="total total-final">Liabilities + Equity</td><td class="total total-final" id="liabEquity">0.00</td></tr>
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
