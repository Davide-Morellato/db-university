## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT CONCAT(`students`.`name`,' ', `students`.`surname`) AS `total_students`, `degrees`.`name` FROM `students` INNER JOIN `degrees` ON `students`.`degree_id`=`degrees`.`id` WHERE `degrees`.`name`= 'Corso di Laurea in Economia';

<!-- OPPURE -->

SELECT CONCAT(`students`.`name`,' ', `students`.`surname`) AS `total_students`, `degrees`.`name` FROM `students` INNER JOIN `degrees` ON `students`.`degree_id`=`degrees`.`id` WHERE `degrees`.`name`LIKE '%__Laurea in Economia';

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `departments`.`name` AS `department_name`, `degrees`.`level` AS `degrees_level`  FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` LIKE '%__Neuroscienze';

<!-- OPPURE -->

SELECT `departments`.`name` AS `department_name`, `degrees`.`name` AS `degrees_name` FROM `degrees` INNER JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`name` LIKE '%__Magistrale__%' AND `departments`.`name` LIKE '%__di Neuroscienze';

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id`=`teachers`.`id` WHERE `teachers`.`name` = 'Fulvio' AND `teachers`.`surname` = 'Amato';

<!-- OPPURE -->

SELECT * FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id`=`teachers`.`id` WHERE `teachers`.`id` = 44;

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT * FROM `students` INNER JOIN `degrees` ON `students`.`degree_id`=`degrees`.`id` INNER JOIN `departments` ON `degrees`.`department_id`=`departments`.`id` ORDER BY `students`.`surname`, `students`.`name`;

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT * FROM `degrees` INNER JOIN `courses` ON `degrees`.`id`=`courses`.`degree_id` INNER JOIN `course_teacher` ON `courses`.`id`=`course_teacher`.`teacher_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id`=`teachers`.`id`;

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT(CONCAT(`teachers`.`name`,' ',`teachers`.`surname`)) AS `full_name_teachers`, `departments`.`name` FROM `departments` INNER JOIN `degrees` ON`departments`.`id`=`degrees`.`department_id` INNER JOIN `courses` ON `degrees`.`id`=`courses`.`degree_id` INNER JOIN `course_teacher` ON `courses`.`id`=`course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id`=`teachers`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica';

## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18