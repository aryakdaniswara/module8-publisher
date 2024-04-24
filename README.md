## Understanding publisher and message broker.

- How many data your publlsher program will send to the message broker in one run? </p>
Dalam tiap operasi, program publisher mengirimkan lima pesan ke message broker. Setiap pesan dikirim melalui pemanggilan fungsi `publisher_event`, yang menghasilkan pesan `UserCreatedEventMessage` berisi `user_id` dan `user_name`.
Pesan yang dikirimkan
1. User ID: "1", Nama Pengguna: "2206083546-Amir"
2. User ID: "2", Nama Pengguna: "2206083546-Budi"
3. User ID: "3", Nama Pengguna: "2206083546-Cica"
4. User ID: "4", Nama Pengguna: "2206083546-Dira"
5. User ID: "5", Nama Pengguna: "2206083546-Emir"
- The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean? </p>
URL amqp://guest:guest@localhost:5672 yang sama digunakan di program publisher dan subscriber menunjukkan bahwa keduanya terhubung ke broker pesan AMQP yang sama.
Dalam konteks ini, broker pesan yang digunakan adalah RabbitMQ yang berjalan di mesin lokal dengan nomor port 5672. Artinya, program publisher akan mengirim pesan ke RabbitMQ menggunakan URL tersebut, dan program subscriber akan mendengarkan dan mengambil pesan dari RabbitMQ juga menggunakan URL yang sama. Hal ini bertujuan untuk memastikan bahwa keduanya dapat berkomunikasi dengan efisien dan terintegrasi dengan broker pesan yang sama, memfasilitasi pertukaran pesan antara pengirim dan penerima dengan lancar.

## Running RabbitMQ as message broker.
![RabbitMQ](img/image_rabbit.jpg)

## Sending and processing event.
![alt text](img/image_event.jpg)
Ketika program publisher berjalan, data subscriber yang sebelumnya telah dibuat akan dikirimkan ke message queue. Subscriber alam menerima data tersebut dari message queue dan menunjukkannya.

## Monitoring chart based on publisher.
![alt text](img/image_spike.jpg)
Ketika kita menjalankan publisher secara berulang kali, terjadi spike yang menunjukkan adanya peningkatan laju pesan. Peningkatan laju pesan ini menunjukkan adanya antrian di RabbitMQ, yang mengelola sistem message queue.