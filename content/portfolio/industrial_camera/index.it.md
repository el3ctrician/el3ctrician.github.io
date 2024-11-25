+++
draft = false
title = 'Telecamera Industeriale'
showReadingTime = false
showDate = false
showTableOfContents = true
showSummary = true
summary = "Telecamera industeriale con doppio sensore per l'ispezione dei prodotti ai fini del controllo qualità"
date = 2021-02-23
showAuthor = false
showPagination =  false
+++

# Telecamera Industriale per l'Ispezione dei Prodotti

## Panoramica
Questo progetto ha riguardato la progettazione di un sistema di telecamera industriale per l'ispezione dei prodotti, utilizzando una configurazione a doppio sensore per migliorare le capacità di zoom ottico. Il sistema si basa su un FPGA Xilinx e include un'elaborazione avanzata delle immagini per acquisire e manipolare i frame con alte prestazioni.

## Caratteristiche Principali e Risultati
- **Configurazione a Doppio Sensore:** Integrati due sensori Sony identici con lenti diverse per ottenere la funzionalità di zoom ottico.
- **Pipeline Avanzata di Elaborazione delle Immagini:**
  - Acquisizione dei frame dal sensore Sony.
  - Demosaicizzazione (debayering), bilanciamento del bianco e rimozione della vignettatura.
  - Zoom e ritaglio delle immagini per un output personalizzato.
- **Interfaccia ad Alta Velocità con il Sensore:**
  - Operato alla massima velocità del bus consentita dal dispositivo.
  - Implementato un allineamento dinamico di fase (DPA) per garantire una comunicazione affidabile.
- **Architettura Basata su AXI:**
  - Utilizzo di un bus AXI per la gestione dei dati video, garantendo compatibilità ed efficiente integrazione con i moduli IP Xilinx preesistenti.
- **Gestione della Memoria:** Le immagini elaborate venivano memorizzate per un accesso efficiente da parte del processore Zynq.
- **Trasmissione ad Alta Velocità:** Le immagini venivano ulteriormente elaborate su Zynq e trasmesse tramite Ethernet per un'analisi in tempo reale.

## Dettagli Tecnici
- **Hardware:** FPGA Xilinx, sensori Sony, processore Zynq.
- **Sviluppo:**
  - Progettazione e implementazione dell'architettura FPGA in **VHDL**.
  - Verifica tramite testbench in **SystemVerilog**.
  - Integrazione di moduli IP Xilinx preesistenti.
- **Tecnologie Utilizzate:**
  - Xilinx Vivado per sintesi e implementazione.
  - Verilog/SystemVerilog per la verifica.
  - Bus AXI per il routing interno dei dati video.
- **Pipeline delle Immagini:** Acquisizione e correzione delle immagini memorizzate, poi accessibili dallo Zynq per un'ulteriore elaborazione.

## Sfide e Soluzioni
- **Comunicazione ad Alta Velocità:** Superati i limiti di velocità del bus implementando l'allineamento dinamico di fase (DPA) per garantire una comunicazione affidabile con il sensore alla massima velocità.
- **Integrazione AXI:** Adattato con successo il design per integrare moduli IP Xilinx preesistenti, sfruttando il protocollo AXI per una gestione efficiente dei dati video.
- **Sincronizzazione:** Gestita la sincronizzazione tra i due sensori per un'integrazione fluida dello zoom ottico.
- **Efficienza di Elaborazione:** Ottimizzate le risorse FPGA per gestire l'intera pipeline di elaborazione delle immagini senza colli di bottiglia.

## Risultato
Il sistema della telecamera ha fornito prestazioni eccezionali per l'ispezione industriale dei prodotti, sfruttando lo zoom ottico a doppio sensore e la trasmissione in tempo reale tramite Ethernet. La sua robusta pipeline di elaborazione delle immagini, l'architettura basata su AXI e la comunicazione ad alta velocità hanno soddisfatto i requisiti industriali più esigenti.

---
