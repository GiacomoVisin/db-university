# Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
- Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella. 

# Dipartimenti
- id_dipartimento          PRIMARY KEY UNIQUE NN INT
- nome                     VARCHAR (100) NN

# Corsi_Laurea
- id_corso_laurea          PRIMARY KEY UNIQUE NN INT
- nome                     VARCHAR (100) NN
- id_dipartimento          FOREIGN KEY NN INT

# Corsi
- id_corso                 PRIMARY KEY UNIQUE NN INT
- nome                     VARCHAR (100) NN
- id_corso_laurea FK       FOREIGN KEY NN INT
    

# Corso_Insegnante          
- id_corso                 FOREIGN KEY NN INT
- id_insegnante            FOREIGN KEY NN INT
- PK( id_corso, id_insegnante)

# Insegnanti
- id_insegnante            PRIMARY KEY UNIQUE NN INT
- nome                     VARCHAR (20) NN
- cognome                  VARCHAR (20) NN
- email                    VARCHAR (50) NN

# Appello_Esame
- id_appello_esame         PRIMARY KEY UNIQUE NN INT
- data_appello             DATETIME   
- id_corso FK              FOREIGN KEY NN INT

f
# Partecipazione_Esame
- id_appello_esame         FOREIGN KEY NN INT
- id_matricola             FOREIGN KEY NN INT
- voto                     INT 
- PK ( id_appello_esame, id_matricola)

# Studente 
- id_matricola             PRIMARY KEY UNIQUE NN INT
- nome                     VARCHAR (20) NN
- cognome                  VARCHAR (20) NN
- id_corso_laurea FK       FOREIGN KEY NN INT