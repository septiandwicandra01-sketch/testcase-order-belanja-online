# Test Case: Proses Order Aplikasi Belanja Online

Repository ini berisi test case untuk menguji proses order pada aplikasi belanja online.

## Deskripsi Proses

1. User memasukkan produk ke keranjang dengan quantity yang diinginkan.
2. Di halaman keranjang, user mengisi alamat pengiriman.
3. User klik tombol **Beli**.
4. Setelah proses order selesai, sistem membentuk **Order Number**.

## Asumsi

Soal tidak menyebutkan batas maksimal quantity, panjang alamat, atau metode pembayaran, sehingga test case disusun berdasarkan asumsi berikut:

- User sudah login.
- Quantity minimal 1 dan tidak boleh melebihi stok.
- Alamat pengiriman wajib diisi.
- Order Number bersifat unik untuk setiap order.

## Positive Case

| ID | Skenario | Data Uji | Expected Result |
|---|---|---|---|
| TC-P01 | Order dengan alur lengkap yang valid | Produk A, qty 2, alamat valid, klik Beli | Order berhasil dan Order Number terbentuk |
| TC-P02 | Tambah produk ke keranjang dengan qty 1 | Produk A, qty 1 | Produk masuk keranjang dengan qty 1 |
| TC-P03 | Tambah produk dengan qty lebih dari 1 | Produk A, qty 5 | Produk masuk keranjang dengan qty 5 |
| TC-P04 | Tambah beberapa produk berbeda | Produk A dan Produk B | Kedua produk tampil di keranjang |
| TC-P05 | Ubah quantity di halaman keranjang | Qty 2 diubah menjadi 3 | Qty dan total harga terupdate otomatis |
| TC-P06 | Hapus produk dari keranjang | Hapus Produk A | Produk hilang dan total harga terupdate |
| TC-P07 | Total harga dihitung dengan benar | Harga x qty untuk beberapa produk | Total sesuai penjumlahan |
| TC-P08 | Order Number unik untuk setiap order | Buat 2 order berbeda | Kedua Order Number berbeda |
| TC-P09 | Order Number tersimpan di riwayat pesanan | Selesaikan order lalu buka riwayat | Order tampil dengan Order Number yang sama |
| TC-P10 | Isi keranjang tetap tersimpan setelah pindah halaman | Tambah produk, pindah halaman, kembali | Isi keranjang tidak berubah |

## Negative Case

| ID | Skenario | Data Uji | Expected Result |
|---|---|---|---|
| TC-N01 | Klik Beli dengan alamat kosong | Alamat dikosongkan | Muncul pesan error "Alamat harus diisi", order tidak diproses |
| TC-N02 | Klik Beli dengan keranjang kosong | Tidak ada produk | Tombol Beli disabled / muncul pesan keranjang kosong |
| TC-N03 | Quantity diisi 0 | Qty: 0 | Ditolak, minimal qty 1 |
| TC-N04 | Quantity diisi angka negatif | Qty: -1 | Ditolak dengan pesan error |
| TC-N05 | Quantity diisi huruf / simbol | Qty: abc, @# | Ditolak / input tidak bisa diketik |
| TC-N06 | Quantity melebihi stok | Stok 10, qty 11 | Muncul pesan stok tidak mencukupi |
| TC-N07 | Produk dengan stok habis | Produk stok 0 | Tidak bisa ditambahkan ke keranjang |
| TC-N08 | Alamat melebihi batas karakter | Alamat sangat panjang | Ditolak atau dibatasi dengan pesan validasi |
| TC-N09 | Klik tombol Beli berkali-kali | Klik Beli 2x cepat | Hanya satu order terbentuk, tidak duplikat |
| TC-N10 | Koneksi terputus saat klik Beli | Matikan internet lalu klik Beli | Muncul pesan error koneksi, order tidak terbentuk setengah jalan |
| TC-N11 | Belum login saat order | User belum login | Diarahkan ke halaman login |
| TC-N12 | Harga/stok berubah saat produk di keranjang | Admin mengubah harga setelah produk masuk keranjang | Harga terbaru ditampilkan atau ada notifikasi perubahan |

## Struktur Repository

```
testcase-order-belanja-online/
├── README.md          # Dokumentasi dan test case
└── test-cases.csv     # Test case dalam format CSV (bisa dibuka di Excel)
```

## Author

Dibuat oleh: [Septian Dwi Candra]
