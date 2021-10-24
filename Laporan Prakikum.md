## Laporan Prakikum

###### Kelompok 3 

###### Annisa Aulia Arafah		 (1202190038)

###### Fitria Rahma Wulandari  (1202190045)



1. Rename ubuntu_php5.6 menjadi ubuntu_landing

`sudo lxc-copy -R ubuntu_php5.6 name -N ubuntu_landing`

2. Cek apakah container tersebut sudah ter-rename

   `lxc-ls -f`

   ![1](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\1.PNG)

3. mulai dan masuk ke ubuntu_landing

   ```
   sudo lxc-start -n ubuntu_landing
   
   sudo lxc-attach -n ubuntu_landing
   ```

4. Ganti IP

   `nano /etc/network/interfaces` ![4](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\4.PNG)

   

   

5. Cek IP, sudah ganti atau belum

`ifconfig`

![5](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\5.PNG)

6. Keluar dari ubuntu_landing

   `exit`

7. Install lxc debian 9 dengan nama debian_php5.6

   `sudo lxc-create -n debian_php5.6 -t download -- --dist debian --release stretch --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org`

   

8. Cek container

   `Sudo lxc-ls -f` 

![3](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\3.PNG)

**DEBIAN_PHP5.6**

1. Install net tools

   `Apt install nano net-tools curl -y`

2. Setting IP

   `nano /etc/network/interfaces`

   ![6](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\6.PNG)

3. Cek IP, sudah berubah atau belum

   `ifconfig`

   ![7](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\7.PNG)

4. NGINX

   ​	a.    nstall nginx

   `apt install nginx nginx-extras -y`

   ​	b.    Setting nginx (1)

   `cd /etc/nginx/sites-available`

   `touch lxc_php5.6.dev`

   `nano lxc_php5.6.dev`

   ![8](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\8.PNG)

   

   ​	c.    Setting nginx (2)

   ```
   cd ../sites-enabled
   ln -s /etc/nginx/sites-available/lxc_php5.6.dev .
   nginx -t
   nginx -s reload
   ```

5. Setting host

   ```
   nano /etc/hosts
   ```

   ![9](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\9.PNG)

6. Setting index

   ```
   cd /var/www/html
   mkdir lxc_php5.6
   cp index.nginx-debian.html lxc_php5.6/index.html
   cd /lxc_php5.6
   nano index.html
   ```

   ![10](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\10.PNG)

   

7. Curl

   ```
   curl -i http://lxc_php5.dev 
   ```

   

**UBUNTU_LANDING**

1. NGINX

   a. Setting nginx(1)

   `cd /etc/nginx/sites-available`

   `touch lxc_php5.6.dev`

   `nano lxc_php5.6.dev`

   ![11](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\11.PNG)

   b. Setting nginx(2)

   `cd ../sites-enabled`
   `ln -s /etc/nginx/sites-available/lxc_php5.6.dev .`
   `nginx -t`
   `nginx -s reload`

2. Setting index

   `cd /var/www/html/lxc_php5.6/`

   `nano index.html`

   ![12](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\12.PNG)

3. Curl

   ```
   curl -i http://lxc_landing.dev 
   ```

4. Auto start

`echo "lxc.start.auto=1">> /var/lib/lxc/ubuntu_landing/config`



**VM LOCAL**

1. Setting host

   ```
   sudo nano /etc/hosts
   ```

   ![13](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\13.PNG)

2. Start container ubuntu_landing, Debian_php5.6, ubuntu_php7.4

   `sudo lxc-start -n ubuntu_php7.4`

   `sudo lxc-start -n debian_php5.6`

   

3. NGINX

   a. Setting nginx(1)

   ```
   cd /etc/nginx/sites-available
   sudo nano vm.local
   ```

   ![14](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\14.PNG)

   b. Setting nginx(2)

   ```
   sudo ln -s /etc/nginx/sites-available/vm.local .
   sudo nginx -t
   sudo nginx -s reload
   ```

   C. Curl

```
curl -i http://vm.local/php5
curl -i http://vm.local/app
curl -i http://vm.local/blog
```

**HASIL**

1. Buka di google

   a. vm.local

   ![15](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\15.PNG)

   b. vm.local/app

   ![16](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\16.PNG)

   c. vm.local/blog

   ![17](D:\KULIAH\.tugas kuliah\sem 5\AdSer\sas1\sas1\17.PNG)



​	