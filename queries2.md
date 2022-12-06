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