# Website MI DARUL FALAH BIKERU

Website statis responsif dengan halaman publik dan panel admin. Konten berita/pengumuman disimpan di Supabase. Pengunjung hanya melihat konten terbit; admin yang login dapat menambah, mengedit, menerbitkan/draft, dan menghapus konten.

## Penting sebelum digunakan
File ini adalah paket website siap dikonfigurasi, **bukan** website yang sudah online. Login/admin baru berfungsi setelah Anda membuat project Supabase, menyiapkan tabel dan kebijakan keamanan, membuat akun admin, dan mengisi `config.js`. GitHub Pages hanya meng-host halaman; database dan login ditangani Supabase.

## A. Buat database dan login admin (sekali saja)
Lakukan dari browser HP Android. Jika tampilan sulit, aktifkan menu browser ⋮ > Situs desktop.
1. Buka https://supabase.com/ lalu daftar/login dan buat project baru. Simpan password project dengan aman.
2. Di project, buka **SQL Editor** > **New query**. Buka file `supabase-setup.sql` dari paket ini, salin seluruh isinya, tempel di SQL Editor, lalu tekan **Run**.
3. Buka **Authentication** > **Providers** atau **Sign In / Providers**. Pastikan Email aktif.
4. Buka **Authentication > Settings** dan matikan **Allow new users to sign up** (pendaftaran publik). Nama menu dapat sedikit berbeda.
5. Buka **Authentication > Users** > **Add user** / **Create new user**. Buat satu akun dengan email Anda sendiri dan password kuat. Ini akun admin. Jangan bagikan password.
6. Buka **Project Settings > API** (atau Data API/Connect). Salin **Project URL** dan **anon/public key** atau **publishable key**. Jangan gunakan `service_role`/secret key.
7. Edit `config.js` menggunakan editor teks, ganti `TEMPEL_PROJECT_URL_DI_SINI` dan `TEMPEL_ANON_PUBLISHABLE_KEY_DI_SINI` dengan nilai dari project Anda. Jangan beri tanda kutip tambahan; pertahankan tanda kutip yang sudah ada.

## B. Uji website
1. Upload semua file dalam folder ini ke hosting statis atau repository GitHub.
2. Setelah website online, buka `admin.html`, masuk menggunakan akun admin yang dibuat di Supabase.
3. Buat berita/pengumuman percobaan, centang **Terbitkan di website publik**, lalu simpan.
4. Buka halaman utama `index.html` dan pastikan konten tampil. Uji juga tombol draft/hapus dari panel admin.
5. Jika gagal, periksa bahwa SQL berhasil dijalankan, URL/key benar, dan sign-up publik dimatikan.

## C. Hosting gratis dengan GitHub Pages (HP Android)
1. Buka https://github.com dan buat akun.
2. Buat repository baru bernama `mi-darul-falah-bikeru`. Untuk pengaturan paling mudah, pilih **Public**.
3. Masuk repository > **Add file > Upload files**. Upload file-file website dari folder paket (isi folder, bukan file ZIP-nya). Pastikan `index.html`, `admin.html`, `config.js`, `app.js`, `admin.js`, `style.css`, `admin.css`, dan `supabase-setup.sql` ada di root repository.
4. Tekan **Commit changes**.
5. Buka **Settings > Pages**. Pada **Build and deployment**, pilih **Deploy from a branch**, branch `main`, folder `/(root)`, lalu **Save**.
6. Tunggu proses selesai. URL umumnya `https://USERNAME.github.io/mi-darul-falah-bikeru/` (ganti USERNAME dengan nama akun GitHub Anda). Periksa tab Pages untuk URL yang benar.
7. Buka URL tersebut. Panel admin berada di `https://USERNAME.github.io/mi-darul-falah-bikeru/admin.html`.

## Batas keamanan dan catatan
- `config.js` memuat URL dan anon/publishable key. Key ini memang untuk frontend; keamanan harus ditegakkan oleh Row Level Security (RLS), bukan dengan menyembunyikan key.
- **Jangan pernah** memasukkan `service_role` key atau password admin ke file website/repository.
- SQL ini mengizinkan akun yang login mengelola konten yang dibuat oleh akun itu. Matikan signup publik dan buat hanya akun admin Anda. Jika suatu saat perlu beberapa editor, kebijakan harus ditinjau ulang.
- Admin perlu menjaga email/password dan mengaktifkan perlindungan akun yang tersedia.
- Jangan publikasikan data pribadi siswa, nomor telepon pribadi, nilai, alamat rumah, atau foto siswa tanpa izin yang sesuai.
- Kepala madrasah dan WhatsApp masih placeholder “Belum diisi”; ubah di `index.html` setelah informasinya resmi.
- Supabase/GitHub dapat mengubah nama menu. Paket ini tidak bisa otomatis membuat akun atau project layanan atas nama Anda.
