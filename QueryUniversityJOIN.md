## QUERIES WITH JOIN:

# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

- SELECT * 
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia"


# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

- SELECT *
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Neuroscienze";


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


# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

- SELECT * 
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;


# Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

- SELECT DISTINCT `teachers`.*
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Matematica"


# BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
# per ogni esame, stampando anche il voto massimo. Successivamente,
# filtrare i tentativi con voto minimo 18.

-  SELECT `students`.`surname` AS `student_surname`,
    `students`.`name` AS `student_name`,
    `exams`.`course_id` AS `course_id`,
    `courses`.`name` AS `course_name`,
    COUNT(`exam_student`.`exam_id`) AS `total_attempts`,
    MAX(`exam_student`.`vote`) AS `max_vote`
FROM `exam_student`
JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
GROUP BY `exam_student`.`student_id`, `exams`.`course_id`
HAVING MAX(`exam_student`.`vote`) >= 18;
