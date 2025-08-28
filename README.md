# SDK Engine SIARRIAB Java

**Motore di elaborazione per la gestione delle regole di business nel sistema SIARRIAB**
**Sistema Informativo Assistenza Riabilitativa Attività Riabilitazione**
## 🏛️ Contesto

Il progetto è stato sviluppato per supportare le esigenze del Ministero della Salute nella gestione delle regole di business relative ai flussi informativi sanitari. L'SDK è progettato per essere integrato nei sistemi esistenti e facilitare l'applicazione coerente delle regole definite.

## 🧾 Descrizione

Questo SDK Java fornisce un motore per l'elaborazione delle regole di business nel contesto del sistema SIARRIAB, utilizzato dal Ministero della Salute. Il motore consente di definire, gestire ed eseguire regole complesse per l'elaborazione dei dati sanitari.
Il microservizio ha come scopo l'acquisizione dei dati inviati dalle Regioni in merito ai trattamenti riabilitativi erogati, nell'ambito dell'assistenza semiresidenziale e residenziale, a carattere intensivo, estensivo e di mantenimento di cui all'articolo 34 del decreto del Presidente del Consiglio dei ministri del 12 gennaio 2017.

I dati richiesti sono relativi al set di informazioni legate ai trattamenti riabilitativi di cui all'art. 1, previa valutazione multidimensionale dell'assistito, presa in carico e progetto riabilitativo individuale (PRI) ovvero piano individuale di assistenza e riabilitazione. Il tracciato 2 (SIAR_RIAB) comprende le informazioni relative alle prestazioni erogate individualmente ad un assistito.

Il Sistema SIAR viene alimentato con le informazioni relative ai trattamenti riabilitativi erogati a partire dal quarto trimestre 2023

L'invio dei file viene effettuato mediante un tracciato XML. Per ogni tracciato XML, è fornito il relativo schema XSD di convalida a cui far riferimento.

#### Struttura XML:


Campi del nodo di riferimento Trasmissione
-Tipo

Eventi:
- Presa in carico
- Rivalutazione
- Erogazione
- Sospensione 
- Conclusione

Nodi di riferimento Presa in carico:
- Erogatore
- Presa In Carico


Campi Erogatore:
- Regione di erogazione (campo chiave)
- Azienda sanitaria di erogazione (campo chiave)
- Struttura erogatrice (campo chiave)

Campi Presa In Carico: 
- Data apertura PIC (campo chiave)
- ID record (campo chiave)

Nodi di riferimento Rivalutazione:
- Valutazione
- Disturbi

Campi Valutazione:
- Autonomia
- Grado Mobilita
- Comunicazione
- Area sensoriale
- Bisogni internistico- assistenziali
- Stabilità clinica
- Presenza di un caregiver
- Supporto sociale
- Utilizzo di dispositivi/protesi/ortes

Campi Disturbi
- Disturbi cognitivi
- Disturbi comportamentali

Nodi di riferimento Erogazione:
- Trattamento 

Campi Trattamento:
- Data inizio trattamento (campo chiave)
- Data fine trattamento (campo chiave)
- Durata complessiva del trattamento
- Durata media giornaliera del trattament

Nodi di riferimento Sospensione:
- Sospensione

Campi Sospensione:
- Data di inizio sospensione (campo chiave)
- Data di fine sospensione
- Motivazione della sospensione
 
 Nodi di riferimento Conclusione:
- Conclusione

Campi Conclusione:
- Data riunione finale di equipe
- Data di conclusione 
- Modalità di conclusione (campo chiave)
- Esito rilevazione della disabilità in uscita  1
- Esito rilevazione della disabilità in uscita  2
- Esito rilevazione della disabilità in uscita  3
- Esito rilevazione della disabilità in uscita  4
- Esito rilevazione della disabilità in uscita  5
- Esito rilevazione della disabilità in uscita  6
## 📚 XSD di riferimento

Il file xsd è disponibile al seguente link [`docs/FlsSiar_2.xsd`](docs/FlsSiar_2.xsd).

### Istruzioni per l'installazione

Per l'installazione e l'avvio dell'engine seguire la documentazione tecnica dettagliata disponibile all'url [`INSTALL.md`](https://github.com/ministero-salute/sdk-utilities-regole-properties/blob/main/INSTALL.md).

## 📝 Licenza

Questo progetto è rilasciato sotto licenza BSD 3-Clause License così come definita [BSD 3-Clause License](./LICENSE).

## 🤝 Contributi

I contributi sono benvenuti. Si prega di consultare il file [`CONTRIBUTING.md`](CONTRIBUTING.md) per le linee guida su come contribuire al progetto.

## 📞 Contatti

Per ulteriori informazioni, contattare:

- **Service Desk - Ministero della Salute**: servicedesk.mds@medilifegroupspa.com
- **Amministrazione titolare**: [Ministero della Salute](https://www.salute.gov.it)
- 
## mantainer:
 Accenture SpA until January 2026
