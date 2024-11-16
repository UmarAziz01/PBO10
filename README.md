# PBO10
Penugasan matakuliah pemrograman berorientasi obyek pertemuan ketiga belas yakni project yang telah dibuat sebelumnya dalam repository PBO9 ditambahkan frame login yang menggunakan Persistence. Frame ini digunakan agar program digunakan oleh orang yang berhak saja, dimana orang tersebut diberikan username dan password untuk akses ke program crud yang telah dibuat. Sehingga data yang dimasukkan dalam didatabase lebih terintegritas sehingga konsistensi, akurasi, dan validitas data tersebut masih terjaga.

Untuk itu saya akan berbagi cara untuk membuat frame login dengan bahasa java (JDK versi 22) yang akan menggunakan JDBC PostgreSQL sebagai DBMS dan EclipseLink(JPA 2.2) sebagai Persistence Library. NOTE : Gunakan Aplikasi Apache NetBeans Di versi selain versi 21, karena pada versi 21 kita tidak bisa mencreate Entity Clases from Database sebab adanya bug pada form seperti dibawah ini. Untuk itu saya sarankan agar menggunakan versi 21 keatas bisa versi ke 22 ataupun 23 (Saya akan mempraktikan dengan Apache NetBeans versi ke 23) -versi terbaru ketika Repository ini dibuat-. 

![image](https://github.com/user-attachments/assets/2715a465-cf2b-4567-92d6-7d5d20ec891c)

image Foto bug pada Apache NetBeans Di versi 21

Kumpulan Link Pendukung :

https://github.com/UmarAziz01/PBO9

https://github.com/UmarAziz01/PBO8

https://github.com/UmarAziz01/PBO7

https://github.com/UmarAziz01/PBO6

https://github.com/UmarAziz01/PBO_UTS

https://drive.google.com/drive/folders/12E6Avw_WMRfr2LmdsNi6VL3eu4o3m3DJ?usp=sharing

Berikut langkah-langkahnya :

- Karena perintahnya adalah menambahkan Form Login kedalam project yang telah dibuat (PBO9), sehingga kita mencopy/menduplikasi project yang telah ada dari PBO_Persistence menjadi PBO_Login, dengan cara klik kanan pada project PBO_Persistence sehingga muncul gambar kurang lebih seperti ini
  ![image](https://github.com/user-attachments/assets/92482ab4-d3bb-4520-b1d1-5cfeae7a702f)
  ![image](https://github.com/user-attachments/assets/c6e10bba-bf93-4602-9797-2e4e41acca16)
  Dan Klik “Copy” lalu setelah itu cari project dengan nama PBO_Login dan klik copy lalu klik 2x untuk membuka project baru yang telah dibuat
  ![Screenshot 2024-11-16 195441](https://github.com/user-attachments/assets/46ba1228-b3e8-42ea-8451-e905d0b201be)
  karena hasil copy project maka butuh penyesuaian nama package, ubah nama package yang awalnya dari PBO_Persistence menjadi pbo_login, maka klik "Refactor" dengan tekan CTRL + R pada package dan lakukan hal serupa pada kode didalamnya jika masih menggunakan package PBO_Persistence
  ![image](https://github.com/user-attachments/assets/58b30190-ddab-4656-9de5-b8c2ad206902)

- Buat tabel baru dalam database dengan nama pengguna yang memiliki 2 kolom yakni Username dan Password untuk tipe data yang digunakan menyesuaikan kebutuhan, disini saya akan menggunakan Varchar. Dan masukkan juga Username dan password agar bisa diakses
  
  



 
  

    

  
  

  

  

- /
- /
- /
