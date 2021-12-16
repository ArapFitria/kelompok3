### Praktikum Modul 3

Annisa Aulia Arafah    (1202190038)

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

  ![1](https://user-images.githubusercontent.com/92453574/146378288-8e2b8f69-c7fd-4be5-8858-6220afe467b4.PNG)

  

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

  ![2](https://user-images.githubusercontent.com/92453574/146378301-87660a93-79a5-4368-b270-de2666348afd.PNG)

  

- install packages

  ![3](https://user-images.githubusercontent.com/92453574/146378308-31087fa5-6153-43a8-8b02-603207ebc0b7.PNG)



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

  ![4](https://user-images.githubusercontent.com/92453574/146378313-06e3c534-c62d-4193-8c88-e01232e11171.PNG)

  

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

  ![5](https://user-images.githubusercontent.com/92453574/146378329-46c7ee8d-7443-4ff4-95eb-b7f433c42b8a.PNG)

  

- Add subdomain to /etc/hosts

  ![6](https://user-images.githubusercontent.com/92453574/146378334-f461583a-6fb9-459a-882f-97770a2836e9.PNG)



- Open vm.local

  ![7](https://user-images.githubusercontent.com/92453574/146378340-117b34df-f387-4a90-be85-fcc36653cd40.PNG)



- Add line www

  ![8](https://user-images.githubusercontent.com/92453574/146378347-88157153-31b2-455e-a98c-c7585211fb14.PNG)



- Exit lxc. then open and edit in vm.local

  ![9](https://user-images.githubusercontent.com/92453574/146378349-a9a72b0a-60b3-48ed-8fa4-c1acf9e4d9f1.PNG)



- Open and edit /etc/bind/vm/vm.local

  ![10](https://user-images.githubusercontent.com/92453574/146378356-61194ec6-6db1-4e69-8d0f-4c0010e3b529.PNG)



- Restart all

  ```
  service bind9 restart
  service nginx restart
  /etc/init.d/named restart
  ```

  ![11](https://user-images.githubusercontent.com/92453574/146378365-a2c0376b-1fd7-418f-acef-1be45715e18f.PNG)



- Open wifi setting. in menu IPv4, add DNS Server and uncheck automatic

  ![12](https://user-images.githubusercontent.com/92453574/146378371-a9a30336-c7c5-4b42-a1a2-60032c8039f5.PNG)



- Reconnecting the wifi, and open vm.local on browser

  ![13](https://user-images.githubusercontent.com/92453574/146378376-a652994e-8839-46ec-88a1-88717bafc1cd.PNG)





