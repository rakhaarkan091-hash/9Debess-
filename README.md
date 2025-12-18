<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kelas 9D - Sistem Management Kelas</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f172a, #1e3a8a);
            color: white;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Header */
        header {
            text-align: center;
            margin-bottom: 30px;
            padding: 20px;
        }

        .logo {
            font-size: 3rem;
            margin-bottom: 10px;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: #60a5fa;
        }

        .subtitle {
            font-size: 1.2rem;
            color: #93c5fd;
            margin-bottom: 20px;
        }

        /* Navigation */
        .nav-tabs {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 30px;
        }

        .nav-tab {
            background: rgba(30, 58, 138, 0.6);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid rgba(96, 165, 250, 0.3);
        }

        .nav-tab.active {
            background: rgba(96, 165, 250, 0.3);
            border-color: #60a5fa;
            transform: translateY(-5px);
        }

        .nav-tab:hover {
            transform: translateY(-3px);
        }

        .nav-tab i {
            font-size: 2rem;
            margin-bottom: 10px;
            color: #60a5fa;
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: rgba(30, 58, 138, 0.5);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(96, 165, 250, 0.3);
            backdrop-filter: blur(10px);
        }

        .stat-number {
            font-size: 3rem;
            font-weight: bold;
            color: #60a5fa;
            margin-bottom: 10px;
        }

        .stat-label {
            font-size: 1.1rem;
            color: #93c5fd;
        }

        /* Content Sections */
        .content-section {
            display: none;
            background: rgba(30, 58, 138, 0.4);
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            border: 1px solid rgba(96, 165, 250, 0.3);
            backdrop-filter: blur(10px);
        }

        .content-section.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Tables */
        .table-container {
            overflow-x: auto;
            margin: 20px 0;
            border-radius: 10px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background: rgba(15, 23, 42, 0.6);
        }

        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid rgba(96, 165, 250, 0.3);
        }

        th {
            background: rgba(30, 58, 138, 0.8);
            color: #60a5fa;
            font-weight: 600;
        }

        tr:hover {
            background: rgba(96, 165, 250, 0.1);
        }

        /* Buttons */
        .btn {
            background: #60a5fa;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            margin: 10px 5px;
        }

        .btn:hover {
            background: #3b82f6;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }

        .btn-secondary {
            background: rgba(96, 165, 250, 0.3);
            border: 1px solid #60a5fa;
        }

        .btn-secondary:hover {
            background: rgba(96, 165, 250, 0.5);
        }

        /* Forms */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #93c5fd;
            font-weight: 600;
        }

        input, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid rgba(96, 165, 250, 0.3);
            border-radius: 8px;
            background: rgba(15, 23, 42, 0.6);
            color: white;
            font-size: 1rem;
        }

        textarea {
            min-height: 120px;
            resize: vertical;
        }

        /* Fish Animation */
        .fish {
            position: fixed;
            font-size: 2rem;
            z-index: -1;
            opacity: 0.7;
            animation: swim linear infinite;
        }

        @keyframes swim {
            0% { transform: translateX(-100px); }
            100% { transform: translateX(calc(100vw + 100px)); }
        }

        /* Motivation */
        .motivation {
            text-align: center;
            font-style: italic;
            color: #93c5fd;
            margin: 20px 0;
            font-size: 1.2rem;
            padding: 20px;
            background: rgba(30, 58, 138, 0.4);
            border-radius: 10px;
            border-left: 4px solid #60a5fa;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-tabs {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Ikan Animasi -->
    <div class="fish" style="top: 10%; animation-duration: 40s;">🐠</div>
    <div class="fish" style="top: 20%; animation-duration: 35s; animation-delay: 2s;">🐟</div>
    <div class="fish" style="top: 30%; animation-duration: 45s; animation-delay: 5s;">🐡</div>
    <div class="fish" style="top: 40%; animation-duration: 38s; animation-delay: 7s;">🦈</div>
    <div class="fish" style="top: 60%; animation-duration: 42s; animation-delay: 10s;">🐠</div>
    <div class="fish" style="top: 70%; animation-duration: 50s; animation-delay: 12s;">🐟</div>

    <div class="container">
        <header>
            <div class="logo">🌊</div>
            <h1>Kelas 9D</h1>
            <div class="subtitle">Sistem Management Kelas Bertema Laut</div>
        </header>

        <div class="nav-tabs">
            <div class="nav-tab active" onclick="showTab('dashboard')">
                <i class="fas fa-tachometer-alt"></i>
                <div>Dashboard</div>
            </div>
            <div class="nav-tab" onclick="showTab('absen')">
                <i class="fas fa-clipboard-check"></i>
                <div>Absensi</div>
            </div>
            <div class="nav-tab" onclick="showTab('jurnal')">
                <i class="fas fa-book"></i>
                <div>Jurnal</div>
            </div>
            <div class="nav-tab" onclick="showTab('kas')">
                <i class="fas fa-money-bill-wave"></i>
                <div>Kas Kelas</div>
            </div>
        </div>

        <!-- Dashboard -->
        <div id="dashboard" class="content-section active">
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number" id="total-siswa">36</div>
                    <div class="stat-label">Total Siswa</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="hadir-count">0</div>
                    <div class="stat-label">Hadir</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="sakit-count">0</div>
                    <div class="stat-label">Sakit</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="izin-count">0</div>
                    <div class="stat-label">Izin</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="alpa-count">0</div>
                    <div class="stat-label">Alpa</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="total-kas">Rp 0</div>
                    <div class="stat-label">Total Kas</div>
                </div>
            </div>

            <div class="motivation">
                "Kedalaman laut mencerminkan kedalaman ilmu kita"
            </div>

            <h3 style="margin: 20px 0; color: #60a5fa;">Ringkasan Kehadiran Hari Ini</h3>
            <div class="table-container">
                <table id="summary-table">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>Nama Siswa</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody id="summary-tbody">
                        <!-- Data akan diisi JavaScript -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Absensi -->
        <div id="absen" class="content-section">
            <h3 style="margin-bottom: 20px; color: #60a5fa;">
                <i class="fas fa-clipboard-check"></i> Absensi Siswa
            </h3>
            <div class="table-container">
                <table id="attendance-table">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>Nama Siswa</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody id="attendance-tbody">
                        <!-- Data akan diisi JavaScript -->
                    </tbody>
                </table>
            </div>
            <button class="btn" onclick="saveAttendance()">
                <i class="fas fa-save"></i> Simpan Absensi
            </button>
            <button class="btn btn-secondary" onclick="resetAttendance()">
                <i class="fas fa-redo"></i> Reset
            </button>
        </div>

        <!-- Jurnal -->
        <div id="jurnal" class="content-section">
            <h3 style="margin-bottom: 20px; color: #60a5fa;">
                <i class="fas fa-book"></i> Jurnal Kelas
            </h3>
            <div class="form-group">
                <label for="journal-date">Tanggal</label>
                <input type="date" id="journal-date">
            </div>
            <div class="form-group">
                <label for="journal-content">Isi Jurnal</label>
                <textarea id="journal-content" placeholder="Tuliskan kegiatan kelas hari ini..."></textarea>
            </div>
            <button class="btn" onclick="saveJournal()">
                <i class="fas fa-save"></i> Simpan Jurnal
            </button>
            <button class="btn btn-secondary" onclick="clearJournalForm()">
                <i class="fas fa-broom"></i> Bersihkan
            </button>
        </div>

        <!-- Kas -->
        <div id="kas" class="content-section">
            <h3 style="margin-bottom: 20px; color: #60a5fa;">
                <i class="fas fa-money-bill-wave"></i> Kas Kelas
            </h3>
            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                <div>
                    <h4 style="margin-bottom: 15px; color: #93c5fd;">Kas Bulanan</h4>
                    <div class="table-container">
                        <table id="monthly-kas-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Siswa</th>
                                    <th>Jumlah</th>
                                </tr>
                            </thead>
                            <tbody id="monthly-tbody">
                                <!-- Data akan diisi JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <button class="btn" onclick="saveMonthlyKas()">
                        <i class="fas fa-save"></i> Simpan Kas
                    </button>
                </div>
                <div>
                    <h4 style="margin-bottom: 15px; color: #93c5fd;">Kas Harian</h4>
                    <div class="table-container">
                        <table id="daily-kas-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Siswa</th>
                                    <th>Bayar</th>
                                </tr>
                            </thead>
                            <tbody id="daily-tbody">
                                <!-- Data akan diisi JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <button class="btn btn-secondary" onclick="saveDailyKas()">
                        <i class="fas fa-save"></i> Simpan Harian
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Data siswa
        const students = [
            "Agung Ramaindra Syahputra", "Ainun Tiyas martiningsih", "Alessia Alzena Riangga",
            "Almaira Faiqha", "Alya Faliha", "Amirah Julveni Maulana", "Andi Aqil",
            "Aurora Felicia Angelie", "Bilqis Melani", "Chaya muja syatira",
            "Fadhil oktavian nabil", "fahmi firjatullah", "faiz Alfarizi",
            "farhan umaydillah radjiansyah", "fathir pradipta alfarizi", "fazril nizart",
            "januari", "jihaan kaltsum khairunnisa", "juan edra abiya",
            "Khanza Rista Bhanuwati", "Kristiana Berta", "Marselino Prasetyo wijaya",
            "M. Fadil Putra pratama", "M. Kafka adri Al-Maliq 67 sigmo", "M. Luthfi faturrahman",
            "Natalis Fedora Purba", "Rafif Rakha Arkana Dih 🥀", "Rayhan Qolbu",
            "Runika Alzariva", "Suci Pratiwi", "Syafa Damia Sakhi", "Syech Faris maulana",
            "Tegar Tri Pambudi", "Tersa Usela", "Tiara Husna Humairah", "Zhafira Mayarista"
        ];

        // Inisialisasi data
        let attendanceData = JSON.parse(localStorage.getItem('attendanceData')) || {};
        let kasData = JSON.parse(localStorage.getItem('kasData')) || {};
        let journalData = JSON.parse(localStorage.getItem('journalData')) || [];

        // Fungsi untuk menampilkan tab
        function showTab(tabName) {
            // Sembunyikan semua tab
            document.querySelectorAll('.content-section').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Hapus active dari semua nav tab
            document.querySelectorAll('.nav-tab').forEach(nav => {
                nav.classList.remove('active');
            });
            
            // Tampilkan tab yang dipilih
            document.getElementById(tabName).classList.add('active');
            
            // Tambah active ke nav tab yang dipilih
            const navTabs = document.querySelectorAll('.nav-tab');
            if (tabName === 'dashboard') navTabs[0].classList.add('active');
            if (tabName === 'absen') navTabs[1].classList.add('active');
            if (tabName === 'jurnal') navTabs[2].classList.add('active');
            if (tabName === 'kas') navTabs[3].classList.add('active');
            
            // Jika tab absen, render ulang tabel
            if (tabName === 'absen') {
                renderAttendanceTable();
            }
        }

        // Initialize
        function initialize() {
            const today = new Date().toISOString().split('T')[0];
            
            if (!attendanceData[today]) {
                attendanceData[today] = {};
                students.forEach(student => {
                    attendanceData[today][student] = 'hadir';
                });
            }
            
            if (Object.keys(kasData).length === 0) {
                students.forEach(student => {
                    kasData[student] = { monthly: 0, daily: [] };
                });
            }
            
            renderTables();
            updateDashboard();
            
            // Set tanggal hari ini
            document.getElementById('journal-date').value = today;
        }

        // Render tables
        function renderTables() {
            renderAttendanceTable();
            renderKasTables();
        }

        // Render attendance table
        function renderAttendanceTable() {
            const today = new Date().toISOString().split('T')[0];
            const attendanceTbody = document.getElementById('attendance-tbody');
            attendanceTbody.innerHTML = '';
            
            students.forEach((student, index) => {
                const tr = document.createElement('tr');
                const currentStatus = attendanceData[today][student] || 'hadir';
                
                tr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <select style="padding: 8px; border-radius: 5px; background: rgba(15, 23, 42, 0.8); color: white; border: 1px solid #60a5fa;" 
                                onchange="updateAttendance(${index}, this.value)">
                            <option value="hadir" ${currentStatus === 'hadir' ? 'selected' : ''}>Hadir</option>
                            <option value="sakit" ${currentStatus === 'sakit' ? 'selected' : ''}>Sakit</option>
                            <option value="izin" ${currentStatus === 'izin' ? 'selected' : ''}>Izin</option>
                            <option value="alpa" ${currentStatus === 'alpa' ? 'selected' : ''}>Alpa</option>
                        </select>
                    </td>
                `;
                attendanceTbody.appendChild(tr);
            });
        }

        // Render kas tables
        function renderKasTables() {
            const today = new Date().toISOString().split('T')[0];
            const monthlyTbody = document.getElementById('monthly-tbody');
            const dailyTbody = document.getElementById('daily-tbody');
            
            monthlyTbody.innerHTML = '';
            dailyTbody.innerHTML = '';
            
            let totalKas = 0;
            
            students.forEach((student, index) => {
                // Monthly kas
                const monthlyTr = document.createElement('tr');
                const monthlyAmount = kasData[student].monthly || 0;
                
                monthlyTr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <input type="number" id="monthly-kas-${index}" value="${monthlyAmount}" 
                               min="0" style="width: 80px; padding: 5px; border-radius: 5px; background: rgba(15, 23, 42, 0.8); color: white; border: 1px solid #60a5fa;">
                    </td>
                `;
                monthlyTbody.appendChild(monthlyTr);
                
                // Daily kas
                const dailyTr = document.createElement('tr');
                const isPaid = kasData[student].daily && kasData[student].daily.includes(today);
                
                dailyTr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td>
                        <input type="checkbox" id="daily-kas-${index}" ${isPaid ? 'checked' : ''} 
                               style="transform: scale(1.5);">
                    </td>
                `;
                dailyTbody.appendChild(dailyTr);
                
                totalKas += monthlyAmount;
            });
            
            document.getElementById('total-kas').textContent = `Rp ${totalKas.toLocaleString()}`;
        }

        // Update dashboard
        function updateDashboard() {
            const today = new Date().toISOString().split('T')[0];
            const todayData = attendanceData[today] || {};
            
            let hadir = 0, sakit = 0, izin = 0, alpa = 0;
            
            students.forEach(student => {
                const status = todayData[student] || 'hadir';
                if (status === 'hadir') hadir++;
                else if (status === 'sakit') sakit++;
                else if (status === 'izin') izin++;
                else if (status === 'alpa') alpa++;
            });
            
            document.getElementById('hadir-count').textContent = hadir;
            document.getElementById('sakit-count').textContent = sakit;
            document.getElementById('izin-count').textContent = izin;
            document.getElementById('alpa-count').textContent = alpa;
            
            // Update summary table
            const summaryTbody = document.getElementById('summary-tbody');
            summaryTbody.innerHTML = '';
            
            students.forEach((student, index) => {
                const status = todayData[student] || 'hadir';
                const statusColor = {
                    'hadir': '#4ade80',
                    'sakit': '#fbbf24',
                    'izin': '#60a5fa',
                    'alpa': '#f87171'
                }[status];
                
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student}</td>
                    <td style="color: ${statusColor}; font-weight: 600;">${status.toUpperCase()}</td>
                `;
                summaryTbody.appendChild(tr);
            });
        }

        // Update attendance
        function updateAttendance(index, status) {
            const today = new Date().toISOString().split('T')[0];
            const student = students[index];
            attendanceData[today][student] = status;
            updateDashboard();
        }

        // Save attendance
        function saveAttendance() {
            localStorage.setItem('attendanceData', JSON.stringify(attendanceData));
            alert('Absensi berhasil disimpan!');
        }

        // Reset attendance
        function resetAttendance() {
            const today = new Date().toISOString().split('T')[0];
            students.forEach(student => {
                attendanceData[today][student] = 'hadir';
            });
            localStorage.setItem('attendanceData', JSON.stringify(attendanceData));
            renderAttendanceTable();
            updateDashboard();
            alert('Absensi telah direset ke Hadir!');
        }

        // Save journal
        function saveJournal() {
            const date = document.getElementById('journal-date').value;
            const content = document.getElementById('journal-content').value;
            
            if (date && content) {
                journalData.push({ date, content });
                localStorage.setItem('journalData', JSON.stringify(journalData));
                alert('Jurnal berhasil disimpan!');
                document.getElementById('journal-content').value = '';
            } else {
                alert('Harap isi tanggal dan isi jurnal!');
            }
        }

        // Clear journal form
        function clearJournalForm() {
            document.getElementById('journal-content').value = '';
        }

        // Save monthly kas
        function saveMonthlyKas() {
            students.forEach((student, index) => {
                const input = document.getElementById(`monthly-kas-${index}`);
                kasData[student].monthly = parseInt(input.value) || 0;
            });
            localStorage.setItem('kasData', JSON.stringify(kasData));
            renderKasTables();
            alert('Kas bulanan berhasil disimpan!');
        }

        // Save daily kas
        function saveDailyKas() {
            const today = new Date().toISOString().split('T')[0];
            students.forEach((student, index) => {
                const checkbox = document.getElementById(`daily-kas-${index}`);
                if (!kasData[student].daily) kasData[student].daily = [];
                
                if (checkbox.checked) {
                    if (!kasData[student].daily.includes(today)) {
                        kasData[student].daily.push(today);
                    }
                } else {
                    kasData[student].daily = kasData[student].daily.filter(d => d !== today);
                }
            });
            localStorage.setItem('kasData', JSON.stringify(kasData));
            alert('Kas harian berhasil disimpan!');
        }

        // Initialize app
        initialize();
    </script>
</body>
</html>
