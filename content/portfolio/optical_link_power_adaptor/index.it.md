+++
draft = false
title = "Adattatore di unghezza d'onda ottica"
showReadingTime = false
showDate = false
showTableOfContents = true
showSummary = true
summary = "Scheda in pura logica analogica per l'adattamento della lunghezza d'onda tra due link ottici"
date = 2019-11-11
showAuthor = false
showPagination =  false
+++

# Progetto PCB per Interfaccia Ottica

## Panoramica
Questo progetto ha riguardato la progettazione di una PCB completamente analogica per interfacciare due collegamenti ottici che utilizzano lo stesso protocollo digitale ma operano a lunghezze d’onda diverse. L'adattatore ha permesso la conversione dei segnali tra un collegamento Avago HCS a 820 nm e un modulo SFP moderno a 1310 nm. Grazie a un approccio analogico, il design ha garantito la latenza più bassa possibile, supportando una comunicazione bidirezionale affidabile.

## Caratteristiche Principali e Risultati
- **Conversione Analogica del Segnale:**
  - Adattato il segnale **PECL** del collegamento Avago HCS al segnale **LVDS** del modulo SFP.
  - Progettata un'interfaccia completamente analogica e bidirezionale per minimizzare la latenza sia per i flussi dati in upstream che in downstream.
- **Progettazione dello Schema:**
  - Creati schemi elettrici precisi in **Cadence OrCAD**.
  - Fornite indicazioni per il layout, assicurando integrità del segnale ed efficienza energetica.
- **Coordinamento della Produzione:**
  - Collaborato con il produttore del PCB per garantire la consegna di tutti i componenti e il rispetto delle specifiche del design.
  - Verificata l'accuratezza della produzione, con particolare attenzione a tracce a impedenza controllata e isolamento dei segnali.
- **Gestione dell'Alimentazione:**
  - Integrato un power supply a basso rumore ed efficiente per supportare i moduli ottici e i circuiti analogici.
- **Considerazioni Progettuali:**
  - Concentrato sull’uso di componenti e tecniche analogiche per ottenere un adattamento del segnale a bassa latenza.
  - Implementate tracce a impedenza controllata e tecniche di isolamento per segnali ad alta velocità.

## Dettagli Tecnici
- **Specifiche Hardware:**
  - **Collegamento di Ingresso:** Fibra Avago HCS a 820 nm con segnalazione PECL.
  - **Collegamento di Uscita:** Modulo SFP a 1310 nm con segnalazione LVDS.
  - Flusso dati completamente analogico e bidirezionale per upstream e downstream.
- **Strumenti di Progettazione:**
  - **Cadence OrCAD** per la progettazione degli schemi elettrici.
  - Layout eseguito esternamente con indicazioni specifiche sui dettagli del design analogico.
- **Caratteristiche del Design PCB:**
  - Tracce a impedenza controllata per garantire l'integrità del segnale ad alta velocità.
  - Tecniche di isolamento per minimizzare diafonia e rumore.
  - Percorso del segnale analogico a bassa latenza per rispettare rigorosi requisiti temporali.
- **Produzione:**
  - Collaborato con il produttore del PCB per garantire una produzione accurata.
  - Forniti file di produzione completi e verificati i processi per la fabbricazione.

## Sfide e Soluzioni
- **Riduzione della Latenza:** Scelto un approccio completamente analogico per eliminare i ritardi associati all'elaborazione digitale.
- **Integrità del Segnale:** Mantenuta un'elevata integrità del segnale tramite tracce a impedenza controllata e un layout ottimizzato per comunicazioni ad alta velocità.
- **Precisione nella Produzione:** Lavorato a stretto contatto con il produttore per garantire la fabbricazione accurata del PCB, in particolare per le specifiche dei circuiti analogici.
- **Compatibilità:** Collegati sistemi legacy Avago HCS e tecnologia SFP moderna tramite l'adattamento analogico del segnale.

## Risultato
Il design analogico del PCB ha fornito un'interfaccia ad alte prestazioni tra due tecnologie di collegamento ottico, raggiungendo la latenza più bassa possibile e garantendo una comunicazione bidirezionale affidabile. Il progetto ha bilanciato con successo tecnologie
