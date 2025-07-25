# Website Dusun Druju Tegal

Website ini merupakan portal resmi Dusun Druju Tegal, Desa Plosogede, Kabupaten Magelang. Dibangun menggunakan [SvelteKit](https://kit.svelte.dev/) dan [TailwindCSS](https://tailwindcss.com/), website ini bertujuan untuk menyediakan informasi seputar profil dusun, potensi, dokumentasi kegiatan, struktur organisasi, serta layanan interaktif bagi warga dan pengunjung.

## Fitur Utama

- **Profil Dusun**: Informasi umum tentang Dusun Druju Tegal.
- **Peta Administrasi & Rawan Bencana**: Visualisasi peta wilayah dan titik rawan bencana.
- **Struktur Organisasi**: Struktur kepengurusan dusun dan pemuda.
- **Potensi Dusun**: Produk unggulan seperti Slondok dan Pupuk Kompos.
- **Dokumentasi Kegiatan**: Galeri foto kegiatan warga.
- **Komentar Pengunjung**: Form interaktif untuk meninggalkan pesan/komentar.
- **Statistik Kunjungan**: Statistik jumlah pengunjung website secara real-time.

## Teknologi

- [SvelteKit](https://kit.svelte.dev/)
- [TailwindCSS](https://tailwindcss.com/)
- [Firebase Realtime Database](https://firebase.google.com/products/realtime-database) (untuk komentar & statistik kunjungan)
- [Keen Slider](https://keen-slider.io/) (galeri dokumentasi)
- [Leaflet](https://leafletjs.com/) (peta interaktif)

## Instalasi & Pengembangan

1. **Clone repository:**

   ```bash
   git clone https://github.com/username/website_dusun_svelte.git
   cd website_dusun_svelte
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Konfigurasi Firebase:**
   - Salin `.env.example` menjadi `.env`
   - Kontak Admin untuk meminta kredensial Firebase 

4. **Jalankan server pengembangan:**

   ```bash
   npm run dev
   ```

5. **Build untuk produksi:**

   ```bash
   npm run build
   ```

6. **Preview hasil build:**
   ```bash
   npm run preview
   ```

## Kontribusi

Kontribusi terbuka untuk pengembangan website ini. Silakan buat pull request atau issue jika ingin menambahkan fitur atau melaporkan bug.

## Lisensi

Website ini dikembangkan oleh Jeremy Kenneth untuk KKN AA.83.023.  
© 2025 Dusun Druju Tegal, Desa Plosogede, Kabupaten Magelang.
