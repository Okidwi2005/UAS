# UAS
## Deskripsi
Buatlah program sederhana dengan ketentuan:
- Program harus dibuat dengan konsep modular dan OOP (pisahkan
class data, class view, dan class process)
- Program harus meminta input dari pengguna
- Tambahkan validasi input (dapat menggunakan konsep eksepsi)
- Program menapilkan hasil (dapat berupa table view)

## kode python
```python
class Data:
    def __init__(self, nama, umur, alamat):
        self.nama = nama
        self.umur = umur
        self.alamat = alamat

from tabulate import tabulate

class View:
    def __init__(self):
        pass

    def tampilkan_data(self, data):
        header = ["Nama", "Umur", "Alamat"]
        tabel = [[d.nama, d.umur, d.alamat] for d in data]
        print(tabulate(tabel, header, tablefmt="grid"))

    def input_data(self):
        nama = input("Masukkan nama: ")
        while True:
            try:
                umur = int(input("Masukkan umur: "))
                if umur < 0:
                    print("Umur tidak boleh negatif.")
                else:
                    break
            except ValueError:
                print("Umur harus berupa angka.")
        alamat = input("Masukkan alamat: ")
        return nama, umur, alamat

    def pesan_error(self, pesan):
        print(f"Error: {pesan}")

class Process:
    def __init__(self):
        self.data = []

    def tambah_data(self, nama, umur, alamat):
        self.data.append(Data(nama, umur, alamat))


def main():
    proses = Process()
    tampilan = View()

    while True:
        print("\n1. Tambah Data")
        print("2. Tampilkan Data")
        print("3. Keluar")
        pilihan = input("Pilih menu: ")

        if pilihan == "1":
            nama, umur, alamat = tampilan.input_data()
            proses.tambah_data(nama, umur, alamat)
        elif pilihan == "2":
            if proses.data:
                tampilan.tampilkan_data(proses.data)
            else:
                tampilan.pesan_error("Data kosong.")
        elif pilihan == "3":
            break
        else:
            tampilan.pesan_error("Pilihan tidak valid.")

if __name__ == "__main__":
    main()
```

## Penjelasan Program
Struktur Program
1. Class Data: Berisi atribut dan metode untuk mengelola data individu.
2. Class View: Menangani interaksi pengguna, seperti input dan tampilan data.
3. Class Process: Mengelola proses penyimpanan dan pengolahan data.
4. Fungsi main(): Mengatur jalur program utama.
Class Data
- __init__: Inisialisasi objek Data dengan atribut nama, umur, dan alamat.
Class View
- tampilkan_data: Menampilkan data dalam format tabel menggunakan library tabulate.
- input_data: Mengambil input pengguna untuk nama, umur, dan alamat dengan validasi umur.
- pesan_error: Menampilkan pesan kesalahan.
Class Process
- __init__: Inisialisasi objek Process dengan atribut data sebagai list.
- tambah_data: Menambahkan objek Data ke list data.
Fungsi main()
1. Membuat objek Process dan View.
2. Menampilkan menu utama.
3. Mengatur jalur program berdasarkan pilihan pengguna:
- Tambah Data: Mengambil input dan menambahkan data.
- Tampilkan Data: Menampilkan data jika ada.
- Keluar: Mengakhiri program.
Fitur
1. Validasi umur: Memastikan umur tidak negatif dan berupa angka.
2. Tampilan tabel: Menampilkan data dalam format tabel.
3. Pesan kesalahan: Menampilkan pesan jika data kosong atau pilihan tidak valid.
Kelebihan
1. Struktur modular: Membuat kode lebih terorganisir dan mudah dipelihara.
2. OOP: Meningkatkan reusabilitas kode dan kemudahan pengembangan.
3. Validasi data: Mencegah input tidak valid.
4. Tampilan tabel: Membuat data lebih mudah dibaca.
