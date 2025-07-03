#include <iostream>
using namespace std;

// Fungsi pertambahan
void tambah(int* a, int* b, int* hasil) {
    *hasil = *a + *b;
}

// Fungsi pengurangan
void kurang(int* a, int* b, int* hasil) {
    *hasil = *a - *b;
}

// Fungsi perkalian
void kali(int* a, int* b, int* hasil) {
    *hasil = (*a) * (*b);
}

// Fungsi pembagian
void bagi(int* a, int* b, float* hasil) {
    if (*b != 0) {
        *hasil = static_cast<float>(*a) / (*b);
    } else {
        *hasil = 0;
        cout << "Pembagian dengan nol tidak diperbolehkan!" << endl;
    }
}

// Fungsi cek ganjil/genap
void cekGanjilGenap(int* bil) {
    if (*bil % 2 == 0)
        cout << *bil << " adalah bilangan genap." << endl;
    else
        cout << *bil << " adalah bilangan ganjil." << endl;
}

// Fungsi faktorial
void faktorial(int* bil, long long* hasil) {
    *hasil = 1;
    if (*bil < 0) {
        cout << "Faktorial tidak didefinisikan untuk bilangan negatif!" << endl;
        *hasil = 0;
        return;
    }
    for (int i = 1; i <= *bil; i++) {
        *hasil *= i;
    }
}

// Fungsi cek bilangan prima
void cekPrima(int* bil) {
    if (*bil < 2) {
        cout << *bil << " bukan bilangan prima." << endl;
        return;
    }

    bool prima = true;
    for (int i = 2; i <= *bil / 2; i++) {
        if (*bil % i == 0) {
            prima = false;
            break;
        }
    }

    if (prima)
        cout << *bil << " adalah bilangan prima." << endl;
    else
        cout << *bil << " bukan bilangan prima." << endl;
}

int main() {
    int x, y;
    int hasilInt;
    float hasilFloat;
    long long faktorialX, faktorialY;

    // Input
    cout << "Masukkan bilangan pertama: ";
    cin >> x;
    cout << "Masukkan bilangan kedua: ";
    cin >> y;

    // Cek ganjil/genap
    cout << "\n=== Cek Ganjil atau Genap ===" << endl;
    cekGanjilGenap(&x);
    cekGanjilGenap(&y);

    // Cek prima
    cout << "\n=== Cek Bilangan Prima ===" << endl;
    cekPrima(&x);
    cekPrima(&y);

    // Faktorial
    cout << "\n=== Hasil Faktorial ===" << endl;
    faktorial(&x, &faktorialX);
    faktorial(&y, &faktorialY);
    if (faktorialX != 0)
        cout << "Faktorial dari " << x << " = " << faktorialX << endl;
    if (faktorialY != 0)
        cout << "Faktorial dari " << y << " = " << faktorialY << endl;

    // Aritmatika
    cout << "\n=== Hasil Operasi Aritmatika ===" << endl;
    tambah(&x, &y, &hasilInt);
    cout << "Hasil Pertambahan: " << hasilInt << endl;

    kurang(&x, &y, &hasilInt);
    cout << "Hasil Pengurangan: " << hasilInt << endl;

    kali(&x, &y, &hasilInt);
    cout << "Hasil Perkalian: " << hasilInt << endl;

    bagi(&x, &y, &hasilFloat);
    cout << "Hasil Pembagian: " << hasilFloat << endl;

    return 0;
}
