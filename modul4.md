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

  ![1](https://user-images.githubusercontent.com/92453574/148256371-b51204b9-7971-4edb-8ab8-dbe6c0223c64.PNG)

  

- Start each container

  ![2](https://user-images.githubusercontent.com/92453574/148256379-4f6de51e-b8e0-43ed-93e1-86dbcbd78b00.PNG)

  

- Change the IP address to 10.0.3.111 in ubuntu_php7.4_2 and change IP Address to 10.0.3.123 in ubuntu_php7.4_3

  ![3](https://user-images.githubusercontent.com/92453574/148256383-4ed9f83c-0fd2-4235-a3d9-1739226f733e.PNG)

  

- Go to etc/hosts to register lxc_php7_2.dev

  ![5](https://user-images.githubusercontent.com/92453574/148256391-1554aac7-2abd-47ab-a30b-8d7e6ddf69f4.PNG)

  

- Change the server name

  ![6](https://user-images.githubusercontent.com/92453574/148256397-fa168430-5032-47b6-a671-f739e4d6aebd.PNG)

  

- Restart nginx and make curl. then start all container

  ![7](https://user-images.githubusercontent.com/92453574/148256400-9df0671d-a2a4-4c2b-8719-622fed31ced4.PNG)

- xx

  ![8](https://user-images.githubusercontent.com/92453574/148256403-b388e3a0-9ae9-420e-a865-d1c2f473dd5e.PNG)

  

- xx

  ![9](https://user-images.githubusercontent.com/92453574/148256409-95b80c9a-1a20-4d16-82b3-9a5c59382c6f.PNG)

  

- xx

  ![10](https://user-images.githubusercontent.com/92453574/148256412-6d256292-a0d7-44a3-bf4c-fc175755819e.PNG)

  

- xx

  ![11](https://user-images.githubusercontent.com/92453574/148256415-c00fb359-ac6d-4042-a509-3e4156855f83.PNG)


  

- xx

  ![12](https://user-images.githubusercontent.com/92453574/148256359-e59c1ebe-169b-49ba-8016-e17a749a383a.PNG)

  

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
