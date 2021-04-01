# IcesiHelath

This is an application of elective devops in University Icesi that actually I'm working with it. This app was developed in jaavscript.

Context:
The multinational MyHealth is a company in the health sector with a presence in the country for the last thirty years. Throughout this time, it has managed to consolidate and retain a large patient base (patients are the organization's clients and number approximately one hundred and fifty thousand). In parallel with the growth of its customers, the company has had to evolve the IT solutions that support critical business processes.
This application has two foldes: backend and frontend.

MyHealth has stored the records of its patients in a SQL database connected to a BackEnd developed in Java. As it has had to face the multiple challenges posed by the management and service of such a large customer base, it has not been able to update it and the BackEnd has been operating relatively stable and invariably for the last few years with a monolithic architecture. Also, the business rules of have been written in Java.

An application, called Icesi-Health, has been developed, an interface for a patient record system. In it, the user interface is programmed using open source libraries of JavaScript, CSS and HTML5
Canvas. The application is made up of: a frontend, a backend and a database. The user interface (front end) and API (back end) are served by a Node.JS Express server. Additionally, the database is served by a NoSQL database named CouchDB. For now, Icesi-Health has evolved its old business rules written in Java, and under a monolithic architecture, to a microservice architecture deployed in Node.Js

the application containers were created using docker:

DOCKER FILE:

I created dockerfile for each folder.

First, I created dockerfile for backend

Frist I define of base that is builder project
Second, I create directory where the code wiill be hosted in container
third,dependencias are installed.
fourth, run npm install
five, copy all of files to container
six, expose container in port 8089
seven,configure commands that container will run.

![Captura de pantalla de 2021-03-31 22-49-09](https://user-images.githubusercontent.com/43484703/113240995-6d71c900-9273-11eb-9be4-46c257bb35be.png)

After, I created dokcerfile for frontend except number port for expose.

![Captura de pantalla de 2021-03-31 22-51-12](https://user-images.githubusercontent.com/43484703/113241125-a873fc80-9273-11eb-8c91-2c67616deae2.png)


Aditionally, I created a docker-compose.yml file to orchestra.te the containers and run the app.

First, I use version 3.8 of yml
Second I define services; I created three services, there are containers back-c(this will be container for backend), front-c(this will be container for backend) and db(container for databse).

On service back-c:
The image that this service will use is sereme98/backend2, serem98 is my user of dockerhub and backend2 is image on my repository.
I declare the ports where the backend will run, these are 8089:8089.
I declare environment variables of application on bakecnd: This is DATABASE_URL
and this serivices depends container db.

On service front-c
The image that this service will use is sereme98/frontend2.
I declare the ports where the backend will run, these are 8080:8080.
I declare environment variables of application on frontend: These are BACKEND_HOST and API_URL.
and this serivices depends container back-c

Finally
TI declare image, the name of the image  is sereme98/couchb-icesi.
I declare the ports where the db will run, these are 5984:5984.
I declare variables environment ,these are COUCHDB_USER and COUCHDB_PASSWORD.

![Captura de pantalla de 2021-03-31 23-01-08](https://user-images.githubusercontent.com/43484703/113241835-17058a00-9275-11eb-9337-450b4df44301.png)

After, I run applciations with container use next commands:
$ docker-compose up -d 

![Captura de pantalla de 2021-03-31 23-14-10](https://user-images.githubusercontent.com/43484703/113242604-fa6a5180-9276-11eb-9020-f95600dc3414.png)

And... I verify that the application is working correctly

Checking database in backend:

![Captura de pantalla de 2021-03-31 23-57-19](https://user-images.githubusercontent.com/43484703/113245621-efb2bb00-927c-11eb-8b9e-42cbf79b99da.png)

Cheking couchdb running

![Captura de pantalla de 2021-03-31 23-59-22](https://user-images.githubusercontent.com/43484703/113245757-356f8380-927d-11eb-88a4-46d45d1451e1.png)

Cheking Front end and connection of backend
User: opall
password: opall

![Captura de pantalla de 2021-04-01 00-01-54](https://user-images.githubusercontent.com/43484703/113245923-8da68580-927d-11eb-8b4f-910aad71218f.png)


![Captura de pantalla de 2021-04-01 00-00-37](https://user-images.githubusercontent.com/43484703/113245840-63ed5e80-927d-11eb-93c0-e2133ebf38d2.png)

the application works but it has a bug, I have to make a modification in the docker-compose in the back-c service modifying the environment variable. I am working to fix that ebug




