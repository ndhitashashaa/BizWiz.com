<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>BizWis - MSME Finance Web-Based</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --pink-primary: #ff69b4;
      --pink-dark: #cc0066;
      --pink-light: #ffc0cb;
      --pink-bg: #fff0f5;
      --pink-shadow: rgba(255, 105, 180, 0.3);
    }
    
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ffcce6 0%, #ffb3d9 100%);
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      perspective: 1000px;
    }
    
    .container {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 24px;
      box-shadow: 
        0 10px 30px var(--pink-shadow),
        0 0 0 1px rgba(255, 255, 255, 0.3) inset;
      width: 90%;
      max-width: 800px;
      padding: 40px;
      backdrop-filter: blur(12px);
      transform-style: preserve-3d;
      transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      border: 1px solid rgba(255, 255, 255, 0.5);
    }
    
    .container:hover {
      transform: translateY(-5px) rotateX(1deg);
      box-shadow: 
        0 15px 35px var(--pink-shadow),
        0 0 0 1px rgba(255, 255, 255, 0.4) inset;
    }
    
    h1 {
      text-align: center;
      font-size: 2.8rem;
      margin-bottom: 25px;
      color: var(--pink-dark);
      font-family: 'Playfair Display', serif;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.05);
      position: relative;
      display: inline-block;
      width: 100%;
    }
    
    h1:after {
      content: "";
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 100px;
      height: 4px;
      background: linear-gradient(90deg, var(--pink-primary), #ff8fab);
      border-radius: 2px;
    }
    
    .form-group {
      margin-bottom: 25px;
      position: relative;
    }
    
    label {
      font-weight: 600;
      display: block;
      margin-bottom: 8px;
      color: var(--pink-dark);
      font-size: 1.05rem;
    }
    
    input {
      width: 100%;
      padding: 14px 16px;
      border-radius: 12px;
      border: 2px solid var(--pink-light);
      background-color: rgba(255, 248, 250, 0.8);
      font-size: 1rem;
      color: #4d003b;
      transition: all 0.3s ease;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    }
    
    input:focus {
      border-color: var(--pink-primary);
      outline: none;
      box-shadow: 0 0 0 3px rgba(255, 105, 180, 0.2);
      background-color: white;
      transform: translateY(-2px);
    }
    
    input::placeholder {
      color: #d8a7b3;
    }
    
    small {
      color: #99004d;
      font-size: 0.85rem;
      opacity: 0.8;
      display: inline-block;
      margin-top: 5px;
    }
    
    button {
      background: linear-gradient(145deg, var(--pink-primary), #ff1493);
      border: none;
      color: white;
      padding: 16px 30px;
      font-size: 1.1rem;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 
        0 8px 20px var(--pink-shadow),
        0 4px 6px rgba(0, 0, 0, 0.05);
      margin-top: 25px;
      display: block;
      width: 100%;
      font-weight: 600;
      letter-spacing: 0.5px;
      transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      position: relative;
      overflow: hidden;
    }
    
    button:hover {
      background: linear-gradient(145deg, #ff1493, var(--pink-primary));
      transform: translateY(-3px) scale(1.02);
      box-shadow: 0 12px 25px var(--pink-shadow);
    }
    
    button:active {
      transform: translateY(1px);
    }
    
    button:after {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, rgba(255,255,255,0) 70%);
      transform: scale(0);
      transition: transform 0.5s ease;
    }
    
    button:hover:after {
      transform: scale(1);
    }
    
    .output {
      margin-top: 35px;
      background: linear-gradient(145deg, #fff, var(--pink-bg));
      padding: 25px;
      border-radius: 18px;
      box-shadow: 
        0 5px 15px rgba(255, 182, 193, 0.2),
        0 0 0 1px rgba(255, 255, 255, 0.6) inset;
      transition: all 0.5s ease;
      border: 1px solid rgba(255, 255, 255, 0.7);
    }
    
    .output h3 {
      margin-bottom: 18px;
      color: var(--pink-dark);
      font-size: 1.4rem;
      font-weight: 700;
      position: relative;
      padding-bottom: 8px;
    }
    
    .output h3:after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      width: 50px;
      height: 3px;
      background: linear-gradient(90deg, var(--pink-primary), #ff8fab);
      border-radius: 2px;
    }
    
    .output p {
      margin-bottom: 12px;
      line-height: 1.6;
    }
    
    .output b {
      color: var(--pink-dark);
    }
    
    /* 3D floating elements */
    .floating {
      animation: floating 6s ease-in-out infinite;
    }
    
    @keyframes floating {
      0% { transform: translateY(0px) rotate(0.5deg); }
      50% { transform: translateY(-10px) rotate(-0.5deg); }
      100% { transform: translateY(0px) rotate(0.5deg); }
    }
    
    /* Responsive adjustments */
    @media (max-width: 768px) {
      .container {
        padding: 30px 20px;
      }
      
      h1 {
        font-size: 2.2rem;
      }
    }
  </style>
</head>
<body>
  <div class="container floating">
    <h1>BizWis 💖✨</h1>

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
