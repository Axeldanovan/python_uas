# python_uas

# hasil praktikum UAS Mata Kuliah Pemrograman - Python
## Dengan Struktur Seperti:
- daftar_nilai.py berisi modul untuk tambah data, ubah data, cari data, hapus data
- cetak_nilai.py berisi modul untuk cetak daftar nilai, cetak hasil pencarian
- input_nilai.py berisi modul untuk input data yang diminta pengguna untuk memasukkan data
- main.py berisi program secara keseluruhan

# Struktur Program

![UAS_1](https://user-images.githubusercontent.com/81457697/148918800-1866d043-87e4-4ebf-8a28-147b4792dd19.png)

- input untuk daftar_nilai.py
```python
from view.input_nilai import *

dataMahasiswa = {}


def tambah_data():
    global dataMahasiswa
    nama = input_nama()
    nim = input_nim()
    nilaiTugas = input_nilaiTugas()
    nilaiUts = input_nilaiUts()
    nilaiUas = input_nilaiUas()
    nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
    dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
    print("\nData Berhasil Ditambahkan!")
    return dataMahasiswa

def ubah_data():
    nama = input("Masukkan Nama: ")
    if nama in dataMahasiswa.keys():
        nim = input_nim()
        nilaitugas = input_nilaiTugas()
        nilaiUts = input_nilaiUts()
        nilaiUas = input_nilaiUas()
        nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Di Update!")
    else:
        print("Data tidak ditemukan!")


def hapus_data():
    nama = input("Masukkan Nama:  ")
    if nama in dataMahasiswa.keys():
        del dataMahasiswa[nama]
        print("Data",nama, "Telah dihapus!")
    else:
        print("Data Mahasiswa Tidak Ada".format(nama))
```

- input untuk cetak_nilai.py
```python
from model.daftar_nilai import *


def cetak_daftar_nilai():
    if dataMahasiswa.items():
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        i = 0
        for x in dataMahasiswa.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2], x[1][3], x[1][4], i))
        print("==================================================================")
    else:
        print("\n                      DAFTAR NILAI MAHASISWA                    ")
        print("==================================================================")
        print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
        print("==================================================================")
        print("|                          TIDAK ADA DATA!                       |")
        print("==================================================================")


def cetak_hasil_pencarian():
    nama = input("Masukkan Nama        : ")
    if nama in dataMahasiswa.keys():
        print("\n                   DAFTAR NILAI MAHASISWA                   ")
        print("==============================================================")
        print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
        print("==============================================================")
        print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMahasiswa[nama][0], dataMahasiswa[nama][1], dataMahasiswa[nama][2], dataMahasiswa[nama][3], dataMahasiswa[nama][4]))
        print("==============================================================")
    else:
        print("Datanya {0} Tidak Ada ".format(nama))
```
- code untuk input_nilai.py
```python
def input_nama():
    global nama
    nama = input("Masukkan Nama        : ")
    return nama


def input_nim():
    global nim
    nim = input("Masukkan NIM         : ")
    return nim


def input_nilaiTugas():
    global nilaiTugas
    nilaiTugas = int(input("Masukkan Nilai Tugas : "))
    return nilaiTugas


def input_nilaiUts():
    global nilaiUts
    nilaiUts = int(input("Masukkan Nilai UTS   : "))
    return nilaiUts


def input_nilaiUas():
    global nilaiUas
    nilaiUas = int(input("Masukkan Nilai UAS   : "))
    return nilaiUas
```

- input untuk main.py
```python
from view.cetak_nilai import *

while True:
    c = input("\nT)ambah, U)bah, C)ari, H)apus, L)ihat, K)eluar: ")

    if c.lower() == 't':
        tambah_data()

    elif c.lower() == 'u':
        ubah_data()

    elif c.lower() == 'c':
        cetak_hasil_pencarian()

    elif c.lower() == 'h':
        hapus_data()

    elif c.lower() == 'l':
        cetak_daftar_nilai()

    elif c.lower() == 'k':
        break

    else:
        print("Menu yang anda maksud tidak tersedia, Silahkan pilih menu yang tersedia")
```

- output untuk program menambah data dengan input t di keyboard
 
 ![UAS_2](https://user-images.githubusercontent.com/81457697/148923242-faa7f613-dda3-4a62-9cd2-419c1b7d47d6.png)
 
- output untuk mencari data dengan input c di keyboard
 
![UAS_3](https://user-images.githubusercontent.com/81457697/148923466-6b69e8f3-7a8a-4183-a6ec-9820f1c03740.png)

- output untuk menambah data yang kedua dengan input t atau input yang sama yang pertama digunakan
 
![UAS_4](https://user-images.githubusercontent.com/81457697/148928601-484ef81e-0eeb-4e25-92b0-d33126a7a26b.png)

- output untuk melihat program apa saja yang sudah ditambahkan dengan input L di keyboard
 
 ![UAS_5](https://user-images.githubusercontent.com/81457697/148928840-931df52a-4a6e-4411-93f2-878e92ef6ce2.png)
 
- output untuk menghapus program yang ingin dihilangkan dengan input h di keyboard
 
 ![UAS_6](https://user-images.githubusercontent.com/81457697/148929045-6d523a4b-1078-4c8c-bb47-18b53dfabda8.png)
 
 - output untuk melihat apakah data yang dihapus sudah hilang atau masih tertera dengan input L di keyboard
 
 ![UAS_7](https://user-images.githubusercontent.com/81457697/148929230-8fef3ca0-67a9-4143-b773-f9924c0138c6.png)

- output untuk keluar dari program
  
 ![UAS_8](https://user-images.githubusercontent.com/81457697/148929418-de025e18-525f-418d-bd8f-eaab7e16fa61.png)



