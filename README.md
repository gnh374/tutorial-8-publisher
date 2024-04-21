## Reflection

### How many data your publlsher program will send to the message broker in one run?
- 5 kali karena ada 5x pemanggilan `publish_event` dengan topik `user_created` sebanyak 5x

### The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
- Ya sama, karena publisher akan mengirimkan pesan ke server AMQP. Publisher biasanya terhubung ke exchange di server AMQP dan mengirimkan pesan ke exchange tersebut.Setelah itu, subscriber akan menerima pesan tersebut dari AMQP. Subscriber biasanya terhubung ke queue di server AMQP dan menerima pesan dari queue tersebut. Oleh karena itu, keduanya terhubung ke server yang sama namun memiliki peran yang berbeda.

![Screenshot (490)](https://github.com/gnh374/tutorial-publisher/assets/121223135/c9034495-abeb-4f83-ae6b-549b0fbb9cb1)

