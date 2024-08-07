ExamenRecu - Views Projects
```-- Tabla Rutine
CREATE TABLE Rutine (
    id INT PRIMARY KEY,
    description VARCHAR(255),
    disclaimer VARCHAR(255),
    sex CHAR(1)
);
```

```
-- Tabla Exercise
CREATE TABLE Exercise (
    id INT PRIMARY KEY,
    detail VARCHAR(255),
    video_url VARCHAR(255)
);
```

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

```
CREATE VIEW Routine_Exercise_Details AS
SELECT 
    r.id AS routine_id,
    r.description AS routine_description,
    r.disclaimer AS routine_disclaimer,
    r.sex AS routine_sex,
    e.id AS exercise_id,
    e.detail AS exercise_detail,
    e.video_url AS exercise_video_url,
    re.series AS exercise_series,
    re.repetitions AS exercise_repetitions
FROM 
    Rutine r
JOIN 
    Routine_Exercise re ON r.id = re.routine_id
JOIN 
    Exercise e ON re.exercise_id = e.id;
```