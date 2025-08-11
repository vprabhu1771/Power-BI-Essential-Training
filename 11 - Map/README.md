```sql
CREATE TABLE `country`(
  `id` INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  `name` VARCHAR(255)
);

INSERT INTO `country` (`name`) VALUES ("India"), ("America"), ("Russia"), ("China");
```

# Power BI

Get Data -> More... -> Database -> MySQL database

### MySQL database

Server -> 127.0.0.1

Database -> your_database_name


Power BI -> Visualizations -> Map -> Click -> Select name 

Drag and Drop name Into Legend -> Location 
