WarunkChill🏪🥘🛒 <br>
"The Perfect Place to Chill and Fill." <br>

- Nama   : Akhyar Rasyid Asy syifa <br>
- NPM    : 2306241682  <br>
- Kelas  : PBP - D <br>

<details>
<summary>📒 Tugas 7</summary>

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

</details>

## Tugas 8 - PBP 2024/2025
### 1. Apa kegunaan `const` di Flutter? Jelaskan apa keuntungan ketika menggunakan `const` pada kode Flutter. Kapan sebaiknya kita menggunakan `const`, dan kapan sebaiknya tidak digunakan?
`const` digunakan untuk mendefinisikan nilai tetap yang tidak akan berubah sepanjang runtime aplikasi, seperti warna, padding, margin, teks, atau ukuran tertentu. Keuntungan menggunakan `const` adalah performa yang lebih baik karena Flutter bisa mengoptimalkan widget karena Flutter tahu bahwa widget tersebut tidak perlu di-rebuild, sehingga tidak perlu diproses ulang ketika ada perubahan dalam aplikasi. Selain itu, objek yang di-compile dengan `const` hanya disimpan satu kali dalam memori (shared memory), jadi jika ada objek `const` yang sama di beberapa tempat, hanya satu objek yang disimpan, sehingga memori yang digunakan lebih efisien. 

`const` sebaiknya digunakan untuk menyimpan nilai widget atau objek tersebut tidak akan berubah sepanjang runtime aplikasi dan tidak bergantung pada data dinamis, seperti teks tetap, padding tetap, margin tetap, warna tetap, atau ikon tetap. `const` sebaiknya tidak digunakan jika kita menginginkan widget atau objek yang dinamis, artinya nilai objek bergantung pada perubahan state atau input pengguna. Contohnya adalah widget yang nilainya dihasilkan dari variabel yang bisa berubah, seperti hasil dari `setState`.

### 2. Jelaskan dan bandingkan penggunaan _Column_ dan _Row_ pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
**Column** dan **Row** adalah dua widget tata letak (layout) utama di Flutter yang digunakan untuk mengatur widget anak (**children**) dalam sebuah **container**. Meskipun keduanya berfungsi untuk mengatur tata letak, perbedaannya terletak pada arah penempatan elemen.

- _Column_ adalah widget yang mengatur tata letak widget di dalamnya secara vertikal (dari atas ke bawah). _Column_ berguna ketika kita ingin menampilkan beberapa widget dalam satu kolom vertikal. Contoh implementasinya sebagai berikut:

```dart
Column(
    mainAxisAlignment: MainAxisAlignment.center,    // Menyusun widget di sepanjang sumbu utama (vertikal dalam Column_)
    crossAxisAlignment: CrossAxisAlignment.start,   // Menyusun widget di sepanjang sumbu silang (horizontal dalam Column)
    children: <Widget>[
        Text('Selamat Datang Akhyar'),
        SizedBox(height: 8),  // Memberikan jarak antar widget
        Icon(Icons.thumb_up, color: Colors.blue),
        SizedBox(height: 8),
        ElevatedButton(
            onPressed: () {},
            child: Text('Klik Saya'),
        ),
    ],
);
```

Dalam contoh di atas, widget Text dan ElevatedButton ditampilkan secara vertikal dengan jarak antar item menggunakan SizedBox.

- _Row_ adalah widget yang mengatur tata letak widget di dalamnya secara horizontal (dari kiri ke kanan). Ini berguna ketika Anda ingin menyusun widget secara horizontal dalam satu baris.

```dart
Row(
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,   // Menyusun widget di sepanjang sumbu utama (horizontal dalam Row)
    crossAxisAlignment: CrossAxisAlignment.center,      // Menyusun widget di sepanjang sumbu silang (vertikal dalam Row)
    children: <Widget>[
        Icon(Icons.home, color: Colors.green),
        Text('Beranda'),
        ElevatedButton(
            onPressed: () {},
            child: Text('Aksi'),
        ),
    ],
);
```

Dalam contoh di atas, Icon, Text, dan ElevatedButton ditampilkan secara horizontal dengan jarak yang merata di antara elemen menggunakan MainAxisAlignment.spaceAround.

### 3. Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!

Dalam tugas ini saya menggunakan dua input untuk halaman form saya. Berikut penjelasannya :

1. **TextFormField**
Versi _advance_ dari `TextField` yang terintegrasi dengan `Form`. Menyediakan fitur validasi input langsung dalam form, membuatnya ideal untuk pengisian data yang membutuhkan pemeriksaan kesalahan.

2. **ElevatedButton**
Tombol berbasis teks yang memberikan feedback elevasi saat ditekan. Sering digunakan untuk memicu tindakan, seperti menyimpan data atau mengirim form.

#### Input lainnya di Flutter
Selain kedua input tersebut, flutter masih memiliki beberapa input lainnya. Berikut penjelasannya :

1. **TextField**
Elemen input teks dasar yang digunakan untuk memasukkan teks dari pengguna. Cocok untuk masukan satu baris seperti nama atau email. Dapat dikustomisasi dengan properti seperti `controller`, `decoration`, dan `keyboardType`.

2. **DropdownButtonFormField**
Elemen input yang memungkinkan pengguna memilih opsi dari daftar dropdown. Sangat bermanfaat untuk input yang memiliki pilihan terbatas seperti kategori produk atau status.

3. **Checkbox**
Elemen input yang memungkinkan pengguna memilih opsi benar atau salah (checked atau unchecked). Umumnya digunakan dalam form untuk konfirmasi, seperti persetujuan syarat dan ketentuan.

4. **Radio**
Elemen input yang digunakan untuk memilih satu opsi dari beberapa pilihan yang tersedia. Sering digunakan bersama `ListTile` untuk memberikan label pada pilihan.

5. **Slider**
Elemen input yang memungkinkan pengguna memilih nilai dalam rentang tertentu. Biasanya digunakan untuk memilih angka atau level, seperti volume suara atau harga.

6. **DatePicker**
Digunakan untuk memilih tanggal. Elemen ini dapat dipanggil dengan fungsi `showDatePicker()` untuk membuka dialog tanggal yang memungkinkan pengguna memilih tanggal tertentu.

7. **TimePicker**
Digunakan untuk memilih waktu. Sama seperti `DatePicker`, elemen ini dapat dipanggil dengan fungsi `showTimePicker()` dan membuka dialog untuk memilih waktu.

8. **Switch**
Elemen input yang berfungsi sebagai tombol on/off. Biasanya digunakan untuk pengaturan yang memiliki dua status, seperti mengaktifkan atau menonaktifkan fitur.

### 4. Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Pada aplikasi saya, ada beberapa cara yang saya terapkan untuk menjaga konsistensi tema:

1. Definisi Warna Utama dan Sekunder
Saya menetapkan primary dan secondary menggunakan `ColorScheme.fromSwatch().copyWith`, memastikan warna utama (primary) dan sekunder (secondary) digunakan secara konsisten di komponen-komponen utama seperti `AppBar`, tombol, dan elemen UI lainnya.

2. Penggunaan `useMaterial3: true` 
Dengan menambahkan `useMaterial3: true`, aplikasi mengadopsi elemen desain Material You, yang menawarkan tampilan modern dan responsif. Ini juga menyesuaikan elemen UI berdasarkan tema warna yang sudah diatur, seperti efek elevasi dan kurva pada komponen.

3. Pemanfaatan Theme.of(context) dalam Widget 
Pada widget tertentu, saya menggunakan `Theme.of(context)` untuk mengakses warna sesuai tema utama yang sudah didefinisikan, seperti pada bagian `AppBar`, `Scaffold`, `Drawer`, dan komponen lainnya. Misalnya, untuk Drawer header, saya mengatur warna latar belakang menggunakan `Theme.of(context).colorScheme.primary`.

### 5. Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?

Flutter menyediakan class Navigator yang berisi beberapa method, diantaranya `Navigator.push`, `Navigator.pop`,  `Navigator.pushReplacement`, dan masih banyak lagi.

- Navigator.push() menambahkan suatu route ke dalam stack route yang dikelola oleh Navigator. Method ini digunakan untuk menambahkan route di top of stack, dan digunakan ketika kita ingin berpindah halaman dan menambahkan halaman tersebut ke atas stack, sehingga saya dapat menekan tombol Back untuk kembali ke halaman sebelumnya yang berada dibawah top of stack.
penerapan saya sebagai berikut :
```dart
if (item.name == "Tambah Produk") {
  Navigator.push(
    context,
    MaterialPageRoute(
        builder: (context) => const ProductEntryFormPage()),
  );
}
```

- Navigator.pop() menghapus route saat ini (yang sedang ditampilkan ke pengguna) sehingga halaman yang ditampilkan adalah route yang berada di bawah top of stack yang dikelola Navigator (biasanya berupa halaman sebelumnya).
penerapan saya sebagai berikut :
```dart
actions: [
  TextButton(
    child: const Text('OK'),
    onPressed: () {
      Navigator.pop(context);
      _formKey.currentState!.reset();
    },
  ),
],
```

- Navigator.pushReplacement() menghapus route yang sedang ditampilkan ke pengguna dan langsung menggantinya dengan suatu route yang sudah didefinisikan, tanpa mengubah route yang berada di bawah stack. Dalam kata lain, method ini digunakan untuk mengganti halaman saat ini dengan halaman baru tanpa menambahkan ke stack, sehingga pengguna tidak bisa kembali ke halaman sebelumnya.
penerapan pada code saya sebagai berikut :
```dart
ListTile(
  leading: const Icon(Icons.add),
  title: const Text('Tambah Produk'),
  // Bagian redirection ke ProductEntryFormPage
  onTap: () {
    Navigator.pushReplacement(
        context,
        MaterialPageRoute(
          builder: (context) => const ProductEntryFormPage(),
        ));
  },
),
```