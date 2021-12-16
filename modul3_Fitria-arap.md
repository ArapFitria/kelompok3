### Praktikum Modul 3

Annisa Aulia Arafah       (1202190038)

Fitria Rahma Wulandari (1202190045)

---

1. Create a subdomain dev.vm.local using ansible with some rules:
   i. Using ansible

   ii. using the same lxc used with vm.local

   iii. the code folder must be different from the one used by vm.local, use /var/www/html/dev/{app_name}

2. Register vm.local subdomain to DNS

---

- go to directory using ansible

  ```
  cd ~/ansible/laravel/
  ```

  ![1](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\1.PNG)

  

  ```
  ---
  - hosts: all
    become : yes
    tasks:
      - name: install bind9 dan dnsutils
        apt:
         pkg:
           - bind9
           - dnsutils
  ```

  ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\2.PNG)

  

- install packages

  ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\3.PNG)



- create config.yml

  ```
  ---
  - hosts: all
    become : yes
    tasks:
     - name: membuat direktori
       file:
        path: /var/www/html/dev/landing
        state: directory
     - name: copy file vm.local
       copy:
        src: /etc/bind/vm/vm.local
        dest: /var/www/html/dev/landing
     - name: mengganti konfigurasi
       replace:
        path: /var/www/html/dev/landing/vm.local
        regexp: 'www'
        replace: 'dev'
     - name: copy file named.conf.local
       copy:
        src: /etc/bind/named.conf.local
        dest: /etc/bind/named.conf.local
     - name: mengganti konfigurasi conf local
       replace:
        path: /etc/bind/named.conf.local
        regexp: '/etc/bind/vm/vm.local'
        replace: '/var/www/html/dev/landing/vm.local'
     - name: mengganti konfigurasi conf local part2
       replace:
        path: /etc/bind/named.conf.local
        regexp: '/etc/bind/vm/db.192'
        replace: '/var/www/html/dev/landing/db.192'
     - name: copy file db.192
       copy:
        src: /etc/bind/vm/db.192
        dest: /var/www/html/dev/landing
     - name: copy file resolv.conf
       copy:
        src: /etc/resolv.conf
        dest: /etc/resolv.conf
     - name: copy file named.conf.options
       copy:
        src: /etc/bind/named.conf.options
        dest: /etc/bind/named.conf.options
     - name: restart nginx
       service:
        name: nginx
        state: restarted
     - name: restart bind9
       action: service name=bind9 state=restarted
  ```

  ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\4.PNG)

  

- install using this script

  ```
  ---
  - hosts: all
    become : yes
    tasks:
     - name: membuat direktori
       file:
        path: /var/www/html/dev/landing
        state: directory
     - name: copy file vm.local
       copy:
        src: /etc/bind/vm/vm.local
        dest: /var/www/html/dev/landing
     - name: mengganti konfigurasi
       replace:
        path: /var/www/html/dev/landing/vm.local
        regexp: 'www'
        replace: 'dev'
     - name: copy file named.conf.local
       copy:
        src: /etc/bind/named.conf.local
        dest: /etc/bind/named.conf.local
     - name: mengganti konfigurasi conf local
       replace:
        path: /etc/bind/named.conf.local
        regexp: '/etc/bind/vm/vm.local'
        replace: '/var/www/html/dev/landing/vm.local'
     - name: mengganti konfigurasi conf local part2
       replace:
        path: /etc/bind/named.conf.local
        regexp: '/etc/bind/vm/115.168.192.in-addr.arpa'
        replace: '/var/www/html/dev/landing/115.168.192.in-addr.arpa'
     - name: copy file 115.168.192.in-addr.arpa
       copy:
        src: /etc/bind/vm/115.168.192.in-addr.arpa
        dest: /var/www/html/dev/landing
     - name: copy file resolv.conf
       copy:
        src: /etc/resolv.conf
        dest: /etc/resolv.conf
     - name: copy file named.conf.options
       copy:
        src: /etc/bind/named.conf.options
        dest: /etc/bind/named.conf.options
     - name: restart nginx
       service:
        name: nginx
        state: restarted
     - name: restart bind9
       action: service name=bind9 state=restarted
  ```

  ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\5.PNG)

  

- Add subdomain to /etc/hosts

  ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\6.PNG)



- Open vm.local

  ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\7.PNG)



- Add line www

  ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\8.PNG)



- Exit lxc. then open and edit in vm.local

  ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\9.PNG)



- Open and edit /etc/bind/vm/vm.local

  ![10](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\10.PNG)



- Restart all

  ```
  service bind9 restart
  service nginx restart
  /etc/init.d/named restart
  ```

  ![11](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\11.PNG)



- Open wifi setting. in menu IPv4, add DNS Server and uncheck automatic

  ![12](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\12.PNG)



- Reconnecting the wifi, and open vm.local on browser

  ![13](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 3\prak3\prak3\13.PNG)





