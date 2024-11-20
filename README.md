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

<details>
<summary>📒 Tugas 8</summary>

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
<details>

## Tugas 9 - PBP 2024/2025
## 1. Ada beberapa alasan kita membuat model terlebih dahulu di flutter untuk melakukan pengiriman atau pengambilan data json dari backend / django. Berikut penjelasannya :

1.  **Struktur Data yang Jelas:**
    -   Model memungkinkan kita mendefinisikan dengan jelas atribut-atribut data yang dikirim atau diterima (misalnya, tipe data dan properti JSON).
    -   Hal ini mencegah kesalahan parsing JSON karena perubahan struktur data dari API.
    
2.  **Kemudahan Parsing dan Serialization:**
    -   Dengan model, kita dapat menggunakan metode seperti `fromJson()` dan `toJson()` untuk konversi data secara otomatis antara objek Dart dan format JSON.
    -   lebih efisien karena hanya perlu mengakses properti seperti `data.name` daripada menangani JSON secara manual setiap saat tanpa harus mengindexing `data['name']`.
    
3.  **Mudah Dikelola dan Dimodifikasi:**
    -   Ketika API Django mengalami perubahan (misalnya, menambahkan field baru), cukup mengupdate model di Flutter tanpa harus mengubah logika di seluruh aplikasi.
    
4.  **Pendeteksian Error Lebih Cepat:**
    -   Dengan model, IDE dapat memberikan peringatan jika ada kesalahan akses atribut atau metode yang salah karena tipe data yang tidak sesuai.

## 2. Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini
Library http dalam Flutter berfungsi utama untuk memungkinkan aplikasi berkomunikasi dengan server menggunakan protokol HTTP. Dalam tugas ini, library tersebut digunakan untuk mengambil data dari API atau mengirim data ke server. Dengan memanfaatkan library ini, aplikasi dapat melakukan berbagai jenis permintaan HTTP seperti GET, POST, PUT, DELETE, dan lainnya, untuk berinteraksi dengan server dan memperoleh data yang diperlukan.

## 3. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
CookieRequest berfungsi untuk mengelola cookie dalam aplikasi Flutter, yang biasanya digunakan untuk menyimpan informasi seperti sesi pengguna atau preferensi pengguna yang perlu dipertahankan di antara permintaan HTTP. Ketika aplikasi melakukan permintaan ke server, cookie bisa disertakan dalam header HTTP, dan CookieRequest memastikan bahwa cookie yang relevan ikut dikirimkan dan diterima dengan benar. Dengan cara ini, informasi terkait sesi pengguna dapat dipertahankan tanpa perlu mengautentikasi ulang setiap kali permintaan dilakukan.

Instance CookieRequest perlu dibagikan ke seluruh komponen di aplikasi karena cookie sering kali digunakan untuk mengelola status pengguna di seluruh aplikasi, seperti memastikan pengguna tetap masuk setelah aplikasi dimuat ulang. Jika CookieRequest hanya digunakan di satu bagian aplikasi, informasi sesi atau cookie yang dibutuhkan bisa hilang ketika aplikasi berpindah antar tampilan atau komponen. Dengan membagikan instance ini, seluruh aplikasi dapat mengakses dan mengelola cookie secara konsisten, menjaga pengalaman pengguna yang lebih lancar dan menghindari masalah terkait otentikasi atau status sesi yang terputus.

## 4. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
Proses pengiriman data dari input hingga dapat ditampilkan di Flutter melibatkan beberapa langkah utama yang mencakup interaksi antara frontend (Flutter) dan backend (Django). Berikut adalah penjelasan mekanisme lengkapnya:

**1. Input Data pada Flutter**
- **Proses:**
  1.  Pengguna mengisi formulir (seperti form login, register, atau data lainnya) di aplikasi Flutter.
  2.  Data yang diisi dikumpulkan dari widget input seperti `TextField` atau `Form`.
  3.  Data ini disiapkan dalam bentuk JSON atau dictionary Dart.
    
 **2. Mengirim Data ke Django**
- **Proses:**
  1.  Data yang telah disiapkan dikirim ke server Django melalui HTTP request (`POST` atau `GET`) menggunakan `http` atau `CookieRequest`.
  2.  Endpoint Django yang dituju menangani data tersebut.
  3.  Dalam pengiriman, jika menggunakan `CookieRequest`, cookie sesi ditambahkan secara otomatis untuk autentikasi.

**3. Proses Data di Django**
- **Proses:**
  1.  Django menerima data melalui view yang sesuai dengan endpoint (misalnya, `/create-flutter/`).
  2.  Data JSON yang diterima di-decode dan diverifikasi.
  3.  Jika valid, Django menyimpan data ke dalam database menggunakan model Django.

**4. Mengambil Data dari Django**
- **Proses:**
  1.  Flutter mengirimkan permintaan HTTP `GET` ke endpoint Django untuk mengambil data yang disimpan di database.
  2.  Django memproses permintaan dan mengembalikan data dalam bentuk JSON.

**5. Mengolah Data di Flutter**
- **Proses:**
  1.  Data JSON yang diterima di-decode menjadi objek Dart menggunakan model yang sesuai.
  2.  Objek-objek ini disimpan dalam list atau state aplikasi untuk ditampilkan.

**6. Menampilkan Data di Flutter**
- **Proses:**
  1.  Data yang telah diolah ditampilkan di layar menggunakan widget seperti `ListView`, `FutureBuilder`, atau lainnya.
  2.  UI disesuaikan agar data terlihat menarik dan mudah dibaca.

## 5. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
Proses autentikasi mencakup alur data mulai dari input di Flutter, pengolahan di Django, hingga respons kembali ke Flutter. Berikut adalah penjelasan rinci setiap tahapannya:

 **1. Register (Pendaftaran Akun)**

**Di Flutter (Input Data)**
-   **Input:** Pengguna memasukkan data pendaftaran seperti `username`, `password`, dan `confirm password` melalui form register.
-   **Pengiriman Data:** Data dikemas dalam JSON dan dikirim ke endpoint Django `/auth/register/` menggunakan HTTP request (biasanya `POST`).

**Di Django (Pemrosesan Data)**
-   **Penerimaan Data:** Django menerima data JSON dari Flutter melalui view register.
-   **Validasi:**
    1.  Django memeriksa apakah password dan confirm password cocok.
    2.  Memeriksa apakah username sudah terdaftar.
-   **Pembuatan Akun:** Jika valid, Django membuat user baru menggunakan model `User` dan menyimpannya ke database.
-   **Respons:** Django mengirimkan respons JSON ke Flutter dengan status sukses atau gagal.

**Di Flutter (Hasil Register)**
-   **Tampilan:**
    1.  Jika berhasil, pengguna diarahkan ke halaman login.
    2.  Jika gagal, pesan error ditampilkan.

**2. Login**

**Di Flutter (Input Data)**
-   **Input:** Pengguna memasukkan `username` dan `password` melalui form login.
-   **Pengiriman Data:** Data dikirim ke endpoint Django `/auth/login/` menggunakan HTTP request (`POST`).

**Di Django (Pemrosesan Data)**
-   **Penerimaan Data:** Django menerima data JSON dan memprosesnya melalui view login.
-   **Validasi:**
    1.  Django memeriksa kredensial menggunakan fungsi `authenticate`.
    2.  Jika valid, Django memvalidasi apakah akun masih aktif.
-   **Penyimpanan Sesi:** Jika valid, Django membuat cookie sesi untuk pengguna menggunakan fungsi `login`.
-   **Respons:** Django mengirimkan respons JSON dengan status sukses, pesan, dan cookie sesi ke Flutter.

**Di Flutter (Hasil Login)**
-   **Tampilan:**
    1.  Jika login berhasil, Flutter menyimpan status login (`loggedIn`) dan cookie sesi menggunakan `CookieRequest`.
    2.  Pengguna diarahkan ke menu utama.
    3.  Jika login gagal, pesan error ditampilkan.

**3. Logout**

**Di Flutter (Permintaan Logout)**
-   **Aksi:** Pengguna menekan tombol logout.
-   **Pengiriman Data:** Flutter mengirim permintaan HTTP (`POST`) ke endpoint Django `/auth/logout/` untuk menghapus sesi.

**Di Django (Pemrosesan Logout)**
-   **Penerimaan Data:** Django menerima permintaan logout melalui view logout.
-   **Penghapusan Sesi:** Django menghapus cookie sesi pengguna menggunakan fungsi `logout`.
-   **Respons:** Django mengirimkan respons JSON dengan status sukses atau gagal.

**Di Flutter (Hasil Logout)**
-   **Tampilan:**
    1.  Jika logout berhasil, Flutter menghapus status login dan mengarahkan pengguna kembali ke halaman login.
    2.  Jika gagal, pesan error ditampilkan.

## 6. Jelaskan bagaimana cara kamu mengimplementasikan _checklist_ di atas secara _step-by-step_! (bukan hanya sekadar mengikuti tutorial).
### 1.  Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.
1. pertama-tama saya install django-cors-headers, lalu tambahkan ke dalam daftar `INSTALLED_APPS` di file `settings.py`. Selanjutnya, masukkan `corsheaders.middleware.CorsMiddleware` ke bagian MIDDLEWARE di `settings.py` untuk memungkinkan pengaturan CORS (Cross-Origin Resource Sharing). Lalu, buat function register di `views.py` pada app `authentication` yang ada di django app seperti berikut.

```dart
@csrf_exempt
def register(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        username = data['username']
        password1 = data['password1']
        password2 = data['password2']

        # Check if the passwords match
        if password1 != password2:
            return JsonResponse({
                "status": False,
                "message": "Passwords do not match."
            }, status=400)
        
        # Check if the username is already taken
        if User.objects.filter(username=username).exists():
            return JsonResponse({
                "status": False,
                "message": "Username already exists."
            }, status=400)
        
        # Create the new user
        user = User.objects.create_user(username=username, password=password1)
        user.save()
        
        return JsonResponse({
            "username": user.username,
            "status": 'success',
            "message": "User created successfully!"
        }, status=200)
    
    else:
        return JsonResponse({
            "status": False,
            "message": "Invalid request method."
        }, status=400)
```

2. membuat berkas baru pada folder `screens` dengan nama `register.dart` dengan tipe widget stateful agar logic pembuatan data pada model berjalan baik
3. membuat form input untuk username, password, dan confirm password
```dart
 final response = await request.postJson(
  "http://localhost:8000/auth/register/",
  jsonEncode({
    "username": username,
    "password1": password1,
    "password2": password2,
  }));
```
4. jika setelah di klik register user berhasil register, maka navigasi ke login page
```dart
 ...
  Navigator.pushReplacement(
    context, 
    MaterialPageRoute(
        builder: (context) => const LoginPage()),
  );
  ...
```

### 2. Membuat halaman login pada proyek tugas Flutter.
langkahnya agak mirip dengan implementasi register. yakni 
1. membuat function `login` lalu tambahkan di `views.py` authentication pada django app seperti berikut :
```dart
...
@csrf_exempt
def login(request):
    username = request.POST['username']
    password = request.POST['password']
    user = authenticate(username=username, password=password)
    if user is not None:
        if user.is_active:
            auth_login(request, user)
            # Status login sukses.
            return JsonResponse({
                "username": user.username,
                "status": True,
                "message": "Login sukses!"
                # Tambahkan data lainnya jika ingin mengirim data ke Flutter.
            }, status=200)
        else:
            return JsonResponse({
                "status": False,
                "message": "Login gagal, akun dinonaktifkan."
            }, status=401)

    else:
        return JsonResponse({
            "status": False,
            "message": "Login gagal, periksa kembali email atau kata sandi."
        }, status=401)
...
```

2. membuat berkas baru pada folder `screens` dengan nama `login.dart` dengan tipe widget stateful agar logic untuk login ketika tombol login di klik berjalan baik
3. meminta form input dimana user harus memasukkan username, password, dan confirm password
4. membuat logic button untuk login ketika di klik seperti berikut 
```dart
...
ElevatedButton(
onPressed: () async {
  String username = _usernameController.text;
  String password = _passwordController.text;

  // Cek kredensial
  // Untuk menyambungkan Android emulator dengan Django pada localhost,
  // gunakan URL http://10.0.2.2/
  final response = await request
      .login("http://127.0.0.1:8000/auth/login/", {
    'username': username,
    'password': password,
  });

  // pergi ke MyHomePage kalau login berhasil, yeay!
  if (request.loggedIn) {
    String message = response['message'];
    String uname = response['username'];
    if (context.mounted) {
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(
            builder: (context) => MyHomePage()),
      );
...
```

### 3. Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.
sudah dijelaskan dengan detail pada soal nomor 5

### 4. Membuat model kustom sesuai dengan proyek aplikasi Django.
Pada Django, buat terlebih dahulu beberapa contoh product dengan menggunakan fitur add new product, lalu pergi ke page JSON dengan menambahkan `/json/` di url web localhostnya. jadi nanti bentuknya `localhost:8000/json`. Setelah itu, copy data JSON dalam bentuk pretty print dan copas ke website QuickType lalu ubah jadi format dart. Buat sebuah direktori baru bernama `models` dan file baru di dalamnya yang bernama `product_entry.dart` dan paste data JSON tadi ke dalam file tersebut. 

### 5. Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.
Buat file baru di folder `screens` dengan nama `list_productentry.dart`. Di dalam file tersebut, ambil data dari JSON Django dan masukkan ke dalam sebuah list menggunakan loop. Setelah itu, gunakan widget `ListView` untuk menampilkan data dalam format kolom. Pastiin data yang ditampilkan itu mencakup nama produk, harga produk, dan deskripsinya sehingga pengguna dapat melihat informasi produk dengan jelas. kurang lebih implemntasinya sebagai berikut :
```dart
  Future<List<ProductEntry>> fetchProduct(CookieRequest request) async {
    final response = await request.get('http://127.0.0.1:8000/json/');

    // Melakukan decode response menjadi bentuk json
    var data = response;

    List<ProductEntry> listProduct = [];
    for (var d in data) {
      if (d != null) {
        listProduct.add(ProductEntry.fromJson(d));
      }
    }
    return listProduct;
  }
```

### 6. Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.
untuk membuat halaman detail untuk setiap item, saya membuat sebuah file baru di dalam folder `screens` bernama `details_product`. implementasinya sebagai berikut : 
```dart
import 'package:flutter/material.dart';
import 'package:warunk_chill/models/product_entry.dart';

class ProductDetailPage extends StatelessWidget {
  final ProductEntry product;

  const ProductDetailPage({super.key, required this.product});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(
          "View Product: ${product.fields.name}",
          style: const TextStyle(color: Colors.white),
        ),
        backgroundColor: const Color.fromARGB(255, 29, 29, 29),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              "Name: ${product.fields.name}",
              style: const TextStyle(
                  fontSize: 20,
                  fontWeight: FontWeight.bold,
                  color: Colors.white),
            ),
            const SizedBox(height: 12),
            Text(
              "Price: \$${product.fields.description}",
              style: const TextStyle(color: Colors.white),
            ),
            const SizedBox(height: 8),
            Text(
              "Desc:\n${product.fields.price}",
              style: const TextStyle(color: Colors.white),
              softWrap: true,
            ),
            const SizedBox(height: 8),
            Text(
              "Stock: ${product.fields.quantity}",
              style: const TextStyle(color: Colors.white),
            ),
            const SizedBox(height: 8),
            ElevatedButton(
              onPressed: () => Navigator.pop(context),
              style: ElevatedButton.styleFrom(
                backgroundColor:
                    const Color.fromARGB(255, 29, 29, 29), // Background color
                foregroundColor: Colors.white, // Font color
                padding: const EdgeInsets.symmetric(
                    horizontal: 16.0, vertical: 12.0), // Optional padding
                shape: RoundedRectangleBorder(
                  borderRadius:
                      BorderRadius.circular(8.0), // Optional rounded corners
                ),
              ),
              child: const Text("Back to Product List"),
            )
          ],
        ),
      ),
    );
  }
}
```

Setelah itu, saya _connect_-in dengan `list_productentry.dart` agar bisa ditampilkan dengan potongan kode berikut:
```dart
              return ListView.builder(
                itemCount: snapshot.data!.length,
                itemBuilder: (_, index) => Card(
                    color: const Color.fromARGB(
                        255, 29, 29, 29), // Warna latar belakang Card
                    shape: RoundedRectangleBorder(
                      borderRadius:
                          BorderRadius.circular(12.0), // Sudut melengkung Card
                    ),
                    elevation: 4, // Bayangan Card
                    margin: const EdgeInsets.symmetric(
                        horizontal: 16, vertical: 12), // Jarak antar Card
                    child: ListTile(
                      title: Text(
                        "${snapshot.data![index].fields.name}",
                        style: const TextStyle(
                          color: Colors.white,
                          fontSize: 18.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      subtitle: Column(
                        crossAxisAlignment: CrossAxisAlignment.start,
                        children: [
                          const SizedBox(height: 8),
                          Text(
                            "Price: \$${snapshot.data![index].fields.price}",
                            style: const TextStyle(color: Colors.white),
                          ),
                          const SizedBox(height: 8),
                          Text(
                            "Description:\n${snapshot.data![index].fields.description}",
                            style: const TextStyle(color: Colors.white),
                            softWrap:
                                true, // Mendukung teks yang melanjutkan ke baris berikutnya
                          ),
                        ],
                      ),
                      onTap: () {
                        Navigator.push(
                          context,
                          MaterialPageRoute(
                            builder: (context) => ProductDetailPage(
                              product: snapshot.data![index],
                            ),
                          ),
                        );
                      },
                    )),
              );
```

### 7. Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.
Filtering item berdasarkan pengguna yang login ini sudah dihandle pada Back-end Django. karena kita mengintegrasikan function dengan django, jadi seharusnya filterisasi sudah berjalan baik, yaitu melalui potongan kode berikut:
```dart
def show_json(request) :
    data = Product.objects.filter(user=request.user) # Disini
    return HttpResponse(serializers.serialize("json", data), content_type="application/json")
```

YEAYYY TUGAS SELESAII!!!!