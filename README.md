
# Tugas Permograman Mobil

NAMA  : SERIUS NDRURU

NIM   : 312210508

KELAS : TI.22.A.5

DOSEN PENGAMPUH : DONNY MAULANA, S.Kom., M.M.S.I

## MainActivity.java

1. Package dan Import Statements:


```bash
  package com.example.fibonnaci;

  import androidx.appcompat.app.AlertDialog;
  import androidx.appcompat.app.AppCompatActivity;

  import android.content.DialogInterface;
  import android.graphics.Color;
  import android.os.Bundle;
  import android.view.View;
  import android.widget.EditText;
  import android.widget.TextView;

```
- package com.example.fibonnaci;: Menunjukkan bahwa kelas tersebut berada dalam paket dengan nama "com.example.fibonnaci".

- import androidx.appcompat.app.AppCompatActivity;: Mengimpor kelas AppCompatActivity dari AndroidX, yang memberikan fungsionalitas dasar untuk membuat aktivitas pada aplikasi Android.

- import ... AlertDialog;, import ... DialogInterface;: Mengimpor kelas AlertDialog dan DialogInterface untuk menampilkan dialog interaktif.

- import android.graphics.Color;: Mengimpor kelas Color untuk manipulasi warna.

- import android.os.Bundle;: Mengimpor kelas Bundle untuk mengelola data instance state dari aktivitas.

- import android.view.View;: Mengimpor kelas View untuk bekerja dengan antarmuka pengguna.

- import android.widget.EditText;, import android.widget.TextView;: Mengimpor kelas EditText dan TextView untuk bekerja dengan elemen antarmuka pengguna.
 
2. Deklarasi Kelas dan Variabel Kelas:

```bash
  public class MainActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1;
```
- public class MainActivity extends AppCompatActivity {: Mendeklarasikan kelas MainActivity yang merupakan aktivitas utama dalam aplikasi dan mewarisi dari AppCompatActivity.

- private TextView show_count;: Mendeklarasikan variabel show_count sebagai objek TextView.

- private int count = 1;: Mendeklarasikan variabel count sebagai integer dan menginisialisasinya dengan nilai 1.

- private long fibNMinus1 = 1;: Mendeklarasikan variabel fibNMinus1 sebagai long dan menginisialisasinya dengan nilai 1.

- private long fibNMinus2 = 0;: Mendeklarasikan variabel fibNMinus2 sebagai long dan menginisialisasinya dengan nilai 0.

- private int limit = -1;: Mendeklarasikan variabel limit sebagai integer dan menginisialisasinya dengan nilai -1.

3. onCreate Method:
```bash
  protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        show_count = findViewById(R.id.show_count);
    }
```
- @Override: Menandakan bahwa metode ini meng-override metode dari kelas induknya (parent class).

- protected void onCreate(Bundle savedInstanceState) {: Metode yang dipanggil saat aktivitas dibuat. Menginisialisasi tata letak aktivitas menggunakan layout yang didefinisikan dalam file XML (activity_main.xml) dan mengaitkan elemen antarmuka pengguna dengan variabel show_count.

4. countUp Method:

```bash
  public void countUp(View view) {
        if (count == 0) {
            show_count.setText("1");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                count = 1;
                fibNMinus1 = 0;
                fibNMinus2 = 1;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                int colorResId = R.color.orange;
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.orange;
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda;
                        break;
                    case 3:
                        colorResId = R.color.purple;
                        break;
                    case 4:
                        colorResId = R.color.salem;
                        break;
                    case 5:
                        colorResId = R.color.birumuda;
                        break;
                    case 6 :
                        colorResId = R.color.kuning;
                        break;
                    case 7:
                        colorResId = R.color.hijau;
                        break;
                    case 8:
                        colorResId = R.color.cream;
                        break;
                    case 9:
                        colorResId = R.color.pink;
                        break;
                    case 10:
                        colorResId = R.color.biru;
                        break;
                    case 11:
                        colorResId = R.color.colorAccent;
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
                show_count.setBackgroundColor(Color.DKGRAY);
            }
        }

        count++;
    }
```
- public void countUp(View view) {: Metode yang dipanggil saat tombol di layar ditekan untuk menghitung dan menampilkan nilai deret Fibonacci selanjutnya.

5. Reset Method:

```bash
  public void Reset(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
```
- public void Reset(View view) {: Metode yang dipanggil saat tombol reset di layar ditekan untuk mengatur ulang nilai-nilai dan memulai deret Fibonacci dari awal.

6. setLimit Method:
```bash
  public void setLimit(View view) {
```

- public void setLimit(View view) {: Metode yang dipanggil saat tombol "Set Limit" di layar ditekan untuk menampilkan dialog dan meminta pengguna memasukkan batas (limit) deret Fibonacci.

7. DialogBuilder:
```bash
  AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();
```
- Membuat objek AlertDialog.Builder untuk membangun dialog.
- Menambahkan judul dan elemen EditText ke dalam dialog.
- Menetapkan tindakan (listener) untuk tombol "OK" dan "Cancel" di dalam dialog.
- Menampilkan dialog menggunakan builder.show().

## activity_main..xml
1. ConstraintLayout (Utama)
```bash
  <?xml version="1.0" encoding="utf-8"?>
  <androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
```
- Atribut Utama:

    - xmlns:android="http://schemas.android.com/apk/res/android": Mendefinisikan namespace Android.
    - xmlns:app="http://schemas.android.com/apk/res-auto": Namespace untuk atribut tambahan yang didefinisikan oleh aplikasi.
    - xmlns:tools="http://schemas.android.com/tools": Namespace untuk alat pengembangan Android.

- Atribut Layout:

    - android:layout_width="match_parent": Lebar layout diatur agar sama dengan lebar parent.
    - android:layout_height="match_parent": Tinggi layout diatur agar sama dengan tinggi parent.
    - tools:context=".MainActivity": Context yang digunakan untuk keperluan desain dan tampilan di editor.

2. Button (button_toast)
```bash
  <Button
        android:id="@+id/button_toast"
        android:layout_width="226dp"
        android:layout_height="52dp"
        android:layout_marginTop="4dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:text="NumMax"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.987"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```
- Atribut Utama:

    - android:id="@+id/button_toast": ID unik untuk tombol ini.
    - android:layout_width="226dp": Lebar tombol diatur ke 226dp.
    - android:layout_height="52dp": Tinggi tombol diatur ke 52dp.
    - android:layout_marginTop="4dp": Margin atas tombol diatur ke 4dp.
    - android:background="@color/colorPrimary": Warna latar belakang tombol diambil dari resource warna colorPrimary.
    - android:onClick="setLimit": Nama metode yang akan dipanggil saat tombol diklik.
    - android:text="NumMax": Teks tombol diatur sebagai "NumMax".
    - android:textColor="@android:color/white": Warna teks diatur sebagai putih.

- Batasan (Constraints):

    - app:layout_constraintEnd_toEndOf="parent": Bagian akhir tombol diikat ke bagian akhir parent.
    - app:layout_constraintHorizontal_bias="0.987": Bias horizontal diatur.
    - app:layout_constraintStart_toStartOf="parent": Bagian awal tombol diikat ke bagian awal parent.
    - app:layout_constraintTop_toTopOf="parent": Bagian atas tombol diikat ke bagian atas parent.

3. Button (button)

```bash
  <Button
        android:id="@+id/button"
        android:layout_width="185dp"
        android:layout_height="52dp"
        android:layout_marginTop="4dp"
        android:background="@color/colorPrimary"
        android:text="Toast"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="MissingConstraints" />
```

- Atribut Utama:

    - android:id="@+id/button": ID unik untuk tombol ini.
    - android:layout_width="185dp": Lebar tombol diatur ke 185dp.
    - android:layout_height="52dp": Tinggi tombol diatur ke 52dp.
    - android:layout_marginTop="4dp": Margin atas tombol diatur ke 4dp.
    - android:background="@color/colorPrimary": Warna latar belakang tombol diambil dari resource warna colorPrimary.
    - android:text="Toast": Teks tombol diatur sebagai "Toast".
    - android:textColor="@android:color/white": Warna teks diatur sebagai putih.

- Batasan (Constraints):

    - app:layout_constraintEnd_toEndOf="parent": Bagian akhir tombol diikat ke bagian akhir parent.
    - app:layout_constraintHorizontal_bias="0.0": Bias horizontal diatur.
    - app:layout_constraintStart_toStartOf="parent": Bagian awal tombol diikat ke bagian awal parent.
    - app:layout_constraintTop_toTopOf="parent": Bagian atas tombol diikat ke bagian atas parent.
    - tools:ignore="MissingConstraints": Mengabaikan kesalahan kurangnya batasan.

4. Button (button2)

```bash
  <Button
        android:id="@+id/button2"
        android:layout_width="204dp"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.99"
        app:layout_constraintStart_toStartOf="parent" />
```
- Atribut Utama:

    - android:id="@+id/button2": ID unik untuk tombol ini.
    - android:layout_width="204dp": Lebar tombol diatur ke 204dp.
    - android:layout_height="wrap_content": Tinggi tombol disesuaikan dengan kontennya.
    - android:background="@color/colorPrimary": Warna latar belakang tombol diambil dari resource warna colorPrimary.
    - android:onClick="countUp": Nama metode yang akan dipanggil saat tombol diklik.
    - android:text="@string/button_label_count": Teks tombol diambil dari string resource.
    - android:textColor="@android:color/white": Warna teks diatur sebagai putih.

- Batasan (Constraints):

    - app:layout_constraintBottom_toBottomOf="parent": Bagian bawah tombol diikat ke bagian bawah parent.
    - app:layout_constraintEnd_toEndOf="parent": Bagian akhir tombol diikat ke bagian akhir parent.
    - app:layout_constraintHorizontal_bias="0.99": Bias horizontal diatur.
    - app:layout_constraintStart_toStartOf="parent": Bagian awal tombol diikat ke bagian awal parent.

5. Button (back)
```bash
  <Button
        android:id="@+id/back"
        android:layout_width="204dp"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:onClick="Back"
        android:text="@string/Back"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore=",Rtlcompat"/>
```
- Atribut Utama:

    - android:id="@+id/back": ID unik untuk tombol ini.
    - android:layout_width="204dp": Lebar tombol diatur ke 204dp.
    - android:layout_height="wrap_content": Tinggi tombol disesuaikan dengan kontennya.
    - android:background="@color/colorPrimary": Warna latar belakang tombol diambil dari resource warna colorPrimary.
    - android:onClick="Back": Nama metode yang akan dipanggil saat tombol diklik.
    - android:text="@string/Back": Teks tombol diambil dari string resource.
    - android:textColor="@android:color/white": Warna teks diatur sebagai putih.

- Batasan (Constraints):

    - app:layout_constraintBottom_toBottomOf="parent": Bagian bawah tombol diikat ke bagian bawah parent.
    - app:layout_constraintEnd_toEndOf="parent": Bagian akhir tombol diikat ke bagian akhir parent.
    - app:layout_constraintHorizontal_bias="0.0": Bias horizontal diatur.
    - app:layout_constraintStart_toStartOf="parent": Bagian awal tombol diikat ke bagian awal parent.
    - tools:ignore=",Rtlcompat": Mengabaikan kesalahan, termasuk Rtlcompat.

6. TextView (show_count)
```bash
  <TextView
        android:id="@+id/show_count"
        android:layout_width="407dp"
        android:layout_height="626dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button_toast"
        tools:ignore=",Rtlcompat" />
```
- Atribut Utama:

    - android:id="@+id/show_count": ID unik untuk TextView ini.
    - android:layout_width="407dp": Lebar TextView diatur ke 407dp.
    - android:layout_height="626dp": Tinggi TextView diatur ke 626dp.
    - android:background="#FFFF00": Warna latar belakang TextView diatur sebagai kuning.
    - android:gravity="center_vertical": Teks diberi tata letak secara vertikal di tengah.
    - android:text="1": Teks awal TextView diatur sebagai "1".
    - android:textAlignment="center": Teks diberi tata letak secara horizontal di tengah.
    - android:textColor="@color/colorPrimary": Warna teks diambil dari resource warna colorPrimary.
    - android:textSize="160sp": Ukuran teks diatur ke 160sp.
    - android:textStyle="bold": Gaya teks diatur sebagai tebal.

- Batasan (Constraints):

    - app:layout_constraintBottom_toTopOf="@+id/button2": Bagian bawah TextView diikat ke bagian atas tombol button2.
    - app:layout_constraintEnd_toEndOf="parent": Bagian akhir TextView diikat ke bagian akhir parent.
    - app:layout_constraintStart_toStartOf="parent": Bagian awal TextView diikat ke bagian awal parent.
    - app:layout_constraintTop_toBottomOf="@+id/button_toast": Bagian atas TextView diikat ke bagian bawah tombol button_toast.
    - tools:ignore=",Rtlcompat": Mengabaikan kesalahan, termasuk Rtlcompat.

## Colors.xml
```bash
  <resources>
    <string name="app_name">Toast</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">0</string>
    <string name="coast_message">Hello Toast</string>
    <string name="Back">Exit</string>
</resources>
```

- Kode XML di atas mendefinisikan sebuah sumber daya array dengan nama "fibonacci_colors." Array ini berisi daftar referensi ke warna-warna yang didefinisikan dalam file colors.xml. Setiap elemen dalam array ini adalah referensi ke warna, seperti @color/black, @color/white, dan sebagainya. Dalam kelas MainActivity, terdapat metode changeTextColor(). Metode ini digunakan untuk mengganti warna teks pada TextView dengan warna acak dari array fibonacci_colors.
Menggunakan kode TypedArray colors = res.obtainTypedArray(R.array.fibonacci_colors), kita mengambil referensi ke sumber daya array yang telah didefinisikan di atas. Kemudian, kita menggunakan Random untuk menghasilkan indeks acak dari array tersebut, dan mengambil warna sesuai dengan indeks acak tersebut dengan int randomColor = colors.getColor(randomIndex, 0).

Dengan cara ini, setiap kali tombol "Hitung" diklik, warna teks pada TextView akan diubah menjadi warna acak yang ada dalam array fibonacci_colors, menambahkan elemen visual yang menarik ke aplikasi .