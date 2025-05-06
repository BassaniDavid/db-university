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
### 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
**soluzione**:  
**controllo soluzione**: 
### 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
**soluzione**:  
**controllo soluzione**: 
### 6. Selezionare tutti i corsi di laurea magistrale (38)
**soluzione**:  
**controllo soluzione**: 
### 7. Da quanti dipartimenti è composta l'università? (12)
**soluzione**:  
**controllo soluzione**: 
### 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
**soluzione**:  
**controllo soluzione**: 