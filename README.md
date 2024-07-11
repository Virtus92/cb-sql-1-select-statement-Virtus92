# Spaß mit Datenbanken
## SQL
## Selektion

### Auswahl von Zeilen (Selektion)

```sql
SELECT  'Spalten'
FROM    'Tabellen'
WHERE   'Suchbedingung'
```

```sql
SELECT *
FROM EMP
WHERE DEPTNO = 30;
```

#### Beispiel

Gesucht ist der Name aller Büroangestellten

```sql
SELECT ENAME
FROM EMP
WHERE JOB='CLERK';
```

### Vergleichsoperatoren
| Operator | Bedeutung |
|----------|-----------|
| `=`      | gleich    |
| `!=`,`<>`| ungleich  |
| `>=`     | größer gleich |
| `<`      | kleiner   |
| `<=`     | kleiner gleich |
| `BETWEEN ... AND ...` | zwischen zwei Werten |
| `IN(Liste)` | entspricht einem Wert in der 'Liste' |
| `LIKE`   | enthält bestimmte Zeichen |
| `IS NULL`| ist ein Null-Wert |

#### Verneinung

```plaintext
NOT BETWEEN, NOT IN, NOT LIKE, IS NOT NULL
```

#### Beispiele
##### Beispiel 1
Auflisten aller Abteilungen, deren Abteilungsnummer größer als 20 ist.

```sql
SELECT DNAME, DEPTNO
FROM DEPT
WHERE DEPTNO > 20;
```

##### Beispiel 2
Bei sehr großen Tabellen kann es sinnvoll sein, nicht alle Datensätze zu lesen, sondern nur die ersten n Sätze.

```sql
SELECT rownum, empno
 FROM emp
 WHERE ROWNUM < 4;
```

##### Beispiel 3
Es sollen diejenigen Mitarbeiter ermittelt werden, die mehr Provision als Gehalt verdienen.

```sql
SELECT ENAME, SAL, COMM
FROM EMP
WHERE COMM > SAL;
```

##### Beispiel 4
Alle Verkäufer aus Abteilung 30, deren Gehalt größer gleich 1,500.- ist.

```sql
SELECT ENAME, SAL, DEPTNO
FROM EMP
WHERE JOB = ‘SALESMAN‘
AND DEPTNO = 30
AND SAL >= 1500;
```

##### Beispiel 5
Finde alle Mitarbeiter, die von Beruf MANAGER sind oder die mehr als 3,000.- verdienen.

```sql
SELECT ENAME, JOB, SAL
FROM EMP
WHERE JOB = ’MANAGER’
OR SAL > 3000;
```

##### Beispiel 6
Ausgabe aller Mitarbeiter aus Abteilung 10, die weder Manager noch Büroangestellte sind.

```sql
SELECT *
FROM EMP
WHERE NOT (JOB = ‘MANAGER‘ OR JOB = ‘CLERK‘)
AND DEPTNO = 10;
```

##### Beispiel 7
Ausgabe aller Mitarbeiter, die zwischen 1200.- und 1300.- verdienen.

```sql
SELECT ENAME, JOB, SAL
FROM EMP
WHERE SAL BETWEEN 1200 AND 1300;
```

##### Beispiel 8
Ausgabe aller Mitarbeiter, die nicht entweder Büroangestellte, Analytiker oder Verkäufer sind.

```sql
SELECT ENAME, JOB, DEPTNO
  FROM EMP
  WHERE JOB NOT IN (‘CLERK‘,‘ANALYST‘,’SALESMAN’);
```

##### Beispiel 9
Ausgabe aller Mitarbeiter, deren Name mit M beginnt.

```sql
SELECT *
FROM EMP
WHERE ENAME LIKE ‘M%‘;
```

##### Beispiel 10
Ausgabe aller Mitarbeiter, deren Name fünf Zeichen lang ist, mit ALL beginnt und mit N endet.

```sql
SELECT *
FROM EMP
WHERE ENAME LIKE ‘ALL_N‘;
```

##### Beispiel 11
Alle Berufsbezeichnungen sollen 1x ausgegeben werden. Die Überschrift der Spalte soll BERUF sein.

```sql
SELECT DISTINCT JOB BERUF
FROM EMP;
```

#### Alias
Unterschied zwischen:

```sql
Select ename, job from emp;
```
Und

```sql
Select ename job from emp;
```

Beim ersten Beispiel selektiert man die Spalten `ENAME` und `JOB` von der Tabelle `EMP`.
Beim zweiten Beispiel selektiert man die Spalte `ENAME` und gibt der Spalte den Namen `JOB`.

#### Sortieren
Ausgabe aller Mitarbeiter aus Abteilung 30 geordnet nach ihrem Gehalt.

```sql
SELECT *
FROM EMP


WHERE DEPTNO = 30
ORDER BY SAL;
```

Ausgabe der Mitarbeiter aus Abteilung 30 absteigend geordnet nach ihrem Gehalt.

```sql
SELECT *
FROM EMP
WHERE DEPTNO = 30
ORDER BY SAL DESC;
```

Alle Mitarbeiter sollen nach ihrem Job geordnet werden, und innerhalb jedes Jobs in absteigender Reihenfolge nach ihrem Gehalt.

```sql
SELECT *
FROM EMP
ORDER BY JOB, SAL DESC;
```
```

In this Markdown format, SQL code is enclosed in code blocks for clarity and tabular data is represented in tables for easy readability. This format is widely used in GitHub repositories for documentation and readme files.
