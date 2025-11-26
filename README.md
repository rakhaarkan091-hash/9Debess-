<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website Kelas 9D - Tema Laut</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* --- General Styling & Theme --- */
        @keyframes float-up {
            to {
                transform: translateY(-120vh) rotate(360deg);
            }
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        @keyframes wave {
            0% { transform: translateX(0); }
            50% { transform: translateX(-30px); }
            100% { transform: translateX(0); }
        }

        :root {
            --ocean-deep: #003459;
            --ocean-primary: #0077be;
            --ocean-light: #00a8cc;
            --sand: #f4f1de;
            --coral: #e07a5f;
            --seafoam: #a8e6cf;
            --white: #ffffff;
            --text-dark: #2c3e50;
            --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
            --btn-shadow: 0 4px 15px rgba(0, 119, 190, 0.3);
        }

        body {
            font-family: 'Quicksand', sans-serif;
            background: linear-gradient(180deg, var(--ocean-deep) 0%, var(--ocean-primary) 100%);
            color: var(--text-dark);
            margin: 0;
            padding: 20px;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* --- Animated Background --- */
        .ocean-bg {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
            overflow: hidden;
        }

        .bubble {
            position: absolute;
            bottom: -100px;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.5) 0%, rgba(255, 255, 255, 0.1) 70%);
            border-radius: 50%;
            opacity: 0.6;
            animation: float-up linear infinite;
        }

        .bubble:nth-child(1) { width: 40px; height: 40px; left: 10%; animation-duration: 15s; animation-delay: 0s; }
        .bubble:nth-child(2) { width: 20px; height: 20px; left: 20%; animation-duration: 12s; animation-delay: 1s; }
        .bubble:nth-child(3) { width: 50px; height: 50px; left: 35%; animation-duration: 18s; animation-delay: 2s; }
        .bubble:nth-child(4) { width: 25px; height: 25px; left: 50%; animation-duration: 14s; animation-delay: 0s; }
        .bubble:nth-child(5) { width: 35px; height: 35px; left: 65%; animation-duration: 16s; animation-delay: 3s; }
        .bubble:nth-child(6) { width: 45px; height: 45px; left: 80%; animation-duration: 19s; animation-delay: 1s; }
        .bubble:nth-child(7) { width: 15px; height: 15px; left: 90%; animation-duration: 11s; animation-delay: 2s; }

        /* Wave decoration */
        .wave-decoration {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none"><path d="M0,0V46.29c47.79,22.2,103.59,32.17,158,28,70.36-5.37,136.33-33.31,206.8-37.5C438.64,32.43,512.34,53.67,583,72.05c69.27,18,138.3,24.88,209.4,13.08,36.15-6,69.85-17.84,104.45-29.34C989.49,25,1113-14.29,1200,52.47V0Z" opacity=".25" fill="%2300a8cc"/><path d="M0,0V15.81C13,36.92,27.64,56.86,47.69,72.05,99.41,111.27,165,111,224.58,91.58c31.15-10.15,60.09-26.07,89.67-39.8,40.92-19,84.73-46,130.83-49.67,36.26-2.85,70.9,9.42,98.6,31.56,31.77,25.39,62.32,62,103.63,73,40.44,10.79,81.35-6.69,119.13-24.28s75.16-39,116.92-43.05c59.73-5.85,113.28,22.88,168.9,38.84,30.2,8.66,59,6.17,87.09-7.5,22.43-10.89,48-26.93,60.65-49.24V0Z" opacity=".5" fill="%2300a8cc"/><path d="M0,0V5.63C149.93,59,314.09,71.32,475.83,42.57c43-7.64,84.23-20.12,127.61-26.46,59-8.63,112.48,12.24,165.56,35.4C827.93,77.22,886,95.24,951.2,90c86.53-7,172.46-45.71,248.8-84.81V0Z" fill="%2300a8cc"/></svg>');
            background-size: cover;
            z-index: -1;
            animation: wave 10s infinite linear;
        }

        /* --- Main Container --- */
        .container {
            max-width: 1100px;
            margin: 20px auto;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(10px);
            padding: 30px;
            border-radius: 20px;
            box-shadow: var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.18);
            animation: fadeIn 0.8s ease-out;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 3px solid var(--ocean-light);
            position: relative;
        }

        header h1 {
            color: var(--ocean-deep);
            margin: 0;
            font-weight: 700;
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        header p {
            color: var(--ocean-primary);
            margin: 5px 0 0 0;
            font-weight: 500;
        }

        /* --- Navigation --- */
        nav {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .nav-btn {
            padding: 12px 25px;
            background: linear-gradient(135deg, var(--ocean-light), var(--ocean-primary));
            color: var(--white);
            border: 2px solid transparent;
            border-radius: 50px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            font-family: 'Quicksand', sans-serif;
            box-shadow: var(--btn-shadow);
            position: relative;
            overflow: hidden;
        }

        .nav-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s;
        }

        .nav-btn:hover::before {
            left: 100%;
        }

        .nav-btn.active {
            background: linear-gradient(135deg, var(--ocean-primary), var(--ocean-deep));
            transform: scale(1.05);
            box-shadow: 0 6px 20px rgba(0, 119, 190, 0.4);
        }

        .nav-btn:hover:not(.active) {
            background: linear-gradient(135deg, var(--coral), #d86a52);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(224, 122, 95, 0.4);
        }

        /* --- Sections --- */
        .content-section {
            display: none;
        }

        .content-section.active {
            display: block;
            animation: fadeIn 0.5s;
        }

        h2 {
            color: var(--ocean-deep);
            border-bottom: 2px solid var(--ocean-light);
            padding-bottom: 5px;
            margin-top: 0;
            position: relative;
            padding-left: 15px;
        }

        h2::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 5px;
            background: linear-gradient(to bottom, var(--ocean-light), var(--ocean-primary));
            border-radius: 3px;
        }

        /* --- Form Elements --- */
        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--ocean-primary);
        }

        input[type="date"],
        input[type="number"],
        select,
        textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--ocean-light);
            border-radius: 10px;
            box-sizing: border-box;
            font-size: 14px;
            font-family: 'Quicksand', sans-serif;
            transition: all 0.3s ease;
            background: rgba(255, 255, 255, 0.8);
        }

        input[type="date"]:focus,
        input[type="number"]:focus,
        select:focus,
        textarea:focus {
            outline: none;
            border-color: var(--ocean-primary);
            box-shadow: 0 0 0 3px rgba(0, 119, 190, 0.2);
            background: rgba(255, 255, 255, 1);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        .btn {
            padding: 12px 25px;
            background: linear-gradient(135deg, var(--ocean-primary), var(--ocean-light));
            color: var(--white);
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            font-family: 'Quicksand', sans-serif;
            box-shadow: var(--btn-shadow);
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            background: linear-gradient(135deg, var(--ocean-light), var(--ocean-primary));
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 119, 190, 0.4);
        }

        .btn-success {
            background: linear-gradient(135deg, #4CAF50, #45a049);
        }
        .btn-success:hover {
            background: linear-gradient(135deg, #45a049, #4CAF50);
        }

        /* --- Tables --- */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }

        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid rgba(0, 119, 190, 0.2);
        }

        th {
            background: linear-gradient(135deg, var(--ocean-light), var(--ocean-primary));
            font-weight: 600;
            color: var(--white);
        }

        tr:nth-child(even) {
            background-color: rgba(244, 241, 222, 0.3);
        }

        tr:hover {
            background-color: rgba(0, 168, 204, 0.1);
        }

        /* --- Radio & Checkbox --- */
        .radio-group, .checkbox-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }
        .radio-group label, .checkbox-group label {
            font-weight: 500;
            color: var(--text-dark);
        }

        /* --- Dashboard Board --- */
        .board-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .summary-card {
            background: linear-gradient(135deg, var(--ocean-light), var(--ocean-primary));
            color: var(--white);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 4px 15px rgba(0, 119, 190, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .summary-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 0%, transparent 70%);
            transform: rotate(30deg);
        }

        .summary-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 8px 25px rgba(0, 119, 190, 0.4);
        }

        .summary-card h3 {
            font-size: 36px;
            margin: 10px 0 0 0;
            font-weight: 700;
        }

        .summary-card p {
            margin: 0;
            font-weight: 500;
            font-size: 18px;
        }

        /* --- Utility --- */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            background: linear-gradient(135deg, var(--ocean-primary), var(--ocean-light));
            color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            opacity: 0;
            transition: opacity 0.5s, transform 0.5s;
            transform: translateX(100%);
            z-index: 1000;
            font-weight: 600;
        }

        .notification.show {
            opacity: 1;
            transform: translateX(0);
            animation: slideInRight 0.5s;
        }

        /* --- Attendance Status Styling --- */
        .attendance-status {
            display: flex;
            gap: 10px;
            justify-content: center;
        }

        .status-option {
            display: flex;
            align-items: center;
            gap: 5px;
            padding: 5px 10px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .status-option.hadir { background-color: rgba(76, 175, 80, 0.2); color: #2e7d32; }
        .status-option.sakit { background-color: rgba(255, 152, 0, 0.2); color: #ef6c00; }
        .status-option.izin { background-color: rgba(33, 150, 243, 0.2); color: #1565c0; }
        .status-option.alpa { background-color: rgba(244, 67, 54, 0.2); color: #c62828; }

        .status-option.selected {
            transform: scale(1.05);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }

        .status-option:hover {
            transform: translateY(-2px);
        }

        /* --- Responsive Adjustments --- */
        @media (max-width: 768px) {
            .container {
                padding: 15px;
                margin: 10px;
            }
            
            header h1 {
                font-size: 2em;
            }
            
            nav {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-btn {
                width: 100%;
                max-width: 250px;
            }
            
            .board-grid {
                grid-template-columns: 1fr;
            }
            
            table {
                font-size: 14px;
            }
            
            th, td {
                padding: 8px;
            }
        }
    </style>
</head>
<body>

    <!-- Animated Background -->
    <div class="ocean-bg">
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="wave-decoration"></div>
    </div>

    <div class="container">
        <header>
            <h1>🌊 Kelas 9D 🌊</h1>
            <p>Mengarungi Samudra Pengetahuan Bersama</p>
        </header>

        <nav>
            <button class="nav-btn active" data-target="board-section">📊 Dashboard</button>
            <button class="nav-btn" data-target="absensi-section">📝 Absensi</button>
            <button class="nav-btn" data-target="jurnal-section">📔 Jurnal</button>
            <button class="nav-btn" data-target="kas-section">💰 Kas Kelas</button>
        </nav>

        <main>
            <!-- Board Section -->
            <section id="board-section" class="content-section active">
                <h2>Dashboard Kelas</h2>
                <div class="board-grid">
                    <div class="summary-card">
                        <p>👨‍🎓 Jumlah Hadir</p>
                        <h3 id="total-hadir">0</h3>
                    </div>
                    <div class="summary-card">
                        <p>🤒 Jumlah Sakit</p>
                        <h3 id="total-sakit">0</h3>
                    </div>
                    <div class="summary-card">
                        <p>📝 Jumlah Izin</p>
                        <h3 id="total-izin">0</h3>
                    </div>
                    <div class="summary-card">
                        <p>❌ Jumlah Alpa</p>
                        <h3 id="total-alpa">0</h3>
                    </div>
                    <div class="summary-card">
                        <p>💰 Total Kas</p>
                        <h3 id="total-kas-bulanan">Rp 0</h3>
                    </div>
                </div>
            </section>

            <!-- Absensi Section -->
            <section id="absensi-section" class="content-section">
                <h2>Absensi Siswa</h2>
                <div class="form-group">
                    <label for="absen-date">Pilih Tanggal:</label>
                    <input type="date" id="absen-date">
                </div>
                <table id="absensi-table">
                    <thead>
                        <tr>
                            <th>Nama Siswa</th>
                            <th>Status Kehadiran</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- Will be populated by JS -->
                    </tbody>
                </table>
                <button class="btn btn-success" onclick="saveAttendance()" style="margin-top: 20px;">💾 Simpan Absensi</button>
            </section>

            <!-- Jurnal Section -->
            <section id="jurnal-section" class="content-section">
                <h2>Jurnal Kegiatan Pelajaran</h2>
                <div class="form-group">
                    <label for="jurnal-date">Pilih Tanggal:</label>
                    <input type="date" id="jurnal-date">
                </div>
                <div class="form-group">
                    <label for="jurnal-content">Isi Jurnal:</label>
                    <textarea id="jurnal-content" placeholder="Tuliskan kegiatan pelajaran hari ini..."></textarea>
                </div>
                <button class="btn btn-success" onclick="saveJournal()">💾 Simpan Jurnal</button>
            </section>

            <!-- Kas Section -->
            <section id="kas-section" class="content-section">
                <h2>Manajemen Kas</h2>
                
                <!-- Kas Bulanan -->
                <div style="margin-bottom: 40px;">
                    <h3>Input Kas Bulanan</h3>
                    <div class="form-group">
                        <label for="kas-bulanan-student">Pilih Siswa:</label>
                        <select id="kas-bulanan-student">
                            <!-- Will be populated by JS -->
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="kas-bulanan-amount">Jumlah Bayar (Rp):</label>
                        <input type="number" id="kas-bulanan-amount" placeholder="contoh: 5000">
                    </div>
                    <button class="btn btn-success" onclick="processMonthlyPayment()">💳 Bayar</button>
                </div>

                <hr>

                <!-- Kas Harian -->
             
