## Query con Select

# Selezionare tutti gli studenti nati nel 1990 (160)
- SELECT * FROM `students` WHERE  year(date_of_birth) = 1990
  
- SELECT * FROM `students` WHERE date_of_birth >= '1990-01-01'
AND date_of_birth < '1991-01-01';


# Selezionare tutti i corsi che valgono più di 10 crediti (479)
- SELECT * FROM `courses` WHERE cfu > '10'


# Selezionare tutti gli studenti che hanno più di 30 anni
- SELECT * FROM `students` WHERE date_of_birth < CURRENT_DATE - INTERVAL '30' YEAR;


# Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
- SELECT * FROM `courses` WHERE period = 'I semestre' AND year = '1';


# Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
- SELECT * FROM `exams` WHERE hour > '14:00:00' AND date = '2020-06-20';


# Selezionare tutti i corsi di laurea magistrale (38)
- SELECT * FROM `degrees` WHERE name LIKE '%Magistrale%' ;
