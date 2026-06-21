## Query con Select

# Selezionare tutti gli studenti nati nel 1990 (160)
- SELECT * FROM `students` WHERE  year(date_of_birth) = 1990
  
- SELECT * FROM `students` WHERE date_of_birth >= '1990-01-01'
AND date_of_birth < '1991-01-01';