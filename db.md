Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni `Dipartimento` offre più `Corsi di Laurea `(es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni `Corso di Laurea` prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni `Corso` può essere tenuto da diversi `Insegnanti`;
ogni `Corso` prevede più appelli d'`Esame`;
ogni `Studente` è iscritto ad un solo `Corso di Laurea`;
ogni `Studente` può iscriversi a più appelli di `Esame`;
per ogni appello d'`Esame` a cui lo `Studente` ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## Entità

- Dipartimenti
- Dipartimento
- Corso_di_lauera
- Corsi
- Insegnati
- Studnete
- Esame

## Tables

### Dipartimenti

- id int Autoincrement PK Unique
- name_dipartimento varchar(30) Not Null

### Corso_di_laurea 1:N

- id int Autoincrement PK Unique
- dipartimenti_id FK Not Null int
- name_corso varchar(30) Not Null

### Corso

- id int Autoincrement PK Unique
- nome_corso varchar(30) Not Null

### insegnanti

- id int Autoincrement PK Unique
- nome varchar(20) Not Null
- cognome varchar(20) Not Null

### corso_insegnanti (Tabella ponte) N:N

- id int Autoincrement PK Unique
- insegnanti_id int not null
- corso_id int not null

### esami

- id int Autoincrement PK Unique
- nome_esame varchar(20) Not Null
- corso_id Fk int not null

### studeneti

- matricola int Autoincrement Unique PK
- id int Autoincrement Unique
- nome varchar(20) Not Null
- congome varchar(20) Not Null
- email varchar(30) Not Null
- phone int Not Null
- anno_iscrizione year Not Null
- importo_tasse money not null
- isee money not null
- borsa_di_studio money boolean not null
- corso_di_laurea_id FK int not null

### studenete_esami_appelli

- id int Autoincrement PK Unique
- stundente_id FK int not null
- esami_id FK int not null
- voto int not null
- promosso boolean not null
