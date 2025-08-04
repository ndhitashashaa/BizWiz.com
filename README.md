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
    
    input, select {
      width: 100%;
      padding: 12px 16px;
      border-radius: 8px;
      border: 1px solid var(--pink-light);
      background-color: rgba(255, 248, 250, 0.5);
      font-size: 1rem;
      color: #4d003b;
      transition: all 0.3s ease;
    }
    
    input:focus, select:focus {
      border-color: var(--pink-primary);
      outline: none;
      box-shadow: 0 0 0 3px rgba(255, 105, 180, 0.1);
    }
    
    small {
      color: #99004d;
      font-size: 0.85rem;
      opacity: 0.8;
      display: block;
      margin-top: 5px;
    }
    
    .tax-explanation {
      background-color: var(--pink-bg);
      padding: 12px;
      border-radius: 8px;
      margin-top: 10px;
      font-size: 0.85rem;
      border-left: 3px solid var(--pink-primary);
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
    
    .result-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 15px;
      margin-top: 15px;
    }
    
    .result-box {
      background: white;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid rgba(255, 192, 203, 0.3);
    }
    
    .result-box h4 {
      margin: 0 0 10px 0;
      color: var(--pink-primary);
      font-size: 1rem;
      border-bottom: 1px dashed var(--pink-light);
      padding-bottom: 5px;
    }
    
    .recommendation {
      margin-top: 20px;
      background: white;
      padding: 15px;
      border-radius: 8px;
      border: 1px solid rgba(255, 192, 203, 0.3);
    }
    
    .recommendation h4 {
      color: var(--pink-dark);
      margin-top: 0;
    }
    
    .recommendation ul {
      padding-left: 20px;
    }
    
    .recommendation li {
      margin-bottom: 8px;
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
    <h1>BRizz</h1>

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

    <div class="form-group">
      <label for="taxType">Jenis Subjek Pajak</label>
      <select id="taxType">
        <option value="umkm">UMKM (Usaha Mikro Kecil Menengah)</option>
        <option value="karyawan">Karyawan dengan Usaha Sampingan</option>
        <option value="perorangan">Perorangan (Freelancer/Pekerja Lepas)</option>
      </select>
      <div class="tax-explanation" id="taxExplanation">
        <strong>UMKM:</strong> Wajib pajak dengan omset < Rp4,8M/tahun dikenakan pajak final 0,5%
      </div>
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
          <h4>Setelah Pajak</h4>
          <div id="result-after-tax"></div>
        </div>
      </div>
      
      <div class="recommendation" id="recommendation">
        <h4>Rekomendasi Pengembangan Usaha:</h4>
        <div id="business-recommendation"></div>
      </div>
    </div>
  </div>

  <script>
    // Penjelasan jenis pajak
    document.getElementById('taxType').addEventListener('change', function() {
      const explanations = {
        umkm: "<strong>UMKM:</strong> Wajib pajak dengan omset < Rp4,8M/tahun dikenakan pajak final 0,5% dari omset (PP 23/2018)",
        karyawan: "<strong>Karyawan dengan Usaha Sampingan:</strong> Pajak dihitung dari penghasilan usaha setelah dikurangi PTKP (Penghasilan Tidak Kena Pajak)",
        perorangan: "<strong>Perorangan/Freelancer:</strong> Dikenakan tarif progresif 0-30% sesuai UU PPh (berlaku jika omset > Rp4,8M/tahun)"
      };
      document.getElementById('taxExplanation').innerHTML = explanations[this.value];
    });

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
      const taxType = document.getElementById('taxType').value;

      // Perhitungan sebelum pajak
      const totalBiaya = fixed + cicilan + laba + darurat;
      const sisa = income - totalBiaya;
      
      // Perhitungan pajak berdasarkan jenis
      let pajak = 0;
      let taxNote = "";
      
      if (taxType === "umkm") {
        pajak = income * 0.005; // Pajak final 0.5% untuk UMKM
        taxNote = "Pajak UMKM 0.5% dari omset";
      } else if (taxType === "karyawan") {
        // Asumsi PTKP 54 juta/tahun (4.5 juta/bulan)
        const ptkp = 4500000;
        const taxable = Math.max(0, income - ptkp);
        pajak = taxable * 0.05; // Asumsi tarif 5% untuk lapisan pertama
        taxNote = "Pajak 5% dari (penghasilan - PTKP)";
      } else { // perorangan
        // Asumsi tarif progresif lapisan pertama
        pajak = income * 0.05; // 5% untuk lapisan pertama
        taxNote = "Pajak progresif (asumsi tarif 5%)";
      }
      
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

      // Rekomendasi pengembangan usaha
      let businessRecommendation = '';
      if (sisaSetelahPajak > income * 0.3) {
        businessRecommendation = `
          <ul>
            <li><strong>Ekspansi usaha:</strong> Pertimbangkan untuk membuka cabang baru atau menambah produk/jasa</li>
            <li><strong>Investasi peralatan:</strong> Tingkatkan produktivitas dengan peralatan yang lebih modern</li>
            <li><strong>Digital marketing:</strong> Alokasikan dana untuk iklan digital (Google Ads, Instagram Ads)</li>
          </ul>
        `;
      } else if (sisaSetelahPajak > 0) {
        businessRecommendation = `
          <ul>
            <li><strong>Optimalisasi biaya:</strong> Cari supplier dengan harga lebih kompetitif</li>
            <li><strong>Pelatihan SDM:</strong> Tingkatkan keterampilan karyawan untuk efisiensi</li>
            <li><strong>Diversifikasi produk:</strong> Tambahkan varian produk dengan modal minimal</li>
          </ul>
        `;
      } else {
        businessRecommendation = `
          <ul>
            <li><strong>Restrukturisasi utang:</strong> Negosiasikan ulang cicilan dengan bank/kreditor</li>
            <li><strong>Fokus produk unggulan:</strong> Kurangi varian produk yang kurang menguntungkan</li>
            <li><strong>Bantuan pemerintah:</strong> Manfaatkan program KUR atau bantuan UMKM</li>
          </ul>
        `;
      }

      // Tampilkan hasil
      document.getElementById('output').style.display = 'block';
      document.getElementById('result-before-tax').innerHTML = `
        <p><b>Total Pengeluaran:</b> ${formatRupiah(totalBiaya)}</p>
        <p><b>Sisa Penghasilan:</b> ${formatRupiah(sisa)}</p>
        <p><b>Status:</b> ${rekomendasi}</p>
      `;
      
      document.getElementById('result-after-tax').innerHTML = `
        <p><b>Jenis Pajak:</b> ${taxNote}</p>
        <p><b>Beban Pajak:</b> ${formatRupiah(pajak)}</p>
        <p><b>Sisa Penghasilan:</b> ${formatRupiah(sisaSetelahPajak)}</p>
        <p><b>Status:</b> ${rekomendasiPajak}</p>
      `;
      
      document.getElementById('business-recommendation').innerHTML = businessRecommendation;
    }
  </script>
</body>
</html>
