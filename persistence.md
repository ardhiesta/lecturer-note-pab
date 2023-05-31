---
marp: true
---

# Penyimpanan Data pada Aplikasi Mobile

## Pengembangan Aplikasi Bergerak

#### Ardhi Wijayanto

Informatika
Universitas Sebelas Maret
2023

---
## Latar Belakang

Pada beberapa aplikasi diperlukan adanya kemampuan untuk menyimpan data (teks, gambar, audio, video, dll).
Data dapat disimpan secara lokal / *client side* (pada perangkat *smartphone*) ataupun disimpan di *server*.

---
## Folder di Android

![folder](https://github.com/ardhiesta/lecturer-note-pab/blob/main/images/efb.jpg?raw=true)

---
## Android File System

Supported file system 
Low level : exfat, ext4, f2fs, fuse, incfs, Vfat, EROFS
Virtual : debugfs, overlayfs, procfs, sysfs, tmpfs, tracefs

---
## File System Hierrarchy
![file-system](https://miro.medium.com/v2/resize:fit:640/format:webp/1*x9rvV75FdTQj3ol4bJdZUQ.jpeg)

/boot : berisi kernel dan ramdisk
/system : memuat OS
/recovery : backup
/data : data user
/cache : frequently accessed data app & components
/misc : miscellaneous system settings

---
## Android Storage

Opsi [penyimpanan data](https://developer.android.com/training/data-storage) aplikasi Android :
- *App-specific storage* : Penyimpanan data untuk suatu aplikasi, dapat menggunakan *dedicated directories* dalam sebuah *internal storage* atau bisa juga menggunakan *external storage* (gunakan *internal storage* untuk data sensitif yang tidak diakses oleh aplikasi lain). 
- *Shared storage* : Penyimpanan data untuk file yang dibagikan / dapat diakses oleh aplikasi lain (*media files*, dokumen).
- *Preferences* : Penyimpanan data aplikasi dalam bentuk pasangan *key-value*.
- *Databases* : Penyimpanan data terstuktur dalam *private database*. 

---
## Internal vs External Storage

[Old days definitions](https://tdcolvin.medium.com/demystifying-internal-vs-external-storage-in-modern-android-c9c31cb8eeec#:~:text=Internal%20storage%20meant%20the%20device's,as%20an%20inserted%20SD%20card.)
- Internal storage :
- External storage :
