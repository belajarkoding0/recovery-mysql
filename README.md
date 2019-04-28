# recovery-mysql
recovery password root mysql

Pertama-tama silakan masuk ke dalam system operasi Ubuntu anda dan matikan service database mysql dengan menjalankan perintah:

 sudo service mysql stop


kemudian lihat statusnya apakah service mysql server sudah berhenti dengan menjalankan perintah:

 sudo service mysql status


jika berhasil, maka akan terlihat seperti di tampilan di bawah ini:



setelah itu, silakan jalankan layanan mysql server pada mode safe dengan opsi --skip-grant-tables sehingga perintahnya terlihat 
seperti pada gambar di bawah ini:

 sudo mysqld_safe --skip-grant-tables


jika berhasil dijalankan maka akan terlihat log nya seperti pada tampilan di bawah ini:


setelah itu, silakan masuk ke mysql server melalui screen yang lain (menggunakan CTRL + ALT F2 atau bisa membuka koneksi baru 
untuk masuk ke dalam server) lalu jalankan perintah:

 mysql -u root -p


silakan enter tanpa memasukkan password apapun, maka anda akan masuk ke dalam shell mysql sebagai root, seperti yang terlihat 
pada gambar di bawah ini:

silakan gunakan database mysql dengan menjalankan perintah:

 use mysql;


kemudian jalankan update password dengan perintah:

 UPDATE `user` SET `authentication_string` = PASSWORD('masukkan password anda di antara tanda petik disini') WHERE `user`='root';


kemudian jalankan perintah:

 FLUSH PRIVILEGES;


kemudian silakan keluar dari shell mysql dengan perintah:

 quit;


langkah-langkah di atas yang barusan dijalankan akan terlihat seperti pada tampilan di bawah jika tidak ada pesan error yang 
keluar:



setelah itu, silakan matikan PID (Process ID) yang menjalankan service server mysql pada safe mode melalui perintah kill, 
dengan sebelumnya menjalankan perintah:

 ps aux |grep mysql


untuk melihat PID-nya kemudian jalankan perintahdengan format:

 sudo kill -9 


perintah "ps aux |grep mysql" di komputer saya menghasilkan output seperti pada gambar di bawah ini:




dari situ saya mendapatkan PID mysql server sebanyak 3 buah yaitu 17327, 17328 dan 17701 lalu saya menjalankan perintah:

 sudo kill -9 17327 17328 17701



setelah itu saya menjalankan perintah untuk mengaktifkan kembali layanan mysql server dengan perintah:

 sudo service mysql start


jangan lupa setelah itu silakan lihat statusnya dengan menjalankan perintah:

 sudo service mysql status


apabila service mysql server telah aktif akan keluar output tampilan seperti pada gambar di bawah ini:



setelah itu silakan coba kembali masuk ke dalam shell mysql server dengan perintah:

 mysql -u root -p


masukkan password baru yang tadi telah masukkan, dan hasilnya anda akan masuk ke dalam shell mysql server dengan password baru 
seperti yang terlihat pada gambar di bawah ini:


mudah bukan melakukan recovery password mysql server, silakan mencoba dan jangan sampai lupa lagi ya.
Terima kasih telah berkunjung dan semoga membantu.
