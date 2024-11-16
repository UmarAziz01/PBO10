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
  
  ![image](https://github.com/user-attachments/assets/8a0cd469-2a58-4094-902e-7392432c43ee)

- Lalu buat Entity Classes from Database, disini pilih database yang telah kita buat sebelumnya, dan pilih database pada field Data Source dan pilih Add Tables
  
  ![image](https://github.com/user-attachments/assets/5d95b1f6-0fbb-49ff-993a-c03f63fe2aaf)
  ![image](https://github.com/user-attachments/assets/ddae27a2-9a9e-4f9d-967f-a0b89dcddb03)
  ![image](https://github.com/user-attachments/assets/0d738059-ec9e-4d1a-bd97-cb4962b388bf)

  sehingga muncul 3 file tersebut secara otomatis

- Lalu tambahkan Frame baru dengan nama LoginForm
  
  ![Screenshot 2024-11-16 204049](https://github.com/user-attachments/assets/e87097e6-db9c-44ae-9c35-c7ddccec1987)
  ![Screenshot 2024-11-16 204119](https://github.com/user-attachments/assets/d8d43351-5079-4112-85c7-d68ecdffc639)

- Buka LoginForm.java dan lakukan desain GUI
  
  ![image](https://github.com/user-attachments/assets/36c99e52-5fe3-4062-a21c-e3208bcb8f96)
  ![image](https://github.com/user-attachments/assets/b3b3d1f9-92f3-45bf-aed6-acdaa0283e2c)

- Klik Kanan button Login atau klik 2x juga bisa lalu masukkan kode dibawah ini untuk melakukan pencarian atau kecocokan data yang dimasukkan diprogram dengan yang ada di database
  
  ![image](https://github.com/user-attachments/assets/0c12bbbd-cdc4-49d5-8b5a-498f8cf82e28)

  ````java
  private void btnLoginActionPerformed(java.awt.event.ActionEvent evt) {         

        if (tfUsername.getText().equals("") | tfPassword.getText().equals("")) {
            JOptionPane.showMessageDialog(null, "Isi Terlebih Dahulu");
        } else {
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_LOGIN");
            EntityManager em = emf.createEntityManager();
            em.getTransaction().begin();

            String user = tfUsername.getText();
            String pass = tfPassword.getText();
            Pengguna pengguna = em.find(Pengguna.class, user);

            if (pengguna == null) {
                JOptionPane.showMessageDialog(null, "Username salah");
            } else if (pengguna.getPassword().equals(pass)) {
                JOptionPane.showMessageDialog(null, "Selamat datang");
                CRUDForm crudForm = new CRUDForm();
                crudForm.setVisible(true);
                this.dispose();
            } else {
                JOptionPane.showMessageDialog(null, "Password salah!");
            }
            em.getTransaction().commit();
            em.close();
            emf.close();
        }
    }

- Jika error maka anda perlu untuk menambahkan import ini kedalam kode anda
  ```java
  import javax.persistence.EntityManager;
  import javax.persistence.EntityManagerFactory;
  import javax.persistence.Persistence;
  import javax.swing.JOptionPane;
- Lakukan Clean and Build Project
  
  ![image](https://github.com/user-attachments/assets/7370d89d-6e87-4045-b29c-2bfa9b66232b)

- Tunggu proses sampai selesai
  
  ![image](https://github.com/user-attachments/assets/b5d5f4a0-0276-4a57-9cd3-51b7f517ee87)

- Jalankan program anda sekarang

  ![image](https://github.com/user-attachments/assets/6a903176-7be1-4b98-8c00-2f74a812281a)
  
  Klik Run atau bisa dengan tekan F6 pada keyboard anda

  ![image](https://github.com/user-attachments/assets/d7860338-975f-4620-a0f3-ffcda0a851c6)
  
  Form Login yang anda telah buat muncul dilayar anda, silahkan untuk memasukkan username serta password yang tadi telah dibuat

  ![image](https://github.com/user-attachments/assets/cc3b9347-e70a-4063-acda-d8751d4437c2)
  
  Tidak ada error pada program ini

  ![image](https://github.com/user-attachments/assets/132f11cb-8fac-4092-9b83-945267d43f7e)
  
  Disini saya memasukkan
  
  Username : admin1
  
  Password : admin
  
  Muncul pesan Username salah, karena dalam database username ini tidak ada

  ![image](https://github.com/user-attachments/assets/5ae394c1-a373-47cc-a924-a4726808386a)
  
  Disini saya memasukkan
  
  Username : admin
  
  Password : Admin

  Muncul pesan Passowrd salah, karena dalam database password ini penulisannya salah. Seharusnya..

  ![image](https://github.com/user-attachments/assets/30d55555-7af2-4df3-afaa-2eb05c12dbcb)

  Disini saya memasukkan

  Username : admin

  Password : admin

  Muncul pesan Selamat Datang, saat anda menekan OK maka akan diarahkan pada Program CRUDForm.java dan Program FormLogin akan tertutup secara otomatis

  ![image](https://github.com/user-attachments/assets/4d8c32c7-bb17-48f8-a39f-c81d590566fc)

  Sehingga anda disini dapat melakukan pengolahan data dengan nyaman dan tenang, karena hanya orang yang diberi akses saja yang dapat melakukan pengolahan data pada database anda

  Nampak dari awal program dijalankan bahwa program tidak mengalami error, dan Form Login yang saya buat ini dapat membedakan antara Kapital dan Non-Kapitalnya Username serta Password sehingga anda harus mengingat betul penulisan dari Usename juga Password anda, jika tidak maka anda tidak akan bisa mengakses CRUDForm karena anda tidak memiliki hak akses

  Sekian penjelasan saya mengenai langkah langkah membuat Form Login dengan Java Persistence
