# Android ViewModel

Dalam aplikasi Android, sebaiknya dilakukan design struktur aplikasi. Salah satu pendekatan yang dilakukan adalah memisahkan bagian code untuk UI dan code untuk data. Berikut ini diberikan contoh pemisahan UI dan data melalui penggunaan ViewModel. Selengkapnya mengenai ViewModel dapat dibaca pada link yang sudah saya share di classroom di chapter 08. App Architecture.

Buat project baru, misalnya diberi 
```
nama aplikasi : Simple Counter
nama package : com.simple.counter
```
Aplikasi yang dibuat ini berisi sebuah tombol dan sebuah text, setiap tombol diklik akan dilakukan increment bilangan yang hasilnya ditampilkan pada text.

Aktifkan view binding dengan menambahkan code berikut pada 
di build.gradle (app) di dalam segment android { ... }, tambahkan sebelum baris buildTypes {

```
buildFeatures {
        viewBinding = true
}
```

Berikut ini adalah code layout aplikasinya (file activity_main.xml)
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".MainActivity">
    <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="0"
            android:textAppearance="@style/TextAppearance.AppCompat.Large"
            android:textStyle="bold"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            android:id="@+id/tvCounter" android:layout_marginTop="64dp"/>

    <Button android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Add"
            android:id="@+id/btnAdd"
            android:layout_marginTop="64dp" app:layout_constraintTop_toBottomOf="@+id/tvCounter"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

Pada MainActivity.kt, tambahkan code untuk melakukan increment counter dan menampilkan hasilnya di text
```
package com.simple.counter

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import com.simple.counter.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    // variabel binding
    private lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)

        // variabel counter yang akan diincrement
        var counter: Int = 0
        // menambahkan listener, button diklik akan mengeksekusi code
        binding.btnAdd.setOnClickListener{
            // proses increment
            counter++
            // menampilkan counter ke text
            binding.tvCounter.setText(counter.toString())
        }
    }
}
```

Jalankan project Android yang sudah dibuat

PERTANYAAN

1. Setelah program muncul di hp / emulator, klik tombol Add. Jelaskan apa yang terjadi!

2. Ubah orientasi layar hp / emulator, misalnya sebelumnya portrait menjadi landscape. Amati text counter pada aplikasi, jelaskan apa yang terjadi!

Pada code sebelumnya, UI dan data (bilangan counter) dijadikan satu di dalam activity. Kita akan memisahkan data dari activity dengan membuat ViewModel.

Tambahkan 
```
implementation "androidx.activity:activity-ktx:1.7.1"
```
di dalam build.gradle (app)

Buat file baru, beri nama MainViewModel.kt

```
package com.simple.counter

import androidx.lifecycle.ViewModel

class MainViewModel : ViewModel() {
    var counter: Int = 0

    fun addNumber() {
        counter++
    }
}
```

Ubah MainActivity.kt menjadi
```
package com.simple.counter

import android.os.Bundle
import androidx.activity.viewModels
import androidx.appcompat.app.AppCompatActivity
import com.simple.counter.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    // variabel binding
    private lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)

        val mainViewModel: MainViewModel by viewModels()

        updateTextCounter(mainViewModel)

        // menambahkan listener, button diklik akan mengeksekusi code
        binding.btnAdd.setOnClickListener{
            // memanggil fungsi addNumber di mainViewModel untuk melakukan increment counter
            mainViewModel.addNumber()
            updateTextCounter(mainViewModel)
        }
    }

    // fungsi untuk mengupdate tampilan text sesuai jumlah counter
    fun updateTextCounter(mainViewModel: MainViewModel) {
        binding.tvCounter.setText(mainViewModel.counter.toString())
    }
}
```

Jalankan program yang telah diubah codenya

PERTANYAAN

3. Setelah program muncul di hp / emulator, klik tombol Add. Jelaskan apa yang terjadi!

4. Ubah orientasi layar hp / emulator, misalnya sebelumnya portrait menjadi landscape. Amati text counter pada aplikasi, jelaskan apa yang terjadi!


source code lengkap ada di https://github.com/ardhiesta/SimpleCounter