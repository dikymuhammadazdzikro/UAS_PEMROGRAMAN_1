# Project UAS – Manajemen Nilai Mahasiswa

## Deskripsi
Program ini dibuat menggunakan konsep OOP dan modular untuk mengelola data nilai mahasiswa.

## Struktur File
Program dibagi menjadi beberapa modul untuk memenuhi syarat arsitektur modular:

1. data.py: Berisi Class Data untuk menyimpan struktur list/database.

2. process.py: Berisi Class Process untuk logika validasi dan pengolahan data.

3. view.py: Berisi Class View untuk menangani input user dan tampilan tabel.

4. main.py: File utama untuk menjalankan program

## Demo & Dokumentasi
📽️ Video Presentasi:

## pemerograman Python
# =========================
# MODEL
# =========================
class Mahasiswa:
    def __init__(self, nim, nama, nilai):
        self.nim = nim
        self.nama = nama
        self.nilai = nilai


# =========================
# CONTROLLER / PROCESS
# =========================
class MahasiswaProcess:
    def __init__(self):
        self.data_mahasiswa = []

    def tambah(self, nim, nama, nilai):
        if nilai < 0 or nilai > 100:
            raise ValueError("Nilai harus antara 0 - 100")
        self.data_mahasiswa.append(Mahasiswa(nim, nama, nilai))

    def hapus(self, nim):
        self.data_mahasiswa = [
            m for m in self.data_mahasiswa if m.nim != nim
        ]

    def get_all(self):
        return self.data_mahasiswa


# =========================
# VIEW
# =========================
class MahasiswaView:
    def tampilkan(self, data_mahasiswa):
        if not data_mahasiswa:
            print("Data mahasiswa kosong")
            return

        print("\nDAFTAR NILAI MAHASISWA")
        print("-" * 35)
        for m in data_mahasiswa:
            print(f"NIM   : {m.nim}")
            print(f"Nama  : {m.nama}")
            print(f"Nilai : {m.nilai}")
            print("-" * 35)


# =========================
# PROGRAM UTAMA
# =========================
process = MahasiswaProcess()
view = MahasiswaView()

while True:
    print("\nMENU")
    print("1. Tambah Data")
    print("2. Hapus Data")
    print("3. Tampilkan Data")
    print("4. Keluar")

    try:
        pilihan = int(input("Pilih menu: "))

        if pilihan == 1:
            nim = input("NIM   : ")
            nama = input("Nama  : ")
            nilai = int(input("Nilai : "))
            process.tambah(nim, nama, nilai)
            print("Data berhasil ditambahkan")

        elif pilihan == 2:
            nim = input("Masukkan NIM yang dihapus: ")
            process.hapus(nim)
            print("Data berhasil dihapus")

        elif pilihan == 3:
            view.tampilkan(process.get_all())

        elif pilihan == 4:
            print("Program selesai")
            break

        else:
            print("Menu tidak valid")

    except ValueError as e:
        print("Error:", e)


## penjelasan pemerograman
1.Class Data (data.py)
Bagian ini bertanggung jawab penuh atas struktur data program.

Tujuan: Menentukan bagaimana data mahasiswa (Nama, NIM, Kelas) disimpan dalam sebuah objek.

Fungsi: Memisahkan penyimpanan data dari logika lainnya agar struktur data bersifat mandiri dan mudah dikelola.

2.Class Process (process.py)
Bagian ini berisi logika bisnis dan aturan jalannya program.

Tujuan: Mengolah data yang masuk dan melakukan validasi.

Validasi (Exception Handling): Menggunakan blok try-except untuk memastikan input pengguna tidak kosong dan sesuai format sebelum disimpan ke dalam sistem.

3.Class View (view.py)
Bagian ini berinteraksi langsung dengan pengguna.

Input: Meminta input dari pengguna secara interaktif (Nama, NIM, Kelas).

Output: Menampilkan data yang telah tersimpan dalam bentuk tabel yang rapi agar mudah dibaca oleh pengguna.

4.Main Program (main.py)
Ini adalah pengontrol utama atau entry point dari aplikasi.

Tujuan: Menghubungkan ketiga komponen (Data, View, dan Process) menjadi satu alur kerja.

Fungsi: Menjalankan perulangan menu (looping) sehingga pengguna dapat terus menambah atau melihat data sampai memilih untuk keluar.

## Output pemerograman python
<img width="290" height="179" alt="image" src="https://github.com/user-attachments/assets/122a5fcc-0f0d-4bfc-a07c-a06fb06f29b8" />

<img width="228" height="317" alt="image" src="https://github.com/user-attachments/assets/5bf67b17-3a02-41a7-8dbd-ae59b4fb44d1" />

<img width="275" height="305" alt="image" src="https://github.com/user-attachments/assets/ed53b1e9-557f-477a-8a82-6bac174a03bf" />
