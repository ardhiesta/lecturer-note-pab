# Activity dan Intent

Buat project Android baru di IntelliJ IDEA

Pilih Empty Activity

![activity](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/img/empty.jpg?raw=true)

Selanjutnya isi detail project

![proj](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/img/newproj.jpg?raw=true)

Tambahkan tombol di activity_main.xml

![btn](https://github.com/ardhiesta/lecturer-note-pab/blob/main/praktikum/img/layout1.jpg?raw=true)

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
            android:text="Hello World!"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintTop_toTopOf="parent" android:id="@+id/textView"/>
    <Button
            android:text="Submit"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:id="@+id/button"
            android:layout_marginTop="32dp"
            app:layout_constraintTop_toBottomOf="@+id/textView"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
    />

</androidx.constraintlayout.widget.ConstraintLayout>
```

Tambahkan Empty Activity baru, misal beri nama Activity2

tambahkan teks di activity_2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context=".Activity2">

    <TextView
            android:text="ini adalah activity 2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" android:id="@+id/textView2"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintEnd_toEndOf="parent" app:layout_constraintBottom_toBottomOf="parent"
    />
</androidx.constraintlayout.widget.ConstraintLayout>
```

di MainActivity.kt Tambahkan code untuk memanggil Activity2
```
import android.content.Intent
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import androidx.core.content.ContextCompat.startActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val btn = findViewById<Button>(R.id.button)
        btn.setOnClickListener {
            val intent = Intent(this, Activity2::class.java)
            startActivity(intent)
        }
    }
}
```