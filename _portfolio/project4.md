---
title: Building Databases with SQL
subtitle: For keeping track of my students at the Nashville Music School
image: assets/img/portfolio/04-full.jpg
alt: 

caption:
  title: Database Management
  subtitle: SQL, Database Management
  thumbnail: assets/img/portfolio/04-thumbnail.jpg
---

# 🎸 Nashville Music School's Student Database

This project contains an **SQL database** storing some of my students, their chosen **instruments**, and **years** of enrollment throughout the previous years. For data privacy purposes, this is a consolidated version of my database to showcase the minimal design, and not all of the confidential material.

``` sql
-- How I start my scripts
CREATE DATABASE NashvilleMusicSchoolDB;
USE NashvilleMusicSchoolDB;

-- Create the Students Table
CREATE TABLE Students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    year INT
);

-- Create the Instruments Table 
CREATE TABLE Instruments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT UNIQUE,  -- Ensures a student has only one instrument
    instrument VARCHAR(50),
    FOREIGN KEY (student_id) REFERENCES Students(id) ON DELETE CASCADE
);

-- Sort my Students by year
INSERT INTO Students (name, year) VALUES 
    ('Mosheh', 2016), ('Suleyman', 2016), ('Youssef', 2016), ('Emma', 2016),
    ('Nikola', 2016), ('Ronan', 2016), ('Louise', 2016), ('Daniel', 2016), 
    ('Matthew', 2016), ('Rory', 2016),
    ('Daniel', 2018), ('Youssef', 2018), ('Fabrice', 2018), ('Felix', 2018),
    ('Joana', 2018), ('Fred', 2018), ('Marko', 2018), ('Nikola', 2018),
    ('Alofa', 2018), ('Kihwan', 2018),
    ('Jonathan', 2019), ('Ochen', 2019), ('Apiyo', 2019), ('Ronan', 2019),
    ('Louise', 2019), ('Taina', 2019), ('Emma', 2019), ('Manon', 2019),
    ('Matthew', 2019), ('Lyka', 2019), ('Emma 2', 2019),
    ('Jonathan', 2020), ('Emma', 2020), ('Matthew', 2020), ('Tatiana', 2020),
    ('Manon', 2020), ('Nelly', 2020), ('Sara', 2020), ('Matheo', 2020),
    ('Naomi', 2020), ('George', 2020), ('Giorgio', 2020), ('Nihal', 2020),
    ('Scarlett', 2020), ('Didac', 2020), ('Joshua', 2020), ('Media', 2020),
    ('Patrick', 2020), ('Yann', 2020),
    ('Giorgio', 2023), ('Matheo', 2023), ('Giacomo', 2023), ('Didac', 2023),
    ('Theo', 2023), ('Theola', 2023), ('Steve', 2023), ('Lua', 2023),
    ('Rose', 2023), ('Zeb', 2023), ('Troy', 2023), ('Getsy', 2023),
    ('Olivera', 2023);

-- Match the instrument to the student
INSERT INTO Instruments (student_id, instrument)
VALUES 
    ((SELECT id FROM Students WHERE name='Mosheh' AND year=2016), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Suleyman' AND year=2016), 'Piano'),
    ((SELECT id FROM Students WHERE name='Youssef' AND year=2016), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Emma' AND year=2016), 'Bass'),
    ((SELECT id FROM Students WHERE name='Nikola' AND year=2016), 'Drums'),
    ((SELECT id FROM Students WHERE name='Ronan' AND year=2016), 'Drums'),
    ((SELECT id FROM Students WHERE name='Louise' AND year=2016), 'Piano'),
    ((SELECT id FROM Students WHERE name='Daniel' AND year=2016), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Matthew' AND year=2016), 'Piano'),
    ((SELECT id FROM Students WHERE name='Rory' AND year=2016), 'Drums'),
    
    ((SELECT id FROM Students WHERE name='Daniel' AND year=2018), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Youssef' AND year=2018), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Fabrice' AND year=2018), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Felix' AND year=2018), 'Drums'),
    ((SELECT id FROM Students WHERE name='Joana' AND year=2018), 'Drums'),
    ((SELECT id FROM Students WHERE name='Fred' AND year=2018), 'Drums'),
    ((SELECT id FROM Students WHERE name='Marko' AND year=2018), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Nikola' AND year=2018), 'Drums'),
    ((SELECT id FROM Students WHERE name='Alofa' AND year=2018), 'Drums'),
    ((SELECT id FROM Students WHERE name='Kihwan' AND year=2018), 'Guitar'),

    ((SELECT id FROM Students WHERE name='Jonathan' AND year=2019), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Ochen' AND year=2019), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Apiyo' AND year=2019), 'Drums'),
    ((SELECT id FROM Students WHERE name='Ronan' AND year=2019), 'Drums'),
    ((SELECT id FROM Students WHERE name='Louise' AND year=2019), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Taina' AND year=2019), 'Piano'),
    ((SELECT id FROM Students WHERE name='Emma' AND year=2019), 'Bass'),
    ((SELECT id FROM Students WHERE name='Manon' AND year=2019), 'Piano'),
    ((SELECT id FROM Students WHERE name='Matthew' AND year=2019), 'Piano'),
    ((SELECT id FROM Students WHERE name='Lyka' AND year=2019), 'Drums'),
    ((SELECT id FROM Students WHERE name='Emma 2' AND year=2019), 'Piano'),

    ((SELECT id FROM Students WHERE name='Jonathan' AND year=2020), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Emma' AND year=2020), 'Bass'),
    ((SELECT id FROM Students WHERE name='Matthew' AND year=2020), 'Piano'),
    ((SELECT id FROM Students WHERE name='Tatiana' AND year=2020), 'Piano'),
    ((SELECT id FROM Students WHERE name='Manon' AND year=2020), 'Piano'),
    ((SELECT id FROM Students WHERE name='Nelly' AND year=2020), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Sara' AND year=2020), 'Piano'),
    ((SELECT id FROM Students WHERE name='Matheo' AND year=2020), 'Guitar'),
    
    ((SELECT id FROM Students WHERE name='Giorgio' AND year=2023), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Matheo' AND year=2023), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Giacomo' AND year=2023), 'Guitar'),
    ((SELECT id FROM Students WHERE name='Didac' AND year=2023), 'Drums'),
    ((SELECT id FROM Students WHERE name='Theo' AND year=2023), 'Piano'),
    ((SELECT id FROM Students WHERE name='Theola' AND year=2023), 'Piano'),
    ((SELECT id FROM Students WHERE name='Steve' AND year=2023), 'Guitar');

-- Question which is the most popular instrument
SELECT instrument, COUNT(*) AS num_students
FROM Instruments
GROUP BY instrument
ORDER BY num_students DESC;

```

{:.list-inline}
- Date: October 2015+
- Database: Nashville Music School
- Category: SQL, Database Management

