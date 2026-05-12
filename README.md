# Modul-9-Software-Architecture

## Praktikum Message Broker dengan RabbitMQ

### Deskripsi

Praktikum ini bertujuan untuk memahami konsep **message broker** menggunakan **RabbitMQ** sebagai implementasi dari protokol AMQP (Advanced Message Queuing Protocol). Dalam praktikum ini, terdapat dua program utama:

- **Publisher**: Mengirimkan 5 event pesan ke message broker
- **Subscriber**: Menerima dan memproses event pesan dari message broker

Kedua program terhubung ke message broker yang sama menggunakan URL:

```
amqp://guest:guest@localhost:5672
```

---

## Hasil Percobaan

### Overview
![alt text](image-2.png)

#### Total
| Status | Jumlah |
|--------|--------|
| Ready | 0 |
| Unlocked | 0 |
| Total | 0 |

#### Message Rates (per detik)

| Metrik | Rate |
|--------|------|
| Publish | 1.5/s |
| Deliver | 1.0/s |
| Consumer | 0.5/s |
| Other | 0.0/s |

*Catatan: Grafik menunjukkan fluktuasi rate dari 0.0/s hingga 1.5/s*

#### Global Counts

| Komponen | Jumlah |
|----------|--------|
| Connections | 1 |
| Channels | 1 |
| Exchanges | 10 |
| Queues | 2 |
| Consumers | 1 |

#### Nodes

| Atribut | Nilai |
|---------|-------|
| Name | rabbit@[container_id] |
| File descriptors | Tersedia |
| Socket descriptors | Tersedia |
| Erlang processes | Aktif |
| Memory | Terpakai |
| Disk space | Tersedia |
| Uptime | Berjalan |
| Cores | 16 |
| Info | basic |
| Reset stats | Tersedia |

---

## Hasil Running Subscriber

![alt text](image-1.png)

Setelah subscriber dijalankan, pesan yang diterima adalah sebagai berikut:

```
In Anita's Computer [2306152273]. Message received: UserCreatedEventMessage { user_id: "1", user_name: "2306152273-Anita" }
In Anita's Computer [2306152273]. Message received: UserCreatedEventMessage { user_id: "2", user_name: "2306152273-Baila" }
In Anita's Computer [2306152273]. Message received: UserCreatedEventMessage { user_id: "3", user_name: "2306152273-Canti" }
In Anita's Computer [2306152273]. Message received: UserCreatedEventMessage { user_id: "4", user_name: "2306152273-Denis" }
In Anita's Computer [2306152273]. Message received: UserCreatedEventMessage { user_id: "5", user_name: "2306152273-Ema" }
```


## Kesimpulan

1. Publisher berhasil mengirim 5 pesan ke message broker
2. Subscriber berhasil menerima seluruh pesan yang dikirim
3. RabbitMQ mencatat aktivitas dengan:
   - **Message rate publish**: 1.5/s
   - **1 koneksi** dari subscriber
   - **2 queues** dan **10 exchanges** terdaftar
4. Tidak ada pesan yang tertahan dalam antrean (Ready: 0, Total: 0)

---

## Cara Menjalankan

### Prasyarat

- Docker Desktop
- Rust (dengan library crosstown_bus)

### Langkah-langkah

1. **Jalankan RabbitMQ** (di PowerShell/CMD):

```bash
docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.13-management
```

2. **Jalankan Subscriber** (di terminal WSL/Linux):

```bash
cd subscriber
cargo run
```

3. **Jalankan Publisher** (di terminal terpisah):

```bash
cd publisher
cargo run
```

4. **Monitoring** melalui browser:

```
http://localhost:15672
Username: guest
Password: guest
```


## Catatan Penting

- Gunakan RabbitMQ versi **3.13.x** (bukan 4.x) untuk kompatibilitas dengan library `crosstown_bus`
- Pastikan subscriber berjalan **sebelum** publisher agar queue dan exchange terbentuk
- Subscriber harus tetap berjalan untuk menerima pesan yang dikirim


## Referensi

- [RabbitMQ Documentation](https://www.rabbitmq.com/docs)
- [AMQP Protocol](https://www.amqp.org/)
- [Crosstown Bus Rust Library](https://crates.io/crates/crosstown_bus)
```
