<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kelas 9D - Tema Laut</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2980, #26d0ce);
            min-height: 100vh;
            padding: 20px;
            color: white;
            overflow-x: hidden;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(5px);
            border-radius: 15px;
            padding: 25px 20px;
            text-align: center;
            transition: transform 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-card h3 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .stat-card p {
            font-size: 1rem;
            opacity: 0.9;
        }

        .navigation {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .nav-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(5px);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
            cursor: pointer;
        }

        .nav-card:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateY(-5px);
        }

        .nav-card i {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #a8e6cf;
        }

        .nav-card h3 {
            font-size: 1.4rem;
            margin-bottom: 10px;
        }

        .nav-card p {
            opacity: 0.8;
            font-size: 0.9rem;
        }

        .footer {
            text-align: center;
            margin-top: 30px;
            padding: 20px;
            font-size: 1.1rem;
            opacity: 0.9;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }

        .ocean-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .wave {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 200%;
            height: 100px;
            background: url('data:image/svg+xml;utf8,<svg viewBox="0 0 1200 120" xmlns="http://www.w3.org/2000/svg" fill="%2300a8cc22"><path d="M0 0v46.29c47.79 22.2 103.59 32.17 158 28 70.36-5.37 136.33-33.31 206.8-37.5 58.18-4.84 113.48 12.24 168.58 35.26 30.2 12.98 59 26.93 87.62 40.28 37.92 17.19 76.24 31.71 116.94 33.05 59.73 2.02 113.28-22.88 168.9-38.84 30.2-8.66 59-6.17 87.09 7.5 22.43 10.89 48 26.93 60.65 49.24V0z" /></svg>');
            background-size: 1200px 100px;
            animation: wave 12s linear infinite;
        }

        .wave:nth-child(2) {
            bottom: 10px;
            animation: wave 18s linear infinite;
            opacity: 0.7;
        }

        .wave:nth-child(3) {
            bottom: 20px;
            animation: wave 24s linear infinite;
            opacity: 0.5;
        }

        .bubble {
            position: absolute;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            animation: float linear infinite;
        }

        .bubble:nth-child(1) { width: 40px; height: 40px; left: 10%; animation-duration: 15s; animation-delay: 0s; }
        .bubble:nth-child(2) { width: 20px; height: 20px; left: 20%; animation-duration: 12s; animation-delay: 1s; }
        .bubble:nth-child(3) { width: 50px; height: 50px; left: 35%; animation-duration: 18s; animation-delay: 2s; }
        .bubble:nth-child(4) { width: 25px; height: 25px; left: 50%; animation-duration: 14s; animation-delay: 0s; }
        .bubble:nth-child(5) { width: 35px; height: 35px; left: 65%; animation-duration: 16s; animation-delay: 3s; }
        .bubble:nth-child(6) { width: 45px; height: 45px; left: 80%; animation-duration: 19s; animation-delay: 1s; }
        .bubble:nth-child(7) { width: 15px; height: 15px; left: 90%; animation-duration: 11s; animation-delay: 2s; }

        .fish {
            position: absolute;
            width: 40px;
            height: 20px;
            background: linear-gradient(45deg, #FF9A00, #FF6B6B);
            border-radius: 50% 10px 10px 50%;
            animation: swim 20s infinite linear;
            z-index: -1;
            opacity: 0.7;
        }
        
        .fish:before {
            content: '';
            position: absolute;
            top: 5px;
            right: -5px;
            width: 0;
            height: 0;
            border-top: 5px solid transparent;
            border-bottom: 5px solid transparent;
            border-left: 10px solid #FF6B6B;
        }
        
        .fish:nth-child(1) { top: 20%; left: 5%; animation-delay: 0s; }
        .fish:nth-child(2) { top: 60%; left: 15%; animation-delay: 2s; }
        .fish:nth-child(3) { top: 40%; left: 80%; animation-delay: 4s; }

        /* Halaman Kas */
        .page {
            display: none;
            animation: fadeIn 0.5s;
        }

        .page.active {
            display: block;
        }

        .page-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .back-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            color: white;
            font-size: 1.2rem;
            transition: all 0.3s ease;
        }

        .back-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }

        .section {
            margin-bottom: 30px;
        }

        .section h3 {
            margin-bottom: 15px;
            font-size: 1.5rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 12px 15px;
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }

        .form-group input::placeholder, .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.6);
        }

        .btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            border-radius: 10px;
            padding: 12px 20px;
            color: white;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        .btn-success {
            background: rgba(76, 175, 80, 0.6);
        }

        .btn-success:hover {
            background: rgba(76, 175, 80, 0.8);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            border-radius: 10px;
            overflow: hidden;
        }

        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        th {
            background: rgba(255, 255, 255, 0.2);
            font-weight: 600;
        }

        tr:hover {
            background: rgba(255, 255, 255, 0.05);
        }

        .attendance-options {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .attendance-option {
            padding: 8px 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .attendance-option.selected {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.05);
        }

        .attendance-option.hadir { background: rgba(76, 175, 80, 0.3); }
        .attendance-option.sakit { background: rgba(255, 152, 0, 0.3); }
        .attendance-option.izin { background: rgba(33, 150, 243, 0.3); }
        .attendance-option.alpa { background: rgba(244, 67, 54, 0.3); }

        @keyframes wave {
            0% { transform: translateX(0); }
            50% { transform: translateX(-25%); }
            100% { transform: translateX(-50%); }
        }

        @keyframes float {
            to {
                transform: translateY(-100vh) rotate(360deg);
            }
        }

        @keyframes swim {
            0% { transform: translateX(0) translateY(0); }
            25% { transform: translateX(200px) translateY(-50px); }
            50% { transform: translateX(400px) translateY(0); }
            75% { transform: translateX(600px) translateY(50px); }
            100% { transform: translateX(1000px) translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2.2rem;
            }
            
            .stats-container {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .navigation {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="ocean-bg">
        <div class="wave"></div>
        <div class="wave"></div>
        <div class="wave"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="bubble"></div>
        <div class="fish"></div>
        <div class="fish"></div>
        <div class="fish"></div>
    </div>

    <!-- Halaman Utama -->
    <div class="container page active" id="main-page">
        <div class="header">
            <h1>Kelas 9D</h1>
            <p>Sistem Manajemen Kelas Bertema Laut</p>
        </div>

        <div class="glass-card">
            <div class="stats-container">
                <div class="stat-card">
                    <h3 id="hadir-count">0</h3>
                    <p>Hadir</p>
                </div>
                <div class="stat-card">
                    <h3 id="sakit-count">0</h3>
                    <p>Sakit</p>
                </div>
                <div class="stat-card">
                    <h3 id="izin-count">0</h3>
                    <p>Izin</p>
                </div>
                <div class="stat-card">
                    <h3 id="alpa-count">0</h3>
                    <p>Alpa</p>
                </div>
                <div class="stat-card">
                    <h3 id="kas-total">Rp 0</h3>
                    <p>Total Kas</p>
                </div>
            </div>

            <div class="navigation">
                <div class="nav-card" onclick="showPage('absensi-page')">
                    <i class="fas fa-clipboard-list"></i>
                    <h3>Absensi</h3>
                    <p>Catat kehadiran siswa</p>
                </div>
                <div class="nav-card" onclick="showPage('jurnal-page')">
                    <i class="fas fa-book"></i>
                    <h3>Jurnal</h3>
                    <p>Buat catatan jurnal</p>
                </div>
                <div class="nav-card" onclick="showPage('kas-page')">
                    <i class="fas fa-money-bill-wave"></i>
                    <h3>Kas Kelas</h3>
                    <p>Kelola kas kelas</p>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>Kedalaman laut mencerminkan kedalaman ilmu kita!</p>
            <p>Total Siswa: 38</p>
        </div>
    </div>

    <!-- Halaman Absensi -->
    <div class="container page" id="absensi-page">
        <div class="page-header">
            <button class="back-btn" onclick="showPage('main-page')">
                <i class="fas fa-arrow-left"></i>
            </button>
            <div class="header">
                <h1>Absensi Kelas 9D</h1>
                <p>Catat kehadiran siswa dengan mudah</p>
            </div>
            <div style="width: 40px;"></div>
        </div>

        <div class="glass-card">
            <div class="section">
                <h3><i class="fas fa-calendar-alt"></i> Pilih Tanggal</h3>
                <div class="form-group">
                    <input type="date" id="attendance-date">
                </div>
            </div>

            <div class="section">
                <h3><i class="fas fa-users"></i> Daftar Siswa</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Nama Siswa</th>
                            <th>Status Kehadiran</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Agung Ramaindra Syahputra</td>
                            <td>
                                <div class="attendance-options">
                                    <div class="attendance-option hadir selected">Hadir</div>
                                    <div class="attendance-option sakit">Sakit</div>
                                    <div class="attendance-option izin">Izin</div>
                                    <div class="attendance-option alpa">Alpa</div>
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td>Ainun Tiyas Martiningsih</td>
                            <td>
                                <div class="attendance-options">
                                    <div class="attendance-option hadir selected">Hadir</div>
                                    <div class="attendance-option sakit">Sakit</div>
                                    <div class="attendance-option izin">Izin</div>
                                    <div class="attendance-option alpa">Alpa</div>
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td>Alessia Alzena Riangga</td>
                            <td>
                                <div class="attendance-options">
                                    <div class="attendance-option hadir">Hadir</div>
                                    <div class="attendance-option sakit">Sakit</div>
                                    <div class="attendance-option izin selected">Izin</div>
                                    <div class="attendance-option alpa">Alpa</div>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
                <button class="btn btn-success" style="margin-top: 20px;">
                    <i class="fas fa-save"></i> Simpan Absensi
                </button>
            </div>
        </div>
    </div>

    <!-- Halaman Jurnal -->
    <div class="container page" id="jurnal-page">
        <div class="page-header">
            <button class="back-btn" onclick="showPage('main-page')">
                <i class="fas fa-arrow-left"></i>
            </button>
            <div class="header">
                <h1>Jurnal Kelas 9D</h1>
                <p>Catat kegiatan pembelajaran harian</p>
            </div>
            <div style="width: 40px;"></div>
        </div>

        <div class="glass-card">
            <div class="section">
                <h3><i class="fas fa-calendar-alt"></i> Pilih Tanggal</h3>
                <div class="form-group">
                    <input type="date" id="journal-date">
                </div>
            </div>

            <div class="section">
                <h3><i class="fas fa-edit"></i> Isi Jurnal</h3>
                <div class="form-group">
                    <textarea id="journal-content" rows="10" placeholder="Tuliskan kegiatan pembelajaran hari ini..."></textarea>
                </div>
                <button class="btn btn-success">
                    <i class="fas fa-save"></i> Simpan Jurnal
                </button>
            </div>
        </div>
    </div>

    <!-- Halaman Kas -->
    <div class="container page" id="kas-page">
        <div class="page-header">
            <button class="back-btn" onclick="showPage('main-page')">
                <i class="fas fa-arrow-left"></i>
            </button>
            <div class="header">
                <h1>Kas Kelas 9D</h1>
                <p>Kelola keuangan kelas dengan mudah</p>
            </div>
            <div style="width: 40px;"></div>
        </div>

        <div class="glass-card">
            <div class="section">
                <h3><i class="fas fa-calendar-alt"></i> Kas Bulanan</h3>
                <div class="form-group">
                    <label for="student-select">Pilih Siswa:</label>
                    <select id="student-select">
                        <option value="">-- Pilih Siswa --</option>
                        <option value="Agung Ramaindra Syahputra">Agung Ramaindra Syahputra</option>
                        <option value="Ainun Tiyas Martiningsih">Ainun Tiyas Martiningsih</option>
                        <option value="Alessia Alzena Riangga">Alessia Alzena Riangga</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="payment-amount">Jumlah Bayar (Rp):</label>
                    <input type="number" id="payment-amount" placeholder="Contoh: 50000">
                </div>
                <button class="btn btn-success" id="process-payment">
                    <i class="fas fa-check"></i> Pro
