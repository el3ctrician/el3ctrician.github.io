+++
draft = false
title = 'Moniteraggio Industeriale della Temperatura'
showReadingTime = false
showDate = false
showTableOfContents = true
showSummary = true
summary = "Scheda di monitoraggio della temperatura da 16 sensori con il relativo filteraggio e un interfaccia USB per PC"
date = 2021-02-21
showAuthor = false
showPagination =  false
+++

# Sensore di Temperatura Industeriale

## Panoramica
Questo progetto ha riguardato la progettazione di un PCB per la misurazione della temperatura utilizzando sensori **PT1000**. Il sistema dispone di **16 canali** per l'acquisizione dei dati di temperatura, il condizionamento del segnale e il filtraggio prima di interfacciarsi con un **Convertitore Analogico-Digitale (ADC)**. Il PCB include anche un **microcontrollore ST** per gestire il sistema, multiplexers analogici controllati dal microcontrollore, e un **adattatore CAN-to-USB** per la comunicazione con il PC. Il design ha garantito un'alta precisione nella misurazione della temperatura e una trasmissione affidabile dei dati.

## Caratteristiche Principali e Risultati
- **Interfaccia Sensore di Temperatura:**
  - Progettata l'interfaccia per **16 sensori PT1000**, acquisendo i dati e applicando il necessario filtraggio del segnale per garantire letture accurate.
  - Utilizzati **multiplexer analogici** controllati dal microcontrollore per gestire in modo efficiente i canali dei sensori.
- **Integrazione Microcontrollore:**
  - Integrato un **microcontrollore ST** per controllare i multiplexers analogici, gestire l'acquisizione dei dati e processare le informazioni dei sensori.
  - Progettato il circuito necessario per **programmare e fare il debugging** del microcontrollore.
- **Condizionamento del Segnale e ADC:**
  - Sviluppato circuiti analogici per il **filtraggio del segnale** al fine di ottimizzare i dati dei sensori prima di passarli all'**ADC**.
  - Implementata una corretta **generazione di riferimento analogico** per garantire prestazioni stabili e accurate dell'ADC.
- **Comunicazione CAN-to-USB:**
  - Incorporato un **adattatore CAN-to-USB** per la trasmissione dei dati dal sistema al PC per il monitoraggio e l'analisi.
- **Progettazione dell'Alimentazione:**
  - Progettata una **sorgente di alimentazione multi-voltaggio** per garantire una fornitura stabile di energia al microcontrollore, ai sensori e agli altri componenti.

## Dettagli Tecnici
- **Specifiche Hardware:**
  - **Sensori di Temperatura:** Sensori **PT1000** su 16 canali per misurazioni precise della temperatura.
  - **Condizionamento del Segnale:** Filtri analogici per eliminare il rumore e preparare i dati dei sensori per la conversione ADC.
  - **Microcontrollore:** Microcontrollore ST utilizzato per controllare i multiplexers analogici e gestire l'elaborazione dei dati.
  - **ADC:** ADC di alta precisione per digitalizzare i segnali analogici provenienti dai sensori.
  - **Adattatore CAN-to-USB:** Usato per l'interfaccia con il PC, permettendo al sistema di inviare i dati tramite bus CAN via USB.
- **Strumenti di Progettazione:**
  - **Cadence OrCAD** per la progettazione degli schemi e la guida nel layout.
  - Lavorato a stretto contatto con il team di layout esterno per garantire l'integrità del segnale e una corretta disposizione dei componenti.
- **Progettazione dell'Alimentazione:**
  - Progettata una **sorgente di alimentazione multi-voltaggio** per soddisfare i requisiti di alimentazione del microcontrollore, dei sensori e delle periferiche.
  - Creata una **riferimento analogico** stabile per l'ADC per ridurre gli errori di misurazione.

## Sfide e Soluzioni
- **Integrità del Segnale:** Garantita l'acquisizione pulita del segnale attraverso il filtraggio analogico e un'attenta disposizione del layout per evitare interferenze.
- **Multiplexing dei Canali:** Utilizzati multiplexers analogici controllati dal microcontrollore per gestire efficientemente i 16 sensori PT1000, garantendo un corretto instradamento del segnale.
- **Gestione dell'Alimentazione:** Progettata una sorgente di alimentazione multi-voltaggio affidabile per soddisfare le esigenze del microcontrollore e dei sensori.
- **Interfaccia di Comunicazione:** Incorporato un **adattatore CAN-to-USB** per garantire una comunicazione fluida con il PC per il monitoraggio e la registrazione dei dati.
- **Programmazione e Debugging:** Progettato circuiti dedicati per **la programmazione** e **il debugging** del microcontrollore per semplificare lo sviluppo e i test.

## Risultato
Il PCB ha integrato con successo tutti i componenti per la misurazione ad alta precisione della temperatura e la trasmissione efficiente dei dati. Il design ha garantito letture accurate dai sensori, una distribuzione stabile dell'alimentazione e una comunicazione affidabile con il PC tramite il bus CAN. Grazie al corretto condizionamento del segnale, alla generazione di riferimento ADC e alla gestione robusta dell'alimentazione, il sistema ha soddisfatto tutti i requisiti prestazionali.

---
