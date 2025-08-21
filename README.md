<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ProBooks - ADTEMPCO Coopmart</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css" rel="stylesheet">
    <style>
        body {
            background: linear-gradient(135deg, #4a90e2, #50c9c3);
            font-family: 'Poppins', sans-serif;
            color: #2c3e50;
        }
        .container {
            max-width: 700px;
            padding: 20px;
            margin: 30px auto;
        }
        .header {
            background: #2c3e50;
            color: #ecf0f1;
            padding: 20px;
            text-align: center;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            margin-bottom: 30px;
        }
        .header h1 {
            font-size: 24px;
            margin: 0;
            font-weight: 600;
        }
        .header p {
            font-size: 14px;
            margin: 5px 0 0;
            opacity: 0.8;
        }
        .view { display: none; }
        .view.active { display: block; }
        .nav-tabs {
            border-bottom: 2px solid #3498db;
        }
        .nav-tabs .nav-link {
            border-radius: 8px 8px 0 0;
            font-size: 16px;
            color: #2c3e50;
            padding: 12px 20px;
            transition: all 0.3s;
        }
        .nav-tabs .nav-link.active {
            background: #3498db;
            color: #fff;
            border-color: #3498db;
        }
        .nav-tabs .nav-link:hover {
            background: #2980b9;
            color: #fff;
        }
        .card {
            border: none;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.15);
            margin-bottom: 20px;
            background: #fff;
            transition: transform 0.2s;
        }
        .card:hover {
            transform: translateY(-5px);
        }
        .btn {
            border-radius: 8px;
            padding: 10px;
            font-size: 16px;
            font-weight: 500;
            transition: all 0.3s;
        }
        .btn-primary {
            background: #3498db;
            border: none;
        }
        .btn-primary:hover {
            background: #2980b9;
        }
        .btn-success {
            background: #27ae60;
            border: none;
        }
        .btn-success:hover {
            background: #219653;
        }
        .btn-danger {
            background: #e74c3c;
            border: none;
        }
        .btn-danger:hover {
            background: #c0392b;
        }
        .form-control, .form-select {
            border-radius: 8px;
            font-size: 16px;
            border: 1px solid #3498db;
        }
        .form-label {
            font-weight: 500;
            color: #2c3e50;
        }
        .alert {
            border-radius: 8px;
            margin-top: 10px;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .alert-success { background: #dff0d8; color: #27ae60; }
        .alert-danger { background: #f2dede; color: #e74c3c; }
        h2, h3 {
            color: #3498db;
            font-size: 20px;
            font-weight: 600;
        }
        .table {
            font-size: 14px;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        .table th, .table td {
            padding: 12px;
            vertical-align: middle;
        }
        .table th {
            background: #3498db;
            color: #fff;
        }
        .icon-btn {
            font-size: 18px;
            margin-right: 8px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="bi bi-calculator-fill icon-btn"></i> ProBooks</h1>
            <p>ADTEMPCO COOPMART MANABO<br>SAN JUAN NORTE, MANABO, ABRA 2810</p>
        </div>

        <!-- Login View -->
        <div id="login-view" class="view active">
            <div class="card">
                <div class="card-body">
                    <h2 class="text-center mb-4"><i class="bi bi-box-arrow-in-right icon-btn"></i> Login</h2>
                    <div id="login-message"></div>
                    <form id="login-form">
                        <div class="mb-3">
                            <label class="form-label"><i class="bi bi-person icon-btn"></i> Username</label>
                            <input type="text" id="login-username" class="form-control" required>
                        </div>
                        <div class="mb-3">
                            <label class="form-label"><i class="bi bi-lock icon-btn"></i> Password</label>
                            <input type="password" id="login-password" class="form-control" required>
                        </div>
                        <button type="submit" class="btn btn-primary w-100"><i class="bi bi-box-arrow-in-right icon-btn"></i> Login</button>
                    </form>
                    <p class="text-center mt-3">
                        <a href="#" onclick="showView('register')"><i class="bi bi-person-plus icon-btn"></i> Create Account</a> | 
                        <a href="#" onclick="if (Object.keys(users).length > 0) { showView('app'); showTab('debug'); } else { showMessage('login-message', 'No accounts exist. Please register first.', true); }"><i class="bi bi-bug icon-btn"></i> Debug</a> | 
                        <a href="#" onclick="resetData()"><i class="bi bi-arrow-repeat icon-btn"></i> Reset</a>
                    </p>
                </div>
            </div>
        </div>

        <!-- Register View -->
        <div id="register-view" class="view">
            <div class="card">
                <div class="card-body">
                    <h2 class="text-center mb-4"><i class="bi bi-person-plus-fill icon-btn"></i> Register</h2>
                    <div id="register-message"></div>
                    <form id="register-form">
                        <div class="mb-3">
                            <label class="form-label"><i class="bi bi-person icon-btn"></i> Username</label>
                            <input type="text" id="register-username" class="form-control" required>
                        </div>
                        <div class="mb-3">
                            <label class="form-label"><i class="bi bi-lock icon-btn"></i> Password</label>
                            <input type="password" id="register-password" class="form-control" required>
                        </div>
                        <button type="submit" class="btn btn-primary w-100"><i class="bi bi-person-plus-fill icon-btn"></i> Register</button>
                    </form>
                    <p class="text-center mt-3"><a href="#" onclick="showView('login')"><i class="bi bi-arrow-left icon-btn"></i> Back to Login</a></p>
                </div>
            </div>
        </div>

        <!-- Main App View -->
        <div id="app-view" class="view">
            <ul class="nav nav-tabs mb-4">
                <li class="nav-item">
                    <a class="nav-link active" href="#" onclick="showTab('dashboard')"><i class="bi bi-house-door icon-btn"></i> Dashboard</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" onclick="showTab('accounts')"><i class="bi bi-wallet2 icon-btn"></i> Accounts</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" onclick="showTab('transactions')"><i class="bi bi-receipt icon-btn"></i> Transactions</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" onclick="showTab('reports')"><i class="bi bi-file-earmark-text icon-btn"></i> Reports</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" onclick="showTab('debug')"><i class="bi bi-bug icon-btn"></i> Debug</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" onclick="logout()"><i class="bi bi-box-arrow-right icon-btn"></i> Logout</a>
                </li>
            </ul>

            <div class="tab-content">
                <!-- Dashboard Tab -->
                <div id="dashboard-tab" class="tab-pane active">
                    <h2><i class="bi bi-house-door-fill icon-btn"></i> Welcome, <span id="username"></span></h2>
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-wallet2 icon-btn"></i> Accounts Overview</h3>
                            <table class="table table-striped" id="accounts-table">
                                <thead><tr><th>Name</th><th>Type</th><th>Balance</th></tr></thead>
                                <tbody></tbody>
                            </table>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-receipt icon-btn"></i> Recent Transactions</h3>
                            <table class="table table-striped" id="transactions-table">
                                <thead><tr><th>Date</th><th>Desc</th><th>Debit</th><th>Credit</th><th>Amount</th></tr></thead>
                                <tbody></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- Accounts Tab -->
                <div id="accounts-tab" class="tab-pane">
                    <h2><i class="bi bi-wallet2 icon-btn"></i> Manage Accounts</h2>
                    <div class="card">
                        <div class="card-body">
                            <div id="accounts-message"></div>
                            <form id="account-form">
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-tag icon-btn"></i> Name</label>
                                    <input type="text" id="account-name" class="form-control" required>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-list icon-btn"></i> Type</label>
                                    <select id="account-type" class="form-control">
                                        <option value="Asset">Asset</option>
                                        <option value="Liability">Liability</option>
                                        <option value="Equity">Equity</option>
                                        <option value="Revenue">Revenue</option>
                                        <option value="Expense">Expense</option>
                                    </select>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-currency-dollar icon-btn"></i> Opening Balance</label>
                                    <input type="number" step="0.01" id="account-opening-balance" class="form-control" placeholder="0.00">
                                </div>
                                <button type="submit" class="btn btn-primary w-100"><i class="bi bi-plus-circle icon-btn"></i> Add Account</button>
                            </form>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-list-ul icon-btn"></i> Accounts List</h3>
                            <table class="table table-striped" id="accounts-list">
                                <thead><tr><th>Name</th><th>Type</th><th>Balance</th><th>Action</th></tr></thead>
                                <tbody></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- Transactions Tab -->
                <div id="transactions-tab" class="tab-pane">
                    <h2><i class="bi bi-receipt icon-btn"></i> Record Transaction</h2>
                    <div class="card">
                        <div class="card-body">
                            <div id="transactions-message"></div>
                            <form id="transaction-form">
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-calendar icon-btn"></i> Date</label>
                                    <input type="date" id="transaction-date" class="form-control" required>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-pencil icon-btn"></i> Description</label>
                                    <input type="text" id="transaction-description" class="form-control" required>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-arrow-up-right icon-btn"></i> Debit Account</label>
                                    <select id="debit-account" class="form-control"></select>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-arrow-down-right icon-btn"></i> Credit Account</label>
                                    <select id="credit-account" class="form-control"></select>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-currency-dollar icon-btn"></i> Amount</label>
                                    <input type="number" step="0.01" id="transaction-amount" class="form-control" required>
                                </div>
                                <button type="submit" class="btn btn-primary w-100"><i class="bi bi-check-circle icon-btn"></i> Submit</button>
                            </form>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-list-ul icon-btn"></i> Transactions</h3>
                            <table class="table table-striped" id="transactions-list">
                                <thead><tr><th>Date</th><th>Desc</th><th>Debit</th><th>Credit</th><th>Amount</th><th>Action</th></tr></thead>
                                <tbody></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- Reports Tab -->
                <div id="reports-tab" class="tab-pane">
                    <h2><i class="bi bi-file-earmark-text icon-btn"></i> Reports</h2>
                    <!-- Balance Sheet -->
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-file-earmark-spreadsheet icon-btn"></i> Balance Sheet</h3>
                            <div id="balance-sheet-message"></div>
                            <form id="balance-sheet-form">
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-calendar icon-btn"></i> Start Date</label>
                                    <input type="date" id="balance-sheet-start" class="form-control">
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-calendar icon-btn"></i> End Date</label>
                                    <input type="date" id="balance-sheet-end" class="form-control">
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-filetype-csv icon-btn"></i> Export As</label>
                                    <select id="balance-sheet-export" class="form-control">
                                        <option value="csv">CSV</option>
                                        <option value="html">HTML</option>
                                    </select>
                                </div>
                                <button type="submit" class="btn btn-primary w-100 mb-2"><i class="bi bi-eye icon-btn"></i> Generate</button>
                                <button type="button" class="btn btn-success w-100" onclick="exportBalanceSheet()"><i class="bi bi-download icon-btn"></i> Export</button>
                            </form>
                            <table class="table table-striped mt-3" id="balance-sheet-table">
                                <thead><tr><th>Category</th><th>Amount</th></tr></thead>
                                <tbody></tbody>
                            </table>
                        </div>
                    </div>
                    <!-- Account Ledger -->
                    <div class="card">
                        <div class="card-body">
                            <h3><i class="bi bi-file-earmark-text icon-btn"></i> Account Ledger</h3>
                            <div id="account-ledger-message"></div>
                            <form id="account-ledger-form">
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-wallet2 icon-btn"></i> Account</label>
                                    <select id="account-ledger-account" class="form-control"></select>
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-calendar icon-btn"></i> Start Date</label>
                                    <input type="date" id="account-ledger-start" class="form-control">
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-calendar icon-btn"></i> End Date</label>
                                    <input type="date" id="account-ledger-end" class="form-control">
                                </div>
                                <div class="mb-3">
                                    <label class="form-label"><i class="bi bi-filetype-csv icon-btn"></i> Export As</label>
                                    <select id="account-ledger-export" class="form-control">
                                        <option value="csv">CSV</option>
                                        <option value="html">HTML</option>
                                    </select>
                                </div>
                                <button type="submit" class="btn btn-primary w-100 mb-2"><i class="bi bi-eye icon-btn"></i> Generate</button>
                                <button type="button" class="btn btn-success w-100" onclick="exportAccountLedger()"><i class="bi bi-download icon-btn"></i> Export</button>
                            </form>
                            <table class="table table-striped mt-3" id="account-ledger-table">
                                <thead><tr><th>Date</th><th>Description</th><th>Debit</th><th>Credit</th><th>Balance</th></tr></thead>
                                <tbody></tbody>
                            </table>
 
