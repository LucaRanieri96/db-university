1. Contare quanti iscritti ci sono stati ogni anno
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
3. Calcolare la media dei voti di ogni appello d'esame
4. Contare quanti corsi di laurea ci sono per ogni dipartimento

1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(enrolment_date) as `year`, COUNT(*) as `total_students`
FROM `students`
GROUP BY `year`;

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(*) AS 'num_teachers', `office_address`
FROM `teachers`
GROUP BY `office_address`

3. Calcolare la media dei voti di ogni appello d'esame

SELECT `exam_id`, AVG(`vote`) AS `avg_vote`
FROM `exam_student`
GROUP BY `exam_id`

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `department_id`, COUNT(`id`) AS `num_degrees`
FROM `degrees`
GROUP BY `department_id`