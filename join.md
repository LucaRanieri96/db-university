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

SELECT `exams`.`id`, AVG(`exam_student`.`vote`) AS 'avg_vote'
FROM `exams`
JOIN `exam_student` ON `exams`.`id` = `exam_student`.`exam_id`
GROUP BY `exams`.`id`

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `departments`.`name`, COUNT(`degrees`.`id`) AS `num_degrees`
FROM `departments`
LEFT JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id`
GROUP BY `departments`.`id`