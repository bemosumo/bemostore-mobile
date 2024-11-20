# bemostore-mobile

<h2>
Muhammad Fawwaz Edsa Fatin Setiawan
  
2306275582
</h2>

<details>
  <summary>Tugas 7: Elemen Dasar Flutter</summary>

  #  Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
  ### Stateless Widget
  Stateless widget adalah widget yang tidak memiliki status yang bisa berubah selama siklus hidup widget itu. Artinya, begitu widget dibuat, dia tidak akan berubah meskipun ada perubahan data atau aksi dari   pengguna. Stateless widget cocok untuk elemen UI yang statis, seperti teks, gambar, atau elemen layout yang tidak akan berubah.
  Contoh:
  ```dart
  class MyTextWidget extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Text('Ini adalah Stateless Widget');
    }
  }
  ```

  ### Stateful Widget
  Stateful widget adalah widget yang memiliki status dan bisa berubah selama siklus hidup widget. Ketika statusnya berubah, widget akan dibangun ulang untuk mencerminkan perubahan tersebut. Widget ini biasanya dipakai kalau ada elemen UI yang bisa diubah oleh pengguna, seperti form input, tombol yang berubah warna saat ditekan, atau counter.
  Contoh:
  ```dart
  class MyCounterWidget extends StatefulWidget {
    @override
    _MyCounterWidgetState createState() => _MyCounterWidgetState();
  }
  
  class _MyCounterWidgetState extends State<MyCounterWidget> {
    int counter = 0;
  
    @override
    Widget build(BuildContext context) {
      return Column(
        children: [
          Text('Counter: $counter'),
          ElevatedButton(
            onPressed: () {
              setState(() {
                counter++;
              });
            },
            child: Text('Increment'),
          ),
        ],
      );
    }
  }
```

  ### Perbedaan Stateless dan Stateful Widget
  Stateless: Tidak bisa berubah, cocok untuk elemen statis.

  Stateful: Bisa berubah, cocok untuk elemen dinamis yang tergantung pada interaksi pengguna.

#  Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
  - MyApp (StatelessWidget)
MyApp adalah widget utama aplikasi yang berfungsi sebagai root atau titik masuk aplikasi Flutter. MyApp memulai aplikasi dengan MaterialApp, yaitu komponen utama Flutter untuk aplikasi berbasis material design. Stateless karena sifatnya yang tidak berubah atau dinamis.

- MaterialApp
Ini adalah konfigurasi utama aplikasi yang mencakup pengaturan global seperti:

    -  title: Menyediakan judul aplikasi.
    -  theme: Mengatur tema aplikasi secara keseluruhan. Menggunakan ThemeData dengan skema warna khusus (primary merah dan secondary merah tua).
    -  home: Menentukan halaman awal aplikasi, yang di sini adalah MyHomePage.
    
- ThemeData
Mengatur tampilan dan tema keseluruhan aplikasi. Contoh utama yang diatur adalah ColorScheme, di mana:
    - primary: Warna utama aplikasi, yaitu merah.
    - secondary: Warna sekunder aplikasi, merah tua.
  
- MyHomePage (StatelessWidget)
Halaman utama aplikasi, di mana terdapat informasi dasar seperti NPM, nama, dan kelas. Di dalamnya ada daftar item untuk menu, yang diatur menggunakan widget bernama ItemHomepage.

- Scaffold
Struktur utama halaman yang menyediakan kerangka dasar aplikasi, seperti:
    - AppBar: Sebagai header dengan judul aplikasi.
    - body: Tempat di mana isi utama halaman berada.
  
- AppBar
Menyediakan header atau bagian atas halaman dengan gaya teks khusus dan warna latar belakang sesuai tema yang sudah diatur.

- Padding
Membantu mengatur jarak di sekitar widget untuk tampilan yang lebih rapi dan lebih mudah dibaca.

- InfoCard (StatelessWidget)
Sebuah kartu informasi yang memuat judul (misalnya, NPM) dan isinya (seperti nomor NPM). Menggunakan Card untuk tampilan seperti kartu yang ringan dengan bayangan.

- SizedBox
Menyediakan jarak antar widget atau digunakan untuk mengatur ukuran widget tertentu.

- GridView.count
Menampilkan menu aplikasi dalam bentuk grid dengan jumlah kolom yang tetap, yaitu tiga kolom. Setiap item dalam grid ini adalah ItemCard yang berasal dari daftar ItemHomepage.

- ItemHomepage (Model Data)
Model data sederhana yang berfungsi untuk menyimpan name dan icon yang terkait dengan setiap item dalam menu.

- ItemCard (StatelessWidget)
Kartu yang menampilkan ikon dan nama item. Menggunakan Material dengan InkWell agar memiliki efek klik, sehingga saat pengguna menekan kartu, akan muncul SnackBar.

- SnackBar
Komponen untuk menampilkan pesan sementara di bagian bawah layar ketika pengguna menekan ItemCard, memberikan feedback instan kepada pengguna.

#  Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
  Fungsi `setState()` adalah metode yang digunakan pada Stateful Widget untuk memberi tahu Flutter bahwa ada perubahan pada status atau data yang memerlukan rebuild. Ketika `setState()` dipanggil, Flutter akan membangun ulang UI dengan data terbaru.

Contoh variabel yang bisa terpengaruh:

- Counter atau angka: Seperti contoh counter di atas.
- Input teks: Untuk mendapatkan teks yang baru dari pengguna.
- Status tombol atau warna: Jika kamu ingin tombol berubah warna atau bentuk setelah ditekan.

#  Jelaskan perbedaan antara `const` dengan `final`.
- const: Nilai tetap selama compile-time. Artinya, jika kita menetapkan const, nilai ini tidak akan pernah berubah, bahkan sebelum aplikasi dijalankan.
- final: Nilai tetap selama runtime. Artinya, nilai tersebut hanya bisa ditetapkan sekali, tapi penentuannya bisa dilakukan saat runtime (misalnya hasil dari suatu fungsi atau input pengguna).

#  Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.

### Membuat projek flutter
jalankan command berikut pada terminal dengna direktori dimana projek ingin disimpan
```
flutter create bemostore_app
cd /bemostore_app
```

### Merapikan struktur proyek
Buat file bernama `menu.dart` pada direktori yang sama dengan file bernama `main.dart`, kemudian pindahkan class `MyHomePage` dan `_MyHomePageState` dari `main.dart` ke `menu.dart`.
Tambahkan import berikut pada `menu.dart`
```dart
import 'package:flutter/material.dart';
```
dan juga import berikut pada `main.dart`
```dart
import 'package:bemostore_app/menu.dart';
```

### Mengubah ColorScheme
```dart
        colorScheme: ColorScheme.fromSwatch(
              primarySwatch: Colors.blueGrey,
        ).copyWith(secondary: Colors.blueGrey[900]),      
      )
```

### Mmebuat class baru bernama ItemHomepage yang berisi atribut-atribut dari card yang akan dibuat
Tambahkan pada `menu.dart`
```dart
class ItemHomepage {
     final String name;
     final IconData icon;
     final Color color; 

     ItemHomepage(this.name, this.icon, this.color);
 }
```

### Membuat list of ItemHomepage yang berisi tombol-tombol yang akan tambahkan pada class MyHomePage.
```dart
class MyHomePage extends StatelessWidget {
    ...
    final String npm = '2306275582'; // NPM
    final String name = 'Muhammad Fawwaz Edsa Fatin Setiawan '; // Nama
    final String className = 'PBP D'; // Kelas
    final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.mood, const Color.fromARGB(255, 41, 53, 57)!),
    ItemHomepage("Tambah Produk", Icons.add, const Color.fromARGB(255, 37, 48, 38)),
    ItemHomepage("Logout", Icons.logout, const Color.fromARGB(255, 52, 48, 42)),
    ....
}
```

### Menampilkan SnackBar
```dart
class ItemCard extends StatelessWidget {
  // Menampilkan kartu dengan ikon dan nama.

  final ItemHomepage item; 
  
  const ItemCard(this.item, {super.key}); 

  @override
  Widget build(BuildContext context) {
    return Material(
      // Menentukan warna latar belakang dari tema aplikasi.
      color: item.color,
      // Membuat sudut kartu melengkung.
      borderRadius: BorderRadius.circular(12),
      
      child: InkWell(
        // Aksi ketika kartu ditekan.
        onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
        },
        // Container untuk menyimpan Icon dan Text
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              // Menyusun ikon dan teks di tengah kartu.
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  } 
}
```
</details>

<details>
  <summary>Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements</summary>

#  Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?
Di Flutter, `const` digunakan untuk mendeklarasikan objek yang sifatnya konstan dan tidak akan berubah sepanjang masa pakai aplikasi. Dengan mendeklarasikan widget atau nilai sebagai `const`, Flutter hanya membuat satu instance dari objek tersebut di memori. Ini mengurangi kebutuhan alokasi memori yang berulang dan meningkatkan performa aplikasi, karena objek yang didefinisikan sebagai `const` tidak akan dibuat ulang. Contohnya adalah teks atau ikon tetap, seperti di dalam `AppBar` atau item statis dalam list.

Contoh penggunaan `const`:
```dart
const Text('Welcome to Bemostore');
const Icon(Icons.list_alt_rounded);
```

Dengan menggunakan `const`, kita memberitahu Flutter bahwa objek ini bersifat statis dan tidak perlu dibuat ulang, sehingga mempercepat proses rendering dan menghemat memori.

Sebaiknya, `const` digunakan pada widget atau variabel yang bersifat tetap dan tidak akan berubah, misalnya pada widget `Text` atau `Icon` yang tampilannya tidak berubah selama aplikasi berjalan. Ini juga berlaku untuk widget yang terletak dalam hierarki yang jarang diubah. Sebaliknya, `const` tidak cocok untuk objek yang bersifat dinamis atau berubah, seperti elemen yang bergantung pada input pengguna atau data dari API. Jika widget berubah, penggunaan `const` akan menyebabkan error karena Flutter tidak dapat membuat ulang objek tersebut.

#  Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
`Column` dan `Row` adalah widget utama dalam Flutter untuk menata elemen UI secara vertikal atau horizontal. `Column` digunakan untuk menampilkan widget secara vertikal dari atas ke bawah, dan sering digunakan untuk menata elemen-elemen bertumpuk seperti daftar item atau form. Di sisi lain, `Row` menata widget secara horizontal dari kiri ke kanan, cocok untuk toolbar atau item yang perlu tampil berdampingan.

Contoh Implementasi `Column`:
```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    const Text('Welcome to Bemostore', style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold)),
    const SizedBox(height: 16.0),
    ElevatedButton(
      onPressed: () {},
      child: const Text('Explore Products'),
    ),
  ],
);
```
Pada contoh ini, `Column` digunakan untuk menyusun `Text` dan `Button` secara vertikal.

Contoh Implementasi `Row`:
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Icon(Icons.home),
    Icon(Icons.search),
    Icon(Icons.settings),
  ],
);
```
Di sini, `Row` menata beberapa `Icon` secara horizontal dengan jarak yang sama.

#  Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!
Pada halaman form di tugas ini, saya menggunakan beberapa elemen input utama yaitu `TextFormField`. Elemen ini digunakan untuk menerima masukan pengguna untuk produk, deskripsi, dan harga produk. `TextFormField` juga dilengkapi dengan validator untuk memastikan bahwa nilai yang dimasukkan memenuhi syarat tertentu, seperti tidak boleh kosong dan harga harus berupa angka. Validator ini memberikan umpan balik yang penting kepada pengguna.

Selain `TextFormField`, Flutter juga memiliki elemen input lain seperti `Checkbox`, `RadioButton`, `Switch`, dan `Slider`. Namun, elemen-elemen ini tidak digunakan dalam tugas ini karena form ini hanya membutuhkan masukan berupa teks.

Contoh Implementasi `TextFormField`:
```dart
TextFormField(
  decoration: InputDecoration(
    hintText: "Masukkan Nama Produk",
    labelText: "Produk",
    border: OutlineInputBorder(
      borderRadius: BorderRadius.circular(5.0),
    ),
  ),
  onChanged: (String? value) {
    setState(() {
      _product = value!;
    });
  },
  validator: (String? value) {
    if (value == null || value.isEmpty) {
      return "Produk tidak boleh kosong!";
    }
    return null;
  },
);
```
Pada contoh di atas, `TextFormField` digunakan untuk input produk dengan validator yang memastikan kolom ini tidak kosong.

#  Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Dalam Flutter, tema aplikasi diatur melalui `ThemeData` yang didefinisikan di dalam `MaterialApp`. Dengan menggunakan `ThemeData`, kita bisa menentukan warna utama, warna latar belakang, serta gaya teks yang seragam untuk seluruh aplikasi. Tema yang konsisten ini membantu aplikasi memiliki tampilan yang seragam, sehingga lebih enak dilihat dan user-friendly.

Pada tugas ini, saya telah mengatur tema di dalam `MaterialApp`, seperti warna primer yang ditetapkan pada `AppBar` dan elemen lainnya agar seluruh aplikasi memiliki skema warna yang serupa.

Contoh Implementasi Tema:
```dart
MaterialApp(
  theme: ThemeData(
    colorScheme: ColorScheme.fromSwatch(
      primarySwatch: Colors.teal,
    ).copyWith(secondary: Colors.grey[900]),
  ),
  home: MyHomePage(),
);
```
Di sini, warna utama aplikasi diatur dengan `primarySwatch`, yang secara otomatis akan diterapkan pada elemen-elemen yang menggunakan tema, seperti `AppBar`.

#  Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
Pada aplikasi Flutter dengan banyak halaman, `Navigator` digunakan untuk menangani navigasi antar halaman. `Navigator` berfungsi sebagai pengelola stack halaman, yang memungkinkan kita untuk menambah atau mengganti halaman di atas halaman saat ini. Dalam tugas ini, saya menggunakan `Navigator.pushReplacement` untuk mengganti halaman yang sedang dibuka dengan halaman lain ketika pengguna memilih menu pada drawer. Metode ini membuat pengguna berpindah halaman tanpa kembali ke halaman sebelumnya, memberikan pengalaman navigasi yang lebih mulus.

Contoh Implementasi Navigasi:
```dart
ListTile(
  leading: const Icon(Icons.add_shopping_cart_outlined),
  title: const Text('Tambah Produk'),
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (context) => const ProductEntryFormPage()),
    );
  },
);
```
Pada contoh di atas, `Navigator.pushReplacement` digunakan untuk mengarahkan pengguna ke halaman `ProductEntryFormPage` saat mereka mengetuk item menu "Tambah Produk".

</details>

<details>
  <summary>Tugas 9: Integrasi Layanan Web Django dengan Aplikasi Flutter</summary>

  # Mengapa Perlu Membuat Model untuk Pengambilan/Pengiriman Data JSON? Apakah Akan Terjadi Error Jika Tidak Membuat Model Terlebih Dahulu?
Model diperlukan untuk memberikan struktur pada data JSON yang diterima atau dikirimkan, sehingga mempermudah pengelolaan dan manipulasi data dalam aplikasi. Dengan model, Anda dapat memvalidasi bahwa data memiliki format yang sesuai, meminimalkan risiko kesalahan saat memproses informasi, serta membuat kode lebih terstruktur dan mudah dipelihara.

Jika Anda tidak membuat model, tidak akan terjadi error langsung, tetapi ada beberapa risiko:

- Kesalahan Typo: Penulisan key JSON secara manual dapat menyebabkan kesalahan.
- Kurangnya Validasi: Tidak ada mekanisme untuk memastikan struktur data sesuai.
- Kesulitan Maintenance: Kode menjadi lebih sulit dibaca dan dipelihara karena data harus diakses melalui key string secara langsung.

# Jelaskan Fungsi dari Library HTTP yang Sudah Kamu Implementasikan pada Tugas Ini
Library http berfungsi sebagai alat untuk melakukan komunikasi antara aplikasi Flutter dan server Django melalui protokol HTTP. Beberapa fungsi utama dari library ini adalah:

## Mengirim Permintaan HTTP:
- Menggunakan metode seperti POST, GET, PUT, dan DELETE untuk berinteraksi dengan API server.
## Mengirim dan Menerima Data JSON:
- Memproses body request dalam format JSON untuk mengirimkan data ke server.
## Mendapatkan Respons dari Server:
- Menerima respons dari server (biasanya dalam format JSON) untuk digunakan di aplikasi.
## Error Handling:
- Menangani error jaringan atau status kode HTTP seperti 404 (Not Found) dan 500 (Internal Server Error).

# Jelaskan Fungsi dari CookieRequest dan Mengapa Instance CookieRequest Perlu untuk Dibagikan ke Semua Komponen di Aplikasi Flutter
Fungsi CookieRequest:

## Menyimpan Cookie:
- Digunakan untuk menyimpan sesi autentikasi pengguna, misalnya setelah login.
## Melacak Status Pengguna:
- Menggunakan cookie untuk mengetahui apakah pengguna sudah login.
- Melakukan Permintaan HTTP dengan Autentikasi:
- Mengirimkan cookie yang relevan pada setiap permintaan HTTP ke server.

## Mengapa Dibagikan ke Semua Komponen?
### State Global:
- Status autentikasi pengguna (seperti login) harus tersedia di semua bagian aplikasi.
### Kemudahan Akses:
- Dengan membagikan instance, semua halaman dapat menggunakan CookieRequest untuk mengakses atau mengirim data tanpa inisialisasi ulang.
### Efisiensi:
- Menghindari duplikasi pengelolaan sesi atau autentikasi.

# Jelaskan Mekanisme Pengiriman Data Mulai dari Input hingga Dapat Ditampilkan pada Flutter
## Input Data:
- Pengguna mengisi formulir di Flutter.
- Data JSON dikirimkan ke server Django menggunakan metode POST melalui library http atau CookieRequest.

## Proses di Server Django:
- Django menerima data JSON melalui endpoint API.
- Data diproses, diverifikasi, dan disimpan ke dalam database.
- Django mengembalikan respons (biasanya dalam format JSON) ke Flutter.

## Pengambilan Data:
- Flutter mengirimkan permintaan GET ke endpoint Django.
- Django mengirimkan data JSON dari database.

## Konversi JSON ke Model Flutter:
- Data JSON dari server dikonversi ke model Flutter (misalnya ProductEntry) menggunakan metode seperti fromJson.

## Penampilan di UI Flutter:
- Data yang sudah dikonversi ke model digunakan untuk membangun widget (seperti ListView atau GridView) untuk ditampilkan ke pengguna.

# Jelaskan Mekanisme Autentikasi dari Login, Register, hingga Logout
## Register:
- Pengguna mengisi formulir pendaftaran di Flutter.
- Data seperti username, email, dan password dikirimkan ke endpoint register Django menggunakan POST.
- Django memvalidasi data dan membuat akun pengguna di database.

## Login:
- Pengguna memasukkan username dan password di Flutter.
- Data dikirimkan ke endpoint login Django.
- Django memverifikasi kredensial dan mengembalikan cookie autentikasi jika berhasil.
- Cookie ini disimpan di CookieRequest di aplikasi Flutter.

## Logout:
- Flutter mengirim permintaan logout ke Django.
- Django menghapus sesi pengguna (cookie) dari server.

## Tampilan Menu pada Flutter:
- Setelah login, Flutter memeriksa keberadaan cookie autentikasi di CookieRequest.
- Jika cookie valid, pengguna diarahkan ke halaman utama aplikasi.
- Jika tidak valid, pengguna tetap diarahkan ke halaman login
</details>
