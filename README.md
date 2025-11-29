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
            --glass-bg: rgba(255, 255, 255, 0.25);
            --glass-border: rgba(255, 255, 255, 0.18);
            --glass-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
            --text: #2d3748;
            --text-light: #718096;
            --success: #4caf50;
            --warning: #ff9800;
            --danger: #f44336;
            --info: #2196f3;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: var(--text);
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Glassmorphism Effect */
        .glass {
            background: var(--glass-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--glass-border);
            box-shadow: var(--glass-shadow);
        }

        /* Header Styles */
        header {
            border-radius: 20px;
            padding: 25px;
            margin-bottom: 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            overflow: hidden;
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
            color: white;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .logo-text h1 {
            font-size: 2rem;
            color: white;
            margin-bottom: 5px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .logo-text p {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.9);
        }

        .developer {
            font-size: 0.9rem;
            color: rgba(255, 255, 255, 0.9);
            text-align: right;
        }

        .developer strong {
            color: white;
        }

        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            border-radius: 15px;
            margin-bottom: 25px;
            overflow: hidden;
        }

        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            color: white;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        .nav-tab.active {
            background: rgba(255, 255, 255, 0.3);
        }

        .nav-tab:hover:not(.active) {
            background: rgba(255, 255, 255, 0.2);
        }

        .nav-tab i {
            font-size: 1.2rem;
        }

        /* Tab Content */
        .tab-content {
            display: none;
            border-radius: 20px;
            padding: 30px;
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
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
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
            color: white;
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: white;
            margin: 10px 0;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .stat-card p {
            color: rgba(255, 255, 255, 0.9);
        }

        /* Motivation Box */
        .motivation {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            text-align: center;
            font-style: italic;
            font-size: 1.2rem;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .motivation::before {
            content: """;
            position: absolute;
            top: -20px;
            left: 10px;
            font-size: 5rem;
            opacity: 0.3;
        }

        .motivation::after {
            content: """;
            position: absolute;
            bottom: -40px;
            right: 10px;
            font-size: 5rem;
            opacity: 0.3;
        }

        /* Table Styles */
        .table-container {
            overflow-x: auto;
            margin-bottom: 25px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            color: white;
        }

        th {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-weight: 600;
            position: sticky;
            top: 0;
        }

        tr:hover {
            background: rgba(255, 255, 255, 0.1);
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
            color: white;
        }

        .attendance-option label:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        .status-hadir { color: #a7f3a7; font-weight: 600; }
        .status-sakit { color: #ffd699; font-weight: 600; }
        .status-izin { color: #99ccff; font-weight: 600; }
        .status-alpa { color: #ff9999; font-weight: 600; }

        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: white;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            backdrop-filter: blur(10px);
        }

        input::placeholder, textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(26, 115, 232, 0.3);
            background: rgba(255, 255, 255, 0.15);
        }

        textarea {
            min-height: 150px;
            resize: vertical;
        }

        /* Button Styles */
        button {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 14px 28px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            backdrop-filter: blur(10px);
        }

        button:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
            box-shadow: 0 7px 14px rgba(0, 0, 0, 0.2);
        }

        button.primary {
            background: var(--primary);
            border-color: var(--primary);
        }

        button.primary:hover {
            background: var(--primary-dark);
        }

        button.secondary {
            background: var(--secondary);
            border-color: var(--secondary);
        }

        button.secondary:hover {
            background: #00acc1;
        }

        /* Kas Container */
        .kas-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }

        .kas-section {
            border-radius: 15px;
            padding: 25px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        .kas-section h3 {
            margin-bottom: 20px;
            color: white;
            border-bottom: 2px solid rgba(255, 255, 255, 0.2);
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
            color: white;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
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
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            border-left: 4px solid var(--primary);
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .journal-entry h4 {
            color: white;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .journal-entry p {
            color: rgba(255, 255, 255, 0.9);
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

    <div class="container">
        <header class="glass">
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

        <div class="nav-tabs glass">
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
        <div id="dashboard" class="tab-content glass active">
            <div class="stats-container">
                <div class="stat-card glass">
                    <h3>Total Siswa</h3>
                    <div class="stat-value">36</div>
                    <p>Seluruh anggota kelas</p>
                </div>
                <div class="stat-card glass">
                    <h3>Hadir</h3>
                    <div class="stat-value" id="hadir-count">36</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card glass">
                    <h3>Sakit</h3>
                    <div class="stat-value" id="sakit-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card glass">
                    <h3>Izin</h3>
                    <div class="stat-value" id="izin-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card glass">
                    <h3>Alpa</h3>
                    <div class="stat-value" id="alpa-count">0</div>
                    <p>Hari ini</p>
                </div>
                <div class="stat-card glass">
                    <h3>Total Kas</h3>
                    <div class="stat-value" id="total-kas-display">Rp 0</div>
                    <p>Terakumulasi</p>
                </div>
            </div>

            <div class="motivation glass">
                <p>"Kedalaman laut mencerminkan kedalaman ilmu kita"</p>
            </div>

            <h2 style="margin-bottom: 20px; color: white; display: flex; align-items: center; gap: 10px;">
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
        <div id="absen" class="tab-content glass">
            <h2 style="margin-bottom: 20px; color: white; display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-clipboard-check"></i>
                Absensi Siswa
            </h2>
            <p class="motivation glass" style="margin-bottom: 25px;">Catat kehadiran siswa dengan mudah</p>
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
                <button id="save-attendance" class="primary">
                    <i class="fas fa-save"></i>
                    Simpan Absensi
                </button>
                <button id="reset-attendance" class="secondary">
                    <i class="fas fa-redo"></i>
                    Reset Absensi
                </button>
            </div>
        </div>

        <!-- Jurnal Tab -->
        <div id="jurnal" class="tab-content glass">
            <h2 style="margin-bottom: 20px; color: white; display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-book"></i>
                Jurnal Kelas
            </h2>
            <p class="motivation glass" style="margin-bottom: 25px;">Buat catatan jurnal kegiatan kelas</p>
            <div class="form-group">
                <label for="journal-date">
                    <i class="fas fa-calendar-alt"></i>
                    Tanggal
                </label>
                <input type="date" id="journal-date">
            </div>
            <div class="form-group">
                <label for="journal-content">
                    <i class="fas fa-edit"></i>
                    Isi Jurnal
                </label>
                <textarea id="journal-content" placeholder="Tuliskan kegiatan, pencapaian, atau catatan penting hari ini..."></textarea>
            </div>
            <div class="action-buttons">
                <button id="save-journal" class="primary">
                    <i class="fas fa-save"></i>
                    Simpan Jurnal
                </button>
                <button id="clear-journal" class="secondary">
                    <i class="fas fa-broom"></i>
                    Bersihkan Form
                </button>
            </div>
            
            <h3 style="margin: 30px 0 20px; color: white; display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-history"></i>
                Riwayat Jurnal
            </h3>
            <div id="journal-history">
                <!-- Riwayat jurnal akan ditampilkan di sini -->
            </div>
        </div>

        <!-- Kas Tab -->
        <div id="kas" class="tab-content glass">
            <h2 style="margin-bottom: 20px; color: white; display: flex; align-items: center; gap: 10px;">
                <i class="fas fa-money-bill-wave"></i>
                Manajemen Kas Kelas
            </h2>
            <p class="motivation glass" style="margin-bottom: 25px;">Kelola kas kelas dengan mudah</p>
            <div class="kas-container">
                <div class="kas-section">
                    <h3>
                        <i class="fas fa-calendar-month"></i>
                        Kas Bulanan
                    </h3>
                    <p style="color: rgba(255, 255, 255, 0.9);">Masukkan jumlah kas yang dibayar setiap siswa per bulan:</p>
                    <div class="table-container">
                        <table id="monthly-kas-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Siswa</th>
                                    <th>Jumlah Kas</th>
                                </tr>
                            </thead>
                            <tbody>
                                <!-- Data akan diisi oleh JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <button id="save-monthly-kas" class="primary">
                        <i class="fas fa-save"></i>
                        Simpan Kas Bulanan
                    </button>
                </div>

                <div class="kas-section">
                    <h3>
                        <i class="fas fa-calendar-day"></i>
                        Kas Harian
                    </h3>
                    <p style="color: rgba(255, 255, 255, 0.9);">Centang untuk menandai siswa yang telah membayar kas hari ini:</p>
                    <div class="table-container">
                        <table id="daily-kas-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Siswa</th>
                                    <th>Bayar Hari Ini</th>
                                </tr>
                            </thead>
                            <tbody>
                                <!-- Data akan diisi oleh JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <button id="save-daily-kas" class="secondary">
                        <i class="fas fa-save"></i>
                        Simpan Kas Harian
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Data siswa
        const students = [
            "Agung Ramaindra Syahputra",
            "Ainun Tiyas martiningsih",
            "Alessia Alzena Riangga",
            "Almaira Faiqha",
            "Alya Faliha",
            "Amirah Julveni Maulana",
            "Andi Aqil",
            "Aurora Felicia Angelie",
            "Bilqis Melani",
            "Chaya muja syatira",
            "Fadhil oktavian nabil",
            "fahmi firjatullah",
            "faiz Alfarizi",
            "farhan umaydillah radjiansyah",
            "fathir pradipta alfarizi",
            "fazril nizart",
            "januari",
            "jihaan kaltsum khairunnisa",
            "juan edra abiya",
            "Khanza Rista Bhanuwati",
            "Kristiana Berta",
            "Marselino Prasetyo wijaya",
            "M. Fadil Putra pratama",
            "M. Kafka adri Al-Maliq 67 sigmo",
            "M. Luthfi faturrahman",
            "Natalis Fedora Purba",
            "Rafif Rakha Arkana Dih 🥀",
            "Rayhan Qolbu",
            "Runika Alzariva",
            "Suci Pratiwi",
            "Syafa Damia Sakhi",
            "Syech Faris maulana",
            "Tegar Tri Pambudi",
            "Tersa Usela",
            "Tiara Husna Humairah",
            "Zhafira Mayarista"
        ];

        // Inisialisasi data
        let attendanceData = JSON.parse(localStorage.getItem('attendanceData')) || {};
        let kasData = JSON.parse(localStorage.getItem('kasData')) || {};
        let journalData = JSON.parse(localStorage.getItem('journalData')) || [];

        // Tab Navigation - FIXED
        document.querySelectorAll('.nav-tab').forEach(tab => {
            tab.addEventListener('click', function() {
                // Remove active class from all tabs and contents
                document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                
                // Add active class to clicked tab and corresponding content
                this.classList.add('active');
                const tabId = this.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
            });
        });

        // Initialize tables
        function initializeTables() {
            const today = new Date().toISOString().split('T')[0];
            
            // Initialize attendance data for today if not exists
            if (!attendanceData[today]) {
                attendanceData[today] = {};
                students.forEach(student => {
                    attendanceData[today][student] = 'hadir'; // Default value
                });
            }
            
            // Initialize kas data if not exists
            if (Object.keys(kasData).length === 0) {
                students.forEach(student => {
                    kasData[student] = {
                        monthly: 0,
                        daily: []
                    };
                });
            }
            
            // Render tables
            renderAttendanceTable();
            renderKasTables();
            updateDashboard();
            renderJournalHistory();
        }

        // Render attendance table
        function renderAttendanceTable() {
            const today = new Date().toISOString().split('T')[0];
            const tbody = document.querySelector('#attendance-table tbody');
            tbody.innerHTML = '';
            
            students.forEach((student, index) => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <div class="attendance-option">
                            <label>
                                <input type="radio" name="attendance-${index}" value="hadir" ${attendanceData[today][student] === 'hadir' ? 'checked' : ''}>
                                <span class="status-hadir">Hadir</span>
                            </label>
                            <label>
                                <input type="radio" name="attendance-${index}" value="sakit" ${attendanceData[today][student] === 'sakit' ? 'checked' : ''}>
                                <span class="status-sakit">Sakit</span>
                            </label>
                            <label>
                                <input type="radio" name="attendance-${index}" value="izin" ${attendanceData[today][student] === 'izin' ? 'checked' : ''}>
                                <span class="status-izin">Izin</span>
                            </label>
                            <label>
                                <input type="radio" name="attendance-${index}" value="alpa" ${attendanceData[today][student] === 'alpa' ? 'checked' : ''}>
                                <span class="status-alpa">Alpa</span>
                            </label>
                        </div>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        // Render kas tables
        function renderKasTables() {
            const monthlyTbody = document.querySelector('#monthly-kas-table tbody');
            const dailyTbody = document.querySelector('#daily-kas-table tbody');
            const today = new Date().toISOString().split('T')[0];
            
            monthlyTbody.innerHTML = '';
            dailyTbody.innerHTML = '';
            
            let totalKas = 0;
            
            students.forEach((student, index) => {
                // Monthly kas table
                const monthlyTr = document.createElement('tr');
                monthlyTr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <input type="number" id="monthly-kas-${index}" value="${kasData[student].monthly}" min="0">
                    </td>
                `;
                monthlyTbody.appendChild(monthlyTr);
                
                // Daily kas table
                const dailyTr = document.createElement('tr');
                const isPaidToday = kasData[student].daily.includes(today);
                dailyTr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <input type="checkbox" id="daily-kas-${index}" ${isPaidToday ? 'checked' : ''}>
                    </td>
                `;
                dailyTbody.appendChild(dailyTr);
                
                // Calculate total kas
                totalKas += kasData[student].monthly;
            });
            
            // Update total kas display
            document.getElementById('total-kas-display').textContent = `Rp ${totalKas.toLocaleString()}`;
        }

        // Update dashboard
        function updateDashboard() {
            const today = new Date().toISOString().split('T')[0];
            const todayAttendance = attendanceData[today] || {};
            
            // Count attendance status
            let hadir = 0, sakit = 0, izin = 0, alpa = 0;
            
            students.forEach(student => {
                const status = todayAttendance[student] || 'hadir';
                if (status === 'hadir') hadir++;
                else if (status === 'sakit') sakit++;
                else if (status === 'izin') izin++;
                else if (status === 'alpa') alpa++;
            });
            
            // Update counts
            document.getElementById('hadir-count').textContent = hadir;
            document.getElementById('sakit-count').textContent = sakit;
            document.getElementById('izin-count').textContent = izin;
            document.getElementById('alpa-count').textContent = alpa;
            
            // Update summary table
            const summaryTbody = document.querySelector('#summary-table tbody');
            summaryTbody.innerHTML = '';
            
            students.forEach((student, index) => {
                const status = todayAttendance[student] || 'hadir';
                const statusClass = `status-${status}`;
                
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td><span class="${statusClass}">${status.charAt(0).toUpperCase() + status.slice(1)}</span></td>
                `;
                summaryTbody.appendChild(tr);
            });
        }

        // Render journal history
        function renderJournalHistory() {
            const journalHistory = document.getElementById('journal-history');
            journalHistory.innerHTML = '';
            
            if (journalData.length === 0) {
                journalHistory.innerHTML = '<p style="text-align: center; padding: 20px; color: rgba(255, 255, 255, 0.7);">Belum ada jurnal yang disimpan.</p>';
                return;
            }
            
            // Sort journals by date (newest first)
            const sortedJournals = journalData.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedJournals.forEach(journal => {
                const journalDiv = document.createElement('div');
                journalDiv.className = 'journal-entry glass';
                journalDiv.innerHTML = `
                    <h4><i class="fas fa-calendar-day"></i> ${formatDate(journal.date)}</h4>
                    <p>${journal.content}</p>
                `;
                journalHistory.appendChild(journalDiv);
            });
        }

        // Format date for display
        function formatDate(dateString) {
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            return new Date(dateString).toLocaleDateString('id-ID', options);
        }

        // Save attendance - FIXED
        document.getElementById('save-attendance').addEventListener('click', function() {
            const today = new Date().toISOString().split('T')[0];
            
            students.forEach((student, index) => {
                const selectedOption = document.querySelector(`input[name="attendance-${index}"]:checked`);
                if (selectedOption) {
                    attendanceData[today][student] = selectedOption.value;
                }
            });
            
            localStorage.setItem('attendanceData', JSON.stringify(attendanceData));
            updateDashboard();
            alert('Absensi berhasil disimpan!');
        });

        // Reset attendance - FIXED
        document.getElementById('reset-attendance').addEventListener('click', function() {
            const today = new Date().toISOString().split('
