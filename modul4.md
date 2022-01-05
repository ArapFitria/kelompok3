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

  ![13](https://user-images.githubusercontent.com/92453574/148256810-6cae00d2-ea9b-4caf-9242-d71ec1ee2fbf.PNG)

  

- xx

  ![14](https://user-images.githubusercontent.com/92453574/148256822-77a227de-0164-4d5e-908f-b5651a668afe.PNG)
  

- x

  ![15](https://user-images.githubusercontent.com/92453574/148256825-10a0e105-bf04-4ee2-8026-ab67388d45dc.PNG)

  

- x

  ![16](https://user-images.githubusercontent.com/92453574/148256828-52569a85-0e0a-43ae-9e14-bce121e627d8.PNG)

  

- x

  ![17](https://user-images.githubusercontent.com/92453574/148256833-4af698d8-996b-4fd1-b6ed-116dbab2cd5c.PNG)

  

- s

  ![18](https://user-images.githubusercontent.com/92453574/148256837-e85f69e8-e415-4906-a562-1e26f0ed93c5.PNG)

  

- s

  ![19](https://user-images.githubusercontent.com/92453574/148256846-284c1f4c-3f91-4484-80e8-94212fb98aef.PNG)

  

- s

  ![20](https://user-images.githubusercontent.com/92453574/148256850-733dae1e-3e21-419e-9d77-232cf2968a5a.PNG)

  

- x

  ![21](https://user-images.githubusercontent.com/92453574/148256855-5ae882e0-e81d-4c4f-ae3f-6a03db1fe894.PNG)

  

- xx

  ![22](https://user-images.githubusercontent.com/92453574/148256866-cd4aaf10-5ff2-460b-9e51-13c4d9798aa9.PNG)

  

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
