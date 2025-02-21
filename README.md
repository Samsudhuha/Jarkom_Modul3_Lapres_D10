# Jarkom_Modul3_Lapres_D10

### 05111840000129 Ryukazu Andara Saviestyan
### 05111840000155 Muhamat Samsu Dhuha
### Kelompok D10

## Soal

```
Anri adalah seorang mahasiswa tingkat akhir yang sedang mengerjakan TA mengenai DHCP dan Proxy.
Bu Meguri sebagai dosen pembimbing Anri memberikan tugas pertamanya, (1) yaitu untuk membuat
topologi jaringan demi kelancaran TA-nya dengan kriteria sebagai berikut:
```

<br>

<center>
  
![img](/img/topologi.png)

</center>

<br>

```
Anri sudah pernah mempelajari teknik Jaringan Komputer sehingga Anri dapat membuat topologi
tersebut dengan mudah. Bu Meguri memerintahkan Anri untuk menjadikan SURABAYA sebagai
router, MALANG sebagai DNS Server, TUBAN sebagai DHCP server, serta MOJOKERTO sebagai Proxy
server, dan UML lainnya sebagai client.
Bu Meguri berpesan pada Anri untuk menyusun topologi secara hati-hati dan memperhatikan
gambar topologi yang diberikan Bu Meguri.
Karena TUBAN jauh dari client, maka perlu adanya perantara agar bisa saling terhubung. (2)
SURABAYA ditunjuk sebagai perantara (DHCP Relay) antara DHCP Server dan client.
Kriteria lain yang diminta Bu Meguri pada topologi jaringan tersebut adalah:
1. Seluruh client TIDAK DIPERBOLEHKAN menggunakan konfigurasi IP Statis.
2. (3) Client pada subnet 1 mendapatkan range IP dari 192.168.0.10 sampai 192.168.0.100 dan
192.168.0.110 sampai 192.168.0.200.
3. (4) Client pada subnet 3 mendapatkan range IP dari 192.168.1.50 sampai 192.168.1.70.
4. (5) Client mendapatkan DNS Malang dan DNS 202.46.129.2 dari DHCP
5. (6) Client di subnet 1 mendapatkan peminjaman alamat IP selama 5 menit, sedangkan (6) client
pada subnet 3 mendapatkan peminjaman IP selama 10 menit.

Bu Meguri adalah dosbing yang suka overthinking. Ia tidak ingin jaringan lokalnya terhubung ke
internet secara langsung. Sehingga ia memberi tugas tambahan pada Anri untuk membuatkan Proxy
sebagai penghubung jaringan lokal ke internet. Ada beberapa ketentuan yang harus dipenuhi dalam
pembuatan Proxy ini.
Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA. (7) User autentikasi
milik Anri memiliki format:
● User : userta_yyy
● Password : inipassw0rdta_yyy
Keterangan : yyy adalah nama kelompok masing-masing. Contoh: userta_c01
Anri sudah menjadwal pengerjaan TA-nya (8) setiap hari Selasa-Rabu pukul 13.00-18.00. Bu Meguri
membatasi penggunaan internet Anri hanya pada jadwal yang telah ditentukan itu saja. Maka diluar
jam tersebut, Anri tidak dapat mengakses jaringan internet dengan proxy tersebut. Jadwal bimbingan
dengan Bu Meguri adalah (9) setiap hari Selasa-Kamis pukul 21.00 - 09.00 keesokan harinya (sampai
Jumat jam 09.00). Agar Anri bisa fokus mengerjakan TA, (10) setiap dia mengakses google.com, maka
akan di redirect menuju monta.if.its.ac.id agar Anri selalu ingat untuk mengerjakan TA🙂.
Untuk menandakan bahwa Proxy Server ini adalah Proxy yang dibuat oleh Anri, (11) Bu Meguri
meminta Anri untuk mengubah error page default squid menjadi seperti berikut:
```

<br>

<center>
  
![img](/img/404.png)

</center>

<br>

```
Note : File error page bisa diunduh dengan cara wget 10.151.36.202/ERR_ACCESS_DENIED
   Tidak perlu di extract, cukup cp -r


(12) Karena Bu Meguri dan Anri adalah tipe orang pelupa, maka untuk memudahkan mereka, Anri
memiliki ide ketika menggunakan proxy cukup dengan mengetikkan domain
janganlupa-ta.yyy.pw dan memasukkan port 8080.
Keterangan : yyy adalah nama kelompok masing-masing. Contoh: janganlupa-ta.c01.pw
Bantu Anri menyelesaikan TA nya dibawah bimbingan Bu Meguri!👩🏻🎓
Catatan: Jika tidak bisa dan menyerah untuk setup DHCP Server pada TUBAN (dengan relay pada
SURABAYA), maka setup DHCP pada SURABAYA (tanpa DHCP Relay). Pastinya nilai tidak akan maksimal
```

## Jawab

1. 
``` 
Membuat topologi dan interface pada setiap uml
```
<center>
  
![img](/img/no1.topologi.png)

![img](/img/no1.surabaya.png)

![img](/img/no1.malang.png)

![img](/img/no1.mojokerto.png)

![img](/img/no1.tuban.png)

![img](/img/no1.sidoarjo.png)

![img](/img/no1.gresik.png)

![img](/img/no1.banyuwangi.png)

![img](/img/no1.malang.png)

</center>

<br>

2. 
```
install isc-dhcp-relay di uml surabaya, lalu mengubah isi interface pada file /etc/default/isc-dhcp-relay
```
<center>
  
![img](/img/no2.png)

</center>

<br>

3-6. 
```
install isc-dhcp-server di uml tuban, lalu mengubah isi interface pada file /etc/default/isc-dhcp-server dan juga menambah fungsi pada file /etc/dhcp/dhcpd.conf
```
<center>
  
![img](/img/no3.isc-dhcp-server.png)

![img](/img/no3.dhcpd.conf.png)

</center>

<br>

```
setelah itu jalankan perintah service isc-dhcp-server restart dan akan mendapatkan ip pada uml client
```

<center>
  
![img](/img/no3.hasil-madiun.png)

![img](/img/no3.hasil-gresik.png)

![img](/img/no3.hasil-banyuwangi.png)

</center>

<br>

7.
```
ketik perintah tersebut di uml mojokerto
```

<center>
  
![img](/img/7.2.png)

</center>

<br>

```
setelah itu ubah file squid.conf seperti berikut
```

<center>
  
![img](/img/7.3.png)

</center>

<br>

```
maka akan menghasilkan
```

<center>
  
![img](/img/7.4.png)

</center>

<br>

8-10.
```
buat file acl.conf di squid3 pada uml mojokerto seperti berikut
```

<center>
  
![img](/img/waktu.png)

</center>

<br>

```
dan di squid.conf seperti berikut
```

<center>
  
![img](/img/config.png)

</center>

<br>

11.
```
rm ERR_ACCESS_DENIED di /usr/share/squid/errors/English pada uml mojokerto lalu download dengan perintah wget 10.151.36.202/ERR_ACCESS_DENIED
```

<center>
  
![img](/img/error.png)

</center>

<br>

12.
```
buat file janganlupa-ta.d10.pw seperti berikut
```

<center>
  
![img](/img/12a.png)

</center>

<br>

```
dan file named.conf.local seperti berikut
```

<center>
  
![img](/img/12b.png)

</center>

<br>
