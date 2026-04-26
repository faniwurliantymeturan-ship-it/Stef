
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Olimpiade FST 2026 - UNPATTI</title>
    <!-- html2canvas untuk download kartu sebagai gambar -->
    <script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', 'Segoe UI', system-ui, sans-serif;
        }

        body {
            background: #ffffff;
            padding: 40px 20px;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
        }

        /* Header Biru Tua */
        .hero {
            background: #0a2b3e;
            border-radius: 32px;
            padding: 40px 50px;
            margin-bottom: 40px;
            color: white;
            box-shadow: 0 20px 35px -10px rgba(0,0,0,0.15);
        }

        .hero h1 {
            font-size: 3.2rem;
            letter-spacing: 2px;
            font-weight: 700;
        }

        .hero h1 span {
            font-weight: 300;
            color: #ffd966;
        }

        .hero .sub {
            font-size: 1.5rem;
            font-weight: 500;
            margin-top: 10px;
            border-left: 4px solid #ffb347;
            padding-left: 20px;
        }

        .hero .fst {
            font-size: 1rem;
            opacity: 0.9;
            margin-top: 8px;
        }

        .action-row {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            margin-top: 30px;
            gap: 20px;
        }

        .daftar-btn {
            background: #ff9800;
            border: none;
            padding: 14px 42px;
            font-size: 1.6rem;
            font-weight: bold;
            border-radius: 60px;
            color: #1e2f3e;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 8px 18px rgba(0,0,0,0.15);
        }

        .daftar-btn:hover {
            background: #ffb74d;
            transform: scale(1.02);
        }

        .countdown-box {
            background: rgba(0,0,0,0.5);
            backdrop-filter: blur(4px);
            padding: 15px 25px;
            border-radius: 50px;
            text-align: center;
        }

        .countdown-box p {
            font-size: 0.9rem;
            letter-spacing: 1px;
        }

        .timer {
            font-size: 2rem;
            font-weight: 700;
            font-family: monospace;
        }

        .kategori-title {
            font-size: 1.8rem;
            font-weight: 600;
            margin: 40px 0 20px 0;
            color: #1e4663;
            border-left: 7px solid #ff9800;
            padding-left: 20px;
        }

        .lomba-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .card {
            background: white;
            border-radius: 28px;
            padding: 25px 15px;
            text-align: center;
            box-shadow: 0 10px 20px rgba(0,0,0,0.08);
            transition: 0.2s;
            border: 1px solid #eee;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 30px rgba(0,0,0,0.12);
        }

        .card h3 {
            font-size: 1.9rem;
            color: #ff8c42;
            margin-bottom: 12px;
        }

        .card p {
            color: #2c3e4e;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .info-panel {
            background: white;
            border-radius: 28px;
            padding: 30px;
            margin: 30px 0;
            box-shadow: 0 8px 18px rgba(0,0,0,0.05);
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 20px;
            border: 1px solid #eee;
        }

        .info-item {
            flex: 1;
            min-width: 180px;
        }

        .info-item h4 {
            font-size: 1.3rem;
            color: #1e4663;
            margin-bottom: 12px;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .login-btn {
            background: #2c5a7a;
            border: none;
            padding: 10px 24px;
            border-radius: 40px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
        }

        .login-btn:hover {
            background: #1e3f58;
        }

        footer {
            text-align: center;
            margin-top: 50px;
            color: #5a6e7c;
        }

        /* MODAL FORM & LOGIN */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.6);
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }

        .modal-content {
            background: white;
            max-width: 550px;
            width: 90%;
            border-radius: 32px;
            padding: 30px;
            max-height: 85vh;
            overflow-y: auto;
        }

        .modal-content h2 {
            margin-bottom: 20px;
            color: #1e4663;
        }

        .form-group {
            margin-bottom: 16px;
        }

        .form-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 6px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 10px 14px;
            border-radius: 40px;
            border: 1px solid #ccc;
            font-size: 1rem;
        }

        button[type="submit"] {
            background: #ff9800;
            border: none;
            width: 100%;
            padding: 12px;
            border-radius: 40px;
            font-weight: bold;
            font-size: 1rem;
            margin-top: 10px;
            cursor: pointer;
        }

        .close-modal {
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Kartu Peserta */
        .kartu-peserta {
            background: linear-gradient(135deg, #fff9e6, #ffffff);
            border: 2px solid #ff9800;
            border-radius: 24px;
            padding: 25px;
            margin: 20px 0;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        .kartu-header {
            border-bottom: 2px dashed #ff9800;
            padding-bottom: 12px;
            margin-bottom: 15px;
            text-align: center;
        }

        .kartu-header h3 {
            color: #0a2b3e;
            font-size: 1.5rem;
        }

        .kartu-body {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .kartu-row {
            display: flex;
            justify-content: space-between;
            border-bottom: 1px solid #eee;
            padding-bottom: 8px;
        }

        .kartu-label {
            font-weight: 700;
            color: #1e4663;
        }

        .kartu-value {
            color: #2c3e4e;
        }

        .download-btn {
            background: #2c5a7a;
            margin-top: 15px;
        }

        .success-msg {
            background: #e3f7ec;
            padding: 15px;
            border-radius: 20px;
            text-align: center;
            margin-bottom: 20px;
            color: #2e7d32;
            font-weight: bold;
        }

        .row-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="navbar">
        <div style="font-weight: bold; font-size: 1.3rem;">🏆 Olimpiade FST</div>
        <div>
            <button class="login-btn" id="openLoginBtn">🔐 Login</button>
        </div>
    </div>

    <div class="hero">
        <h1>#UNPATTI <span>Universitas Pattimura</span></h1>
        <div class="sub">Fakultas Sains & Teknologi</div>
        <div class="fst">⭐ OLIMPIADE FST 2026: Kompetisi Sains</div>

        <div class="action-row">
            <button class="daftar-btn" id="daftarUtamaBtn">📋 DAFTAR</button>
            <div class="countdown-box">
                <p>⏳ Batas Pendaftaran: 15 Mei 2026</p>
                <div class="timer" id="countdownTimer">25 Hari : 12 Jam : 05 Menit</div>
                <p style="font-size:0.7rem;">Hitung Mundur Pendaftaran</p>
            </div>
        </div>
    </div>

    <div class="kategori-title">🏅 KATEGORI LOMBA</div>
    <div class="lomba-grid">
        <div class="card"><h3>📐 Matematika</h3><p>Aljabar, Geometri, Teori Bilangan, dan...</p></div>
        <div class="card"><h3>⚛️ Fisika</h3><p>Mekanik, Listrik, Optik, Termodinamika dan...</p></div>
        <div class="card"><h3>🧪 Kimia</h3><p>Struktur Atom, Asam, Basa, dan...</p></div>
        <div class="card"><h3>🧬 Biologi</h3><p>Molekuler, Genetika, Anatomi, Ekologi, dan...</p></div>
        <div class="card"><h3>💻 IT</h3><p>Rekayasa Perangkat Lunak, Jaringan, dan...</p></div>
    </div>

    <div class="info-panel">
        <div class="info-item"><h4>📌 Kategori Peserta</h4><p>Siswa SMA, SMP, SD</p></div>
        <div class="info-item"><h4>💰 Total Hadiah</h4><p>Uang Tunai, Sertifikat, Trophy</p></div>
        <div class="info-item"><h4>✅ Status</h4><p>Pendaftaran Dibuka!</p></div>
    </div>

    <footer>© Fakultas Sains & Teknologi UNPATTI - Olimpiade FST 2026</footer>
</div>

<!-- MODAL DAFTAR -->
<div id="registerModal" class="modal">
    <div class="modal-content">
        <span class="close-modal" id="closeRegisterModal">&times;</span>
        <h2>📝 Formulir Pendaftaran</h2>
        <form id="registerForm">
            <div class="form-group">
                <label>Nama Lengkap</label>
                <input type="text" id="regName" required placeholder="Nama lengkap">
            </div>
            <div class="row-2">
                <div class="form-group">
                    <label>Tanggal Lahir</label>
                    <input type="date" id="regTglLahir" required>
                </div>
                <div class="form-group">
                    <label>Asal Sekolah</label>
                    <input type="text" id="regAsalSekolah" required placeholder="Kota/Kabupaten">
                </div>
            </div>
            <div class="form-group">
                <label>Jenjang Sekolah</label>
                <select id="regJenjang" required>
                    <option value="">Pilih Jenjang</option>
                    <option value="SD">SD</option>
                    <option value="SMP">SMP</option>
                    <option value="SMA">SMA</option>
                </select>
            </div>
            <div class="form-group">
                <label>Mata Lomba (otomatis sesuai jenjang)</label>
                <select id="regMataLomba" required disabled>
                    <option value="">Pilih jenjang terlebih dahulu</option>
                </select>
            </div>
            <div class="form-group">
                <label>Nama Sekolah</label>
                <input type="text" id="regNamaSekolah" required placeholder="Nama lengkap sekolah">
            </div>
            <div class="form-group">
                <label>Nomor HP / WhatsApp</label>
                <input type="tel" id="regPhone" required placeholder="08xxxxxxxxxx">
            </div>
            <button type="submit">✨ Daftar Sekarang ✨</button>
        </form>
        <div id="registerResult"></div>
    </div>
</div>

<!-- MODAL LOGIN -->
<div id="loginModal" class="modal">
    <div class="modal-content">
        <span class="close-modal" id="closeLoginModal">&times;</span>
        <h2>🔑 Login Peserta</h2>
        <form id="loginForm">
            <div class="form-group">
                <label>Nomor Pendaftar</label>
                <input type="text" id="loginNoPeserta" required placeholder="Contoh: FST-2604-1234">
            </div>
            <div class="form-group">
                <label>Nomor HP (saat daftar)</label>
                <input type="tel" id="loginPhone" required placeholder="08xxxxxxxxxx">
            </div>
            <button type="submit">🔓 Login</button>
        </form>
        <div id="loginResult"></div>
    </div>
</div>

<!-- MODAL KARTU PESERTA (setelah daftar sukses) -->
<div id="kartuModal" class="modal">
    <div class="modal-content" style="max-width: 600px;">
        <span class="close-modal" id="closeKartuModal">&times;</span>
        <div id="kartuContainer">
            <!-- Kartu akan diisi JS -->
        </div>
    </div>
</div>

<script>
    // Data mata lomba berdasarkan jenjang
    const lombaByJenjang = {
        SD: [
            "Matematika SD (Berhitung, Logika Dasar)",
            "IPA SD (Eksperimen Sederhana)",
            "Bahasa Inggris SD"
        ],
        SMP: [
            "Matematika SMP (Aljabar, Geometri)",
            "Fisika SMP (Mekanika Dasar)",
            "Biologi SMP (Ekologi, Anatomi Dasar)",
            "Kimia SMP (Asam Basa, Reaksi Sederhana)"
        ],
        SMA: [
            "Matematika SMA (Kalkulus, Trigonometri)",
            "Fisika SMA (Mekanika Lanjut, Listrik)",
            "Kimia SMA (Termokimia, Stoikiometri)",
            "Biologi SMA (Genetika, Biologi Molekuler)",
            "Informatika / IT (Pemrograman Dasar, Jaringan)"
        ]
    };

    // Generate nomor peserta & ruangan (contoh: 1/rk10-lt3)
    function generateNomorPeserta() {
        let randomNum = Math.floor(Math.random() * 9000) + 1000;
        let now = new Date();
        let year = now.getFullYear().toString().slice(-2);
        let month = (now.getMonth()+1).toString().padStart(2,'0');
        return `FST-${year}${month}-${randomNum}`;
    }

    function generateRuangLomba() {
        const ruanganList = ["1/rk10-lt3", "2/rk08-lt2", "3/rk12-lt1", "4/labkom-lt2", "5/auditorium"];
        return ruanganList[Math.floor(Math.random() * ruanganList.length)];
    }

    // Simpan ke localStorage
    let participants = JSON.parse(localStorage.getItem('olimpiade_peserta')) || [];

    function saveParticipant(data) {
        const exists = participants.find(p => p.phone === data.phone);
        if(exists) return { success: false, message: "❌ Nomor HP sudah terdaftar! Silakan login." };
        
        const noPeserta = generateNomorPeserta();
        const ruangLomba = generateRuangLomba();
        
        const newParticipant = {
            ...data,
            noPeserta: noPeserta,
            ruangLomba: ruangLomba,
            tanggalDaftar: new Date().toLocaleString('id-ID')
        };
        participants.push(newParticipant);
        localStorage.setItem('olimpiade_peserta', JSON.stringify(participants));
        return { success: true, noPeserta, ruangLomba, nama: data.nama, jenjang: data.jenjang, namaSekolah: data.namaSekolah, mataLomba: data.mataLomba };
    }

    // Update dropdown mata lomba
    const jenjangSelect = document.getElementById('regJenjang');
    const mataLombaSelect = document.getElementById('regMataLomba');
    
    jenjangSelect.addEventListener('change', function() {
        const jenjang = this.value;
        mataLombaSelect.innerHTML = '';
        if (jenjang === '') {
            mataLombaSelect.disabled = true;
            mataLombaSelect.innerHTML = '<option value="">Pilih jenjang terlebih dahulu</option>';
            return;
        }
        mataLombaSelect.disabled = false;
        const lombaList = lombaByJenjang[jenjang];
        lombaList.forEach(lomba => {
            const option = document.createElement('option');
            option.value = lomba;
            option.textContent = lomba;
            mataLombaSelect.appendChild(option);
        });
    });

    // Tampilkan kartu peserta yang bisa di-download
    function showKartuPeserta(data) {
        const kartuHtml = `
            <div class="success-msg">
                🎉 Terima kasih telah mendaftar! 🎉
            </div>
            <div id="kartuDownloadArea" class="kartu-peserta">
                <div class="kartu-header">
                    <h3>🏅 KARTU PESERTA</h3>
                    <p>Olimpiade FST 2026 - UNPATTI</p>
                </div>
                <div class="kartu-body">
                    <div class="kartu-row">
                        <span class="kartu-label">Nama Peserta:</span>
                        <span class="kartu-value">${data.nama}</span>
                    </div>
                    <div class="kartu-row">
                        <span class="kartu-label">Jenjang:</span>
                        <span class="kartu-value">${data.jenjang}</span>
                    </div>
                    <div class="kartu-row">
                        <span class="kartu-label">Nama Sekolah:</span>
                        <span class="kartu-value">${data.namaSekolah}</span>
                    </div>
                    <div class="kartu-row">
                        <span class="kartu-label">Nomor Peserta:</span>
                        <span class="kartu-value"><strong>${data.noPeserta}</strong></span>
                    </div>
                    <div class="kartu-row">
                        <span class="kartu-label">Ruang Lomba:</span>
                        <span class="kartu-value"><strong>${data.ruangLomba}</strong></span>
                    </div>
                    <div class="kartu-row">
                        <span class="kartu-label">Mata Lomba:</span>
                        <span class="kartu-value">${data.mataLomba}</span>
                    </div>
                </div>
                <div style="text-align: center; margin-top: 20px; font-size: 12px; color: gray;">
                    Simpan kartu ini sebagai bukti pendaftaran
                </div>
            </div>
            <button id="downloadKartuBtn" class="download-btn" style="background:#ff9800; width:100%;">📥 Download Kartu Peserta (PNG)</button>
        `;
        document.getElementById('kartuContainer').innerHTML = kartuHtml;
        document.getElementById('kartuModal').style.display = 'flex';
        
        // Event download
        setTimeout(() => {
            const downloadBtn = document.getElementById('downloadKartuBtn');
            if(downloadBtn) {
                downloadBtn.addEventListener('click', function() {
                    const element = document.getElementById('kartuDownloadArea');
                    html2canvas(element, { scale: 2, backgroundColor: '#ffffff' }).then(canvas => {
                        const link = document.createElement('a');
                        link.download = `kartu_peserta_${data.noPeserta}.png`;
                        link.href = canvas.toDataURL();
                        link.click();
                    }).catch(err => {
                        alert("Gagal download, coba screenshot manual.");
                    });
                });
            }
        }, 100);
    }

    // Login logic
    function loginUser(noPeserta, phone) {
        const user = participants.find(p => p.noPeserta === noPeserta && p.phone === phone);
        if(user) {
            return { success: true, user };
        }
        return { success: false, message: "❌ Nomor pendaftar atau HP tidak cocok." };
    }

    // Modal elements
    const registerModal = document.getElementById('registerModal');
    const loginModal = document.getElementById('loginModal');
    const kartuModal = document.getElementById('kartuModal');

    function closeAllModals() {
        registerModal.style.display = 'none';
        loginModal.style.display = 'none';
        kartuModal.style.display = 'none';
    }

    document.getElementById('daftarUtamaBtn').addEventListener('click', () => {
        registerModal.style.display = 'flex';
        document.getElementById('registerResult').innerHTML = '';
        document.getElementById('registerForm').reset();
        mataLombaSelect.disabled = true;
        mataLombaSelect.innerHTML = '<option value="">Pilih jenjang terlebih dahulu</option>';
    });

    document.getElementById('openLoginBtn').addEventListener('click', () => {
        loginModal.style.display = 'flex';
        document.getElementById('loginResult').innerHTML = '';
        document.getElementById('loginForm').reset();
    });

    document.getElementById('closeRegisterModal').onclick = () => registerModal.style.display = 'none';
    document.getElementById('closeLoginModal').onclick = () => loginModal.style.display = 'none';
    document.getElementById('closeKartuModal').onclick = () => kartuModal.style.display = 'none';
    window.onclick = (e) => {
        if(e.target === registerModal) registerModal.style.display = 'none';
        if(e.target === loginModal) loginModal.style.display = 'none';
        if(e.target === kartuModal) kartuModal.style.display = 'none';
    };

    // Register form submit
    document.getElementById('registerForm').addEventListener('submit', (e) => {
        e.preventDefault();
        const nama = document.getElementById('regName').value.trim();
        const tglLahir = document.getElementById('regTglLahir').value;
        const asalSekolah = document.getElementById('regAsalSekolah').value.trim();
        const jenjang = document.getElementById('regJenjang').value;
        const mataLomba = document.getElementById('regMataLomba').value;
        const namaSekolah = document.getElementById('regNamaSekolah').value.trim();
        const phone = document.getElementById('regPhone').value.trim();

        if(!nama || !tglLahir || !asalSekolah || !jenjang || !mataLomba || !namaSekolah || !phone) {
            document.getElementById('registerResult').innerHTML = '<p style="color:red;">Semua field harus diisi!</p>';
            return;
        }
        if(!/^08\d{8,12}$/.test(phone)) {
            document.getElementById('registerResult').innerHTML = '<p style="color:red;">Nomor HP harus dimulai 08 dan minimal 10 digit</p>';
            return;
        }

        const result = saveParticipant({ nama, tglLahir, asalSekolah, jenjang, mataLomba, namaSekolah, phone });
        if(result.success) {
            registerModal.style.display = 'none';
            showKartuPeserta({
                nama: result.nama,
                jenjang: result.jenjang,
                namaSekolah: result.namaSekolah,
                noPeserta: result.noPeserta,
                ruangLomba: result.ruangLomba,
                mataLomba: result.mataLomba
            });
            document.getElementById('registerForm').reset();
        } else {
            document.getElementById('registerResult').innerHTML = `<p style="color:red;">${result.message}</p>`;
        }
    });

    // Login submit
    document.getElementById('loginForm').addEventListener('submit', (e) => {
        e.preventDefault();
        const noPeserta = document.getElementById('loginNoPeserta').value.trim();
        const phone = document.getElementById('loginPhone').value.trim();
        const result = loginUser(noPeserta, phone);
        if(result.success) {
            const user = result.user;
            loginModal.style.display = 'none';
            showKartuPeserta({
                nama: user.nama,
                jenjang: user.jenjang,
                namaSekolah: user.namaSekolah,
                noPeserta: user.noPeserta,
                ruangLomba: user.ruangLomba,
                mataLomba: user.mataLomba
            });
        } else {
            document.getElementById('loginResult').innerHTML = `<p style="color:red;">${result.message}</p>`;
        }
    });

    // Countdown Timer
    function updateCountdown() {
        const targetDate = new Date(2026, 4, 15, 0, 0, 0);
        const now = new Date();
        const diff = targetDate - now;
        if(diff <= 0) {
            document.getElementById('countdownTimer').innerHTML = "0 Hari : 0 Jam : 0 Menit";
            return;
        }
        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff % (86400000)) / (3600000));
        const minutes = Math.floor((diff % 3600000) / 60000);
        document.getElementById('countdownTimer').innerHTML = `${days} Hari : ${hours} Jam : ${minutes} Menit`;
    }
    setInterval(updateCountdown, 60000);
    updateCountdown();
</script>
</body>
</html>
