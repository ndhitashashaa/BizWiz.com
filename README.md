<!-- Updated and Enhanced Version of BizWis - Simulasi Inflasi & Pajak UMKM -->
<!-- Focused on Clarity, Simplicity, and Educative UI for All Ages -->

<!-- Only show changes made in script section for brevity -->
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
      inflasi_info = "(Inflasi harian dikalikan 30 hari)";
    } else {
      inflasi_info = "(Inflasi langsung digunakan karena bertipe bulanan)";
    }

    const biaya_akhir = biaya + (biaya * inflasi_adjust);
    const laba_kotor = penghasilan - biaya_akhir;
    const pajak = penghasilan * 0.005;
    const laba_bersih = laba_kotor - pajak;
    const break_even = biaya_akhir;

    const formatter = new Intl.NumberFormat('id-ID', {
      style: 'currency',
      currency: 'IDR',
      minimumFractionDigits: 0
    });

    let output = `
      <h2 class="hasil-title"><i class="fas fa-chart-pie"></i> Hasil Perhitungan</h2>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-money-bill-wave"></i> Biaya setelah Inflasi</div>
        <div class="result-value">${formatter.format(biaya_akhir)}</div>
      </div>
      <small>Jumlah biaya yang naik karena inflasi. ${inflasi_info}</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-chart-line"></i> Laba Kotor</div>
        <div class="result-value">${formatter.format(laba_kotor)}</div>
      </div>
      <small>Penghasilan dikurangi biaya. Belum dipotong pajak ya!</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-file-invoice"></i> Pajak UMKM 0.5%</div>
        <div class="result-value">${formatter.format(pajak)}</div>
      </div>
      <small>Pajak tetap 0.5% dari penghasilan bulananmu.</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-coins"></i> Laba Bersih</div>
        <div class="result-value">${formatter.format(laba_bersih)}</div>
      </div>
      <small>Ini sisa uangmu setelah semua biaya dan pajak dibayar. Ini uang "untung"-mu~</small>

      <div class="result-item">
        <div class="result-label"><i class="fas fa-balance-scale"></i> Break Even Point</div>
        <div class="result-value">${formatter.format(break_even)}</div>
      </div>
      <small>Jumlah minimal penghasilan agar usahamu impas (tidak rugi).</small>
    `;

    if (laba_bersih <= 0) {
      output += `
        <div class="recommendation loss">
          <i class="fas fa-exclamation-triangle"></i> <strong>Rekomendasi:</strong> Kurangi biaya atau naikkan harga jual yaa! 💔 Masih rugi nih!
        </div>
      `;
    } else {
      output += `
        <div class="recommendation profit">
          <i class="fas fa-check-circle"></i> <strong>Rekomendasi:</strong> Bisnismu untung! 🎉 Tetap jaga efisiensi dan kontrol inflasi yaa~
        </div>
      `;
    }

    document.getElementById("output").innerHTML = output;
  }
</script>

<!-- Optional: You can add a tooltip or note below the form: -->
<small style="text-align:center;display:block;margin-top:20px;color:var(--text-light);font-style:italic">
  💡 <strong>Cara menghitung inflasi:</strong> Jika inflasi 3% dan biaya awal Rp1.000.000 maka biaya setelah inflasi = 1.000.000 + (3% dari 1.000.000) = Rp1.030.000. 
  Untuk harian, kalikan % dengan 30 dulu, bestie~
</small>
