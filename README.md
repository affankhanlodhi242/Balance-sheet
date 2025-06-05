<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Balance Sheet - PTCL Pvt Ltd.</title>
    <style>
        /* Reset and base */
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #f0f4f8 0%, #d9e2ec 100%);
            margin: 0;
            padding: 30px 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            color: #333;
            overflow-x: hidden;
        }

        /* Header styles */
        h1, h2, h3 {
            margin: 0;
            text-align: center;
            color: #2c3e50;
            user-select: none;
        }

        h1 {
            font-size: 2.8rem;
            font-weight: 700;
            margin-bottom: 8px;
            letter-spacing: 1px;
        }

        h2 {
            font-size: 2rem;
            font-weight: 600;
            margin-bottom: 6px;
            color: #34495e;
        }

        h3 {
            font-size: 1.1rem;
            font-weight: 400;
            color: #555;
            margin-bottom: 30px;
            font-style: italic;
        }

        /* Table container */
        table {
            width: 90%;
            max-width: 720px;
            border-collapse: separate;
            border-spacing: 0;
            border-radius: 12px;
            background: #ffffff;
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.12);
            overflow: hidden;
            opacity: 0;
            animation: fadeInScale 0.8s ease-out forwards;
        }

        /* Table cells */
        th, td {
            padding: 18px 22px;
            border: 1px solid #e0e6ed;
            text-align: left;
            transition: background-color 0.3s ease;
            font-size: 1rem;
        }

        /* Header row */
        th {
            background: #f3f6fb;
            color: #34495e;
            font-weight: 700;
            font-size: 1.15rem;
            position: sticky;
            top: 0;
            z-index: 2;
            user-select: none;
        }

        /* Hover effect on rows */
        tr:hover td:not(.total):not(.total-final) {
            background-color: #f8fbfd;
        }

        /* Input styles */
        input[type="number"] {
            width: 100%;
            padding: 8px 10px;
            border: 1.5px solid #cdd5df;
            border-radius: 6px;
            font-size: 1rem;
            font-weight: 500;
            background-color: #fafbfc;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
            -moz-appearance: textfield; /* remove spinner in Firefox */
        }
        input[type="number"]::-webkit-inner-spin-button,
        input[type="number"]::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }
        input[type="number"]:focus {
            outline: none;
            border-color: #4a90e2;
            box-shadow: 0 0 6px rgba(74, 144, 226, 0.4);
            background-color: #ffffff;
        }

        /* Totals styling */
        .total {
            font-weight: 700;
            background: #e0f7fa;
            color: #00796b;
            font-size: 1.15rem;
            user-select: none;
        }

        .total-final {
            background: #c8e6c9;
            color: #2e7d32;
            font-size: 1.25rem;
            font-weight: 800;
            user-select: none;
        }

        /* Rounded corners */
        table tr:first-child th:first-child {
            border-top-left-radius: 12px;
        }
        table tr:first-child th:last-child {
            border-top-right-radius: 12px;
        }
        table tr:last-child td:first-child {
            border-bottom-left-radius: 12px;
        }
        table tr:last-child td:last-child {
            border-bottom-right-radius: 12px;
        }

        /* Animations */
        @keyframes fadeInScale {
            from {
                opacity: 0;
                transform: scale(0.95);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes slideInFromLeft {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        /* Animate each row with delay */
        .animated-row {
            opacity: 0;
            animation: slideInFromLeft 0.5s ease-out forwards;
        }

        .animated-row:nth-child(1) {
            animation-delay: 0.1s;
        }
        .animated-row:nth-child(2) {
            animation-delay: 0.2s;
        }
        .animated-row:nth-child(3) {
            animation-delay: 0.3s;
        }
        .animated-row:nth-child(4) {
            animation-delay: 0.4s;
        }
        .animated-row:nth-child(5) {
            animation-delay: 0.5s;
        }
        .animated-row:nth-child(6) {
            animation-delay: 0.6s;
        }
        .animated-row:nth-child(7) {
            animation-delay: 0.7s;
        }
        .animated-row:nth-child(8) {
            animation-delay: 0.8s;
        }
        .animated-row:nth-child(9) {
            animation-delay: 0.9s;
        }
        .animated-row:nth-child(10) {
            animation-delay: 1.0s;
        }
        .animated-row:nth-child(11) {
            animation-delay: 1.1s;
        }
        .animated-row:nth-child(12) {
            animation-delay: 1.2s;
        }
        .animated-row:nth-child(13) {
            animation-delay: 1.3s;
        }
        .animated-row:nth-child(14) {
            animation-delay: 1.4s;
        }
        .animated-row:nth-child(15) {
            animation-delay: 1.5s;
        }

        /* Responsive tweaks */
        @media (max-width: 600px) {
            th, td {
                padding: 14px 10px;
                font-size: 0.9rem;
            }
            h1 {
                font-size: 2rem;
            }
            h2 {
                font-size: 1.4rem;
            }
            h3 {
                font-size: 1rem;
            }
            table {
                width: 100%;
            }
        }
    </style>
</head>

<body>

    <h1>PTCL Pvt Ltd.</h1>
    <h2>Balance Sheet</h2>
    <h3>For the Period Ending March 31, 2021</h3>

    <table>
        <tr class="animated-row">
            <th colspan="2">Assets</th>
        </tr>
        <tr class="animated-row">
            <td>Cash</td>
            <td><input type="number" value="0" class="asset" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td>Accounts Receivable</td>
            <td><input type="number" value="0" class="asset" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td>Inventory</td>
            <td><input type="number" value="0" class="asset" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td>Property, Plant & Equipment (Net)</td>
            <td><input type="number" value="0" class="asset" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td class="total">Total Assets</td>
            <td class="total" id="totalAssets">0.00</td>
        </tr>

        <tr class="animated-row">
            <th colspan="2">Liabilities</th>
        </tr>
        <tr class="animated-row">
            <td>Accounts Payable</td>
            <td><input type="number" value="0" class="liability" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td>Loan Payable</td>
            <td><input type="number" value="0" class="liability" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td class="total">Total Liabilities</td>
            <td class="total" id="totalLiabilities">0.00</td>
        </tr>

        <tr class="animated-row">
            <th colspan="2">Equity</th>
        </tr>
        <tr class="animated-row">
            <td>Common Stock</td>
            <td><input type="number" value="0" class="equity" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td>Retained Earnings</td>
            <td><input type="number" value="0" class="equity" oninput="calculateTotals()" min="0" step="0.01"></td>
        </tr>
        <tr class="animated-row">
            <td class="total">Total Equity</td>
            <td class="total" id="totalEquity">0.00</td>
        </tr>

        <tr class="animated-row">
            <td class="total-final">Total Liabilities & Equity</td>
            <td class="total-final" id="totalLiabilitiesEquity">0.00</td>
        </tr>
    </table>

    <script>
        // Calculate totals and update the display
        function calculateTotals() {
            // Sum assets
            let assets = [...document.querySelectorAll('input.asset')]
                .reduce((sum, input) => sum + parseFloat(input.value || 0), 0);

            // Sum liabilities
            let liabilities = [...document.querySelectorAll('input.liability')]
                .reduce((sum, input) => sum + parseFloat(input.value || 0), 0);

            // Sum equity
            let equity = [...document.querySelectorAll('input.equity')]
                .reduce((sum, input) => sum + parseFloat(input.value || 0), 0);

            // Update totals in table
            document.getElementById('totalAssets').textContent = assets.toFixed(2);
            document.getElementById('totalLiabilities').textContent = liabilities.toFixed(2);
            document.getElementById('totalEquity').textContent = equity.toFixed(2);

            let totalLiabEquity = liabilities + equity;
            document.getElementById('totalLiabilitiesEquity').textContent = totalLiabEquity.toFixed(2);

            // Optional: Highlight if imbalance (Assets != Liabilities + Equity)
            const totalAssetsCell = document.getElementById('totalAssets');
            const totalLiabEquityCell = document.getElementById('totalLiabilitiesEquity');

            if (Math.abs(assets - totalLiabEquity) > 0.01) {
                totalAssetsCell.style.color = '#d32f2f'; // red
                totalLiabEquityCell.style.color = '#d32f2f';
            } else {
                totalAssetsCell.style.color = '#00796b'; // green
                totalLiabEquityCell.style.color = '#00796b';
            }
        }

        // Initialize totals on page load
        window.addEventListener('load', calculateTotals);
    </script>
</body>

</html>
