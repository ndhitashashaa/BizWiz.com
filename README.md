<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>BizWis - Simulasi UMKM</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #ff69b4;
      --light-bg: #fff7fb;
      --accent: #d63384;
      --text: #3b2c35;
      --gray: #999;
      --success: #28a745;
      --danger: #dc3545;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #fff0f5, #ffe4f1);
      color: var(--text);
      padding: 40px 16px;
      display: flex;
      justify-content: center;
      align-items: flex-start;
    }

    .container {
      background: white;
      max-width: 850px;
      width: 100%;
      padding: 32px;
      border-radius: 16px;
      box-shadow: 0 15px 40px rgba(214, 51, 132, 0.12);
    }

    h1 {
      font-family: 'Poppins', sans-serif;
      text-align: center;
      font-size: 2rem;
      font-weight: 700;
      color: var(--accent);
      margin-bottom: 24px;
    }

    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
    }

    label {
      font-weight: 600;
      font-size: 0.95rem;
      margin-bottom: 6px;
    }

    input[type="text"],
    input[type="number"] {
      padding: 12px 16px;
      border: 1.5px solid #ffd6e9;
      border-radius: 10px;
      font-size: 1rem;
      transition: all 0.2s ease;
    }

    input:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 2px rgba(255, 105, 180, 0.15);
    }

    small {
      font-size: 0.82rem;
      color: var(--gray);
      margin-top: 4px;
    }

    button {
      margin-top: 30px;
      width: 100%;
      background: var(--primary);
      color: white;
      border: none;
      padding: 14px;
      border-radius: 50px;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background: var(--accent);
    }

    .hasil {
      margin-top: 40px;
      background: var(--light-bg);
      padding: 24px;
      border-radius: 12px;
      border: 1px solid #ffd6e9;
      box-shadow: 0 10px 20px rgba(214, 51, 132, 0.08);
    }

    .hasil h3 {
      margin-bottom: 20px;
      color: var(--accent);
      font-size: 1.3rem;
    }

    .hasil p {
      margin-bottom: 8px;
      font-size: 0.95rem;
    }

    .success {
      color: var(--success);
      font-weight: bold;
    }

    .danger {
      color: var(--danger);
      font-weight: bold;
    }

    @media (max-width: 768px) {
      .grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>BizWis - Simulasi UMKM</h1>
    
    <div class="grid">
      <div class="form-group">
        <label for="penghasilan">Penghasilan Bulanan (Rp)</label>
        <input type="text" id="penghasilan" placeholder="Contoh: 10.000.000">
        <small>Pendapatan total dari usaha setiap bulan</small>
      </div>
      <div class="form-group">
        <label for="biaya">Biaya Tetap (Rp)</label>
        <input type="text" id="biaya" placeholder="Contoh: 3.000.000">
        <small>Sewa, listrik, bahan baku, langganan dll</small>
      </div>
      <div class="form-group">
        <label for="gaji">Gaji Pegawai (Rp)</label>
        <input type="text" id="gaji" placeholder="Contoh: 1.500.000">
        <small>Total gaji bulanan karyawan</small>
      </div>
      <div class="form-group">
        <label for="cicilan">Cicilan Usaha (Rp)</label>
        <input type="text" id="cicilan" placeholder="Contoh: 500.000">
        <small>Cicilan alat, kendaraan, pinjaman dll</small>
      </div>
      <div class="form-group">
        <label for="target">Target Laba Bersih (%)</label>
        <input type="number" id="target" placeholder="Contoh: 20">
        <small>Misal ingin untung 20% dari penghasilan</small>
      </div>
      <div class="form-group">
        <label for="darurat">Dana Darurat (%)</label>
        <input type="number" id="darurat" placeholder="Contoh: 10">
        <small>Tabungan cadangan dari keuntungan</small>
      </div>
    </div>

    <button onclick="hitung()">Hitung Simulasi</button>

    <div class="hasil" id="output">
      <h3>Hasil perhitungan akan muncul di sini.</h3>
    </div>
  </div>

  <script>
    function formatRupiah(angka) {
      return angka.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    }

    function parseRupiah(str) {
      return parseInt(str.replace(/\./g, '')) || 0;
    }

    document.querySelectorAll('input[type="text"]').forEach(input => {
      input.addEventListener('input', function () {
        const clean = this.value.replace(/\./g, '').replace(/[^\d]/g, '');
        this.value = formatRupiah(clean);
      });
    });

    function hitung() {
      const penghasilan = parseRupiah(document.getElementById("penghasilan").value);
      const biaya = parseRupiah(document.getElementById("biaya").value);
      const gaji = parseRupiah(document.getElementById("gaji").value);
      const cicilan = parseRupiah(document.getElementById("cicilan").value);
      const target = parseFloat(document.getElementById("target").value) / 100;
      const darurat = parseFloat(document.getElementById("darurat").value) / 100;

      const totalPengeluaran = biaya + gaji + cicilan;
      const labaKotor = penghasilan - totalPengeluaran;
      const danaDarurat = labaKotor * darurat;
      const labaBersih = labaKotor - danaDarurat;
      const targetLaba = penghasilan * target;

      let hasil = `
        <h3>Hasil Perhitungan:</h3>
        <p><strong>Total Pengeluaran:</strong> Rp ${formatRupiah(totalPengeluaran)}</p>
        <p><strong>Laba Kotor:</strong> Rp ${formatRupiah(labaKotor)}</p>
        <p><strong>Dana Darurat:</strong> Rp ${formatRupiah(danaDarurat)}</p>
        <p><strong>Laba Bersih:</strong> Rp ${formatRupiah(labaBersih)}</p>
        <p><strong>Target Laba:</strong> Rp ${formatRupiah(targetLaba)}</p>
      `;

      if (labaBersih >= targetLaba) {
        hasil += `<p class="success">✅ Selamat! Kamu sudah mencapai target keuntungan 🎉</p>`;
      } else {
        hasil += `<p class="danger">⚠️ Keuntungan belum sesuai target. Evaluasi pengeluaran atau naikkan penjualan.</p>`;
      }

      document.getElementById("output").innerHTML = hasil;
    }
  </script>
</body>
</html>
