# <h1 align="center">STACK</h1>
<p align="center">IKLIL BAHY SABAIKI</p>

## Dasar Teori

Stack adalah struktur data yang bekerja seperti tumpukan. Elemen yang terakhir dimasukkan akan menjadi elemen pertama yang diambil. Konsep ini disebut LIFO (Last In First Out).
    
## Guided 

### 1. [stack]
**stack.h**
```C++
#ifndef STACK_TABLE
#define STACK_TABLE

#include <iostream>
using namespace std;

//ubah kapasitas sesuai kebutuhan
const int MAX = 10;

struct stackTable{
    int data[MAX];
    int top; // -1 = kosong

};

bool isEmpty(stackTable s);
bool isFull(stackTable s);
void createStack(stackTable &s);

void push(stackTable &s, int angka);
void pop(stackTable &s);
void update(stackTable &s, int posisi);
void view(stackTable s);
void searchData(stackTable s, int data);

#endif
```
**stak.cpp**
```C++
#include "stack.h"
#include <iostream>

using namespace std;

bool isEmpty(stackTable s) {
    return s.top == -1;
}

bool isFull(stackTable s){
    return s.top == MAX -1;
}

void createStack(stackTable &s) {
    s.top = -1;
}

void push(stackTable &s, int angka){
    if(isFull(s)){
        cout << "Stack Penuh!" << endl;
    } else {
        s.top++;
        s.data[s.top] = angka;
        cout << "Data " << angka << " berhasil ditambahkan kedalam stack!" << endl;
    }
}

void pop(stackTable &s){
    if(isEmpty(s)){
        cout << "Stack kosong!" << endl;
    } else {
        int val = s.data[s.top];
        s.top--;
        cout << "Data " << val << " Berhasil dihapus dari stack!" << endl;
    }
}

void update(stackTable &s, int posisi){
    if(isEmpty(s)){
        cout << "Stack kosong!" << endl;
        return;
    }
    if(posisi <= 0){
        cout << "Posisi tidak valid!" << endl;
        return;
    }

    //index = top - (posisi -1)
    int idx = s.top - (posisi -1);
    if(idx < 0 || idx > s.top){
        cout << "Posisi " << posisi << " Tidak valid!" << endl;
        return;
    }

    cout << "Update data posisi ke-" << posisi << endl;
    cout << "Masukkan angka: ";
    cin >> s.data[idx];
    cout << "Data berhasil diupdate!" << endl;
    cout << endl;
}

void view(stackTable s){
    if(isEmpty(s)){
        cout << "Stack Kosong!" << endl;
    } else {
        for(int i = s.top; i >= 0; --i){
            cout << s.data[i] << " ";
        }
    }
    cout << endl;
}

void searchData(stackTable s, int data){
    if(isEmpty(s)){
        cout << "Stack Kosong!" << endl;
        return;
    }
    cout << "Mencari data" << data << "..." << endl;
    int posisi = 1;
    bool found = false;

    for(int i = s.top; i >= 0; --i){
        if(s.data[i] == data){
            cout << "Data " << data << " ditemukan pada posisi ke-" << posisi << endl;
            cout << endl;
            found = true;
            break;
        }
        posisi++;
    }

    if(!found){
        cout << "Data " << data << " tidak ditemukan didalam stack!" << endl;
        cout << endl;
    }
}
```
**main.cpp**
```C++
#include "stack.h"
#include <iostream>

using namespace std;

int main(){
    stackTable s;
    createStack(s);

    push(s, 1);
    push(s, 2);
    push(s, 3);
    push(s, 4);
    push(s, 5);
    cout << endl;

    cout << "--- Stack setelah push ---" << endl;
    view(s);
    cout << endl;

    pop(s);
    pop(s);
    cout << endl;

    cout << "--- Stack setelah pop 2 kali ---" << endl;
    view(s);
    cout << endl;

    //Posisi dihitung dari TOP(1-based)
    update(s, 2);
    update(s, 1);
    update(s, 4);
    cout << endl;

    cout << "--- Stack setelah update ---" << endl;
    view(s);
    cout << endl;

    searchData(s, 4);
    searchData(s, 9);

    return 0;
}
```
Program ini mengimplementasikan struktur data stack menggunakan array dengan operasi dasar push, pop, dan fitur tambahan seperti update dan search data.

## Unguided 

### 1. [Soal]
**stack.h**
```C++
#ifndef STACK_H
#define STACK_H

const int MAX = 20;

struct Stack {
    int data[MAX];
    int top;
};

void createStack(Stack &S);
void push(Stack &S, int x);
int pop(Stack &S);
void printInfo(Stack S);
void balikStack(Stack &S);
void getInputStream(Stack &S);

#endif
```
**stack.cpp**
```C++
#include <iostream>
#include "stack.h"
using namespace std;

void createStack(Stack &S) {
    S.top = -1;
}

void push(Stack &S, int x) {
    if (S.top < MAX - 1) {
        S.top++;
        S.data[S.top] = x;
    }
}

int pop(Stack &S) {
    if (S.top >= 0) {
        int value = S.data[S.top];
        S.top--;
        return value;
    }
    return -1;
}

void printInfo(Stack S) {
    cout << "[TOP] ";
    for (int i = S.top; i >= 0; i--) {
        cout << S.data[i] << " ";
    }
    cout << endl;
}

void balikStack(Stack &S) {
    Stack temp;
    createStack(temp);

    while (S.top >= 0) {
        push(temp, pop(S));
    }

    S = temp;
}

void getInputStream(Stack &S) {
    string input = "4729601"; 
    cout << input << endl;

    for (char ch : input) {
        push(S, ch - '0');
    }
}
```
**main.cpp**
```C++
#include <iostream>
#include "stack.h"
using namespace std;

int main() {
    cout << "Hello Word" << endl;  

    Stack S;
    createStack(S);

    getInputStream(S);  
    printInfo(S);

    cout << "balik stack" << endl;
    balikStack(S);
    printInfo(S);

    return 0;
}
```
#### Output:
<img width="273" height="74" alt="image" src="https://github.com/user-attachments/assets/dcb23936-cb65-41b0-95c5-ee9a9ccbe265" />



Program membuat sebuah stack, otomatis mengisi stack dengan angka 4729601, lalu menampilkan isi stack dari atas ke bawah. Setelah itu, program membalik urutan stack menggunakan stack sementara, dan menampilkan hasilnya.

#### Full code Screenshot:


stack.h
<img width="221" height="227" alt="image" src="https://github.com/user-attachments/assets/42d292c1-d692-45ed-9651-b1a54d0ea616" />


stack.cpp
<img width="284" height="595" alt="image" src="https://github.com/user-attachments/assets/c3a606b0-e6f2-4ce4-9500-a1d41ef837a8" />


main.cpp
<img width="197" height="235" alt="image" src="https://github.com/user-attachments/assets/f7fa0fd8-b335-44b3-b890-937001110aaa" />

## Kesimpulan
Cara kerja stack yang memakai prinsip LIFO, yaitu data yang masuk terakhir akan keluar duluan. Saya mencoba operasi dasar seperti push dan pop, lalu membuat fungsi untuk menampilkan isi stack dan membalik urutannya. Hasil percobaan menunjukkan bahwa stack bekerja sesuai logikanya dan proses pembalikan data berhasil. Praktikum ini membantu saya lebih paham cara menggunakan stack dalam program.

## Referensi
Yulyanto, A. (2012). Aplikasi Simulasi Pembelajaran Struktur Data Materi Stack (Doctoral dissertation, Universitas Mercu Buana).
