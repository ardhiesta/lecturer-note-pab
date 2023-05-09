# Android LiveData

Kali ini kita akan berkenalan dengan LiveData. Sebenarnya apa sih LiveData itu? 

> LiveData is an observable data holder class. Unlike a regular observable, LiveData is lifecycle-aware, meaning it respects the lifecycle of other app components, such as activities, fragments, or services. This awareness ensures LiveData only updates app component observers that are in an active lifecycle state.

*Observable data holder class* : maksudnya LiveData ini adalah sebuah class yang menangani data observable, yaitu ketika terjadi perubahan terhadap suatu data programmer tidak perlu dilakukan update secara manual (menambahkan code untuk memeriksa perubahan data).

*LiveData is lifecycle-aware* : LiveData ini memiliki lifecycle. Jika ada perubahan data, maka LiveData akan memberitahukan kepada kelas Observer (yang mengamati perubahan data) jika ada perubahan, dan akan diubah ketika status lifecycle nya dalam keadaan aktif, jika tidak, maka LiveData tidak akan memberitahukannya sampai lifecycle nya dalam keadaan aktif.

Lebih lengkapnya dapat dibaca [di sini](https://developer.android.com/topic/libraries/architecture/livedata) dan [di sini](https://kotakode.com/blogs/6956/PDKT-dengan-LiveData-di-Android%2C-Yuk!).

Melanjutkan [tutorial sebelumnya](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/view-model.md), kita akan menggunakan LiveData ke dalam aplikasi.

Ubah file MainViewModel.kt, jadikan variabel counter sebagai MutableLiveData. MutableLiveData adalah kelas turunan dari LiveData yang mempunyai kemampuan untuk mengubah data.

Selengkapnya sebagai berikut

```
package com.simple.counter

import androidx.lifecycle.MutableLiveData
import androidx.lifecycle.ViewModel

class MainViewModel : ViewModel() {
    var counter = MutableLiveData<Int>()

    init {
        counter.value = 0
    }

    fun addNumber() {
        counter.value = (counter.value)?.plus(1)
    }
}
```

Ubah MainActivity.kt menjadi
```
package com.simple.counter

import android.os.Bundle
import androidx.activity.viewModels
import androidx.appcompat.app.AppCompatActivity
import androidx.lifecycle.Observer
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

        mainViewModel.counter.observe(this, Observer {
            binding.tvCounter.text = it.toString()
        })
        binding.btnAdd.setOnClickListener{
            mainViewModel.addNumber()
        }
    }
}
```

Jawablah pertanyaan berikut ini

Bandingkan dengan [tutorial sebelumnya](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/view-model.md), berikan penjelasan mengenai keuntungan yang didapat dari penggunaan LiveData!