# Test 6 Bahasa Indonesia Full Form single sample

# Dapatkan Nama/Kode Sampel, Tanggal dan Nama Cupper
sample_name = input("Masukkan Nama/Kode Sampel: ")
date = input("Masukkan Tanggal (dalam format DD-MM-YYYY): ")
cupper_name = input("Masukkan Nama Cupper: ")

# Daftar atribut cupping
attributes = ["Fragrance/Aroma", "Flavor", "Aftertaste", "Acidity", "Body", "Balance", "Overall"]
cup_attributes = ["Uniformity", "Sweetness", "Clean Cup"]

# Kamus nilai dan deskripsi untuk menyimpan masukan pengguna
scores = {}
descriptions = {}

# Dapatkan masukan pengguna untuk tujuh atribut pertama
for attribute in attributes:
    while True:
        try:
            score = float(input(f"Masukkan nilai Anda (0-10, dalam kenaikan 0.25) untuk {attribute}: "))
            if 0 <= score <= 10 and (score * 4) % 1 == 0:  # Pastikan nilai dalam kenaikan 0.25
                scores[attribute] = score
                break
            else:
                print("Nilai tidak valid. Harap masukkan angka antara 0 dan 10 dalam kenaikan 0.25.")
        except ValueError:
            print("Input tidak valid. Harap masukkan angka.")
    description = input(f"Masukkan evaluasi deskriptif untuk {attribute} (atau tekan enter untuk meninggalkannya kosong): ")
    descriptions[attribute] = description

# Dapatkan masukan pengguna untuk Uniformity, Sweetness, dan Clean Cup
defect_cups = []
for attribute in cup_attributes:
    total = 10  # Mulai dari 10 poin
    while True:
        no_cups = input(f"Untuk {attribute}, harap masukkan nomor cangkir (dipisahkan dengan spasi) yang merupakan 'Tidak': ")
        # Pisahkan input menjadi daftar nomor cangkir
        no_cups = no_cups.split()
        # Jika pengguna memasukkan 0 (yaitu, semua cangkir adalah 'Ya')
        if no_cups == ['0']:
            break
        # Periksa apakah semua input adalah nomor cangkir yang valid (1-5)
        elif all(cup.isdigit() and 1 <= int(cup) <= 5 for cup in no_cups):
            total -= len(no_cups) * 2  # Setiap 'Tidak' mengurangi 2 poin
            if attribute == "Clean Cup":
                defect_cups = [int(cup) for cup in no_cups]
            break
        else:
            print("Input tidak valid. Harap masukkan nomor cangkir (1-5) yang dipisahkan dengan spasi, atau 0 jika semua cangkir adalah 'Ya'.")
    scores[attribute] = total

# Periksa cacat dalam kategori "Clean Cup"
defect_intensity = 0
defect_type = None
if defect_cups:
    while True:
        intensity = input(f"Cangkir nomor {defect_cups} memiliki cacat. Bagaimana intensitas rata-rata? (Taint (T)/Fault (F)): ")
        if intensity.lower() == 't':
            defect_intensity = 2 * len(defect_cups)
            defect_type = 'Taint'
            break
        elif intensity.lower() == 'f':
            defect_intensity = 4 * len(defect_cups)
            defect_type = 'Fault'
            break
        else:
            print("Input tidak valid. Harap masukkan 'T' untuk Taint atau 'F' untuk Fault.")

# Hitung nilai total dan nilai akhir setelah memperhitungkan intensitas cacat
total_score = sum(scores.values())
final_score = total_score - defect_intensity

# Cetak nilai dan deskripsi
print("\nBerikut adalah nilai dan deskripsi Anda:")
print() # Spasi Kosong
print(f"Nama/Kode Sampel: {sample_name}")
print(f"Tanggal: {date}")
print(f"Nama Penyaring: {cupper_name}")
print() # Spasi Kosong
for attribute in attributes + cup_attributes:
    print(f"{attribute}: {scores[attribute]}")
    if attribute in descriptions:
        print(f"Deskripsi: {descriptions[attribute]}")
print(f"\nNilai Total: {total_score}")
if defect_cups:
    print(f"Cangkir nomor {defect_cups} memiliki {defect_type}s.")
print() # Spasi kosong
print("*******************************")
print(f"Nilai Akhir (setelah memperhitungkan intensitas cacat): {final_score}")
print("*******************************")
