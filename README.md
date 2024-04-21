## Reflection

### How many data your publlsher program will send to the message broker in one run?
- 5 kali karena ada 5x pemanggilan `publish_event` dengan topik `user_created` sebanyak 5x

### The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
- Ya sama, karena publisher akan mengirimkan pesan ke server AMQP. Publisher biasanya terhubung ke exchange di server AMQP dan mengirimkan pesan ke exchange tersebut.Setelah itu, subscriber akan menerima pesan tersebut dari AMQP. Subscriber biasanya terhubung ke queue di server AMQP dan menerima pesan dari queue tersebut. Oleh karena itu, keduanya terhubung ke server yang sama namun memiliki peran yang berbeda.

![Screenshot (490)](https://github.com/gnh374/tutorial-publisher/assets/121223135/c9034495-abeb-4f83-ae6b-549b0fbb9cb1)
![Screenshot 2024-04-21 202239](https://github.com/gnh374/tutorial-publisher/assets/121223135/8de177a9-93fe-4e47-a36e-ca0934488a21)
Saya menjalankan subscriber kemudian menjalankan publisher. Kemudian pesan ini terlihat pada terminal subscriber. Hal ini menunjukkan bahwa publisher berhasil mengirimkan data ke subscriber melalui RabbitMQ. Publisher mengirimkan data ke exchange. Selanjutnya exchange akan mengarahkan pesan ke queue yang tepat berdasarkan binding. Queue akan menyimpan pesan sementara. Kemudian subscriber akan menunggu pesan dalam antrian dan akan memprosesnya sesuai kebutuhan.

![Screenshot (492)](https://github.com/gnh374/tutorial-publisher/assets/121223135/13f42cb7-9449-4c41-934c-274d30d713d6)
Grafik diatas menunjukkan peningkatan banyaknya pesan yang dikirimkan pada suatu interval waktu. Spike kedua lebih tinggi daripada spike pertama karena pada rentang waktu tersebut saya menjalankan publisher lebih banyak dari pada rentang waktu sebelumnya sehingga pesan yang dikirimkan pada interval kedua lebih banyak dari interval sebelumnya.
![Screenshot (493)](https://github.com/gnh374/tutorial-publisher/assets/121223135/726dcb2d-a2af-421c-8620-d1735fc81cac)
Grafik diatas menunjukkan sempat ada 10 pesan pada queue. Hal ini terjadi karena kecepatan subscriber dalam mengonsumsi data pada ququq lebih lambat dari pada kecepatan pesan yang masuk sehingga pesan akan tetap berada di queue sampai subscriber mengonsumsi data tersebut
