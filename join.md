1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
   relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per
   superare ciascuno dei suoi esami

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT *
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT *
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.*, `teachers`.`name`
FROM `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `course_teacher`.`teacher_id` = 44;

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il
   relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`id` as 'students_id', `students`.`name` as 'students_name',`students`.`surname` as 'students_surname', `students`.`date_of_birth` as 'students-date_of_birth', `degrees`.`name` as 'degree_name', `departments`.`name` as 'department_name'
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC, `students`.`name` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.`name` as 'degree_name',`courses`.`id` as 'courses_id',`courses`.`name` as 'courses_name',`teachers`.`name` as 'teachers_name',`teachers`.`surname` as 'teachers_surname'
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (5)

SELECT `teachers`.`id` as 'teachers_id', `teachers`.`name` as 'teachers_name', `teachers`.`surname` as 'teachers_surname', `departments`.`name` as 'department_name'
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`id` = 5;
