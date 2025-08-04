<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>BizWis - MSME Finance Web-Based</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Playfair Display', serif;
      background-image: url('https://i.ibb.co/XV35Z0c/pink-bg.jpg');
      background-size: cover;
      background-attachment: fixed;
      background-position: center;
      background-repeat: no-repeat;
      color: #4d003b;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .container {
      background: rgba(255, 240, 250, 0.95);
      border-radius: 20px;
      box-shadow: 0 15px 30px rgba(255, 105, 180, 0.25);
      width: 90%;
      max-width: 800px;
      padding: 30px;
      backdrop-filter: blur(10px);
    }
    h1 {
      text-align: center;
      font-size: 2.6rem;
      margin-bottom: 15px;
      color: #cc0066;
      text-shadow: 1px 1px 2px #ffccdd;
    }
    .form-group {
      margin-bottom: 20px;
    }
    label {
      font-weight: bold;
      display: block;
      margin-bottom: 6px;
    }
    input {
      width: 100%;
      padding: 12px;
      border-radius: 10px;
      border: 2px solid #ffc0cb;
      background-color: #fff8fa;
      font-size: 1rem;
      color: #333;
    }
    input:focus {
      border-color: #ff69b4;
      outline: none;
      box-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
    }
    small {
      color: #99004d;
      font-size: 0.85rem;
    }
    button {
      background: linear-gradient(145deg, #ff69b4, #ff1493);
      border: none;
      color: white;
      padding: 14px 30px;
      font-size: 1rem;
      border-radius: 40px;
      cursor: pointer;
      box-shadow: 0 8px 16px rgba(255, 105, 180, 0.4);
      margin-top: 20px;
      display: block;
      width: 100%;
    }
    button:hover {
      background: linear-gradient(145deg, #ff1493, #ff69b4);
      transform: scale(1.02);
    }
    .output {
      margin-top: 30px;
      background: #fff0f5;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(255, 182, 193, 0.2);
    }
    .output h3 {
      margin-bottom: 15px;
      color: #b30059;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>BizWis 💼✨</h1>

    <div class="form-group">
      <label for="income">Penghasilan Bulanan</label>
      <input type="text" id="income" placeholder="Contoh: 10.000.000">
      <small>Total semua pemasukan tetap setiap bulan</small>
    </div>

    <div class="form-group">
      <label for="fixed">Biaya Tetap</label>
      <input type="text" id="fixed" placeholder="Contoh: 2.000.000">
      <small>Biaya sewa, gaji pegawai, internet, dan listrik</small>
    </div>

    <div class="form-group">
      <label for="cicilan">Cicilan Usaha</label>
      <input type="text" id="cicilan" placeholder="Contoh: 1.500.000">
      <small>Angsuran modal usaha: pinjaman bank, koperasi, dll</small>
    </div>

    <div class="form-group">
      <label for="laba">Target Laba Bersih</label>
      <input type="text" id="laba" placeholder="Contoh: 1.500.000">
      <small>Target keuntungan bersih yang ingin dicapai. Misal: dari 10jt omzet, ingin bersih 15% (1.500.000)</small>
    </div>

    <div class="form-group">
      <label for="darurat">Dana Darurat</label>
      <input type="text" id="darurat" placeholder="Contoh: 1.000.000">
      <small>Jumlah yang disisihkan untuk keadaan darurat, sebaiknya 10–20% dari penghasilan</small>
    </div>

    <button onclick="hitung()">Hitung 📊</button>

    <div class="output" id="output" style="display:none;">
      <h3>Hasil Simulasi:</h3>
      <div id="result-detail"></div>
    </div>
  </div>

  <script>
    function toAngka(str) {
      return parseFloat(str.replace(/\./g, '').replace(',', '.')) || 0;
    }

    function formatRupiah(angka) {
      return angka.toLocaleString('id-ID', { style: 'currency', currency: 'IDR' });
    }

    function hitung() {
      const income = toAngka(document.getElementById('income').value);
      const fixed = toAngka(document.getElementById('fixed').value);
      const cicilan = toAngka(document.getElementById('cicilan').value);
      const laba = toAngka(document.getElementById('laba').value);
      const darurat = toAngka(document.getElementById('darurat').value);

      const totalBiaya = fixed + cicilan + laba + darurat;
      const sisa = income - totalBiaya;

      let rekomendasi = '';
      if (sisa > 0) {
        rekomendasi = `Keuangan sehat! Kamu masih punya sisa ${formatRupiah(sisa)}. Bisa dialokasikan untuk investasi atau pengembangan usaha.`;
      } else if (sisa < 0) {
        rekomendasi = `Oops! Kamu kekurangan ${formatRupiah(Math.abs(sisa))}. Kurangi beban atau tambah penghasilan.`;
      } else {
        rekomendasi = `Kamu berada di titik impas. Tidak rugi, tapi juga belum untung.`;
      }

      document.getElementById('output').style.display = 'block';
      document.getElementById('result-detail').innerHTML = `
        <p><b>Total Pengeluaran (Biaya Tetap + Cicilan + Laba + Darurat):</b><br> ${formatRupiah(totalBiaya)}</p>
        <p><b>Sisa Penghasilan:</b><br> ${formatRupiah(sisa)}</p>
        <p><b>Rekomendasi:</b><br> ${rekomendasi}</p>
      `;
    }
  </script>
</body>
</html>
