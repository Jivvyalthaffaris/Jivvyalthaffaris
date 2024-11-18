# Daftar menu dan harga
menu = {
    1: {"nama": "Nasi Goreng", "harga": 25000},
    2: {"nama": "Mie Goreng", "harga": 20000},
    3: {"nama": "Ayam Bakar", "harga": 30000},
    4: {"nama": "Sate Ayam", "harga": 35000},
    5: {"nama": "Es Teh Manis", "harga": 5000},
    6: {"nama": "Jus Jeruk", "harga": 15000}
}

# Fungsi untuk menampilkan menu
def tampilkan_menu():
    print("\nMenu Makanan & Minuman:")
    for key, item in menu.items():
        print(f"{key}. {item['nama']} - Rp {item['harga']}")

# Fungsi untuk memproses pemesanan
def pesan_makanan():
    total_biaya = 0
    while True:
        tampilkan_menu()
        try:
            pilihan = int(input("\nPilih menu (nomor) yang ingin dipesan (0 untuk selesai): "))
            if pilihan == 0:
                break
            elif pilihan in menu:
                jumlah = int(input(f"Berapa banyak {menu[pilihan]['nama']} yang ingin dipesan? "))
                total_biaya += menu[pilihan]["harga"] * jumlah
                print(f"{jumlah} {menu[pilihan]['nama']} ditambahkan ke pesanan.")
            else:
                print("Pilihan tidak tersedia. Coba lagi.")
        except ValueError:
            print("Masukkan pilihan yang valid.")
    
    return total_biaya

# Fungsi untuk menghitung dan menampilkan total
def checkout(total_biaya):
    print(f"\nTotal biaya yang harus dibayar: Rp {total_biaya}")
    if total_biaya > 0:
        pembayaran = int(input("Masukkan jumlah pembayaran: Rp "))
        if pembayaran >= total_biaya:
            kembalian = pembayaran - total_biaya
            print(f"Pembayaran berhasil. Kembalian: Rp {kembalian}")
        else:
            print("Pembayaran tidak cukup. Coba lagi.")
    else:
        print("Tidak ada pesanan yang dipilih.")

# Main program
def main():
    print("Selamat datang di Restaurant Takeaway!")
    total_biaya = pesan_makanan()
    checkout(total_biaya)

if __name__ == "__main__":
    main()
