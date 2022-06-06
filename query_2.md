## QUERY GROUP BY

1. Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS "Numero_iscritti", YEAR(`enrolment_date`) AS "Anno"
FROM `students`
WHERE `enrolment_date`
GROUP BY YEAR(`enrolment_date`);

Numero_iscritti    Anno
  912              2018
  1709             2019
  1645             2020
  734              2021

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(`office_address`) AS "numero_insegnanti", `office_address` AS "Indirizzo"
FROM `teachers`
GROUP BY `office_address`;


3. Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`vote`) AS "Media_voti", `exam_id` AS "Numero_appello"
FROM `exam_student`
GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(`id`) AS "Numero_corsi_laurea", `department_id` AS "Numero_dipartimenti"
FROM `degrees`
GROUP BY `department_id`;



## QUERY JOIN

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.`name` AS `nome`, `students`.`surname` AS `cognome`, `degrees`.`name` AS `nome_dipartimento`
FROM `students` 
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";


2. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
SELECT `degrees`.`name` AS `corsi_di_laurea`, `departments`.`name` AS `nome_dipartimento`
FROM `degrees`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` LIKE "%Neuroscienze%"


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `teachers`.`surname` AS `cognome`, `teachers`.`name` AS `nome`, `courses`.`name` AS `nome_corso`
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `teachers`.`id` = 44;



4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT `students`.`surname` AS `cognome`, `students`.`name` AS `nome`, `degrees`.`name` AS `corso_laurea`, `departments`.`name` AS `nome_dipartimento` 
FROM `students`
JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname`, `students`.`name`;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT `degrees`.`name` AS `corso_laurea`, `courses`.`name` AS `nome_corso`, `teachers`.`surname` AS `cognome_insegnante`, `teachers`.`name` AS `nome_insegnante` 
FROM `degrees`
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`;


6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT `teachers`.`name` AS `nome_insegnante`, `teachers`.`surname` AS `cognome_insegnante`, `departments`.`name` AS `nome_dipartimento`
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'dipartimento di matematica';

