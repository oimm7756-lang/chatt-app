# chatt — proyek awal Android

Aplikasi chat Android bertema gelap menggunakan Kotlin, Jetpack Compose, Firebase Authentication, dan Cloud Firestore.

## Fitur versi ini
- Siapa saja dapat mendaftar menggunakan email dan kata sandi.
- Login dan keluar akun.
- Nama tampilan diambil dari profil pendaftaran.
- Ruang obrolan umum online: semua akun yang login ke proyek Firebase yang sama dapat melihat pesan.
- Pesan teks diperbarui secara langsung melalui Firestore.
- Aturan Firestore membatasi akses profil, validasi pengirim, panjang pesan, dan mencegah edit/hapus pesan melalui klien.

## Hubungkan ke Firebase (wajib agar online)
1. Buka https://console.firebase.google.com/ dan buat proyek Firebase.
2. Tambahkan aplikasi Android dengan package name persis: `com.example.chatt`.
3. Unduh `google-services.json` dan letakkan di folder `app/`.
4. Firebase Console → Authentication → Sign-in method → aktifkan **Email/Password**.
5. Firebase Console → Firestore Database → buat database.
6. Buka tab **Rules** pada Firestore, salin isi file `firestore.rules` dari proyek ini, lalu klik **Publish**.
7. Jangan mengaktifkan akses database publik tanpa autentikasi. Jangan menghapus aturan keamanan ini.
8. Buka folder proyek di Android Studio, tunggu Gradle Sync, lalu pilih **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

APK debug biasanya dibuat di `app/build/outputs/apk/debug/app-debug.apk`.

## Catatan keamanan dan privasi
- Pendaftaran terbuka: siapa saja yang memasang aplikasi dan membuat akun Firebase dapat bergabung.
- Lobby ini bukan percakapan pribadi. Semua pengguna yang sudah login dapat membaca pesan di lobby.
- Versi ini belum memiliki enkripsi end-to-end, pelaporan/blokir, moderasi, anti-spam lanjutan, atau notifikasi push.
- Aturan Firestore membatasi akses dasar, tetapi belum menjadikan aplikasi siap untuk publik berskala besar. Sebelum rilis luas, tambahkan Firebase App Check, pembatasan spam/rate, moderasi, kebijakan privasi, dan pengujian aturan.
- Jangan kirim informasi pribadi atau rahasia melalui lobby.

## Struktur penting
- `app/` — kode aplikasi Android.
- `firestore.rules` — aturan keamanan Firestore yang harus dipublikasikan.
- `google-services.json` — file konfigurasi Firebase milik pembuat proyek; tidak disertakan dan jangan dibagikan ke publik.
