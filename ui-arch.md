---
marp: true
---

# App Architecture (UI)

## Pengembangan Aplikasi Bergerak

#### Ardhi Wijayanto

Informatika
Universitas Sebelas Maret
2023

---
## View Binding

[Fitur](https://developer.android.com/topic/libraries/view-binding) yang dapat membantu programmer agar lebih mudah untuk berinteraksi dengan View yang ada pada Layout XML Android (alternatif dari findViewById, Butterknife, atau Kotlin Synthetic). 

Binding class akan digenerate untuk setiap xml yang dibuat, id dari widget dapat diakses melalui binding class tidak perlu membuat variabel untuk setiap id widget.

---
## View Binding

Tanpa view binding

```
val buttonSubmit = findViewById<Button>(R.id.btnSubmit)
buttonSubmit.setOnClickListener { ... }
```

dengan view binding

```
private lateinit var binding: ActivityMainBinding
...
binding = ActivityMainBinding.inflate(layoutInflater)
...
binding.btnSubmit.setOnClickListener { ... }
```

---
## MVVM (Model-View-ViewModel)



---
## LiveData