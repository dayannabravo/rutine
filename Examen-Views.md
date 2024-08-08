Equipo de Futbol
```-- Tabla Rutine
-- Tabla Team
CREATE TABLE Team (
    id INT PRIMARY KEY,
    description VARCHAR(255),
    country VARCHAR(255),
    creation_year INT
);

```

```
--Tabla Player
CREATE TABLE Player (
    id INT PRIMARY KEY,
    full_name VARCHAR(200),
    position  VARCHAR(100),
    age INT,
    team_id INT,
    FOREIGN KEY (team_id) REFERENCES Team (id)
    
);

```

```
CREATE VIEW PlayerTeamInfo AS
SELECT 
    p.full_name AS player_name,
    p.age,
    t.description AS team_description,
    t.country
FROM 
    Player p
JOIN 
    Team t ON p.team_id = t.id;

```
![image](https://github.com/user-attachments/assets/1b1aa047-9b93-481d-a400-d66433b66f44)
