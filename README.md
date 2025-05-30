<<<<<<< HEAD
# OOTD Planner
=======
package main
import "fmt"

const NMAX int = 10
type item struct{
	nama string
	kategori string
	cuaca string
	acara string
}

type ootd [NMAX]item

func main(){
	var outfit ootd
	var nData int
	var pilih int
	
	selesai := false
	for !selesai{
		fmt.Println("\n--- OOTD Planner ---")
		fmt.Println("1. Tambah Item Fashion")
		fmt.Println("2. Lihat Semua Item")
		fmt.Println("3. Rekomendasi Outfit")
		fmt.Println("4. Urutkan data")
		fmt.Println("5. Hapus Item Fashion")
		fmt.Println("6. Keluar")
		fmt.Print("Pilih menu: ")
		fmt.Scan(&pilih)
		
		if pilih == 1{
			inputData(&outfit, &nData)
		}else if pilih == 2{
			cetakData(outfit, nData)
		}else if pilih == 3{
			rekomendasi(outfit, nData)
		}else if pilih == 4{
			urutAcara(&outfit, nData)
			cetakData(outfit, nData)
		}else if pilih == 5{
			hapusdata(&outfit, &nData)
		} else if pilih == 6 {
			selesai = true
		}
	}
}

func inputData(A *ootd, n *int){
	var tambah int
	fmt.Println("Berapa banyak item yang akan ditambahkan?")
	fmt.Scan(&tambah) 
	for i := 0; i < tambah; i++{
		fmt.Println("Nama item(gunakan _ jika lebih dari 2 kata), Kategori(Atasan/Bawahan/Sepatu), Dan Acara(Formal/Kasual/Pesta): ")
		fmt.Scan(&A[*n].nama, &A[*n].kategori, &A[*n].acara)
		fmt.Println("Input berhasil 😊")
		*n++
	}
	fmt.Printf("Total item sekarang : %d\n", *n)
}

func cetakData(A ootd, n int){
    fmt.Printf("%-20s %-15s %-15s\n", "Nama Item", "Kategori", "Acara")
	for i := 0; i < 36; i++ {
        fmt.Print("-")
    }
	fmt.Println()
    for i := 0; i < n; i++ {
        fmt.Printf("%-20s %-15s %-15s\n", A[i].nama, A[i].kategori, A[i].acara)
    }
}

func urutAcara(A *ootd, n int) {
	if n <= 1 {
		return
	}
	
	for i := 0; i < n-1; i++ {
		for j := 0; j < n-1-i; j++ {
			if A[j].acara > A[j+1].acara {
				A[j], A[j+1] = A[j+1], A[j]
			}
		}
	}
}

func rekomendasi(A ootd, n int) {
	var targetAcara string
	var ditemukan bool = false

	fmt.Print("Masukkan jenis acara (cth: Formal, Kasual, Pesta): ")
	fmt.Scan(&targetAcara)
	
	fmt.Printf("\n--- Rekomendasi untuk Acara '%s' ---\n", targetAcara)
	fmt.Printf("%-20s %-15s %-15s\n", "Nama Item", "Kategori", "Acara")

	for k := 0; k < 51; k++ {
		fmt.Print("-")
	}
	fmt.Println()


	for i := 0; i < n; i++ {
		if A[i].acara == targetAcara {
			fmt.Printf("%-20s %-15s %-15s\n", A[i].nama, A[i].kategori, A[i].acara)
			ditemukan = true
		}
	}

	if !ditemukan {
		fmt.Printf("Tidak ditemukan item yang cocok untuk acara '%s'.\n", targetAcara)
	}
}

func hapusdata (A *ootd, n *int) {
	var target string 
	var found bool = false 
	fmt.Print("Masukkan nama item yang ingin dihapus: ")
	fmt.Scan(&target)
	for i := 0 ; i< *n ; i++ {
		if A[i].nama == target {
			for j:= i ; j<*n -1 ; j++ {
			A[j] = A [j+1]
			}
			*n-- 
			found = true 
		i = *n 
		}
	}
	if found {
	fmt.Printf("Item '%s' berhasil dihapus.\n", target)
	}
}	
>>>>>>> 94ea448063465510bcdcc39f95ef8290b65e809a
