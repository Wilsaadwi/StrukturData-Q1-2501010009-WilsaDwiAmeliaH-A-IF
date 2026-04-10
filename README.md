# 1. Karakteristik Memori dan Akses Data

Array bisa melakukan akses elemen dalam waktu O(1) karena datanya disimpan secara kontinu (berurutan di memori). Jadi kalau mau ambil data di indeks tertentu, alamat memorinya bisa langsung dihitung tanpa harus mencari satu per satu.

Sedangkan pada Singly Linked List, data disimpan secara tidak berurutan (non-kontinu). Setiap node hanya menyimpan data dan pointer ke node berikutnya. Jadi untuk mengakses elemen tertentu, harus ditelusuri dari awal (head) sampai ke posisi yang diinginkan. Proses ini membuat waktu akses menjadi O(n).

# 2. Analisis Efisiensi Operasi Manipulasi

Linked List lebih unggul dibanding Array ketika sering melakukan penyisipan (insertion) dan penghapusan (deletion), terutama di bagian tengah atau awal.

Secara teoritis, perbedaannya ada pada cara penyimpanan dan manipulasi datanya:

* Pada Array, elemen disimpan secara berurutan, sehingga ketika ada insertion atau deletion di tengah, elemen lain harus digeser (shifting) untuk menjaga urutan. Proses ini menyebabkan kompleksitas waktu menjadi O(n).

* Pada Linked List, data tidak disimpan berurutan, melainkan dihubungkan dengan pointer. Saat melakukan insertion atau deletion, cukup mengubah hubungan pointer antar node tanpa memindahkan data lain.

Karena tidak memerlukan proses shifting data, maka secara teoritis operasi insertion dan deletion pada Linked List bisa dilakukan dalam O(1) (jika posisi node sudah diketahui). Hal ini yang membuat Linked List lebih efisien dalam kondisi data yang sering berubah.

# 3. Konsep Doubly Linked List

Pada Doubly Linked List, setiap node memiliki tiga bagian utama, yaitu data, pointer ke node berikutnya (next), dan pointer ke node sebelumnya (prev). Berbeda dengan Singly Linked List yang hanya memiliki satu arah, struktur ini memungkinkan setiap node terhubung secara dua arah, sehingga traversal dapat dilakukan dari depan ke belakang maupun dari belakang ke depan. Secara konsep, hal ini membuat Doubly Linked List lebih fleksibel dalam proses penelusuran data.

Selain itu, keberadaan pointer prev juga memberikan keuntungan dalam operasi tertentu seperti penghapusan node, karena tidak perlu mencari node sebelumnya dari awal. Namun, di sisi lain, penggunaan dua pointer dalam setiap node menyebabkan kebutuhan memori menjadi lebih besar dibandingkan Singly Linked List. Selain itu, pengelolaannya juga lebih kompleks karena setiap perubahan harus menjaga konsistensi antara pointer next dan prev agar struktur tidak rusak. Oleh karena itu, Doubly Linked List bisa dibilang sebagai struktur yang lebih fleksibel, tetapi dengan konsekuensi penggunaan memori dan kompleksitas yang lebih tinggi.

# 4. Mekanisme Circular Linked List

Perbedaan utama secara teoritis antara Circular Linked List dan Linked List biasa terletak pada struktur hubungan node terakhir.

* Pada Linked List biasa, node terakhir menunjuk ke null, yang menandakan akhir dari struktur data.
  
* Pada Circular Linked List, node terakhir tidak menunjuk ke null, tetapi kembali menunjuk ke node pertama (head), sehingga membentuk struktur melingkar (circular).

Secara konsep, Circular Linked List tidak memiliki nilai null sebagai penanda akhir, sehingga proses traversal dapat dilakukan secara terus-menerus tanpa berhenti, selama tidak diberikan kondisi penghentian.

Struktur ini lebih efektif digunakan pada sistem yang membutuhkan perulangan berkelanjutan, seperti round robin scheduling, karena setelah elemen terakhir diproses, proses dapat langsung kembali ke elemen pertama tanpa perlu mengulang dari awal secara manual.

# 5. Array Dinamis di Python

Python list sebenarnya diimplementasikan sebagai dynamic array, yaitu array yang kapasitasnya bisa bertambah secara otomatis tanpa harus kita atur manual.

Di balik layar, Python tidak langsung menambah 1 slot setiap kali append, tapi dia punya konsep kapasitas (capacity) dan jumlah elemen (size). Kapasitas biasanya lebih besar dari jumlah elemen yang sedang dipakai.

Saat melakukan append, ada dua kemungkinan:

* Kalau kapasitas masih cukup → elemen langsung ditambahkan, jadi prosesnya cepat (O(1)).
  
* Kalau kapasitas sudah penuh → Python akan melakukan proses resize.

Proses resize :

1. Python membuat array baru dengan kapasitas yang lebih besar (biasanya tidak cuma +1, tapi langsung dilipatgandakan atau ditambah sekian persen biar efisien).
2. Semua elemen lama disalin (copy) ke array baru.
3. Elemen baru dimasukkan ke array tersebut.
4. Array lama tidak dipakai lagi.

Karena ada proses menyalin semua data, maka saat resize terjadi, kompleksitas waktunya jadi O(n).

Tapi karena resize ini tidak terjadi setiap kali append (jarang terjadi), maka secara keseluruhan atau rata-rata (amortized), operasi append tetap dianggap O(1).

Selain itu, dari sisi memori:

* Dynamic array biasanya punya ruang kosong (unused space) untuk menghindari resize terlalu sering.
  
* Ini membuat penggunaan memori sedikit lebih besar, tapi jauh lebih efisien dari sisi performa.

Jadi intinya, Python list itu cepat untuk penambahan data karena pakai strategi resize yang jarang, walaupun sesekali ada biaya mahal saat harus menyalin seluruh elemen.
