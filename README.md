#include <iostream>
using namespace std;

void tambah(int* a, int* b, int* hasil) {
    *hasil = *a + *b;
}

void kurang(int* a, int* b, int* hasil) {
    *hasil = *a - *b;
}

void kali(int* a, int* b, int* hasil) {
    *hasil = (*a) * (*b);
}

void bagi(int* a, int* b, float* hasil) {
    if (*b != 0) {
        *hasil = static_cast<float>(*a) / (*b);
    } else {
        *hasil = 0;
        cout << "Pembagian dengan nol tidak diperbolehkan!" << endl;
    }
}

void cekGanjilGenap(int* bil) {
    if (*bil % 2 == 0)
        cout << *bil << " adalah bilangan genap." << endl;
    else
        cout << *bil << " adalah bilangan ganjil." << endl;
}

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

    cout << "Masukkan bilangan pertama: ";
    cin >> x;
    cout << "Masukkan bilangan kedua: ";
    cin >> y;

    cout << "\n=== Cek Ganjil atau Genap ===" << endl;
    cekGanjilGenap(&x);
    cekGanjilGenap(&y);

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
