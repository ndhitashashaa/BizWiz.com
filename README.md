<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>BRizz</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #e83e8c;
      --primary-dark: #c2185b;
      --primary-light: #f8bbd0;
      --primary-bg: #fff5f9;
      --primary-shadow: rgba(232, 62, 140, 0.2);
      --success: #4caf50;
      --warning: #ff9800;
      --danger: #f44336;
      --text-dark: #212121;
      --text-medium: #424242;
      --text-light: #757575;
      --border-light: #e0e0e0;
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Montserrat', sans-serif;
      background-color: #fafafa;
      color: var(--text-dark);
      line-height: 1.7;
      padding: 0;
      background-image: linear-gradient(135deg, var(--primary-bg) 0%, #ffffff 100%);
      min-height: 100vh;
    }
    
    .container {
      max-width: 900px;
      margin: 0 auto;
      background: white;
      border-radius: 16px;
      box-shadow: 0 10px 30px var(--primary-shadow);
      overflow: hidden;
      margin-top: 40px;
      margin-bottom: 40px;
      border: 1px solid rgba(232, 62, 140, 0.1);
    }
    
    .header {
      background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
      color: white;
      padding: 30px 40px;
      text-align: center;
    }
    
    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 10px;
      letter-spacing: 0.5px;
    }
    
    .header p {
      font-weight: 300;
      opacity: 0.9;
      max-width: 600px;
      margin: 0 auto;
    }
    
    .content {
      padding: 40px;
    }
    
    .form-group {
      margin-bottom: 30px;
    }
    
    label {
      display: block;
      font-weight: 500;
      margin-bottom: 10px;
      color: var(--text-medium);
      font-size: 15px;
    }
    
    input, select {
      width: 100%;
      padding: 15px 20px;
      border: 1px solid var(--border-light);
      border-radius: 10px;
      font-size: 16px;
      transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
      background-color: #fcfcfc;
      color: var(--text-dark);
    }
    
    input:focus, select:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px var(--primary-shadow);
      background-color: white;
    }
    
    .info-text {
      font-size: 13px;
      color: var(--text-light);
      margin-top: 8px;
      line-height: 1.5;
    }
    
    button {
      background: linear-gradient(to right, var(--primary), var(--primary-dark));
      color: white;
      border: none;
      padding: 18px;
      border-radius: 10px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      width: 100%;
      transition: all 0.3s;
      margin-top: 20px;
      text-transform: uppercase;
      letter-spacing: 1px;
      box-shadow: 0 4px 15px rgba(232, 62, 140, 0.3);
    }
    
    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 20px rgba(232, 62, 140, 0.4);
    }
    
    button:active {
      transform: translateY(0);
    }
    
    .results {
      margin-top: 40px;
      display: none;
      animation: fadeIn 0.6s cubic-bezier(0.39, 0.575, 0.565, 1) both;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .result-section {
      margin-bottom: 30px;
    }
    
    .result-section h2 {
      font-family: 'Playfair Display', serif;
      color: var(--primary-dark);
      font-size: 1.5rem;
      margin-bottom: 20px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--border-light);
    }
    
    .result-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }
    
    .result-card {
      background: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
      border: 1px solid rgba(232, 62, 140, 0.1);
    }
    
    .result-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 15px;
    }
    
    .result-item:last-child {
      margin-bottom: 0;
    }
    
    .result-label {
      font-weight: 500;
      color: var(--text-medium);
      font-size: 14px;
    }
    
    .result-value {
      font-weight: 600;
      color: var(--text-dark);
      text-align: right;
    }
    
    .recommendation {
      margin-top: 40px;
      padding: 25px;
      border-radius: 10px;
      background: white;
      box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
    }
    
    .success {
      border-left: 4px solid var(--success);
      background: linear-gradient(to right, rgba(76, 175, 80, 0.05), white);
    }
    
    .warning {
      border-left: 4px solid var(--warning);
      background: linear-gradient(to right, rgba(255, 152, 0, 0.05), white);
    }
    
    .danger {
      border-left: 4px solid var(--danger);
      background: linear-gradient(to right, rgba(244, 67, 54, 0.05), white);
    }
    
    .recommendation h3 {
      font-family: 'Playfair Display', serif;
      margin-bottom: 15px;
      font-size: 1.3rem;
      color: var(--text-dark);
    }
    
    .recommendation p {
      margin-bottom: 15px;
      color: var(--text-medium);
    }
    
    .recommendation ul {
      padding-left: 20px;
      margin-bottom: 15px;
    }
    
    .recommendation li {
      margin-bottom: 10px;
      color: var(--text-medium);
      position: relative;
    }
    
    .recommendation li:before {
      content: "";
      position: absolute;
      left: -15px;
      top: 8px;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background-color: var(--primary);
    }
    
    @media (max-width: 768px) {
      .container {
        margin: 20px;
        border-radius: 12px;
      }
      
      .header {
        padding: 25px 20px;
      }
      
      h1 {
        font-size: 2rem;
      }
      
      .content {
        padding: 25px;
      }
      
      .result-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <h1>BRizz</h1>
      <p>Welcome to Shafira website</p>
    </div>
    
    <div class="content">
      <div class="form-group">
        <label for="income">Penghasilan Bruto Bulanan</label>
        <input type="text" id="income" placeholder="Contoh: 10.000.000" autocomplete="off">
        <p class="info-text">Total semua pemasukan kotor sebelum dipotong biaya apapun. Termasuk penjualan, jasa, dan pendapatan lainnya.</p>
      </div>
      
      <div class="form-group">
        <label for="fixed">Biaya Tetap Bulanan</label>
        <input type="text" id="fixed" placeholder="Contoh: 3.500.000" autocomplete="off">
        <p class="info-text">Biaya rutin yang harus dikeluarkan setiap bulan seperti sewa, gaji, listrik, internet, dan lainnya.</p>
      </div>
      
      <div class="form-group">
        <label for="profit">Target Laba Bersih Bulanan</label>
        <input type="text" id="profit" placeholder="Contoh: 2.000.000" autocomplete="off">
        <p class="info-text">Keuntungan bersih yang ingin Anda dapatkan setelah dikurangi semua biaya.</p>
      </div>
      
      <div class="form-group">
        <label for="businessType">Jenis Usaha</label>
        <select id="businessType">
          <option value="umkm">UMKM (Usaha Mikro Kecil Menengah)</option>
          <option value="perorangan">Perorangan (Freelancer/Pekerja Lepas)</option>
          <option value="badan-usaha">Badan Usaha (PT/CV/Firma)</option>
        </select>
        <p class="info-text" id="businessTypeInfo">UMKM: Omset < Rp4,8M/tahun dikenakan PPh Final 0,5%. Untuk omset > Rp4,8M/tahun dikenakan tarif normal.</p>
      </div>
      
      <button onclick="calculate()">HITUNG ANALISIS</button>
      
      <div class="results" id="results">
        <div class="result-section">
          <h2>Ringkasan Keuangan</h2>
          <div class="result-grid">
            <div class="result-card">
              <div class="result-item">
                <span class="result-label">Penghasilan Bruto:</span>
                <span class="result-value" id="grossIncome"></span>
              </div>
              <div class="result-item">
                <span class="result-label">Total Biaya Tetap:</span>
                <span class="result-value" id="totalFixedCost"></span>
              </div>
              <div class="result-item">
                <span class="result-label">Laba Kotor:</span>
                <span class="result-value" id="grossProfit"></span>
              </div>
            </div>
          </div>
        </div>
        
        <div class="result-section">
          <h2>Analisis Pajak</h2>
          <div class="result-grid">
            <div class="result-card">
              <div class="result-item">
                <span class="result-label">Jenis Pajak:</span>
                <span class="result-value" id="taxType"></span>
              </div>
              <div class="result-item">
                <span class="result-label">Tarif Pajak:</span>
                <span class="result-value" id="taxRate"></span>
              </div>
              <div class="result-item">
                <span class="result-label">Beban Pajak:</span>
                <span class="result-value" id="taxAmount"></span>
              </div>
              <div class="result-item">
                <span class="result-label">Laba Bersih Setelah Pajak:</span>
                <span class="result-value" id="netProfit"></span>
              </div>
            </div>
          </div>
        </div>
        
        <div class="recommendation" id="recommendation">
          <!-- Recommendation will be inserted here -->
        </div>
      </div>
    </div>
  </div>

  <script>
    // Format number with dots as thousand separators
    function formatNumber(input) {
      return input.replace(/\D/g, "").replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    }
    
    // Parse formatted number back to integer
    function parseNumber(formattedNumber) {
      return parseInt(formattedNumber.replace(/\./g, "")) || 0;
    }
    
    // Auto-format input fields
    document.getElementById('income').addEventListener('input', function(e) {
      this.value = formatNumber(this.value);
    });
    
    document.getElementById('fixed').addEventListener('input', function(e) {
      this.value = formatNumber(this.value);
    });
    
    document.getElementById('profit').addEventListener('input', function(e) {
      this.value = formatNumber(this.value);
    });
    
    // Update business type info
    document.getElementById('businessType').addEventListener('change', function() {
      const infoTexts = {
        'umkm': 'UMKM: Omset < Rp4,8M/tahun dikenakan PPh Final 0,5%. Untuk omset > Rp4,8M/tahun dikenakan tarif normal.',
        'perorangan': 'Perorangan: Dikenakan tarif progresif 5-30% dengan PTKP Rp54 juta/tahun. Penghasilan dihitung setelah pengurangan biaya.',
        'badan-usaha': 'Badan Usaha: Dikenakan tarif pajak badan 22% (2022) dari laba bersih. Untuk UMKM tertentu bisa dapat tarif lebih rendah.'
      };
      document.getElementById('businessTypeInfo').textContent = infoTexts[this.value];
    });
    
    // Main calculation function
    function calculate() {
      // Get input values
      const grossIncome = parseNumber(document.getElementById('income').value);
      const fixedCost = parseNumber(document.getElementById('fixed').value);
      const targetProfit = parseNumber(document.getElementById('profit').value);
      const businessType = document.getElementById('businessType').value;
      
      // Validate inputs
      if (!grossIncome || !fixedCost) {
        alert('Mohon isi penghasilan bruto dan biaya tetap terlebih dahulu');
        return;
      }
      
      // Calculate gross profit
      const grossProfit = grossIncome - fixedCost;
      
      // Calculate tax based on business type (according to klikpajak.id)
      let taxType = '';
      let taxRate = '';
      let taxAmount = 0;
      let annualIncome = grossIncome * 12;
      
      if (businessType === 'umkm') {
        if (annualIncome <= 480000000) { // UMKM with turnover < 4.8B/year
          taxType = 'PPh Final UMKM (PP 23/2018)';
          taxRate = '0,5% dari omset bruto';
          taxAmount = grossIncome * 0.005;
        } else {
          taxType = 'PPh Normal UMKM';
          taxRate = '1% dari omset bruto';
          taxAmount = grossIncome * 0.01;
        }
      } 
      else if (businessType === 'perorangan') {
        const ptkp = 54000000 / 12; // Monthly PTKP
        const taxableIncome = Math.max(0, grossIncome - fixedCost - ptkp);
        
        if (taxableIncome <= 60000000 / 12) {
          taxRate = '5% dari penghasilan kena pajak';
          taxAmount = taxableIncome * 0.05;
        } else if (taxableIncome <= 250000000 / 12) {
          taxRate = '15% dari penghasilan kena pajak';
          taxAmount = (3000000/12) + (taxableIncome - (60000000/12)) * 0.15;
        } else if (taxableIncome <= 500000000 / 12) {
          taxRate = '25% dari penghasilan kena pajak';
          taxAmount = (34500000/12) + (taxableIncome - (250000000/12)) * 0.25;
        } else if (taxableIncome <= 5000000000 / 12) {
          taxRate = '30% dari penghasilan kena pajak';
          taxAmount = (97000000/12) + (taxableIncome - (500000000/12)) * 0.3;
        } else {
          taxRate = '35% dari penghasilan kena pajak';
          taxAmount = (1447000000/12) + (taxableIncome - (5000000000/12)) * 0.35;
        }
        taxType = 'PPh Orang Pribadi Progresif';
      }
      else { // badan usaha
        taxType = 'PPh Badan';
        taxRate = '22% dari laba bersih';
        taxAmount = (grossIncome - fixedCost) * 0.22;
      }
      
      // Calculate net profit
      const netProfit = grossIncome - fixedCost - taxAmount;
      
      // Format currency
      const formatIDR = (amount) => {
        return 'Rp' + amount.toLocaleString('id-ID');
      };
      
      // Display results
      document.getElementById('grossIncome').textContent = formatIDR(grossIncome);
      document.getElementById('totalFixedCost').textContent = formatIDR(fixedCost);
      document.getElementById('grossProfit').textContent = formatIDR(grossProfit);
      document.getElementById('taxType').textContent = taxType;
      document.getElementById('taxRate').textContent = taxRate;
      document.getElementById('taxAmount').textContent = formatIDR(taxAmount);
      document.getElementById('netProfit').textContent = formatIDR(netProfit);
      
      // Generate recommendation
      let recommendation = document.getElementById('recommendation');
      recommendation.className = 'recommendation';
      
      if (netProfit >= targetProfit) {
        recommendation.classList.add('success');
        recommendation.innerHTML = `
          <h3>🎉 Selamat! Usaha Anda Menguntungkan</h3>
          <p>Laba bersih Anda setelah pajak sebesar <strong>${formatIDR(netProfit)}</strong> melebihi target <strong>${formatIDR(targetProfit)}</strong>.</p>
          <p><strong>Analisis Keberhasilan:</strong></p>
          <ul>
            <li>Biaya tetap Anda sebesar <strong>${(fixedCost/grossIncome*100).toFixed(1)}%</strong> dari penghasilan termasuk efisien</li>
            <li>Beban pajak sebesar <strong>${(taxAmount/grossIncome*100).toFixed(1)}%</strong> termasuk wajar</li>
            <li>Laba kotor sebelum pajak mencapai <strong>${(grossProfit/grossIncome*100).toFixed(1)}%</strong> dari penghasilan</li>
          </ul>
          <p><strong>Rekomendasi Strategi:</strong></p>
          <ul>
            <li>Pertahankan efisiensi biaya tetap di bawah 50% penghasilan</li>
            <li>Alokasikan 20-30% keuntungan untuk pengembangan usaha</li>
            <li>Manfaatkan insentif pajak jika memungkinkan</li>
            <li>Pertimbangkan investasi dalam pemasaran untuk meningkatkan omset</li>
          </ul>
        `;
      } 
      else if (netProfit > 0) {
        recommendation.classList.add('warning');
        recommendation.innerHTML = `
          <h3>⚠️ Usaha Anda Masih Untung Tapi Belum Capai Target</h3>
          <p>Laba bersih Anda setelah pajak sebesar <strong>${formatIDR(netProfit)}</strong> masih di bawah target <strong>${formatIDR(targetProfit)}</strong>.</p>
          <p><strong>Analisis:</strong></p>
          <ul>
            <li>Biaya tetap sebesar <strong>${(fixedCost/grossIncome*100).toFixed(1)}%</strong> dari penghasilan ${fixedCost/grossIncome > 0.6 ? 'terlalu tinggi (disarankan <60%)' : 'masih wajar'}</li>
            <li>Beban pajak sebesar <strong>${(taxAmount/grossIncome*100).toFixed(1)}%</strong> ${taxAmount/grossIncome > 0.1 ? 'cukup signifikan' : 'masih wajar'}</li>
            <li>Margin laba kotor <strong>${(grossProfit/grossIncome*100).toFixed(1)}%</strong> ${grossProfit/grossIncome < 0.3 ? 'terlalu tipis (disarankan >30%)' : 'masih cukup'}</li>
          </ul>
          <p><strong>Rekomendasi Perbaikan:</strong></p>
          <ul>
            ${fixedCost/grossIncome > 0.6 ? '<li>Evaluasi biaya tetap dan cari cara penghematan</li>' : ''}
            ${taxAmount/grossIncome > 0.1 ? '<li>Manfaatkan insentif pajak atau konsultasi dengan akuntan pajak</li>' : ''}
            ${grossProfit/grossIncome < 0.3 ? '<li>Tingkatkan harga jual atau cari supplier dengan harga lebih murah</li>' : ''}
            <li>Tinjau kembali target laba atau tingkatkan volume penjualan</li>
            <li>Pertimbangkan diversifikasi produk/jasa yang lebih menguntungkan</li>
          </ul>
        `;
      } 
      else {
        recommendation.classList.add('danger');
        recommendation.innerHTML = `
          <h3>❌ Perhatian: Usaha Anda Mengalami Kerugian</h3>
          <p>Setelah memperhitungkan semua biaya dan pajak, Anda mengalami kerugian sebesar <strong>${formatIDR(Math.abs(netProfit))}</strong> per bulan.</p>
          <p><strong>Penyebab Utama:</strong></p>
          <ul>
            <li>Biaya tetap terlalu tinggi (<strong>${(fixedCost/grossIncome*100).toFixed(1)}%</strong> dari penghasilan)</li>
            <li>Beban pajak signifikan (<strong>${(taxAmount/grossIncome*100).toFixed(1)}%</strong> dari penghasilan)</li>
            <li>Margin laba kotor negatif (<strong>${(grossProfit/grossIncome*100).toFixed(1)}%</strong>)</li>
          </ul>
          <p><strong>Langkah Darurat:</strong></p>
          <ul>
            <li>Segera evaluasi biaya tetap dan kurangi yang tidak esensial</li>
            <li>Tingkatkan harga jual atau cari supplier dengan harga lebih murah</li>
            <li>Manfaatkan program bantuan UMKM dari pemerintah</li>
            <li>Negosiasikan ulang kredit/cicilan dengan bank/kreditor</li>
            <li>Pertimbangkan pivot model bisnis jika perlu</li>
            <li>Fokus pada produk/jasa yang paling menguntungkan</li>
          </ul>
          <p>Disarankan untuk segera berkonsultasi dengan ahli keuangan atau akuntan.</p>
        `;
      }
      
      // Show results
      document.getElementById('results').style.display = 'block';
      
      // Scroll to results
      document.getElementById('results').scrollIntoView({ behavior: 'smooth' });
    }
  </script>
</body>
</html>
