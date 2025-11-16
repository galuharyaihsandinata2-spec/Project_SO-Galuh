# Project_SO-Galuh
# Project 1. Skenario Praktik: Manajemen File Server

Gambar 1 : https://drive.google.com/file/d/1cPIvU1vnlTTE4FX9HDvahQoRM6Pq-MiU/view?usp=sharing

# 1. **Membuat direktori baru
```bash
mkdir project_file_manajement_server
```
- Membuat folder/direktori baru bernama `project_file_manajement_server`.
---

# 2. **Masuk ke direktori yang sudah dibuat
```bash
cd project_file_manajement_server
```
- Berpindah ke direktori `project_file_manajement_server`.
---

# 3. **Membuat subdirektori dalam satu perintah (dengan opsi -p)**
```bash
mkdir -p marketing/documents marketing/archives
mkdir -p engineering/documents engineering/archives
mkdir -p hr/documents hr/archives
```
- Membuat beberapa direktori sekaligus dengan subfolder.
- `-p` untuk membuat induk folder jika belum ada tanpa error.
- Membuat struktur seperti:
  - marketing/documents
  - marketing/archives
  - engineering/documents
  - engineering/archives
  - hr/documents
  - hr/archives
---

# 4. **Melihat isi folder**
```bash
ls
```
- Menampilkan isi folder saat ini, yaitu muncul `engineering`, `hr`, dan `marketing`.
---

# 5. **Memindahkan file dengan mv
```bash
mv /home/hozz/project_file_manajement/documents/file{1..10}.txt /home/hozz/project_file_manajement_server/marketing/documents
```
- Memindahkan file bernama file1.txt sampai file10.txt dari folder `/home/hozz/project_file_manajement/documents/` ke `/home/hozz/project_file_manajement_server/marketing/documents`.
- `file{1..10}.txt` adalah ekspansi untuk file 1 sampai 10.
---

# 6. **Menyalin file dengan cp dan mencoba menyalin file tertentu
```bash
cp marketing/documents/file{1..10}.txt /marketing/archives
```
- Dicoba untuk menyalin file dari `marketing/documents` ke `/marketing/archives`.
- Gagal karena `/marketing/archives` adalah path absolut yang tidak ditemukan (harusnya langsung `marketing/archives`, bukan `/marketing/archives`).
---

# 7. **Kesalahan penggunaan cp dan fix path
Kesalahan muncul karena:
- Target direktori `/marketing/archives` dianggap path absolut di root, tapi folder tersebut tidak ada.
- `cp` tanpa opsi `-r` tidak bisa menyalin folder, hanya file.
- Jadi, mencoba menyalin dengan opsi `-R` agar bisa menyalin direktori.
---

# 8. **Menyalin direktori secara rekursif dengan cp -R
```bash
cp -R /home/hozz/project_file_manajement_server/marketing/documents /home/hozz/project_file_manajement_server/marketing/archives
```
- Menyalin seluruh isi folder `documents` ke folder `archives` dalam `marketing`.
- Menggunakan `-R` (recursive) agar direktori dapat disalin beserta isinya.
---

# 9. **Menambahkan user baru
```bash
sudo adduser admin_marketing
```
- Menambahkan user baru dengan nama `admin_marketing`.
- Memerlukan password `sudo` (superuser) untuk otorisasi.
- Sistem memberikan informasi:
  - Membuat user `admin_marketing`.
  - Membuat grup baru `admin_marketing`.
  - Membuat home directory untuk user tersebut.
  - Meminta masukkan password untuk user baru `admin_marketing`.

# Kesimpulan:
- Perintah digunakan untuk membuat struktur file proyek.
- Memindahkan dan menyalin file atau folder secara terorganisir.
- Penambahan user baru untuk administrasi bagian marketing.
- Ada beberapa kesalahan path dan pemahaman opsi perintah yang diperbaiki pada langkah berikutnya.

Gambar 2 : https://drive.google.com/file/d/1w0qeG70vrKy2h404x65R1Fn94bodnjFe/view?usp=sharing

# 1. **Penambahan user baru (dari konteks sebelumnya)
```
info: Adding new user `admin_marketing` to supplemental / extra groups `users` ...
info: Adding user `admin_marketing` to group `users` ...
```
- Sistem menginformasikan bahwa user baru bernama `admin_marketing` telah ditambahkan, dan secara otomatis menjadi anggota grup `users`.

# 2. Perintah `sudo chown -R admin_marketing /home/hozz/project_file_manajement_server/marketing

```
sudo chown -R admin_marketing /home/hozz/project_file_manajement_server/marketing
```

`sudo` 
  Menjalankan perintah dengan hak akses administrator (root).

  `chown`
  Perintah untuk mengubah **owner** (pemilik) file atau direktori.

  `-R`
  Opsi recursive, yang berarti perintah akan diterapkan tidak hanya pada direktori utama, tapi juga seluruh isi subdirektori dan file di dalamnya.

  `admin_marketing`
  Nama user yang akan dijadikan pemilik baru dari direktori dan isinya.

  `/home/hozz/project_file_manajement_server/marketing`
  Direktori target yang akan diubah kepemilikannya.

Fungsi lengkap:  
Perintah ini mengubah pemilik (owner) direktori `/home/hozz/project_file_manajement_server/marketing` dan seluruh isinya menjadi user `admin_marketing`.


# 3. **Perintah `chmod -R 700 /home/hozz/project_file_manajement_server/marketing

```
chmod -R 700 /home/hozz/project_file_manajement_server/marketing
```

`chmod`
  Perintah untuk mengubah permission (hak akses) file atau direktori.

  `-R`
  Opsi recursive, yaitu mengubah hak akses secara menyeluruh ke subdirektori dan file di dalam direktori tersebut.

  `700` 
  Mode permission dalam format oktal, yang artinya:  
  - Owner (pemilik): baca (r), tulis (w), dan eksekusi (x) → 7  
  - Grup: tidak ada akses → 0  
  - Others (lainnya): tidak ada akses → 0

  `/home/hozz/project_file_manajement_server/marketing` 
  Direktori target yang ingin diubah permission-nya.

Fungsi lengkap:
Perintah ini memberikan kontrol penuh (baca, tulis, eksekusi) hanya pada pemilik direktori dan isinya, sementara grup dan pengguna lain tidak memiliki akses sama sekali.

# Ringkasan akhir:

- User baru `admin_marketing` sudah ditambahkan ke sistem dan grup `users`.
- Direktori `marketing` dan semua isinya sekarang dimiliki oleh user `admin_marketing`.
- Permission direktori `marketing` dan isinya dibatasi hanya untuk pemilik (`admin_marketing`) saja, dengan hak penuh (700).

Gambar 3 : https://drive.google.com/file/d/1w0qeG70vrKy2h404x65R1Fn94bodnjFe/view?usp=sharing

# 1. Perintah mengubah permission direktori marketing
```bash
sudo chmod -R 700 /home/hozz/project_file_manajement_server/marketing
```
- `sudo` : menjalankan perintah sebagai superuser (admin).
- `chmod` : mengubah hak akses file/direktori.
- `-R` : secara rekursif (meliputi seluruh isi di dalam direktori).
- `700` : hanya pemilik yang memiliki akses penuh (baca, tulis, eksekusi).
- `/home/hozz/project_file_manajement_server/marketing` : target direktori.
- **Fungsi:** Membatasi akses hanya untuk pemilik pada direktori marketing dan isinya.


# 2. Perintah menambahkan user baru `admin_engineering`
```bash
sudo adduser admin_engineering
```
- Menambah user `admin_engineering`.
- Sistem memilih UID/GID secara otomatis dari range 1000–59999.
- Membuat grup baru `admin_engineering` dan menambah user ke grup tersebut.
- Membuat home directory `/home/admin_engineering`.
- Meminta input password:  
  - Password pertama terlalu pendek (peringatan "BAD PASSWORD").
  - Password kedua berhasil dan di-update.
- Meminta informasi seperti nama lengkap, nomor kamar, telepon, dll (boleh kosong).
- Meminta konfirmasi apakah data sudah benar (`y` untuk ya).
- Menambahkan user ke grup `users` juga (akses tambahan).

# 3. Mengubah kepemilikan direktori engineering
```bash
sudo chown -R admin_engineering /home/hozz/project_file_manajement_server/engineering
```
- Mengubah owner (pemilik) direktori `/home/hozz/project_file_manajement_server/engineering` dan seluruh isinya menjadi `admin_engineering`.


# 4. Mengubah permission direktori engineering
```bash
sudo chmod -R 700 /home/hozz/project_file_manajement_server/engineering
```
- Mengatur hak akses hanya untuk pemilik `admin_engineering` agar memiliki kontrol penuh terhadap direktori tersebut.


# 5. Menambahkan user baru `admin_hr`
```bash
sudo adduser admin_hr
```
- Proses sama seperti pada pembuatan user `admin_engineering`:
  - Membuat user dan grup baru `admin_hr`.
  - Membuat home directory `/home/admin_hr`.
  - Menyiapkan user untuk mengelola bagian HR.

# Kesimpulan:
- Setiap bagian tim (marketing, engineering, HR) diberikan folder sendiri dalam project.
- User admin khusus dibuat untuk tiap bagian (`admin_marketing`, `admin_engineering`, `admin_hr`).
- Folder yang terkait diberikan kepemilikan dan akses khusus hanya untuk user admin yang bersangkutan dengan mode `700`.
- Menerapkan keamanan akses file directory yang ketat untuk menjaga privasi dan kontrol file.

  Gambar 4 : https://drive.google.com/file/d/1IQlhpD85oK_S9K9lri-tLrWw24mvZiZy/view?usp=sharing

# 1. Menampilkan informasi penambahan user
```
Is the information correct? [Y/n] y
info: Adding new user `admin_hr` to supplemental / extra groups `users` ...
info: Adding user `admin_hr` to group `users` ...
```
- Mengonfirmasi penambahan user `admin_hr`.
- Sistem menambahkan user ke grup `users` sebagai grup ekstra.

---

# 2. Mengubah kepemilikan direktori `hr`
```bash
sudo chown -R admin_hr /home/hozz/project_file_manajement_server/hr
```
- `sudo` : menjalankan sebagai administrator.
- `chown -R` : mengubah owner secara rekursif.
- User `admin_hr` menjadi pemilik direktori `/home/hozz/project_file_manajement_server/hr` beserta isinya.

# 3. Mengatur permission folder `hr`
```bash
sudo chmod -R 700 /home/hozz/project_file_manajement_server/hr
```
- Memberikan hak akses penuh (read, write, execute) hanya kepada pemilik (`admin_hr`) di direktori `hr`.
- Melarang akses untuk grup dan user lain.

# 4. Percobaan masuk ke direktori `marketing` gagal
```bash
cd marketing
bash: cd: marketing: Permission denied
```
- User saat ini tidak punya izin untuk masuk ke folder `marketing`.
- Ini karena permission folder marketing membatasi akses, mungkin hanya untuk user `admin_marketing`.

# 5. Switch user ke `admin_marketing`
```bash
su admin_marketing
Password:
cd marketing/
ls
```
- `su admin_marketing` : beralih ke user `admin_marketing`.
- User ini berhasil masuk ke direktori `marketing`.
- Menampilkan isi folder `marketing` berupa direktori `archives` dan `documents`.

# 6. Keluar dari sesi `admin_marketing`
```bash
exit
```
- Kembali ke user awal (`hozz`).

---

# 7. Percobaan masuk ke direktori `engineering` gagal`
```bash
cd engineering
bash: cd: engineering: Permission denied
```
- Sama seperti sebelumnya, akses ditolak karena permission yang membatasi.

# 8. Switch user ke `admin_engineering`
```bash
su admin_engineering
Password:
ls
```
- Beralih ke user `admin_engineering`.
- User berhasil melihat isi folder `project_file_manajement_server`, yaitu folder engineering, hr, dan marketing sebagai daftar folder di dalamnya.

# 9. Keluar dari sesi `admin_engineering`
```bash
exit
```
- Kembali ke user awal (`hozz`).

---

# 10. Percobaan masuk direktori `hr` oleh user biasa gagal
```bash
cd hr
bash: cd: hr: Permission denied
```
- User `hozz` tidak punya akses ke folder `hr`.

# 11. switch user ke `admin_hr`
```bash
su admin_hr
Password:
ls
```
- Beralih ke user `admin_hr`.
- User ini dapat melihat isi folder level atas project yaitu `engineering`, `hr`, `marketing`.

---

# 12. Masuk ke direktori `hr` dan melihat isinya
```bash
cd hr
ls
```
- Berhasil masuk ke direktori `hr`.
- Menampilkan isi folder `hr` yaitu `archives` dan `documents`.

---

# 13. Keluar dari sesi `admin_hr`
```bash
exit
```
- Kembali ke user awal (`hozz`).

# Kesimpulan:

- Direktori `marketing`, `engineering`, dan `hr` diberikan **permission 700**, sehingga hanya user pemilik yang dapat mengaksesnya.
- User umum (`hozz`) tidak dapat mengakses folder tersebut karena kondisi permission yang ketat.
- Masing-masing direktori memiliki user admin khusus (`admin_marketing`, `admin_engineering`, `admin_hr`) yang dapat bebas mengakses folder bagian mereka.
- Perpindahan user dengan `su <username>` digunakan untuk mengakses folder yang memiliki hak akses terbatas.
- Sistem keamanan direktori sudah diimplementasikan dengan membatasi akses sesuai user yang berhak.

Gambar 5 : https://drive.google.com/file/d/1EimOLTRer6WR5h8LQaPI5MA5l6yzhmMP/view?usp=sharing

# 1. Perintah `exit`
```bash
exit
```
- Perintah untuk keluar dari sesi shell atau user saat ini.
- Jika sebelumnya menggunakan `su` untuk berpindah user, `exit` mengembalikan ke user sebelumnya.
- Jika di shell biasa, perintah ini akan menutup terminal atau sesi SSH.

# 2. Perintah `find` dengan redirect output ke file
```bash
find /home/hozz/project_file_manajement -type f -name "*.pdf" > daftar_pdf.txt
```
- `find` : perintah untuk mencari file atau direktori berdasarkan kriteria tertentu.
- `/home/hozz/project_file_manajement` : direktori root tempat pencarian dimulai.
- `-type f` : mencari hanya file biasa (bukan direktori, link, dll).
- `-name "*.pdf"` : mencari file dengan ekstensi `.pdf` (nama file yang berakhiran `.pdf`).
- `>` : redirect output perintah ke file.
- `daftar_pdf.txt` : file tujuan untuk menyimpan daftar hasil pencarian.
  
# Fungsi: 
Mencari semua file `.pdf` di dalam folder `/home/hozz/project_file_manajement` dan menyimpan daftar lengkap path file tersebut ke dalam `daftar_pdf.txt`.

# 3. Perintah `ls`
```bash
ls
```
- Menampilkan isi direktori kerja saat ini.
- Dalam output terlihat `daftar_pdf.txt` (file hasil pencarian), dan folder `engineering`, `hr`, `marketing`.

# 4. Perintah `cat` untuk menampilkan isi file
```bash
cat daftar_pdf.txt
```
- Menampilkan isi file `daftar_pdf.txt` ke terminal.
- Isi file berupa path lengkap ke file-file `.pdf` yang ditemukan, misalnya:
  ```
  /home/hozz/project_file_manajement/archives/file16.pdf
  /home/hozz/project_file_manajement/archives/file17.pdf
  /home/hozz/project_file_manajement/archives/file18.pdf
  ```

# Ringkasan:

- `exit` mengakhiri sesi shell / berpindah user.
- `find ... -type f -name "*.pdf"` mencari seluruh file PDF.
- Output hasil `find` disimpan dalam file `daftar_pdf.txt`.
- `ls` menampilkan file dan folder yang ada saat ini.
- `cat` digunakan untuk membaca isi file hasil pencarian dan menampilkannya di terminal.


