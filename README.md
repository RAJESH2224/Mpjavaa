create database Final;
use Final;
create table Students(
Std_Id int primary key not null,
Std_name varchar(20) not null,
DOB date not null,
Gender char(1) not null default 'M',
Contact_num bigint not null unique,
Email_id varchar(50) not null unique,
Address varchar(100),
Date_of_joining date check(Date_of_joining>='2024-08-01') not null,
Room_Id int,
foreign key (Room_Id) references Rooms(Room_Id)
on delete cascade,
Status ENUM('active','inactive','graduated') default 'active'
);
insert into Students values (112,'Manoj','1998-01-03','M',9515571537,'manoj@gmail.com','Gachibowli,near le merdian,Hyderabad,Telangana,500032','2024-08-01',111,'graduated'),
(222,'Tanish','2000-02-03','M',9515571539,'tanish@gmail.com','Kukatpally,Hyderabad,Telangana,500032','2024-08-05',222,'active'),
(332,'Jaanvi','2001-03-03','F',9515571530,'janvi@gmail.com','Whitefields,Hyderabad,Telangana,500034','2024-08-03',333,'active');

create table Rooms(
Room_Id Int primary key,
Floor_no int not null,
Capacity int check(Capacity>0) not null,
Hostel_id int,
foreign key (Hostel_id) references Hostels(Hostel_id)
on delete cascade,
Status ENUM('occupied','vacant', 'under maintanence') default 'vacant'
);
insert into Rooms values (111,2,3,001,'vacant'), (222,3,3,002,'vacant'), (333,2,2,003,'vacant');



create table Hostels(
Hostel_id int primary key,
Hostel_name varchar(20) unique,
Location varchar(100) not null,
Total_rooms int check(Total_rooms!=0),
Warden_name varchar(20)
);
insert into hostels values(001,'Srinath mens hostel','CRR puram street 1, Srinath mens hostel, Ramapuram, Chennai',5,'Surya'),
(002,'Balaji mens hostel','CRR puram street 2, Balaji mens hostel, Ramapuram, Chennai',5,'Senthil'),
(003,'SKM mens hostel','CRR puram street 3, SKM mens hostel, Ramapuram, Chennai',3,'Naveen');




create table Staff(
Staff_id int primary key,
Staff_name varchar(20) not null,
Role_ long not null,
Contact_number bigint unique,
Email_id varchar(50) unique,
Hostel_id int,
foreign key (Hostel_id) references Hostels(Hostel_id)
on delete cascade
);
insert into Staff values(100,'Ram','sweeping',9989066832,'ram@gmail.com',001),
(200,'Sreenu','cooking',9989066833,'sreenu@gmail.com',002),
(300,'Sai','Maintanence',9989066834,'sai@gmail.com',003);


create table Facilities(
Facility_id int primary key,
Facility_name long not null,
Hostel_id int,
foreign key (Hostel_id) references Hostels(Hostel_id)
on delete cascade
);
insert into facilities values(101,'AC,Washing machine,Bed,Fridge',001),
(202,'AC,Washing machine,Bed,Fridge',002),
(303,'AC,Washing machine,Bed,Fridge',003);
