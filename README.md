<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>BizWis - Simulasi Keuangan UMKM</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary-pink: #ff69b4;
      --light-pink: #ffe4f1;
      --medium-pink: #ffb6c1;
      --dark-pink: #d63384;
      --accent-pink: #ff1493;
      --text-dark: #5d0064;
      --text-light: #a0528d;
      --success: #4caf50;
      --danger: #f44336;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff0f5, #ffe4f1, #ffd1e3);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      color: var(--text-dark);
    }

    .container {
      width: 100%;
      max-width: 800px;
      background: #fff;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 10px 30px rgba(214, 51, 132, 0.2);
      border: 1px solid var(--light-pink);
    }

    h1 {
      text-align: center;
      color: var(--dark-pink);
      margin-bottom: 20px;
      font-size: 2rem;
    }

    .form-group {
      margin-bottom: 20px;
    }

    label {
      font-weight: 600;
      margin-bottom: 6px;
      display: block;
    }

    input {
      width: 100%;
      padding: 12px 16px;
      border-radius: 12px;
      border: 2px solid var(--light-pink);
      font-size: 1rem;
    }

    input:focus {
      border-color: var(--primary-pink);
      outline: none;
      box-shadow: 0 0 0 2px rgba(255, 105, 180, 0.2);
    }

    small {
      color: var(--text-light);
      display: block;
      margin-top: 4px;
      font-size: 0.85rem;
      font-style: italic;
    }

    button {
      background: linear-gradient(135deg, var(--primary-pink), var(--dark-pink));
      color: #fff;
      border: none;
      border-radius: 30px;
      padding: 14px 30px;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      width: 100%;
      margin-top: 20px;
    }

    button:hover {
      box-shadow: 0 6px 16px rgba(255, 105, 180, 0.3);
    }

    .hasil {
      margin-top: 30px;
      background: #fff0f8;
      padding: 20px;
      border-radius: 15px;
      border: 1px solid var(--light-pink);
    }

    .hasil h3 {
      color: var(--dark-pink);
      margin-bottom: 15px;
      font-size: 1.3rem;
    }

    .hasil p {
      margin: 8px 0;
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
  </style>
</head>
<body>
  <div class="container">
    <h1><i class="fas fa-store"></i> BizWis - Simulasi UMKM</h1>

    <div class="form-group">
      <label for="penghasilan">Penghasilan Bulanan (Rp)</label>
      <input type="text" id="penghasilan" placeholder="contoh: 10.000.000">
      <small>Uang yang kamu terima dari hasil jualan setiap bulan</small>
    </div>

    <div class="form-group">
      <label for="biaya">Biaya Tetap (Rp)</label>
      <input type="text" id="biaya" placeholder="contoh: 3.000.000">
      <small>Biaya rutin seperti sewa, listrik, air, kuota, bahan baku</small>
    </div>

    <div class="form-group">
      <label for="gaji">Gaji Pegawai (Rp)</label>
      <input type="text" id="gaji" placeholder="contoh: 1.500.000">
      <small>Total gaji karyawan setiap bulan</small>
    </div>

    <div class="form-group">
      <label for="cicilan">Cicilan Usaha (Rp)</label>
      <input type="text" id="cicilan" placeholder="contoh: 500.000">
      <small>Cicilan alat, motor, utang bank, dll</small>
    </div>

    <div class="form-group">
      <label for="target">Target Laba Bersih (%)</label>
      <input type="number" id="target" placeholder="contoh: 20">
      <small>Berapa persen kamu ingin untung dari penghasilan (misal 20%)</small>
    </div>

    <div class="form-group">
      <label for="darurat">Dana Darurat (%)</label>
      <input type="number" id="darurat" placeholder="contoh: 10">
      <small>Tabungan darurat dari laba bersih, misalnya 10%</small>
    </div>

    <button onclick="hitung()">Hitung Sekarang</button>

    <div class="hasil" id="output">
      <h3>Hasil Perhitungan Akan Muncul di Sini</h3>
    </div>
  </div>

  <script>
    function formatRupiah(angka) {
      return angka.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    }

    function parseRupiah(str) {
      return parseInt(str.replaceAll('.', '').replace(',', '')) || 0;
    }

    document.querySelectorAll('input[type="text"]').forEach(input => {
      input.addEventListener('input', function (e) {
        let value = this.value.replace(/\./g, '').replace(/[^\d]/g, '');
        this.value = formatRupiah(value);
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
        <small>Jumlah seluruh pengeluaran rutin tiap bulan</small>

        <p><strong>Laba Kotor:</strong> Rp ${formatRupiah(labaKotor)}</p>
        <small>Penghasilan dikurangi total pengeluaran</small>

        <p><strong>Dana Darurat:</strong> Rp ${formatRupiah(danaDarurat)}</p>
        <small>Cadangan untuk keperluan mendadak</small>

        <p><strong>Laba Bersih:</strong> Rp ${formatRupiah(labaBersih)}</p>
        <small>Uang keuntungan setelah sisihkan darurat</small>

        <p><strong>Target Laba:</strong> Rp ${formatRupiah(targetLaba)}</p>
        <small>Laba minimal yang kamu harapkan</small>
      `;

      if (labaBersih >= targetLaba) {
        hasil += `<p class="success">✅ Selamat! Laba kamu sudah sesuai target 💖</p>`;
      } else {
        hasil += `<p class="danger">⚠️ Wah, belum sesuai target. Coba kurangi biaya atau tingkatkan penjualan!</p>`;
      }

      document.getElementById("output").innerHTML = hasil;
    }
  </script>
</body>
</html>
