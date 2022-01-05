Modul 4

Annisa Aulia Arafah (1202190038)

Fitria Rahma Wulandari (1202190045)

---

1. Apply loadbalancer for /blog and /app with conditions
   i. /blog using least_conn
   ii. /app uses ip hash
   iii. it is recommended to use ansible for installation
2. Use apache Jmeter to analyze the difference between /, /app, /blog with loadbalancer and without loadbalancer on traffic of 50, 100 and 150 users. Analysis in terms of time only. Write testing and analysis steps in your own language.

---

- For each container, make 2 copies 

  ![1](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\1.PNG)

  

- Start each container

  ![2](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\2.PNG)

  

- Change the IP address to 10.0.3.111 in ubuntu_php7.4_2 and change IP Address to 10.0.3.123 in ubuntu_php7.4_3

  ![3](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\3.PNG)

  

- Go to etc/hosts to register lxc_php7_2.dev

  ![5](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\5.PNG)

  

- Change the server name

  ![6](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\6.PNG)

  

- Restart nginx and make curl. then start all container

  ![7](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\7.PNG)

- xx

  ![8](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\8.PNG)

  

- xx

  ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\9.PNG)

  

- xx

  ![10](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\10.PNG)

  

- xx

  ![9](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\11.PNG)

  

- xx

  ![12](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\12.PNG)

  

- xx

  ![13](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\13.PNG)

  

- xx

  ![14](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\14.PNG)

  

- x

  ![15](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\15.PNG)

  

- x

  ![16](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\16.PNG)

  

- x

  ![17](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\17.PNG)

  

- s

  ![18](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\18.PNG)

  

- s

  ![19](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\19.PNG)

  

- s

  ![20](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\20.PNG)

  

- x

  ![21](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\21.PNG)

  

- xx

  ![22](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\22.PNG)

  

- Run the jmeter. Change the number from 50,100, 150

  ![23](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\23.PNG)

  ![24](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\24.PNG)

  ![25](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\25.PNG)

  ![26](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\26.PNG)

  ![27](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\27.PNG)

  ![28](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\28.PNG)

  ![29](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\29.PNG)

  ![30](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\30.PNG)![31](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\31.PNG)

  ![32](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\32.PNG)

  ![33](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\33.PNG)

  ![34](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\34.PNG)

  

- Go back to VM and go to

  ```
  /etc/nginx/sites-available/vm.local
  ```

  

- Add upstream landing, php5, and php7

  ![35](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\35.PNG)

  

- Go back to jmeter and redo

  ![36](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\36.PNG)

  ![37](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\37.PNG)

  ![38](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\38.PNG)

  ![39](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\39.PNG)

  ![40](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\40.PNG)

  ![41](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\41.PNG)

  ![42](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\42.PNG)

  ![43](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\43.PNG)

  ![44](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\44.PNG)

  ![45](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\45.PNG)

  ![46](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\46.PNG)

  ![47](D:\KULIAH\.tugas kuliah\sem 5\SAS\modul 4\47.PNG)

  

Analysis

xxx isien rap xxx