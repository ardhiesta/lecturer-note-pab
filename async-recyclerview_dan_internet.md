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
<figcaption align = "left"><b>Contoh implementasi RecyclerView</b></figcaption>
</figure>

> **Pertanyaan 1** : Tulis 3 contoh implementasi RecyclerView (sebutkan nama aplikasi yang menggunakan RecyclerView dan penggunaannya untuk menampilkan data apa)!

### Mengapa disebut RecyclerView?

RecyclerView melakukan *recycle* elemen individual penyusunnya. Ketika sebuah *item* tidak terlihat di layar karena user melakukan *scroll*, RecyclerView tidak melakukan *destroy* terhadap *view* tersebut namun menggunakannya kembali untuk me-*render* *item* baru yang akan dimunculkan. Desain ini bertujuan untuk meningkatkan *performance* dan mengurangi konsumsi daya.


### RecyclerView (list-based widget) vs Table

Alternatif lain untuk menampilkan data di aplikasi mobile adalah menggunakan tabel.

<figure>
<img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*4ZlAY6HN11n9RyU-lz7B_Q@2x.png" alt="Trulli" style="width:100%">
<figcaption align = "left"><b>Contoh penggunaan tabel di aplikasi mobile</b></figcaption>
</figure>

> **Pertanyaan 2** : Sebutkan kekurangan dan kelebihan menampilkan data menggunakan tampilan tabel di aplikasi mobile!

## Materi 2: Membuat Aplikasi dengan Koneksi Internet

Slide dapat diunduh [di sini](https://app.box.com/s/fsgds8imd9ouflfw9ksaivzspwnt798h).

