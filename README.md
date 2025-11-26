# Proiect-BD-Firma-Constructii
Descrierea Scenariului

Acest proiect realizează modelarea și implementarea unei baze de date pentru gestionarea activității unei firme de construcții care administrează proiecte în diverse orașe ale țării. Baza de date centralizează informații despre clienți, proiecte, angajați, furnizori și materialele utilizate.

Obiective Principale de Gestiune:

Proiecte: Fiecare proiect este comandat de un client și are un termen de execuție definit (data de început și data de finalizare).

Resurse Umane: Gestionarea angajaților (ingineri sau muncitori) și a calificărilor acestora. Angajații pot fi alocați la mai multe proiecte, fiind contorizat numărul de ore lucrate per proiect.

Logistică: Monitorizarea materialelor de construcție, a costurilor acestora și a furnizorilor de la care sunt achiziționate. Se ține evidența cantităților de materiale consumate pentru fiecare proiect.

Structura Bazei de Date (Schema Normalizată)

Baza de date este compusă din 7 tabele relaționale:

Entități Principale

CLIENT: Stochează datele de identificare (Nume, Prenume, Adresă, Telefon, Email).

PROIECT: Conține detalii despre lucrări (Status, Perioadă desfășurare) și face legătura cu clientul beneficiar.

ANGAJAT: Include date personale, data angajării, salariul, și rolul (Calificare pentru muncitori / Specializare pentru ingineri).

MATERIALE: Lista materialelor disponibile, descrierea și costul per unitate (100 kg).

FURNIZOR: Datele de contact ale firmelor partenere care livrează materiale.

Tabele de Asociere (Relații M:N) Deoarece un angajat poate lucra la mai multe proiecte și un proiect folosește mai multe materiale, au fost create tabele de legătură:

ALOCARE_MUNCITORI: Leagă ANGAJAT de PROIECT și reține Nr_ore_lucrate.

ALOCARE_MATERIALE: Leagă MATERIALE de PROIECT și reține Cantitate utilizată.

Reguli de Validare și Constrângeri

Pentru a asigura integritatea datelor, au fost implementate următoarele reguli:

Validare Date: Data angajării trebuie să fie ulterioară datei nașterii. Data finalizării unui proiect trebuie să fie după data de începere (sau nulă dacă proiectul este în curs).

Validare Financiară: Salariul angajaților și costul materialelor trebuie să fie strict pozitive. Există o constrângere pentru un salariu minim de 3000.

Validare Cantități: Orele lucrate și cantitățile de materiale nu pot fi negative.

Unicitate: Adresele de email ale clienților trebuie să fie unice.

Funcționalități Implementate (Vederi)

Proiectul include vederi (views) pentru raportare rapidă:

Proiecte_Angajati: Afișează lista angajaților și proiectele la care aceștia sunt alocați.

Detalii_Materiale: Raport cu materialele folosite, cantitățile și furnizorii acestora.

Clienti_Proiecte: Monitorizează statusul proiectelor pentru fiecare client.

Materiale_Scumpe: Identifică materialele cu un cost unitar mai mare de 300.
