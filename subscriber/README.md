# Subscriber

## Apa itu AMQP?
**Advanced Message Queuing Protocol (AMQP)** adalah standar terbuka untuk middleware perpesanan yang memungkinkan aplikasi berkomunikasi secara asinkron. Protokol ini menyediakan cara bagi berbagai komponen dalam suatu aplikasi, maupun antar aplikasi yang berbeda, untuk bertukar pesan dengan andal, aman, dan interoperabel.

AMQP mendefinisikan protokol untuk middleware berorientasi pesan, mencakup:
- Format dari pesan itu sendiri
- Aturan dalam pertukaran pesan
- Operasi yang dapat dilakukan terhadap pesan

Tujuan utama AMQP adalah memfasilitasi komunikasi antar sistem yang terdistribusi, termasuk skenario seperti:
- Antrean pesan (*message queuing*)
- Pengiriman pesan model *publish-subscribe*
- Model komunikasi *request-response*

## Contoh Format Koneksi AMQP
Berikut adalah contoh format URI untuk menghubungkan klien ke server AMQP:
```
amqp://guest:guest@localhost:5672
```
## Penjelasan Format URI
Format umum URI tersebut adalah:
```
protocol://username:password@hostname:port
```

| Bagian | Nilai dalam contoh | Keterangan |
|--------|--------------------|-------------|
| **Protocol** | `amqp` | Protokol yang digunakan untuk terhubung ke server, yaitu AMQP |
| **Username** | `guest` | Nama pengguna untuk autentikasi ke server |
| **Password** | `guest` | Kata sandi untuk autentikasi ke server |
| **Hostname** | `localhost` | Alamat dari server (dalam contoh ini, server berjalan pada mesin lokal) |
| **Port** | `5672` | Nomor port tempat server mendengarkan koneksi (port default AMQP) |
