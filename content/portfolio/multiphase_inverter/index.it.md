+++
draft = false
title = 'Inverter Multi-Fase'
showReadingTime = false
date =  2019-12-23
showDate = false
showTableOfContents = true
showSummary = true
summary = "Sistema di controllo distributio per un inverter a multi-fase per la fondazione dell'acciaio nei processi sideurgici"
showAuthor = false
showPagination =  false
+++

# Inverter a Multi-Fase

## Panoramica
Questo progetto ha riguardato lo sviluppo di un sistema di controllo distribuito per un inverter a multi-fase, utilizzato nelle siderurgia. Il sistema è stato progettato con due FPGA principali (una master e una slave) utilizzando tecnologia Intel (Altera). Il master controlla simultaneamente più slave tramite collegamenti ottici punto-punto e si interfaccia con un PC che gestisce i parametri ad alto livello e l'operazione complessiva.

## Caratteristiche Principali e Risultati
- **Controllo Distribuito:** Il sistema è composto da un FPGA master e più FPGA slave che operano in parallelo.
- **Collegamenti Ottici Punto-Punto:** Il master gestisce la comunicazione con gli slave utilizzando collegamenti ottici punto-punto.
- **Protocollo di Comunicazione:**
  - Sviluppato un protocollo di comunicazione tra il master e gli slave tramite collegamenti ottici con clock integrato.
  - Il protocollo utilizza uno schema di trasmissione periodica con funzionalità di auto-recupero.
- **Canale per Dati in Tempo Reale:** Creato un canale speciale sulla connessione ottica per il flusso di dati in tempo reale dallo slave al PC.
- **Controllo del Segnale PWM:** Sviluppato il controllo per i segnali PWM, inclusi algoritmi per la gestione di frequenza e larghezza di impulso.
- **Monitoraggio dei Sensori:** Implementato il monitoraggio continuo dei sensori per garantire un'operazione sicura e per rilevare eventuali guasti.
- **Documentazione Completa:**
  - Sono stati prodotti documenti dettagliati di studio e architettura che forniscono approfondimenti sul design del sistema, i protocolli e le specifiche hardware.
  - È stata creata una documentazione tecnica completa per lo sviluppo e l'integrazione del codice VHDL, dei protocolli di comunicazione e della logica di controllo.

## Dettagli Tecnici
- **Hardware:** FPGA Intel (Altera), sensori di corrente e temperatura, PC di controllo.
- **Sviluppo:**
  - Progettazione e implementazione del **protocollo di comunicazione** tra master e slave in **VHDL**.
  - Sviluppato la **logica di controllo PWM** e i **sistemi di lettura sensori** in **VHDL** per garantire un controllo preciso e in tempo reale del sistema inverter.
  - Gestita la comunicazione tramite collegamenti ottici punto-punto per garantire bassa latenza e alta affidabilità.
  - Creato un **canale dedicato per dati in tempo reale** per trasmettere dati critici dallo slave al PC di controllo.
- **Tecnologie Utilizzate:**
  - FPGA Intel (Altera) per il controllo e la gestione della comunicazione.
  - **VHDL** per lo sviluppo del protocollo di comunicazione, della logica di controllo e dell'integrazione dei sensori.
  - Tecnologie di sensori per il monitoraggio di correnti e temperature.
- **Controllo PWM:** Algoritmi avanzati per il controllo delle frequenze PWM, garantendo operazioni sicure e rilevamento guasti.

## Sfide e Soluzioni
- **Affidabilità della Comunicazione:** Ottimizzata la trasmissione tramite collegamenti ottici punto-punto per garantire una comunicazione affidabile in ambienti industriali difficili.
- **Sincronizzazione:** Gestita la sincronizzazione tra il master e gli slave per controllare simultaneamente più inverter.
- **Recupero da Errori:** Implementato un meccanismo di auto-recupero per la comunicazione tra master e slave in caso di perdita di pacchetti o guasti nel link.

## Risultato
Il sistema ha fornito un controllo preciso e sicuro sugli inverter a multi-fase, garantendo un'operazione ottimale nelle fonderie di metalli. Grazie alla comunicazione ottica e a un protocollo avanzato sviluppato interamente in **VHDL**, il sistema ha mantenuto un'alta affidabilità operativa anche in condizioni gravose, con monitoraggio continuo e rilevamento guasti.
Inoltre, sono stati prodotti tutti i documenti pertinenti per lo **studio dell'architettura** e la **documentazione dettagliata**, fornendo approfondimenti chiari e completi sul design e sul funzionamento del sistema.

---
