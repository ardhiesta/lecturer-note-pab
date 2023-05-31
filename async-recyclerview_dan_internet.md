# Kuliah Asinkronus 31 Mei 2023

## Update Tugas Project

Seperti yang sudah saya post di google classroom, ada penyesuaian mengenai ketentuan tugas project membuat aplikasi Android :

1. Bahasa pemrograman untuk membuat app dibebaskan, tidak harus menggunakan Kotlin / Java
Alternatif yang dapat digunakan : Flutter, ReactNative atau framework berbasis JavaScript lainnya, AppInventor, atau membuat web app juga diperbolehkan
> **Catatan** : khusus untuk web app harus dapat menunjukkan adanya fitur smartphone yang digunakan pada aplikasi

2. Tidak harus mengikuti pembagian topik aplikasi yang sudah dibagi apabila kesulitan
> **Catatan** : kreativitas dijadikan sebagai pertimbangan dalam penilaian, semakin unik (tidak sama seperti aplikasi lain yang sudah ada) semakin bagus

Kelonggaran diberikan karena saya mengalami sendiri development native app Android menggunakan IntelliJ Idea / Android Studio semakin menguras resource (RAM dan CPU). Apabila tidak mengalami kendala spek hardware, bisa tetap menggunakan topik yang sudah dibagi dan pakai Kotlin.

> **PENTING** : Tugas project akan dipresentasikan untuk dinilai tanggal **19 - 24 Juni 2023**.

## Materi 1: RecyclerView

Slide dapat diunduh [di sini](https://app.box.com/s/l81abguhaao6256x79b2we4kplqbi4k7).

### Introduction

RecyclerView adalah widget yang digunakan untuk menampilkan data yang jumlahnya banyak pada aplikasi Android. Widget RecyclerView berupa tampilan list item yang memenuhi layar, user dapat melakukan scroll ke atas dan ke bawah untuk melihat data.

<figure>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20220801125801/CardViewusingRecyclerViewinAndroid-305x660.jpg" alt="Trulli" style="width:60%">
<figcaption align = "left">Gambar 1: Contoh implementasi RecyclerView</figcaption>
</figure>

> **Pertanyaan 1** : Tulis 3 contoh implementasi RecyclerView (sebutkan nama aplikasi yang menggunakan RecyclerView dan penggunaannya untuk menampilkan data apa)!

### Mengapa disebut RecyclerView?

RecyclerView melakukan *recycle* elemen individual penyusunnya. Ketika sebuah *item* tidak terlihat di layar karena user melakukan *scroll*, RecyclerView tidak melakukan *destroy* terhadap *view* tersebut namun menggunakannya kembali untuk me-*render* *item* baru yang akan dimunculkan. Desain ini bertujuan untuk meningkatkan *performance* dan mengurangi konsumsi daya.

<figure>
<img src="https://github.com/ardhiesta/lecturer-note-pab/blob/main/images/rv.jpg?raw=true" alt="Trulli" style="width:100%">
<figcaption align = "left">Gambar 2: Ilustrasi RecyclerView</figcaption>
</figure>

### RecyclerView (list-based widget) vs Table

Alternatif lain untuk menampilkan data di aplikasi mobile adalah menggunakan tabel.

<figure>
<img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*4ZlAY6HN11n9RyU-lz7B_Q@2x.png" alt="Trulli" style="width:100%">
<figcaption align = "left">Gambar 3: Contoh penggunaan tabel di aplikasi mobile</figcaption>
</figure>

> **Pertanyaan 2** : Sebutkan kekurangan dan kelebihan menampilkan data menggunakan tampilan tabel di aplikasi mobile!

### [Komponen RecyclerView](https://google-developer-training.github.io/android-developer-fundamentals-course-concepts-v2/unit-2-user-experience/lesson-4-user-interaction/4-5-c-recyclerview/4-5-c-recyclerview.html)

<figure>
<img src="https://google-developer-training.github.io/android-developer-fundamentals-course-concepts-v2/images/4-5-c-recyclerview/dg_recycler_architecture.png" alt="Trulli" style="width:100%">
<figcaption align = "left">Gambar 4: Komponen RecyclerView</figcaption>
</figure>

**Data** : Data bisa berasal dari local, misal dari database di smartphone atau bisa diambil dari server melalui koneksi internet.

**Adapter** : Untuk menghubungkan data ke RecyclerView. Adapter mempersiapkan data untuk ditampilkan melalui ViewHolder. Ketika terjadi perubahan data, adapter akan memperbarui isi dari list item view pada RecyclerView.

**ViewHolder** : Berisi informasi untuk menampilkan sebuah view item menggunakan item layout.

**Layout manager** : Layout manager menangani layout (user interface) komponen view yang akan ditampilkan dalam RecyclerView. Setiap ViewGroup (termasuk RecyclerView) memiliki sebuah layout manager. RecyclerView membutuhkan sebuah layout manager eksplisit untuk mengelola susunan list item yang ada di dalamnya. Item-item bisa disusun secara vertikal, horizontal, atau menggunakan grid. 

**Layout untuk satu item data** : Setiap item dalam RecyclerView memiliki tampilan yang sama, hanya berbeda pada isi datanya saja. Perlu dibuat sebuah layout (file xml) yang akan digunakan menampilkan untuk setiap item data. 

## Materi 2: Membuat Aplikasi dengan Koneksi Internet

Slide dapat diunduh [di sini](https://app.box.com/s/fsgds8imd9ouflfw9ksaivzspwnt798h).

### Introduction

Terdapat kondisi tertentu yang mengharuskan sebuah aplikasi Android terhubung ke internet, misalnya ketika mengakses data yang tersimpan di server. Programmer dapat menambahkan fitur koneksi internet pada aplikasi yang dibuat agar dapat mengakses data lewat internet. Untuk menambahkan fitur tersebut terlebih dulu harus diberikan permission (hak akses) ke aplikasi.

### Permission

Merupakan mekanisme untuk menjamin privasi user. Permission dapat diberikan pada saat instalasi ataupun saat runtime. 

Aplikasi Android secara default tidak diberikan hak akses untuk terhubung ke internet. Untuk menambahkannya programmer harus menambahkan baris 
```
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
di file AndroidManifest.xml.

> **Pertanyaan 3** : Jelaskan mengapa secara default sebuah aplikasi Android tidak diberikan permission untuk terhubung ke internet?

### App permission best practice

* Jangan berikan semua jenis permission, berikan permission-permission spesifik yang hanya dibutuhkan oleh sebuah aplikasi.
* Perhatikan permission yang dibutuhkan oleh external library.
* Berikan informasi mengenai permission aplikasi secara transparan dan jelas ke user.

### Menggunakan sumber daya pada jaringan

Sumber daya yang tersedia biasanya berupa data yang diakses melalui internet. Data tersedia dalam bentuk API yang dapat diakses melalui URL. Untuk meudahkan dalam mengakses API terdapat sejumlah library yang dapat digunakan ketika melakukan development aplikasi Android misalnya menggunakan [retrofit](https://square.github.io/retrofit/).

Data yang tersedia di API umumnya diformat dalam bentuk [JSON](https://www.w3schools.com/js/js_json_intro.asp), programmer dapat melakukan parsing data JSON untuk ditampilkan dalam aplikasi.

Contoh code teknis untuk mengakses API dapat dilihat di [slide](https://app.box.com/s/fsgds8imd9ouflfw9ksaivzspwnt798h).