# LAPORAN TUGAS KEENAM PEMROGRAMAN BERORIENTASI OBJEK

👨‍🏫 *Dosen Pembimbing*: Bayu Adhi Nugroho, Ph.D  
🎓 *Program Studi*: Sistem Informasi

📝#A. Penjelasan

Laporan ini membahas pembuatan aplikasi Java Swing untuk menampilkan dan mengelola data mata kuliah
dalam tabel yang mencakup Kode Mk, SKS, Nama Mata Kuliah, dan Semester Ajar. Aplikasi ini mendukung fitur CRUD (Create, Read, Update, Delete)
serta dilengkapi kemampuan untuk mencetak laporan data mata kuliah dengan format yang rapi menggunakan JasperReports 📄✨.

# Langkah-Langkah
1. Langkah pertama yaitu menginstal plugins ke dalam java
    ![image](https://github.com/user-attachments/assets/e938183f-9a73-4b54-8001-dfe97b0d7741)
    ![image](https://github.com/user-attachments/assets/1c4ac9b8-5c18-4516-9ff6-4c244a67b2d0)

2. Langkah kedua yaitu menginstal ireport kedalam java
    ![image](https://github.com/user-attachments/assets/68384a3c-de69-47e2-a774-be3f140b89fc)

3. Langkag ketiga yaitu menambahkan library
    ![image](https://github.com/user-attachments/assets/fe52ca0c-f559-4cf4-9cc5-5213ec7c087a)

4. Menambahlan report pada untuk membuat template laporan dan mencari database dengan cara klik kana
   pada bagian package lalu pilih other dan pilih report lalu pilih report Wizerd.
    ![image](https://github.com/user-attachments/assets/b97bf722-2147-4c2b-a2a8-ddea97d23fe1)

5. Selanjutnya memilih template yang ingin dipake untuk  laporan
    ![image](https://github.com/user-attachments/assets/990d3407-ad9b-4420-91e8-e9bfe84f8cab)

6. Menentukan nama file (reportPerkuliahan.jrxml) dan lokasi penyimpanan template laporan dalam proyek NetBeans (src/soaluts).
    ![image](https://github.com/user-attachments/assets/d59a9008-010d-4a79-a9ab-a5fbb3dd6b4e)

7. Langkah ketuju yaitu Menyisipkan Query SQL pada postgres untuk mengambil semua data yang
   ada di tabel "MataKuliah" yang sudah tersimpan di database sebelumnya.
    ![image](https://github.com/user-attachments/assets/8fc983b6-5956-456f-8731-4d4785f7b03b)

8. Langkah ke delapan yaitu memindahkan field seperti kodemk, sks, namamk, dan semesterajar agar tercetak kedalam laporan yaitu ke sebelah kanan.
    ![image](https://github.com/user-attachments/assets/5ff3105b-f8b2-43f7-92d0-0f49450e3a27)
    ![image](https://github.com/user-attachments/assets/c085e1dc-2f0d-4a2d-894a-d88b874152bf)

9. Langkah kesembilan yaitu menampilna hasil dari laporan yang sudah dibuat dan sudah diedit lalu klik priview agar gambar terlihat sempurna.
    ![image](https://github.com/user-attachments/assets/d16bfc09-88c7-4438-9cc6-79323dc13354)

10. Langkah ke sepuluh yaitu membuat button cetak agar laporan yang sudah dibuat bisa dicetak.
Yaitu dengan menggunakan kode dibawah ini :

        private void btnCetakActionPerformed(java.awt.event.ActionEvent evt) {                                         
        JasperReport reports;
        try {
            if (conn == null || conn.isClosed()) {
                // Mencoba untuk membuka koneksi baru
                try {
                    conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/Perkuliahan", "postgres", "Ela200705");
                    System.out.println("Koneksi berhasil dibuka.");
                } catch (SQLException e) {
                    System.err.println("Gagal membuka koneksi: " + e.getMessage());
                    return; // Keluar dari metode jika koneksi gagal
                }
            }
        } catch (SQLException ex) {
            Logger.getLogger(Perkuliahan.class.getName()).log(Level.SEVERE, null, ex);
        }

        String path = ".\\src\\soaluts\\ReportPerkuliahan.jasper";
        try {
            reports = (JasperReport) JRLoader.loadObjectFromFile(path);
            JasperPrint jprint = JasperFillManager.fillReport(path, null, conn);
            JasperViewer jviewer = new JasperViewer(jprint, false);
            jviewer.setDefaultCloseOperation(DISPOSE_ON_CLOSE);
            jviewer.setVisible(true);
        } catch (JRException ex) {
            Logger.getLogger(Perkuliahan.class.getName()).log(Level.SEVERE, null, ex);
        }}                                        

    ![image](https://github.com/user-attachments/assets/1c84bfbd-1b73-49dc-b3fe-0ef87a040a26)

11. Melakukan konfigurasi project properties untuk menambahkan vm option pada bagian RUN untuk mengatasi akses server pada java.
      ![image](https://github.com/user-attachments/assets/96e97915-256b-49c1-83ea-3cea914be814)

12. Finish
      ![image](https://github.com/user-attachments/assets/f0493959-381e-4025-ac4e-990daefe171a)
      ![image](https://github.com/user-attachments/assets/b4ae26cb-f6ef-4cb2-95f7-e76a0132f030)
