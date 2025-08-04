<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>BizWis - Simulasi Inflasi & Pajak UMKM</title>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    /* ... [keep entire original CSS here as before] ... */
  </style>
</head>
<body>
  <div class="container">
    <!-- ... [header, form and layout as original] ... -->

    <div class="form-group">
      <label for="tipe"><i class="fas fa-sync-alt"></i> Tipe Inflasi</label>
      <div class="input-with-icon">
        <i class="fas fa-calendar-alt"></i>
        <select id="tipe">
          <option value="bulanan">Bulanan</option>
          <option value="harian">Harian</option>
        </select>
      </div>
      <small><i class="fas fa-info-circle"></i> Bulanan = inflasi per bulan. Harian = inflasi harian, kalikan dengan 30. Misal 0.1% harian → jadi 3% bulanan~</small>
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

    let inflasi_adjust = inflasi;
    let inflasi_info = "";
    if (tipe === "harian") {
      inflasi_adjust *= 30;
      inflasi_info = "(Inflasi harian dikali 30)";
    } else {
      inflasi_info = "(Inflasi bulanan langsung)";
    }

    const biaya_akhir = biaya + (biaya * inflasi_adjust);
    const laba_kotor = penghasilan - biaya_akhir;
    const pajak = penghasilan * 0.005;
    const laba_bersih = laba_kotor - pajak;
    const break_even = biaya_akhir;

    const formatter = new Intl.NumberFormat('id-ID', {
      style: 'currency', currency: 'IDR', minimumFractionDigits: 0
    });

    let output = `
      <h2 class="hasil-title"><i class="fas fa-chart-pie"></i> Hasil Perhitungan</h2>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-money-bill-wave"></i> Biaya setelah Inflasi</div>
        <div class="result-value">${formatter.format(biaya_akhir)}</div>
      </div>
      <small>Biaya naik karena inflasi yaa ${inflasi_info}</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-chart-line"></i> Laba Kotor</div>
        <div class="result-value">${formatter.format(laba_kotor)}</div>
      </div>
      <small>Penghasilan dikurangi biaya (belum kena pajak)</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-file-invoice"></i> Pajak UMKM 0.5%</div>
        <div class="result-value">${formatter.format(pajak)}</div>
      </div>
      <small>Pajak UMKM tetap 0.5% dari penghasilan</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-coins"></i> Laba Bersih</div>
        <div class="result-value">${formatter.format(laba_bersih)}</div>
      </div>
      <small>Uang yang tersisa setelah semua potongan</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-balance-scale"></i> Break Even Point</div>
        <div class="result-value">${formatter.format(break_even)}</div>
      </div>
      <small>Penghasilan minimal agar tidak rugi</small>
    `;

    if (laba_bersih <= 0) {
      output += `<div class="recommendation loss">
          <i class="fas fa-exclamation-triangle"></i> <strong>Rekomendasi:</strong> Kurangi biaya atau naikkan harga jual yaa! 💔 Masih rugi nih!
        </div>`;
    } else {
      output += `<div class="recommendation profit">
          <i class="fas fa-check-circle"></i> <strong>Rekomendasi:</strong> Bisnismu untung! 🎉 Pertahankan efisiensi dan kendalikan biaya!
        </div>`;
    }

    document.getElementById("output").innerHTML = output;
  }
</script>
</body>
</html>
