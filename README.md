# MCF-TestQuery

### Soal Test Query

### 1. Sebutkan kolom yang bisa dijadikan primary key dan foreign key.

-   **TabelPembayaran**:
    -   **Primary Key**: `NoKontrak`
    -   **Foreign Key**: `KodeCabang`, `KodeMotor`
    
-   **TabelCabang**:
    -   **Primary Key**: `KodeCabang`

-   **TabelMotor**:
    -   **Primary Key**: `KodeMotor`

### 2. Tuliskan query untuk menampilkan data pembayaran yang dibayar pada tanggal 20-10-2014.

    SELECT * FROM TabelPembayaran WHERE CONVERT(DATE, TglBayar) =  '2014-10-20';

### 3. Tuliskan query untuk menambahkan data pada tabel “Cabang”, dengan informasi berikut: kode cabang 200, nama cabang Tangerang.

    INSERT  INTO TabelCabang (KodeCabang, NamaCabang) VALUES (200, 'Tangerang');

### 4. Tuliskan query untuk update data “Kode Motor” pada tabel “Pembayaran” menjadi “001” untuk semua Cabang Jakarta.

    UPDATE TabelPembayaran SET KodeMotor = '001' FROM TabelPembayaran INNER JOIN TabelCabang ON TabelPembayaran.KodeCabang = TabelCabang.KodeCabang WHERE TabelCabang.NamaCabang = 'Jakarta';

### 5. Tuliskan query untuk menampilkan data berikut

    SELECT 
        TabelPembayaran.NoKontrak, 
        TabelPembayaran.TglBayar, 
        TabelPembayaran.JumlahBayar, 
        TabelPembayaran.KodeCabang, 
        TabelPembayaran.NoKwitansi, 
        TabelPembayaran.KodeMotor, 
        TabelMotor.NamaMotor
    FROM 
        TabelPembayaran
    LEFT JOIN 
        TabelMotor
    ON 
        TabelPembayaran.KodeMotor = TabelMotor.KodeMotor;
        
### 5. Tuliskan query untuk menampilkan data berikut
![No 5](https://i.ibb.co.com/nDnHXhm/Screenshot-2024-05-30-at-20-11-54.png)

    SELECT 
        TabelPembayaran.NoKontrak, 
        TabelPembayaran.TglBayar, 
        TabelPembayaran.JumlahBayar, 
        TabelPembayaran.KodeCabang, 
        TabelPembayaran.NoKwitansi, 
        TabelPembayaran.KodeMotor, 
        TabelMotor.NamaMotor
    FROM 
        TabelPembayaran
    LEFT JOIN 
        TabelMotor
    ON 
        TabelPembayaran.KodeMotor = TabelMotor.KodeMotor;

### 6.  Tuliskan query untukmenampilkan data berikut.
![No 6](https://i.ibb.co.com/JKd89Hq/Screenshot-2024-05-30-at-20-14-18.png)

    SELECT 
        TabelCabang.KodeCabang, 
        TabelCabang.NamaCabang, 
        TabelPembayaran.NoKontrak, 
        TabelPembayaran.NoKwitansi
    FROM 
        TabelCabang
    LEFT JOIN 
        TabelPembayaran
    ON 
        TabelCabang.KodeCabang = TabelPembayaran.KodeCabang;


### 7.  Tuliskan query untukmenampilkan data berikut.
![No 7](https://i.ibb.co.com/f8y12pT/Screenshot-2024-05-30-at-20-17-27.png)

       SELECT 
        TabelCabang.KodeCabang, 
        TabelCabang.NamaCabang, 
        COUNT(TabelPembayaran.NoKontrak) AS TotalData, 
        ISNULL(SUM(TabelPembayaran.JumlahBayar), 0) AS TotalBayar
    FROM 
        TabelCabang
    LEFT JOIN 
        TabelPembayaran
    ON 
        TabelCabang.KodeCabang = TabelPembayaran.KodeCabang
    GROUP BY 
        TabelCabang.KodeCabang, 
        TabelCabang.NamaCabang;
