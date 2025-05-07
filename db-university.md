### 1. Selezionare tutti gli studenti nati nel 1990 (160)
**soluzione**:   
```
SELECT 
    * 
FROM  
    dbuniversity.students  

WHERE  
    YEAR(date_of_birth) = '1990';  
```

**controllo soluzione**:   
```
SELECT 
    COUNT(id)  

FROM  
    dbuniversity.students  

WHERE  
    YEAR(date_of_birth) = '1990'; 
```
---



### 2. Selezionare tutti i corsi che valgono più di 10 crediti (479)  
**soluzione**:
```
SELECT     
    `name` 

FROM  
    dbuniversity.courses  

WHERE `cfu` > '10';
```
**controllo soluzione**: 
```
SELECT     
    COUNT(id) 

FROM  
    dbuniversity.courses  

WHERE `cfu` > '10';
```
---



### 3. Selezionare tutti gli studenti che hanno più di 30 anni
**soluzione**:  
```
SELECT 
    *  

FROM
    dbuniversity.students  

WHERE 
    YEAR(date_of_birth) < '1995';
```
**soluzioni migliori**:
```
SELECT 
    *  

FROM
    dbuniversity.students  

WHERE 
    YEAR(CURDATE()) - YEAR(date_of_birth) > 30;
```
```
SELECT 
    *  

FROM
    dbuniversity.students  

WHERE 
    TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) > 30;
```
---



### 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
**soluzione**: 
 ```
SELECT 
    *  

FROM
    dbuniversity.courses  

WHERE
    `year` = '1' AND `period` = 'I semestre';
```
**controllo soluzione**: 
 ```
SELECT 
    COUNT(id)  

FROM
    dbuniversity.courses  

WHERE
    `year` = '1' AND `period` = 'I semestre';
```
---



### 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
**soluzione**: 
 ```
SELECT 
    *  

FROM
    dbuniversity.exams  

WHERE 
    `date` = '2020-06-20'AND `hour` > '14:00:00';
```
**soluzione leggermente migliore**: 
 ```
SELECT 
    *  

FROM
    dbuniversity.exams  

WHERE 
    `date` = '2020-06-20'AND HOUR(`hour`) >= 14;
``` 
**controllo soluzione**: 
 ```
SELECT 
    COUNT(id) 

FROM
    dbuniversity.exams  

WHERE 
    `date` = '2020-06-20'AND `hour` > '14:00:00';
``` 
---



### 6. Selezionare tutti i corsi di laurea magistrale (38)
**soluzione**:  
 ```
SELECT 
    *  

FROM
    dbuniversity.degrees  

WHERE `level` = 'magistrale';
``` 
**controllo soluzione**: 
 ```
SELECT 
    COUNT(id)  

FROM
    dbuniversity.degrees  

WHERE `level` = 'magistrale';
``` 
---


### 7. Da quanti dipartimenti è composta l'università? (12)
**soluzione**:  
``` 
SELECT 
    COUNT(name)  AS `numero_dipertimenti`

FROM
    dbuniversity.departments;
``` 
---
### 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
**soluzione**:  
``` 
SELECT 
    COUNT(id)  

FROM
    dbuniversity.teachers  

WHERE `phone` IS NULL;
``` 
---