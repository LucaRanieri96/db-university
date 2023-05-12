1. Selezionare tutti gli studenti nati nel 1990 (160)
2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
3. Selezionare tutti gli studenti che hanno più di 30 anni
4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
   laurea (286)
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
   20/06/2020 (21)
6. Selezionare tutti i corsi di laurea magistrale (38)
7. Da quanti dipartimenti è composta l'università? (12)
8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

###### RISOLUZIONE

1.  Selezionare tutti gli studenti nati nel 1990 (160)

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `students`;
    SELECT `date_of_birth` FROM `students` WHERE `date_of_birth` LIKE '1990-%';

2.  Selezionare tutti i corsi che valgono più di 10 crediti (479)

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `courses`;
    SELECT \* FROM `courses` WHERE `cfu` > 10;

3.  Selezionare tutti gli studenti che hanno più di 30 anni

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `students`;
    SELECT \* FROM `students` WHERE YEAR(CURDATE()) - YEAR(`date_of_birth`) > 30;

4.  Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
    laurea (286)

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `courses`;
    SELECT `year` FROM `courses`; //per vedere come sono scritti i dati
    SELECT `period` FROM `courses`; //per vedere come sono scritti i dati
    SELECT `year`,`period` FROM `courses` WHERE `year` = 1 AND `period` = 'I semestre';

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
   20/06/2020 (21)

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `exams`;
    SELECT `date` FROM `exams`; //per vedere come sono scritti i dati
    SELECT `hour` FROM `exams`; //per vedere come sono scritti i dati
    SELECT `date`,`hour` FROM `exams` WHERE `date` = '2020-06-20' AND `hour` >= '14:00';

6. Selezionare tutti i corsi di laurea magistrale (38)

    SHOW databases;
    USE 91_database;
    SHOW tables;
    DESCRIBE `degrees`;
    SELECT `level` FROM `degrees`; //per vedere come sono scritti i dati
    SELECT `level` FROM `degrees` WHERE `level` LIKE 'magistrale';