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
      <label for="mode">Pilih Simulasi</label>
      <select id="mode" onchange="updateMode()">
        <option value="">-- Pilih Jenis Simulasi --</option>
        <option value="pajak">Hitung Pajak UMKM Saja</option>
        <option value="modal">Hitung Modal Pengembangan Usaha</option>
        <option value="analisis">Analisis Usaha (Pajak + Modal)</option>
      </select>
      <small>Pilih jenis simulasi sesuai kebutuhan Anda</small>
    </div>
    <div id="simulasi-container"></div>
  </div>
  <script>
    function updateMode() {
      const mode = document.getElementById('mode').value;
      const container = document.getElementById('simulasi-container');
      container.innerHTML = '';
      if (mode === 'pajak') {
        container.innerHTML = '<p><i>Form simulasi pajak akan ditampilkan di sini...</i></p>';
      } else if (mode === 'modal') {
        container.innerHTML = '<p><i>Form perhitungan modal akan ditampilkan di sini...</i></p>';
      } else if (mode === 'analisis') {
        container.innerHTML = '<p><i>Form analisis gabungan pajak + modal akan ditampilkan di sini...</i></p>';
      }
    }
  </script>
</body>
</html>
