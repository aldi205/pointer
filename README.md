
import java.util.Scanner;

// Superclass
class Pembayaran {
    public void proses(double total) {
        System.out.println("Memproses pembayaran sebesar Rp" + total);
    }
}

// Subclass: Tunai
class Tunai extends Pembayaran {
    @Override
    public void proses(double total) {
        Scanner sc = new Scanner(System.in);
        System.out.println("\n=== Pembayaran Tunai ===");
        System.out.print("Masukkan uang yang dibayarkan: Rp");
        double uangDiberikan = sc.nextDouble();

        if (uangDiberikan < total) {
            System.out.println("Uang tidak cukup! Transaksi dibatalkan.");
            return;
        }

        double kembalian = uangDiberikan - total;
        System.out.println("Total Belanja : Rp" + total);
        System.out.println("Uang Diberikan: Rp" + uangDiberikan);
        System.out.println("Kembalian     : Rp" + kembalian);
        System.out.println("Transaksi berhasil!");
    }
}

// Subclass: Kartu
class Kartu extends Pembayaran {
    @Override
    public void proses(double total) {
        double biayaAdmin = total * 0.02; // 2% biaya admin
        double totalBayar = total + biayaAdmin;
        System.out.println("\n=== Pembayaran Kartu ===");
        System.out.println("Total Belanja  : Rp" + total);
        System.out.println("Biaya Admin (2%): Rp" + biayaAdmin);
        System.out.println("Total yang Dikenakan: Rp" + totalBayar);
        System.out.println("Pembayaran dengan kartu berhasil!");
    }
}

// Subclass: DompetDigital
class DompetDigital extends Pembayaran {
    @Override
    public void proses(double total) {
        double potongan = total * 0.05; // potongan 5%
        double totalBayar = total - potongan;
        System.out.println("\n=== Pembayaran Dompet Digital ===");
        System.out.println("Total Belanja  : Rp" + total);
        System.out.println("Potongan (5%)  : Rp" + potongan);
        System.out.println("Total Bayar    : Rp" + totalBayar);
        System.out.println("Pembayaran dengan dompet digital berhasil!");
    }
}

// Tester
public class TesterPembayaran {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        double totalBelanja;

        System.out.println("=== PROGRAM PEMBAYARAN POLYMORPHISM ===");
        System.out.print("Masukkan total belanja Anda: Rp");
        totalBelanja = input.nextDouble();

        Pembayaran[] daftarPembayaran = new Pembayaran[3];
        daftarPembayaran[0] = new Tunai();
        daftarPembayaran[1] = new Kartu();
        daftarPembayaran[2] = new DompetDigital();

        int pilihan;
        do {
            System.out.println("\nPilih metode pembayaran:");
            System.out.println("1. Tunai");
            System.out.println("2. Kartu");
            System.out.println("3. Dompet Digital");
            System.out.println("4. Keluar");
            System.out.print("Masukkan pilihan: ");
            pilihan = input.nextInt();

            switch (pilihan) {
                case 1:
                    daftarPembayaran[0].proses(totalBelanja);
                    break;
                case 2:
                    daftarPembayaran[1].proses(totalBelanja);
                    break;
                case 3:
                    daftarPembayaran[2].proses(totalBelanja);
                    break;
                case 4:
                    System.out.println("\nTerima kasih sudah menggunakan sistem pembayaran!");
                    break;
                default:
                    System.out.println("Pilihan tidak valid!");
            }
        } while (pilihan != 4);
    }
}

