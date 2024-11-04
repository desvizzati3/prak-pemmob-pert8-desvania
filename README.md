# Penjelasan Cara Kerja Login pada Ionic

Nama    : Desvania Tirta Izzati
NIM     : H1D022088

## 1. Login

koneksi.php dan login.php dibuat untuk mengatur koneksinya ke databse mySql. 

koneksi.php berfungsi untuk menghubungkan aplikasi dengan database. CORS (Cross-Origin Resource Sharing) digunakan untuk mengontrol akses untuk semua domain dapat mengakses server, mengizinkan kredensial seperti http authentication, menentukan metode PHP yang diizinkan.

sedangkan login.php digunakan untuk memverifikasi login aplikasi, dan memberikan respon kepada aplikasi apakah login yang dilakukan berhasil atau tidak.

## 2. Setup HTTP Client

Di awal, di file app.module.ts, kita set up dulu biar aplikasi bisa nge-call API. Jadi, di sini kita tambahin provideHttpClient, yang intinya bikin aplikasi kita bisa kirim request ke server, misalnya buat login.

## 3. Halaman Login

Di halaman login (login.page.html), ada form buat masukin username sama password. Pas kita klik tombol "Login", aplikasi bakal ngambil data dari inputan kita dan mulai proses login.

## 4. Logika Login di Frontend

Di file login.page.ts, ada fungsi login() yang aktif pas tombol "Login" diklik. Jadi, fungsi ini bakal ambil data username sama password yang kita masukin, terus dikirim ke server pakai postMethod() dari AuthenticationService. Dia bakal kirim request HTTP POST ke API di server buat ngecek data login ini.

## 3. Cek Login di Server

Nah, di server, data yang tadi dikirim di-handle sama file login.php. Di sini, aplikasi connect ke database lewat koneksi.php, terus ngecek apakah username dan password kita ada di database. Kalau cocok, server bakal balikin JSON yang isinya status "berhasil", token, dan username. Tapi kalau nggak cocok, statusnya "gagal".

## 4. Simpan Status Login

Balik lagi ke frontend, kalau login berhasil, aplikasi nyimpen token sama username kita di perangkat (pake Preferences) lewat saveData() di AuthenticationService. Ini semacam tanda bahwa kita udah login. Kalau gagal, aplikasi bakal munculin notifikasi yang bilang kalau login gagal atau ada masalah koneksi.

## 5. Proteksi Akses Halaman (Guard)

Di sini, ada guard authGuard buat ngejaga biar cuma pengguna yang udah login yang bisa buka halaman tertentu, kayak halaman home. Terus ada juga autoLoginGuard yang otomatis ngarahin kita ke halaman home kalau kita udah login dan buka aplikasi lagi.

## 6. Halaman Home

Setelah login sukses, kita masuk ke halaman home (home.page.html), di mana kita bisa lihat nama kita muncul di sana. Ada juga tombol logout di halaman ini, yang kalau diklik bakal ngejalanin fungsi logout() di AuthenticationService.




