# Final_Work!
Задание 1 
Используя команду cat в терминале операционной системы Linux, создать два файла Домашние животные (заполнив файл собаками, кошками, хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и ослы), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя (Друзья человека).
![Задание 1](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/00d12fd1-b3dc-4ca5-b761-30a6913aeb44)
Задание 2 
Создать директорию, переместить файл туда.
![Задание 2](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/0ae672fd-9735-48cf-8da6-f2e466853589)
Задание 3 
Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.
![Задание 3-1](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/3d25518f-1831-4565-a4f8-20880c49801d)
![Задание 3-2](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/1c0d67b0-18a9-4da5-852e-d1237d8ee8fe)
![Задание 3-3](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/0262f38c-8243-49a0-aae2-ef0149f38518)
![Задание 3-4](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/1cc2e0f2-3b32-499d-b8b0-70beae97af0d)
Задание 4 
Установить и удалить deb-пакет с помощью dpkg.
![Задание 4](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/a1740213-7238-4aa7-a0d8-94031aba9506)
![Задание 4-1](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/a8ea6b1b-1677-4169-a027-b1784edda3ce)
Задание 5 находится в файле History_Comand


Задание 6 Нарисовать диаграмму, в которой есть класс родительский класс, домашние животные и вьючные животные, в составы которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут: Лошади, верблюды и ослы).
![Снимок экрана (30)](https://github.com/Anton-Kovalev-10/Final_Work/assets/119130095/3f44d14f-7b4f-4e32-8d8a-d58726c74be3)


Задание 7 В подключенном MySQL репозитории создать базу данных “Друзья человека”


CREATE DATABASE Human_friends;


Задание 8 Создать таблицы с иерархией из диаграммы в БД

USE Human_friends;  
CREATE TABLE animal_classes  
(  
	     Id INT AUTO_INCREMENT PRIMARY KEY,  
	     Class_name VARCHAR(20)  
);  

INSERT INTO animal_classes (Class_name)  
VALUES ('вьючные'),  
('домашние');  


CREATE TABLE packed_animals  
(  
	       Id INT AUTO_INCREMENT PRIMARY KEY,  
         Genus_name VARCHAR (20),  
         Class_id INT,  
         FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE  
);  

INSERT INTO packed_animals (Genus_name, Class_id)  
VALUES ('Лошади', 1),  
('Ослы', 1),  
('Верблюды', 1);  
    
CREATE TABLE home_animals  
(  
	  Id INT AUTO_INCREMENT PRIMARY KEY,  
    Genus_name VARCHAR (20),  
    Class_id INT,  
    FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE  
);  

INSERT INTO home_animals (Genus_name, Class_id)  
VALUES ('Кошки', 2),  
('Собаки', 2),  
('Хомяки', 2);  

CREATE TABLE cats  
(  
    Id INT AUTO_INCREMENT PRIMARY KEY,  
    Name VARCHAR(20),  
    Birthday DATE,  
    Commands VARCHAR(50),  
    Genus_id int,  
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE  
);  


Задание 9 Заполнить низкоуровневые таблицы именами(животных), командами которые они выполняют и датами рождения


INSERT INTO cats (Name, Birthday, Commands, Genus_id)
VALUES ('Пупа', '2011-01-01', 'кс-кс-кс', 1),
('Олег', '2016-01-01', "отставить!", 1),  
('Тьма', '2017-01-01', "", 1); 

CREATE TABLE dogs 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO dogs (Name, Birthday, Commands, Genus_id)
VALUES ('Дик', '2020-01-01', 'ко мне, лежать, лапу, голос', 2),
('Граф', '2021-06-12', "сидеть, лежать, лапу", 2),  
('Шарик', '2018-05-01', "сидеть, лежать, лапу, след, фас", 2), 
('Босс', '2021-05-10', "сидеть, лежать, фу, место", 2);

CREATE TABLE hamsters 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO hamsters (Name, Birthday, Commands, Genus_id)
VALUES ('Малой', '2020-10-12', '', 3),
('Медведь', '2021-03-12', "атака сверху", 3),  
('Ниндзя', '2022-07-11', NULL, 3), 
('Бурый', '2022-05-10', NULL, 3);

CREATE TABLE horses 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO horses (Name, Birthday, Commands, Genus_id)
VALUES ('Гром', '2020-01-12', 'бегом, шагом', 1),
('Закат', '2017-03-12', "бегом, шагом, хоп", 1),  
('Байкал', '2016-07-12', "бегом, шагом, хоп, брр", 1), 
('Молния', '2020-11-10', "бегом, шагом, хоп", 1);

CREATE TABLE donkeys 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO donkeys (Name, Birthday, Commands, Genus_id)
VALUES ('Первый', '2019-04-10', NULL, 2),
('Второй', '2020-03-12', "", 2),  
('Третий', '2021-07-12', "", 2), 
('Четвертый', '2022-12-10', NULL, 2);

CREATE TABLE camels 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO camels (Name, Birthday, Commands, Genus_id)
VALUES ('Горбатый', '2022-04-10', 'вернись', 3),
('Самец', '2019-03-12', "остановись", 3),  
('Сифон', '2015-07-12', "повернись", 3), 
('Борода', '2022-12-10', "улыбнись", 3);


Задание 10
Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.


SET SQL_SAFE_UPDATES = 0;
DELETE FROM camels;

SELECT Name, Birthday, Commands FROM horses
UNION SELECT  Name, Birthday, Commands FROM donkeys;


Задание 11 Создать новую таблицу “молодые животные” в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью до месяца подсчитать возраст животных в новой таблице


CREATE TEMPORARY TABLE animals AS 
SELECT *, 'Лошади' as genus FROM horses
UNION SELECT *, 'Ослы' AS genus FROM donkeys
UNION SELECT *, 'Собаки' AS genus FROM dogs
UNION SELECT *, 'Кошки' AS genus FROM cats
UNION SELECT *, 'Хомяки' AS genus FROM hamsters;

CREATE TABLE yang_animal AS
SELECT Name, Birthday, Commands, genus, TIMESTAMPDIFF(MONTH, Birthday, CURDATE()) AS Age_in_month
FROM animals WHERE Birthday BETWEEN ADDDATE(curdate(), INTERVAL -3 YEAR) AND ADDDATE(CURDATE(), INTERVAL -1 YEAR);
 
SELECT * FROM yang_animal;


Задание 12 Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам.


SELECT h.Name, h.Birthday, h.Commands, pa.Genus_name, ya.Age_in_month 
FROM horses h
LEFT JOIN yang_animal ya ON ya.Name = h.Name
LEFT JOIN packed_animals pa ON pa.Id = h.Genus_id
UNION 
SELECT d.Name, d.Birthday, d.Commands, pa.Genus_name, ya.Age_in_month 
FROM donkeys d 
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN packed_animals pa ON pa.Id = d.Genus_id
UNION
SELECT c.Name, c.Birthday, c.Commands, ha.Genus_name, ya.Age_in_month 
FROM cats c
LEFT JOIN yang_animal ya ON ya.Name = c.Name
LEFT JOIN home_animals ha ON ha.Id = c.Genus_id
UNION
SELECT d.Name, d.Birthday, d.Commands, ha.Genus_name, ya.Age_in_month 
FROM dogs d
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN home_animals ha ON ha.Id = d.Genus_id
UNION
SELECT hm.Name, hm.Birthday, hm.Commands, ha.Genus_name, ya.Age_in_month 
FROM hamsters hm
LEFT JOIN yang_animal ya ON ya.Name = hm.Name
LEFT JOIN home_animals ha ON ha.Id = hm.Genus_id;
