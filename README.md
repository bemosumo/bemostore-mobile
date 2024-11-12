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

  # Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?
  Penggunaan `const` memiliki peran penting dalam menjaga efisiensi dan performa aplikasi. Ketika kita mendeklarasikan objek sebagai `const`, objek tersebut menjadi immutable atau tidak dapat diubah. Ini berarti Flutter hanya membuat objek tersebut satu kali dan menyimpannya dalam memori sepanjang aplikasi berjalan, mengurangi kebutuhan akan alokasi memori tambahan. Penggunaan `const` ini sangat berguna pada widget atau nilai yang bersifat statis dan tidak akan berubah, seperti teks atau ikon tetap. Keuntungan utama dari `const` adalah efisiensi memori dan peningkatan performa render, karena objek yang bersifat `const` tidak perlu di-render ulang, menghemat waktu saat aplikasi berjalan. Selain itu, `const` juga memberikan stabilitas dengan memastikan bahwa data tidak berubah secara tak terduga selama runtime, mengurangi risiko error. Namun, `const` tidak ideal untuk objek atau widget yang berubah selama aplikasi berjalan, seperti item dalam `ListView` yang diambil dari server atau widget yang dipengaruhi oleh interaksi pengguna, karena perubahan tersebut akan menyebabkan error jika dipaksa menjadi `const`.

# Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
Dalam penataan layout, widget `Column` dan `Row` adalah dua pilihan utama yang digunakan berdasarkan orientasi elemen. `Column` menata widget secara vertikal dari atas ke bawah dan cocok untuk tampilan yang membutuhkan elemen bertumpuk, seperti daftar item atau form UI. Sebaliknya, `Row` menata widget secara horizontal dari kiri ke kanan, cocok untuk toolbar atau tombol yang disusun berdampingan. Keduanya memiliki properti `mainAxisAlignment` dan `crossAxisAlignment` yang memungkinkan pengaturan posisi anak-anak widget di sepanjang sumbu utama dan sumbu silang. Misalnya, `Column` dapat diatur agar elemen-elemen di dalamnya berada di tengah atau disejajarkan ke kiri, sementara `Row` dapat membuat elemen-elemen memiliki jarak sama rata di sepanjang sumbu horizontal. Singkatnya, pemilihan antara `Column` dan `Row` tergantung pada arah susunan yang diinginkan, sementara penggunaan `const` yang bijak pada widget atau value statis akan membantu meningkatkan efisiensi aplikasi Flutter secara keseluruhan.

</details>
