+++
draft = false
title = 'Sensore CMOS per Endoscopia'
showReadingTime = false
showDate = false
showTableOfContents = true
showSummary = true
summary = "Blocchi digitali per un sensore CMOS da utilizzare per applicazioni endoscopiche"
date = 2022-09-21
showAuthor = false
showPagination =  false
+++

# Sensore CMOS per Applicazioni Endoscopiche

## Panoramica
Questo progetto ha riguardato lo sviluppo dei blocchi digitali di un **sensore CMOS** progettato per applicazioni endoscopiche. Il pipeline comprendeva l'acquisizione dei pixel dai convertitori ADC, l'elaborazione dei dati con filtraggio minimo e lo streaming dei dati elaborati verso un'interfaccia di uscita analogica. Il progetto ha inoltre richiesto la progettazione di blocchi di controllo chiave, come il **sequencer** e il **generatore di timing**, per una corretta integrazione con i componenti analogici.

## Caratteristiche Principali e Risultati
- **Sviluppo del Pipeline:**
  - Progettazione del pipeline digitale per l'**acquisizione dei dati dai convertitori ADC**, inclusa l'elaborazione del percorso dati con filtraggio minimo e lo streaming verso un'interfaccia di uscita analogica.
- **Controllo e Sequenziamento:**
  - Sviluppo del **sequencer** e del **generatore di timing** necessari per sincronizzare e controllare i blocchi analogici del sensore.
- **Gestione delle Interfacce Registro:**
  - Implementazione dell'interfaccia di configurazione e controllo tramite **registri**.
  - Distribuzione dei registri e dei segnali di clock per garantire un funzionamento efficiente dei blocchi digitali posizionati in diverse aree dell'ASIC.
- **Sviluppo e Verifica RTL:**
  - Progettazione di tutti i componenti digitali in **VHDL**, con particolare attenzione alla funzionalità, all'efficienza e alla modularità.
- **Supporto per il Design Fisico:**
  - Scrittura di **vincoli di timing** dettagliati per guidare la sintesi e garantire la chiusura del timing.
  - Esecuzione di **partial backend runs** utilizzando strumenti Cadence per verificare la sintesi e risolvere i problemi di timing.

## Dettagli Tecnici
- **Caratteristiche del Pipeline:**
  - Acquisizione dei dati dai convertitori ADC, con l'applicazione di un filtraggio minimo per ridurre il rumore.
  - Streaming dell'uscita analogica per una facile integrazione con interfacce esterne.
- **Logica di Controllo:**
  - Sviluppo di un **sequencer** per orchestrare il funzionamento dei blocchi digitali e analogici.
  - Creazione di un **generatore di timing** per fornire segnali di temporizzazione precisi ai componenti analogici del sistema.
- **Gestione di Clock e Registri:**
  - Progettazione della distribuzione dei segnali di clock e registri su tutto il chip, ottimizzando le prestazioni e il consumo energetico.
- **Dettagli di Implementazione:**
  - Programmazione RTL in **VHDL** per tutti i blocchi digitali.
  - Sviluppo e applicazione di vincoli di timing per garantire la chiusura del timing.
  - Utilizzo degli strumenti Cadence, tra cui:
    - **Cadence Genus** per la sintesi.
    - **Cadence Xcelium** per la simulazione.
    - **Cadence Innovus** per il design fisico.
    - **Cadence Tempus** per l'analisi del timing.

## Sfide e Soluzioni
- **Chiusura del Timing:** Affrontate le sfide legate al timing iterando sulle run di sintesi e affinando i vincoli di timing con **Tempus** per rispettare requisiti stringenti.
- **Distribuzione del Clock:** Garantita una distribuzione robusta dei segnali di clock nell'ASIC per mantenere la sincronizzazione dei blocchi digitali.
- **Integrazione con Componenti Analogici:** Progettazione di un **sequencer** e di un **generatore di timing** per controllare con precisione le funzioni analogiche, garantendo un funzionamento fluido del sistema mixed-signal.
- **Utilizzo degli Strumenti:** Sfruttata la suite completa degli strumenti **Cadence** per progettazione, verifica e chiusura del timing.

## Risultato
Il progetto ha consegnato con successo tutti i blocchi digitali necessari per il sensore CMOS, consentendo un funzionamento affidabile e preciso in applicazioni endoscopiche. Grazie alla chiusura del timing robusta, alla distribuzione efficiente del clock e all'integrazione fluida con i componenti analogici, il design ha soddisfatto i rigorosi requisiti delle applicazioni medicali. L'implementazione RTL in **VHDL**, supportata da sintesi e verifica fisica rigorosa con strumenti **Cadence**, ha prodotto un ASIC ad alte prestazioni e affidabile.

---
