use  DB2024
--Creating Patients table and adding Inputs
Create table Patients (patient_id int, first_name varchar(30), last_name varchar(30),gender char(1),birth_date  DATE ,city varchar(30),
province_id char(2), allergies varchar(80), height decimal(3,0) ,weight decimal (4,0))
Insert into Patients values(1,'Donald','Waterfield', 'M', '1963-02-12', 'Barrie','ON', NULL, 156,65)
Insert into Patients values(2,'Mickey','Baasha', 'M', '1981-05-28', 'Dundas','ON', 'Sulfa', 185,76)
Insert into Patients values(3,'Jiji','Sharma', 'M', '1957-09-05', 'Hamilton','ON', 'Penicillin', 194,106)
Insert into Patients values(4,'Blair','Diaz', 'M', '1967-01-07', 'Hamilton','ON', NULL, 191,104)
Insert into Patients values(5,'Charles','Wolfe', 'M', '2017-11-19', 'Orillia','ON', 'Penicillin', 47,10)
Insert into Patients values(6,'Sue','Falcon','F', '2017-09-30','	Ajax','ON','Penicillin',43,5)
Insert into Patients values(7,'Thomas','ONeill','M', '1993-01-31','	Burlington','ON',NULL,180,117)
Insert into Patients values(8,'Sonny','Beckett','M', '1952-12-11','	Port Hawkesbury','NS',NULL,174,105)
Insert into Patients values(9,'Sister','Spitzer','F', '1966-10-15','	Toronto','ON','Penicillin',	173,95)
Insert into Patients values(10,'Cedric','Coltrane','M', '1961-11-10','	Toronto','ON',NULL,	157,61)
Insert into Patients values(11,'Sara','	di Marco','F', '1949-04-29','	Hamilton','ON',NULL,	145,46)
Insert into Patients values(12,'Daphne','	Seabright','F', '1954-11-18','	Ancaster','ON','Codeine',	146,77)
Insert into Patients values(13,'Rick','	Bennett','M', '1977-01-27','	Ancaster','ON','Penicillin',	220,95)
Insert into Patients values(14,'Amy','	Leela','F', '1977-06-25','	Hamilton','ON',Null,172,72)
Insert into Patients values(15,'Woody','	Bashir','M', '1951-11-15','	Barrie','ON','Penicillin',153,59)
Insert into Patients values(16,'Tom','	Halliwell','M', '1987-08-01','	Hamilton','ON','Ragweed',179,114)
Insert into Patients values(17,'Rachel','	Winterbourne','F', '1966-04-26','	Hamilton','ON',NULL,163,95)
Insert into Patients values(18,'John','	West','M', '1961-06-19','	Oakville','ON',NULL,138,61)
Insert into Patients values(19,'Jon','	Doggett','M', '1951-12-25','	Hamilton','ON',NULL,194,116)
Insert into Patients values(20,'Angel','	Edwards','F', '1975-08-22	','	Brantford	','ON',NULL,176,106)
Insert into Patients values(21,'Brodie','	Beck','F', '1975-08-01	','	Carlisle	','ON',NULL,157,66)
Insert into Patients values(22,'Beanie','	Foster','F', '1998-11-22	','	Ancaster	','ON','Sulfa',157,75)




Select * from Patients

select patient_id , COUNT(*) AS Occurances
from Patients
Group By patient_id
HAVING COUNT(*)> 1;
/* this will delete the duplicate value with no original data*
PARTITION BY name = the column(s) you consider for duplicates

rn > 1 = keeps the first row and deletes the rest/


DELETE FROM Patients
WHERE patient_id IN (
    SELECT patient_id FROM (
        SELECT patient_id,
               ROW_NUMBER() OVER (PARTITION BY patient_id ORDER BY patient_id) AS rn
        FROM Patients
    ) AS t
    WHERE rn > 1
);

Create table admissions (patient_id int, 	admission_date date,	discharge_date date,diagnosis varchar(80),	attending_doctor_id int)
insert into admissions values(1, '2018-11-06','2018-11-08','Ovarian Dermoid-Cyct',21)
insert into admissions values(1,'2018-09-20','2018-09-20','Ineffective Breathin Pattern R/T Fluid Accumulatio',24)
insert into admissions values (3,'2019-01-24	','2019-01-29	','Cardiac Arrest	',2),
	(3,'2018-10-21','2018-10-27	','Congestive Heart Failure	',8),
	(6,'2018-06-13	','2018-06-15	','Asthma Exacerbation	',3),
	(6,'2018-11-08','2018-11-09	','Uterine Fibroid	',22),
(7,'2018-06-24	','2018-07-03	','Cancer',8),
(8,'2018-09-18','	2018-09-21	','Amigima',6),
(9,'2019-03-02','		2019-03-09	','Osteoarthritis',8),
(9,'	2018-12-31','		2018-12-31	','Ruptured Appendicitis',19),
(10,'2018-12-30','2019-01-05	','Zenkers Diverticulitis',14),
(10,'2019-02-27','2019-02-27','	Lower Quadrant Pain',27),
(11,'2018-12-14','2018-12-16	','Prostatectomy',15),
(12,'2019-04-27	','2019-05-04','Cerebral Aneurysm Rupture',21),
(13,'2019-04-28		','	2019-05-01','Renal Failure',1),
(15,'	2018-10-01','	2018-10-05','Hiatal Hernia',5),
(16,'	2019-01-10','2019-01-14	','Pyloric Obstruction',	6),
(16,'		2019-04-04','	2019-04-13	','Schizophrenic Disorder',	12),
(17,'2019-03-04','	2019-03-04	','Diabetes Mellitus',	9),
(17,'2018-12-12','		2018-12-14	','	Fractured Femur',	2),
(18,'2018-07-02','		2018-07-05	','	Spinal Infection',	3),
Select * from admissions;

Create table doctors(	doctor_id int, 	first_name varchar(80),	last_name varchar (80),specialty varchar(80))
insert into doctors (	doctor_id, 	first_name ,	last_name ,specialty )
values(1,'	Claude',	'Walls','	Internist'),
	(2,'	Joshua','Green','Cardiologist'),
	(3,'Miriam','Tregre','General Surgeon'),
	(4,'James','Russo','Obstetrician/Gynecologist'),
	(5,'Scott','Hill','Gastroenterologist'),
	(6,'Tasha','Phillips','Psychiatrist'),
	(7,'Hazel','Patterson','Oncologist'),
	(8,'Mickey','Duval','Pediatrician'),
	(9,'Jon','Nelson','Neurologist'),
	(10,'Monica','Singleton','Orthopaedic Surgeon'),
	(11,'Douglas','Brooks','Respirologist'),
	(12,'Flora','Moore','Cardiovascular Surgeon'),
	(13,'Angelica','Noe','Nuclear Medicine'),
	(14,'Tyrone','Smart','Gerontologist'),
	(15,'Marie','Brinkman','Urologist'),
	(16,'Irene','Brooks','Gastroenterologist'),
	(17,'Mary','Walker','Nuclear Medicine'),
	(18,'Bobbi','Estrada','Gerontologist'),
	(19,'Stephanie','Cohen','Oncologist'),
	(20,'Ralph','Wilson','General Surgeon'),
	(21,'Lisa','Cuddy','Obstetrician/Gynecologist'),
	(22,'Simon','Santiago','Cardiologist');


Select * from doctors

create table province_names (province_id char(2),province_name varchar(50))
insert into province_names (province_id,province_name)
values('AB','Alberta'),
	insert into province_names (province_id,province_name)
values ('BC','British Columbia'),
	('MB', 'Manitoba'),
	('NB', 'New Brunswick'),
	('NL','Newfoundland and Labrador'),
	('NT','Northwest Territories'),
	('NS','Nova Scotia'),
	('NU','Nunavut'),
	('ON ', 'Ontario'),
	('PE','Prince Edward Island'),
	('QC','Quebec'),
	('SK','Saskatchewan'),
	('YT','Yukon');
	select * from province_names

	/*Show unique birth years from patients and order them by ascending*/

	/* first name of patients that start with the letter 'C'*/

	Select first_name from patients where first_name LIKE 'C%';

	/*Show first name, last name, and the full province name of each patient*/

Select first_name, last_name, province_name from Patients

JOIN  province_names

/*CONCATINATE query-Show first name and last name concatinated into one column to show their full name*/

SELECT first_name, last_name, CONCAT (first_name,' ',last_name) as Full_name from Patients;
ON Patients.province_id = province_names.province_id

Select * from Patients
