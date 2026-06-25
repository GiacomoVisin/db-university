## QUERIES WITH JOIN:

# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

- SELECT * 
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia"


# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

- SELECT *
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `department_id`
WHERE `departments`.`name` = "Dipartimento di Neuroscienze"


# Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

- SELECT *
FROM `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `course_teacher`.`teacher_id` = 44


# Selezionare tutti gli studenti con i dati relativi al corso di laurea a cuisono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

- SELECT * 
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`name` ASC, `students`.`surname` ASC;