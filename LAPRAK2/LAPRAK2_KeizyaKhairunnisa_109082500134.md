# <h1 align="center">Laporan Praktikum Modul 2 - Pengenalan Bahasa C++ (Bagian Kedua)</h1>
<p align="center"> Keizya Khairunnisa - 109082500134</p>

## Dasar Teori
Array adalah kumpulan data bertipe sama yang disimpan berurutan di memori dan diakses pakai indeks mulai dari 0 [1]. Matriks dibuat dengan array dua dimensi, contohnya int A[3][3], di mana indeks pertama untuk baris dan indeks kedua untuk kolom [2]. Penjumlahan dan pengurangan matriks dilakukan pada elemen yang posisinya sama, sedangkan perkalian butuh tiga perulangan bersarang [2].

Pointer dan Reference

Pointer adalah variabel yang menyimpan alamat memori variabel lain [1]. Reference adalah nama lain dari variabel yang sudah ada, jadi kalau reference diubah, variabel aslinya ikut berubah [1]. Secara default, parameter fungsi di C++ hanya mengirim salinan nilai, jadi agar fungsi bisa mengubah variabel aslinya harus pakai pointer atau reference [2].

Function, Prosedur, dan Switch-Case

Function adalah blok kode yang mengembalikan nilai lewat return, sedangkan prosedur adalah function bertipe void yang tidak mengembalikan nilai [2]. Switch-case dipakai untuk memilih satu dari beberapa pilihan berdasarkan nilai variabel, dan sering dipakai untuk membuat menu program [2].

## Unguided 

### 1. Buatlah program yang dapat melakukan operasi penjumlahan, pengurangan dan perkalian matriks 3x3

source code unguided 1
```C++
#include <iostream>
using namespace std;

void inputMatriks(int m[3][3], string nama) {
    cout << "Masukkan matriks " << nama << ":" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << nama << "[" << i << "][" << j << "] = ";
            cin >> m[i][j];
        }
    }
}

void tampil(int m[3][3]) {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << m[i][j] << "\t";
        }
        cout << endl;
    }
}

int main() {
    int A[3][3], B[3][3], hasil[3][3];

    inputMatriks(A, "A");
    inputMatriks(B, "B");

    // penjumlahan
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            hasil[i][j] = A[i][j] + B[i][j];
    cout << "\nA + B =" << endl;
    tampil(hasil);

    // pengurangan
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            hasil[i][j] = A[i][j] - B[i][j];
    cout << "\nA - B =" << endl;
    tampil(hasil);

    // perkalian
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            hasil[i][j] = 0;
            for (int k = 0; k < 3; k++) {
                hasil[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    cout << "\nA x B =" << endl;
    tampil(hasil);

    return 0;
}
```
### Output Unguided 1 :

![Screenshot Output Unguided](https://github.com/keizyakha/STRUKTUR-DATA-MODUL-2/blob/main/LAPRAK2/Screenshot_Output-soal1.png)


penjelasan unguided 1 

Program ini digunakan untuk melakukan operasi pada dua matriks yang berukuran 3×3. Pengguna terlebih dahulu memasukkan 9 angka untuk matriks A dan 9 angka untuk matriks B. Setelah itu, program menghitung hasil penjumlahan, pengurangan, dan perkalian dari kedua matriks tersebut. Hasil dari setiap perhitungan kemudian disimpan dan ditampilkan dalam bentuk matriks.

### 2. Berdasarkan guided pointer dan reference sebelumnya, buatlah keduanya dapat menukar nilai dari 3 variabel.

source code unguided 2
```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], T[3][3], K[3][3], P[3][3] = {};

    cout << "Isi matriks A (9 angka): ";
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++) cin >> A[i][j];

    cout << "Isi matriks B (9 angka): ";
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++) cin >> B[i][j];

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            T[i][j] = A[i][j] + B[i][j];
            K[i][j] = A[i][j] - B[i][j];
            for (int k = 0; k < 3; k++)
                P[i][j] += A[i][k] * B[k][j];
        }
    }

    cout << "\nPenjumlahan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cout << T[i][j] << "\t";
        cout << endl;
    }
    cout << "\nPengurangan:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cout << K[i][j] << "\t";
        cout << endl;
    }
    cout << "\nPerkalian:\n";
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) cout << P[i][j] << "\t";
        cout << endl;
    }
    return 0;
}
```

### Output Unguided 2 :

![Screenshot Output Unguided](https://github.com/keizyakha/STRUKTUR-DATA-MODUL-2/blob/main/LAPRAK2/Screenshot_Output-soal2.png)


penjelasan unguided 2

Program ini digunakan untuk menukar nilai dari tiga variabel yaitu x, y, dan z. Awalnya program menampilkan nilai awal dari ketiga variabel tersebut. Setelah itu, nilai x, y, dan z ditukar menggunakan pointer. Kemudian nilai tersebut ditukar lagi menggunakan reference. Jadi, dari program ini bisa dilihat perbedaan cara penggunaan pointer dan reference dalam mengubah nilai variabel.

### 3. arrA = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55} Buatlah program yang dapat mencari nilai minimum, maksimum, dan rata-rata dari array tersebut! Gunakan function cariMinimum() untuk mencari nilai minimum dan function cariMaksimum() untuk mencari nilai maksimum, serta gunakan prosedur hitungRataRata() untuk menghitung nilai rata-rata! Buat program menggunakan menu switch-case.

source code unguided 3
```C++
#include <iostream>
using namespace std;

int arrA[10] = {11, 8, 5, 7, 12, 26, 3, 54, 33, 55};

int cariMinimum() {
    int min = arrA[0];
    for (int i = 1; i < 10; i++) {
        if (arrA[i] < min) {
            min = arrA[i];
        }
    }
    return min;
}

int cariMaksimum() {
    int max = arrA[0];
    for (int i = 1; i < 10; i++) {
        if (arrA[i] > max) {
            max = arrA[i];
        }
    }
    return max;
}

void hitungRataRata() {
    int total = 0;
    for (int i = 0; i < 10; i++) {
        total += arrA[i];
    }
    float rata = (float)total / 10;
    cout << "Nilai rata-rata : " << rata << endl;
}

int main() {
    int pilih;

    do {
        cout << "\n--- Menu Program Array ---" << endl;
        cout << "1. Tampilkan isi array" << endl;
        cout << "2. Cari nilai maksimum" << endl;
        cout << "3. Cari nilai minimum" << endl;
        cout << "4. Hitung nilai rata - rata" << endl;
        cout << "0. Keluar" << endl;
        cout << "Pilih menu : ";
        cin >> pilih;

        switch (pilih) {
            case 1:
                cout << "Isi array : ";
                for (int i = 0; i < 10; i++) {
                    cout << arrA[i] << " ";
                }
                cout << endl;
                break;
            case 2:
                cout << "Nilai maksimum : " << cariMaksimum() << endl;
                break;
            case 3:
                cout << "Nilai minimum : " << cariMinimum() << endl;
                break;
            case 4:
                hitungRataRata();
                break;
            case 0:
                cout << "Program selesai." << endl;
                break;
            default:
                cout << "Pilihan tidak ada!" << endl;
        }
    } while (pilih != 0);

    return 0;
}
```

### Output Unguided 3 :

![Screenshot Output Unguided](https://github.com/keizyakha/STRUKTUR-DATA-MODUL-2/blob/main/LAPRAK2/Screenshot_Output-soal3.png)

penjelasan unguided 3

Program ini digunakan untuk mengolah isi array yang terdiri dari 10 angka. Di dalam program terdapat beberapa pilihan menu, seperti melihat isi array, mencari nilai paling besar, mencari nilai paling kecil, dan menghitung rata-rata. Untuk mencari nilai terbesar dan terkecil, program akan membandingkan angka satu per satu. Sedangkan untuk mencari rata-rata, semua angka dijumlahkan lalu dibagi dengan jumlah data yang ada.

## Kesimpulan
Kesimpulannya, dari beberapa program yang dibuat, saya menjadi lebih paham cara menggunakan array, pointer, reference, dan matriks di C++. Saya juga belajar cara mengolah data seperti mencari nilai terbesar dan terkecil, menghitung rata-rata, menukar nilai, serta menghitung operasi pada matriks.

## Referensi
[1] B. Stroustrup, The C++ Programming Language, 4th ed. Upper Saddle River, NJ, USA: Addison-Wesley, 2013.

[2] P. Deitel and H. Deitel, C++ How to Program, 10th ed. Boston, MA, USA: Pearson, 2017.
