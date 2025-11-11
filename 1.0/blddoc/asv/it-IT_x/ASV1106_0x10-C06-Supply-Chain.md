# C6 Sicurezza della catena di approvvigionamento per modelli, framework e dati

## Obiettivo di Controllo

Gli attacchi alla supply chain dell'AI sfruttano modelli, framework o dataset di terze parti per inserire backdoor, bias o codice sfruttabile. Questi controlli forniscono una provenienza end-to-end, gestione delle vulnerabilità e monitoraggio per proteggere l'intero ciclo di vita del modello.

---

## C6.1 Verifica e Provenienza del Modello Preaddestrato

Valutare e autenticare l'origine dei modelli di terze parti, le licenze e i comportamenti nascosti prima di qualsiasi messa a punto o distribuzione.

|   #   | Descrizione                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.1.1 | Verificare che ogni artefatto di modello di terze parti includa un record di provenienza firmato che identifichi il repository di origine e l'hash del commit.                    |    1    |  D/V  |
| 6.1.2 | Verificare che i modelli siano analizzati per rilevare livelli dannosi o trigger Trojan mediante strumenti automatizzati prima dell'importazione.                                 |    1    |  D/V  |
| 6.1.3 | Verificare che il fine-tuning tramite transfer learning superi la valutazione avversaria per rilevare comportamenti nascosti.                                                     |    2    |   D   |
| 6.1.4 | Verificare che le licenze del modello, i tag di controllo delle esportazioni e le dichiarazioni sull'origine dei dati siano registrati in una voce ML-BOM.                        |    2    |   V   |
| 6.1.5 | Verificare che i modelli ad alto rischio (pesi caricati pubblicamente, creatori non verificati) rimangano isolati fino alla revisione e approvazione da parte di un essere umano. |    3    |  D/V  |

---

## C6.2 Scansione del Framework e delle Librerie

Scansionare continuamente i framework e le librerie di ML per CVE e codice dannoso per mantenere sicuro lo stack di runtime.

|   #   | Descrizione                                                                                                                                                   | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.2.1 | Verificare che le pipeline CI eseguano scanner di dipendenze su framework di intelligenza artificiale e librerie critiche.                                    |    1    |  D/V  |
| 6.2.2 | Verificare che le vulnerabilità critiche (CVSS ≥ 7.0) impediscano la promozione alle immagini di produzione.                                                  |    1    |  D/V  |
| 6.2.3 | Verificare che l'analisi statica del codice venga eseguita sulle librerie ML forkate o fornite.                                                               |    2    |   D   |
| 6.2.4 | Verificare che le proposte di aggiornamento del framework includano una valutazione dell'impatto sulla sicurezza che faccia riferimento ai feed pubblici CVE. |    2    |   V   |
| 6.2.5 | Verificare che i sensori runtime segnalino i caricamenti di librerie dinamiche imprevisti che deviano dal SBOM firmato.                                       |    3    |   V   |

---

## C6.3 Blocco e Verifica delle Dipendenze

Blocca ogni dipendenza su digest immutabili e riproduci le build per garantire artefatti identici e privi di manomissioni.

|   #   | Descrizione                                                                                                                | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.3.1 | Verificare che tutti i gestori di pacchetti applicano il version pinning tramite i file di blocco.                         |    1    |  D/V  |
| 6.3.2 | Verificare che vengano utilizzati digest immutabili invece di tag modificabili nei riferimenti ai container.               |    1    |  D/V  |
| 6.3.3 | Verificare che i controlli di build riproducibili confrontino gli hash tra le esecuzioni CI per garantire output identici. |    2    |   D   |
| 6.3.4 | Verificare che le attestazioni di build siano archiviate per 18 mesi per la tracciabilità dell'audit.                      |    2    |   V   |
| 6.3.5 | Verificare che le dipendenze scadute attivino PR automatiche per aggiornare o forkare le versioni bloccate.                |    3    |   D   |

---

## C6.4 Applicazione di Fonte Affidabile

Consentire il download degli artefatti solo da fonti approvate dall'organizzazione e verificati criptograficamente e bloccare tutto il resto.

|   #   | Descrizione                                                                                                                                          | Livello | Ruolo |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.4.1 | Verificare che i pesi del modello, i set di dati e i container vengano scaricati solo da domini approvati o registri interni.                        |    1    |  D/V  |
| 6.4.2 | Verificare che le firme Sigstore/Cosign convalidino l'identità dell'editore prima che gli artefatti vengano memorizzati nella cache locale.          |    1    |  D/V  |
| 6.4.3 | Verificare che i proxy di uscita blocchino i download di artifact non autenticati per applicare la politica della fonte attendibile.                 |    2    |   D   |
| 6.4.4 | Verificare che le liste di autorizzazione del repository siano riviste trimestralmente con evidenza della giustificazione commerciale per ogni voce. |    2    |   V   |
| 6.4.5 | Verificare che le violazioni della policy attivino la messa in quarantena degli artifact e il rollback delle esecuzioni di pipeline dipendenti.      |    3    |   V   |

---

## C6.5 Valutazione del rischio dei dataset di terze parti

Valutare i dataset esterni per avvelenamento, bias e conformità legale, e monitorarli durante tutto il loro ciclo di vita.

|   #   | Descrizione                                                                                                                                                               | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.5.1 | Verificare che i dataset esterni siano sottoposti a una valutazione del rischio di avvelenamento (ad esempio, impronta digitale dei dati, rilevamento di valori anomali). |    1    |  D/V  |
| 6.5.2 | Verificare che le metriche di bias (parità demografica, pari opportunità) siano calcolate prima dell'approvazione del dataset.                                            |    1    |   D   |
| 6.5.3 | Verificare che la provenienza e i termini di licenza per i set di dati siano registrati nelle voci ML‑BOM.                                                                |    2    |   V   |
| 6.5.4 | Verificare che il monitoraggio periodico rilevi il drift o la corruzione nei dataset ospitati.                                                                            |    2    |   V   |
| 6.5.5 | Verificare che i contenuti non consentiti (copyright, dati personali identificabili) siano rimossi tramite cancellazione automatica prima dell'addestramento.             |    3    |   D   |

---

## C6.6 Monitoraggio degli Attacchi alla Catena di Fornitura

Rileva precocemente le minacce alla catena di approvvigionamento tramite feed CVE, analisi dei log di audit e simulazioni red-team.

|   #   | Descrizione                                                                                                                                                                       | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.6.1 | Verificare che i log di audit CI/CD vengano inviati allo SIEM per il rilevamento di pull di pacchetti anomali o passaggi di build manomessi.                                      |    1    |   V   |
| 6.6.2 | Verificare che i playbook di risposta agli incidenti includano procedure di rollback per modelli o librerie compromessi.                                                          |    2    |   D   |
| 6.6.3 | Verificare che i tag di arricchimento di threat‑intel identifichino indicatori specifici per ML (ad esempio, IoC di avvelenamento del modello) nella gestione delle segnalazioni. |    3    |   V   |

---

## C6.7 ML‑BOM per gli Artefatti del Modello

Genera e firma SBOM dettagliati specifici per ML (ML-BOM) in modo che i consumatori a valle possano verificare l'integrità dei componenti al momento del deploy.

|   #   | Descrizione                                                                                                                                   | Livello | Ruolo |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.7.1 | Verificare che ogni artefatto del modello pubblichi un ML‑BOM che elenchi dataset, pesi, iperparametri e licenze.                             |    1    |  D/V  |
| 6.7.2 | Verificare che la generazione di ML‑BOM e la firma Cosign siano automatizzate nel CI e obbligatorie per la fusione.                           |    1    |  D/V  |
| 6.7.3 | Verificare che i controlli di completezza ML‑BOM facciano fallire la build se manca qualsiasi metadato del componente (hash, licenza).        |    2    |   D   |
| 6.7.4 | Verificare che i consumatori downstream possano interrogare gli ML-BOM tramite API per convalidare i modelli importati al momento del deploy. |    2    |   V   |
| 6.7.5 | Verificare che le ML-BOM siano sotto controllo versione e confrontate per rilevare modifiche non autorizzate.                                 |    3    |   V   |

---

## Riferimenti

* [OWASP LLM03:2025 Supply Chain](https://genai.owasp.org/llmrisk/llm032025-supply-chain/)
* [MITRE ATLAS : Supply Chain Compromise](https://atlas.mitre.org/techniques/AML.T0010)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)

