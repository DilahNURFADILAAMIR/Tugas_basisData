Sistem Database Rumah Sakit

*Proyek SQL • MariaDB/XAMPP*

Repository ini berisi proses lengkap pembuatan database rumah_sakit,
mulai dari pembuatan tabel, pengisian data, hingga contoh penggunaan
WHERE dan BETWEEN pada query SQL.\
Semua script dapat dijalankan langsung pada MariaDB, MySQL, atau XAMPP.

------------------------------------------------------------------------

1. Create Database

``` sql
CREATE DATABASE rumah_sakit;
USE rumah_sakit;
```

------------------------------------------------------------------------

2. Create Tables

 Tabel: pasien

``` sql
CREATE TABLE pasien (
    id_pasien INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100),
    umur INT,
    alamat VARCHAR(150)
);
```

 Tabel: dokter

``` sql
CREATE TABLE dokter (
    id_dokter INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100),
    spesialis VARCHAR(50),
    no_hp VARCHAR(20)
);
```

 Tabel: kunjungan

``` sql
CREATE TABLE kunjungan (
    id_kunjungan INT AUTO_INCREMENT PRIMARY KEY,
    id_pasien INT,
    id_dokter INT,
    tanggal DATE,
    keluhan VARCHAR(150),
    FOREIGN KEY (id_pasien) REFERENCES pasien(id_pasien),
    FOREIGN KEY (id_dokter) REFERENCES dokter(id_dokter)
);
```

------------------------------------------------------------------------

3. Insert Data

 Data Pasien (15 data)

``` sql
INSERT INTO pasien (nama, umur, alamat) VALUES
('Rama', 25, 'Jl. Melati 1'),
('Putri', 30, 'Jl. Anggrek 2'),
('Budi', 40, 'Jl. Kenanga 3'),
('Nanda', 22, 'Jl. Mawar 4'),
('Salsa', 35, 'Jl. Teratai 5'),
('Fahri', 28, 'Jl. Dahlia 6'),
('Lala', 33, 'Jl. Seroja 7'),
('Reza', 45, 'Jl. Cemara 8'),
('Tiara', 20, 'Jl. Ketapang 9'),
('Dimas', 38, 'Jl. Kamboja 10'),
('Maya', 27, 'Jl. Akasia 11'),
('Rizky', 31, 'Jl. Flamboyan 12'),
('Wawan', 29, 'Jl. Pinang 13'),
('Rina', 24, 'Jl. Randu 14'),
('Dito', 36, 'Jl. Pepaya 15');
```

 Data Dokter (15 data)

``` sql
INSERT INTO dokter (nama, spesialis, no_hp) VALUES
('Dr. Andi', 'Umum', '081300001'),
('Dr. Rina', 'Anak', '081300002'),
('Dr. Budi', 'Jantung', '081300003'),
('Dr. Laila', 'Kandungan', '081300004'),
('Dr. Fajar', 'Bedah', '081300005'),
('Dr. Maya', 'Kulit', '081300006'),
('Dr. Rizal', 'Saraf', '081300007'),
('Dr. Putri', 'THT', '081300008'),
('Dr. Hadi', 'Mata', '081300009'),
('Dr. Tika', 'Gigi', '081300010'),
('Dr. Nita', 'Psikiatri', '081300011'),
('Dr. Wawan', 'Paru-paru', '081300012'),
('Dr. Fina', 'Ginjal', '081300013'),
('Dr. Dedi', 'Orthopedi', '081300014'),
('Dr. Sari', 'Rehab Medis', '081300015');
```

 Data Kunjungan (15 data)

``` sql
INSERT INTO kunjungan (id_pasien, id_dokter, tanggal, keluhan) VALUES
(1, 2, '2025-01-10', 'Demam'),
(2, 1, '2025-01-11', 'Batuk'),
(3, 5, '2025-01-11', 'Luka jatuh'),
(4, 3, '2025-01-12', 'Nyeri dada'),
(5, 4, '2025-01-13', 'Cek kehamilan'),
(6, 10, '2025-01-14', 'Sakit gigi'),
(7, 9, '2025-01-15', 'Mata merah'),
(8, 6, '2025-01-16', 'Ruam kulit'),
(9, 8, '2025-01-17', 'Sakit telinga'),
(10, 14, '2025-01-17', 'Nyeri tulang'),
(11, 11, '2025-01-18', 'Cemas berlebih'),
(12, 12, '2025-01-19', 'Sesak napas'),
(13, 13, '2025-01-19', 'Masalah ginjal'),
(14, 7, '2025-01-20', 'Pusing berlebih'),
(15, 15, '2025-01-21', 'Terapi cedera');
```

------------------------------------------------------------------------

4. Query WHERE (3 Contoh)

 1️ Pasien dengan umur \> 30

``` sql
SELECT * FROM pasien
WHERE umur > 30;
```

 2️ Dokter dengan spesialis = 'Jantung'

``` sql
SELECT * FROM dokter
WHERE spesialis = 'Jantung';
```

 3️ Kunjungan dengan keluhan 'Pusing berlebih'

``` sql
SELECT * FROM kunjungan
WHERE keluhan = 'Pusing berlebih';
```

------------------------------------------------------------------------

5. Query BETWEEN (3 Contoh)

 1 Pasien umur 25--35

``` sql
SELECT * FROM pasien
WHERE umur BETWEEN 25 AND 35;
```

 2️ Kunjungan tanggal 12--18 Januari 2025

``` sql
SELECT * FROM kunjungan
WHERE tanggal BETWEEN '2025-01-12' AND '2025-01-18';
```

 3️ Dokter dengan ID 5 sampai 10

``` sql
SELECT * FROM dokter
WHERE id_dokter BETWEEN 5 AND 10;
```

------------------------------------------------------------------------
