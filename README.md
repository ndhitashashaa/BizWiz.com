<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BRizz✨</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Libre+Baskerville:wght@700&family=Inter:wght@500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --pink-primary: #ff69b4;
      --pink-dark: #c2185b;
      --pink-light: #ffd6e8;
      --pink-bg: #fff0f5;
      --pink-shadow: rgba(255, 105, 180, 0.25);
      --text-dark: #2c001e;
      --white: #fff;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(to right bottom, #ffe8f4, #fff0f5);
      color: var(--text-dark);
      transition: all 0.5s ease-in-out;
    }

    header {
      padding: 100px 30px 80px;
      text-align: center;
      background: linear-gradient(135deg, #fff0f5 30%, #ffd6e8);
      box-shadow: inset 0 0 80px rgba(255, 182, 193, 0.3);
      animation: fadeIn 1s ease-in-out;
    }

    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(-30px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    header h1 {
      font-family: 'Libre Baskerville', serif;
      font-size: 4rem;
      font-weight: 700;
      color: var(--pink-dark);
      margin-bottom: 20px;
    }

    header p {
      font-family: 'Inter', sans-serif;
      font-size: 1.25rem;
      color: #5a0b3f;
      max-width: 700px;
      margin: 0 auto;
    }

    .main {
      background: var(--white);
      margin: -60px auto 60px;
      border-radius: 30px;
      padding: 60px;
      max-width: 960px;
      width: 90%;
      box-shadow: 0 20px 50px var(--pink-shadow);
      border: 2px solid var(--pink-light);
    }

    h2 {
      font-family: 'Libre Baskerville', serif;
      font-size: 2.2rem;
      text-align: center;
      color: var(--pink-dark);
      margin-bottom: 40px;
    }

    .form-group {
      margin-bottom: 24px;
    }

    label {
      font-weight: 700;
      font-size: 1.05rem;
      display: block;
      margin-bottom: 10px;
      color: var(--pink-dark);
    }

    input, select {
      width: 100%;
      padding: 14px 20px;
      border-radius: 12px;
      border: 1.8px solid var(--pink-light);
      background-color: rgba(255, 245, 247, 0.9);
      font-size: 1rem;
      color: #4d003b;
      font-family: 'Inter', sans-serif;
    }

    input:focus, select:focus {
      outline: none;
      border-color: var(--pink-primary);
      box-shadow: 0 0 0 4px rgba(255, 105, 180, 0.15);
    }

    small {
      color: #8a004a;
      font-size: 0.85rem;
      opacity: 0.75;
    }

    button {
      background: var(--pink-primary);
      border: none;
      color: var(--white);
      padding: 18px;
      font-size: 1.15rem;
      border-radius: 14px;
      cursor: pointer;
      width: 100%;
      margin-top: 30px;
      font-weight: 700;
      font-family: 'Inter', sans-serif;
      transition: background 0.3s, transform 0.2s;
    }

    button:hover {
      background: var(--pink-dark);
      transform: scale(1.02);
    }

    .output {
      margin-top: 50px;
      background: var(--pink-bg);
      padding: 35px;
      border-radius: 20px;
      border: 1.5px solid rgba(255, 192, 203, 0.5);
    }

    .output h3 {
      margin-bottom: 25px;
      color: var(--pink-dark);
      font-size: 1.5rem;
      font-family: 'Libre Baskerville', serif;
    }

    .result-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 30px;
    }

    .result-box {
      background: white;
      padding: 24px;
      border-radius: 16px;
      border: 1.5px solid rgba(255, 192, 203, 0.4);
      box-shadow: 0 10px 20px rgba(255, 182, 193, 0.2);
    }

    .result-box h4 {
      margin-bottom: 14px;
      color: var(--pink-primary);
      font-size: 1.1rem;
      font-family: 'Inter', sans-serif;
    }

    .tax-info {
      font-size: 0.9rem;
      color: #666;
      font-style: italic;
      margin-top: 12px;
    }

    @media (max-width: 768px) {
      .result-grid {
        grid-template-columns: 1fr;
      }

      header h1 {
        font-size: 2.6rem;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>BRizz✨</h1>
    <p>MSME Finance Web-Based</p>
  </header>

  <section class="main">
    <h2>Finance Simulator</h2>

    <div class="form-group">
      <label for="jenisUsaha">Jenis Subjek Pajak</label>
      <select id="jenisUsaha">
        <option value="perorangan">Perorangan</option>
        <option value="badan">Badan Usaha</option>
        <option value="karyawan">Karyawan dengan Usaha Sampingan</option>
      </select>
      <small>Pilih status sesuai dengan bentuk usaha Anda</small>
    </div>

    <div class="form-group">
      <label for="income">Penghasilan Bruto Bulanan</label>
      <input type="text" id="income" placeholder="Contoh: 10.000.000">
      <small>Total semua pemasukan kotor sebelum biaya</small>
    </div>

    <div class="form-group">
      <label for="fixed">Biaya Operasional</label>
      <input type="text" id="fixed" placeholder="Contoh: 2.000.000">
      <small>Sewa, gaji pegawai, listrik, internet, dll</small>
    </div>

    <div class="form-group">
      <label for="laba">Target Laba Bersih</label>
      <input type="text" id="laba" placeholder="Contoh: 1.500.000">
      <small>Keuntungan bersih yang ingin dicapai</small>
    </div>

    <button onclick="hitung()">Hitung Pajak & Laba</button>

    <div class="output" id="output" style="display:none;">
      <h3>Hasil Simulasi:</h3>
      <div class="result-grid">
        <div class="result-box">
          <h4>Total Pengeluaran</h4>
          <div id="result-before-tax"></div>
        </div>
        <div class="result-box">
          <h4>Pajak UMKM Sesuai Kategori</h4>
          <div id="result-after-tax"></div>
          <p class="tax-info" id="tax-note"></p>
        </div>
      </div>
    </div>
  </section>

  <script>
    function toAngka(str) {
      return parseFloat(str.replace(/\./g, '').replace(',', '.')) || 0;
    }

    function formatRupiah(angka) {
      return angka.toLocaleString('id-ID', { style: 'currency', currency: 'IDR' });
    }

    function hitung() {
      const jenis = document.getElementById('jenisUsaha').value;
      const income = toAngka(document.getElementById('income').value);
      const biaya = toAngka(document.getElementById('fixed').value);
      const laba = toAngka(document.getElementById('laba').value);
      const totalBiaya = biaya + laba;
      const sisa = income - totalBiaya;

      let tarif = 0.005;
      let note = '*Tarif pajak final 0.5% dari penghasilan bruto (sesuai PP 23/2018).';

      if (jenis === 'badan') {
        tarif = 0.01;
        note = '*Badan Usaha (CV/PT) dengan omzet < 4.8M: tarif 1% final sesuai regulasi lama.';
      } else if (jenis === 'karyawan') {
        tarif = 0.005;
        note = '*Usaha sampingan dengan NPWP aktif tetap dapat tarif 0.5% (PP 23).';
      }

      const pajak = income * tarif;
      const labaSetelahPajak = sisa - pajak;

      document.getElementById('output').style.display = 'block';
      document.getElementById('result-before-tax').innerHTML = `
        <p><b>Penghasilan Bruto:</b> ${formatRupiah(income)}</p>
        <p><b>Total Biaya + Laba Target:</b> ${formatRupiah(totalBiaya)}</p>
        <p><b>Sisa Usaha:</b> ${formatRupiah(sisa)}</p>
      `;
      document.getElementById('result-after-tax').innerHTML = `
        <p><b>Pajak:</b> ${formatRupiah(pajak)}</p>
        <p><b>Laba Setelah Pajak:</b> ${formatRupiah(labaSetelahPajak)}</p>
      `;
      document.getElementById('tax-note').textContent = note;
    }
  </script>
</body>
</html>
