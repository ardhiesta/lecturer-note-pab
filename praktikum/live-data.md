# Android LiveData

Melanjutkan tutorial sebelumnya https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/view-model.md



Ubah file MainViewModel.kt, jadikan variabel counter sebagai MutableLiveData. Selengkapnya sebagai berikut

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

