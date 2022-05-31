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

id:
name:
address:
teachers:
students:
telephone:
email:

## Degrees

id:
name:
language:
exams_nr:

## Courses

id:
name:
CFU:
teachers:
start_date:
end_date:

## Exams

id:
name:
teacher:
vote_id:
date:

## Students

id:
name:
lastname:
birth_date:
badge_number:
votes:
taxes_status:

## Vote

id:
name: 
exam:
passed:

## Teachers

id:
name:
lastname:
telephone:
email:
course:


