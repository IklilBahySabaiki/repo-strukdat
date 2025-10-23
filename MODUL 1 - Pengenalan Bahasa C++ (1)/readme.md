# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Iklil Bahy Sabaiki</p>

## Dasar Teori

Modul 1 membahas pengenalan Code::Blocks IDE dan dasar-dasar bahasa pemrograman C++. Code::Blocks berfungsi sebagai lingkungan kerja terpadu untuk menulis, mengompilasi, dan menjalankan program dengan mudah. Bahasa C++ sendiri merupakan pengembangan dari bahasa C yang bersifat efisien dan mendukung pemrograman berorientasi objek. Dalam modul ini dijelaskan struktur dasar program C++, penggunaan tipe data, variabel, operator, serta cara melakukan input dan output menggunakan cin dan cout. Selain itu, dijelaskan juga proses kompilasi yang mengubah kode sumber menjadi program yang dapat dijalankan serta jenis-jenis kesalahan yang umum terjadi. Secara keseluruhan, modul ini bertujuan agar mahasiswa mampu memahami lingkungan kerja pemrograman dan menulis program C++ sederhana dengan benar.

## Guided 

### 1. [pengenalan bahasa c++ (1)]

```C++
#include <iostream>

using namespace std;

void tulis (int x){
    for (int i = 0; 1 < x; i++ ){
        cout << "Baris ke -: " << i+1 << endl;
    }
}
int main () {
    int jum;
    cout << "Jumlah baris kata: ";
    cin >> jum;
    tulis(jum);
    
    return 0;
}
```
Program di atas berfungsi untuk menampilkan sejumlah baris teks sesuai angka yang dimasukkan pengguna. Nilai input disimpan dalam variabel jum, kemudian dikirim ke fungsi tulis(int x) yang menggunakan perulangan for untuk mencetak teks ke layar dengan perintah cout. Setiap iterasi akan menampilkan tulisan “Baris ke -: [nomor]” hingga jumlah yang ditentukan tercapai. Dengan demikian, program ini menunjukkan cara penggunaan fungsi, perulangan, serta input-output dasar pada bahasa C++.
## Unguided 

### 1. [Soal]

```C++
#include <iostream>
using namespace std;

int main () {
    float a, b;

    cout << "masukan angka: ";
    cin >> a;
    cout << "masukan angka: ";
    cin >> b;

    cout << "a + b = " << (a+b) << endl;
    cout << "a - b = " << (a-b) << endl;
    cout << "a * b = " << (a*b) << endl;
    cout << "a / b = " << (a/b) << endl;

    cout << "a < b = " << (a<b) << endl;
    cout << "a > b = " << (a>b) << endl;
    cout << "a <= b = " << (a<=b) << endl;
    cout << "a >= b = " << (a>=b) << endl;
    cout << "a == b = " << (a==b) << endl;
    cout << "a != b = " << (a!=b) << endl;

    return 0;
}

```
#### Output:
<img width="705" height="382" alt="image" src="https://github.com/user-attachments/assets/5bdeab36-8cf0-4be6-98c6-5f5ecf2b36bd" />


Program di atas digunakan untuk menghitung dan menampilkan hasil operasi aritmatika serta perbandingan antara dua angka yang dimasukkan pengguna. Dengan memanfaatkan cin untuk input dan cout untuk output, program menunjukkan hasil penjumlahan, pengurangan, perkalian, pembagian, serta hubungan perbandingan seperti lebih besar, lebih kecil, sama dengan, atau tidak sama. Program ini bertujuan untuk memahami penggunaan operator aritmatika dan relasional dasar dalam bahasa C++.

#### Full code Screenshot:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0bec5af5-90f5-45d8-8217-3c097f8052bc" />

### 2. [Soal]

```C++
#include <iostream>
#include <string>
using namespace std;

int main() {
    int n;
    cout << "Masukkan angka (0-100): ";
    cin >> n;

    string satuan[] = {"", "satu", "dua", "tiga", "empat", "lima", "enam", "tujuh", "delapan", "sembilan"};
    string hasil;

    if (n == 0) hasil = "nol";
    else if (n == 10) hasil = "sepuluh";
    else if (n == 11) hasil = "sebelas";
    else if (n < 20) hasil = satuan[n - 10] + " belas";
    else if (n < 100) {
        hasil = satuan[n / 10] + " puluh";
        if (n % 10 != 0) hasil += " " + satuan[n % 10];
    } 
    else if (n == 100) hasil = "seratus";
    else hasil = "di luar jangkauan";

    cout << n << " : " << hasil << endl;
    return 0;
}

```
#### Output:
<img width="839" height="359" alt="image" src="https://github.com/user-attachments/assets/d476a788-cebd-45ad-807f-4940c0f3e2c8" />


Program di atas berfungsi untuk mengonversi angka yang dimasukkan pengguna menjadi bentuk tulisan dalam bahasa Indonesia. Dengan menggunakan array satuan dan struktur percabangan if-else, program menentukan cara penulisan angka seperti belas, puluh, atau kasus khusus seperti sepuluh, sebelas, dan seratus. Hasil konversi kemudian ditampilkan ke layar menggunakan fungsi cout.

#### Full code Screenshot:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0151786a-fd19-4769-a77b-31aed84eb23d" />


### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Input: ";
    cin >> n;
    cout << "Output:" << endl;

    for (int i = n; i >= 1; i--) {
        for (int s = 0; s < (n - i); s++)
            cout << "  ";

        for (int j = i; j >= 1; j--)
            cout << j << " ";
        
        cout << "* ";

        for (int j = 1; j <= i; j++)
            cout << j << " ";

        cout << endl;
    }

    return 0;
}

```
#### Output:
<img width="743" height="255" alt="image" src="https://github.com/user-attachments/assets/bdb49835-787e-4126-b3b6-06b37dfa8e48" />

Program di atas digunakan untuk menampilkan pola angka berbentuk piramida terbalik yang simetris dengan tanda bintang di tengahnya. Pengguna memasukkan nilai n, lalu program menggunakan perulangan bersarang untuk mencetak deretan angka menurun di sebelah kiri dan menaik di sebelah kanan bintang, dengan spasi yang diatur agar pola tampak rapi. Program ini menunjukkan penggunaan perulangan dan pengaturan format output dalam bahasa C++.

#### Full code Screenshot:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ba1114a7-4051-43f2-9606-12666604dd7c" />


## Kesimpulan
Secara keseluruhan, kumpulan program yang telah dibahas bertujuan untuk memperkenalkan dasar-dasar pemrograman C++ seperti penggunaan fungsi, variabel, operator, input-output, percabangan, dan perulangan. Melalui berbagai contoh, program pertama menampilkan baris teks berulang, program kedua melakukan operasi aritmatika dan perbandingan dua angka, program ketiga mengonversi angka menjadi tulisan bahasa Indonesia, dan program terakhir mencetak pola angka simetris dengan bintang di tengah. Semua program tersebut menunjukkan cara kerja logika dasar dalam C++ serta penerapan struktur kontrol untuk menghasilkan output yang sesuai.


## Referensi
[1] GeeksforGeeks. (2024, January 10). C++ For Loop (With Examples). Retrieved from https://www.geeksforgeeks.org/cpp-for-loop/
[2]. Tutorialspoint. (n.d.). C++ Operators. Retrieved from https://www.tutorialspoint.com/cplusplus/cpp_operators.htm
[3].GeeksforGeeks. (2024, February 28). Program to convert a given number to words | Set 2. Retrieved from https://www.geeksforgeeks.org/dsa/program-to-convert-a-given-number-to-words-set-2/
