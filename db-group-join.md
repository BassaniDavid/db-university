# query con GROUP BY

### 1. Contare quanti iscritti ci sono stati ogni anno
```
SELECT 
    YEAR(`enrolment_date`) AS `anno_iscrizione`, COUNT(id) AS `numero_iscritti`
FROM
    dbuniversity.students
GROUP BY `anno_iscrizione`
ORDER BY `anno_iscrizione`;
```
### 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```
SELECT 
   `office_address` AS `edificio`, COUNT(id) AS `numero_docenti`
FROM
    dbuniversity.teachers
GROUP BY `office_address`
ORDER BY `office_address`;
```
### 3. Calcolare la media dei voti di ogni appello d'esame
```
SELECT 
   `exam_id`, AVG (`vote`) AS `media_voti`
FROM
    dbuniversity.exam_student
GROUP BY `exam_id`
ORDER BY `exam_id`;
```
### 4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```
SELECT 
  `departments`.`name` , COUNT(`department_id`) AS `numero_corsi_di_laurea`
FROM
    `departments`
INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`
GROUP BY `department_id`
ORDER BY `departments`.`name`;
```
# query con JOIN

### 1.Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```
SELECT 
   `degrees`.`name` ,`students`.*
FROM
    `degrees`
INNER JOIN `students`
ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` ='Corso di Laurea in Economia';
```
### 2.Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```
SELECT 
    `departments`.`name` AS `nome_dipartimento`, `degrees`.*
FROM
    `departments`
INNER JOIN
    `degrees` ON `departments`.`id` = `degrees`.`department_id`
WHERE
    `departments`.`name` = 'dipartimento di neuroscienze';
```
### 3.Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```
SELECT 
    `teachers`.`name`, `teachers`.`surname`, `courses`.*
FROM
    `teachers`
INNER JOIN
    `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN
    `courses` ON `course_teacher`.`course_id` = `courses`.`id`
WHERE
    `teachers`.`name` = 'Fulvio'
AND `teachers`.`surname` = 'amato';
```
### 4.Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento,in ordine alfabetico per cognome e nome
```
SELECT 
    `students`.`surname`,
    `students`.`name`,
    `degrees`.*,
    `departments`.*
FROM
    `students`
INNER JOIN
    `degrees` ON `degrees`.`id` = `students`.`degree_id`
INNER JOIN
    `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname` , `students`.`name`;
```
### 5.Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```
SELECT 
    *
FROM
    `degrees`
    INNER JOIN
    `courses` ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN
    `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN
    `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `degrees`.`name`;
```
### 6.Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica(54)
```
SELECT 
    `departments`.`name` AS `nome_dipartimento`,
    `teachers`.`name` AS `nome_docente`,
    `teachers`.`surname` AS `cognome_docente`
FROM
    `departments`
INNER JOIN
    `degrees` ON `degrees`.`department_id` = `departments`.`id`
INNER JOIN
    `courses` ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN
    `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN
    `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE
    `departments`.`name` = 'Dipartimento di Matematica';
```
### 7.BONUS:Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame,stampando anche il voto massimo.Successivamente, filtrare i tentativi con voto minimo 18.
```

```