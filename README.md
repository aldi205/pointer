#include <iostream>
#include <string>
using namespace std;

// Struct untuk menyimpan data KTP
struct KTP {
    string nik;
    string nama;
    string jenisKelamin;
    string alamat;
    string tanggalLahir;
    string agama;
    string pekerjaan;
    string statusKawin;
    string kewarganegaraan;
    string noHP;
};

// Class untuk mengatur input dan output data
class OperasiKTP {
private:
    KTP data[100];
    int jumlah;
public:
    OperasiKTP() {
        jumlah = 0;
    }

    void inputData() {
        cout << "Masukkan jumlah data KTP: ";
        cin >> jumlah;
        cin.ignore(); // membersihkan buffer

        for (int i = 0; i < jumlah; i++) {
            cout << "\n=== Input Data ke-" << i + 1 << " ===\n";
            cout << "NIK              : "; getline(cin, data[i].nik);
            cout << "Nama             : "; getline(cin, data[i].nama);
            cout << "Jenis Kelamin    : "; getline(cin, data[i].jenisKelamin);
            cout << "Alamat           : "; getline(cin, data[i].alamat);
            cout << "Tanggal Lahir    : "; getline(cin, data[i].tanggalLahir);
            cout << "Agama            : "; getline(cin, data[i].agama);
            cout << "Pekerjaan        : "; getline(cin, data[i].pekerjaan);
            cout << "Status Kawin     : "; getline(cin, data[i].statusKawin);
            cout << "Kewarganegaraan  : "; getline(cin, data[i].kewarganegaraan);
            cout << "No. HP           : "; getline(cin, data[i].noHP);
        }
    }

    void tampilkanData() {
        cout << "\n\n=== DATA KTP KELOMPOK ===\n";
        for (int i = 0; i < jumlah; i++) {
            cout << "\nData ke-" << i + 1 << endl;
            cout << "NIK              : " << data[i].nik << endl;
            cout << "Nama             : " << data[i].nama << endl;
            cout << "Jenis Kelamin    : " << data[i].jenisKelamin << endl;
            cout << "Alamat           : " << data[i].alamat << endl;
            cout << "Tanggal Lahir    : " << data[i].tanggalLahir << endl;
            cout << "Agama            : " << data[i].agama << endl;
            cout << "Pekerjaan        : " << data[i].pekerjaan << endl;
            cout << "Status Kawin     : " << data[i].statusKawin << endl;
            cout << "Kewarganegaraan  : " << data[i].kewarganegaraan << endl;
            cout << "No. HP           : " << data[i].noHP << endl;
        }
    }
};

// Fungsi utama
int main() {
    OperasiKTP ktpApp;

    ktpApp.inputData();
    ktpApp.tampilkanData();

    return 0;
}

