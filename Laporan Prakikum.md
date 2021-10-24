## Laporan Prakikum

###### Kelompok 3 

###### Annisa Aulia Arafah		 (1202190038)

###### Fitria Rahma Wulandari  (1202190045)



1. Rename ubuntu_php5.6 to ubuntu_landing

   ```
   sudo lxc-copy -R ubuntu_php5.6 name -N ubuntu_landing
   ```

2. Check if the container has been renamed

   ```
   lxc-ls -f
   ```
   ![1](https://user-images.githubusercontent.com/92453574/138603435-4e467f41-3a8c-454d-9ca9-60b6c296e7b4.PNG)

3. start and go to ubuntu_landing

   ```
   sudo lxc-start -n ubuntu_landing
   
   sudo lxc-attach -n ubuntu_landing
   ```

4. Change the IP

   ```
   nano /etc/network/interfaces
   ``` 
   ![4](https://user-images.githubusercontent.com/92453574/138603479-83b9907c-9a57-4d66-99a6-c17745c5daac.PNG)
   

5. Check the IP, has it change or not

   ```
   ifconfig
   ```
   ![5](https://user-images.githubusercontent.com/92453574/138603480-00fa71a4-9f3b-4535-891b-12cc5cf2cfce.PNG)

6. Exit ubuntu_landing

   ```
   exit
   ```

7. Install lxc debian 9 with the name debian_php5.6

   ```
   sudo lxc-create -n debian_php5.6 -t download -- --dist debian --release stretch --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
   ```

8. Check the container

   ```
   sudo lxc-ls -f
   ``` 
   ![3](https://user-images.githubusercontent.com/92453574/138603474-566e03c2-c9f8-4ffa-8746-c6cec2830738.PNG)


**DEBIAN_PHP5.6**

1. Install net tools

   ```
   apt install nano net-tools curl -y
   ```

2. Setting IP

   ```
   nano /etc/network/interfaces
   ```

   ![6](https://user-images.githubusercontent.com/92453574/138603482-2c55f0f2-1b09-4d19-82a1-8cdc66a0ef97.PNG)

3. Check the IP, has it changed or not

   ```
   ifconfig
   ```
   ![7](https://user-images.githubusercontent.com/92453574/138603483-1e1a7bfc-6be3-465e-8f07-07472b1bed7c.PNG)
  
4. NGINX

   ​	a.    Install nginx

      ```
      apt install nginx nginx-extras -y
      ```

   ​	b.    Setting nginx (1)

      ```
      cd /etc/nginx/sites-available
      touch lxc_php5.6.dev
      nano lxc_php5.6.dev
      ```
      
      ![8](https://user-images.githubusercontent.com/92453574/138603486-49fade2c-e7d4-432c-8bce-b02dabee58ec.PNG)

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

   ![9](https://user-images.githubusercontent.com/92453574/138603489-19512389-9c76-4558-bf83-60eb868e6181.PNG)

6. Setting index

   ```
   cd /var/www/html
   mkdir lxc_php5.6
   cp index.nginx-debian.html lxc_php5.6/index.html
   cd /lxc_php5.6
   nano index.html
   ```
   ![10](https://user-images.githubusercontent.com/92453574/138603490-b2d51be0-2062-42b3-bcda-87fa6f52afb1.PNG)

7. Curl

   ```
   curl -i http://lxc_php5.dev 
   ```

**UBUNTU_LANDING**

1. NGINX

   a. Setting nginx(1)

      ```
      cd /etc/nginx/sites-available
      touch lxc_php5.6.dev
      nano lxc_php5.6.dev
      ```

      ![11](https://user-images.githubusercontent.com/92453574/138603491-b4385ec0-4dd6-4a0e-a4e1-cd9396426928.PNG)

   b. Setting nginx(2)

      ```
      cd ../sites-enabled
      ln -s /etc/nginx/sites-available/lxc_php5.6.dev .
      nginx -t
      nginx -s reload
      ```

2. Setting index

   ```
   cd /var/www/html/lxc_php5.6/
   nano index.html
   ```

   ![12](https://user-images.githubusercontent.com/92453574/138603495-4b93cbbf-2623-44e8-bc88-1c564c05f547.PNG)

3. Curl

   ```
   curl -i http://lxc_landing.dev 
   ```

4. Auto start

   ```
   echo "lxc.start.auto=1">> /var/lib/lxc/ubuntu_landing/config
   ```

**VM LOCAL**

1. Setting host

   ```
   sudo nano /etc/hosts
   ```

   ![13](https://user-images.githubusercontent.com/92453574/138603497-8f2c8ad6-768b-4ae0-86fe-5f4f2283b6c2.PNG)

2. Start container ubuntu_landing, Debian_php5.6, ubuntu_php7.4

   ```
   sudo lxc-start -n ubuntu_php7.4
   sudo lxc-start -n debian_php5.6
   ```

3. NGINX

   a. Setting nginx(1)

      ```
      cd /etc/nginx/sites-available
      sudo nano vm.local
      ```

      ![14](https://user-images.githubusercontent.com/92453574/138603499-67fda872-56f6-4c67-8ef7-462aec75fbfe.PNG)

   b. Setting nginx(2)

      ```
      sudo ln -s /etc/nginx/sites-available/vm.local .
      sudo nginx -t
      sudo nginx -s reload
      ```

   c. Curl

      ```
      curl -i http://vm.local/php5
      curl -i http://vm.local/app
      curl -i http://vm.local/blog
      ```

**RESULT**

1. Open on google
   a. vm.local
      ![15](https://user-images.githubusercontent.com/92453574/138604625-4418ee9e-81b5-48a2-a959-dca97a7ac76e.PNG)

   b. vm.local/app
      ![16](https://user-images.githubusercontent.com/92453574/138603502-e347bcb5-b63c-4e35-ba37-b44d5c467129.PNG)

   c. vm.local/blog
      ![17](https://user-images.githubusercontent.com/92453574/138603504-38f8ead1-9d93-4a93-96dc-1b88470eef95.PNG)

