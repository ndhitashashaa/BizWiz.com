<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>BizWis - Simulasi Inflasi & Pajak UMKM</title>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
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
      --warning: #ff9800;
      --danger: #f44336;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff0f5, #ffe4f1, #ffd1e3);
      min-height: 100vh;
      padding: 20px;
      display: flex;
      justify-content: center;
      align-items: center;
      color: var(--text-dark);
    }
    .container {
      max-width: 800px;
      width: 100%;
      background: rgba(255, 255, 255, 0.95);
      border-radius: 20px;
      box-shadow: 0 15px 35px rgba(214, 51, 132, 0.2);
      border: 1px solid rgba(255, 182, 193, 0.5);
      overflow: hidden;
      position: relative;
    }
    .header {
      background: linear-gradient(135deg, var(--dark-pink), var(--accent-pink));
      padding: 30px 20px;
      text-align: center;
      position: relative;
    }
    .header::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none"><path d="M0,0 C30,0 50,30 100,30 L100,100 L0,100 Z" fill="rgba(255,255,255,0.15)"/></svg>');
      background-size: cover;
    }
    h1 {
      font-family: 'Nunito', sans-serif;
      font-weight: 800;
      font-size: 2.5rem;
      color: white;
      z-index: 1;
      position: relative;
    }
    h1 i { margin: 0 10px; animation: pulse 2s infinite; }
    .subtitle {
      font-size: 1.1rem;
      color: rgba(255, 255, 255, 0.9);
      margin-top: 10px;
      font-weight: 300;
      z-index: 1;
      position: relative;
    }
    .content { padding: 30px; }
    .form-group { margin-bottom: 20px; }
    label {
      display: block;
      margin-bottom: 8px;
      font-weight: 500;
      color: var(--text-dark);
    }
    .input-with-icon { position: relative; }
    .input-with-icon i {
      position: absolute;
      left: 15px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--medium-pink);
    }
    input, select {
      width: 100%;
      padding: 14px 20px 14px 45px;
      border-radius: 12px;
      border: 2px solid var(--light-pink);
      background: rgba(255, 182, 193, 0.1);
      font-size: 1rem;
      color: var(--text-dark);
    }
    input:focus, select:focus {
      outline: none;
      border-color: var(--primary-pink);
      box-shadow: 0 0 0 3px rgba(255, 105, 180, 0.2);
    }
    small {
      display: block;
      margin-top: 5px;
      color: var(--text-light);
      font-size: 0.85rem;
      font-style: italic;
    }
    .btn-container { text-align: center; margin: 25px 0; }
    button {
      background: linear-gradient(135deg, var(--primary-pink), var(--dark-pink));
      color: white;
      border: none;
      border-radius: 50px;
      padding: 16px 40px;
      font-size: 1.1rem;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 6px 15px rgba(214, 51, 132, 0.3);
    }
    button:hover {
      transform: translateY(-3px);
      box-shadow: 0 10px 20px rgba(214, 51, 132, 0.4);
    }
    .hasil {
      background: linear-gradient(135deg, rgba(255, 105, 180, 0.08), rgba(255, 182, 193, 0.12));
      padding: 25px;
      border-radius: 15px;
      margin-top: 20px;
    }
    .hasil-title {
      font-size: 1.4rem;
      color: var(--dark-pink);
      margin-bottom: 15px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .result-item {
      display: flex;
      justify-content: space-between;
      padding: 12px 0;
    }
    .result-label { font-weight: 500; }
    .result-value { font-weight: 600; color: var(--dark-pink); }
    .recommendation {
      margin-top: 20px;
      padding: 15px;
      border-radius: 10px;
      font-weight: 500;
    }
    .profit {
      background: rgba(76, 175, 80, 0.1);
      border-left: 4px solid var(--success);
      color: var(--success);
    }
    .loss {
      background: rgba(244, 67, 54, 0.1);
      border-left: 4px solid var(--danger);
      color: var(--danger);
    }
    .footer {
      text-align: center;
      padding: 20px;
      font-size: 0.9rem;
      border-top: 1px solid rgba(255, 182, 193, 0.3);
      background: rgba(255, 255, 255, 0.7);
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1><i class="fas fa-calculator"></i> BizWis <i class="fas fa-chart-line"></i></h1>
      <p class="subtitle">Simulasi Inflasi & Pajak UMKM untuk Bisnismu</p>
    </div>
    <div class="content">
      <div class="form-group">
        <label for="penghasilan"><i class="fas fa-money-bill-wave"></i> Penghasilan per Bulan (Rp)</label>
        <div class="input-with-icon">
          <i class="fas fa-wallet"></i>
          <input type="number" id="penghasilan" placeholder="Masukkan penghasilan bulanan">
        </div>
        <small>Contoh: 5000000 (tanpa titik/koma)</small>
      </div>
      <div class="form-group">
        <label for="biaya"><i class="fas fa-receipt"></i> Total Biaya Bulanan (Rp)</label>
        <div class="input-with-icon">
          <i class="fas fa-file-invoice-dollar"></i>
          <input type="number" id="biaya" placeholder="Masukkan total biaya">
        </div>
        <small>Contoh: 3500000 (tanpa titik/koma)</small>
      </div>
      <div class="form-group">
        <label for="inflasi"><i class="fas fa-chart-line"></i> Tingkat Inflasi (%)</label>
        <div class="input-with-icon">
          <i class="fas fa-percentage"></i>
          <input type="number" id="inflasi" placeholder="Contoh: 3 untuk 3%">
        </div>
        <small>Cara hitung: 3% dari biaya = biaya x 0.03</small>
      </div>
      <div class="form-group">
        <label for="tipe"><i class="fas fa-sync-alt"></i> Tipe Inflasi</label>
        <div class="input-with-icon">
          <i class="fas fa-calendar-alt"></i>
          <select id="tipe">
            <option value="bulanan">Bulanan</option>
            <option value="harian">Harian</option>
          </select>
        </div>
        <small><i class="fas fa-info-circle"></i> Bulanan: langsung. Harian: kalikan % dengan 30 dulu ya~</small>
      </div>
      <div class="btn-container">
        <button onclick="hitung()">
          <i class="fas fa-calculator"></i> Hitung Sekarang
        </button>
      </div>
      <div class="hasil" id="output">
        <h2 class="hasil-title"><i class="fas fa-chart-pie"></i> Hasil Perhitungan</h2>
        <p style="text-align: center; color: var(--text-light);">Isi formulir di atas dan klik "Hitung Sekarang"</p>
      </div>
    </div>
    <div class="footer">
      <p><i class="fas fa-heart"></i> BizWis - Simulasi UMKM | © 2023</p>
    </div>
  </div>
<script>
function hitung() {
  const penghasilan = parseFloat(document.getElementById("penghasilan").value);
  const biaya = parseFloat(document.getElementById("biaya").value);
  const inflasi = parseFloat(document.getElementById("inflasi").value) / 100;
  const tipe = document.getElementById("tipe").value;
  if (isNaN(penghasilan) || isNaN(biaya) || isNaN(inflasi)) {
    alert("🌸 Mohon isi semua kolom dengan benar yaa, bestie!");
    return;
  }
  if (penghasilan < 0 || biaya < 0 || inflasi < 0) {
    alert("🌸 Nilai tidak boleh negatif, bestie!");
    return;
  }
  let inflasi_adjust = (tipe === "harian") ? inflasi * 30 : inflasi;
  const biaya_akhir = biaya + (biaya * inflasi_adjust);
  const laba_kotor = penghasilan - biaya_akhir;
  const pajak = penghasilan * 0.005;
  const laba_bersih = laba_kotor - pajak;
  const break_even = biaya_akhir;
  const format = n => new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(n);
  let out = `
    <h2 class='hasil-title'><i class='fas fa-chart-pie'></i> Hasil Perhitungan</h2>
    <div class='result-item'><div class='result-label'><i class='fas fa-money-bill-wave'></i> Biaya setelah Inflasi</div><div class='result-value'>${format(biaya_akhir)}</div></div>
    <small>Biaya awal + inflasi total</small>
    <div class='result-item'><div class='result-label'><i class='fas fa-chart-line'></i> Laba Kotor</div><div class='result-value'>${format(laba_kotor)}</div></div>
    <small>Penghasilan - biaya akhir</small>
    <div class='result-item'><div class='result-label'><i class='fas fa-file-invoice'></i> Pajak UMKM 0.5%</div><div class='result-value'>${format(pajak)}</div></div>
    <small>0.5% dari penghasilan</small>
    <div class='result-item'><div class='result-label'><i class='fas fa-coins'></i> Laba Bersih</div><div class='result-value'>${format(laba_bersih)}</div></div>
    <small>Laba kotor dikurangi pajak</small>
    <div class='result-item'><div class='result-label'><i class='fas fa-balance-scale'></i> Break Even Point</div><div class='result-value'>${format(break_even)}</div></div>
    <small>Penghasilan minimum agar tidak rugi</small>
  `;
  out += laba_bersih <= 0 ? `<div class='recommendation loss'><i class='fas fa-exclamation-triangle'></i> Rugi! Kurangi biaya atau naikkan harga~</div>` : `<div class='recommendation profit'><i class='fas fa-check-circle'></i> Untung! Pertahankan strategi kamu 🎉</div>`;
  document.getElementById("output").innerHTML = out;
}
</script>
</body>
</html>
