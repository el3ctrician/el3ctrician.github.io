+++
draft = false
title = 'What 10 years of digital design has taught me'
showReadingTime = true
showDate = true
showTableOfContents = true
showSummary = true
summary = "A reflection from the field after 10 years of digital design"
date = 2026-04-09
showAuthor = true
showPagination = true
showComments= true
+++

# Lezioni personali imparati dall'ASIC e FPGA

*opinabili ma comunque fondate*


---

Ho avuto la fortuna di lavorare su sistemi oggi in produzione: dagli ASIC per dispositivi biomedici, agli FPGA per la computer vision, fino alla logica di controllo per infrastrutture acceleratori di particelle. Progettare sistemi digitali che funzionino al di fuori di una simulazione è difficile. Portarli in produzione in modo affidabile, efficiente e senza spiacevoli sorprese dell'ultimo minuto lo è ancora di più.

Dopo 10 anni di lavoro sul campo, sono convinto che la maggior parte dei progetti non fallisca a causa di un codice scritto male ma bensi falliscono per assunzioni errate, verifica tralasciata e flussi di lavoro che contrastano gli strumenti di sviluppo invece di sfruttarli a proprio vantaggio.

Non si tratta di regole da manuale. Sono modelli che ho visto funzionare (o fallire) in tape-out e bring-up di laboratorio. In questo post, voglio evidenziare alcune lezioni apprese sul campo e il tipo di interventi tecnici che hanno fatto una differenza misurabile in sistemi reali.

---

## Gli strumenti e i costrutti del linguaggio sono qui per aiutarci!

Non è un segreto che molti professionisti del settore provino, comprensibilmente, una certa diffidenza verso i sintetizzatori. Lo standard del linguaggio è una cosa, ma il supporto da parte degli strumenti è spesso molto lento o non disponibile nativamente portando le persone a non fidarsi dell'intelligenza del sintetizzatore e evitare l'uso di troppa astrazioni.

Alcuni team, in particolare negli ambienti VHDL tradizionalisti, tendono per abitudine a scrivere un RTL estremamente granulare. Sebbene questo dia una sensazione di controllo prevedibile, spesso si finisce per combattere contro il sintetizzatore invece di sfruttarlo.

Ho imparato rapidamente che il metodo migliore è "studiare" gradualmente il proprio sintetizzatore, osservando la logica risultante per comprenderne il funzionamento e trarne vantaggio. È possibile utilizzare descrizioni a un livello di astrazione intermedio e lasciare che il sintetizzatore elabori i dettagli, imparando a conoscere lo strumento passo dopo passo.

Un RTL pulito non si basa su trucchetti intelligenti. Si tratta di esprimere chiaramente l'intento progettuale, in modo che gli strumenti possano ottimizzare per te — non contro di te.

---

## Verifica: non è opzionale, nemmeno su FPGA

È convinzione diffusa che su FPGA si possa semplicemente "testare direttamente sulla scheda". Questo approccio causa più ritardi e bug di progettazione di quasi qualsiasi altra cosa.

Il debugging di un progetto scarsamente verificato in laboratorio è lento, incompleto e cieco rispetto ai flussi di lavoro guidati da testbench. Pensate al tempo necessario per rieseguire la sintesi ogni volta che volete osservare un nuovo segnale nel debugger o, peggio ancora, al tentativo di decidere quale sia la causa principale da monitorare fin dall'inizio.

È evidente che la necessità di un ambiente di verifica solido è cruciale sia per le FPGA che per gli ASIC, sebbene con ambiti e ruoli diversi. Tipicamente, in un flusso FPGA, si desidera progettare un ambiente di verifica che serva anche a riprodurre i bug osservati in laboratorio, garantendo accesso completo a tutto ciò che avviene nel sistema all'interno del simulatore. Negli ASIC, invece, l'attenzione si concentra sulla copertura di un numero sufficiente di casi per garantire che l'HDL venga sottoposto a tape-out correttamente, evitando costose maschere.

Detto questo, non tutti i team possono permettersi un'implementazione UVM completa o ambienti di test approfonditi. Grazie a molti strumenti eccellenti disponibili, è possibile creare un ambiente potente con un investimento minimo. Ho aiutato diversi team a colmare questa lacuna integrando dei *golden model* basati su Python, tramite DPI, direttamente nei testbench SystemVerilog, consentendo controlli funzionali senza dover riscrivere algoritmi complessi.

---

## Interfacce reali, sfide reali

Le interfacce ad alta velocità sono il punto in cui teoria e realtà spesso divergono. Nel corso degli anni ho sviluppato:

- Un **trasmettitore SLVS-EC**, completamente parametrizzato e portabile
- Un **sistema di allineamento di fase dinamico** per acquisire dati da sensori di immagine Sony ad alta risoluzione utilizzando I/O standard, evitando costosi transceiver
- Un **livello di interfaccia e logica di controllo per un acceleratore di particelle**, integrato profondamente con sistemi legacy e vincoli di temporizzazione complessi

Ciascuno di questi progetti ha richiesto una profonda comprensione dell'integrità del segnale, della tolleranza alla latenza, del clock domain crossing (CDC) e, spesso cosa ancora più importante, di come estrarre prestazioni massime da dispositivi non originariamente progettati per tali casi d'uso. La progettazione di queste interfacce richiede molte soluzioni pratiche e un processo di scelta tra compromessi difficili e subottimali per bilanciare i trade-off. Sebbene sia sempre allettante scrivere un HDL pulito e comprensibile, a volte bisogna accettare il fatto di dover ricorrere ad alcuni "truchetti" per aggirare le particolarità dei protocolli e i limiti della piattaforma target.

Per quanto riguarda le interfacce, direi che l'allineamento di fase dinamico dà il meglio di sé sulle FPGA, mentre i flussi ASIC richiedono vincoli di temporizzazione rigorosi fin dal primo giorno.

---

## Passaggio da FPGA ad ASIC: fallo subito, o te ne pentirai dopo

Se prevedete di testare un algoritmo su FPGA per poi migrare ad ASIC, non costruite mai sistemi attorno a IP del fornitore che non siano facilmente portabili su ASIC. Definite in modo rigoroso i vincoli di temporizzazione e, soprattutto, ricordate che sulle FPGA la logica viene mappata su LUT, quindi la complessità non è sempre linearmente correlata all'area. Negli ASIC, invece, il numero di gate, la lunghezza delle interconnessioni e la gerarchia di memoria impattano direttamente su area e temporizzazione, rendendo critica una pianificazione architetturale sin da subito.

Inoltre, le FPGA fanno ampio uso di memorie distribuite e shift register, che si sintetizzano in modo quasi trasparente. Negli ASIC, invece, ogni memoria inferita deve essere pianificata esplicitamente in termini di area, temporizzazione e posizionamento fisico. Trattate l'architettura di memoria come un vincolo progettuale primario fin dal primo giorno.

Il mio flusso di lavoro personale include:
1. **Rimuovere presto la logica specifica del fornitore**
2. **Astrazione delle interfacce di I/O e di memoria**
3. **Eseguire sintesi e P&R (Place & Route) di prova**

Assicuratevi sempre di tenere sotto controllo le problematiche del backend ASIC e di affrontarle prima ancora di puntare alla target ASIC.

---

## L'automazione non è opzionale

Se continui a generare la mappa dei registri a mano o utilizzi metodi antiquati per conservare dati di progetto cruciali che poi devono essere copiati manualmente da un progettista, stai volontariamente aprendo la porta agli errori nel tuo flusso. Per un cliente ho sostituito un intero flusso di generazione RTL utilizzando Python, recuperando i dati tramite il parsing di file di testo e fogli Excel. Non serve più una figura dedicata a raccogliere input da altri team e convertirli manualmente in HDL. Il risultato: tempi di manutenzione, ovvero il lasso di tempo tra gli aggiornamenti delle specifiche e l'implementazione HDL, ridotti di oltre l'80%, meno bug ed errori grazie al codice generato automaticamente e integrazione continua resa immediata.

---

## Conclusione: non conta solo cosa costruisci, ma come pensi

Che si tratti di revisionare architetture, ottimizzare RTL o progettare un nuovo chip, tengo profondamente a una cosa: **sistemi robusti costruiti con chiarezza e intento progettuale**.

Credo in:
- Scrivere codice portatile per impostazione predefinita
- Utilizzare l'automazione per ridurre l'errore umano
- Sfruttare *completamente* le toolchain, non utilizzarle con timore
- Segnalare tempestivamente le assunzioni errate, anche quando è scomodo

Quali lezioni avete appreso durante il vostro percorso? Mi piacerebbe confrontarmi con voi nei commenti.

*Image by <a href="https://pixabay.com/users/compileideas-6085846/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4972649">Amol Sharma</a> from <a href="https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=4972649">Pixabay</a>*