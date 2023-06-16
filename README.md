# Task Web Server & Load Balancing

#### 1. Instalasi nginx melalui apt
- Pertama jalankan perintah ``$ sudo apt install nginx``<br/><br/>![1](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/f8ef96b7-c320-417c-bd68-bb81770af673)
<br/><br/> Nanti akan ada tampilan **Do you want to continue? [Y/n]** maka ketik "y" untuk melanjutkan installan.<br/><br/>
- Kedua bila sudah selesai penginstallan maka kita bisa mengecek nginx sudah terinstall apa belum. dengan perintah ``$ nginx -v``<br/><br/>![2](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/10f8b593-88f9-4b11-baf0-756a76b02d4b)<br/><br/>
- Setelah jalankan ``$ sudo systemctl enable nginx``, dan ``$ sudo systemctl start nginx``. dan kita bisa mengecek nginx berjalan atau tidak dengan perintah ``$ sudo systemctl status nginx``.<br/><br/>![4](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/dec1ab1d-ec92-44c6-84e1-2aefb9bda6df)<br/><br/>
- Terakhir akses Web browser dan ketik IP kalian. Bila tampil seperti berikut installan nginx berhasil.<br/><br/>![3](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/27c79c5c-5e24-4109-a3b5-e462135a40d0)<br/><br/>

#### 2. menjalankan aplikasi dumbflix menggunakan PM2
- Pertama kita perintahkan ``$ git clone https://github.com/dumbwaysdev/dumbflix-frontend`` untuk mengclone data aplikasi. setelah itu, lakukan ``$ npm install`` untuk menampilkan node_modules di folder dumwaysdev.<br/><br/>![1  npm install](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/0c067c36-df7c-40d1-949a-4cd73c42e47f)<br/><br/>
- Selanjutnya lakukan ``$ npm run build`` fungsinya untuk mengikat aplikasinya. <br/><br/>![2](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/e7edb977-113e-4c5c-8bbe-06de3c5f2696)<br/><br/>
- Lakukan perintah ``$ npm install -g pm2`` bila sebelumnya belum ada PM2.<br/><br/>![3  npm install -g pm2](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/c2a436a5-b8ce-46f7-986e-0e0db92718e7)<br/><br/>
- Setelah install, lakukan penginstallan serve dengan command ``$ npm install -g serve``dan ``$ sudo snap install serve``<br/><br/>![4 npm install -g serve](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/52f290df-e4a5-4f45-8f17-4d49a24e68d1)<br/><br/>
- Kemudian jalankan aplikasi dengan ``$ pm2 serve build``<br/><br/>![5  pm2 serve build](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/1221e638-6c7d-489d-be78-62e6299b90c0)<br/><br/>
- Kita bisa liat bahwa aplikasi sudah berjalan di port 8080.<br/><br/>![6  port 8080](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/fb75274a-2e80-4483-8a95-d588753bea81)<br/><br/>
- Langsung akses IP:8080 di Web Browser untuk memastikan Aplikasi berjalan atau tidak.<br/><br/>![7  Akses aplikasi di Web](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/fd4820ca-a7b3-4595-b128-4d1dbf9db2d2)<br/><br/>

#### 3. buatlah konfigurasi reverse proxy!<br/>(Gunakan 2 server untuk memenuhi challenge, tidak wajib)

- Pertama masuk ke folder nginx ``$ cd /etc/nginx`` dan membuat folder ``$ sudo mkdir dumbways``<br/><br/>![1](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/0b61b1d4-01ac-43fa-b7f3-8b4a6998de50)<br/><br/>
- Dan buat folder ``$ sudo nano my-proxy.conf``<br/><br/>![2](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/b1be629d-a6a3-49cc-b708-90fb4d81f434)<br/><br/>
- Setelah masuk, masukkan konfigurasi :<br/><br/>![3](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/51073bd9-29f7-4baf-9a3f-ebd0d96afb79)<br/><br/>
  **Note**: pastikan port 8080 diganti dengan aplikasi yang digunakan
- Keluar dari folder dumbways, dan masuk ke file nginx dengan perintah ``$ sudo nano nginx.conf``<br/><br/>![4](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/13d6b9a0-a6f7-4e91-982b-ae001a0abc15)<br/><br/>
- Pergi ke bagian **include**, dan masukan lokasi dari direktori yang berisi konfigurasi yang sudah dibuat.<br/><br/>![5](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/bfe471d6-732c-4c40-a143-b5c51065930d)<br/><br/>
- Untuk mengecek konfigurasi dengan perintah ``$ sudo nginx -t``<br/><br/>![6](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/c9b3090d-2ecb-4f6a-9db0-f29f977f5050)<br/><br/>
- <br/><br/><br/><br/>


























