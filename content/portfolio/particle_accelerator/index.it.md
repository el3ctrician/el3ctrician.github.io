+++
draft = false
title = 'Acceleratore di Particelle'
showReadingTime = false
date =  2019-03-15
showDate = false
showTableOfContents = true
showSummary = true
summary = "Sistema di controllo per un acceleratore di paricelle per trattamento cancro"
showAuthor = false
showPagination =  false
+++

# Sistema di Controllo per Acceleratore di Particelle Utilizzato nel trattamento del Cancro

## Panoramica
Questo progetto ha riguardato l'aggiornamento del sistema di controllo di un acceleratore di particelle esistente utilizzato nel trattamentodel cancro. Lo sviluppo principale ha comportato la creazione di un nuovo protocollo di comunicazione per distribuire dati in modo efficiente tramite collegamenti ottici connessi a un master. Il sistema ha inoltre permesso a un dispositivo National Instruments (NI) su un backplane di recuperare i dati raccolti dagli slave tramite il master utilizzando PCI.

## Caratteristiche Principali e Risultati
- **Protocollo di Comunicazione Avanzato:**
  - Progettato e implementato un nuovo protocollo per distribuire i dati tra il master e più slave tramite collegamenti ottici.
  - Consentito il recupero dei dati da parte di un dispositivo National Instruments connesso tramite PCI sul backplane.
- **Funzionalità del Protocollo:**
  - Aggiunti campi speciali per la gestione di eventi specifici.
  - Integrato un sistema basato su priorità per gestire la trasmissione di dati critici.
  - Inclusa una clock embedded nel flusso dati per semplificare la sincronizzazione.
  - Utilizzato **codifica 8b/10b** per una trasmissione dati affidabile e **codici di correzione degli errori** per una tolleranza ai guasti migliorata.
- **Sincronizzazione:**
  - Sviluppato un meccanismo di sincronizzazione tra il master e gli slave utilizzando un **oscillatore controllato digitalmente (DCO)** e un **PLL di secondo ordine** sull'FPGA master.
- **Miglioramenti al Design del Sistema:**
  - Supportata la distribuzione e la raccolta di dati in tempo reale necessari per il controllo preciso dell'acceleratore di particelle.
  - Ottimizzata la performance e l'affidabilità per un utilizzo in applicazioni mediche, dove accuratezza e sicurezza sono fondamentali.

## Dettagli Tecnici
- **Hardware:**
  - FPGA Xilinx per i dispositivi master e slave.
  - Collegamenti ottici per la comunicazione tra master e slave.
  - Dispositivo National Instruments su backplane per il recupero dati tramite PCI.
- **Sviluppo del Protocollo:**
  - Meccanismo di clock embedded per garantire la sincronizzazione sui collegamenti ottici.
  - Implementata la **codifica 8b/10b** per migliorare l'integrità del segnale.
  - Incorporati codici di correzione degli errori (ECC) per rilevare e correggere errori di trasmissione.
  - Sviluppati campi personalizzati per la gestione di eventi speciali e un sistema a priorità per i dati critici.
- **Meccanismo di Sincronizzazione:**
  - Controllo di un **oscillatore controllato digitalmente (DCO)** sull'FPGA master per la sincronizzazione.
  - Allineamento preciso del clock realizzato utilizzando un **PLL di secondo ordine**, garantendo un'operazione fluida e una comunicazione affidabile.
- **Tecnologie Utilizzate:**
  - VHDL per la progettazione della logica del protocollo e dei sistemi di gestione dei dati.
  - Bus PCI per l'interfacciamento del master con il dispositivo National Instruments.

## Sfide e Soluzioni
- **Sincronizzazione dei Dati:** Utilizzato un **oscillatore controllato digitalmente** con un **PLL di secondo ordine** sull'FPGA master per mantenere una tempistica precisa con gli slave.
- **Resilienza agli Errori:** Usata **codifica 8b/10b** ed ECC per migliorare l'affidabilità dei dati e il recupero del clock.
- **Gestione delle Priorità:** Progettato un sistema basato su priorità per gestire in modo efficiente la trasmissione di dati critici senza ritardi.
- **Recupero Dati in Tempo Reale:** Integrata la comunicazione PCI per un accesso rapido e affidabile ai dati tramite il dispositivo National Instruments.

## Risultato
Il nuovo protocollo di comunicazione ha migliorato il sistema di controllo dell'acceleratore di particelle, consentendo operazioni precise e affidabili, fondamentali per le applicazioni nel trattamentodel cancro. Integrando funzionalità avanzate come il clock embedded, la correzione degli errori e la gestione delle priorità, oltre alla sincronizzazione tramite un **oscillatore controllato digitalmente** e un **PLL di secondo ordine**, il sistema ha raggiunto un'elevata affidabilità e performance, rispettando rigorosi standard medici.

---
