# Project Title

Welcome to the [Your Project Name] repository! This project utilizes XAMPP for local development and includes guidelines on setting up XAMPP and editing PHP files.

## Getting Started

### Prerequisites

Before you begin, make sure you have the following installed on your machine:

- XAMPP: [Download and Install XAMPP](https://www.apachefriends.org/index.html)

## Start XAMPP:

- Open XAMPP and start the MySql server.

![image](https://github.com/minhfarm/ComputingDesignProject/assets/125583435/d5998d58-3910-43d3-823d-d56f3146b94e)

### Access the phpMyadmin:

- Open your web browser and go to https://www.phpmyadmin.net/).

## Set up the database
1. Create databases:

   ```sql
   CREATE DATABASE IF NOT EXISTS test_dtb DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci;
   USE test_dtb;

2. Create Table in Database:

   ```sql
      SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
      START TRANSACTION;
      SET time_zone = "+07:00";
   
   
   
      CREATE TABLE user_info (
        id int(11) NOT NULL,
        username varchar(255) NOT NULL,
        password varchar(255) NOT NULL,
        firstname varchar(255) NOT NULL,
        lastname varchar(255) NOT NULL,
        age TinyInt NOT NULL,
        gender char(1) NOT NULL,
        accountrole TinyText NOT NULL,
        academiclevel TinyText NOT NULL
      );
   
      CREATE TABLE user_contact (
        id int(11) NOT NULL,
        userID int(11) NOT NULL,
        mail varchar(255) NOT NULL,
        phone varchar(12) NOT NULL,
        social_media_link varchar(255) NOT NULL
      );
   
   CREATE TABLE address (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     street varchar(255) NOT NULL,
     district varchar(255) NOT NULL,
     city varchar(255) NOT NULL,
     country varchar(255) NOT NULL,
     description varchar(255) NOT NULL
   );
   
   CREATE TABLE user_profile (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     userExperienceID int(11) NOT NULL,
     userExActivityID int(11) NOT NULL
   );
   
   CREATE TABLE user_experience (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     jobRole varchar(255) NOT NULL,
     timeRange varchar(255) NOT NULL,
     experienceLevel varchar(255) NOT NULL,
     company varchar(255) NOT NULL,
     workscope varchar(255) NOT NULL
   );
   
   CREATE TABLE user_ex_activity (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     jobRole varchar(255) NOT NULL,
     timeRange varchar(255) NOT NULL,
     organization varchar(255) NOT NULL,
     workscope varchar(255) NOT NULL
   );
   
   CREATE TABLE interviews (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     meetingLink varchar(255) DEFAULT NULL,
     status varchar(255) DEFAULT NULL
   );
   
   CREATE TABLE payment (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     jobID int(11) NOT NULL,
     bank varchar(255) NOT NULL,
     paymentMethod TinyText NOT NULL,
     cardNumber TinyText NOT NULL,
     typeOfCard TinyText NOT NULL,
     cardExpireDate date NOT NULL
   );
   
   CREATE TABLE courses (
     id int(11) NOT NULL,
     courseName varchar(255) NOT NULL,
     introduction varchar(255),
     length varchar(255) NOT NULL,
     outline varchar(255) NOT NULL ,
     provider varchar(255) NOT NULL,
     benefit varchar(255) NOT NULL
   );
   
   CREATE TABLE registered_courses (
     id int(11) NOT NULL,
     userID int(11) NOT NULL,
     courseID int(11) NOT NULL,
     dateOfRegistered date NOT NULL,
     status varchar(255) NOT NULL
   );
   
   CREATE TABLE jobs (
     id int(11) NOT NULL,
     title varchar(255) NOT NULL,
     salary decimal(10,2) NOT NULL,
     applicationDL date,
     location varchar(255),
     experiencRequirement varchar(255) NOT NULL,
     workScope varchar(255),
     CompanyID int(11) NOT NULL,
     workingFormat varchar(255),
     specialization varchar(255),
     benefits varchar(255) 
   );
   
   CREATE TABLE job_application (
     id int(11) NOT NULL,
     user_id int(11) NOT NULL,
     job_id int(11) NOT NULL,
     applicationDate datetime NOT NULL,
     status varchar(255) NOT NULL,
     cvResume varchar(255) NOT NULL,
     statementOfPurpose varchar(255) NOT NULL,
     supportExpectation varchar(255) NOT NULL,
     question varchar(255)
   );
   
   CREATE TABLE company (
     id int(11) NOT NULL,
     name varchar(255) NOT NULL,
     size  varchar(255) NOT NULL,
     email varchar(255) NOT NULL,
     phone_number varchar(12) NOT NULL,
     message varchar(255) DEFAULT NULL,
     shortDes varchar(255) DEFAULT NULL
   );
   
   ALTER TABLE user_info
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE user_contact
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE address
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE user_profile
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE user_experience
   
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE user_ex_activity
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE interviews
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE payment
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE courses
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE registered_courses
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE jobs
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE job_application
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
   
   ALTER TABLE company
     ADD PRIMARY KEY (id),
     MODIFY id int(11) NOT NULL AUTO_INCREMENT;
After write this code in it should looks like this 
![image](https://github.com/minhfarm/ComputingDesignProject/assets/125583435/581608f0-ca01-42ac-998a-51032805096d)


### Some example of use cases:

We provide some intrustions for some commmon cases and the code for these cases:
- You should copy the code in the SQL in phpMyadmin
  ![image](https://github.com/minhfarm/ComputingDesignProject/assets/125583435/2de0b23f-cf5e-4472-9ad5-16cccf9bb33e)

1. Logging account 
   ```sql
   SELECT * FROM user
   WHERE username = 'username' AND password = 'userpassword';
2. See a user's job Application lists
   ```sql
   SELECT * FROM job_application
   WHERE userID = 1;
3. Job Search Engine case:
   ```sql
   SELECT * FROM jobs
   WHERE experience_requirement = 'None'
     AND salary >= 100000
     AND specialization = 'Computer Science'
   ORDER BY salary DESC; 
   ### Use a Code Editor:

## Contributing

If you'd like to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/new-feature`.
3. Make your changes and commit them: `git commit -m 'Add new feature'`.
4. Push to the branch: `git push origin feature/new-feature`.
5. Submit a pull request.

## License

This project is licensed under the Computing Boiz Team 

## Acknowledgments

- Thanks to the XAMPP and phpMyadmin team for providing a robust local development environment.
- Hat tip to anyone whose code was used.

Happy coding!
