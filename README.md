<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kelas 9D - Sistem Management Kelas Bertema Laut</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #1a73e8;
            --primary-dark: #0d47a1;
            --secondary: #00bcd4;
            --accent: #ff6b6b;
            --light: #e3f2fd;
            --dark: #2d3748;
            --success: #4caf50;
            --warning: #ff9800;
            --danger: #f44336;
            --info: #2196f3;
            --text: #2d3748;
            --text-light: #718096;
            --bg: #f7fafc;
            --card-bg: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            color: var(--text);
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Header Styles */
        header {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            overflow: hidden;
            border-left: 5px solid var(--secondary);
        }

        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--secondary), var(--primary));
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo-icon {
            font-size: 3rem;
            margin-right: 15px;
            color: var(--primary);
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .logo-text h1 {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 5px;
        }

        .logo-text p {
            font-size: 1rem;
            color: var(--text-light);
        }

        .developer {
            font-size: 0.9rem;
            color: var(--text-light);
            text-align: right;
        }

        .developer strong {
            color: var(--primary);
        }

        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            background: var(--card-bg);
            border-radius: 15px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            color: var(--text);
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .nav-tab.active {
            background: var(--primary);
            color: white;
        }

        .nav-tab:hover:not(.active) {
            background: rgba(26, 115, 232, 0.1);
        }

        .nav-tab i {
            font-size: 1.2rem;
        }

        /* Tab Content */
        .tab-content {
            display: none;
            background: var(--card-bg);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Stats Container */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            text-align: center;
            transition: all 0.3s ease;
            border-top: 5px solid var(--primary);
            position: relative;
            overflow: hidden;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .stat-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--secondary), var(--primary));
        }

        .stat-card h3 {
            font-size: 1.1rem;
            margin-bottom: 15px;
            color: var(--text-light);
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--primary);
            margin: 10px 0;
        }

        .stat-card.total {
            border-top-color: var(--secondary);
        }

        .stat-card.hadir {
            border-top-color: var(--success);
        }

        .stat-card.sakit {
            border-top-color: var(--warning);
        }

        .stat-card.izin {
            border-top-color: var(--info);
        }

        .stat-card.alpa {
            border-top-color: var(--danger);
        }

        .stat-card.kas {
            border-top-color: var(--accent);
        }

        /* Motivation Box */
        .motivation {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            text-align: center;
            font-style: italic;
            font-size: 1.2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }

        .motivation::before {
            content: """;
            position: absolute;
            top: -20px;
            left: 10px;
            font-size: 5rem;
            opacity: 0.2;
        }

        .motivation::after {
            content: """;
            position: absolute;
            bottom: -40px;
            right: 10px;
            font-size: 5rem;
            opacity: 0.2;
        }

        /* Table Styles */
        .table-container {
            overflow-x: auto;
            margin-bottom: 25px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }

        th {
            background-color: var(--light);
            color: var(--primary-dark);
            font-weight: 600;
            position: sticky;
            top: 0;
        }

        tr:hover {
            background-color: rgba(0, 188, 212, 0.05);
        }

        /* Attendance Options */
        .attendance-option {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .attendance-option label {
            display: flex;
            align-items: center;
            gap: 5px;
            cursor: pointer;
            padding: 5px 10px;
            border-radius: 5px;
            transition: all 0.2s;
        }

        .attendance-option label:hover {
            background: rgba(0, 0, 0, 0.05);
        }

        .status-hadir { color: var(--success); font-weight: 600; }
        .status-sakit { color: var(--warning); font-weight: 600; }
        .status-izin { color: var(--info); font-weight: 600; }
        .status-alpa { color: var(--danger); font-weight: 600; }

        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }

        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(26, 115, 232, 0.2);
        }

        textarea {
            min-height: 150px;
            resize: vertical;
        }

        /* Button Styles */
        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 14px 28px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        button:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: 0 7px 14px rgba(0, 0, 0, 0.1);
        }

        button.secondary {
            background: var(--secondary);
        }

        button.secondary:hover {
            background: #00acc1;
        }

        button.danger {
            background: var(--danger);
        }

        button.danger:hover {
            background: #d32f2f;
        }

        /* Kas Container */
        .kas-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }

        .kas-section {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            border-top: 5px solid var(--accent);
        }

        .kas-section h3 {
            margin-bottom: 20px;
            color: var(--dark);
            border-bottom: 2px solid var(--light);
            padding-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .total-kas {
            font-size: 1.8rem;
            font-weight: bold;
            text-align: center;
            margin: 25px 0;
            color: var(--primary);
            background: var(--light);
            padding: 15px;
            border-radius: 10px;
        }

        /* Ocean Decoration */
        .ocean-decoration {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: linear-gradient(to top, rgba(13, 71, 161, 0.7), transparent);
            z-index: -1;
        }

        .wave {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: url('data:image/svg+xml;utf8,<svg viewBox="0 0 1200 120" xmlns="http://www.w3.org/2000/svg" fill="%231a298080"><path d="M0 0v46.29c47.79 22.2 103.59 32.17 158 28 70.36-5.37 136.33-33.31 206.8-37.5 73.84-4.36 147.54 16.88 218.2 35.26 69.27 18 138.3 24.88 209.4 13.08 36.15-6 69.85-17.84 104.45-29.34C989.49 25 1113-14.29 1200 52.47V0z" /></svg>');
            background-size: 1200px 100px;
            animation: wave 15s linear infinite;
        }

        .wave:nth-child(2) {
            animation-delay: -7s;
            opacity: 0.5;
        }

        @keyframes wave {
            0% { background-position-x: 0; }
            100% { background-position-x: 1200px; }
        }

        /* Fish Animation */
        .fish {
            position: fixed;
            font-size: 2.5rem;
            z-index: -1;
            opacity: 0.7;
            animation: swim linear infinite;
            filter: drop-shadow(0 2px 5px rgba(0, 0, 0, 0.2));
        }

        @keyframes swim {
            0% {
                transform: translateX(-100px) scaleX(1);
            }
            100% {
                transform: translateX(calc(100vw + 100px)) scaleX(1);
            }
        }

        .fish.reverse {
            animation-name: swim-reverse;
        }

        @keyframes swim-reverse {
            0% {
                transform: translateX(calc(100vw + 100px)) scaleX(-1);
            }
            100% {
                transform: translateX(-100px) scaleX(-1);
            }
        }

        /* Journal Entry */
        .journal-entry {
            background: var(--card-bg);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            border-left: 4px solid var(--primary);
        }

        .journal-entry h4 {
            color: var(--primary);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-top: 25px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .kas-container {
                grid-template-columns: 1fr;
            }
            
            .nav-tabs {
                flex-direction: column;
            }
            
            header {
                flex-direction: column;
                text-align: center;
                gap: 15px;
            }
            
            .logo {
                margin-bottom: 10px;
            }
            
            .attendance-option {
                flex-direction: column;
                gap: 5px;
            }
            
            .stats-container {
                grid-template-columns: 1fr;
            }
            
            .action-buttons {
                flex-direction: column;
            }
            
            button {
                width: 100%;
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <!-- Ikan animasi -->
    <div class="fish" style="top: 10%; animation-duration: 40s;">🐠</div>
    <div class="fish reverse" style="top: 20%; animation-duration: 35s; animation-delay: 2s;">🐟</div>
    <div class="fish" style="top: 30%; animation-duration: 45s; animation-delay: 5s;">🐡</div>
    <div class="fish reverse" style="top: 40%; animation-duration: 38s; animation-delay: 7s;">🦈</div>
    <div class="fish" style="top: 60%; animation-duration: 42s; animation-delay: 10s;">🐠</div>
    <div class="fish reverse" style="top: 70%; animation-duration: 50s; animation-delay: 12s;">🐟</div>
    <div class="fish" style="top: 80%; animation-duration: 36s; animation-delay: 15s;">🐡</div>
    <div class="fish reverse" style="top: 85%; animation-duration: 48s; animation-delay: 18s;">🦈</div>

    <div class="ocean-decoration">
        <div class="wave"></div>
        <div class="wave"></div>
    </div>

    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon">🌊</div>
                <div class="logo-text">
                    <h1>Kelas 9D - Samudra Ilmu</h1>
                    <p>Sistem Management Kelas Bertema Laut</p>
                </div>
            </div>
            <div class="developer">
                <p>Dikembangkan oleh <strong>Rafif</strong></p>
            </div>
        </header>

        <div class="nav-tabs">
            <div class="nav-tab active" data-tab="dashboard">
                <i class="fas fa-tachometer-alt"></i>
                <span>Dashboard</span>
            </div>
            <div class="nav-tab" data-tab="absen">
                <i class="fas fa-clipboard-check"></i>
                <span>Absensi</span>
            </div>
            <div class="nav-tab" data-tab="jurnal">
                <i class="fas fa-book"></i>
                <span>Jurnal</span>
            </div>
            <div class="nav-tab" data-tab="kas">
                <i class="fas fa-money-bill-wave"></i>
                <span>Kas Kelas</span>
            </div>
        </div>

        <!-- Dashboard Tab -->
        <div id="dashboard" class="tab-content active">
            <div class="stats-container">
                <div class="stat-card total">
                    <h3>Total Siswa</h3>
                    <div class="stat-value">36</div>
                    <p>Seluruh anggota kelas</p>
                </div>
                <div class="stat-card hadir">
                    <h3>Hadir</h3>
                    <div class="stat-value" id="hadir-count">36</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card sakit">
                    <h3>Sakit</h3>
                    <div class="stat-value" id="sakit-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card izin">
                    <h3>Izin</h3>
                    <div class="stat-value" id="izin-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card alpa">
                    <h3>Alpa</h3>
                    <div class="stat-value" id="alpa-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card kas">
                    <h3>Total Kas</h3>
                    <div class="stat-value" id="total-kas-display">Rp 0</div>
                    <p>Terakumulasi</p>
                </div>
            </div>

            <div class="motivation">
                <p>"Kedalaman laut mencerminkan kedalaman ilmu kita"</p>
            </div>

            <h2 style="margin-bottom: 20px; color: var(--primary); display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-list-alt"></i>
                Ringkasan Kehadiran Hari Ini
            </h2>
            <div class="table-container">
                <table id="summary-table">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>Nama Siswa</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- Data akan diisi oleh JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Absensi Tab -->
        <div id="absen" class="tab-content">
            <h2 style="margin-bottom: 20px; color: var(--primary); display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-clipboard-check"></i>
                Absensi Siswa
            </h2>
            <p class="motivation" style="margin-bottom: 25px;">Catat kehadiran siswa dengan mudah</p>
            <div class="table-container">
                <table id="attendance-table">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>Nama Siswa</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- Data akan diisi oleh JavaScript -->
                    </tbody>
                </table>
            </div>
            <div class="action-buttons">
                <button id="save-attendance">
                    <i class="fas fa-save"></i>
                    Simpan Absensi
                </b
