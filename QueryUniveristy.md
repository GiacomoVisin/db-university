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


# Da quanti dipartimenti è composta l'università? (12)
- SELECT COUNT(id) FROM `departments` as `n.departments`;


# Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
- SELECT * FROM `teachers` WHERE phone IS NULL;


## Query con Grup by


# Contare quanti iscritti ci sono stati ogni anno
- SELECT YEAR(enrolment_date) AS anno, COUNT(id) AS totale_iscritti 
FROM `students`
GROUP BY YEAR(enrolment_date) 
ORDER BY anno ;


# Contare gli insegnanti che hanno l'ufficio nello stesso edificio
- SELECT office_address AS Address, COUNT(id) AS Teachers
FROM `teachers`
GROUP BY office_address; 


# Calcolare la media dei voti di ogni appello d'esame
- SELECT exam_id as Exam, ROUND(AVG(vote)) AS Media
FROM `exam_student`
group by exam_id 