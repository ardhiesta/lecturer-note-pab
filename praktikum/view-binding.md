# Android View Binding

View Binding adalah fitur yang dapat membantu programmer agar lebih mudah untuk berinteraksi dengan View yang ada pada Layout XML Android (alternatif dari findViewById, Butterknife, atau Kotlin Synthetic). Selengkapnya mengenai view binding dapat dibaca [di sini](https://developer.android.com/topic/libraries/view-binding).

Melalui tutorial berikut ini akan kita lihat perbedaannya. Pada tutorial ini akan dibuat aplikasi yang menerima input text dari user dan menampilkan text yang diinput user ke TextView, untuk lebih jelasnya silakan lihat di [video demo](https://youtu.be/yDeLrAqDyOI). 

1. Buat project Android baru di IntelliJ IDEA / Android Studio. Pilih **Empty Activity** dan beri nama misal dengan nama project **Hello View Binding** dan package name **hello.view.binding**

2. Tambahkan code berikut untuk membuat layout di activity_main.xml

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
            android:id="@+id/tvOutput"
            android:text="Hello World!"
            app:layout_constraintEnd_toEndOf="parent"
            android:layout_marginTop="16dp"
            app:layout_constraintTop_toBottomOf="@+id/btnSubmit"
            android:layout_marginEnd="16dp"/>
    <EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:inputType=""
            android:hint="ketik text di sini"
            android:text=""
            android:ems="10"
            android:id="@+id/etInput"
            app:layout_constraintTop_toTopOf="parent"
            android:layout_marginTop="64dp"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            android:layout_marginStart="8dp"
            android:layout_marginEnd="8dp"/>
    <Button
            android:text="submit"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:id="@+id/btnSubmit"
            android:layout_marginTop="24dp"
            app:layout_constraintTop_toBottomOf="@+id/etInput"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            android:layout_marginStart="32dp"
            android:layout_marginEnd="32dp"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

kita akan mendapatkan layout activity sebagai berikut 

![viewb](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/img/viewb.jpg?raw=true)

3. Tambahkan code di MainActivity.kt untuk mengambil text yang diinputkan user dan menampilkan hasilnya di TextView, code selengkapnya adalah sebagai berikut.

```
package hello.view.binding

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // mengarahkan tampilan activity menggunakan layout activity_main.xml
        setContentView(R.layout.activity_main)

        // membuat variabel yang berisi object widget
        // variabel untuk widget EditText, tempat user mengetikkan text
        val editTextInput = findViewById<EditText>(R.id.etInput)
        // variabel untuk widget Button, tombol yang diklik user untuk mengambil text input dan menampilkan ke TextView
        val buttonSubmit = findViewById<Button>(R.id.btnSubmit)
        // variabel untuk widget TextView, tempat menampilkan text yang diinput di EditText
        val textOutput = findViewById<TextView>(R.id.tvOutput)

        // menambahkan listener OnClick, klik pada Button akan mengeksekusi code
        buttonSubmit.setOnClickListener {
            // code yang dieksekusi apabila Button diklik
            // mengambil text yang diketik pada EditText
            var textInputFromUser = editTextInput.text.toString()
            // menampilkan text yang diinput dari EditText ke TextView
            textOutput.text = textInputFromUser
        }
    }
}
```

4. Jalankan project Android melalui emulator / smartphone

5. Sekarang kita gunakan Android View Binding, pertama tambahkan code berikut di build.gradle (app) di dalam segment android { ... }, misalnya sebelum baris buildTypes {

```
buildFeatures {
        viewBinding = true
}
```

6. Ubah code MainActivity.kt 

```
package hello.view.binding

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import hello.view.binding.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
// variabel binding
private lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)

        // menambahkan listener OnClick, klik pada Button akan mengeksekusi code
        binding.btnSubmit.setOnClickListener {
            // code yang dieksekusi apabila Button diklik
            // mengambil text yang diketik pada EditText
            var textInputFromUser = binding.etInput.text.toString()
            // menampilkan text yang diinput dari EditText ke TextView
            binding.tvOutput.text = textInputFromUser
        }
    }
}
```

7. Apabila project dijalankan, akan didapatkan hasil yang sama

Jawablah pertanyaan berikut

1. Apa saja perbedaan antara sebelum dan sesudah menggunakan Android View Binding?

2. Apa keuntungan yang didapatkan dari penggunaan Android View Binding?