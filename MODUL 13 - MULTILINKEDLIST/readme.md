# <h1 align="center">MULTI LINKED LIST</h1>
<p align="center">IKLIL BAHY SABAIKI</p>

## Dasar Teori

Multi List itu kumpulan dari beberapa list yang saling terhubung. Setiap elemen di dalamnya bisa punya list sendiri. Biasanya ada list utama (induk) dan list tambahan yang jadi anaknya.

## Guided 

### 1. [Nama Topik]

```C++
#include <iostream>
using namespace std;

int main() {
    cout << "ini adalah file code guided praktikan" << endl;
    return 0;
}
```
Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

## Unguided 

### 1. [Soal]

**multilist.h**
```C++
#ifndef SLL_H
#define SLL_H
#include <iostream>
using namespace std;

struct Mahasiswa {
    string nama;
    string nim;
    char kelamin; 
    float ipk;
};

struct Node {
    Mahasiswa info;
    Node *next;
};

struct List {
    Node *first;
};

void createList(List &L);
Node* alokasi(Mahasiswa x);
void insertFirst(List &L, Node *p);
void insertLast(List &L, Node *p);
void insertAfter(Node *prec, Node *p);
void printInfo(List L);

#endif
}
```
**multilist.cpp**
```C++
#include "multilist.h"

void createList(List &L) {
    L.first = NULL;
}

Node* alokasi(Mahasiswa x) {
    Node *p = new Node;
    p->info = x;
    p->next = NULL;
    return p;
}

void insertFirst(List &L, Node *p) {
    p->next = L.first;
    L.first = p;
}

void insertLast(List &L, Node *p) {
    if (L.first == NULL) {
        L.first = p;
    } else {
        Node *q = L.first;
        while (q->next != NULL) q = q->next;
        q->next = p;
    }
}

void insertAfter(Node *prec, Node *p) {
    p->next = prec->next;
    prec->next = p;
}

void printInfo(List L) {
    Node *p = L.first;

    while (p != NULL) {
        cout << "Nama : " << p->info.nama << endl;
        cout << "NIM  : " << p->info.nim << endl;
        cout << "L/P  : " << p->info.kelamin << endl;
        cout << "IPK  : " << p->info.ipk << endl << endl;
        p = p->next;
    }
}
```
**main.cpp**
```C++
#include "multilist.h"

int main() {
    List L;
    createList(L);

    cout << "coba insert first, last, dan after" << endl;

    Mahasiswa m1 = {"Ali", "01", 'L', 3.3};
    insertFirst(L, alokasi(m1));

    Mahasiswa m2 = {"Bobi", "02", 'L', 3.71};
    insertLast(L, alokasi(m2));

    Mahasiswa m3 = {"Cindi", "03", 'P', 3.5};
    insertLast(L, alokasi(m3));

    Mahasiswa m4 = {"Danu", "04", 'L', 4.0};
    Node *p = L.first;
    while (p->info.nama != "Cindi") p = p->next;
    insertAfter(p, alokasi(m4));

    insertLast(L, alokasi({"Eli", "05", 'P', 3.4}));
    insertLast(L, alokasi({"Fahmi", "06", 'L', 3.45}));
    insertLast(L, alokasi({"Gita", "07", 'P', 3.75}));
    insertLast(L, alokasi({"Hilmi", "08", 'L', 3.3}));

    printInfo(L);

    return 0;
}
```
#### Output:
<img width="352" height="520" alt="image" src="https://github.com/user-attachments/assets/628ee50a-dbd1-4ef0-bf8e-0c9473e029e8" />


Kode ini menunjukkan cara menambahkan data mahasiswa ke dalam single linked list lalu menampilkannya dari awal sampai akhir.

#### Full code Screenshot:


multilist.h
<img width="309" height="410" alt="image" src="https://github.com/user-attachments/assets/7977ac2d-9a6b-4f11-b728-f60ba838987d" />

multilist.cpp
<img width="495" height="604" alt="image" src="https://github.com/user-attachments/assets/fa2ef0a8-491e-4de8-8631-9a7fc82ca82c" />

main.cpp
<img width="444" height="447" alt="image" src="https://github.com/user-attachments/assets/c0fb9ff8-0316-4afa-b09e-947a66590fe9" />


## Kesimpulan
Praktikum ini memahami cara kerja Multi Linked List dan cara memasukkan data ke dalam sebuah linked list, khususnya bagaimana menambah data di awal, akhir, dan setelah elemen tertentu serta menampilkannya kembali secara berurutan.

## Referensi
Syahputra, F., Sabrina, E., Ilham, M., Saputra, R. A., & Sitepu, Z. B. (2025). Penerapan Ai Di Platform Linkedin Learning Untuk Meningkatkan Keterampilan Profesional Mahasiswa: Penelitian. Jurnal Pengabdian Masyarakat dan Riset Pendidikan, 3(3), 327-332.
