# bemostore-mobile

<details>
  <summary>Tugas 7: Elemen Dasar Flutter</summary>

  #  Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
  ## Stateless Widget
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

  ## Stateful Widget
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
  - Text: Menampilkan teks sederhana.
  - Container: Membuat kotak dengan properti seperti warna, padding, dan margin.
  - Column dan Row: Menyusun widget secara vertikal (Column) atau horizontal (Row).
  - ListView: Menampilkan daftar item yang bisa di-scroll.
  - ElevatedButton: Tombol yang bisa ditekan, dengan efek bayangan.
  - TextField: Input teks dari pengguna.
  - Image: Menampilkan gambar, baik dari aset maupun dari jaringan.

#  Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
  Fungsi `setState()` adalah metode yang digunakan pada Stateful Widget untuk memberi tahu Flutter bahwa ada perubahan pada status atau data yang memerlukan rebuild. Ketika `setState()` dipanggil, Flutter akan membangun ulang UI dengan data terbaru.

Contoh variabel yang bisa terpengaruh:

- Counter atau angka: Seperti contoh counter di atas.
- Input teks: Untuk mendapatkan teks yang baru dari pengguna.
- Status tombol atau warna: Jika kamu ingin tombol berubah warna atau bentuk setelah ditekan.

#  Jelaskan perbedaan antara `const` dengan `final`.
- const: Nilai tetap selama compile-time. Artinya, jika kita menetapkan const, nilai ini tidak akan pernah berubah, bahkan sebelum aplikasi dijalankan.
- final: Nilai tetap selama runtime. Artinya, nilai tersebut hanya bisa ditetapkan sekali, tapi penentuannya bisa dilakukan saat runtime (misalnya hasil dari suatu fungsi atau input pengguna).
</details>
