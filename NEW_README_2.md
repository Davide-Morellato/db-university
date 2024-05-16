## Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(*) AS `total_students`, YEAR(`enrolment_date`) AS `year` FROM `students` GROUP BY `year`;

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio
## Calcolare la media dei voti di ogni appello d'esame
## Contare quanti corsi di laurea ci sono per ogni dipartimento