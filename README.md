# Task Web Server & Load Balancing

#### 1. Instalasi nginx melalui apt
- Pertama jalankan perintah ``$ sudo apt install nginx``<br/><br/>![1](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/f8ef96b7-c320-417c-bd68-bb81770af673)
<br/><br/> Nanti akan ada tampilan **Do you want to continue? [Y/n]** maka ketik "y" untuk melanjutkan installan.<br/><br/>
- Kedua bila sudah selesai penginstallan maka kita bisa mengecek nginx sudah terinstall apa belum. dengan perintah ``$ nginx -v``<br/><br/>![2](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/10f8b593-88f9-4b11-baf0-756a76b02d4b)<br/><br/>
- Setelah jalankan ``$ sudo systemctl enable nginx``, dan ``$ sudo systemctl start nginx``. dan kita bisa mengecek nginx berjalan atau tidak dengan perintah ``$ sudo systemctl status nginx``.<br/><br/>![4](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/dec1ab1d-ec92-44c6-84e1-2aefb9bda6df)<br/><br/>
- Terakhir akses Web browser dan ketik IP kalian. Bila tampil seperti berikut installan nginx berhasil.<br/><br/>![3](https://github.com/darblietz/devops17-dumbways--M-Yusuf-Haidar-Week-2-Web-Server-Load-Balancing/assets/98991080/27c79c5c-5e24-4109-a3b5-e462135a40d0)<br/><br/>







#### 2. menjalankan aplikasi dumbflix menggunakan PM2
#### 3. buatlah konfigurasi reverse proxy!<br/>(Gunakan 2 server untuk memenuhi challenge, tidak wajib)
