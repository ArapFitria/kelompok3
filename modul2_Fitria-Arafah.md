Laporan Praktikum 3

- Annisa Aulia Arafah (1202190038)
- Fitria Rahma Wulandari (1202190045)

1. **Rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)**

   - menghapus container ubuntu_landing sebelum membuat container baru dengan nama yang sama 

     `lxc-destroy ubuntu_landing`

     ![](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\1.PNG)

     

   - buat container lxc ubuntu versi focal baru 

     `lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org`

     ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\2.PNG)

     

   - setelah itu, masuk ke dalam container

     ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\3.PNG)

     

   - konfigurasi IP static di dalam nano

     `nano /etc/netplan/00-installer-config.yaml`

     ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\4.PNG)

     ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\5.PNG)

     ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\6.PNG)

     

   - kemudian install open ssh server untuk media transfer data

     `apt-get install openssh-server -y`

     ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\7.PNG)

     

   - lalu lakukan konfigurasi ssh

     `nano /etc/ssh/sshd_config`

     ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no1\no1\8.PNG)





2. **Rubah LXC php7 dengan ubuntu focal (destroy n create, same ip, same name)**

   - menghapus container ubuntu php 7.4

     `lxc-destroy ubuntu_php7.4 -f`

     ![](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\1.PNG)

     

   - buat container lxc ubuntu versi focal 

     `sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org`

     ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\2.PNG)

     

   - masuk pada ubuntu php 7.4 dan ketik `apt-get install nano net-tools curl`

     ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\3.PNG)

     

   - konfigurasi menjadi IP statik pada nano

     `sudo nano /etc/netplan/10-lxc.yaml`

     ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\4.PNG)

     ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\5.PNG)

     ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\6.PNG)

     

   - kemudian install open ssh server untuk media transfer data

     `apt-get install openssh-server -y`

     ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\7.PNG)

     

   - lalu lakukan konfigurasi ssh

     `nano /etc/ssh/sshd_config`

     ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\prak 3\no2\no2\8.PNG)

     

     















