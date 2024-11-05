WarunkChill🏪🥘🛒 <br>
"The Perfect Place to Chill and Fill." <br>

- Nama   : Akhyar Rasyid Asy syifa <br>
- NPM    : 2306241682  <br>
- Kelas  : PBP - D <br>

## Tugas 7 - PBP 2024/2025
### 1. Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
- **Stateless Widget** adalah widget yang bersifat statis dan tidak memiliki state atau keadaan yang berubah. `StatelessWidget` hanya dibangun sekali ketika di-render dan tidak akan berubah selama aplikasi berjalan. Contohnya, widget seperti `Text`, `Icon`, atau `Container`, yang tidak memerlukan interaksi atau perubahan data.
- **Stateful Widget** adalah widget yang memiliki state atau keadaan yang dapat berubah. `StatefulWidget` dibangun ulang setiap kali terjadi perubahan pada state-nya menggunakan fungsi `setState()`. Widget ini cocok untuk komponen yang membutuhkan perubahan tampilan karena interaksi pengguna atau perubahan data, seperti `Checkbox`, `TextField`, `Radio`, `Slider`, form input, atau tombol yang merespons aksi pengguna dan memerlukan pembaruan tampilan setiap kali state berubah.

Perbedaan utama antara keduanya terletak pada pengelolaan keadaan: stateless widget sederhana dan efisien, sedangkan stateful widget lebih kompleks dan memerlukan metode untuk mengelola perubahan keadaan.

### 2. Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
built in widget yang saya gunakan pada proyek ini adalah sebagai berikut ;
- `MaterialApp`: Berfungsi sebagai komponen utama aplikasi Flutter, bertindak sebagai root dari semua widget dalam aplikasi.
- `Scaffold`: Menyediakan struktur dasar halaman, meliputi area seperti appBar dan body untuk menyusun tampilan aplikasi.
- `AppBar`: Menampilkan bagian atas halaman yang berfungsi sebagai bar judul, biasanya untuk menampilkan nama atau judul aplikasi.
- `Text`: Digunakan untuk menampilkan teks pada tampilan aplikasi.
- `GridView`: Menyusun item dalam format grid atau kotak-kotak, cocok untuk menampilkan daftar item dalam tata letak kolom dan baris.
- `Card`: Membuat tampilan berupa kartu yang dapat diisi informasi atau widget lainnya, memberikan efek elevasi (bayangan).
- `Container`: Komponen dasar yang berfungsi sebagai wadah bagi widget lain dan memungkinkan pengaturan ukuran, warna, margin, dan padding.
- `Column dan Row`: Digunakan untuk menata widget secara berurutan, Column secara vertikal dan Row secara horizontal.
- `Icon`: Menampilkan ikon gambar yang dapat dipilih dari berbagai simbol standar yang tersedia di Flutter.
- `InkWell`: Memberikan efek visual (ripple) saat suatu widget disentuh atau ditekan, meningkatkan interaksi pengguna.
- `SnackBar`: Memunculkan pesan singkat sementara di bagian bawah layar, biasanya untuk memberi umpan balik kepada pengguna.
- `Material`: Memberikan dasar bagi tampilan yang mengikuti gaya desain material, memungkinkan elemen-elemen aplikasi terlihat dan berperilaku sesuai dengan standar Material Design.

dan terdapat custom widget yang saya implementasikan:
- `InfoCard`: widget kustom yang digunakan untuk menampilkan informasi statis seperti NPM, Nama, dan Kelas.
- `ItemCardwidget`: widget kustom yang digunakan untuk menampilkan satu item dalam bentuk kartu, dengan ikon dan nama item yang berasal dari objek ItemHomepage. Ini juga menangani aksi ketika kartu ditekan.

### 3. Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
`setState()` adalah fungsi dalam Flutter yang digunakan untuk memperbarui state dari sebuah widget. Fungsi ini memungkinkan perubahan nilai variabel yang digunakan dalam widget dan secara otomatis memperbarui tampilan widget tersebut. Variabel yang dapat terpengaruh oleh fungsi `setState()` adalah variabel yang dideklarasikan dalam kelas widget yang menggunakan fungsi ini. Sebagai contoh, jika terdapat sebuah variabel `items` yang digunakan dalam widget `GridView`, maka perubahan nilai `items` melalui fungsi `setState()` akan secara otomatis memperbarui tampilan `GridView`.

### 4. Jelaskan perbedaan antara const dengan final.
Dalam Dart, `const` dan `final` digunakan untuk membuat variabel dengan nilai tetap (immutable), namun keduanya memiliki perbedaan dalam cara kerjanya dan kapan mereka digunakan.
- `const` adalah variabel yang nilainya bersifat konstan dan tidak akan berubah selama aplikasi berjalan (runtime). `const` harus diketahui nilainya saat compile-time. Ini biasanya digunakan untuk widget yang bersifat statis. 
- `final` adalah variabel yang nilainya tetap setelah diinisialisasi. Variabel bertipe `final` tidak perlu diketahui atau diinisialisasi pada waktu kompilasi, sehingga nilainya dapat diinisialisasi saat runtime. Namun, setelah diinisialisasi, nilai tersebut tidak dapat diubah lagi.

### 5. Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.
#### :one: Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.
Saya membuat folder baru di komputer saya untuk menyimpan proyek flutter saya.
```bash
flutter create warunk_chill
```
lalu cek apakah flutter sudah sepenuhnya terbuat dengan cara mengecek atau menjalankan aplikasi flutternya dengan 
```bash
flutter run
```
ada opsi lain yang paling mudah agar langsung run di chrome dengan cara 
```bash
flutter run -d chrome
```

#### :two: Membuat tiga tombol sederhana dengan ikon dan teks untuk:
- Melihat daftar produk (Lihat Daftar Produk)
- Menambah produk (Tambah Produk)
- Logout (Logout)

sebelum itu, saya perlu membuat list of `ItemHomepage` yang berisi tombol-tombol yang ingin kamu tambahkan pada class MyHomePage.
```dart
class MyHomePage extends StatelessWidget {
  ...
  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.list, Colors.blue),
    ItemHomepage("Tambah Produk", Icons.add, Colors.red),
    ItemHomepage("Logout", Icons.logout, Colors.green),
  ];
  ...
}
```

lalu Saya membuat tiga tombol dasar (dengan class bernama `ItemCard`) yang dilengkapi dengan ikon dan teks di dalam file `menu.dart`. 
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
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}")));
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

#### :three: Mengimplementasikan warna-warna yang berbeda untuk setiap tombol (Lihat Daftar Produk, Tambah Produk, dan Logout).
Saya menerapkan warna yang berbeda untuk setiap tombol di dalam kelas ItemHomePage, yang memiliki atribut color.
```dart
class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color;

  ItemHomepage(this.name, this.icon, this.color);
}
```

pastikan widget buildnya juga mereturn color
```dart
@override
Widget build(BuildContext context) {
return Material(
    // Menentukan warna latar belakang dari tema aplikasi.
    color: item.color,                                          // disini
    // Membuat sudut kartu melengkung.
    borderRadius: BorderRadius.circular(12),
```

jangan lupa set warna yang diinginkan. di code di bawah ini saya memilih warna biru, merah, dan hijau karena cukup kontras dengan background yang berwarna putih
```dart
  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.list, Colors.blue),
    ItemHomepage("Tambah Produk", Icons.add, Colors.red),
    ItemHomepage("Logout", Icons.logout, Colors.green),
  ];
```

#### :four: Memunculkan Snackbar dengan tulisan:
"Kamu telah menekan tombol Lihat Daftar Produk" ketika tombol Lihat Daftar Produk ditekan.
"Kamu telah menekan tombol Tambah Produk" ketika tombol Tambah Produk ditekan.
"Kamu telah menekan tombol Logout" ketika tombol Logout ditekan.

saya memunculkan `Snackbar` dengan tulisan ketika tombol-tombol ditekan. Saya menggunakan widget `ScaffoldMessenger` untuk menampilkan `Snackbar`.
```dart
// Aksi ketika kartu ditekan.
onTap: () {
    // Menampilkan pesan SnackBar saat kartu ditekan.
    ScaffoldMessenger.of(context)
    ..hideCurrentSnackBar()
    ..showSnackBar(SnackBar(
        content: Text("Kamu telah menekan tombol ${item.name}")));
},
```

#### :five: tambahan
saya juga menampilkan tombol-tombol di layar dalam bentuk grid dengan menggunakan widget `GridView`.
```dart
class MyHomePage extends StatelessWidget {
  MyHomePage({super.key});

  final String npm = '2306241682'; // NPM
  final String name = 'Akhyar Rasyid Asy syifa'; // Nama
  final String className = 'PBP D'; // Kelas

  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Daftar Produk", Icons.list, Colors.blue),
    ItemHomepage("Tambah Produk", Icons.add, Colors.red),
    ItemHomepage("Logout", Icons.logout, Colors.green),
  ];

  @override
  Widget build(BuildContext context) {
    // Scaffold menyediakan struktur dasar halaman dengan AppBar dan body.
    return Scaffold(
      // AppBar adalah bagian atas halaman yang menampilkan judul.
      appBar: AppBar(
        // Judul aplikasi "Warunk Chill" dengan teks putih dan tebal.
        title: const Text(
          'Warunk Chill',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        // Warna latar belakang AppBar diambil dari skema warna tema aplikasi.
        backgroundColor: Theme.of(context).colorScheme.primary,
      ),
      // Body halaman dengan padding di sekelilingnya.
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        // Menyusun widget secara vertikal dalam sebuah kolom.
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            // Row untuk menampilkan 3 InfoCard secara horizontal.
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),

            // Memberikan jarak vertikal 16 unit.
            const SizedBox(height: 16.0),

            // Menempatkan widget berikutnya di tengah halaman.
            Center(
              child: Column(
                // Menyusun teks dan grid item secara vertikal.

                children: [
                  // Menampilkan teks sambutan dengan gaya tebal dan ukuran 18.
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to Warunk Chill',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),

                  // Grid untuk menampilkan ItemCard dalam bentuk grid 3 kolom.
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    // Agar grid menyesuaikan tinggi kontennya.
                    shrinkWrap: true,

                    // Menampilkan ItemCard untuk setiap item dalam list items.
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```




