# UJIAN-AKHIR-SEMESTER-PEMROGRAMAN

## PENJELASAN SINGKAT
Program Python sederhana menggunakan konsep OOP dan modular,
yang terdiri dari class Data, Process, dan View.
Program ini digunakan untuk mengelola data mahasiswa
class data berfungsi untuk menyimpan nama dan nlai mahasiswa
class process berfungsi untuk mengelola data
class view berfungsi untuk input dan output
validasi input menggunakan try-except untuk mencegah kesalahan saat memasukan data
hasil data mahasiswa ditampilkan dalam bentuk tabel agar lebih mudah dibaca

## KODE PROGRAM
#class data
class Mahasiswa:
    def __init__(self, nama, nilai):
        self.nama = nama
        self.nilai = nilai
#class process
class MahasiswaProcess:
    def __init__(self):
        self.data_mahasiswa = []

    def tambah_mahasiswa(self, nama, nilai):
        self.data_mahasiswa.append(Mahasiswa(nama, nilai))

    def get_data(self):
        return self.data_mahasiswa
#classview + validasi
class MahasiswaView:
    def input_mahasiswa(self):
        try:
            nama = input("Masukkan Nama Mahasiswa: ")
            nilai = float(input("Masukkan Nilai Mahasiswa: "))

            if nilai < 0 or nilai > 100:
                raise ValueError("Nilai harus antara 0 - 100")

            return nama, nilai

        except ValueError as e:
            print("Input tidak valid:", e)
            return None, None

    def tampilkan_tabel(self, data):
        print("\n+----+----------------+--------+")
        print("| No | Nama           | Nilai  |")
        print("+----+----------------+--------+")

        for i, mhs in enumerate(data, start=1):
            print(f"| {i:<2} | {mhs.nama:<14} | {mhs.nilai:<6} |")

        print("+----+----------------+--------+")

#program utama
def main():
    process = MahasiswaProcess()
    view = MahasiswaView()

    while True:
        print("\nMenu:")
        print("1. Tambah Data Mahasiswa")
        print("2. Tampilkan Data")
        print("3. Keluar")

        pilihan = input("Pilih menu (1/2/3): ")

        if pilihan == "1":
            nama, nilai = view.input_mahasiswa()
            if nama is not None:
                process.tambah_mahasiswa(nama, nilai)
                print("Data berhasil ditambahkan!")

        elif pilihan == "2":
            data = process.get_data()
            if data:
                view.tampilkan_tabel(data)
            else:
                print("Data masih kosong.")

        elif pilihan == "3":
            print("Program selesai.")
            break

        else:
            print("Pilihan tidak valid.")

if __name__ == "__main__":
                main()



