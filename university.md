<!-- Modellizzare la struttura di una tabella per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. -->

# DB University


## Departments

id:          PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:        VARCHAR(50) NOTNULL
address:     VARCHAR(50) NOTNULL
teachers:    VARCHAR(50) NOTNULL
students:    VARCHAR(50) NOTNULL
telephone:   VARCHAR(15) NOTNULL
email:       VARCHAR(50) NOTNULL UNIQUE

## Degrees

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:       VARCHAR(50) NOTNULL
language:   VARCHAR(5)  NULL DEFAULT("it_IT")
exams_nr:   TINYINT NOTNULL

## Courses

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:       VARCHAR(50) NOTNULL
CFU:        TINYINT NOTNULL
teachers:   VARCHAR(50) NOTNULL
start_date: DATETIME NOTNULL
end_date:   DATETIME NOTNULL

## Exams

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:
teacher:
date:

## Students

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:       VARCHAR(50) NOTNULL
lastname:   VARCHAR(50) NOTNULL
birth_date: 
badge_number: VARCHAR(8) NOTNULL
votes:        TINYINT
taxes_status: 

## Vote

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:       VARCHAR(50) NOTNULL
exam:       VARCHAR(50) NOTNULL
passed:     

## Teachers

id:         PK NOTNULL UNIQUE INDEX AUTOINCREMENTAL
name:       VARCHAR(50) NOTNULL
lastname:   VARCHAR(50) NOTNULL
telephone:  VARCHAR(15) NOTNULL
email:      VARCHAR(50) NOTNULL UNIQUE
course:     VARCHAR(50) NOTNULL


