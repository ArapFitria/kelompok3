**Laporan Modul 2**

- Annisa Aulia Arafah (1202190038)
- Fitria Rahma Wulandari (1202190045)

---

1. **Rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)**

   - menghapus container ubuntu_landing sebelum membuat container baru dengan nama yang sama 
     ```
     lxc-destroy ubuntu_landing
     ```
     ![1](https://user-images.githubusercontent.com/92453574/144299793-22ddbd42-a752-4268-b40b-23cd31f9c8d7.PNG)

     

   - buat container lxc ubuntu versi focal baru 
     ```
     lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```
     ![2](https://user-images.githubusercontent.com/92453574/144299802-f10d438b-f41a-42cd-8f01-eeb676754808.PNG)

     

     ```
     lxc-start -n ubuntu_landing
     
     lxc-attach -n ubuntu_landing
     ```
     ![3](https://user-images.githubusercontent.com/92453574/144299805-3cb0e406-65d4-4b6f-9fd2-05cb1fcf0b60.PNG)

     

   - konfigurasi IP static di dalam nano
     ```
     nano /etc/netplan/00-installer-config.yaml
     ```
     ![4](https://user-images.githubusercontent.com/92453574/144299807-4d3625e1-48d4-4b92-930f-b2863a3ecb25.PNG)

     

     ```
     netplan apply
     ```
     ![5](https://user-images.githubusercontent.com/92453574/144299808-cc2fbc0e-cf7e-4863-b4ea-1bed6a731e6d.PNG)
     ![6](https://user-images.githubusercontent.com/92453574/144299813-bb286b3c-745d-4a57-82f6-86075067581c.PNG)

     

   - kemudian install open ssh server 
     ```
     apt-get install openssh-server -y
     ```
     ![7](https://user-images.githubusercontent.com/92453574/144299818-73d1a254-5279-4502-8c23-d3fb80390a17.PNG)

     
   
   - lalu lakukan konfigurasi ssh
     ```
     nano /etc/ssh/sshd_config
     ```
     ![8](https://user-images.githubusercontent.com/92453574/144299822-7b5d916f-222c-40fb-a064-fffcb377d6cb.PNG)
     
     
     
   - buat password baru
     ```
     service sshd restart
   
     passwd
     ```
     ![9](https://user-images.githubusercontent.com/92453574/144299824-67afcd67-710a-4acf-a47d-9b528582b324.PNG)
     
     
     
   - cek ssh 
     ```
     ssh root@10.0.3.103
     ```
   
     ![10](https://user-images.githubusercontent.com/92453574/144299827-8eaab05a-75be-477f-8004-217886bf5548.PNG)
     
     





2. **Rubah LXC php7 dengan ubuntu focal (destroy n create, same ip, same name)**

   - menghapus container ubuntu php 7.4

     `lxc-destroy ubuntu_php7.4 -f`

     ![](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no2\no2\1.PNG)

     

   - buat container lxc ubuntu versi focal 

     `sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org`

     ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\2.PNG)

     

     `lxc-start -n ubuntu_php7.4`

     `lxc-attach -n ubuntu_php7.4`

     `apt-get install nano net-tools curl`

     ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\3.PNG)

     

   - konfigurasi menjadi IP statik 

     `sudo nano /etc/netplan/10-lxc.yaml`

     ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\4.PNG)

     

     `netplan apply`

     ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\5.PNG)

     ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\6.PNG)

     

   - kemudian install open ssh server 

     `apt-get install openssh-server -y`

     ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\\modul 2\no2\no2\7.PNG)

     

   - lalu lakukan konfigurasi ssh
   
     `nano /etc/ssh/sshd_config`
   
     ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no2\no2\8.PNG)
   
     
   
     - buat password baru
     
       `service sshd restart`
     
       `passwd`
     
       ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no2\no2\9.PNG)
     
       
     
     - cek ssh 
     
       `ssh root@10.0.3.103`
     
       ![10](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no2\no2\10.PNG)
     
     
     
     

3. **vm.local/**

   - masuk ansible untuk install laravel

     cd ~/ansible/
     mkdir laravel
     cd laravel/
     nano host

     ![1](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\1.PNG)

     

   - membuat host untuk lxc

     nano host

     ubuntu_landing ansible_host=lxc_landing.dev ansible_ssh_user=root ansible_become_pass=1234

     ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\2.PNG)

     

   - buat direktori yang akan dijalankan pada folder php dam install di nginxphp.yml

     - hosts: all
       become : yes
       tasks:
         - name: install nginx nginx extras
           apt:
            pkg:
              - nginx
              - nginx-extras
            state: latest
         - name: start nginx
           service:
            name: nginx
            state: started
         - name: menginstall tools
           apt:
            pkg:
              - curl
              - software-properties-common
              - unzip
            state: latest
              - name: "Repo PHP 7.4"
            apt_repository:
              repo="ppa:ondrej/php"
         - name: "Updating the repo"
           apt: update_cache=yes
         - name: Installation PHP 7.4
           apt: name=php7.4 state=present
         - name: install php untuk laravel
           apt:
            pkg:
               - php7.4-fpm
                   - php7.4-mysql
                   - php7.4-mbstring
                   - php7.4-xml
                   - php7.4-bcmath
                   - php7.4-json
                   - php7.4-zip
                   - php7.4-common
                        state: present

     ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\3.PNG)

     

   - instalasi

     `ansible-playbook -y hosts nginxphp.yml -k`

     ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\4.PNG)

     

   - buat folder installcomposer.yml

     -hosts: all
       become : yes
       tasks:

        - name: Download and install Composer
          shell: curl -sS https://getcomposer.org/installer | php
          args:
           chdir: /usr/src/
           creates: /usr/local/bin/composer
           warn: false
        - name: Add Composer to global path
          copy:
           dest: /usr/local/bin/composer
           group: root
           mode: '0755'
           owner: root
           src: /usr/src/composer.phar
           remote_src: yes
        - name: Composer create project
          become_user: root
          composer:
           command: create-project
           arguments: laravel/laravel landing 
           working_dir: /var/www/html
           prefer_dist: yes
          environment:
             COMPOSER_NO_INTERACTION: "1"
        - name: mengkopi file .env.example jadi .env
          copy:
           dest: /var/www/html/landing/.env.example
           src: /var/www/html/landing/.env
           remote_src: yes
        - name: mengganti konfigurasi .env
          lineinfile:
           path: /var/www/html/landing/.env
           regexp: "{{ item.regexp }}"
           line: "{{ item.line }}"
           backrefs: yes
          loop:
           - { regexp: '^(.*)DB_HOST(.*)$', line: 'DB_HOST=10.0.3.200' }
           - { regexp: '^(.*)DB_DATABASE(.*)$', line: 'DB_DATABASE=landing' }
           - { regexp: '^(.*)DB_USERNAME(.*)$', line: 'DB_USERNAME=admin' }
           - { regexp: '^(.*)DB_PASSWORD(.*)$', line: 'DB_PASSWORD= ' }
           - { regexp: '^(.*)APP_URL(.*)$', line: 'APP_URL=http://vm.local' }
           - { regexp: '^(.*)APP_NAME=(.*)$', line: 'APP_NAME=landing' }
        - name: Composer install ke landing
          composer:
            command: install
            working_dir: /var/www/html/landing
          environment:
            COMPOSER_NO_INTERACTION: "1"
        - name: generate php artisan
          args:
           chdir: /var/www/html/landing
          shell: php artisan key:generate
        - name: mengganti permission storage
          file:
           path: /var/www/html/landing/storage
           mode: 0777
           recurse: yes

     ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\5.PNG)

     

   - instalasi

     `ansible-playbook -y hosts nginxphp.yml -k`

     ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\6.PNG)

     

   - mengatur lxc_landing.dev

     server {
             listen 80;

             root /var/www/html/landing/public;
             index index.php index.html index.htm;
             server_name lxc_landing.dev;
         
             error_log /var/log/nginx/landing_error.log;
             access_log /var/log/nginx/landing_access.log;
         
             client_max_body_size 100M;
             location / {
                     try_files $uri $uri/ /index.php$args;
             }
             location ~\.php$ {
                     include snippets/fastcgi-php.conf;
                     fastcgi_pass unix:run/php/php7.4-fpm.sock;
                     fastcgi_param SCRIPTFILENAME $document_root$fastcgi_script_name;
             }
     }

     ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\7.PNG)

     

   - buat folder config.yml

   - 

   - ---
     - hosts: all
       become : yes
       vars:
         domain: 'lxc_landing.dev'
       tasks:
        - name: stop apache2
          service:
           name: apache2
           state: stopped
           enabled: no
        - name: Write {{ domain }} to /etc/hosts
          lineinfile:
           dest: /etc/hosts
           regexp: '.*{{ domain }}$'
           line: "127.0.0.1 {{ domain }}"
           state: present
        - name: ensure nginx is at the latest version
          apt: name=nginx state=latest
        - name: start nginx
          service:
           name: nginx
           state: started
        - name: copy the nginx config file 
          copy:
           src: ~/ansible/laravel/lxc_landing.dev
           dest: /etc/nginx/sites-available/lxc_landing.dev
        - name: Symlink lxc_landing.dev
          command: ln -sfn /etc/nginx/sites-available/lxc_landing.dev /etc/nginx/sites-enabled/lxc_landing.dev
          args:
           warn: false
        - name: restart nginx
          service:
           name: nginx
           state: restarted
        - name: restart php7
          service:
           name: php7.4-fpm
           state: restarted
        - name: curl web
          command: curl -i http://lxc_landing.dev
          args:
           warn: false

     ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\8.PNG)

     

   - instalasi

     ansible-playbook -y hosts config.yml -k

     ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\9.PNG)

     

   - buka vm.local untuj mengecek keberhasilan instalasi

     ![10](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no3\no3\10.PNG)

     berhasil



4. **vm.local/blog**

   - masuk ansible untuk install laravel

     cd ~/ansible/
     mkdir wordoress/
     cd wordpress/

     ![1](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\1.PNG)

     

   - membuat host untuk lxc

     nano host

     ubuntu_php7.4 ansible_host=lxc_php7.dev ansible_ssh_user=root ansible_become_pass=1234

     ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\2.PNG)

     

   - buat direktori untuk tasks

     ---
     - hosts: all
       vars:
         domain: 'lxc_php7.dev'
       tasks:
        - name: delete apt chache
          become: yes
          become_user: root
          become_method: su
          command: rm -vf /var/lib/apt/lists/*

        - name: install requirement
          become: yes
          become_user: root
          become_method: su
          apt: name={{ item }} state=latest update_cache=true
          with_items:
           - nginx
           - nginx-extras
           - curl
           - wget
           - php7.4
           - php7.4-fpm
           - php7.4-curl
           - php7.4-xml
           - php7.4-gd
           - php7.4-opcache
           - php7.4-mbstring
           - php7.4-zip
           - php7.4-json
           - php7.4-cli
           - php7.4-mysqlnd
           - php7.4-xmlrpc
           - php7.4-curl

        - name: wget wordpress
          shell: wget -c http://wordpress.org/latest.tar.gz

        - name: tar latest.tar.gz
          shell: tar -xvzf latest.tar.gz

        - name: copy folder wordpress
          shell: cp -R wordpress /var/www/html/blog

        - name: chmod
          become: yes
          become_user: root
          become_method: su
          command: chmod 775 -R /var/www/html/blog/

        - name: copy .wp-config.conf
          copy:
           src=~/ansible/wordpress/wp.conf
           dest=/var/www/html/blog/wp-config.php

        - name: copy wordpress.conf
          copy:
           src=~/ansible/wordpress/wordpress.conf
           dest=/etc/nginx/sites-available/{{ domain }}
          vars:
           servername: '{{ domain }}'

        - name: Symlink wordpress.conf
          command: ln -sfn /etc/nginx/sites-available/{{ domain }} /etc/nginx/sites-enabled/{{ domain }}
       
        - name: restart nginx
          become: yes
          become_user: root
          become_method: su
          action: service name=nginx state=restarted

        - name: Write {{ domain }} to /etc/hosts
          lineinfile:
           dest: /etc/hosts
           regexp: '.*{{ domain }}$'
           line: "127.0.0.1 {{ domain }}"
           state: present

        - name: enable module php mbstring
          command: phpenmod mbstring

        - name: restart php
          become: yes
          become_user: root
          become_method: su
          action: service name=php7.4-fpm state=restarted

        - name: restart nginx
          become: yes
          become_user: root
          become_method: su
          action: service name=nginx state=restarted

     ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\3.PNG)

     

   - masuk pada template wp.conf

     <?php
     /**
      * The base configuration for WordPress
      *
      * The wp-config.php creation script uses this file during the installation.
      * You don't have to use the web site, you can copy this file to "wp-config.php"
      * and fill in the values.
      *
      * This file contains the following configurations:
      *
      * * MySQL settings
      * * Secret keys
      * * Database table prefix
      * * ABSPATH
      *
      * @link https://wordpress.org/support/article/editing-wp-config-php/
      *
      * @package WordPress
      */

     define( 'WP_HOME', 'http://vm.local/blog' );
     define( 'WP_SITEURL', 'http://vm.local/blog' );

     // ** MySQL settings - You can get this info from your web host ** //
     /** The name of the database for WordPress */
     define( 'DB_NAME', 'blog' );

     /** MySQL database username */
     define( 'DB_USER', 'admin' );

     /** MySQL database password */
     define( 'DB_PASSWORD', 'SysAdminSas0102' );

     /** MySQL hostname */
     define( 'DB_HOST', '10.0.3.200:3306' );

     /** Database charset to use in creating database tables. */
     define( 'DB_CHARSET', 'utf8' );

     /** The database collate type. Don't change this if in doubt. */
     define( 'DB_COLLATE', '' );

     /**#@+
      * Authentication unique keys and salts.
      *
      * Change these to different unique phrases! You can generate these using
      * the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-key service}.
      *
      * You can change these at any point in time to invalidate all existing cookies.
      * This will force all users to have to log in again.
      *
      * @since 2.6.0
      */
      define( 'AUTH_KEY',         'put your unique phrase here' );
      define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
      define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
      define( 'NONCE_KEY',        'put your unique phrase here' );
      define( 'AUTH_SALT',        'put your unique phrase here' );
      define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
      define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
      define( 'NONCE_SALT',       'put your unique phrase here' );

     /**#@-*/

     /**
      * WordPress database table prefix.
      *
      * You can have multiple installations in one database if you give each
      * a unique prefix. Only numbers, letters, and underscores please!
      */
      $table_prefix = 'wp_';

     /**
      * For developers: WordPress debugging mode.
      *
      * Change this to true to enable the display of notices during development.
      * It is strongly recommended that plugin and theme developers use WP_DEBUG
      * in their development environments.
      *
      * For information on other constants that can be used for debugging,
      * visit the documentation.
      *
      * @link https://wordpress.org/support/article/debugging-in-wordpress/
      */
      define( 'WP_DEBUG', false );

     /* Add any custom values between this line and the "stop editing" line. */

     

     /* That's all, stop editing! Happy publishing. */

     /** Absolute path to the WordPress directory. */
     if ( ! defined( 'ABSPATH' ) ) {
             define( 'ABSPATH', __DIR__ . '/' );
     }

     /** Sets up WordPress vars and included files. */
     require_once ABSPATH . 'wp-settings.php';

     ![4](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\4.PNG)

     

   - masuk template wordpress.conf

     server {
          listen 80;
          listen [::]:80;

          # Log files for Debugging
          access_log /var/log/nginx/wordpress-access.log;
          error_log /var/log/nginx/wordpress-error.log;
         
          # Webroot Directory for Laravel project
          root /var/www/html/blog;
          index index.php index.html index.htm;
         
          # Your  Name
          server_name lxc_php7.dev;
         
          location / {
                  try_files $uri $uri/ /index.php?$query_string;
          }
         
          # PHP-FPM Configuration Nginx
          location ~ \.php$ {
                  try_files $uri =404;
                  fastcgi_split_path_info ^(.+\.php)(/.+)$;
                  fastcgi_pass unix:/run/php/php7.4-fpm.sock;
                  fastcgi_index index.php;
                  fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                  include fastcgi_params;
          }
     }

     ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\5.PNG)

     

   - jalankan ansible untuk menginstall

     sudo ansible-playbook -i hosts install-wp.yml -k

     ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\6.PNG)

     

   - buka vm.local/blog/ untuk mengecek

     ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\7.png)

   - 

     ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\8.png)

     

     ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\9.png)

     

     ![10](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 2\no4\no4\10.png)

     berhasil























