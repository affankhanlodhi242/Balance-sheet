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
        header {
            text-align: center;
            margin-bottom: 20px;
        }
        h1, h2, h3 { /* Apply centering to h1, h2, and h3 */
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
        h3 { /* New style for the date heading */
            font-size: 1.2em;
            font-weight: 400;
            color: #555;
            margin-top: -5px; /* Adjust spacing */
        }
        main {
            width: 100%;
            max-width: 800px; /* Increased max-width for overall content */
            display: flex;
            flex-direction: column;
            align-items: center;
        }
      .table-container {
            width: 100%;
            overflow-x: auto; /* Allows horizontal scroll on small screens */
            margin-bottom: 20px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            background: #ffffff;
            opacity: 0; /* Start hidden for animation */
            animation: fadeInScale 0.8s ease-out forwards; /* Table animation */
        }
        table {
            width: 100%;
            border-collapse: separate; /* Use separate for rounded corners on cells */
            border-spacing: 0;
            background: #ffffff;
            border-radius: 12px; /* More rounded corners */
            overflow: hidden; /* Ensures rounded corners apply to content */
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
        input[type="number"] {
            width: calc(100% - 2px); /* Adjust for border */
            padding: 8px;
            border: 1px solid #cdd5df; /* Soft border for inputs */
            background: #fdfefe;
            font-size: 1em;
            border-radius: 6px; /* Rounded input fields */
            box-sizing: border-box; /* Include padding and border in width */
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }
        input[type="number"]:focus {
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
        /* Keeping original animation delays for initial rows */
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

      .controls {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
            justify-content: center;
            width: 100%;
        }
      .controls button {
            padding: 10px 15px;
            border: none;
            border-radius: 8px;
            background-color: #4a90e2;
            color: white;
            font-size: 1em;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
      .controls button:hover {
            background-color: #357ABD;
            transform: translateY(-2px);
        }
      .controls button:active {
            transform: translateY(0);
        }

      .delete-row-btn {
            background-color: #e74c3c;
            padding: 5px 10px;
            border-radius: 5px;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 0.8em;
            transition: background-color 0.3s ease;
        }
      .delete-row-btn:hover {
            background-color: #c0392b;
        }

      .financial-ratios {
            background: #ffffff;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin-top: 20px;
            width: 100%;
            max-width: 700px;
        }
      .financial-ratios h3 {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.8em;
        }
      .financial-ratios p {
            margin-bottom: 8px;
            font-size: 1.1em;
            color: #555;
        }
      .financial-ratios strong {
            color: #34495e;
        }
      .financial-ratios span {
            font-weight: bold;
            color: #00796b;
        }
        footer {
            margin-top: 40px;
            text-align: center;
            color: #777;
            font-size: 0.9em;
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            body {
                padding: 10px;
            }
            h1 {
                font-size: 2em;
            }
            h2 {
                font-size: 1.2em;
            }
            h3 {
                font-size: 1em;
            }
          .controls {
                flex-direction: column;
                align-items: stretch;
            }
          .controls button {
                width: 100%;
            }
          .financial-ratios {
                padding: 15px;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>PTCL Pvt Ltd.</h1>
        <h2>Balance Sheet</h2>
        <h3>For the Period Ending March 31, 2021</h3>
    </header>

    <main>
        <section class="balance-sheet-section">
            <div class="table-container">
                <table id="balanceSheetTable">
                    <thead>
                        <tr class="animated-row">
                            <th colspan="2">Assets</th>
                            <th></th> </tr>
                    </thead>
                    <tbody id="assetsBody">
                        <tr class="animated-row">
                            <td>Cash</td>
                            <td><input type="number" value="0" class="asset"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Accounts Receivable</td>
                            <td><input type="number" value="0" class="asset"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Inventory</td>
                            <td><input type="number" value="0" class="asset"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Property, Plant & Equipment (Net)</td>
                            <td><input type="number" value="0" class="asset"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                    </tbody>
                    <tfoot>
                        <tr class="animated-row">
                            <td class="total">Total Assets</td>
                            <td class="total" id="totalAssets">0.00</td>
                            <td></td>
                        </tr>
                    </tfoot>

                    <thead>
                        <tr class="animated-row">
                            <th colspan="2">Liabilities</th>
                            <th></th>
                        </tr>
                    </thead>
                    <tbody id="liabilitiesBody">
                        <tr class="animated-row">
                            <td>Accounts Payable</td>
                            <td><input type="number" value="0" class="liability"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Loan Payable</td>
                            <td><input type="number" value="0" class="liability"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Salaries Payable</td>
                            <td><input type="number" value="0" class="liability"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                    </tbody>
                    <tfoot>
                        <tr class="animated-row">
                            <td class="total">Total Liabilities</td>
                            <td class="total" id="totalLiabilities">0.00</td>
                            <td></td>
                        </tr>
                    </tfoot>

                    <thead>
                        <tr class="animated-row">
                            <th colspan="2">Equity</th>
                            <th></th>
                        </tr>
                    </thead>
                    <tbody id="equityBody">
                        <tr class="animated-row">
                            <td>Owner's Capital</td>
                            <td><input type="number" value="0" class="equity"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                        <tr class="animated-row">
                            <td>Retained Earnings</td>
                            <td><input type="number" value="0" class="equity"></td>
                            <td><button class="delete-row-btn">Delete</button></td>
                        </tr>
                    </tbody>
                    <tfoot>
                        <tr class="animated-row">
                            <td class="total">Total Equity</td>
                            <td class="total" id="totalEquity">0.00</td>
                            <td></td>
                        </tr>
                        <tr class="animated-row">
                            <td class="total total-final">Liabilities + Equity</td>
                            <td class="total total-final" id="liabEquity">0.00</td>
                            <td></td>
                        </tr>
                    </tfoot>
                </table>
            </div>

            <div class="controls">
                <button id="addAssetRowBtn">Add Asset Row</button>
                <button id="addLiabilityRowBtn">Add Liability Row</button>
                <button id="addEquityRowBtn">Add Equity Row</button>
                <button id="saveDataBtn">Save Data</button>
                <button id="loadDataBtn">Load Data</button>
                <button id="exportCsvBtn">Export to CSV</button>
                <button id="exportPdfBtn">Export to PDF</button>
            </div>
        </section>

        <section class="financial-ratios">
            <h3>Key Financial Ratios</h3>
            <div id="ratiosDisplay">
                <p><strong>Debt-to-Equity Ratio:</strong> <span id="debtToEquity">0.00</span></p>
                <p><strong>Debt Ratio:</strong> <span id="debtRatio">0.00</span></p>
                <p><strong>Current Ratio:</strong> <span id="currentRatio">0.00</span></p>
                <p><strong>Quick Ratio:</strong> <span id="quickRatio">0.00</span></p>
            </div>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Affan Enterprises. All rights reserved.</p>
    </footer>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js" integrity="sha512-GsLlZN/3F2ErC5ifS5QtgpiJtWd43JWSuIgh7mbzZ8zBps+dvLusV+eNQATqgA/HdeKFVgA5v3S/cIrLF7QnIg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    <script>
        // Helper function to sum values from inputs with a given selector
        const sumValues = (selector) => {
            const fields = document.querySelectorAll(selector);
            let total = 0;
            fields.forEach(field => {
                // Use parseFloat and default to 0 if NaN
                total += parseFloat(field.value) |
| 0;
            });
            return total.toFixed(2);
        };

        // Calculate and display all totals
        const calculateTotals = () => {
            const assetTotal = sumValues('.asset');
            const liabilityTotal = sumValues('.liability');
            const equityTotal = sumValues('.equity');
            const totalLE = parseFloat(liabilityTotal) + parseFloat(equityTotal);

            document.getElementById('totalAssets').textContent = assetTotal;
            document.getElementById('totalLiabilities').textContent = liabilityTotal;
            document.getElementById('totalEquity').textContent = equityTotal;
            document.getElementById('liabEquity').textContent = totalLE.toFixed(2);

            calculateRatios(); // Recalculate ratios whenever totals change
        };

        // Calculate and display key financial ratios
        const calculateRatios = () => {
            const totalAssets = parseFloat(document.getElementById('totalAssets').textContent);
            const totalLiabilities = parseFloat(document.getElementById('totalLiabilities').textContent);
            const totalEquity = parseFloat(document.getElementById('totalEquity').textContent);

            // Debt-to-Equity Ratio: Total Liabilities / Total Shareholder Equity [1, 2]
            const debtToEquity = totalEquity!== 0? (totalLiabilities / totalEquity).toFixed(2) : 'N/A';
            document.getElementById('debtToEquity').textContent = debtToEquity;

            // Debt Ratio: Total Liabilities / Total Assets [1, 2]
            const debtRatio = totalAssets!== 0? (totalLiabilities / totalAssets).toFixed(2) : 'N/A';
            document.getElementById('debtRatio').textContent = debtRatio;

            // Current Ratio: Current Assets / Current Liabilities [1, 2]
            // For simplicity, assuming all assets are current assets and all liabilities are current liabilities in this basic model.
            const currentAssets = totalAssets; // In a real scenario, this would be a sum of specific current asset lines
            const currentLiabilities = totalLiabilities; // In a real scenario, this would be a sum of specific current liability lines
            const currentRatio = currentLiabilities!== 0? (currentAssets / currentLiabilities).toFixed(2) : 'N/A';
            document.getElementById('currentRatio').textContent = currentRatio;

            // Quick Ratio (Acid-Test Ratio): (Current Assets – Inventory) / Current Liabilities [1, 2]
            const inventoryValue = parseFloat(document.querySelector('.asset[data-name="Inventory"]')?.value) |
| 0; // Assuming Inventory has a data-name attribute
            const quickRatio = currentLiabilities!== 0? ((currentAssets - inventoryValue) / currentLiabilities).toFixed(2) : 'N/A';
            document.getElementById('quickRatio').textContent = quickRatio;
        };

        // Function to add a new row to a specific section
        const addRow = (type) => {
            const tbodyId = `${type}sBody`; // e.g., 'assetsBody', 'liabilitiesBody'
            const tbody = document.getElementById(tbodyId);
            if (!tbody) return;

            const newRow = document.createElement('tr');
            newRow.classList.add('animated-row'); // Add animation class

            const nameCell = document.createElement('td');
            const nameInput = document.createElement('input');
            nameInput.type = 'text';
            nameInput.placeholder = `Enter ${type} item name`;
            nameCell.appendChild(nameInput);

            const valueCell = document.createElement('td');
            const valueInput = document.createElement('input');
            valueInput.type = 'number';
            valueInput.value = '0';
            valueInput.classList.add(type); // Add asset/liability/equity class
            valueCell.appendChild(valueInput);

            const deleteCell = document.createElement('td');
            const deleteButton = document.createElement('button');
            deleteButton.classList.add('delete-row-btn');
            deleteButton.textContent = 'Delete';
            deleteCell.appendChild(deleteButton);

            newRow.appendChild(nameCell);
            newRow.appendChild(valueCell);
            newRow.appendChild(deleteCell);
            tbody.appendChild(newRow);

            // Trigger animation for the new row
            setTimeout(() => newRow.style.opacity = 1, 10);

            calculateTotals(); // Recalculate totals after adding a row
        };

        // Function to remove a row
        const removeRow = (buttonElement) => {
            const row = buttonElement.closest('tr');
            if (row) {
                row.remove();
                calculateTotals(); // Recalculate totals after removing a row
            }
        };

        // Save data to localStorage [3, 4, 5, 6, 7, 8]
        const saveData = () => {
            const data = {
                assets:,
                liabilities:,
                equity:
            };

            document.querySelectorAll('#assetsBody tr').forEach(row => {
                const name = row.querySelector('td:first-child input')?.value |
| row.querySelector('td:first-child')?.textContent;
                const value = row.querySelector('.asset')?.value;
                if (name && value!== undefined) {
                    data.assets.push({ name: name.trim(), value: parseFloat(value) |
| 0 });
                }
            });

            document.querySelectorAll('#liabilitiesBody tr').forEach(row => {
                const name = row.querySelector('td:first-child input')?.value |
| row.querySelector('td:first-child')?.textContent;
                const value = row.querySelector('.liability')?.value;
                if (name && value!== undefined) {
                    data.liabilities.push({ name: name.trim(), value: parseFloat(value) |
| 0 });
                }
            });

            document.querySelectorAll('#equityBody tr').forEach(row => {
                const name = row.querySelector('td:first-child input')?.value |
| row.querySelector('td:first-child')?.textContent;
                const value = row.querySelector('.equity')?.value;
                if (name && value!== undefined) {
                    data.equity.push({ name: name.trim(), value: parseFloat(value) |
| 0 });
                }
            });

            localStorage.setItem('affanBalanceSheetData', JSON.stringify(data));
            alert('Balance Sheet data saved!');
        };

        // Load data from localStorage [3, 4, 5, 6, 7, 8]
        const loadData = () => {
            const storedData = localStorage.getItem('affanBalanceSheetData');
            if (storedData) {
                const data = JSON.parse(storedData);

                // Clear existing dynamic rows before loading
                document.querySelectorAll('#assetsBody tr:not(.initial-row)').forEach(row => row.remove());
                document.querySelectorAll('#liabilitiesBody tr:not(.initial-row)').forEach(row => row.remove());
                document.querySelectorAll('#equityBody tr:not(.initial-row)').forEach(row => row.remove());

                // Populate initial rows and add new ones from loaded data
                const populateSection = (sectionId, items, className) => {
                    const tbody = document.getElementById(sectionId);
                    const initialRows = tbody.querySelectorAll('tr');
                    
                    items.forEach((item, index) => {
                        let row;
                        let nameInput;
                        let valueInput;

                        if (index < initialRows.length) {
                            // Update existing initial row
                            row = initialRows[index];
                            nameInput = row.querySelector('td:first-child input') |
| row.querySelector('td:first-child');
                            valueInput = row.querySelector(`.${className}`);
                            if (nameInput.tagName === 'INPUT') {
                                nameInput.value = item.name;
                            } else {
                                nameInput.textContent = item.name;
                            }
                            if (valueInput) valueInput.value = item.value;
                        } else {
                            // Add new row if it's beyond initial static rows
                            row = document.createElement('tr');
                            row.classList.add('animated-row');

                            nameInput = document.createElement('input');
                            nameInput.type = 'text';
                            nameInput.value = item.name;
                            const nameCell = document.createElement('td');
                            nameCell.appendChild(nameInput);

                            valueInput = document.createElement('input');
                            valueInput.type = 'number';
                            valueInput.value = item.value;
                            valueInput.classList.add(className);
                            const valueCell = document.createElement('td');
                            valueCell.appendChild(valueInput);

                            const deleteCell = document.createElement('td');
                            const deleteButton = document.createElement('button');
                            deleteButton.classList.add('delete-row-btn');
                            deleteButton.textContent = 'Delete';
                            deleteCell.appendChild(deleteButton);

                            row.appendChild(nameCell);
                            row.appendChild(valueCell);
                            row.appendChild(deleteCell);
                            tbody.appendChild(row);
                        }
                    });
                };

                populateSection('assetsBody', data.assets, 'asset');
                populateSection('liabilitiesBody', data.liabilities, 'liability');
                populateSection('equityBody', data.equity, 'equity');

                calculateTotals();
                alert('Balance Sheet data loaded!');
            } else {
                alert('No saved data found.');
            }
        };

        // Export data to CSV [8]
        const exportToCSV = () => {
            const table = document.getElementById('balanceSheetTable');
            let csv =;

            // Get headers
            table.querySelectorAll('thead th').forEach(header => {
                if (header.textContent.trim()!== '') { // Exclude empty delete column header
                    csv.push(header.textContent.trim());
                }
            });
            csv = [csv.join(',')]; // Join headers with comma

            // Get data rows
            table.querySelectorAll('tbody tr').forEach(row => {
                const rowData =;
                const nameCell = row.querySelector('td:first-child');
                const valueInput = row.querySelector('input[type="number"]');

                const name = nameCell.querySelector('input')? nameCell.querySelector('input').value : nameCell.textContent.trim();
                const value = valueInput? valueInput.value : '';

                rowData.push(`"${name}"`); // Enclose name in quotes to handle commas
                rowData.push(value);
                csv.push(rowData.join(','));
            });

            // Get total rows
            table.querySelectorAll('tfoot tr').forEach(row => {
                const rowData =;
                const label = row.querySelector('td:first-child').textContent.trim();
                const total = row.querySelector('td:nth-child(2)').textContent.trim();
                rowData.push(`"${label}"`);
                rowData.push(total);
                csv.push(rowData.join(','));
            });

            const csvString = csv.join('\n');
            const blob = new Blob(, { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'Affan_Balance_Sheet.csv';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            alert('Balance Sheet exported to CSV!');
        };

        // Export data to PDF [9, 10]
        const exportToPDF = () => {
            const element = document.querySelector('.balance-sheet-section'); // Target the section containing the table and controls
            const opt = {
                margin: 1,
                filename: 'Affan_Balance_Sheet.pdf',
                image: { type: 'jpeg', quality: 0.98 },
                html2canvas: { scale: 2 },
                jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
            };

            html2pdf().set(opt).from(element).save();
            alert('Balance Sheet exported to PDF!');
        };

        // Event Listeners
        document.addEventListener('DOMContentLoaded', () => {
            // Event delegation for input changes to recalculate totals
            document.getElementById('balanceSheetTable').addEventListener('input', (event) => {
                if (event.target.matches('.asset,.liability,.equity')) {
                    calculateTotals();
                }
            });

            // Event delegation for delete buttons
            document.getElementById('balanceSheetTable').addEventListener('click', (event) => {
                if (event.target.classList.contains('delete-row-btn')) {
                    removeRow(event.target);
                }
            });

            document.getElementById('addAssetRowBtn').addEventListener('click', () => addRow('asset'));
            document.getElementById('addLiabilityRowBtn').addEventListener('click', () => addRow('liability'));
            document.getElementById('addEquityRowBtn').addEventListener('click', () => addRow('equity'));
            document.getElementById('saveDataBtn').addEventListener('click', saveData);
            document.getElementById('loadDataBtn').addEventListener('click', loadData);
            document.getElementById('exportCsvBtn').addEventListener('click', exportToCSV);
            document.getElementById('exportPdfBtn').addEventListener('click', exportToPDF);

            // Initial calculation and load data on page load
            calculateTotals();
            loadData();

            // Add a class to initial rows for easier identification during loadData
            document.querySelectorAll('#assetsBody tr, #liabilitiesBody tr, #equityBody tr').forEach(row => {
                row.classList.add('initial-row');
            });

            // Add data-name to initial rows for ratio calculation
            document.querySelector('#assetsBody tr:nth-child(3) td:first-child').setAttribute('data-name', 'Inventory');
        });
    </script>
</body>
</html>
