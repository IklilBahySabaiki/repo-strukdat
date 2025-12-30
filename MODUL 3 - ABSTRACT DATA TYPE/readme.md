# <h1 align="center">ABSTRACT DATA TYPE (3)</h1>
<p align="center">IKLIL BAHY SABAIKI</>

## Dasar Teori

3. MODUL 3 ABSTRACT DATA TYPE (ADT)
## Guided 

### 1. [Nama Topik]

```C++
#include <iostream>
using namespace std;
struct mahasiswa{
 char nim[10];
 int nilai1,nilai2;
};
void inputMhs(mahasiswa &m);
float rata2(mahasiswa m);
int main()
{
 mahasiswa mhs;
 inputMhs(mhs);
 cout << “rata-rata = “ << rata2(mhs);
 return 0;
}
void inputMhs(mahasiswa &m){
 cout << “input nama = “;
 cin >> m.nim;
 cout << “input nilai = “;
 cin >> m.nilai1;
 cout << “input nilai2 = “;
 cin >> m.nilai2;
}
float rata2(mahasiswa m){
 return float(m.nilai1+m.nilai2)/2
```
Kode di atas digunakan untuk menampilkan list mahasiswa dan input nilai.
## Unguided 

### 1. [Soal,]

```C++
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    float uts;
    float uas;
    float tugas;
    float nilaiAkhir;
};

float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return (0.3 * uts) + (0.4 * uas) + (0.3 * tugas);
}

int main() {
    Mahasiswa mhs[10];
    int n;

    cout << "Masukkan jumlah mahasiswa (maks 10): ";
    cin >> n;
    cin.ignore(); 

    if (n > 10) n = 10; 

    for (int i = 0; i < n; i++) {
        cout << "\nData mahasiswa ke-" << i + 1 << endl;
        cout << "Nama   : ";
        getline(cin, mhs[i].nama);
        cout << "NIM    : ";
        getline(cin, mhs[i].nim);
        cout << "UTS    : ";
        cin >> mhs[i].uts;
        cout << "UAS    : ";
        cin >> mhs[i].uas;
        cout << "Tugas  : ";
        cin >> mhs[i].tugas;

        mhs[i].nilaiAkhir = hitungNilaiAkhir(mhs[i].uts, mhs[i].uas, mhs[i].tugas);
        cin.ignore();
    }

    cout << "\n=========================================\n";
    cout << "DATA MAHASISWA\n";
    cout << "=========================================\n";
    for (int i = 0; i < n; i++) {
        cout << "Nama        : " << mhs[i].nama << endl;
        cout << "NIM         : " << mhs[i].nim << endl;
        cout << "UTS         : " << mhs[i].uts << endl;
        cout << "UAS         : " << mhs[i].uas << endl;
        cout << "Tugas       : " << mhs[i].tugas << endl;
        cout << "Nilai Akhir : " << mhs[i].nilaiAkhir << endl;
        cout << "-----------------------------------------\n";
    }

    return 0;
}
```

#### Output:

<img width="353" height="682" alt="image" src="https://github.com/user-attachments/assets/2e9450c3-7957-49fd-a7c8-1f123ed745ed" />

Kode di atas digunakan untuk menghitung dan menampilkan hasil operasi dua matriks 3×3. Pengguna memasukkan elemen matriks A dan B, lalu memilih operasi (tambah, kurang, atau kali). Hasil perhitungan ditampilkan ke layar dengan cout.

#### Full code Screenshot:
<img width="637" height="954" alt="image" src="https://github.com/user-attachments/assets/e2f6599c-7aef-42de-ba68-204f5d717cb8" />


### 2. [SOAL]

pelajaran.h

```C++
#ifndef PELAJARAN_H
#define PELAJARAN_H
#include <string>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodePel;
};

// Fungsi untuk membuat data pelajaran baru
pelajaran create_pelajaran(string namaMapel, string kodePel);

// Prosedur untuk menampilkan data pelajaran
void tampil_pelajaran(pelajaran pel);

#endif
```


pelajaran.cpp

```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

// Implementasi fungsi create_pelajaran
pelajaran create_pelajaran(string namaMapel, string kodePel) {
    pelajaran pel;
    pel.namaMapel = namaMapel;
    pel.kodePel = kodePel;
    return pel;
}

// Implementasi prosedur tampil_pelajaran
void tampil_pelajaran(pelajaran pel) {
    cout << "nama pelajaran : " << pel.namaMapel << endl;
    cout << "nilai : " << pel.kodePel << endl;
}

```

main.cpp

```C++
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string namaMapel = "Struktur Data";
    string kodePel = "STD";

    pelajaran pel = create_pelajaran(namaMapel, kodePel);
    tampil_pelajaran(pel);

    return 0;
}
```
### Output
<img width="364" height="102" alt="image" src="https://github.com/user-attachments/assets/387a152a-adaa-430d-846f-ad89846b638a" />

### Fullscreenshot
pelajaran.h

<img width="477" height="303" alt="image" src="https://github.com/user-attachments/assets/af342859-19aa-4cb2-88e0-74ea5010d213" />

pelajaran.cpp
<img width="537" height="322" alt="image" src="https://github.com/user-attachments/assets/cc41b69c-dd87-4763-b13c-f83bc6387c82" />

main.cpp
<img width="468" height="240" alt="image" src="https://github.com/user-attachments/assets/64aeaa8c-6b86-405c-b080-b8e5a22b3d6d" />

kode diatas untuk membuat program lebih terstruktur, modular, dan mudah dikembangkan.

### 3. [SOAL]
```C++
#include <iostream>
using namespace std;

// Fungsi untuk menampilkan isi array 2D
void tampilArray(int arr[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << arr[i][j] << "\t";
        }
        cout << endl;
    }
}

// Fungsi untuk menukar isi dari dua array 2D pada posisi tertentu
void tukarElemen(int arr1[3][3], int arr2[3][3], int baris, int kolom) {
    int temp = arr1[baris][kolom];
    arr1[baris][kolom] = arr2[baris][kolom];
    arr2[baris][kolom] = temp;
}

// Fungsi untuk menukar isi dari dua pointer integer
void tukarPointer(int* ptr1, int* ptr2) {
    int temp = *ptr1;
    *ptr1 = *ptr2;
    *ptr2 = temp;
}

int main() {
    int A[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int B[3][3] = {
        {9, 8, 7},
        {6, 5, 4},
        {3, 2, 1}
    };

    int x = 10, y = 20;
    int *p1 = &x;
    int *p2 = &y;

    cout << "Array A sebelum ditukar:\n";
    tampilArray(A);
    cout << "\nArray B sebelum ditukar:\n";
    tampilArray(B);

    // Menukar elemen pada posisi [1][2] (baris ke-2 kolom ke-3)
    tukarElemen(A, B, 1, 2);

    cout << "\nSetelah menukar elemen pada posisi [1][2]:\n";
    cout << "Array A:\n";
    tampilArray(A);
    cout << "\nArray B:\n";
    tampilArray(B);

    // Menampilkan nilai pointer sebelum ditukar
    cout << "\nNilai yang ditunjuk pointer sebelum ditukar:\n";
    cout << "p1 menunjuk nilai = " << *p1 << endl;
    cout << "p2 menunjuk nilai = " << *p2 << endl;

    // Menukar nilai yang ditunjuk pointer
    tukarPointer(p1, p2);

    cout << "\nNilai yang ditunjuk pointer setelah ditukar:\n";
    cout << "p1 menunjuk nilai = " << *p1 << endl;
    cout << "p2 menunjuk nilai = " << *p2 << endl;

    return 0;
}
```
### Output

<img width="406" height="472" alt="image" src="https://github.com/user-attachments/assets/4d1e4782-7b45-42d0-8ea5-2cbcaf1b8f48" />

### Full screenshot
<img width="583" height="936" alt="image" src="https://github.com/user-attachments/assets/3019d59f-a8d1-422a-a6b1-0ee8e14a9929" />
<img width="506" height="213" alt="image" src="https://github.com/user-attachments/assets/a6cb1056-a91f-4f02-9599-cea7bce0c084" />


## Kesimpulan
Kode ini menunjukkan bagaimana penggunaan array dua dimensi (2D) dan pointer dalam bahasa C++. Program ini mendemonstrasikan tiga konsep utama.

  ## Referensi
Abstract Data Types in Object-Capability Systems — James Noble, Sophia Drossopoulou, Mark S. Miller, Toby Murray, Alex Potanin (ECOOP 2016)





