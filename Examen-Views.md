ExamenRecu - Views Projects
```-- Tabla Rutine
CREATE TABLE Rutine (
    id INT PRIMARY KEY,
    description VARCHAR(255),
    disclaimer VARCHAR(255),
    sex CHAR(1)
);```

```
-- Tabla Exercise
CREATE TABLE Exercise (
    id INT PRIMARY KEY,
    detail VARCHAR(255),
    video_url VARCHAR(255)
);```

```
-- Tabla Routine_Exercise
CREATE TABLE Routine_Exercise (
    id INT PRIMARY KEY,
    series INT,
    repetitions INT,
    routine_id INT,
    exercise_id INT,
    FOREIGN KEY (routine_id) REFERENCES Rutine(id),
    FOREIGN KEY (exercise_id) REFERENCES Exercise(id)
);
```



1. Routine_By_Sex AS
Sentencia:
```--Vista de Rutinas por Sexo
CREATE VIEW Routine_By_Sex AS
SELECT 
    r.id AS routine_id,
    r.description AS routine_description,
    r.disclaimer AS routine_disclaimer,
    r.sex AS routine_sex
FROM 
    Rutine r
WHERE 
    r.sex = 'F'; 

 ```
 
 - Captura:

    <img src="./capturas/Vista de Rutinas por Sexo.png"alt="drawing" width="500"/>
    
    

2. Simple_Routines
Sentencia:
```--Vista de Detalles de Rutinas
CREATE VIEW Simple_Routines AS
SELECT 
    id AS routine_id,
    description AS routine_description,
    disclaimer AS routine_disclaimer,
    sex AS routine_sex
FROM 
    Rutine;

```

 - Captura:

    <img src="./capturas/Vista de Detalles de Rutinas.png"alt="drawing" width="500"/>
 

3. Routines_Exercise_Count 
Sentencia:
```--Vista de Rutinas con Número de Ejercicios
CREATE VIEW Routines_Exercise_Count AS
SELECT 
    r.id AS routine_id,
    r.description AS routine_description,
    COUNT(re.id) AS exercise_count
FROM 
    Rutine r
JOIN 
    Routine_Exercise re ON r.id = re.routine_id
GROUP BY 
    r.id, r.description;

```

 - Captura:

    <img src="./capturas/Vista de Rutinas con Número de Ejercicios.png"alt="drawing" width="500"/>
