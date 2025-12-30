# <h1 align="center">Laporan Praktikum Modul SINGLY LINKED LIST (4)</h1>
<p align="center">IKLIL BAHY SABAIKI</>

## Dasar Teori

3. MODUL 4 SINGLY LINKED LIST
## Guided 

### 1. [Nama Topik]

```C++
Type infotype : int
Type address : pointer to ElmList

Type ElmList <
    info : infotype
    next : address
>

Type List : < First : address >

procedure createList(input/output L : List)
function alokasi(x : infotype) → address
procedure dealokasi(input/output P : address)
procedure printInfo(input L : List)
procedure insertFirst(input/output L : List, input P : address)
```
Kode di atas digunakan untuk menampilkan list .
## Unguided 

### 1. [Soal,]

singlylist.h

```C++
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

typedef int infotype;

struct ElmList;
typedef ElmList* address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address First;
};


void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void printInfo(List L);
void insertFirst(List &L, address P);

#endif


```
singlylist.cpp

```C++
#include "Singlylist.h"

void createList(List &L) {
    L.First = nullptr;
}

address alokasi(infotype x) {
    address P = new ElmList;
    P->info = x;
    P->next = nullptr;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = nullptr;
}

void printInfo(List L) {
    address P = L.First;
    while (P != nullptr) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

void insertFirst(List &L, address P) {
    P->next = L.First;
    L.First = P;
}

```

main.cpp

```C++

#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

    P1 = alokasi(2);
    insertFirst(L, P1);

    P2 = alokasi(0);
    insertFirst(L, P2);

    P3 = alokasi(8);
    insertFirst(L, P3);

    P4 = alokasi(12);
    insertFirst(L, P4);

    P5 = alokasi(9);
    insertFirst(L, P5);

    printInfo(L);

    return 0;
}

```


#### Output:
<img width="354" height="68" alt="image" src="https://github.com/user-attachments/assets/18f42277-01fe-4c47-9077-aca70a840684" />

Kode di atas digunakan untuk membuat dan menampilkan isi Singly Linked List berupa data 9, 12, 8, 0, dan 2 menggunakan tiga file program Singlylist.h, Singlylist.cpp, dan main.cpp.

#### Full code Screenshot:


singlylist.h
<img width="334" height="484" alt="image" src="https://github.com/user-attachments/assets/cf7e593e-5ab1-421d-bc20-dc4c9cb75db5" />

singlylist.cpp
<img width="379" height="524" alt="image" src="https://github.com/user-attachments/assets/437e5e73-f975-4e32-9fb2-5104ec534aeb" />

main.cpp
<img width="290" height="508" alt="image" src="https://github.com/user-attachments/assets/5e4259dc-6302-4b61-b364-dd92a5a49113" />


### 2. [SOAL]

singlylist.h

```C++
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

typedef int infotype;

struct ElmList;
typedef ElmList* address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address First;
};

// Deklarasi fungsi/prosedur
void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void insertFirst(List &L, address P);
void deleteFirst(List &L);
void deleteLast(List &L);
void deleteAfter(List &L, address Prec);
void printInfo(List L);
int nbList(List L);
void deleteList(List &L);

#endif


```

singlylist.cpp

```C++

#include "Singlylist.h"

void createList(List &L) {
    L.First = nullptr;
}

address alokasi(infotype x) {
    address P = new ElmList;
    P->info = x;
    P->next = nullptr;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = nullptr;
}

void insertFirst(List &L, address P) {
    P->next = L.First;
    L.First = P;
}

void deleteFirst(List &L) {
    if (L.First != nullptr) {
        address P = L.First;
        L.First = P->next;
        dealokasi(P);
    }
}

void deleteLast(List &L) {
    if (L.First != nullptr) {
        if (L.First->next == nullptr) {
            deleteFirst(L);
        } else {
            address Q = L.First;
            address P = nullptr;
            while (Q->next != nullptr) {
                P = Q;
                Q = Q->next;
            }
            P->next = nullptr;
            dealokasi(Q);
        }
    }
}

void deleteAfter(List &L, address Prec) {
    if (Prec != nullptr && Prec->next != nullptr) {
        address P = Prec->next;
        Prec->next = P->next;
        dealokasi(P);
    }
}

void printInfo(List L) {
    address P = L.First;
    while (P != nullptr) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

int nbList(List L) {
    int count = 0;
    address P = L.First;
    while (P != nullptr) {
        count++;
        P = P->next;
    }
    return count;
}

void deleteList(List &L) {
    while (L.First != nullptr) {
        deleteFirst(L);
    }
}

```

main.cpp

```C++
#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

    // Membuat list dari soal pertama
    P1 = alokasi(2);
    insertFirst(L, P1);
    P2 = alokasi(0);
    insertFirst(L, P2);
    P3 = alokasi(8);
    insertFirst(L, P3);
    P4 = alokasi(12);
    insertFirst(L, P4);
    P5 = alokasi(9);
    insertFirst(L, P5);

    cout << "Isi List awal: ";
    printInfo(L);

    // Penghapusan node sesuai soal
    cout << endl << "Hapus node 9 (deleteFirst)" << endl;
    deleteFirst(L);
    printInfo(L);

    cout << "Hapus node 2 (deleteLast)" << endl;
    deleteLast(L);
    printInfo(L);

    cout << "Hapus node 8 (deleteAfter)" << endl;
    deleteAfter(L, L.First); // setelah 12
    printInfo(L);

    cout << endl << "Jumlah node : " << nbList(L) << endl;

    cout << endl << "- List Berhasil Terhapus -" << endl;
    deleteList(L);
    cout << "Jumlah node : " << nbList(L) << endl;

    return 0;
}
```

### Output
<img width="267" height="188" alt="image" src="https://github.com/user-attachments/assets/8b134956-3b45-4529-8277-fd65e111ff9f" />

### Fullscreenshot


singlylist.h

<img width="380" height="554" alt="image" src="https://github.com/user-attachments/assets/00ecdbb0-7dfa-423f-b638-450ce6485801" />

singlylist.cpp

<img width="307" height="920" alt="image" src="https://github.com/user-attachments/assets/0c12a097-f02d-4931-8b5b-3c3e46142be9" />

main.cpp

<img width="529" height="736" alt="image" src="https://github.com/user-attachments/assets/fe17ef6f-7a02-4e99-b3ef-6d6cceb3bd43" />

kode ini menampilkan proses penghapusan node pada singly linked list hingga tersisa data 12 dan 0, lalu menghapus seluruh node tinggal 0

## Kesimpulan
Kedua kode tersebut menunjukkan cara membuat, menampilkan, dan menghapus data pada Singly Linked List. Soal pertama menampilkan proses pembentukan list dengan data 9 12 8 0 2, 
sedangkan soal kedua menampilkan proses penghapusan hingga list kosong dengan jumlah node 0.
## Referensi
Penggunaan Algoritma Doubly Linked List Untuk Insertion Dan Deletion — oleh Agung Wijoyo et al., Universitas Pamulang.






