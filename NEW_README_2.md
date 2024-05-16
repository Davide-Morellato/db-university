## Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(*) AS `total_students`, YEAR(`enrolment_date`) AS `year` FROM `students` GROUP BY `year`;

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS `total_teachers`, `office_address` AS `address` FROM `teachers` GROUP BY `office_address`;

<!-- HO PROVATO AD USARE ANCHE COUNT(`id`) E COUNT(`name`) ED HO AVUTO LO STESSO RISULTATO -->

## Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`vote`) AS `average_vote`, `exams`.`date` AS `date` FROM `exam_student` INNER JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` GROUP BY `date`;

## Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(`degrees`.`name`) AS `degrees_name`, `departments`.`name` AS `departments_name` FROM `departments` INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` GROUP BY `departments`.`name`;