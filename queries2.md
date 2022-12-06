Contare quanti iscritti ci sono stati ogni anno
```sql
SELECT YEAR(`enrolment_date`) , COUNT(`id`) FROM `students` GROUP BY YEAR(`enrolment_date`);
```

Contare gli insegnanti che hanno l'ufficio nello stesso edificio
```sql
SELECT `office_number`, COUNT(`id`) FROM `teachers` GROUP BY `office_number`;
```


Calcolare la media dei voti di ogni appello d'esame
```sql
SELECT `exams`.`id`, AVG(`exam_student`.`vote`) FROM `exam_student` JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` GROUP BY `exams`.`id`;

```

Contare quanti corsi di laurea ci sono per ogni dipartimento
```sql
SELECT `departments`.`name` , COUNT(`degrees`.`id`) FROM `degrees` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` GROUP BY `departments`. `name`;

```

Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```sql
SELECT * FROM `students` JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

```

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```sql
SELECT * FROM degrees JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name` = 'Dipartimento di Neuroscienze';

```

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```sql
SELECT * FROM `courses` JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`id` = 44;

```

Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```sql
SELECT `students`.`id` , `students`.`name` ,`students`.`surname` , `degrees`.`name` , `departments`.`name` FROM `students` JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` ORDER BY `students`.`surname`,`students`.`name`;

```

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```sql
SELECT `degrees`.`name` , `courses`.`name`, `teachers`.`surname` FROM `courses` JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;

```

Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT `teachers`.`name` , `teachers`.`surname` , `teachers`.`id` , `departments`.`name`, `courses`.`name` FROM `departments` JOIN `degrees` ON `degrees`.`department_id` = `departments`.`id` JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id` JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `departments`.`name` = "Dipartimento di Matematica";

```