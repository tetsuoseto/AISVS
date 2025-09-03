# C6 Sicurezza della catena di fornitura per modelli, framework e dati

## Obiettivo di controllo

Attacchi alla catena di fornitura dell'IA sfruttano modelli, framework o set di dati di terze parti per introdurre backdoor, bias o codice sfruttabile. Questi controlli forniscono tracciabilità end‑to‑end, gestione delle vulnerabilità e monitoraggio per proteggere l'intero ciclo di vita del modello.

---

## C6.1 Verifica e Provenienza dei Modelli Preaddestrati

Valuta e autentica le origini dei modelli di terze parti, le licenze e i comportamenti nascosti prima di qualsiasi messa a punto o implementazione in produzione.

|   #   | Descrizione                                                                                                                                                                               | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.1.1 | Verifica che ogni artefatto di modello di terze‑parti includa un record di provenienza firmato che identifichi il repository sorgente e l'hash del commit.                                |    1    |  D/V  |
| 6.1.2 | Verificare che i modelli vengano scansionati per individuare strati dannosi o trigger Trojan utilizzando strumenti automatizzati prima dell'importazione.                                 |    1    |  D/V  |
| 6.1.3 | Verifica che il fine-tuning nel transfer‑learning superi una valutazione avversaria per rilevare comportamenti nascosti.                                                                  |    2    |   D   |
| 6.1.4 | Verifica che le licenze del modello, i tag di controllo export‑control e le dichiarazioni sull'origine dei dati siano registrati in una voce ML‑BOM.                                      |    2    |   V   |
| 6.1.5 | Verifica che i modelli ad alto rischio (pesi caricati pubblicamente, creatori non verificati) rimangano in quarantena fino alla revisione e all'approvazione da parte di un essere umano. |    3    |  D/V  |

---

## C6.2 Scansione di framework e librerie

Scansionare continuamente i framework e le librerie ML alla ricerca di CVEs e codice dannoso per mantenere lo stack di runtime sicuro.

|   #   | Descrizione                                                                                                                                                 | Livello | Ruolo |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.2.1 | Verifica che le pipeline CI eseguano scanner delle dipendenze sui framework di IA e sulle librerie critiche.                                                |    1    |  D/V  |
| 6.2.2 | Verificare che le vulnerabilità critiche (CVSS ≥ 7.0) blocchino la promozione alle immagini di produzione.                                                  |    1    |  D/V  |
| 6.2.3 | Verifica che l'analisi statica del codice venga eseguita su librerie ML forkate o vendorizzate.                                                             |    2    |   D   |
| 6.2.4 | Verifica che le proposte di aggiornamento del framework includano una valutazione dell'impatto sulla sicurezza che faccia riferimento ai feed CVE pubblici. |    2    |   V   |
| 6.2.5 | Verificare che i sensori a tempo di esecuzione emettano avvisi quando si verificano caricamenti dinamici di librerie che deviano dallo SBOM firmato.        |    3    |   V   |

---

## C6.3 Bloccaggio delle dipendenze e verifica

Vincola ogni dipendenza a hash immutabili e riproduci le build per garantire artefatti identici e non manomissabili.

|   #   | Descrizione                                                                                                              | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 6.3.1 | Verifica che tutti i gestori di pacchetti impongano il pinning delle versioni tramite i file di blocco.                  |    1    |  D/V  |
| 6.3.2 | Verifica che i digest immutabili vengano utilizzati al posto dei tag mutabili nei riferimenti ai contenitori.            |    1    |  D/V  |
| 6.3.3 | Verifica che i controlli di build riproducibili confrontino gli hash tra le esecuzioni CI per garantire output identici. |    2    |   D   |
| 6.3.4 | Verifica che le attestazioni di build siano conservate per 18 mesi per la tracciabilità dell'audit.                      |    2    |   V   |
| 6.3.5 | Verifica che le dipendenze scadute inneschino pull request automatiche per aggiornare o forkare le versioni fissate.     |    3    |   D   |

---

## C6.4 Applicazione delle fonti attendibili

Consenti solo i download di artefatti da fonti verificate crittograficamente e approvate dall'organizzazione e blocca tutto il resto.

|   #   | Descrizione                                                                                                                                  | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.4.1 | Verifica che i pesi del modello, i set di dati e i contenitori siano scaricati solo da domini approvati o registri interni.                  |    1    |  D/V  |
| 6.4.2 | Verifica che le firme Sigstore/Cosign validino l'identità dell'editore prima che gli artefatti vengano memorizzati nella cache locale.       |    1    |  D/V  |
| 6.4.3 | Verifichi che i proxy di uscita blocchino i download di artefatti non autenticati per applicare la politica di origine attendibile.          |    2    |   D   |
| 6.4.4 | Verifica che le liste-consentite del repository vengano riviste trimestralmente, con evidenze della giustificazione aziendale per ogni voce. |    2    |   V   |
| 6.4.5 | Verifica che le violazioni delle policy inneschino la quarantena degli artefatti e il rollback delle esecuzioni di pipeline dipendenti.      |    3    |   V   |

---

## C6.5 Valutazione del rischio del dataset di terze parti

Valutare set di dati esterni per avvelenamento, bias e conformità legale, e monitorarli durante l'intero ciclo di vita.

|   #   | Descrizione                                                                                                                                              | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.5.1 | Verificare che i set di dati esterni subiscano una valutazione del rischio di avvelenamento (ad es. impronta digitale dei dati, rilevamento di outlier). |    1    |  D/V  |
| 6.5.2 | Verificare che le metriche di bias (parità demografica, parità di opportunità) siano calcolate prima dell'approvazione del set di dati.                  |    1    |   D   |
| 6.5.3 | Verificare che i termini di provenienza e di licenza per i set di dati siano registrati nelle voci ML‑BOM.                                               |    2    |   V   |
| 6.5.4 | Verifica che il monitoraggio periodico rilevi la deriva o la corruzione dei dataset ospitati.                                                            |    2    |   V   |
| 6.5.5 | Verificare che i contenuti vietati (copyright, PII) siano rimossi tramite pulizia automatizzata prima dell'addestramento.                                |    3    |   D   |

---

## C6.6 Monitoraggio degli attacchi alla catena di fornitura

Rilevare precocemente le minacce della supply‑chain attraverso feed CVE, analisi dei log di audit e simulazioni di red‑team.

|   #   | Descrizione                                                                                                                                                                            | Livello | Ruolo |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-----: | :---: |
| 6.6.1 | Verifica che i log di audit CI/CD vengano trasmessi ai rilevamenti SIEM per identificare prelievi di pacchetti anomali o passaggi di build manomessi.                                  |    1    |   V   |
| 6.6.2 | Verificare che i piani di risposta agli incidenti includano procedure di rollback per modelli o librerie compromessi.                                                                  |    2    |   D   |
| 6.6.3 | Verifica che le etichette di arricchimento delle informazioni sulle minacce contengano indicatori specifici per ML (ad es. IoCs di avvelenamento del modello) nel triage degli avvisi. |    3    |   V   |

---

## C6.7 ML‑BOM per gli artefatti del modello

Genera e firma digitalmente SBOM dettagliate specifiche per ML (ML‑BOM) affinché i consumatori a valle possano verificare l'integrità dei componenti al momento della messa in produzione.

|   #   | Descrizione                                                                                                                                | Livello | Ruolo |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :-----: | :---: |
| 6.7.1 | Verifica che ogni artefatto del modello pubblichi un ML‑BOM che elenchi set di dati, pesi, iperparametri e licenze.                        |    1    |  D/V  |
| 6.7.2 | Verificare che la generazione ML‑BOM e la firma Cosign siano automatizzate nell'integrazione continua (CI) e obbligatorie per il merge.    |    1    |  D/V  |
| 6.7.3 | Verifica che i controlli di completezza ML‑BOM falliscano la build se manca qualsiasi metadato del componente (hash, licenza).             |    2    |   D   |
| 6.7.4 | Verificare che i consumatori a valle possano interrogare ML-BOMs tramite API per convalidare i modelli importati in fase di distribuzione. |    2    |   V   |
| 6.7.5 | Verifica che i ML‑BOMs siano sotto controllo di versione e confrontati per rilevare modifiche non autorizzate.                             |    3    |   V   |

---

## Riferimenti

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

