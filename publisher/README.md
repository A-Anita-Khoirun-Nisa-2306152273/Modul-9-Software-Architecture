# Publisher

**a. Seberapa banyak data yang akan dikirim oleh program publisher ke message broker dalam satu kali proses?**

Dalam satu kali proses (satu kali run), program publisher akan mengirimkan **5 kali** pesan ke message broker.

**b. URL `amqp://guest:guest@localhost:5672` pada program publisher sama dengan yang ada di program subscriber. Apa maknanya?**

Artinya, **kedua program (publisher dan subscriber) terhubung ke server (message broker) yang sama**, yaitu server AMQP yang berjalan di `localhost` pada port `5672`, dengan kredensial yang sama (`guest:guest`). Dengan demikian, publisher dan subscriber dapat saling bertukar pesan karena mereka terdaftar pada broker yang sama.

Dengan kata lain:
- Publisher mengirim pesan ke broker tersebut.
- Subscriber mengambil atau menerima pesan dari broker yang sama.
- Inilah yang memungkinkan komunikasi antara keduanya.