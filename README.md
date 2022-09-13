# springtesters

requirements:
- Postgres (for database) Download Link: https://www.postgresql.org/download/
- IntelliJ IDEA CE (used in the tutorial below) Download Link: https://www.jetbrains.com/idea/download

Credits(This tutorial is followed): https://www.youtube.com/watch?v=9SGDpanrc8U&t=4844s

Setup Steps:
1. Create your Springboot project
    1. Go to https://start.spring.io/ (This is where you create the project)
    2. DO NOT CHANGE the default settings (except for the Project Metadata; but the Packaging and Java version should be unchanged)
    3. Add the following dependencies:
        - Spring Web (uses MVC; more info about MVC here: https://www.youtube.com/watch?v=DUg2SWWK18I)
        - MySQL Driver
        - Spring Data JPA
    4. Click "Generate". A zip file will be downloaded in your device. Extract the zip file
2. Postgre:
    1. After downloading Postgres in the link, start your Postgre server
    2. Open the postgres CLI by clicking on your main database
    3. in your CLI, type in the following: 
        - :EMOJICODE: CREATE DATABASE database_name; :EMOJICODE: (database_name is the name of your database)
        - :EMOJICODE: GRANT ALL PRIVILEGES ON DATABASE "database_name" TO admin_user :EMOJICODE:
    4. Type this in the same CLI as the previous step:  :EMOJICODE: \l :EMOJICODE: . You should see the changes being reflected
    5. Go to your Springboot project and search for the folder "application.properties"; inside this path: src --> main --> resources
        1. Add these lines in your file: (to configure your Postgre database)
            - spring.datasource.url=jdbc:postgresql://localhost:5432/database_name
            - spring.datasource.username=
            - spring.datasource.password=
            - spring.jpa.hibernate.ddl-auto=create-drop
            - spring.jpa.show-sql=true
            - spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQL82Dialect
            - spring.jpa.properties.hibernate=true

Folder Structure:

```bash
ProjectFolder
├── .idea (can ignore)
├──.mvn (dont touch this)
├── project_name (can ignore this)
├── src
|   ├── main
|       ├──package_name (the name of the package from the Springboot initialiser)
|           ├─-Entity (based on what you name ur entity)
|               ├──Entity
|               ├──EntityConfig
|               ├──EntityController (Determine API routes; which uses specific functions from the Service)
|               ├──EntityRepository (This provides basic crud operations which can be used by the Service; most of the essentials are inherited)
|               ├──EntityService (Basic CRUD operations which calls the methods from the Repository)
|               ├──DemoApplication (this name may vary; bascially like your main.js in JS frameworks)
|   ├── test (can ignore this)
├── target
|
... you can ignore the rest
        
```
        
