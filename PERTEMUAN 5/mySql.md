# membuat database mysql di aws ec2

1. aktifkan instances

2. remote SSH via terminal 
    - Masuk ke FOLDER penyimpanan Privet key
    - Masuka komn (ssh - i nama file.pem ubuntu@[ip_addres])
    - enter

3. lakuka patching os
    - sudo apt-get update && sudo apt-get upgrade

4. kita lakukan mariaDB
    - sudo apt-get install mariadb-server
    - sudo systemctl start mariadb
    - sudo systemctl enable mariadb
    - sudo systemctl status mariadb
    - coba apakah default setting yg berlaku ( sudo mysql -u root -p )
    - cek apakah masih ada data dummy (show databases;)
![alt text](image.png)
![alt text](image-1.png)

5. kita lakukan hardening security
    - masukkan comand ( sudo mysql_secure_installation)
    - masukkan password akun kuat untuk user 
    - Remove anonymous users(Y)
    - disallow root login remotely (Y)
    - remove test database and acces to it(Y)
    reload privilage (Y)
    ![alt text](image-2.png)
    ![alt text](image-3.png)

6. membuat database dan user
    - membuat database untuk web company profile (Create database dbCompro;)
    - membuat user untuk web company profile (create user 'userCompro'@'localhost' identified by 'passwordCompro';)
    - memberikan hak akses user untuk web company profile (grant all privileges on dbCompro.* to 'usercompro'@'localhost';)()
    - flus pprivilage (flush privilage;)
    - keluar exit
    ![alt text](image-5.png)
    ![alt text](image-6.png)

7. login sebagai user baru
    - masuukan command (mysql -u userCompro -p)
    - masukkan password
    - cek apakah database db compro ada(show databases;)
    ![alt text](image-7.png)
