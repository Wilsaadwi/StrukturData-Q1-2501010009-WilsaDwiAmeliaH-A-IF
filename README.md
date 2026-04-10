# 1. Karakteristik Memori dan Akses Data

Array bisa melakukan akses elemen dalam waktu O(1) karena datanya disimpan secara kontinu (berurutan di memori). Jadi kalau mau ambil data di indeks tertentu, alamat memorinya bisa langsung dihitung tanpa harus mencari satu per satu.

Sedangkan pada Singly Linked List, data disimpan secara tidak berurutan (non-kontinu). Setiap node hanya menyimpan data dan pointer ke node berikutnya. Jadi untuk mengakses elemen tertentu, harus ditelusuri dari awal (head) sampai ke posisi yang diinginkan. Proses ini membuat waktu akses menjadi O(n).

# 2. 

Linked List lebih unggul dibanding Array ketika sering melakukan penyisipan (insertion) dan penghapusan (deletion), terutama di bagian tengah atau awal.

Secara teoritis, perbedaannya ada pada cara penyimpanan dan manipulasi datanya:

* Pada Array, elemen disimpan secara berurutan, sehingga ketika ada insertion atau deletion di tengah, elemen lain harus digeser (shifting) untuk menjaga urutan. Proses ini menyebabkan kompleksitas waktu menjadi O(n).

* Pada Linked List, data tidak disimpan berurutan, melainkan dihubungkan dengan pointer. Saat melakukan insertion atau deletion, cukup mengubah hubungan pointer antar node tanpa memindahkan data lain.

Karena tidak memerlukan proses shifting data, maka secara teoritis operasi insertion dan deletion pada Linked List bisa dilakukan dalam O(1) (jika posisi node sudah diketahui). Hal ini yang membuat Linked List lebih efisien dalam kondisi data yang sering berubah.
