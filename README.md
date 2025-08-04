<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>MSME Finance Web-Based</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --pink-primary: #ff69b4;
      --pink-dark: #cc0066;
      --pink-light: #ffc0cb;
      --pink-bg: #fff0f5;
      --pink-shadow: rgba(255, 105, 180, 0.2);
    }
    
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background-color: #fff5f9;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .container {
      background: white;
      border-radius: 16px;
      box-shadow: 0 10px 30px var(--pink-shadow);
      width: 90%;
      max-width: 800px;
      padding: 40px;
      border: 1px solid rgba(255, 192, 203, 0.3);
    }
    
    h1 {
      text-align: center;
      font-size: 2.5rem;
      margin-bottom: 25px;
      color: var(--pink-dark);
      font-family: 'Playfair Display', serif;
      position: relative;
    }
    
    h1:after {
      content: "";
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 80px;
      height: 3px;
      background: var(--pink-primary);
      border-radius: 2px;
    }
    
    .form-group {
      margin-bottom: 20px;
    }
    
    label {
      font-weight: 600;
      display: block;
      margin-bottom: 8px;
      color: var(--pink-dark);
    }
    
    input {
      width: 100%;
      padding: 12px 16px;
      border-radius: 8px;
      border: 1px solid var(--pink-light);
      background-color: rgba(255, 248, 250, 0.5);
      font-size: 1rem;
      color: #4d003b;
      transition: all 0.3s ease;
    }
    
    input:focus {
      border-color: var(--pink-primary);
      outline: none;
      box-shadow: 0 0 0 3px rgba(255, 105, 180, 0.1);
    }
    
    small {
      color: #99004d;
      font-size: 0.85rem;
      opacity: 0.8;
    }
    
    button {
      background: var(--pink-primary);
      border: none;
      color: white;
      padding: 14px;
      font-size: 1rem;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
      display: block;
      width: 100%;
      font-weight: 600;
      transition: background 0.3s;
    }
    
    button:hover {
      background: var(--pink-dark);
    }
    
    .output {
      margin-top: 30px;
      background: var(--pink-bg);
      padding: 20px;
      border-radius: 12px;
      border: 1px solid rgba(255, 192, 203, 0.5);
    }
    
    .output h3 {
      margin-bottom: 15px;
      color: var(--pink-dark);
      font-size: 1.3rem;
    }
    
    .tax-info {
      font-size: 0.9rem;
      color: #666;
      margin-top: 5px;
      font-style: italic;
    }
    
    .result-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 15px;
      margin-top: 15px;
    }
    
    .result-box {
      background: white;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid rgba(255, 192, 203, 0.3);
    }
    
    .result-box h4 {
      margin: 0 0 8px 0;
      color: var(--pink-primary);
      font-size: 1rem;
    }
    
    @media (max-width: 600px) {
      .result-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>BizWis 💖</h1>

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
      <small>Target keuntungan bersih yang ingin dicapai</small>
    </div>

    <div class="form-group">
      <label for="darurat">Dana Darurat</label>
      <input type="text" id="darurat" placeholder="Contoh: 1.000.000">
      <small>Jumlah yang disisihkan untuk keadaan darurat</small>
    </div>

    <button onclick="hitung()">Hitung 📊</button>

    <div class="output" id="output" style="display:none;">
      <h3>Hasil Simulasi:</h3>
      <div class="result-grid">
        <div class="result-box">
          <h4>Sebelum Pajak</h4>
          <div id="result-before-tax"></div>
        </div>
        <div class="result-box">
          <h4>Setelah Pajak UMKM (0.5%)</h4>
          <div id="result-after-tax"></div>
          <p class="tax-info">*Pajak dihitung dari penghasilan bulanan</p>
        </div>
      </div>
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

      // Perhitungan sebelum pajak
      const totalBiaya = fixed + cicilan + laba + darurat;
      const sisa = income - totalBiaya;
      
      // Perhitungan pajak UMKM 0.5%
      const pajak = income * 0.005;
      const sisaSetelahPajak = sisa - pajak;

      // Hasil sebelum pajak
      let rekomendasi = '';
      if (sisa > 0) {
        rekomendasi = `Keuangan sehat! Sisa: ${formatRupiah(sisa)}`;
      } else if (sisa < 0) {
        rekomendasi = `Perhatian! Defisit: ${formatRupiah(Math.abs(sisa))}`;
      } else {
        rekomendasi = `Break even (impas)`;
      }

      // Hasil setelah pajak
      let rekomendasiPajak = '';
      if (sisaSetelahPajak > 0) {
        rekomendasiPajak = `Sisa setelah pajak: ${formatRupiah(sisaSetelahPajak)}`;
      } else if (sisaSetelahPajak < 0) {
        rekomendasiPajak = `Defisit setelah pajak: ${formatRupiah(Math.abs(sisaSetelahPajak))}`;
      } else {
        rekomendasiPajak = `Break even setelah pajak`;
      }

      document.getElementById('output').style.display = 'block';
      document.getElementById('result-before-tax').innerHTML = `
        <p><b>Total Pengeluaran:</b> ${formatRupiah(totalBiaya)}</p>
        <p><b>Sisa Penghasilan:</b> ${formatRupiah(sisa)}</p>
        <p><b>Rekomendasi:</b> ${rekomendasi}</p>
      `;
      
      document.getElementById('result-after-tax').innerHTML = `
        <p><b>Pajak UMKM:</b> ${formatRupiah(pajak)}</p>
        <p><b>Sisa Penghasilan:</b> ${formatRupiah(sisaSetelahPajak)}</p>
        <p><b>Rekomendasi:</b> ${rekomendasiPajak}</p>
      `;
    }
  </script>
</body>
</html>
