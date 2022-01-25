# Bibliothéque
- Developer : Abdennour Kerboub
- Contact : abdennour.kerboub@gmil.com

MYSQL a été utilisé pour la base de données dans ce projet. Il contient 4 tableaux :-

  - Livre : Cette table contient des champs comme ISBN, Titre, Auteur, Quantité et Prix.
    
   - Admin : cette table contient des champs tels que User_id et Password.
    
   - Étudiant : ce tableau contient des champs tels que Student_ID, Name, Course, Branch et Year.
  
   - Enregistrement : ce tableau contient des champs tels que Return_Date, ISBN, Student_id et Issue_Date.

Configuration de MYSQL :-
 
Créer toutes les tables au préalable


	Création de la base de données
---------------------
 CREATE DATABASE library_management_system;

    USE library_management_system;
---------------------


	Créer une table de livre
---------------------
CREATE TABLE Book(ISBN int primary key, Title varchar(20) not null, Author varchar(20) not null, Price int default 0, Quantity int default 0,CHECK (Price>=0),CHECK (Quantity>=0));
---------------------


	Créer une table d'étudiants
---------------------
 CREATE TABLE Student(SID int primary key, Name varchar(20) not null, Course varchar(20) not null, Branch varchar(20) not null, Email varchar(30) not null );
---------------------


	Créer une table Issue_Book
---------------------
CREATE TABLE Issue_Book (ISBN int, SID int,IssueDate date not null, foreign key Fk1(ISBN) references Book(ISBN),foreign key Fk2(SID) references Student(SID) ); 
---------------------


	Créer une table Return_Book
---------------------
CREATE TABLE Return_Book (SID int,ISBN int, ReturnDate date not null, foreign key Fk1(SID) references Student(SID),foreign key Fk2(ISBN) references Book(ISBN) );
---------------------


	Record Table
---------------------
CREATE TABLE Record (SID int, ISBN int, IssueDate date default null, ReturnDate date default null,foreign key Fk1(SID) references Student(SID), foreign key Fk2(ISBN) references Book(ISBN) ); 
---------------------
