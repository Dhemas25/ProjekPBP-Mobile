# dhemas_musicstore

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.


## Nama    :   Dhemas Wicaksono Nugroho
## NPM     :   2206030786
## Kelas   :   PBP E##

### **TUGAS 7**

1.  **Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?**
    *   **Stateless Widget**
        -   Stateless widget tidak memiliki keadaan internal atau data yang dapat berubah. Mereka bersifat statis dan tidak dapat dirender ulang   dengan keadaan yang berbeda.
        -   Widget ini cocok digunakan ketika komponen antarmuka pengguna Anda tidak bergantung pada data yang berubah selama siklus hidupnya.
        -   Contoh: teks, gambar, ikon, tombol sederhana, dan elemen UI statis lainnya.
    *   **Stateful Widget**
        -   Stateful widget memiliki keadaan internal yang dapat berubah selama siklus hidup aplikasi. Mereka dapat di-render ulang ketika data dalam widget berubah.
        -   Widget ini cocok digunakan ketika Anda perlu mengikuti dan merespons perubahan data atau tindakan pengguna dalam aplikasi Anda.
        -   Contoh: formulir interaktif, daftar yang dapat digulir, tampilan halaman detail, dan komponen yang memerlukan interaktivitas.
    
2.  **Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.**
    1.  MyHomePage: Ini adalah kelas yang merepresentasikan halaman utama aplikasi. Diwarisi dari StatelessWidget, artinya tidak menyimpan state.
    2.  Scaffold: Widget yang memberikan struktur dasar untuk tampilan visual aplikasi seperti AppBar, body, dan floatingActionButton.
    3.  AppBar: Sebuah app bar dengan desain Material, digunakan untuk menampilkan judul aplikasi, branding, atau navigasi.
    4.  Text: Widget yang menampilkan teks dengan gaya yang bisa disesuaikan.
    5.  SingleChildScrollView: Widget scrollable untuk konten yang lebih besar daripada layar.
    6.  Padding: Widget yang memberikan ruang di sekitar widget anaknya.
    7.  Column: Menampilkan anak-anaknya dalam susunan vertikal.
    8.  GridView: Menampilkan widget anaknya dalam bentuk grid yang bisa discroll.
    9.  ShopCard: Widget kustom yang menerima objek ShopItem dan menampilkannya dalam bentuk card.
    10. Material: Widget yang menerapkan visual Material Design.

3.  **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)**
    1.  **Membuat Program Flutter Baru dengan Tema Inventory**
        -   jalankan perintah flutter create dhemas_musicstore untuk memulai proyek Flutter.
        -   Navigasi ke direktori proyek dengan cd dhemas_musicstore.
    2.  **Membuat Tiga Tombol Sederhana dengan Ikon dan Teks**
        -   Ubah main.dart dengan mengganti MyHomePage(title: 'Flutter Demo Home Page') menjadi MyHomePage().
        -   Di menu.dart:
            *   Definisikan tipe data untuk item yang akan dijual:

                class ShopItem {
                    final String name;
                    final IconData icon;

                    ShopItem(this.name, this.icon);
                }

            *   Modifikasi widget halaman menjadi stateless dan sesuaikan konstruktor:

                ({Key? key}) : super(key: key);
            
            *   Daftar barang yang akan dijual:
                
                final List<ShopItem> items = [
                    ShopItem("Lihat Item", Icons.checklist),
                    ShopItem("Tambah Item", Icons.add_shopping_cart),
                    ShopItem("Logout", Icons.logout),
                ];

            
            
