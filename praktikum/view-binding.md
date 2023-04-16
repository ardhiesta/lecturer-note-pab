# Android View Binding

View Binding adalah fitur yang dapat membantu programmer agar lebih mudah untuk berinteraksi dengan View yang ada pada Layout XML Android (alternatif dari findViewById, Butterknife, atau Kotlin Synthetic). Selengkapnya mengenai view binding dapat dibaca [di sini](https://developer.android.com/topic/libraries/view-binding).

Melalui tutorial berikut ini akan kita lihat perbedaannya.

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
            android:inputType="textPersonName"
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

3.