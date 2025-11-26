<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Kelas 9D - Ocean Theme</title>
    <!-- Font Modern -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* --- VARIABLES & RESET --- */
        :root {
            --bg-deep: #0f172a;
            --bg-ocean: #1e293b;
            --accent-cyan: #06b6d4;
            --accent-teal: #14b8a6;
            --accent-coral: #f43f5e;
            --text-light: #f1f5f9;
            --text-dim: #94a3b8;
            --glass-bg: rgba(30, 41, 59, 0.7);
            --glass-border: rgba(255, 255, 255, 0.1);
            --shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            outline: none;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #051821 0%, #004e64 100%);
            color: var(--text-light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* --- ANIMATED BUBBLES --- */
        .bubbles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }
        .bubble {
            position: absolute;
            bottom: -100px;
            background: radial-gradient(circle, rgba(255,255,255,0.2) 0%, rgba(255,255,255,0) 70%);
            border-radius: 50%;
            animation: float 15s infinite linear;
        }
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 0.8; }
            100% { transform: translateY(-120vh) rotate(360deg); opacity: 0; }
        }
        /* Randomizing bubbles via CSS nth-child handled in JS or manual CSS would be too long, 
           sticking to simple CSS setup for a few bubbles */
        .bubble:nth-child(1) { width: 80px; height: 80px; left: 10%; animation-duration: 12s; }
        .bubble:nth-child(2) { width: 40px; height: 40px; left: 20%; animation-duration: 18s; animation-delay: 2s; }
        .bubble:nth-child(3) { width: 60px; height: 60px; left: 35%; animation-duration: 15s; animation-delay: 1s; }
        .bubble:nth-child(4) { width: 90px; height: 90px; left: 70%; animation-duration: 20s; }
        .bubble:nth-child(5) { width: 30px; height: 30px; left: 85%; animation-duration: 14s; animation-delay: 3s; }

        /* --- LAYOUT --- */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 40px 0;
            animation: fadeInDown 1s ease;
        }
        
        header h1 {
            font-size: 3rem;
            font-weight: 700;
            background: linear-gradient(to right, var(--accent-cyan), var(--accent-teal));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            letter-spacing: 2px;
        }
        
        header p {
            color: var(--text-dim);
            font-size: 1.1rem;
        }

        /* --- NAVIGATION --- */
        .glass-nav {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            padding: 15px;
            border-radius: 50px;
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            box-shadow: var(--shadow);
            flex-wrap: wrap;
        }

        .nav-btn {
            background: transparent;
            border: none;
            color: var(--text-dim);
            padding: 10px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-btn:hover {
            color: var(--text-light);
            background: rgba(255,255,255,0.05);
        }

        .nav-btn.active {
            background: linear-gradient(135deg, var(--accent-cyan), var(--accent-teal));
            color: #0f172a;
            font-weight: 600;
            box-shadow: 0 4px 15px rgba(20, 184, 166, 0.4);
        }

        /* --- CONTENT SECTIONS --- */
        .content-section {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        .content-section.active {
            display: block;
        }

        .glass-card {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            padding: 30px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }

        h2 {
            font-size: 1.8rem;
            margin-bottom: 25px;
            color: var(--accent-cyan);
            border-bottom: 2px solid rgba(6, 182, 212, 0.3);
            padding-bottom: 10px;
            display: inline-block;
        }

        /* --- DASHBOARD GRID --- */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }
        
        .stat-card {
            background: rgba(255,255,255,0.05);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s;
            border: 1px solid transparent;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-cyan);
            background: rgba(255,255,255,0.1);
        }

        .stat-card h3 {
            font-size: 2.5rem;
            margin: 10px 0;
            color: var(--text-light);
        }
        
        .stat-card span {
            color: var(--text-dim);
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .stat-card.money h3 {
            color: var(--accent-teal);
            font-size: 1.8rem;
        }

        /* --- FORMS & TABLES --- */
        .control-panel {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
            align-items: center;
            flex-wrap: wrap;
        }

        input, select, textarea {
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid var(--glass-border);
            color: var(--text-light);
            padding: 12px 20px;
            border-radius: 10px;
            font-family: inherit;
            font-size: 1rem;
        }
        
        input[type="date"]::-webkit-calendar-picker-indicator {
            filter: invert(1);
            cursor: pointer;
        }

        button.btn-primary {
            background: linear-gradient(135deg, var(--accent-cyan), var(--accent-teal));
            color: #0f172a;
            border: none;
            padding: 12px 30px;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(6, 182, 212, 0.3);
        }

        button.btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(6, 182, 212, 0.5);
        }

        table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0 8px;
        }

        th {
            text-align: left;
            padding: 15px;
            color: var(--accent-cyan);
            font-weight: 600;
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
        }

        td {
            background: rgba(255,255,255,0.03);
            padding: 15px;
            font-size: 0.95rem;
        }

        td:first-child { border-radius: 10px 0 0 10px; }
        td:last-child { border-radius: 0 10px 10px 0; }
        
        tr:hover td {
            background: rgba(255,255,255,0.08);
        }

        /* Radio Buttons Custom */
        .radio-group {
            display: flex;
            gap: 15px;
        }
        
        .radio-option {
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        input[type="radio"] {
            accent-color: var(--accent-cyan);
            width: 16px;
            height: 16px;
        }

        /* --- TOAST NOTIFICATION --- */
        #toast {
            visibility: hidden;
            min-width: 250px;
            background-color: var(--accent-teal);
            color: #0f172a;
            text-align: center;
            border-radius: 50px;
            padding: 16px;
            position: fixed;
            z-index: 1000;
            left: 50%;
            bottom: 30px;
            transform: translateX(-50%);
            font-weight: 600;
            box-shadow: 0 5px 20px rgba(0,0,0,0.4);
            opacity: 0;
            transition: opacity 0.3s, bottom 0.3s;
        }

        #toast.show {
            visibility: visible;
            opacity: 1;
            bottom: 50px;
        }

        /* Animations */
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeInDown { from { opacity: 0; transform: translateY(-20px); } to { opacity: 1; transform: translateY(0); } }
        
        /* Mobile Responsive */
        @media (max-width: 768px) {
            header h1 { font-size: 2rem; }
            .radio-group { flex-direction: column; gap: 5px; }
            .control-panel { flex-direction: column; align-items: stretch; }
            .stats-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- Animated Bubbles -->
    <div class="bubbles">
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
    </div>

    <div class="container">
        <header>
            <i class="fas fa-water fa-3x" style="color: var(--accent-cyan); margin-bottom: 10px;"></i>
            <h1>KELAS 9D</h1>
            <p>Mengarungi Samudra Pengetahuan Bersama</p>
        </header>

        <!-- Navigation -->
        <nav class="glass-nav">
            <button class="nav-btn active" onclick="switchTab('dashboard')">
                <i class="fas fa-th-large"></i> Dashboard
            </button>
            <button class="nav-btn" onclick="switchTab('absensi')">
                <i class="fas fa-user-check"></i> Absensi
            </button>
            <button class="nav-btn" onclick="switchTab('jurnal')">
                <i class="fas fa-book-open"></i> Jurnal
            </button>
            <button class="nav-btn" onclick="switchTab('kas')">
                <i class="fas fa-coins"></i> Keuangan
            </button>
        </nav>

        <!-- DASHBOARD SECTION -->
        <section id="dashboard" class="content-section active">
            <div class="glass-card">
                <h2><i class="fas fa-chart-pie"></i> Statistik Kelas</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <span>Hadir Hari Ini</span>
                        <h3 id="stat-hadir">0</h3>
                        <i class="fas fa-users" style="color: var(--accent-cyan)"></i>
                    </div>
                    <div class="stat-card">
                        <span>Sakit / Izin</span>
                        <h3 id="stat-absen">0</h3>
                        <i class="fas fa-procedures" style="color: #fbbf24"></i>
                    </div>
                    <div class="stat-card">
                        <span>Alpha</span>
                        <h3 id="stat-alpha" style="color: var(--accent-coral)">0</h3>
                        <i class="fas fa-user-times" style="color: var(--accent-coral)"></i>
                    </div>
                    <div class="stat-card money">
                        <span>Total Kas</span>
                        <h3 id="stat-kas">Rp 0</h3>
                        <i class="fas fa-wallet"></i>
                    </div>
                </div>
            </div>
        </section>

        <!-- ABSENSI SECTION -->
        <section id="absensi" class="content-section">
            <div class="glass-card">
                <h2><i class="fas fa-calendar-check"></i> Input Absensi</h2>
                <div class="control-panel">
                    <input type="date" id="absen-date">
                    <button class="btn-primary" onclick="loadAttendance()">
                        <i class="fas fa-sync"></i> Muat Data
                    </button>
                    <button class="btn-primary" onclick="saveAttendance()" style="background: var(--accent-teal)">
                        <i class="fas fa-save"></i> Simpan Absen
                    </button>
                </div>
                <div style="overflow-x: auto;">
                    <table id="table-absen">
                        <thead>
                            <tr>
                                <th width="5%">No</th>
                                <th width="40%">Nama Siswa</th>
                                <th>Status Kehadiran</th>
                            </tr>
                        </thead>
                        <tbody id="tbody-absen">
                            <!-- JS will populate -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- JURNAL SECTION -->
        <section id="jurnal" class="content-section">
            <div class="glass-card">
                <h2><i class="fas fa-pen-fancy"></i> Jurnal Harian</h2>
                <div class="control-panel">
                    <input type="date" id="jurnal-date">
                    <button class="btn-primary" onclick="loadJournal()">Lihat Jurnal</button>
                </div>
                <textarea id="jurnal-text" rows="10" style="width: 100%; margin-top: 15px;" placeholder="Tulis kegiatan belajar mengajar hari ini..."></textarea>
                <br><br>
                <button class="btn-primary" onclick="saveJournal()">
                    <i class="fas fa-save"></i> Simpan Jurnal
                </button>
            </div>
        </section>

        <!-- KAS SECTION -->
        <section id="kas" class="content-section">
            <div class="glass-card">
                <h2><i class="fas fa-hand-holding-usd"></i> Manajemen Kas</h2>
                
                <!-- Input Deposit -->
                <div style="background: rgba(255,255,255,0.05); padding: 20px; border-radius: 15px; margin-bottom: 30px;">
                    <h3 style="font-size: 1.2rem; margin-bottom: 15px; color: var(--accent-cyan);">Isi Saldo Bulanan</h3>
                    <div class="control-panel">
                        <select id="kas-student-select" style="flex: 1;"></select>
                        <input type="number" id="kas-amount" placeholder="Jumlah (Rp)" style="flex: 1;">
                        <button class="btn-primary" onclick="addDeposit()">Tambah Saldo</button>
                    </div>
                </div>

                <!-- Daily Check -->
                <h3 style="font-size: 1.2rem; margin-bottom: 15px;">Absen Kas Harian (Rp 1.000)</h3>
                <div class="control-panel">
                    <input type="date" id="kas-date">
                    <button class="btn-primary" onclick="saveDailyKas()">Simpan Kas Harian</button>
                </div>

                <div style="overflow-x: auto;">
                    <table id="table-kas">
                        <thead>
                            <tr>
                                <th>Nama Siswa</th>
                                <th>Sisa Saldo</th>
                                <th>Bayar Hari Ini</th>
                            </tr>
                        </thead>
                        <tbody id="tbody-kas">
                            <!-- JS will populate -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

    </div>

    <!-- Toast -->
    <div id="toast">Notifikasi</div>

    <script>
        // --- 1. DATA INITIALIZATION ---
        const studentNames = [
            'Agung Ramaindra Syahputra', 'Ainun Tiyas Martiningsih', 'Alessia Alzena Riangga', 'Almaira Faiqha', 'Alya Faliha',
            'Amirah Julveni Maulana', 'Andi Aqil', 'Aurora Felicia Angelie', 'Bilqis Melani', 'Chaya Muja Syatira',
            'Fadhil Oktavian Nabil', 'Fahmi Firjatullah', 'Faiz Alfarizi', 'Farhan Umaydillah Rajiansyah', 'Fathir Pradipta Alfarizi',
            'Fazril Nizart', 'Januari', 'Jihaan Kaltsum Khairunnisa', 'Juan Edra Abiya', 'Khanza Rista Bhanuwati',
            'Kristiana Berta', 'Marselino Prasetyo Wijaya', 'M. Fadil Putra Pratama', 'M. Kafka Adri Al-Maliq', 'M. Luthfi Faturrahman',
            'Natalis Fedora Purba', 'Rafif Rakha Arkana', 'Rayhan Qolbu', 'Runika Alzariva', 'Suci Pratiwi',
            'Syafa Damia Sakhi', 'Syech Faris Maulana', 'Tegar Tri Pambudi', 'Tersa Usela', 'Tiara Husna Humairah',
            'Zhafira Mayarista'
        ];

        // Struktur Data Utama
        let appData = {
            attendance: {}, // format: { 'YYYY-MM-DD': { 'Nama': 'hadir' } }
            journal: {},    // format: { 'YYYY-MM-DD': 'Isi text' }
            balances: {},   // format: { 'Nama': 50000 } (Saldo Siswa)
            dailyKas: {}    // format: { 'YYYY-MM-DD': ['Nama1', 'Nama2'] } (Siapa yg bayar hari itu)
        };

        // Load from LocalStorage
        function initApp() {
            const savedData = localStorage.getItem('kelas9d_data_v2');
            if (savedData) {
                appData = JSON.parse(savedData);
            } else {
                // Init balances 0 if new
                studentNames.forEach(name => {
                    if (!appData.balances[name]) appData.balances[name] = 0;
                });
            }
            
            // Set input dates to today
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('absen-date').value = today;
            document.getElementById('jurnal-date').value = today;
            document.getElementById('kas-date').value = today;

            // Render all initial views
            updateDashboard();
            renderAttendanceTable();
            renderKasSelect();
            renderKasTable();
        }

        function saveData() {
            localStorage.setItem('kelas9d_data_v2', JSON.stringify(appData));
        }

        // --- 2. NAVIGATION ---
        function switchTab(tabId) {
            // Hide all sections
            document.querySelectorAll('.content-section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.nav-btn').forEach(el => el.classList.remove('active'));
            
            // Show target
            document.getElementById(tabId).classList.add('active');
            
            // Set active button (finding by onclick attribute matching is a simple way here)
            const btns = document.querySelectorAll('.nav-btn');
            btns.forEach(btn => {
                if(btn.getAttribute('onclick').includes(tabId)) {
                    btn.classList.add('active');
                }
            });

            if(tabId === 'dashboard') updateDashboard();
            if(tabId === 'absensi') loadAttendance(); // Refresh table view based on date
            if(tabId === 'kas') {
                renderKasTable();
                renderKasSelect();
            }
        }

        // --- 3. DASHBOARD LOGIC ---
        function updateDashboard() {
            // Calculate Absensi Today
            const today = new Date().toISOString().split('T')[0];
            const todayAbsen = appData.attendance[today] || {};
            
            let hadir = 0, absen = 0, alpha = 0;
            
            // If data exists for today, count it. If not, assume 0.
            // Alternatively, default to assuming everyone present if not filled? 
            // Let's count explicitly marked data.
            Object.values(todayAbsen).forEach(status => {
                if(status === 'Hadir') hadir++;
                if(status === 'Sakit' || status === 'Izin') absen++;
                if(status === 'Alpha') alpha++;
            });

            document.getElementById('stat-hadir').innerText = hadir;
            document.getElementById('stat-absen').innerText = absen;
            document.getElementById('stat-alpha').innerText = alpha;

            // Calculate Total Kas (Sum of all student balances + spent logic if needed)
            // For now, let's display Total Collected in Balances
            let totalKas = 0;
            for(let name in appData.balances) {
                totalKas += appData.balances[name];
            }
            document.getElementById('stat-kas').innerText = 'Rp ' + totalKas.toLocaleString('id-ID');
        }

        // --- 4. ABSENSI LOGIC ---
        function renderAttendanceTable() {
            const tbody = document.getElementById('tbody-absen');
            tbody.innerHTML = '';
            
            const date = document.getElementById('absen-date').value;
            const record = appData.attendance[date] || {};

            studentNames.forEach((name, index) => {
                const status = record[name] || 'Hadir'; // Default Hadir
                
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${name}</td>
                    <td>
                        <div class="radio-group">
                            <label class="radio-option"><input type="radio" name="status-${index}" value="Hadir" ${status==='Hadir'?'checked':''}> Hadir</label>
                            <label class="radio-option"><input type="radio" name="status-${index}" value="Sakit" ${status==='Sakit'?'checked':''}> Sakit</label>
                            <label class="radio-option"><input type="radio" name="status-${index}" value="Izin" ${status==='Izin'?'checked':''}> Izin</label>
                            <label class="radio-option"><input type="radio" name="status-${index}" value="Alpha" ${status==='Alpha'?'checked':''}> Alpha</label>
                        </div>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        function loadAttendance() {
            renderAttendanceTable();
            showToast("Data absensi dimuat");
        }

        function saveAttendance() {
            const date = document.getElementById('absen-date').value;
            if(!date) return showToast("Pilih tanggal dulu!");

            const newRecord = {};
            studentNames.forEach((name, index) => {
                const radios = document.getElementsByName(`status-${index}`);
                let val = 'Hadir';
                for(let r of radios) {
                    if(r.checked) val = r.value;
                }
                newRecord[name] = val;
            });

            appData.attendance[date] = newRecord;
            saveData();
            showToast("Absensi berhasil disimpan!");
            updateDashboard();
        }

        // --- 5. JURNAL LOGIC ---
        function loadJournal() {
            const date = document.getElementById('jurnal-date').value;
            const text = appData.journal[date] || '';
            document.getElementById('jurnal-text').value = text;
            showToast("Jurnal dimuat");
        }

        function saveJournal() {
            const date = document.getElementById('jurnal-date').value;
            const text = document.getElementById('jurnal-text').value;
            
            if(!date) return showToast("Pilih tanggal!");
            
            appData.journal[date] = text;
            saveData();
            showToast("Jurnal tersimpan!");
        }

        // --- 6. KAS LOGIC ---
        function renderKasSelect() {
            const sel = document.getElementById('kas-student-select');
            sel.innerHTML = '';
            studentNames.forEach(name => {
                const opt = document.createElement('option');
                opt.value = name;
                opt.text = name;
                sel.appendChild(opt);
            });
        }

        function addDeposit() {
            const name = document.getElementById('kas-student-select').value;
            const amount = parseInt(document.getElementById('kas-amount').value);

            if(!name || !amount || amount <= 0) {
                showToast("Data tidak valid!");
                return;
            }

            if(!appData.balances[name]) appData.balances[name] = 0;
            appData.balances[name] += amount;
            
            saveData();
            document.getElementById('kas-amount').value = '';
            showToast(`Saldo ${name} bertambah Rp ${amount}`);
            renderKasTable(); // Update table view
            updateDashboard();
        }

        function renderKasTable() {
            const tbody = document.getElementById('tbody-kas');
            tbody.innerHTML = '';
            const date = document.getElementById('kas-date').value;
            
            // List of people who paid ON THIS DATE
            const paidTodayList = appData.dailyKas[date] || [];

            studentNames.forEach((name, index) => {
                const saldo = appData.balances[name] || 0;
                const isPaid = paidTodayList.includes(name);

                // Auto-check logic: if already paid manually OR if not paid but has enough balance?
                // For simplified UX: We show check based on data.
                
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td>${name}</td>
                    <td style="color: ${saldo < 0 ? '#ff6b6b' : '#2CB5A0'}">Rp ${saldo.toLocaleString('id-ID')}</td>
                    <td>
                        <input type="checkbox" id="kas-check-${index}" ${isPaid ? 'checked' : ''}> 
                        <span style="font-size: 0.8rem; margin-left:5px;">Bayar (1k)</span>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        // Trigger render when kas date changes
        document.getElementById('kas-date').addEventListener('change', renderKasTable);
        document.getElementById('absen-date').addEventListener('change', renderAttendanceTable);
        document.getElementById('jurnal-date').addEventListener('change', loadJournal);

        function saveDailyKas() {
            const date = document.getElementById('kas-date').value;
            if(!date) return showToast("Pilih tanggal!");

            const currentPaidList = appData.dailyKas[date] || [];
            const newPaidList = [];
            const KAS_HARIAN = 1000;

            studentNames.forEach((name, index) => {
                const checkbox = document.getElementById(`kas-check-${index}`);
                const wasPaid = currentPaidList.includes(name);
                const isChecked = checkbox.checked;

                if (isChecked) {
                    newPaidList.push(name);
                    // If previously NOT paid, deduct balance now
                    if (!wasPaid) {
                        if(!appData.balances[name]) appData.balances[name] = 0;
                        appData.balances[name] -= KAS_HARIAN; // Subtract logic? Or assume balance is just a pot?
                        // Let's assume Balance is "Credit". 
                        // If they pay cash daily, balance shouldn't change? 
                        // Simplified Logic based on request: 
                        // Usually Kas Class: 
                        // Option A: Pay Monthly (Credit goes up). Daily check reduces Credit.
                        // Option B: Pay Daily Cash (Credit doesn't change, just record paid).
                        
                        // Let's stick to Option A for automatic feel.
                        // If checked, we deduct 1000 from their stored balance.
                    }
                } else {
                    // If unchecked but WAS paid, refund balance (undo)
                    if (wasPaid) {
                        appData.balances[name] += KAS_HARIAN;
                    }
                }
            });

            appData.dailyKas[date] = newPaidList;
            saveData();
            renderKasTable(); // Refresh to show new balances
            updateDashboard();
            showToast("Data Kas Harian Disimpan!");
        }

        // --- UTILS ---
        function showToast(msg) {
            const x = document.getElementById("toast");
            x.innerText = msg;
            x.className = "show";
            setTimeout(function(){ x.className = x.className.replace("show", ""); }, 3000);
        }

        // Initialize
        window.onload = initApp;

    </script>
</body>
</html>

