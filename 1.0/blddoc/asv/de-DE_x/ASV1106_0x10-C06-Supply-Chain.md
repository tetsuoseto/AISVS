# C6 Lieferkettensicherheit für Modelle, Rahmenwerke und Daten

## Kontrollziel

KI-Lieferkettenangriffe nutzen Modelle, Frameworks oder Datensätze von Drittanbietern aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzuschleusen. Diese Kontrollen bieten End-to-End‑Provenienz, Schwachstellenmanagement und Überwachung, um den gesamten Modelllebenszyklus zu schützen.

---

## C6.1 vorgetrainte Modelle: Prüfung und Provenienz

Bewerten und Authentifizieren der Herkunft, Lizenzen und versteckten Verhaltensweisen von Drittanbieter-Modellen, bevor jegliche Feinabstimmung oder Bereitstellung erfolgt.

|   #   | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.1.1 | Verifizieren Sie, dass jedes Drittanbieter-Modellartefakt einen signierten Herkunftsnachweis enthält, der das Quell-Repository und den Commit-Hash identifiziert.                                |   1   |  D/V  |
| 6.1.2 | Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojaner-Auslöser überprüft werden.                                                  |   1   |  D/V  |
| 6.1.3 | Verifizieren Sie, dass Transfer‑Learning Feinabstimmungen eine adversariale Evaluierung bestehen, um versteckte Verhaltensweisen zu erkennen.                                                    |   2   |   D   |
| 6.1.4 | Überprüfen Sie, dass Modell‑Lizenzen, Exportkontrollkennzeichnungen und Datenherkunftsaussagen in einem ML‑BOM‑Eintrag verzeichnet sind.                                                         |   2   |   V   |
| 6.1.5 | Stellen Sie sicher, dass Modelle mit hohem Risiko (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) in Quarantäne bleiben, bis eine menschliche Überprüfung und Freigabe erfolgt. |   3   |  D/V  |

---

## C6.2 Rahmenwerk und Bibliotheken-Scan

Kontinuierlich ML-Frameworks und Bibliotheken auf CVEs und schädlichen Code scannen, um den Laufzeit-Stack sicher zu halten.

|   #   | Beschreibung                                                                                                                                              | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Überprüfen Sie, ob CI-Pipelines Abhängigkeits-Scanner für KI-Frameworks und kritische Bibliotheken ausführen.                                             |   1   |  D/V  |
| 6.2.2 | Stellen Sie sicher, dass kritische Schwachstellen (CVSS ≥ 7.0) die Freigabe von Produktions-Images blockieren.                                            |   1   |  D/V  |
| 6.2.3 | Überprüfen Sie, ob die statische Code-Analyse auf geforkten oder eingebundenen ML-Bibliotheken läuft.                                                     |   2   |   D   |
| 6.2.4 | Überprüfen Sie, ob Vorschläge für Framework-Upgrades eine Sicherheitsfolgenabschätzung enthalten, die sich auf öffentliche CVE-Feeds bezieht.             |   2   |   V   |
| 6.2.5 | Verifizieren Sie, dass Laufzeitsensoren bei unerwarteten Ladevorgängen dynamischer Bibliotheken, die vom signierten SBOM abweichen, einen Alarm auslösen. |   3   |   V   |

---

## C6.3 Abhängigkeits-Pinning und Verifizierung

Jede Abhängigkeit auf unveränderliche Hash-Werte festlegen und Builds reproduzieren, um identische, manipulationssichere Artefakte zu garantieren.

|   #   | Beschreibung                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.3.1 | Stellen Sie sicher, dass alle Paketmanager die Versionssperre über Lockfiles erzwingen.                                                       |   1   |  D/V  |
| 6.3.2 | Stellen Sie sicher, dass in Containerreferenzen unveränderliche Digest-Werte verwendet werden, anstelle von Tags, die veränderlich sind.      |   1   |  D/V  |
| 6.3.3 | Vergewissern Sie sich, dass Reproduzierbarkeitsprüfungen Hash-Werte über CI-Läufe hinweg vergleichen, um identische Ausgaben sicherzustellen. |   2   |   D   |
| 6.3.4 | Stellen Sie sicher, dass Build-Attestationen für 18 Monate zur Audit-Nachverfolgbarkeit gespeichert werden.                                   |   2   |   V   |
| 6.3.5 | Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull-Requests auslösen, um gepinnte Versionen zu aktualisieren oder zu forken.   |   3   |   D   |

---

## C6.4 Durchsetzung vertrauenswürdiger Quellen

Laden Sie Artefakte nur aus kryptografisch verifizierten, organisations‑genehmigten Quellen herunter und blockieren Sie alles andere.

|   #   | Beschreibung                                                                                                                                                 | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.4.1 | Stellen Sie sicher, dass Modellgewichte, Datensätze und Container ausschließlich von genehmigten Domains oder internen Registries heruntergeladen werden.    |   1   |  D/V  |
| 6.4.2 | Verifizieren Sie, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers validieren, bevor Artefakte lokal zwischengespeichert werden.               |   1   |  D/V  |
| 6.4.3 | Überprüfen Sie, dass Ausgangsproxies nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.    |   2   |   D   |
| 6.4.4 | Vergewissern Sie sich, dass die Allowlisten des Repositories vierteljährlich überprüft werden, mit Nachweis der geschäftlichen Begründung für jeden Eintrag. |   2   |   V   |
| 6.4.5 | Überprüfen Sie, ob Richtlinienverstöße die Quarantäne von Artefakten und das Rollback abhängiger Pipeline-Läufe auslösen.                                    |   3   |   V   |

---

## C6.5 Risikobewertung von Drittanbieterdatensätzen

Externe Datensätze auf Datenvergiftung, Verzerrung und rechtliche Konformität bewerten und sie während ihres gesamten Lebenszyklus überwachen.

|   #   | Beschreibung                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Stellen Sie sicher, dass externe Datensätze einer Poisoning-Risikobewertung unterzogen werden (z. B. Datenfingerprinting, Ausreißererkennung). |   1   |  D/V  |
| 6.5.2 | Überprüfen Sie, ob Bias-Metriken (demografische Parität, gleiche Chancen) vor der Genehmigung des Datensatzes berechnet werden.                |   1   |   D   |
| 6.5.3 | Überprüfen Sie, ob die Provenienz- und Lizenzbedingungen für Datensätze in ML‑BOM-Einträgen erfasst werden.                                    |   2   |   V   |
| 6.5.4 | Überprüfen Sie, ob regelmäßige Überwachung Drift oder Datenkorruption in gehosteten Datensätzen erkennt.                                       |   2   |   V   |
| 6.5.5 | Stellen Sie sicher, dass verbotene Inhalte (Urheberrecht, PII) vor dem Training durch automatisierte Bereinigung entfernt werden.              |   3   |   D   |

---

## C6.6 Überwachung von Lieferkettenangriffen

Frühzeitig Lieferkettenbedrohungen erkennen durch CVE-Feeds, Audit-Log-Analytik und Red-Team-Simulationen.

|   #   | Beschreibung                                                                                                                                                          | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.6.1 | Stellen Sie sicher, dass CI/CD-Auditprotokolle an SIEM-Erkennungen weitergeleitet werden, die sich auf anomale Paketabrufe oder manipulierte Build-Schritte beziehen. |   1   |   V   |
| 6.6.2 | Stellen Sie sicher, dass Incident-Response-Playbooks Rollback-Verfahren für kompromittierte Modelle oder Bibliotheken enthalten.                                      |   2   |   D   |
| 6.6.3 | Stellen Sie sicher, dass Threat‑Intel‑Enrichment‑Tags ML‑spezifische Indikatoren (z. B. IoCs zur Modellvergiftung) in der Alarm‑Triage kennzeichnen.                  |   3   |   V   |

---

## C6.7 ML‑BOM für Modellartefakte

Erzeuge und signiere detaillierte ML‑spezifische SBOMs (ML‑BOMs), damit nachgelagerte Verbraucher die Integrität der Komponenten zum Bereitstellungszeitpunkt überprüfen können.

|   #   | Beschreibung                                                                                                                                         | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Vergewissern Sie sich, dass jedes Modellartefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.        |   1   |  D/V  |
| 6.7.2 | Stellen Sie sicher, dass ML‑BOM-Erzeugung und Cosign-Signierung in der CI automatisiert sind und für das Merge erforderlich sind.                    |   1   |  D/V  |
| 6.7.3 | Überprüfen Sie, dass ML‑BOM‑Vollständigkeitsprüfungen den Build fehlschlagen lassen, wenn Metadaten einer Komponente (Hash, Lizenz) fehlen.          |   2   |   D   |
| 6.7.4 | Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über eine API abfragen können, um importierte Modelle während der Bereitstellung zu validieren. |   2   |   V   |
| 6.7.5 | Stellen Sie sicher, dass ML‑BOMs versionskontrolliert sind und auf Unterschiede verglichen werden, um unbefugte Änderungen zu erkennen.              |   3   |   V   |

---

## Referenzen

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

