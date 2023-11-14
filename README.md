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

    3.  **Memunculkan Snackbar dengan tulisan:**
        -   ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));


### **TUGAS 8**

1.  **Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!**
    -   **Navigator.Push()**
        Metode ini digunakan untuk menambahkan halaman baru ke dalam tumpukan navigasi (navigation stack).
        -   Contoh: 
            if (item.name == "Tambah Produk") {
              // TODO: Gunakan Navigator.push untuk melakukan navigasi ke MaterialPageRoute yang mencakup ShopFormPage.
              Navigator.push(context,
              MaterialPageRoute(builder: (context) => const ShopFormPage()));
            }
    -   **Navigator.pushReplacement()**
        Metode ini digunakan untuk menambahkan halaman baru ke dalam tumpukan navigasi, tetapi dengan menggantikan halaman saat ini.
        -   contoh:
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },

2.  **Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**
    1.  Container:
        Digunakan untuk menentukan area konten di layar. Container dapat berisi widget lain dan dapat dikonfigurasi dengan properti seperti padding, margin, dan dekorasi.
    2.  Row dan Column:
        Digunakan untuk mengatur widget secara horizontal (Row) atau vertikal (Column). 
    3.  ListView:
        Digunakan untuk menampilkan daftar item yang dapat di-scroll. 
    4.  GridView:
        Mirip dengan ListView, tetapi digunakan untuk menampilkan item dalam bentuk grid.

3.  **Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**
    Elemen input yang dipakai pada form adalah string name, integer amount, dan string description. Hal ini sesuai dengan proyek django saya yang memanfaatkan model produk dengan atribut name, amount, description.

4.  **Bagaimana penerapan clean architecture pada aplikasi Flutter?**

5.  **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**
    1.  **Membuat minimal satu halaman baru pada aplikasi, yaitu halaman formulir tambah item baru**
        -   membuat file baru yaitu shoplist_form.dart
        -   pada class shopformstate menambahkan variabel _name, _amount, _description
        -   membuat input field form dengan validator, contohnya untuk elemen name:
            Padding(
                          padding: const EdgeInsets.all(8.0),
                          child: TextFormField(
                            decoration: InputDecoration(
                              hintText: "Nama Produk",
                              labelText: "Nama Produk",
                              border: OutlineInputBorder(
                                borderRadius: BorderRadius.circular(5.0),
                              ),
                            ),
                            onChanged: (String? value) {
                              setState(() {
                                _name = value!;
                              });
                            },
                            validator: (String? value) {
                              if (value == null || value.isEmpty) {
                                return "Nama tidak boleh kosong!";
                              }
                              return null;
                            },
                          ),
                        ),
        -   Kemudian membuat untuk tiap elemen lain
        -   Memiliki tombol save:
            child: const Text(
                              "Save",
                              style: TextStyle(color: Colors.white),
                            ),
    2.  **Mengarahkan pengguna ke halaman form tambah item baru ketika menekan tombol Tambah Item pada halaman utama.**
        if (item.name == "Tambah Produk") {
              // TODO: Gunakan Navigator.push untuk melakukan navigasi ke MaterialPageRoute yang mencakup ShopFormPage.
              Navigator.push(context,
              MaterialPageRoute(builder: (context) => const ShopFormPage()));
            }

    3.  **Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah pop-up setelah menekan tombol Save pada halaman formulir tambah item baru.**
        Dalam shoplift_form.dart:

        onPressed: () {
            if (_formKey.currentState!.validate()) {
                showDialog(
                    context: context,
                    builder: (context) {
                        return AlertDialog(
                            title: const Text('Produk berhasil tersimpan'),
                            content: SingleChildScrollView(
                                child: Column(
                                    crossAxisAlignment:
                                    CrossAxisAlignment.start,
                                    children: [
                                        Text('Nama: $_name'),
                                        Text('Jumlah: $_amount'),
                                        Text('Deskripsi: $_description'),
                                    ],
                                ),
                            ),
                            actions: [
                                TextButton(
                                    child: const Text('OK'),
                                    onPressed: () {
                                        Navigator.pop(context);
                                    },
                                ),
                            ],
                        );
                    },
                );
                _formKey.currentState!.reset();
                }
            },
    4.  **Membuat sebuah drawer pada aplikasi dengan ketentuan**
        -   Drawer minimal memiliki dua buah opsi, yaitu Halaman Utama dan Tambah Item.
            Menggunakan ListTile():

            ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Halaman Utama'),
            // Bagian redirection ke MyHomePage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
            ),
            ListTile(
                leading: const Icon(Icons.add_shopping_cart),
                title: const Text('Tambah Produk'),
                // Bagian redirection ke ShopFormPage
                onTap: () {
                Navigator.push(
                    context,
                    MaterialPageRoute(
                    builder: (context) => ShopFormPage(), // Gantilah dengan nama halaman yang sesuai
                    ),
                );
                },
            ),
        
        -   Ketika memiih opsi Halaman Utama, maka aplikasi akan mengarahkan pengguna ke halaman utama.
            Menggunakan navigator.pushReplacement() routing ke MyHomePage()

            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },

        -   Ketika memiih opsi (Tambah Item), maka aplikasi akan mengarahkan pengguna ke halaman form tambah item baru
            Menggunakan navigator.push()

            onTap: () {
                Navigator.push(
                    context,
                    MaterialPageRoute(
                    builder: (context) => ShopFormPage(), // Gantilah dengan nama halaman yang sesuai
                    ),
                );
            },



            
            
