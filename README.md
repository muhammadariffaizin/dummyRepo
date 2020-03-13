# Spesifikasi Program BST Lamp Controller

Detail Program

![](img/detail.png)

## Overview

***BST Lamp Controller*** adalah program berbasisi CLI yang digunakan untuk melakukan pengontrolan dan virtualisasi terhadap alat controller yang terhubung dengan susunan suatu himpunan lampu yang disusun mengikuti aturan tertentu. Struktur lampu-lampu tersebut disusun sedemikan rupa membentuk struktur sebuah Binary Search Tree (BST) yang kemudian dinamakan **BST Lamp**.

Tujuan dibentuknya struktur BST Lamp ini adalah untuk mengedukasi dan menunjukkan struktur Binary Search Tree agar menarik dan mudah untuk dipelajari. Berikut adalah contoh gambaran sederhana sebuah BST Lamp.

![](img/bstlamp.png)

## Detail Lampu

Sebuah lampu pada BST Lamp mempunyai komponen-komponen sebagai berikut:

- Bilangan bulat positif, yang digunakan untu membedakan lampu satu dengan lampu lainnya dan menandakan kebutuhan daya untuk lampu tersebut.
- Dua buah port yang mempunyai kabel pada masing-masing portnya dapat diekstensi (disambungkan) menuju lampu lain.
- Satu buah port yang digunakan untuk menerima ekstensi kabel dari kabel lain.

BST Lamp ini hanya bisa mengakomodasi lampu-lampu yang unik (tidak ada duplikasi).

## Initial Runtime

Saat program pertama kali dijalankan, akan muncul output pesan berupa:
```
Initializing application...
Insert your initial configuration:
```

Kemudian baris berikutnya adalah input bentuk awal BST Lamp. Input awal terdiri dari bilangan bulat positif sebanyak-banyaknya (paling tidak satu buah bilangan) yang dipisahkan spasi. Input selesai apabila tombol `Enter` ditekan yang kemudian menampilkan output:
```
Starting interactive shell...
```

Perintah-perintah (command) dapat mulai diinputkan dibaris setelah itu.

## Daftar Perintah

---

- ### **`install`**
    

    **Sintaks**
    ```
    install <arg>
    ```
    Perintah `install` digunakan untuk mem-virtualisasikan pemasangan lampu baru pada struktur BST Lamp yang telah ada.


    **Argumen:**
    + **`<arg>`** merupakan argumen berupa bilangan bulat positif. Misal 2, 3, 14, dsb.

    **Normal Output**

    Jika lampu berhasil dipasang

    ```
    >> Lamp <arg> installed

    ```

    Jika lampu sudah pernah dipasang

    ```
    >> Lamp <arg> already exist

    ```

    ---
- ### **`inspect`**


    **Sintaks**
    
    ```
    inspect [option]
    ```
    Perintah inspect digunakan untuk melihat status terkini lampu.

    **Argumen:**

    > Argumen `[option]` bersifat opsional, dapat dituliskan atau tidak. Apabila tidak dituliskan, akan otomatis menggunakan `--all`.

    + **`--all`**
        
        Digunakan untuk melihat status untuk dua poin selanjutnya sekaligus. Hasil dari `--longestCable` diikuti `--cableCount`.
    + **`--longestCable`**
        
        Digunakan untuk menghitung total kabel terpanjang yang terpasang (dihitung dari tempat lampu paling atas) hingga lampu terbawah.
    + **`--cableCount`**
        
        Digunakan untuk menghitung banyaknya kabel yang terkoneksi sekarang.

    **Normal Output**

    **`--all`**
    ```
    >> Longest cable: <number>
    >> Interconnected cable: <number>

    ```


    **`--longestCable`**
    ```
    >> Longest cable: <number>

    ```

    **`--cableCount`**
    ```
    >> Interconnected cable: <number>

    ```
    > Note: **`<number>`** merupakan suatu bilangan bulat sesuai dengan deskripsi perintah.

    ---
- ### **`analyze`**


    **Sintaks :**
    
    ```
    analyze <option>
    ```

    Perintah `analyze` digunakan untuk menganalisis keadaan lampu yang terpasang pada BST yang sekarang. Untuk saat ini hanya dapat menganalisis dua hal, yakni:

    1. Mencari lampu pertama (dihitung dari lampu paling atas) yang kemungkinan menyebabkan N lampu bermasalah/mati/rusak.

    2. Mencari dua lampu A dan B yang mempunyai jumlahan daya tepat X. Dalam hal ini, A dan B masing-masing merupakan lampu dengan daya terkecil dan lampu dengan daya terbesar.


    > Argumen `<option>` harus dispesifikan.

    **Argumen:**

    + **`--brokenLamp <args...>`**

        Menjalankan perintah spesifik untuk **poin 1** di atas. Argumen `<args...>` menerima bilangan bulat sebanyak-banyaknya dipisahkan spasi.

    + **`--totalPower <arg>`**

        Menjalankan perintah spesifik untuk **poin 2** di atas. Argumen `<arg>` merupakan bilangan **X**.

    **Normal Output**

    Perintah **`--brokenLamp <args...>`**
    
    Jika banyaknya yang dianalisis lebih dari 1, maka:
    ```
    >> There might be a problem with cable on the lamp <number> and so on

    ```

    Jika banyaknya yang dianalisis hanya 1, maka:
    ```
    >> Only a lamp inserted. You need minimum of two lamps

    ```

    Perintah **`-- totalPower <arg>`**
    ```
    >> Lamp with total of <X> are <A> dan <B>

    ```
    > `<X>`, `<A>`, dan `<B>` masing-masing adalah bilangan bulat sesuai pada deskripsi perintah.

    Apabila memang tidak ada lampu yang memenuhi, akan mencetak pesan error:

    ```
    >> No lamps found

    ```

    ---

- ### `exit`

    **Sintaks :**

    ```
    exit
    ```
    Digunakan untuk mengakhiri program dan keluar dari program.

    **Normal Output**
    ```
    >> Exiting application

    ```

## Asumsi Input

Pada bagian ini, developer dapat menganggap bahwa beberapa input dapat diasumsikan pasti benar. Input-input tersebut termasuk dalam:

- Bilangan bulat lampu diasumsikan selalu positif kurang dari 1000.
- Input awal konfigurasi BST Lamp diasumsikan benar (minimal satu lampu).
- Argumen perintah `analyze` diasumsikan pasti ada lampu yang dianalisis.

## Error Handling

Selain daftar perintah di atas, program juga dapat menangani error ketika user salah meng-inputkan sesuatu atau salah meng-inputkan perintah.

- ### CommandError Exception

    Command Error terjadi ketika perintah yang dimasukkan tidak terdapat dalam daftar/tidak dikenali. Dalam hal ini, program akan mencetak pesan error sebagai berikut.

    ```
    >> Error: unrecognized command

    ```

- ### ArgumentError Exception

    Argument Error terjadi ketika memasukkan perintah tanpa argumen dan/atau argumen tidak sesuai. Argument Error dibagi berdasarkan perintah yang dimaksud.

    + Perintah **`install`**

        Ketika argumen tidak disertakan, maka akan mencetak pesan error:

        ```
        >> Error: argument required -> <lamp_power>
            
            install <lamp_power>

        ```
    + Perintah **`inspect`**

        Ketika memasukkan argumen yang tidak dikenali, maka akan mencetak pesan error:
        ```
        >> Error: invalid argument

        ```

    + Perintah **`analyze`**

        Ketika memasukkan perintah tanpa argumen, maka akan mencetak pesan error:
        ```
        >> Error: argument requires -> [options]
        >> You can try one of the following options:

            analyze --brokenLamp <args...>
            analyze --totalPower <arg>
        
        ```

        Ketika memasukkan argumen yang tidak dikenali, maka akan mencetak pesan error:
        ```
        >> Error: invalid argument

        ```

- ### LogicalError Exception

    Logical Error terjadi ketika argumen yang dimasukkan tidak ditemukan. Dalam hal ini hanya terdapat pada perintah **`analyze --brokenLamp`**.

    Jika dalam menjalankan perintah tersebut, terdapat paling tidak 1 saja argumen yang tidak ditemukan dalam BST Lamp, maka akan mencetak pesan error:
    ```
    >> Error: lamp(s) not found

    ```

## Exit Process

Setelah program diberhentikan, maka akan muncul pesan terakhir seperti berikut.
```
Application stopped
```
