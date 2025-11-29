<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kelas 9D - Sistem Management Kelas Bertema Laut</title>
    <style>
        :root {
            --primary: #1a73e8;
            --secondary: #0d47a1;
            --accent: #00bcd4;
            --light: #e3f2fd;
            --dark: #0d47a1;
            --success: #4caf50;
            --warning: #ff9800;
            --danger: #f44336;
            --info: #2196f3;
            --text: #333;
            --text-light: #fff;
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
            padding-bottom: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
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
            background: linear-gradient(90deg, var(--accent), var(--primary));
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo-icon {
            font-size: 2.5rem;
            margin-right: 10px;
            color: var(--primary);
        }

        .logo-text h1 {
            font-size: 1.8rem;
            color: var(--primary);
        }

        .logo-text p {
            font-size: 0.9rem;
            color: var(--dark);
        }

        .developer {
            font-size: 0.8rem;
            color: var(--dark);
            text-align: right;
        }

        .nav-tabs {
            display: flex;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .nav-tab {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            color: var(--dark);
            position: relative;
        }

        .nav-tab.active {
            background: var(--primary);
            color: white;
        }

        .nav-tab:hover:not(.active) {
            background: rgba(26, 115, 232, 0.1);
        }

        .tab-content {
            display: none;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-card h3 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--dark);
        }

        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
        }

        .motivation {
            background: white;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
            font-style: italic;
            border-left: 5px solid var(--accent);
        }

        .table-container {
            overflow-x: auto;
            margin-bottom: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }

        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        th {
            background-color: var(--light);
            color: var(--dark);
            font-weight: 600;
        }

        tr:hover {
            background-color: rgba(0, 188, 212, 0.05);
        }

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
        }

        .status-hadir { color: var(--success); }
        .status-sakit { color: var(--warning); }
        .status-izin { color: var(--info); }
        .status-alpa { color: var(--danger); }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--dark);
        }

        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
        }

        textarea {
            min-height: 150px;
            resize: vertical;
        }

        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-block;
            margin: 10px 0;
        }

        button:hover {
            background: var(--secondary);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .kas-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .kas-section {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .kas-section h3 {
            margin-bottom: 15px;
            color: var(--dark);
            border-bottom: 2px solid var(--accent);
            padding-bottom: 10px;
        }

        .total-kas {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin: 20px 0;
            color: var(--primary);
        }

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
            animation: wave 12s linear infinite;
        }

        .wave:nth-child(2) {
            animation-delay: -6s;
            opacity: 0.5;
        }

        @keyframes wave {
            0% { background-position-x: 0; }
            100% { background-position-x: 1200px; }
        }

        .journal-entry {
            background: white;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .journal-entry h4 {
            color: var(--primary);
            margin-bottom: 10px;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        /* Ikan animasi */
        .fish {
            position: fixed;
            font-size: 2rem;
            z-index: -1;
            opacity: 0.7;
            animation: swim linear infinite;
        }

        @keyframes swim {
            0% {
                transform: translateX(-100px);
            }
            100% {
                transform: translateX(calc(100vw + 100px));
            }
        }

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
            }
            
            .logo {
                margin-bottom: 10px;
            }
            
            .attendance-option {
                flex-direction: column;
                gap: 5px;
            }
        }
    </style>
</head>
<body>
    <!-- Ikan animasi -->
    <div class="fish" style="top: 10%; animation-duration: 30s;">🐠</div>
    <div class="fish" style="top: 20%; animation-duration: 25s; animation-delay: 2s;">🐟</div>
    <div class="fish" style="top: 30%; animation-duration: 35s; animation-delay: 5s;">🐡</div>
    <div class="fish" style="top: 40%; animation-duration: 28s; animation-delay: 7s;">🦈</div>
    <div class="fish" style="top: 50%; animation-duration: 32s; animation-delay: 10s;">🐠</div>
    <div class="fish" style="top: 60%; animation-duration: 40s; animation-delay: 12s;">🐟</div>
    <div class="fish" style="top: 70%; animation-duration: 26s; animation-delay: 15s;">🐡</div>
    <div class="fish" style="top: 80%; animation-duration: 38s; animation-delay: 18s;">🦈</div>

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
            <div class="nav-tab active" data-tab="dashboard">Dashboard</div>
            <div class="nav-tab" data-tab="absen">Absensi</div>
            <div class="nav-tab" data-tab="jurnal">Jurnal</div>
            <div class="nav-tab" data-tab="kas">Kas Kelas</div>
        </div>

        <!-- Dashboard Tab -->
        <div id="dashboard" class="tab-content active">
            <div class="stats-container">
                <div class="stat-card">
                    <h3>Total Siswa</h3>
                    <div class="stat-value">36</div>
                </div>
                <div class="stat-card">
                    <h3>Hadir</h3>
                    <div class="stat-value" id="hadir-count">0</div>
                </div>
                <div class="stat-card">
                    <h3>Sakit</h3>
                    <div class="stat-value" id="sakit-count">0</div>
                </div>
                <div class="stat-card">
                    <h3>Izin</h3>
                    <div class="stat-value" id="izin-count">0</div>
                </div>
                <div class="stat-card">
                    <h3>Alpa</h3>
                    <div class="stat-value" id="alpa-count">0</div>
                </div>
                <div class="stat-card">
                    <h3>Total Kas</h3>
                    <div class="stat-value" id="total-kas-display">Rp 0</div>
                </div>
            </div>

            <div class="motivation">
                <p>"Kedalaman laut mencerminkan kedalaman ilmu kita"</p>
            </div>

            <h2>Ringkasan Kehadiran Hari Ini</h2>
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
            <h2>Absensi Siswa</h2>
            <p class="motivation">Catat kehadiran siswa dengan mudah</p>
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
                <button id="save-attendance">Simpan Absensi</button>
                <button id="reset-attendance">Reset Absensi</button>
            </div>
        </div>

        <!-- Jurnal Tab -->
        <div id="jurnal" class="tab-content">
            <h2>Jurnal Kelas</h2>
            <p class="motivation">Buat catatan jurnal kegiatan kelas</p>
            <div class="form-group">
                <label for="journal-date">Tanggal</label>
                <input type="date" id="journal-date">
            </div>
            <div class="form-group">
                <label for="journal-content">Isi Jurnal</label>
                <textarea id="journal-content" placeholder="Tuliskan kegiatan, pencapaian, atau catatan penting hari ini..."></textarea>
            </div>
            <div class="action-buttons">
                <button id="save-journal">Simpan Jurnal</button>
                <button id="clear-journal">Bersihkan Form</button>
            </div>
            
            <h3 style="margin-top: 30px;">Riwayat Jurnal</h3>
            <div id="journal-history">
                <!-- Riwayat jurnal akan ditampilkan di sini -->
            </div>
        </div>

        <!-- Kas Tab -->
        <div id="kas" class="tab-content">
            <h2>Manajemen Kas Kelas</h2>
            <p class="motivation">Kelola kas kelas dengan mudah</p>
            <div class="kas-container">
                <div class="kas-section">
                    <h3>Kas Bulanan</h3>
                    <p>Masukkan jumlah kas yang dibayar setiap siswa per bulan:</p>
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
                    <button id="save-monthly-kas">Simpan Kas Bulanan</button>
                </div>

                <div class="kas-section">
                    <h3>Kas Harian</h3>
                    <p>Centang untuk menandai siswa yang telah membayar kas hari ini:</p>
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
                    <button id="save-daily-kas">Simpan Kas Harian</button>
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

        // Tab Navigation
        document.querySelectorAll('.nav-tab').forEach(tab => {
            tab.addEventListener('click', () => {
                // Remove active class from all tabs and contents
                document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                
                // Add active class to clicked tab and corresponding content
                tab.classList.add('active');
                document.getElementById(tab.dataset.tab).classList.add('active');
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
                journalHistory.innerHTML = '<p>Belum ada jurnal yang disimpan.</p>';
                return;
            }
            
            // Sort journals by date (newest first)
            const sortedJournals = journalData.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedJournals.forEach(journal => {
                const journalDiv = document.createElement('div');
                journalDiv.className = 'journal-entry';
                journalDiv.innerHTML = `
                    <h4>${formatDate(journal.date)}</h4>
                    <p>${journal.content}</p>
                    <hr>
                `;
                journalHistory.appendChild(journalDiv);
            });
        }

        // Format date for display
        function formatDate(dateString) {
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            return new Date(dateString).toLocaleDateString('id-ID', options);
        }

        // Save attendance
        document.getElementById('save-attendance').addEventListener('click', () => {
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

        // Reset attendance
        document.getElementById('reset-attendance').addEventListener('click', () => {
            const today = new Date().toISOString().split('T')[0];
            
            students.forEach(student => {
                attendanceData[today][student] = 'hadir';
            });
            
            localStorage.setItem('attendanceData', JSON.stringify(attendanceData));
            renderAttendanceTable();
            updateDashboard();
            alert('Absensi telah direset!');
        });

        // Save monthly kas
        document.getElementById('save-monthly-kas').addEventListener('click', () => {
            students.forEach((student, index) => {
                const input = document.getElementById(`monthly-kas-${index}`);
                kasData[student].monthly = parseInt(input.value) || 0;
            });
            
            localStorage.setItem('kasData', JSON.stringify(kasData));
            renderKasTables();
            alert('Kas bulanan berhasil disimpan!');
        });

        // Save daily kas
        document.getElementById('save-daily-kas').addEventListener('click', () => {
            const today = new Date().toISOString().split('T')[0];
            
            students.forEach((student, index) => {
                const checkbox = document.getElementById(`daily-kas-${index}`);
                
                if (checkbox.checked) {
                    // Add today to daily payments if not already there
                    if (!kasData[student].daily.includes(today)) {
                        kasData[student].daily.push(today);
                    }
                } else {
                    // Remove today from daily payments
                    kasData[student].daily = kasData[student].daily.filter(date => date !== today);
                }
            });
            
            localStorage.setItem('kasData', JSON.stringify(kasData));
            alert('Kas harian berhasil disimpan!');
        });

        // Save journal
        document.getElementById('save-journal').addEventListener('click', () => {
            const date = document.getElementById('journal-date').value;
            const content = document.getElementById('journal-content').value;
            
            if (!date || !content) {
                alert('Harap isi tanggal dan isi jurnal!');
                return;
            }
            
            // Add new journal entry
            journalData.push({
                date,
                content
            });
            
            localStorage.setItem('journalData', JSON.stringify(journalData));
            
            // Clear form
            document.getElementById('journal-content').value = '';
            
            // Update journal history
            renderJournalHistory();
            
            alert('Jurnal berhasil disimpan!');
        });

        // Clear journal form
        document.getElementById('clear-journal').addEventListener('click', () => {
            document.getElementById('journal-content').value = '';
        });

        // Set today's date as default in journal form
        document.getElementById('journal-date').value = new Date().toISOString().split('T')[0];

        // Initialize the application
        initializeTables();
    </script>
</body>
</html>
