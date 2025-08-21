# C8 Speicher, Einbettungen & Vektor-Datenbanksicherheit

## Steuerungsziel

Einbettungen und Vektorspeicher fungieren als das „lebendige Gedächtnis“ zeitgenössischer KI-Systeme, indem sie kontinuierlich benutzergelieferte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in Modellkontexte zurückspielen. Wenn dieses Gedächtnis unkontrolliert bleibt, kann es personenbezogene Daten (PII) preisgeben, Zustimmungen verletzen oder umgedreht werden, um den Originaltext zu rekonstruieren. Das Ziel dieser Kontrollfamilie ist es, Gedächtnispipelines und Vektordatenbanken so zu härten, dass der Zugriff nach dem Prinzip der minimalen Rechte erfolgt, Einbettungen datenschutzfreundlich sind, gespeicherte Vektoren ablaufen oder auf Abruf widerrufen werden können und das Gedächtnis pro Benutzer niemals Eingabeaufforderungen oder Ausgaben eines anderen Benutzers kontaminiert.

---

## C8.1 Zugriffskontrollen für Speicher- und RAG-Indizes

Durchsetzung feinkörniger Zugriffskontrollen auf jede Vektorsammlung.

|   #   | Beschreibung                                                                                                                                                                                      | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Verifizieren Sie, dass Zugriffssteuerungsregeln auf Zeilen- bzw. Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokument-Tag einschränken.                    |   1   |  D/V  |
| 8.1.2 | Überprüfen Sie, ob API-Schlüssel oder JWTs scoped Claims enthalten (z. B. Kollektion-IDs, Aktionsverben) und mindestens vierteljährlich rotiert werden.                                           |   1   |  D/V  |
| 8.1.3 | Stellen Sie sicher, dass Versuche zur Privilegienerweiterung (z. B. Abfragen zur Ähnlichkeit über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden. |   2   |  D/V  |
| 8.1.4 | Überprüfen Sie, ob die Vektor-Datenbank Protokolle über Subjektkennung, Operation, Vektor-ID/Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.                                            |   2   |  D/V  |
| 8.1.5 | Stellen Sie sicher, dass Zugriffsbeschlüsse auf Umgehungsfehler getestet werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.                                      |   3   |   V   |

---

## C8.2 Einbettungsbereinigung und Validierung

Vor der Vektorisierung Text auf personenbezogene Daten (PII) prüfen, schwärzen oder pseudonymisieren und gegebenenfalls die Einbettungen nachbearbeiten, um verbleibende Signale zu entfernen.

|   #   | Beschreibung                                                                                                                                                                                                         | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Stellen Sie sicher, dass PII und regulierte Daten durch automatisierte Klassifizierer erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.                                                     |   1   |  D/V  |
| 8.2.2 | Stellen Sie sicher, dass Einbettungspipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder isolieren.                                         |   1   |   D   |
| 8.2.3 | Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Privacy-Sanitization angewendet wird. |   2   |  D/V  |
| 8.2.4 | Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückruf der PII-Ausblendung, semantische Verschiebung) mindestens halbjährlich anhand von Referenzkorpora überprüft wird.                            |   2   |   V   |
| 8.2.5 | Stellen Sie sicher, dass Sanitierungskonfigurationen versionskontrolliert sind und Änderungen einer Peer-Review unterzogen werden.                                                                                   |   3   |  D/V  |

---

## C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO-"Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine rechtzeitige Löschung; Vektorspeicher müssen daher TTLs, dauerhafte Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

|   #   | Beschreibung                                                                                                                                                                                                       | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.3.1 | Stellen Sie sicher, dass jeder Vektor- und Metadatensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.                                      |   1   |  D/V  |
| 8.3.2 | Stellen Sie sicher, dass benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.                                                                |   1   |  D/V  |
| 8.3.3 | Überprüfen Sie, dass logische Löschungen von einer kryptografischen Vernichtung der Speicherblöcke gefolgt werden, falls die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssel-Tresor-Schlüssels. |   2   |   D   |
| 8.3.4 | Überprüfen Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf aus den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.                                                                 |   3   |  D/V  |

---

## C8.4 Verhinderung von Embedding-Inversion und -Leckage

Aktuelle Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Privacy-Neuron-Störung und Anwendungsschicht-Verschlüsselung—können die Inversionsraten auf Token-Ebene auf unter 5 % senken.

|   #   | Beschreibung                                                                                                                                                                                                       | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.4.1 | Verifizieren Sie, dass ein formales Bedrohungsmodell vorliegt, das Inversions-, Mitgliedschafts- und Attributinferenzangriffe abdeckt und jährlich überprüft wird.                                                 |   1   |   V   |
| 8.4.2 | Stellen Sie sicher, dass Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direkten Zugriffen durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt.                |   2   |  D/V  |
| 8.4.3 | Stellen Sie sicher, dass die Verteidigungsparameter (ε für DP, Rauschwert σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Tokenschutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten. |   3   |   V   |
| 8.4.4 | Stellen Sie sicher, dass Inversionsresistenz-Metriken Teil der Freigabekriterien für Modellaktualisierungen sind, wobei Regressionsbudgets definiert werden.                                                       |   3   |  D/V  |

---

## C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein Hauptrisiko bei RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden sichtbar machen.

|   #   | Beschreibung                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.5.1 | Stellen Sie sicher, dass jede Abrufabfrage vor der Weitergabe an die LLM-Eingabeaufforderung nach Mieter-/Benutzer-ID nachgefiltert wird.                                                                              |   1   |  D/V  |
| 8.5.2 | Überprüfen Sie, ob Sammlungsnamen oder namespaced IDs pro Benutzer oder Mandant gesalzen werden, damit Vektoren nicht über verschiedene Bereiche hinweg kollidieren können.                                            |   1   |   D   |
| 8.5.3 | Überprüfen Sie, dass Ähnlichkeitsergebnisse oberhalb eines konfigurierbaren Distanzschwellenwerts, die jedoch außerhalb des Geltungsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen. |   2   |  D/V  |
| 8.5.4 | Stellen Sie sicher, dass Multi-Tenant-Stresstests adversariale Anfragen simulieren, die versuchen, Dokumente außerhalb des zulässigen Bereichs abzurufen, und demonstrieren, dass keine Datenlecks entstehen.          |   2   |   V   |
| 8.5.5 | Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um eine kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.                           |   3   |  D/V  |

---

## C8.6 Fortschrittliche Sicherheitssysteme für den Arbeitsspeicher

Sicherheitskontrollen für komplexe Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.6.1 | Überprüfen Sie, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen.                             |   1   |  D/V  |
| 8.6.2 | Stellen Sie sicher, dass die Prozesse der Gedächtniskonsolidierung eine Sicherheitsvalidierung umfassen, um die Einspeisung bösartiger Erinnerungen durch Inhaltsbereinigung, Quellverifikation und Integritätsprüfungen vor der Speicherung zu verhindern.                                            |   2   |  D/V  |
| 8.6.3 | Überprüfen Sie, ob Speicherabfrageanfragen validiert und bereinigt werden, um die Extraktion unbefugter Informationen durch Analyse von Abfragemustern, Durchsetzung der Zugriffskontrolle und Ergebnisfilterung zu verhindern.                                                                        |   2   |  D/V  |
| 8.6.4 | Stellen Sie sicher, dass Gedächtnisvergessensmechanismen sensible Informationen mit kryptografischen Löschgarantien sicher löschen, indem Sie Schlüssel löschen, mehrfach überschreiben oder hardwarebasierte sichere Löschungen mit Verifikationszertifikaten verwenden.                              |   3   |  D/V  |
| 8.6.5 | Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Prüfprotokolle und automatische Warnungen verwendet werden, wenn sich der Speicherinhalt außerhalb normaler Betriebsbedingungen ändert. |   3   |  D/V  |

---

## Literaturverzeichnis

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

