Nusantara Cerdas Mobile

Nusantara Cerdas Mobile adalah aplikasi mobile berbasis Flutter yang dirancang sebagai prototype layanan Smart City. Aplikasi menyediakan informasi mengenai pilar Smart City serta fitur layanan untuk warga. Pada Modul 5, aplikasi ditingkatkan dengan manajemen state menggunakan Cubit (flutter_bloc) untuk layanan favorit dan pengajuan layanan, tanpa mengubah kerangka navigasi dari Modul 2.

Fitur Utama
Beranda — Menampilkan informasi 6 pilar Smart City.
Layanan — Daftar layanan kota per bidang (Perizinan, Kesehatan, Transportasi) dengan ikon bintang untuk menandai layanan favorit.
Detail Layanan — Informasi detail layanan dan tombol Ajukan Permohonan yang menampilkan indikator sedang mengirim.
Warga — Halaman warga dengan bagian Layanan Favorit yang tampil reaktif, tanpa memandang bidang asal layanan.
Badge Pengajuan — Jumlah layanan yang sedang diajukan tampil pada ikon tujuan Warga, baik di NavigationBar (layar sempit) maupun NavigationRail (layar lebar).
Riwayat Laporan — Menampilkan riwayat laporan warga.
Pengaturan Kota — Menyediakan pengaturan terkait kota.
Tentang Aplikasi — Menampilkan informasi aplikasi.
Route Tidak Dikenal — Menangani route yang tidak tersedia.
Teknologi
Flutter dan Dart
Material Design 3
Flutter Navigator / Named Routes
flutter_bloc (Cubit, MultiBlocProvider, BlocBuilder, BlocSelector)
Manajemen State
Data	Pendekatan	Alasan
Layanan favorit (Set<String>)	FavoritCubit	Dipakai bersama oleh halaman Layanan dan Warga
Daftar pengajuan dan totalPengajuan	PengajuanCubit	Dipakai oleh halaman Detail dan badge navigasi
Status sedang mengirim	setState()	State lokal yang hanya relevan bagi satu halaman
Tab bidang dan indeks navigasi	setState() / TabController	State lokal tampilan

Widget yang dipakai: context.read() untuk memicu aksi, BlocBuilder untuk daftar favorit, dan BlocSelector untuk ikon bintang serta badge agar hanya bagian kecil yang dibangun ulang.

Struktur Folder
text
lib/
├── main.dart
├── cubit/
│   ├── favorit_cubit.dart
│   └── pengajuan_cubit.dart
├── navigation/
│   ├── app_routes.dart
│   └── kerangka_navigasi.dart
└── pages/
    ├── beranda_page.dart
    ├── layanan_page.dart
    ├── detail_layanan_page.dart
    ├── warga_page.dart
    ├── riwayat_laporan_page.dart
    ├── pengaturan_kota_page.dart
    ├── tentang_aplikasi_page.dart
    └── route_tidak_dikenal_page.dart
Penjelasan Singkat
main.dart → Entry point; MultiBlocProvider dipasang di atas MaterialApp.
cubit/ → Logika state favorit dan pengajuan.
navigation/ → Routing dan kerangka navigasi adaptif.
pages/ → Seluruh halaman aplikasi.
Cara Menjalankan

Pastikan Flutter sudah terpasang, kemudian jalankan:

bash
flutter pub get
flutter run

Untuk menjalankan di peramban: flutter run -d chrome. Untuk mengecek environment: flutter doctor.

Alur Navigasi
text
Beranda
├── Layanan (tab Perizinan / Kesehatan / Transportasi)
│   └── Detail Layanan  → Ajukan Permohonan (kembali dengan Navigator.pop)
├── Warga (Layanan Favorit, badge pengajuan)
│   └── Riwayat Laporan
├── Pengaturan Kota
└── Tentang Aplikasi
Pengembangan Selanjutnya
Backend dan REST API
Penyimpanan permanen (database / local storage) untuk favorit dan pengajuan
Login dan registrasi
Sistem laporan warga
Notifikasi
Data layanan secara real-time
Status

Project ini merupakan prototype aplikasi Smart City berbasis Flutter untuk keperluan pembelajaran dan pengembangan aplikasi mobile.