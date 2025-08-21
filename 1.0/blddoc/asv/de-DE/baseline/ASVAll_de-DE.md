## Vorderseite

### Über den Standard

Der Artificial Intelligence Security Verification Standard (AISVS) ist ein gemeinschaftlich erstellter Katalog von Sicherheitsanforderungen, den Data Scientists, MLOps-Ingenieure, Softwarearchitekten, Entwickler, Tester, Sicherheitsexperten, Tool-Anbieter, Regulierungsbehörden und Anwender nutzen können, um vertrauenswürdige KI-gestützte Systeme und Anwendungen zu entwerfen, zu entwickeln, zu testen und zu verifizieren. Er bietet eine gemeinsame Sprache zur Spezifikation von Sicherheitskontrollen im gesamten KI-Lebenszyklus – von der Datenerfassung und Modellentwicklung bis hin zur Bereitstellung und laufenden Überwachung – sodass Organisationen die Widerstandsfähigkeit, den Datenschutz und die Sicherheit ihrer KI-Lösungen messen und verbessern können.

### Urheberrecht und Lizenz

Version 0.1 (Erster öffentlicher Entwurf – Arbeit im Gange), 2025  

![license](images/license.png)
Copyright © 2025 Das AISVS-Projekt.  

Veröffentlicht unter derCreative Commons Attribution‑ShareAlike 4.0 International License.
Für jegliche Wiederverwendung oder Verbreitung müssen Sie die Lizenzbedingungen dieses Werks deutlich an andere kommunizieren.

### Projektleiter

Jim Manico
Aras „Russ“ Memisyazici

### Mitwirkende und Prüfer

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS ist ein brandneuer Standard, der speziell entwickelt wurde, um die einzigartigen Sicherheitsherausforderungen von künstlichen Intelligenzsystemen zu adressieren. Während er sich von allgemeinen Sicherheits-Best-Practices inspirieren lässt, wurde jede Anforderung in AISVS von Grund auf entwickelt, um die Bedrohungslandschaft im Bereich KI abzubilden und Organisationen dabei zu unterstützen, sicherere und widerstandsfähigere KI-Lösungen zu entwickeln.

## Vorwort

Willkommen zum Artificial Intelligence Security Verification Standard (AISVS) Version 1.0!

### Einführung

Gegründet im Jahr 2025 durch eine gemeinschaftliche Kooperation definiert AISVS die Sicherheitsanforderungen, die bei der Gestaltung, Entwicklung, Bereitstellung und dem Betrieb moderner KI-Modelle, Pipelines und KI-basierter Dienste zu berücksichtigen sind.

AISVS v1.0 stellt die gemeinsame Arbeit seiner Projektleiter, Arbeitsgruppe und breiteren Community-Beitragenden dar, um eine pragmatische, überprüfbare Basis für die Sicherung von KI-Systemen zu schaffen.

Unser Ziel mit dieser Veröffentlichung ist es, AISVS einfach anwendbar zu machen, dabei jedoch den klar definierten Aufgabenbereich strikt einzuhalten und die sich schnell ändernde Risikolandschaft, die für KI einzigartig ist, gezielt anzugehen.

### Hauptziele für AISVS Version 1.0

Version 1.0 wird mit mehreren Leitprinzipien erstellt.

#### Gut definierter Umfang

Jede Anforderung muss mit dem Namen und der Mission von AISVS übereinstimmen:

Künstliche Intelligenz – Kontrollen werden auf der AI/ML-Ebene (Daten, Modell, Pipeline oder Inferenz) durchgeführt und liegen in der Verantwortung der AI-Fachleute.
Sicherheit – Anforderungen mindern direkt identifizierte Sicherheits-, Datenschutz- oder Sicherheitsrisiken.
Verifikation – Die Sprache ist so verfasst, dass die Konformität objektiv validiert werden kann.
Standard – Abschnitte folgen einer konsistenten Struktur und Terminologie, um eine kohärente Referenz zu bilden.
​
---

Durch die Einhaltung von AISVS können Organisationen die Sicherheitslage ihrer KI-Lösungen systematisch bewerten und stärken, wodurch eine Kultur der sicheren KI-Entwicklung gefördert wird.

## Verwendung des AISVS

Der Artificial Intelligence Security Verification Standard (AISVS) definiert Sicherheitsanforderungen für moderne KI-Anwendungen und -Dienste, wobei der Schwerpunkt auf Aspekten liegt, die unter der Kontrolle der Anwendungsentwickler stehen.

Der AISVS ist für alle vorgesehen, die die Sicherheit von KI-Anwendungen entwickeln oder bewerten, einschließlich Entwickler, Architekten, Sicherheitstechniker und Prüfer. Dieses Kapitel stellt die Struktur und Verwendung des AISVS vor, einschließlich seiner Verifizierungsstufen und vorgesehenen Anwendungsfälle.

### Sicherheitsüberprüfungsstufen für Künstliche Intelligenz

Das AISVS definiert drei aufsteigende Ebenen der Sicherheitsüberprüfung. Jede Ebene fügt Tiefe und Komplexität hinzu, sodass Organisationen ihre Sicherheitslage an das Risikoniveau ihrer KI-Systeme anpassen können.

Organisationen können auf Stufe 1 beginnen und nach und nach höhere Stufen annehmen, wenn die Sicherheitsreife und die Bedrohungsexposition zunehmen.

#### Definition der Ebenen

Jede Anforderung in AISVS v1.0 wird einem der folgenden Stufen zugewiesen:

 Anforderungen der Stufe 1

Level 1 umfasst die kritischsten und grundlegendsten Sicherheitsanforderungen. Diese konzentrieren sich darauf, häufige Angriffe zu verhindern, die nicht von anderen Voraussetzungen oder Schwachstellen abhängen. Die meisten Kontrollen der Stufe 1 sind entweder einfach umzusetzen oder so wichtig, dass der Aufwand gerechtfertigt ist.

 Level 2 Anforderungen

Level 2 befasst sich mit fortgeschritteneren oder weniger häufigen Angriffen sowie mit mehrschichtigen Abwehrmaßnahmen gegen weit verbreitete Bedrohungen. Diese Anforderungen können komplexere Logik beinhalten oder spezifische Voraussetzungen für Angriffe anvisieren.

 Anforderungen der Stufe 3

Level 3 umfasst Kontrollen, die typischerweise schwerer umzusetzen sind oder situativ anwendbar sind. Diese stellen oft Verteidigungsmechanismen in der Tiefe oder Abschwächungen gegen Nischen-, gezielte oder hochkomplexe Angriffe dar.

#### Rolle (D/V)

Jede AISVS-Anforderung wird entsprechend der Hauptzielgruppe gekennzeichnet:

D – Entwicklerorientierte Anforderungen
V – Anforderungen für Prüfer/Auditoren
D/V – Relevanz sowohl für Entwickler als auch für Prüfer

## C1 Schulungsdaten-Governance & Bias-Management

### Steuerungsziel

Trainingsdaten müssen so beschafft, verarbeitet und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness erhalten bleiben. Dies erfüllt gesetzliche Verpflichtungen und verringert Risiken von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinflussen könnten.

---

### C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

 #1.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Herkunft, Verwalter/Eigentümer, Lizenz, Erfassungsmethode, Nutzungsbeschränkungen und Verarbeitungshistorie) geführt wird.
 #1.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Trainingsdatenprozesse unnötige Merkmale, Attribute oder Felder ausschließen (z. B. nicht verwendete Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).
 #1.1.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Änderungen an Datensätzen einem protokollierten Genehmigungsworkflow unterliegen.
 #1.1.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Datensätze oder Teilmengen, sofern möglich, mit Wasserzeichen versehen oder mit Fingerabdrücken gekennzeichnet sind.

---

### C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und validieren Sie deren Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

 #1.2.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Zugriffskontrollen den Speicher für Trainingsdaten und die Pipelines schützen.
 #1.2.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass jeder Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeitpunkt und Aktion.
 #1.2.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand verschlüsselt sind, unter Verwendung von branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungspraktiken.
 #1.2.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass kryptographische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten sicherzustellen.
 #1.2.5    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass automatisierte Erkennungstechniken angewendet werden, um unbefugte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.
 #1.2.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.
 #1.2.7    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Versionen des Trainingsdatensatzes eindeutig identifiziert, unveränderlich gespeichert und auditierbar sind, um Rücksetzungen und forensische Analysen zu unterstützen.

---

### C1.3 Qualität, Integrität und Sicherheit der Trainingsdaten-Kennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

 #1.3.1    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität zu gewährleisten.
 #1.3.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Kennzeichnungsoberflächen und -plattformen strenge Zugriffskontrollen durchsetzen, manipulationssichere Prüfprotokolle aller Kennzeichnungsaktivitäten führen und vor unbefugten Modifikationen schützen.
 #1.3.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass sensible Informationen in Bezeichnungen auf Feldebene sowohl im Ruhezustand als auch bei der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.

---

### C1.4 Qualität und Sicherheit der Trainingsdaten gewährleisten

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebung, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

 #1.4.1    Ebene: 1    Rolle: D
 Überprüfen Sie, ob automatisierte Tests Formatfehler und Nullwerte bei jedem Import oder jeder bedeutenden Datenumwandlung erfassen.
 #1.4.2    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass LLM-Trainings- und Fine-Tuning-Pipelines eine Erkennung von Vergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Einbettungsanalyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügen von Backdoor-Triggern, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren.
 #1.4.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass geeignete Schutzmaßnahmen wie adversariales Training (unter Verwendung generierter adversarialer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und basierend auf der Risikobewertung für relevante Modelle abgestimmt sind.
 #1.4.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass automatisch generierte Labels (z. B. durch LLMs oder schwache Überwachung) Schwellenwerte für die Vertrauenswürdigkeit und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Vertrauenswürdigkeit zu erkennen.
 #1.4.5    Ebene: 3    Rolle: D
 Verifizieren Sie, dass automatisierte Tests bei jeder Datenaufnahme oder signifikanten Datenveränderung Label-Skews erfassen.

---

### C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie die vollständige Reise jedes einzelnen Datenpunkts von der Quelle bis zur Modelleingabe für Nachvollziehbarkeit und Vorfallreaktion.

 #1.5.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Abstammung jedes einzelnen Datenpunkts, einschließlich aller Transformationen, Augmentierungen und Zusammenführungen, dokumentiert ist und rekonstruiert werden kann.
 #1.5.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Stammdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.
 #1.5.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Rückverfolgbarkeit die über datenschutzfördernde oder generative Techniken erzeugten synthetischen Daten abdeckt und dass alle synthetischen Daten im gesamten Ablauf eindeutig gekennzeichnet und von realen Daten unterscheidbar sind.

---

### Literaturverzeichnis

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## C2 Benutzer-Eingabevalidierung

### Steuerungsziel

Robuste Validierung von Benutzereingaben ist eine Erstlinientaktik zum Schutz vor einigen der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten offenlegen oder das Modell zu unerlaubtem Verhalten lenken. Ohne spezielle Filter und hierarchische Anweisungen zeigen Forschungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, effektiv sein werden. Ebenso können subtile adversariale Störangriffe – wie Homoglyph-Tausch oder Leetspeak – die Entscheidungen eines Modells unauffällig verändern.

---

### C2.1 Abwehr von Prompt-Injektionen

Prompt Injection ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik setzen eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und Durchsetzung der Anweisungshierarchie ein.

 #2.1.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektionsmuster (Jailbreak-Stichwörter, "ignore previous", Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.
 #2.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überstimmen, selbst nach Erweiterung des Kontextfensters.
 #2.1.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass adversarielle Evaluationstests (z. B. Red Team "many-shot"-Prompts) vor jeder Modell- oder Prompt-Template-Freigabe durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Rückschritte.
 #2.1.4    Ebene: 2    Rolle: D
 Überprüfen Sie, ob Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Analysekontext bereinigt werden, bevor sie in die Hauptaufforderung eingefügt werden.
 #2.1.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filter-Regeln, Versionen der Klassifizierungsmodelle und Änderungen an der Blockliste versionskontrolliert und prüfbar sind.

---

### C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (NLP) sind weiterhin anfällig für subtile Störungen auf Zeichen- oder Wortebene, die Menschen häufig übersehen, aber von den Modellen oft falsch klassifiziert werden.

 #2.2.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass grundlegende Eingabenormalisierungsschritte (Unicode NFC, Homoglyph-Mapping, Entfernen von Leerzeichen) vor der Tokenisierung ausgeführt werden.
 #2.2.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßigen wiederholten Token oder abnormen Einbettungsdistanzen kennzeichnet.
 #2.2.3    Ebene: 2    Rolle: D
 Verifizieren Sie, dass die Inferenz-Pipeline optionale, durch adversariales Training gehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Distillation) für Hochrisiko-Endpunkte unterstützt.
 #2.2.4    Ebene: 2    Rolle: V
 Verifizieren Sie, dass vermutete adversariale Eingaben isoliert, mit vollständigen Nutzdaten (nach PII-Redaktion) protokolliert werden.
 #2.2.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen einen Release-Blocker auslösen.

---

### C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überlaufen von Eingaben über Felder hinweg und Ressourcenerschöpfung verursachen. Strikte Schemaüberprüfung ist ebenfalls eine Voraussetzung für die Durchführung deterministischer Werkzeugaufrufe.

 #2.3.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Prompt-Zusammenstellung validiert werden.
 #2.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einem sicheren Fehler abgelehnt werden und niemals stillschweigend abgeschnitten werden.
 #2.3.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enumerationswerte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.
 #2.3.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.
 #2.3.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Validierungsfehler mit geschwärzten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitstriangulation zu unterstützen.

---

### C2.4 Inhalts- und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Eingabeaufforderungen zu erkennen, die unzulässige Inhalte anfordern (wie illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und diese daran hindern, weiterverbreitet zu werden.

 #2.4.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinjustiert) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten.
 #2.4.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, sodass sie nicht an nachgelagerte LLM-Aufrufe weitergegeben werden.
 #2.4.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster einbezieht.
 #2.4.4    Ebene: 2    Rolle: D
 Überprüfen Sie, dass das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Beschränkungen) durch attributbasierte Regeln einhält, die zur Anforderungszeit aufgelöst werden.
 #2.4.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für SOC-Korrelation und zukünftige Red-Team-Wiederholungen enthalten.

---

### C2.5 Eingangsratebegrenzung und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie die Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

 #2.5.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob die Grenzwerte für Anfragen pro Benutzer, pro IP und pro API-Schlüssel für alle Eingabe-Endpunkte durchgesetzt werden.
 #2.5.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Burst- und anhaltenden Ratenbegrenzungen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.
 #2.5.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflutung) automatisierte Sperren oder Eskalationen auslösen.
 #2.5.4    Ebene: 3    Rolle: V
 Überprüfen Sie, ob Protokolle zur Missbrauchsprävention aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.

---

### C2.6 Multi-modale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

 #2.6.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden.
 #2.6.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganographische Nutzlasten gescannt werden.
 #2.6.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Bild-/Audioeingaben auf feindliche Störungen oder bekannte Angriffsmuster überprüft werden.
 #2.6.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass fehlerhafte Eingaben bei multimodaler Validierung protokolliert werden und Warnmeldungen zur Untersuchung auslösen.

---

### C2.7 Eingabeherkunft & Zuschreibung

KI-Systeme sollten die Prüfung, Nachverfolgung von Missbrauch und Einhaltung von Vorschriften unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

 #2.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) gekennzeichnet sind.
 #2.7.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben beibehalten und prüfbar sind.
 #2.7.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Prüfung oder Sperrung unterzogen werden.

---

### C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsverfahren anpassen und mit kompiliertem Musterabgleich Echtzeitschutz bieten.

 #2.8.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine leistungsstarke Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.
 #2.8.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Bedrohungserkennungssysteme separate Musterbibliotheken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, vertrauliche Daten, Systembefehle) verwalten.
 #2.8.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die adaptive Bedrohungserkennung Machine-Learning-Modelle beinhaltet, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.
 #2.8.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-Bedrohungsinformationsquellen die Musterbibliotheken automatisch mit neuen Angriffs-Signaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.
 #2.8.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Fehlalarmrate bei der Bedrohungserkennung kontinuierlich überwacht wird und die Musterspezifität automatisch angepasst wird, um Störungen legitimer Anwendungsfälle zu minimieren.
 #2.8.6    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die kontextbezogene Bedrohungsanalyse die Eingabequelle, das Benutzerverhaltensmuster und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.
 #2.8.7    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcennutzung) in Echtzeit überwacht und optimiert werden.

---

### C2.9 Multi-Modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Bedrohungserkennungstypen und Ressourcenisolation bereitstellen.

 #2.9.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass jede Eingabemodalität dedizierte Sicherheit-Validatoren mit dokumentierten Bedrohungsmustern (Text: Prompt Injection, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellenwerten besitzt.
 #2.9.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass multi-modale Eingaben in isolierten Sandboxes mit definierten Ressourcenbeschränkungen (Speicher, CPU, Verarbeitungszeit), die für jeden Modalitätstyp spezifisch sind, verarbeitet werden und in den Sicherheitsrichtlinien dokumentiert sind.
 #2.9.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von cross-modalen Angriffen koordinierte Angriffe über mehrere Eingabetypen hinweg identifiziert (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektion im Text) durch Korrelationsregeln und Alarmgenerierung.
 #2.9.4    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass Validierungsfehler bei Multi-Modalität eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsbewertungen und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst.
 #2.9.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob modalitätsspezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks, die über den Mindestanforderungen liegen, aktualisiert werden.

---

### Literaturverzeichnis

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## C3 Modell-Lebenszyklusverwaltung & Änderungssteuerung

### Steuerungsziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität während des gesamten Lebenszyklus – von der Entwicklung über die Bereitstellung bis hin zur Stilllegung – und ermöglicht eine schnelle Reaktion auf Vorfälle sowie die Aufrechterhaltung der Verantwortlichkeit für alle Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch den Einsatz kontrollierter Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

### C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität gelangen in Produktionsumgebungen.

 #3.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Implementierung kryptografisch von autorisierten Stellen signiert sind.
 #3.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Modells zum Zeitpunkt der Bereitstellung überprüft wird und dass Signaturprüfungsfehler das Laden des Modells verhindern.
 #3.1.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Modellherkunftsaufzeichnungen die Identität der genehmigenden Stelle, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit Bestehen/Nichtbestehen-Status und einen Erstellungszeitstempel enthalten.
 #3.1.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Modell-Artefakte semantische Versionsnummern (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.
 #3.1.5    Ebene: 2    Rolle: V
 Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.

---

### C3.2 Modellvalidierung & Testen

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

 #3.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsbewertungen mit zuvor vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen.
 #3.2.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Validierungsfehler die Bereitstellung des Modells automatisch blockieren, es sei denn, es liegt eine ausdrückliche Genehmigung zum Überschreiben von zuvor festgelegtem autorisiertem Personal mit dokumentierten geschäftlichen Begründungen vor.
 #3.2.3    Ebene: 2    Rolle: V
 Überprüfen Sie, ob die Testergebnisse kryptografisch signiert und unveränderlich mit dem zu validierenden Hash der spezifischen Modellversion verknüpft sind.
 #3.2.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung durch eine vorgesehene Sicherheitsinstanz innerhalb vorher vereinbarter Zeitrahmen erfordern.

---

### C3.3 Kontrollierte Bereitstellung & Rückrollen

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

 #3.3.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Produktionseinsätze schrittweise Rollout-Mechanismen implementieren (Canary-Deployments, Blue-Green-Deployments) mit automatisierten Rückroll-Auslösern basierend auf vorab vereinbarten Fehlerquoten, Latenzgrenzen oder Sicherheitswarnkriterien.
 #3.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vorgegebener organisatorischer Zeitfenster wiederherstellen.
 #3.3.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen vor der Modellaktivierung berechnen und die Bereitstellung bei jeglicher Abweichung fehlschlagen.
 #3.3.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Notabschaltfunktionen für das Modell die Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltschalter deaktivieren können.
 #3.3.5    Ebene: 2    Rolle: V
 Verifizieren Sie, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.

---

### C3.4 Verantwortlichkeit für Änderungen & Audit

Alle Änderungen im Modelllebenszyklus müssen nachvollziehbar und überprüfbar sein.

 #3.4.1    Ebene: 1    Rolle: V
 Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Prüfprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.
 #3.4.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob der Zugriff auf das Audit-Log eine entsprechende Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.
 #3.4.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten in Git-Repositories versionskontrolliert sind, wobei vor der Bereitstellung eine obligatorische Codeüberprüfung und Genehmigung durch festgelegte Prüfer erfolgt.
 #3.4.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Prüfprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb der Aufbewahrungsfrist zu ermöglichen.

---

### C3.5 Sichere Entwicklungspraktiken

Modellentwicklungs- und Trainingsprozesse müssen sichere Praktiken befolgen, um eine Kompromittierung zu verhindern.

 #3.5.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass die Entwicklungs-, Test- und Produktionsumgebungen für Modelle physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.
 #3.5.2    Ebene: 1    Rolle: D
 Verifizieren Sie, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.
 #3.5.3    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachverfolgbarkeit authentifiziert werden.
 #3.5.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert werden und vor der Verwendung im Training eine Genehmigung durch Peer Review erforderlich ist.

---

### C3.6 Modellstilllegung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

 #3.6.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Modell-Rückzugsprozesse automatisch Abhängigkeitsdiagramme scannen, alle konsumierenden Systeme identifizieren und vor der Außerdienststellung vorab vereinbarte Vorankündigungsfristen einhalten.
 #3.6.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass ausgemusterte Modellartefakte gemäß den dokumentierten Datenaufbewahrungsrichtlinien durch kryptografische Löschung oder mehrfaches Überschreiben sicher gelöscht werden, und bestätigen Sie dies mit verifizierten Vernichtungszertifikaten.
 #3.6.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Modell-Ruhestandsereignisse mit Zeitstempel und Akteursidentität protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.
 #3.6.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Notfallmodellstilllegung den Zugriff auf das Modell innerhalb vorab festgelegter Notfallreaktionszeiträume durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.

---

### Literaturverzeichnis

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## C4 Infrastruktur, Konfiguration und Bereitstellungssicherheit

### Steuerungsziel

Die KI-Infrastruktur muss durch sichere Konfiguration, Laufzeitisolation, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und -konfigurationen gelangen durch kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Audit-Trails aufrechterhalten, in die Produktion.

---

### C4.1 Laufzeitumgebungs-Isolierung

Verhindern Sie Container-Ausbrüche und Privilegienerweiterungen durch Kernel-Ebenen-Isolationsprimitive und obligatorische Zugriffskontrollen.

 #4.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten entfernen.
 #4.1.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vordefinierten Zulassungslisten, wobei Verstöße zur Beendigung des Containers und zur Generierung von Sicherheitswarnungen führen.
 #4.1.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.
 #4.1.4    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass die auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder ein gleichwertiges System) Versuche zur Privilegienerweiterung erkennt und die verantwortlichen Prozesse automatisch innerhalb der organisatorischen Reaktionszeitvorgaben beendet.
 #4.1.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass hochriskante KI-Arbeitslasten in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestationsüberprüfung ausgeführt werden.

---

### C4.2 Sichere Build- und Deployment-Pipelines

Gewährleisten Sie kryptografische Integrität und Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

 #4.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und das Zusammenführen bei CRITICAL- oder HIGH-Severity-Funden blockiert wird.
 #4.2.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Container-Builds mit identischen SHA256-Hashwerten über mehrere Builds hinweg reproduzierbar sind, und erstellen Sie SLSA Level 3 Herkunftszertifikate, die mit Sigstore signiert sind.
 #4.2.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs eingebettet haben und vor dem Push in das Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.
 #4.2.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Laufzeiten die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreiten.
 #4.2.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Ausführung des Containers validiert werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt.
 #4.2.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Build-Umgebungen in ephemeren Containern oder VMs ohne persistenten Speicher und mit Netzwerkisolierung von Produktions-VPCs ausgeführt werden.

---

### C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit Standard-Ablehnungsrichtlinien und verschlüsselter Kommunikation.

 #4.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Kubernetes NetworkPolicies oder ein Äquivalent eine Standardverweigerung für Ingress/Egress mit expliziten Erlaubnisregeln für die erforderlichen Ports (443, 8080, etc.) implementieren.
 #4.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.
 #4.3.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Positivlisten gefiltert wird und blockierte Anfragen protokolliert werden.
 #4.3.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei die Zertifikate gemäß der Organisationsrichtlinie rotiert werden und die Zertifikatsvalidierung durchgesetzt wird (keine Skip-Verify-Flags).
 #4.3.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und ausschließlich über NAT-Gateways oder Bastion-Hosts kommuniziert.

---

### C4.4 Geheimnisse & Verwaltung kryptographischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatische Rotation mit Zero-Trust-Zugriff.

 #4.4.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit Verschlüsselung im Ruhezustand unter Verwendung von AES-256 gespeichert werden.
 #4.4.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) erzeugt werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.
 #4.4.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass die Rotation von Geheimnissen automatisiert ist mit einem Zero-Downtime-Deployment und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.
 #4.4.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Container-Images mit Werkzeugen (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.
 #4.4.5    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Audit-Protokolle mit Benutzeridentitäten und Zeitstempeln dokumentiert wird.
 #4.4.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse über Kubernetes-Geheimnisse, eingehängte Volumes oder Init-Container injiziert werden, und gewährleisten Sie, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind.

---

### C4.5 KI-Arbeitslast-Sandboxing und Validierung

Isoliere nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

 #4.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.
 #4.5.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert werden.
 #4.5.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalyse zur Rückdohrerkennung umfasst.
 #4.5.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden.
 #4.5.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Golden Images neu erstellt werden, wobei eine vollständige Bereinigung des Dateisystems und des Speichers erfolgt.

---

### C4.6 Überwachung der Infrastruktursicherheit

Infrastruktur kontinuierlich mit automatischer Behebung und Echtzeit-Benachrichtigungen scannen und überwachen.

 #4.6.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITICAL-Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.
 #4.6.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen für fehlerhafte Prüfungen durchführt.
 #4.6.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass HIGH-Schweregrad-Schwachstellen gemäß den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, mit Notfallverfahren für aktiv ausgenutzte CVEs.
 #4.6.4    Ebene: 2    Rolle: V
 Überprüfen Sie, ob Sicherheitswarnungen mithilfe der Formate CEF oder STIX/TAXII mit automatischer Anreicherung in SIEM-Plattformen (Splunk, Elastic oder Sentinel) integriert werden.
 #4.6.5    Ebene: 3    Rolle: V
 Überprüfen Sie, dass Infrastrukturskennzahlen an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Managementberichten exportiert werden.
 #4.6.6    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Konfigurationsabweichungen gemäß den organisatorischen Überwachungsanforderungen mithilfe von Tools (Chef InSpec, AWS Config) erkannt werden, und führen Sie bei unautorisierten Änderungen eine automatische Rücksetzung durch.

---

### C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenverteilung durch Kontingente und Überwachung.

 #4.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die GPU/TPU-Auslastung überwacht wird, wobei bei organisatorisch festgelegten Schwellenwerten Alarme ausgelöst und basierend auf Kapazitätsmanagementrichtlinien automatische Skalierung oder Lastenausgleich aktiviert werden.
 #4.7.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob KI-Arbeitslastmetriken (Inference-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Monitoring-Anforderungen erfasst und mit der Auslastung der Infrastruktur korreliert werden.
 #4.7.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Kubernetes ResourceQuotas oder entsprechende Mechanismen einzelne Workloads gemäß den Ressourcenallokationsrichtlinien der Organisation mit durchgesetzten harten Grenzwerten begrenzen.
 #4.7.4    Ebene: 2    Rolle: V
 Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant mit Alarmen basierend auf den organisatorischen Budgetgrenzen und automatisierten Kontrollen bei Budgetüberschreitungen verfolgt.
 #4.7.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfrageverläufen erfolgt.
 #4.7.6    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Ressourcenerschöpfung die Circuit Breaker gemäß den organisatorischen Reaktionsanforderungen auslöst, einschließlich der Drosselung der Rate basierend auf Kapazitätsrichtlinien und der Arbeitslastisolierung.

---

### C4.8 Trennung der Umgebungen und Steuerung der Promotion

Durchsetzung strenger Umweltgrenzen mit automatisierten Fördertoren und Sicherheitsvalidierung.

 #4.8.1    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.
 #4.8.2    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass die Umgebungspromotion die Genehmigung durch organisatorisch definierte autorisierte Personen mit kryptografischen Signaturen und unveränderlichen Prüfpfaden erfordert.
 #4.8.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Produktionsumgebungen den SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanfragen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen erfordern.
 #4.8.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Änderungen an der Infrastruktur als Code vor dem Zusammenführen in den Hauptzweig Peer-Review, automatisierte Tests und Sicherheitsscans erfordern.
 #4.8.5    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert werden, die Generierung synthetischer Daten erfolgt oder eine vollständige Datenmaskierung mit Entfernung personenbezogener Daten (PII) überprüft wurde.
 #4.8.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Freigabetore automatisierte Sicherheitstests (SAST, DAST, Container-Scans) enthalten, wobei für die Genehmigung keine CRITICAL-Befunde zulässig sind.

---

### C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Fähigkeiten zur Katastrophenwiederherstellung.

 #4.9.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Infrastrukturkonfigurationen gemäß den organisatorischen Backup-Zeitplänen in geografisch getrennte Regionen gesichert werden, unter Anwendung der 3-2-1-Backup-Strategie.
 #4.9.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Backup-Systeme in isolierten Netzwerken mit separaten Anmeldedaten und air-gapped Speicher zur Ransomware-Abwehr betrieben werden.
 #4.9.3    Ebene: 2    Rolle: V
 Verifizieren Sie, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit automatisierten Tests getestet und validiert werden, wobei die RTO- und RPO-Ziele den organisatorischen Anforderungen entsprechen.
 #4.9.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit Modellgewichtswiederherstellung, GPU-Cluster-Neuaufbau und Dienstabhängigkeitskartierung umfasst.

---

### C4.10 Infrastruktur-Compliance & Governance

Gewährleisten Sie die Einhaltung von Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

 #4.10.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen gegen SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatisierter Beweissammlung bewertet wird.
 #4.10.2    Ebene: 2    Rolle: V
 Verifizieren Sie, dass die Infrastrukturdokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.
 #4.10.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung unterzogen werden, einschließlich regulatorischer Genehmigungsabläufe für risikoreiche Änderungen.

---

### C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

 #4.11.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird.
 #4.11.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mittels TPM 2.0, Intel TXT oder AMD SVM überprüft wird.
 #4.11.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob der GPU-Speicher zwischen Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen hardwarebasierten Partitionierung mit Speichersanierung zwischen den Aufgaben isoliert ist.
 #4.11.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die Lieferkette der KI-Hardware eine Herkunftsüberprüfung mit Herstellungszertifikaten und eine Validierung manipulationssicherer Verpackungen umfasst.
 #4.11.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) die KI-Modellgewichte und kryptografischen Schlüssel mit einer FIPS 140-2 Level 3- oder Common Criteria EAL4+-Zertifizierung schützen.

---

### C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

 #4.12.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mittels mutual TLS mit Gerätezertifikaten authentifizieren, die gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie regelmäßig ausgetauscht werden.
 #4.12.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und einer Rückrollschutzfunktion implementieren, um Firmware-Downgrade-Angriffe zu verhindern.
 #4.12.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.
 #4.12.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation von Edge zu Cloud Bandbreiten-Drosselung, Datenkompression und Offline-Betriebsfähigkeit mit sicherer lokaler Speicherung umfasst.

---

### C4.13 Sicherheit von Multi-Cloud- und Hybrid-Infrastrukturen

Sichern Sie KI-Workloads über mehrere Cloud-Anbieter und hybride Cloud-On-Premises-Bereitstellungen hinweg.

 #4.13.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.
 #4.13.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass der datenaustausch zwischen verschiedenen Cloud-Anbietern eine Ende-zu-Ende-Verschlüsselung mit kundenseitig verwalteten Schlüsseln verwendet und dass Datenresidenzkontrollen gemäß den jeweiligen Rechtsgebieten durchgesetzt werden.
 #4.13.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlichem Monitoring und Alerting implementieren.
 #4.13.4    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Verhinderung von Cloud-Anbieterbindung portierbare Infrastructure-as-Code, standardisierte APIs und Datenexportmöglichkeiten mit Formatkonvertierungstools umfasst.
 #4.13.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausbreitung von Ressourcen verhindern als auch unautorisierte Gebühren für Datenübertragungen zwischen Clouds unterbinden.

---

### C4.14 Infrastrukturautomatisierung & GitOps-Sicherheit

Sichere Automatisierungspipelines für Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

 #4.14.1    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass GitOps-Repositories signierte Commits mit GPG-Schlüsseln verlangen und Branch-Schutzregeln vorhanden sind, die direkte Pushes auf Haupt-Branches verhindern.
 #4.14.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Behebung und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für nicht autorisierte Änderungen ausgelöst werden.
 #4.14.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die automatisierte Infrastruktur-Bereitstellung eine Validierung der Sicherheitspolitik umfasst und die Bereitstellung bei nicht konformen Konfigurationen blockiert wird.
 #4.14.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Infrastruktur-Automatisierungsgeheimnisse durch externe Geheimnis-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.
 #4.14.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die selbstheilende Infrastruktur eine Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Interessengruppen umfasst.

---

### C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantengerechte Kryptographie und quantensichere Protokolle einsetzen.

 #4.15.1    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur NIST-zugelassene postquantische kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert.
 #4.15.2    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Quantenschlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.
 #4.15.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass kryptografische Agilitätsrahmen eine schnelle Migration zu neuen postquantumalgorithmen mit automatischer Zertifikats- und Schlüsseldrehung ermöglichen.
 #4.15.4    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Quantendrohungsmodellierung die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet, einschließlich dokumentierter Migrationszeitpläne und Risikobewertungen.
 #4.15.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase mit Leistungsüberwachung eine Defense-in-Depth bieten.

---

### C4.16 Vertrauliches Computing & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe hardwarebasierter vertrauenswürdiger Ausführungsumgebungen und Technologien für vertrauliches Computing.

 #4.16.1    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.
 #4.16.2    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mit hardwaregestützter Speicher­verschlüsselung isolieren.
 #4.16.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass die Remote-Attestierung die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Echtheit einer Ausführungsumgebung geladen werden.
 #4.16.4    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass vertrauliche KI-Inferenzdienste die Modellauslesung durch verschlüsselte Berechnungen mit versiegelten Modellgewichten und geschützter Ausführung verhindern.
 #4.16.5    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus sicherer Enklaven mit Remote-Attestierung und verschlüsselten Kommunikationskanälen verwaltet.
 #4.16.6    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Secure Multi-Party Computation (SMPC) kollaboratives AI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.

---

### C4.17 Zero-Knowledge Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

 #4.17.1    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings bestätigen, ohne Modellgewichte oder Trainingsdaten offenzulegen.
 #4.17.2    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass auf ZK basierende Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.
 #4.17.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderierte KI ermöglichen, ohne einzelne Datensätze offenzulegen.
 #4.17.4    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass Zero-Knowledge-Maschinelles Lernen (ZKML)-Systeme überprüfbare KI-Schlussfolgerungen mit kryptographischem Nachweis der korrekten Berechnung ermöglichen.
 #4.17.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Stapelverifikation und reduziertem Rechenaufwand bieten.

---

### C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

 #4.18.1    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die AI-Inferenzzeiten mithilfe von Konstantzeit-Algorithmen und Padding normalisiert werden, um timingbasierte Modell-Extraktionsangriffe zu verhindern.
 #4.18.2    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob der Schutz vor Leistungsanalyse Rauschinjektion, Filterung der Stromversorgung und zufällige Ausführungsmuster für KI-Hardware umfasst.
 #4.18.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die cache-basierte Seitenkanalabwehr Cache-Partitionierung, Randomisierung und Flush-Anweisungen verwendet, um Informationslecks zu verhindern.
 #4.18.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-artige Angriffe zu verhindern.
 #4.18.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob mikroraumarchitektonische Seitenkanalabwehrmaßnahmen spekulative Ausführungskontrollen und die Verschleierung von Speicherzugriffsmustern umfassen.

---

### C4.19 Neuromorphe und spezialisierte KI-Hardware-Sicherheit

Sichern Sie neuartige KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, maßgeschneiderter ASICs und optischer Rechensysteme.

 #4.19.1    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass die Sicherheit neuromorpher Chips die Verschlüsselung von Spike-Mustern, den Schutz von synaptischen Gewichten und die hardwarebasierte Validierung von Lernregeln umfasst.
 #4.19.2    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Manipulationsmechanismen und sicheres Konfigurationsladen mit authentifizierten Updates implementieren.
 #4.19.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass die benutzerdefinierte ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root of Trust und einen sicheren Schlüsselspeicher mit Manipulationsdetektion umfasst.
 #4.19.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.
 #4.19.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob hybride analog-digital KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung enthalten.

---

### C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

 #4.20.1    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen bei sensiblen KI-Arbeitslasten mit kryptografischer Integritätsprüfung und Leistungsüberwachung ermöglicht.
 #4.20.2    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass Systeme zur privaten Informationsabfrage Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, und dabei kryptographischen Schutz der Zugriffsmuster gewährleisten.
 #4.20.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Mehrparteienrechnung-Protokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.
 #4.20.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die datenschutzschonende Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwertkryptografie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.
 #4.20.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistung von datenschutzwahrendem Rechnen durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien aufrechterhalten bleiben.

---

### C4.15 Agent Framework Cloud-Integrationssicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises/Cloud-Architekturen.

 #4.15.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Integration von Cloud-Speicher End-to-End-Verschlüsselung mit agentengesteuerter Schlüsselverwaltung verwendet.
 #4.15.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden.
 #4.15.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung beinhaltet.
 #4.15.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die Anforderungen an den Datenstandort durch kryptografische Bestätigung der Speicherorte eingehalten werden.
 #4.15.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob Sicherheitsbewertungen des Cloud-Anbieters agentenspezifisches Bedrohungsmodellieren und Risikoanalyse enthalten.

---

### Literaturverzeichnis

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5 Zugriffskontrolle & Identität für KI-Komponenten & Benutzer

### Steuerungsziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und Laufzeiterzwingung nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur innerhalb explizit gewährter Bereiche mit Modellen, Daten und Rechenressourcen interagieren, wobei kontinuierliche Überprüfungs- und Auditfähigkeiten gewährleistet sind.

---

### C5.1 Identitätsmanagement & Authentifizierung

Errichten Sie kryptographisch gesicherte Identitäten für alle Entitäten mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

 #5.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale über einen zentralen unternehmensweiten Identitätsanbieter (IdP) mit OIDC/SAML-Protokollen authentifiziert werden, wobei eindeutige Identitäts-zu-Token-Zuordnungen verwendet werden (keine gemeinsamen Konten oder Anmeldedaten).
 #5.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass für risikoreiche Operationen (Modelleinführung, Gewichts-Export, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine erweiterte Authentifizierung mit Sitzungsnevalidierung erforderlich ist.
 #5.1.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass neue Berechtigte eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das produktive System erhalten.
 #5.1.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Zugriffskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und De-Provisioning-Workflows.
 #5.1.5    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und kryptografischen Ursprungsnachweis enthalten.

---

### C5.2 Ressourcenautorisierung & geringste Privilegien

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

 #5.2.1    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Zulassungslisten und Standard-Deny-Richtlinien durchsetzt.
 #5.2.2    Ebene: 1    Rolle: D/V
 Vergewissern Sie sich, dass das Prinzip der minimalen Rechte standardmäßig bei Dienstkonten durchgesetzt wird, beginnend mit Lesezugriffen, und dass eine dokumentierte geschäftliche Begründung für Schreibzugriffe erforderlich ist.
 #5.2.3    Ebene: 1    Rolle: V
 Überprüfen Sie, ob alle Änderungen der Zugangskontrolle mit genehmigten Änderungsanfragen verknüpft und unveränderlich protokolliert sind, einschließlich Zeitstempeln, Akteursidentitäten, Ressourcenkennungen und Berechtigungsdifferenzen.
 #5.2.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Datenklassifizierungsbezeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit einheitlicher Richtliniendurchsetzung übertragen werden.
 #5.2.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass unautorisierte Zugriffsversuche und Ereignisse zur Eskalation von Berechtigungen innerhalb von 5 Minuten Echtzeitwarnungen mit kontextbezogenen Metadaten an SIEM-Systeme auslösen.

---

### C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollsysteme (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

 #5.3.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder gleichwertig) ausgelagert sind, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist.
 #5.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich Benutzerfreigabestufe, Sensitivitätsklassifizierung der Ressource, Anforderungskontext, Mandantenisolation und zeitliche Einschränkungen.
 #5.3.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion bereitgestellt werden.
 #5.3.4    Ebene: 2    Rolle: V
 Überprüfen Sie, ob die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.
 #5.3.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches 5 Minuten für hochsensible Ressourcen und 1 Stunde für Standardressourcen mit Cache-Invalidierungsmöglichkeiten nicht überschreiten.

---

### C5.4 Sicherheitsdurchsetzung zur Laufzeit der Abfrage

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und zeilenbasierten Sicherheitsrichtlinien.

 #5.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Abfragen zur Vektordatenbank und SQL obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode.
 #5.4.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Richtlinien für die Zeilenebenen-Sicherheit (RLS) und Feldmaskierung mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.
 #5.4.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen „confused deputy attacks“ verhindern, indem Abfragen sofort abgebrochen werden und explizite Autorisierungsfehlercodes zurückgegeben werden, anstatt leere Ergebnismengen zu liefern.
 #5.4.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass die Latenz bei der Richtlinienbewertung kontinuierlich mit automatisierten Warnungen bei Zeitüberschreitungsbedingungen überwacht wird, die eine Umgehung der Autorisierung ermöglichen könnten.
 #5.4.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Abfrage-Wiederholmechanismen Autorisierungsrichtlinien neu bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.

---

### C5.5 Ausgabe-Filterung & Datenschutz (Data Loss Prevention)

Setzen Sie Nachbearbeitungskontrollen ein, um eine unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

 #5.5.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Nachinferenz-Filtermechanismen unautorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden.
 #5.5.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Zitate, Referenzen und Quellenangaben in den Modellausgaben anhand der Berechtigungen des Anrufers validiert werden und entfernen Sie diese, wenn ein unbefugter Zugriff festgestellt wird.
 #5.5.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Beschränkungen für Ausgabeformate (bereinigte PDFs, metadatenfreie Bilder, genehmigte Dateitypen) basierend auf Benutzerberechtigungsstufen und Datenklassifizierungen durchgesetzt werden.
 #5.5.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Redaktionsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.
 #5.5.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Hochrisiko-Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptographische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.

---

### C5.6 Mehrmandanten-Isolierung

Sichern Sie die kryptografische und logische Isolation zwischen Mandanten in gemeinsam genutzter KI-Infrastruktur.

 #5.6.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Arbeitsspeicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-getrennt sind und bei Mandantenlöschung oder Sitzungsbeendigung sicher gelöscht werden.
 #5.6.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandantenkennung enthält, die kryptografisch gegen den Sitzungs-Kontext und die Benutzerberechtigungen validiert wird.
 #5.6.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob Netzwerk-Richtlinien Standard-Deny-Regeln für die Kommunikation zwischen verschiedenen Mandanten innerhalb von Service Meshes und Container-Orchestrierungsplattformen umsetzen.
 #5.6.4    Ebene: 3    Rolle: D
 Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für vom Kunden verwaltete Schlüssel (CMK) und kryptografischer Isolierung zwischen den Datenspeichern der Mandanten.

---

### C5.7 Autonome Agenten-Autorisierung

Steuerung der Berechtigungen für KI-Agenten und autonome Systeme durch abgegrenzte Fähigkeitstoken und kontinuierliche Autorisierung.

 #5.7.1    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass autonome Agenten Scoped Capability Tokens erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Beschränkungen auflisten.
 #5.7.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Hochrisikofunktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, finanzielle Transaktionen) standardmäßig deaktiviert sind und zur Aktivierung eine ausdrückliche Autorisierung mit geschäftlicher Begründung erforderlich ist.
 #5.7.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und gewährleisten Sie, dass sie nicht offline gespeichert oder wiederverwendet werden können.
 #5.7.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass agenteninitiierte Aktionen eine sekundäre Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Audit-Protokollierung durchlaufen.
 #5.7.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.

---

### Literaturverzeichnis

#### Standards & Rahmenwerke

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Implementierungsleitfäden

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### KI-spezifische Sicherheit

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Lieferkettensicherheit für Modelle, Frameworks & Daten

### Steuerungsziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, Frameworks oder Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzufügen. Diese Kontrollen bieten eine durchgängige Herkunftsnachverfolgung, Schwachstellenmanagement und Überwachung, um den gesamten Modelllebenszyklus zu schützen.

---

### C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie Herkunft, Lizenzen und verborgene Verhaltensweisen von Modellen Dritter, bevor Sie eine Feinabstimmung oder Bereitstellung durchführen.

 #6.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Drittanbieter-Modellartefakt eine signierte Herkunftsaufzeichnung enthält, die das Quell-Repository und den Commit-Hash identifiziert.
 #6.1.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Modelle vor dem Import mithilfe automatisierter Werkzeuge auf bösartige Schichten oder Trojaner-Auslöser gescannt werden.
 #6.1.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob das Transfer-Learning-Feinabstimmung einer adversarialen Evaluation standhält, um verborgene Verhaltensweisen zu erkennen.
 #6.1.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Modelllizenzen, Exportkontrollkennzeichnungen und Angaben zur Datenherkunft in einem ML-BOM-Eintrag erfasst sind.
 #6.1.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Hochrisikomodelle (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe in Quarantäne bleiben.

---

### C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und Bibliotheken nach CVEs und bösartigem Code, um den Laufzeit-Stack sicher zu halten.

 #6.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass CI-Pipelines Abhängigkeits-Scanner auf AI-Frameworks und kritische Bibliotheken ausführen.
 #6.2.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass kritische Schwachstellen (CVSS ≥ 7.0) die Freigabe von Produktionsabbildern verhindern.
 #6.2.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebundenen ML-Bibliotheken ausgeführt wird.
 #6.2.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Framework-Upgrade-Vorschläge eine Bewertung der Sicherheitsauswirkungen enthalten, die sich auf öffentliche CVE-Feeds bezieht.
 #6.2.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksladungen, die von der signierten SBOM abweichen, Alarm schlagen.

---

### C6.3 Abhängigkeitsverankerung und -verifizierung

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationssichere Artefakte zu garantieren.

 #6.3.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob alle Paketmanager Versionssperrung durch Lockfiles erzwingen.
 #6.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass unveränderliche Digests anstelle von veränderlichen Tags in Containerreferenzen verwendet werden.
 #6.3.3    Ebene: 2    Rolle: D
 Überprüfen Sie, dass Reproduzierbarkeitsprüfungen Hashes über CI-Durchläufe hinweg vergleichen, um identische Ausgaben sicherzustellen.
 #6.3.4    Ebene: 2    Rolle: V
 Überprüfen Sie, ob Build-Bestätigungen für 18 Monate zur Prüfspuraufzeichnung gespeichert werden.
 #6.3.5    Ebene: 3    Rolle: D
 Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um gepinnte Versionen zu aktualisieren oder zu forken.

---

### C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlauben Sie den Download von Artefakten nur von kryptografisch verifizierten, von der Organisation genehmigten Quellen und blockieren Sie alles andere.

 #6.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registern heruntergeladen werden.
 #6.4.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers überprüfen, bevor Artefakte lokal zwischengespeichert werden.
 #6.4.3    Ebene: 2    Rolle: D
 Überprüfen Sie, dass Egress-Proxys nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.
 #6.4.4    Ebene: 2    Rolle: V
 Überprüfen Sie, ob die Repository-Zulassungslisten vierteljährlich mit Nachweisen der geschäftlichen Rechtfertigung für jeden Eintrag überprüft werden.
 #6.4.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob Richtlinienverstöße zur Isolierung von Artefakten und zum Rücksetzen abhängiger Pipeline-Ausführungen führen.

---

### C6.5 Risikobewertung von Drittanbieter-Datensätzen

Bewerten Sie externe Datensätze auf Manipulation, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

 #6.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass externe Datensätze einer Risikoanalyse auf Vergiftung unterzogen werden (z. B. Daten-Fingerprinting, Ausreißererkennung).
 #6.5.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.
 #6.5.3    Ebene: 2    Rolle: V
 Überprüfen Sie, dass Herkunft und Lizenzbedingungen für Datensätze in ML‑BOM-Einträgen erfasst sind.
 #6.5.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass die periodische Überwachung Drift oder Korruption in gehosteten Datensätzen erkennt.
 #6.5.5    Ebene: 3    Rolle: D
 Stellen Sie sicher, dass unzulässige Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Scrubbing entfernt werden.

---

### C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Lieferkettenbedrohungen frühzeitig durch CVE-Feeds, Audit-Log-Analysen und Red-Team-Simulationen.

 #6.6.1    Ebene: 1    Rolle: V
 Überprüfen Sie, dass CI/CD-Auditprotokolle an SIEM-Erkennungen für anomale Paketabrufe oder manipulierte Build-Schritte übertragen werden.
 #6.6.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Incident-Response-Playbooks Rücksetzverfahren für kompromittierte Modelle oder Bibliotheken enthalten.
 #6.6.3    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Bedrohungs‑Intel‑Anreicherung ML‑spezifische Indikatoren (z. B. Modellvergiftungs-IoCs) bei der Alarm‑Triage kennzeichnet.

---

### C6.7 ML‑BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, ML-spezifische SBOMs (ML-BOMs), damit nachgelagerte Nutzer die Integrität der Komponenten zum Zeitpunkt der Bereitstellung überprüfen können.

 #6.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Modell-Artefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.
 #6.7.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die ML-BOM-Erstellung und die Cosign-Unterzeichnung im CI automatisiert sind und für den Merge erforderlich sind.
 #6.7.3    Ebene: 2    Rolle: D
 Überprüfen Sie, dass die ML-BOM-Vollständigkeitsprüfungen den Build fehlschlagen lassen, wenn Metadaten einer Komponente (Hash, Lizenz) fehlen.
 #6.7.4    Ebene: 2    Rolle: V
 Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zum Bereitstellungszeitpunkt zu validieren.
 #6.7.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass ML‑BOMs versioniert und verglichen werden, um unautorisierte Änderungen zu erkennen.

---

### Literaturverzeichnis

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Modellverhalten, Ausgabekontrolle & Sicherheitsgarantie

### Steuerungsziel

Modelloutputs müssen strukturiert, zuverlässig, sicher, erklärbar und im Produktionsbetrieb kontinuierlich überwacht werden. Dadurch werden Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen reduziert, während das Vertrauen der Nutzer und die Einhaltung gesetzlicher Vorschriften erhöht werden.

---

### C7.1 Ausgabeformatdurchsetzung

Strikte Schemata, eingeschränkte Dekodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte sich ausbreiten.

 #7.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Antwortschemas (z. B. JSON Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus.
 #7.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die eingeschränkte Dekodierung (Stoppzeichen, Regex, Max-Tokens) aktiviert ist, um Überläufe oder Prompt-Injection-Seitenkanäle zu verhindern.
 #7.1.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.
 #7.1.4    Ebene: 3    Rolle: V
 Überprüfen Sie, dass fehlerhafte Ausgabereignisse protokolliert, mit einer Ratenbegrenzung versehen und im Monitoring angezeigt werden.

---

### C7.2 Halluzinationserkennung und -minderung

Unsicherheitsabschätzung und Ausweichstrategien begrenzen erfundene Antworten.

 #7.2.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob tokenbasierte Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.
 #7.2.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Antworten unterhalb einer konfigurierbaren Vertrauensschwelle Fallback-Workflows auslösen (z. B. retrieval-augmented generation, sekundäres Modell oder menschliche Überprüfung).
 #7.2.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Vorfälle von Halluzinationen mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungs-Pipelines weitergeleitet werden.
 #7.2.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.
 #7.2.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.

---

### C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

 #7.3.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Pre- und Post-Generation-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren.
 #7.3.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort ausgeführt werden; Verstöße lösen einen Datenschutzvorfall aus.
 #7.3.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Vertraulichkeitstags (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg übertragen werden, um ein Auslaufen in Text, Bildern oder Code zu verhindern.
 #7.3.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Versuche zur Umgehung des Filters oder Hochrisikoklassifizierungen eine sekundäre Genehmigung oder eine erneute Benutzerauthentifizierung erfordern.
 #7.3.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Kontext von Benutzeralter und -rolle widerspiegeln.

---

### C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungsschranken verhindern Missbrauch und übermäßige Autonomie.

 #7.4.1    Ebene: 1    Rolle: D
 Überprüfen Sie, dass benutzerbezogene und API-Schlüssel-bezogene Kontingente Anfragen, Token und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.
 #7.4.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkanrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Beteiligung erfordern.
 #7.4.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass cross-modale Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht verwendet werden können, um bösartigen Inhalt zu schmuggeln.
 #7.4.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass die Tiefe der Agentendelegation, Rekursionsgrenzen und erlaubte Werkzeuglisten explizit konfiguriert sind.
 #7.4.5    Ebene: 3    Rolle: V
 Überprüfen Sie, dass die Verletzung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Erfassung aussendet.

---

### C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Nutzer und die interne Fehlersuche.

 #7.5.1    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikoabschätzung dies für angemessen hält.
 #7.5.2    Ebene: 2    Rolle: D/V
 Vergewissern Sie sich, dass generierte Erklärungen keine sensiblen Systemanweisungen oder proprietären Daten preisgeben.
 #7.5.3    Ebene: 3    Rolle: D
 Überprüfen Sie, ob das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und diese für autorisierte Prüfungen speichert.
 #7.5.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Erklärungsartefakte zusammen mit Modellversionen versioniert werden, um die Nachprüfbarkeit zu gewährleisten.

---

### C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt die Lücke zwischen Entwicklung und Produktion.

 #7.6.1    Ebene: 1    Rolle: D
 Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform gestreamt werden.
 #7.6.2    Ebene: 1    Rolle: V
 Stellen Sie sicher, dass für jede Sicherheitsmetrik Warnschwellen definiert sind, einschließlich Eskalationspfade für Bereitschaftsdienste.
 #7.6.3    Ebene: 2    Rolle: V
 Überprüfen Sie, ob Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.
 #7.6.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regelaktualisierungen zurückfließen.
 #7.6.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Überwachungspipelines einem Penetrationstest unterzogen und zugangskontrolliert sind, um das Auslaufen sensibler Protokolle zu vermeiden.

---

### 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabevalidierung und Nachvollziehbarkeit durchsetzen.

 #7.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung von illegalen, schädlichen oder nicht einvernehmlichen Deepfake-Medien (z. B. Bild, Video, Audio) verbieten.
 #7.7.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Eingabeaufforderungen auf Versuche gefiltert werden, Nachahmungen zu erzeugen, sexuell explizite Deepfakes zu erstellen oder Medien darzustellen, die reale Personen ohne deren Zustimmung zeigen.
 #7.7.3    Ebene: 2    Rolle: V
 Überprüfen Sie, ob das System Perceptual Hashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Material zu verhindern.
 #7.7.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um eine nachgelagerte Rückverfolgbarkeit zu gewährleisten.
 #7.7.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversariale Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird an Überwachungssysteme gemeldet.

### Literaturverzeichnis

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Speicher, Einbettungen & Vektor-Datenbanksicherheit

### Steuerungsziel

Einbettungen und Vektorspeicher fungieren als das „lebendige Gedächtnis“ zeitgenössischer KI-Systeme, indem sie kontinuierlich benutzergelieferte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in Modellkontexte zurückspielen. Wenn dieses Gedächtnis unkontrolliert bleibt, kann es personenbezogene Daten (PII) preisgeben, Zustimmungen verletzen oder umgedreht werden, um den Originaltext zu rekonstruieren. Das Ziel dieser Kontrollfamilie ist es, Gedächtnispipelines und Vektordatenbanken so zu härten, dass der Zugriff nach dem Prinzip der minimalen Rechte erfolgt, Einbettungen datenschutzfreundlich sind, gespeicherte Vektoren ablaufen oder auf Abruf widerrufen werden können und das Gedächtnis pro Benutzer niemals Eingabeaufforderungen oder Ausgaben eines anderen Benutzers kontaminiert.

---

### C8.1 Zugriffskontrollen für Speicher- und RAG-Indizes

Durchsetzung feinkörniger Zugriffskontrollen auf jede Vektorsammlung.

 #8.1.1    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass Zugriffssteuerungsregeln auf Zeilen- bzw. Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokument-Tag einschränken.
 #8.1.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob API-Schlüssel oder JWTs scoped Claims enthalten (z. B. Kollektion-IDs, Aktionsverben) und mindestens vierteljährlich rotiert werden.
 #8.1.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Versuche zur Privilegienerweiterung (z. B. Abfragen zur Ähnlichkeit über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden.
 #8.1.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Vektor-Datenbank Protokolle über Subjektkennung, Operation, Vektor-ID/Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.
 #8.1.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Zugriffsbeschlüsse auf Umgehungsfehler getestet werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.

---

### C8.2 Einbettungsbereinigung und Validierung

Vor der Vektorisierung Text auf personenbezogene Daten (PII) prüfen, schwärzen oder pseudonymisieren und gegebenenfalls die Einbettungen nachbearbeiten, um verbleibende Signale zu entfernen.

 #8.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass PII und regulierte Daten durch automatisierte Klassifizierer erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.
 #8.2.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Einbettungspipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder isolieren.
 #8.2.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Privacy-Sanitization angewendet wird.
 #8.2.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückruf der PII-Ausblendung, semantische Verschiebung) mindestens halbjährlich anhand von Referenzkorpora überprüft wird.
 #8.2.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Sanitierungskonfigurationen versionskontrolliert sind und Änderungen einer Peer-Review unterzogen werden.

---

### C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO-"Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine rechtzeitige Löschung; Vektorspeicher müssen daher TTLs, dauerhafte Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

 #8.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jeder Vektor- und Metadatensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.
 #8.3.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.
 #8.3.3    Ebene: 2    Rolle: D
 Überprüfen Sie, dass logische Löschungen von einer kryptografischen Vernichtung der Speicherblöcke gefolgt werden, falls die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssel-Tresor-Schlüssels.
 #8.3.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf aus den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.

---

### C8.4 Verhinderung von Embedding-Inversion und -Leckage

Aktuelle Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Privacy-Neuron-Störung und Anwendungsschicht-Verschlüsselung—können die Inversionsraten auf Token-Ebene auf unter 5 % senken.

 #8.4.1    Ebene: 1    Rolle: V
 Verifizieren Sie, dass ein formales Bedrohungsmodell vorliegt, das Inversions-, Mitgliedschafts- und Attributinferenzangriffe abdeckt und jährlich überprüft wird.
 #8.4.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direkten Zugriffen durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt.
 #8.4.3    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die Verteidigungsparameter (ε für DP, Rauschwert σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Tokenschutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten.
 #8.4.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Inversionsresistenz-Metriken Teil der Freigabekriterien für Modellaktualisierungen sind, wobei Regressionsbudgets definiert werden.

---

### C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein Hauptrisiko bei RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden sichtbar machen.

 #8.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Abrufabfrage vor der Weitergabe an die LLM-Eingabeaufforderung nach Mieter-/Benutzer-ID nachgefiltert wird.
 #8.5.2    Ebene: 1    Rolle: D
 Überprüfen Sie, ob Sammlungsnamen oder namespaced IDs pro Benutzer oder Mandant gesalzen werden, damit Vektoren nicht über verschiedene Bereiche hinweg kollidieren können.
 #8.5.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Ähnlichkeitsergebnisse oberhalb eines konfigurierbaren Distanzschwellenwerts, die jedoch außerhalb des Geltungsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.
 #8.5.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Multi-Tenant-Stresstests adversariale Anfragen simulieren, die versuchen, Dokumente außerhalb des zulässigen Bereichs abzurufen, und demonstrieren, dass keine Datenlecks entstehen.
 #8.5.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um eine kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.

---

### C8.6 Fortschrittliche Sicherheitssysteme für den Arbeitsspeicher

Sicherheitskontrollen für komplexe Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

 #8.6.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen.
 #8.6.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Prozesse der Gedächtniskonsolidierung eine Sicherheitsvalidierung umfassen, um die Einspeisung bösartiger Erinnerungen durch Inhaltsbereinigung, Quellverifikation und Integritätsprüfungen vor der Speicherung zu verhindern.
 #8.6.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Speicherabfrageanfragen validiert und bereinigt werden, um die Extraktion unbefugter Informationen durch Analyse von Abfragemustern, Durchsetzung der Zugriffskontrolle und Ergebnisfilterung zu verhindern.
 #8.6.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Gedächtnisvergessensmechanismen sensible Informationen mit kryptografischen Löschgarantien sicher löschen, indem Sie Schlüssel löschen, mehrfach überschreiben oder hardwarebasierte sichere Löschungen mit Verifikationszertifikaten verwenden.
 #8.6.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Prüfprotokolle und automatische Warnungen verwendet werden, wenn sich der Speicherinhalt außerhalb normaler Betriebsbedingungen ändert.

---

### Literaturverzeichnis

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Autonome Orchestrierung & Agentisches Handeln Sicherheit

### Steuerungsziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb begrenzter Kosten- und Risikoschwellen liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Missbrauch von Werkzeugen, Erkennung von Agentenschleifen, Übernahme der Kommunikation, Identitätsfälschung, Schwarmmanipulation und Manipulation der Absicht.

---

### 9.1 Agent Aufgabenplanung & Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Überprüfungen für privilegierte Aktionen.

 #9.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass maximale Rekursionstiefe, Breite, Echtzeit, Tokens und monetäre Kosten pro Agentenausführung zentral konfiguriert und versionskontrolliert sind.
 #9.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, finanzielle Überweisungen) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern.
 #9.1.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob Echtzeit-Ressourcenmonitore eine Unterbrechung durch einen Circuit-Breaker auslösen, wenn eine Budgetschwelle überschritten wird, und dadurch eine weitere Aufgabenerweiterung stoppen.
 #9.1.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Circuit-Breaker-Ereignisse mit Agenten-ID, auslösender Bedingung und erfasstem Planstatus für die forensische Überprüfung protokolliert werden.
 #9.1.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Sicherheitstests Budgeterschöpfungs- und Ausreißer-Plan-Szenarien abdecken und einen sicheren Abbruch ohne Datenverlust bestätigen.
 #9.1.6    Ebene: 3    Rolle: D
 Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code ausgedrückt und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.

---

### 9.2 Werkzeug-Plugin-Sandboxing

Isolieren Sie Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

 #9.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Tool/Plugin innerhalb eines Betriebssystems, Containers oder eines WASM-Level-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird.
 #9.2.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Ressourcenkontingente (CPU, Speicher, Festplatte, Netzwerk-Ausgang) und Ausführungszeitüberschreitungen durchgesetzt und protokolliert werden.
 #9.2.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Tool-Binärdateien oder Deskriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.
 #9.2.4    Ebene: 2    Rolle: V
 Überprüfen Sie, dass Sandboxtelemetrie an ein SIEM übertragen wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Warnmeldungen aus.
 #9.2.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Hochrisiko-Plugins vor der Produktionsbereitstellung einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden.
 #9.2.6    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Fluchtversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung unter Quarantäne gestellt wird.

---

### 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte rekursive Agent-zu-Agent-Aufrufe und Kostenexplosionen.

 #9.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.
 #9.3.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Agenten eine eindeutige Aufrufgraph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.
 #9.3.3    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass kumulative Recheneinheiten- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits bricht die Kette ab.
 #9.3.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die formale Analyse oder Model Checking das Fehlen von unbeschränkter Rekursion in Agentenprotokollen nachweist.
 #9.3.5    Ebene: 3    Rolle: D
 Überprüfen Sie, ob Schleifen-Abbruchereignisse Alarme erzeugen und kontinuierliche Verbesserungsmetriken speisen.

---

### 9.4 Protokollebene-Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Übernahmen oder Manipulationen zu verhindern.

 #9.4.1    Ebene: 1    Rolle: D/V
 Verifizieren Sie, dass alle Nachrichten von Agent zu Werkzeug und von Agent zu Agent authentifiziert sind (z. B. mittels gegenseitigem TLS oder JWT) und Ende-zu-Ende verschlüsselt sind.
 #9.4.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Schemata streng validiert werden; unbekannte Felder oder fehlerhaft formatierte Nachrichten werden abgelehnt.
 #9.4.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nachrichten-Nutzlast einschließlich der Werkzeugparameter abdecken.
 #9.4.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass der Replay-Schutz (Nonces oder Zeitstempelfenster) auf der Protokollebene durchgesetzt wird.
 #9.4.5    Ebene: 3    Rolle: V
 Überprüfen Sie, dass Protokollimplementierungen Fuzzing und statische Analyse auf Injektions- oder Deserialisierungsfehler durchlaufen.

---

### 9.5 Agenten-Identität & Manipulationssicherheit

Stellen Sie sicher, dass Aktionen zuordenbar und Änderungen erkennbar sind.

 #9.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Agenteninstanz eine eindeutige kryptografische Identität (Schlüsselpaar oder hardwarebasierte Anmeldeinformationen) besitzt.
 #9.5.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Agentenaktionen signiert und mit einem Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nicht-Abstreitbarkeit.
 #9.5.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass manipulationssichere Protokolle in einem nur-anfügbaren oder einmal beschreibbaren Medium gespeichert werden.
 #9.5.4    Ebene: 3    Rolle: D
 Überprüfen Sie, ob Identitätsschlüssel gemäß einem definierten Zeitplan und bei Kompromittierungsindikatoren rotieren.
 #9.5.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.

---

### 9.6 Risikominderung bei Multi-Agenten-Schwärmen

Mildern Sie Gefahren durch kollektives Verhalten durch Isolation und formale Sicherheitsmodellierung.

 #9.6.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten, die in unterschiedlichen Sicherheitsdomänen operieren, in isolierten Laufzeit-Sandboxes oder Netzwerksegmenten ausgeführt werden.
 #9.6.2    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Schwarmverhalten modelliert und formal auf Lebendigkeit und Sicherheit vor der Bereitstellung verifiziert werden.
 #9.6.3    Ebene: 3    Rolle: D
 Überprüfen Sie, ob Laufzeit-Monitore emergente unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und korrigierende Maßnahmen einleiten.

---

### 9.7 Benutzer- und Tool-Authentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede durch Agenten ausgelöste Aktion.

 #9.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale gegenüber nachgelagerten Systemen authentifizieren und niemals Endbenutzeranmeldeinformationen wiederverwenden.
 #9.7.2    Ebene: 2    Rolle: D
 Verifizieren Sie, dass fein abgestimmte Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er dabei übermitteln darf.
 #9.7.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.
 #9.7.4    Ebene: 3    Rolle: D
 Überprüfen Sie, dass delegierte Berechtigungen automatisch ablaufen und nach Ablauf der Zeitspanne oder bei Änderung des Umfangs eine erneute Zustimmung erforderlich ist.

---

### 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und Integritätsschutz für alle Nachrichten zwischen Agenten, um Abhören und Manipulationen zu verhindern.

 #9.8.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass gegenseitige Authentifizierung und perfekte Vorwärtsgeheimnis-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.
 #9.8.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Fehler führen zu Warnungen und die Nachricht wird verworfen.
 #9.8.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.
 #9.8.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass die formale Verifikation oder Model-Checking bestätigt, dass Protokoll-Zustandsautomaten nicht in unsichere Zustände gebracht werden können.

---

### 9.9 Intent-Überprüfung & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

 #9.9.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Pre-Execution Constraint Solver vorgeschlagene Aktionen anhand von fest codierten Sicherheits- und Richtlinienregeln überprüfen.
 #9.9.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Maßnahmen mit hoher Auswirkung (finanziell, zerstörerisch, datenschutzsensitiv) eine ausdrückliche Intentbestätigung des initiierenden Benutzers erfordern.
 #9.9.3    Ebene: 2    Rolle: V
 Überprüfen Sie, dass Postconditionsprüfungen validieren, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebenwirkungen erreicht haben; Abweichungen lösen eine Rücksetzung aus.
 #9.9.4    Ebene: 3    Rolle: V
 Verifizieren Sie, dass formale Methoden (z. B. Modellüberprüfung, Theorembeweis) oder eigenschaftsbasierte Tests demonstrieren, dass Agentenpläne alle angegebenen Einschränkungen erfüllen.
 #9.9.5    Ebene: 3    Rolle: D
 Stellen Sie sicher, dass Vorfälle von Intent-Mismatch oder Constraint-Verletzungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.

---

### 9.10 Sicherheit der Agenten-Reasoning-Strategie

Sichere Auswahl und Ausführung verschiedener Denkstrategien, einschließlich ReAct, Chain-of-Thought und Tree-of-Thoughts Ansätzen.

 #9.10.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass die Auswahl der Argumentationsstrategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und dass identische Eingaben innerhalb desselben Sicherheitskontexts zu identischen Strategiewahlen führen.
 #9.10.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) eine dedizierte Eingabevalidierung, Ausgabe-Säuberung und spezifische Ausführungszeitbegrenzungen entsprechend ihrem kognitiven Ansatz aufweist.
 #9.10.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Übergänge der Denkstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabemerkmalen, Werten der Auswahlkriterien und Ausführungsmetadaten zur Rekonstruktion der Prüfspur.
 #9.10.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass das Tree-of-Thoughts-Reasoning Verzweigungsstornierungsmechanismen umfasst, die die Exploration beenden, wenn Richtlinienverletzungen, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.
 #9.10.5    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass ReAct (Reason-Act-Observe)-Zyklen Validierungskontrollpunkte in jeder Phase enthalten: Verifizierung des Denkschritts, Autorisierung der Aktion und Bereinigung der Beobachtung vor dem Fortfahren.
 #9.10.6    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Leistungskennzahlen der Schlussfolgerungsstrategie (Ausführungszeit, Ressourcennutzung, Ausgabequalität) überwacht werden und automatisierte Alarme ausgelöst werden, wenn die Kennzahlen über die konfigurierten Schwellenwerte hinaus abweichen.
 #9.10.7    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.
 #9.10.8    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitstests der Denkstrategie Fuzzing mit fehlerhaften Eingaben, adversarielle Eingabeaufforderungen, die zum Erzwingen eines Strategiewechsels entworfen wurden, sowie Grenzwerttests für jeden kognitiven Ansatz umfassen.

---

### 9.11 Agent-Lebenszykluszustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Audit-Trails und definierten Wiederherstellungsverfahren.

 #9.11.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Agenteninitalisierung die Einrichtung einer kryptografischen Identität mit hardwaregestützten Anmeldeinformationen sowie unveränderliche Startprüfprotokolle enthält, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter umfassen.
 #9.11.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Agentenzustandsübergänge kryptografisch signiert, mit einem Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich auslösender Ereignisse, Hash des vorherigen Zustands, Hash des neuen Zustands und durchgeführter Sicherheitsprüfungen.
 #9.11.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass die Agenten-Abschaltverfahren eine sichere Speicherlöschung mittels kryptographischer Löschung oder mehrfacher Überschreibung, die Zurückziehung von Berechtigungen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen.
 #9.11.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob Agent-Wiederherstellungsmechanismen die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Beschädigung automatisch auf bekannte fehlerfreie Zustände zurücksetzen, wobei automatisierte Warnmeldungen und manuelle Genehmigungsanforderungen verwendet werden.
 #9.11.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Persistenzmechanismen der Agenten sensible Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und eine sichere Schlüsselrotation nach konfigurierbaren Zeitplänen (maximal 90 Tage) mit Null-Ausfallzeit-Bereitstellung implementieren.

---

### 9.12 Sicherheitsrahmen für Werkzeugintegration

Sicherheitskontrollen für das dynamische Laden von Tools, deren Ausführung und Ergebnisvalidierung mit definierten Risikobewertungen und Genehmigungsverfahren.

 #9.12.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Tool-Beschreibungen Sicherheitsmetadaten enthalten, die erforderliche Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcengrenzen (CPU, Speicher, Netzwerk) und Validierungsanforderungen, die in den Tool-Manifests dokumentiert sind, angeben.
 #9.12.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Ausführungsergebnisse von Tools vor der Integration anhand der erwarteten Schemas (JSON-Schema, XML-Schema) und der Sicherheitsrichtlinien (Ausgabe-Sanitierung, Datenklassifizierung) validiert werden, und implementieren Sie dabei Zeitlimitbeschränkungen sowie Fehlerbehandlungsverfahren.
 #9.12.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcenverbrauch und Rückgabecodes mit strukturierter Protokollierung für die SIEM-Integration.
 #9.12.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Werkzeuglade-Mechanismen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung sowie Berechtigungsverifizierung vor der Ausführung implementieren.
 #9.12.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Sicherheitsbewertungen von Tools für neue Versionen automatisch ausgelöst werden, mit obligatorischen Genehmigungsschritten einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, einschließlich dokumentierter Genehmigungskriterien und SLA-Anforderungen.

---

#### Literaturverzeichnis

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Gegnerische Robustheit & Datenschutzverteidigung

### Steuerungsziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben, wenn sie Angriffen wie Umgehung, Rückschluss, Extraktion oder Vergiftung ausgesetzt sind.

---

### 10.1 Modellabstimmung und Sicherheit

Schützen Sie vor schädlichen oder gegen Richtlinien verstoßenden Ausgaben.

 #10.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Alignment-Test-Suite (Red-Team-Aufforderungen, Jailbreak-Tests, nicht erlaubte Inhalte) versionskontrolliert ist und bei jeder Modellfreigabe ausgeführt wird.
 #10.1.2    Ebene: 1    Rolle: D
 Überprüfen Sie, dass Verweigerungs- und Sicherheitsabschluss-Schutzvorrichtungen durchgesetzt werden.
 #10.1.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob ein automatisierter Evaluator die Rate schädlicher Inhalte misst und Rückschritte, die über einen festgelegten Schwellenwert hinausgehen, kennzeichnet.
 #10.1.4    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.
 #10.1.5    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachung kritische Bereiche abdecken.

---

### 10.2 Härtung gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes adversariales Training und Bewertung anhand von Benchmarks sind derzeit die besten Verfahren.

 #10.2.1    Ebene: 1    Rolle: D
 Überprüfen Sie, dass Projekt-Repositorys Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.
 #10.2.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines blockierende Warnungen auslöst.
 #10.2.4    Ebene: 3    Rolle: V
 Verifizieren Sie, dass zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken.
 #10.2.5    Ebene: 3    Rolle: V
 Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Verlust der Robustheit zu bestätigen.

---

### 10.3 Maßnahmen zur Minderung von Mitgliedschaftsinferenz

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsdatensatz enthalten war. Differentielle Privatsphäre und das Maskieren von Konfidenz-Scores bleiben die effektivsten bekannten Schutzmaßnahmen.

 #10.3.1    Ebene: 1    Rolle: D
 Überprüfen Sie, ob eine Entropie-Regularisierung pro Abfrage oder Temperaturskalierung übermäßig selbstsichere Vorhersagen reduziert.
 #10.3.2    Ebene: 2    Rolle: D
 Verifizieren Sie, dass das Training eine ε-begrenzte differentielle private Optimierung für sensible Datensätze verwendet.
 #10.3.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Angriffssimulationen (Shadow-Modell oder Black-Box) einen Angriff-AUC ≤ 0,60 auf zurückgehaltenen Daten zeigen.

---

### 10.4 Widerstand gegen Modell-Inversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen betonen die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen.

 #10.4.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie bei Bedarf Buckets oder Einweg-Transformationen.
 #10.4.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Abfrage-Ratenbeschränkungen wiederholte adaptive Abfragen vom selben Prinzipal drosseln.
 #10.4.3    Ebene: 2    Rolle: D
 Verifizieren Sie, dass das Modell mit datenschutzwahrendem Rauschen trainiert wurde.

---

### 10.5 Modell-Extraktionsabwehr

Erkennen und Verhindern unautorisierter Klone. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

 #10.5.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Inferenz-Gateways globale und pro API-Schlüssel angepasste Grenzwerte für die Anfragerate durchsetzen, die auf den Memorierungsschwellenwert des Modells abgestimmt sind.
 #10.5.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und zur Eingabe-Mehrzahligkeit einen automatischen Extraktionsdetektor speisen.
 #10.5.3    Ebene: 2    Rolle: V
 Überprüfen Sie, ob fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1.000 Abfragen gegen einen verdächtigen Klon nachgewiesen werden können.
 #10.5.4    Ebene: 3    Rolle: D
 Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.
 #10.5.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob Extraction-Alert-Ereignisse die anstößigen Abfragen enthalten und in Incident-Response-Playbooks integriert sind.

---

### 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Erkennen und Neutralisieren von mit Hintertüren verseuchten oder vergifteten Eingaben.

 #10.6.1    Ebene: 1    Rolle: D
 Verifizieren Sie, dass Eingaben vor der Modellausführung durch einen Anomalieerkenner (z. B. STRIP, Konsistenzbewertung) geprüft werden.
 #10.6.2    Ebene: 1    Rolle: V
 Stellen Sie sicher, dass die Detektorschwellenwerte an sauberen/verseuchten Validierungssets so eingestellt sind, dass weniger als 5 % falsch positive Ergebnisse erzielt werden.
 #10.6.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob Eingaben, die als vergiftet markiert sind, Soft-Blocking und menschliche Überprüfungs-Workflows auslösen.
 #10.6.4    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Detektoren mit adaptiven, triggerlosen Backdoor-Angriffen einem Stresstest unterzogen werden.
 #10.6.5    Ebene: 3    Rolle: D
 Stellen Sie sicher, dass Metriken zur Erkennungseffizienz protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.

---

### 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Aktualisierungen von Sicherheitsrichtlinien basierend auf Bedrohungsinformationen und Verhaltensanalysen.

 #10.7.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion erhalten bleibt.
 #10.7.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.
 #10.7.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzverfahren.
 #10.7.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf Risikokontext und Verhaltensmustern anpassen.
 #10.7.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Nachweispfade für die Überprüfung durch das Sicherheitsteam enthalten.

---

### 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

 #10.8.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.
 #10.8.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Reflektionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch adversarielle Eingaben zu verhindern.
 #10.8.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Kompromittierungen in den Denkprozessen von Agenten identifiziert.
 #10.8.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass reflektionsbasierte Sicherheitswarnungen eine erweiterte Überwachung und potenzielle menschliche Interventionsprozesse auslösen.
 #10.8.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.

---

### 10.9 Evolution & Selbstverbesserungssicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

 #10.9.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Selbstmodifikationsfähigkeiten auf festgelegte sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.
 #10.9.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Evolutionsvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.
 #10.9.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Selbstverbesserungsmechanismen Rücksetzfunktionen mit Integritätsprüfung enthalten.
 #10.9.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.
 #10.9.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen für die Konvergenz.

---

#### Literaturverzeichnis

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Datenschutz und Verwaltung persönlicher Daten

### Steuerungsziel

Gewährleisten Sie strenge Datenschutzgarantien im gesamten KI-Lebenszyklus—Erhebung, Training, Inferenz und Vorfallreaktion—sodass personenbezogene Daten nur mit eindeutiger Einwilligung, auf das notwendige Minimum beschränkt, nachweislich gelöscht und mit formalen Datenschutzgarantien verarbeitet werden.

---

### 11.1 Anonymisierung & Datenminimierung

 #11.1.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass direkte und Quasi-Identifikatoren entfernt oder gehasht werden.
 #11.1.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Alarm schlagen, wenn die Schwellenwerte unter die Richtlinie fallen.
 #11.1.3    Ebene: 2    Rolle: V
 Verifizieren Sie, dass Modell-Feature-Importance-Berichte keine Identifikator-Lecks über ε = 0,01 gegenseitige Information hinaus nachweisen.
 #11.1.4    Ebene: 3    Rolle: V
 Überprüfen Sie, dass formale Beweise oder Zertifizierungen für synthetische Daten ein Re-Identifikationsrisiko von ≤ 0,05 zeigen, selbst bei Linkage-Angriffen.

---

### 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

 #11.2.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Löschanfragen von Betroffenen in Bezug auf Daten auf rohe Datensätze, Checkpoints, Einbettungen, Protokolle und Backups innerhalb von Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden.
 #11.2.2    Ebene: 2    Rolle: D
 Verifizieren Sie, dass "Machine-Unlearning"-Routinen physisch neu trainieren oder eine angenäherte Entfernung durch zertifizierte Unlearning-Algorithmen durchführen.
 #11.2.3    Ebene: 2    Rolle: V
 Verifizieren Sie, dass die Auswertung des Schattenmodells beweist, dass vergessene Datensätze weniger als 1 % der Ausgaben nach dem Unlearning beeinflussen.
 #11.2.4    Ebene: 3    Rolle: V
 Verifizieren Sie, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden prüfbar sind.

---

### 11.3 Differential-Privacy-Schutzmaßnahmen

 #11.3.1    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Datenschutz-Verlust-Abrechnungs-Dashboards Alarm schlagen, wenn der kumulative ε die Richtliniengrenzen überschreitet.
 #11.3.2    Ebene: 2    Rolle: V
 Verifizieren Sie, dass Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10 % des angegebenen Werts schätzen.
 #11.3.3    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen und Einbettungen nach dem Training abdecken.

---

### 11.4 Zweckbindung & Schutz vor Umfangserweiterung

 #11.4.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass jeder Datensatz und jeder Modell-Checkpoint einen maschinenlesbaren Zweck-Tag trägt, der mit der ursprünglichen Einwilligung übereinstimmt.
 #11.4.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Laufzeitüberwachungen Abfragen erkennen, die mit dem deklarierten Zweck nicht übereinstimmen, und eine sanfte Ablehnung auslösen.
 #11.4.3    Ebene: 3    Rolle: D
 Überprüfen Sie, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.
 #11.4.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass formelle Rückverfolgbarkeitsnachweise zeigen, dass jeder Lebenszyklus personenbezogener Daten im genehmigten Umfang verbleibt.

---

### 11.5 Einwilligungsmanagement & rechtmäßige Basisverfolgung

 #11.5.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro betroffener Person aufzeichnet.
 #11.5.2    Ebene: 2    Rolle: D
 Überprüfen Sie, ob APIs Zustimmungstoken bereitstellen; Modelle müssen den Geltungsbereich des Tokens vor der Inferenz validieren.
 #11.5.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungspipelines innerhalb von 24 Stunden stoppen.

---

### 11.6 Föderiertes Lernen mit Datenschutzkontrollen

 #11.6.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Client-Updates vor der Aggregation eine lokale Differential-Privacy-Rauschaddition verwenden.
 #11.6.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients offenlegen.
 #11.6.3    Ebene: 2    Rolle: V
 Vergewissern Sie sich, dass eine gegen Vergiftung resistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.
 #11.6.4    Ebene: 3    Rolle: V
 Überprüfen Sie, dass formale Beweise das gesamte ε-Budget mit weniger als 5 Nutzungsverlust nachweisen.

---

#### Literaturverzeichnis

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Überwachung, Protokollierung & Anomalieerkennung

### Steuerungsziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Transparenz darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, bewertet und daraus gelernt werden kann.

### C12.1 Anforderungs- und Antwortprotokollierung

 #12.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit geeigneten Metadaten (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion) protokolliert werden.
 #12.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Sicherungsverfahren gespeichert werden.
 #12.1.3    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Log-Speichersysteme Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen, die in Logs enthalten sind, zu schützen.
 #12.1.4    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben automatisch vor der Protokollierung geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen.
 #12.1.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfilteraktionen mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Inhaltsmoderationssystemen zu ermöglichen.
 #12.1.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der Protokolle z. B. durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.

---

### C12.2 Missbrauchserkennung und Alarmierung

 #12.2.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Versuche zur Prompt-Injektion und adversariale Eingaben mithilfe einer signaturbasierten Erkennung erkennt und meldet.
 #12.2.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass das System mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert ist.
 #12.2.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifische Kontextinformationen enthalten, wie Modellkennungen, Vertrauenswerte und Entscheidungen von Sicherheitsfiltern.
 #12.2.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abtastverhalten erkennt.
 #12.2.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-Benachrichtigungsmechanismen Sicherheitsteams informieren, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.
 #12.2.6    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modellextraktionsangriffe.
 #12.2.7    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob automatisierte Abläufe zur Vorfallsreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.

---

### C12.3 Modell-Drift-Erkennung

 #12.3.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.
 #12.3.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder signifikant von den Baselines abweichen.
 #12.3.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Überwachungen zur Halluzinationserkennung Instanzen identifizieren und markieren, wenn Modell-Ausgaben faktisch falsche, inkonsistente oder erfundene Informationen enthalten.

---

### C12.4 Leistungs- und Verhaltens-Telemetrie

 #12.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass operative Metriken wie Anfragelatenz, Tokenverbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.
 #12.4.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Erfolgs- und Fehlerquoten mit Kategorisierung der Fehlertypen und deren Ursachen nachverfolgt werden.
 #12.4.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Überwachung der Ressourcenauslastung die Nutzung von GPU/CPU, den Speicherverbrauch und die Speicheranforderungen umfasst, mit Alarmierung bei Überschreitung von Schwellenwerten.

---

### C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

 #12.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Vorfallreaktionspläne speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversariale Angriffe berücksichtigen.
 #12.5.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Incident-Response-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachkenntnisse haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.
 #12.5.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Analyse nach Vorfällen Überlegungen zur Modellerneuerung, Aktualisierungen der Sicherheitsfilter und die Integration gewonnener Erkenntnisse in die Sicherheitskontrollen umfasst.

---

### C12.5 Erkennung von Leistungsabfällen bei KI

Überwachen und Erkennen von Leistungs- und Qualitätsverschlechterungen von KI-Modellen im Laufe der Zeit.

 #12.5.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass die Modellgenauigkeit, Präzision, Sensitivität und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.
 #12.5.2    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von Datenverschiebungen Änderungen in der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.
 #12.5.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob die Konzeptdrifterkennung Veränderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.
 #12.5.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Leistungsabfälle automatisierte Warnmeldungen auslösen und Workflows für das Nachtrainieren oder den Austausch des Modells starten.
 #12.5.5    Ebene: 3    Rolle: V
 Überprüfen Sie, ob die Ursachenanalyse für Leistungsverluste Leistungseinbrüche mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.

---

### C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

 #12.6.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob die Visualisierungsdaten des DAG bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.
 #12.6.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Zugriffskontrollen der Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer Entscheidungswege von Agenten und Nachverfolgungen der Entscheidungsbegründungen einsehen können.
 #12.6.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermethoden geschützt ist.
 #12.6.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.
 #12.6.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen rate-begrenzt und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.

---

### C12.7 Proaktive Überwachung von Sicherheitsverhalten

Erkennung und Prävention von Sicherheitsbedrohungen durch proaktive Verhaltensanalyse von Agenten.

 #12.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit einer Risikobewertungsintegration sicherheitsgeprüft sind.
 #12.7.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob autonome Initiativauslöser die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.
 #12.7.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass proaktive Verhaltensmuster auf mögliche Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.
 #12.7.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfprotokollen erfordern.
 #12.7.5    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten erkennt, die auf eine Kompromittierung hinweisen könnten.

---

### Literaturverzeichnis

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menschliche Aufsicht, Verantwortlichkeit & Governance

### Steuerungsziel

Dieses Kapitel enthält Anforderungen zur Aufrechterhaltung der menschlichen Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen, um Erklärbarkeit, Transparenz und ethische Steuerung über den gesamten Lebenszyklus der KI sicherzustellen.

---

### C13.1 Notschalter- und Übersteuerungsmechanismen

Stellen Sie Abschalt- oder Rücksetzwege bereit, wenn ein unsicheres Verhalten des KI-Systems festgestellt wird.

 #13.1.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob ein manueller Not-Aus-Mechanismus vorhanden ist, um die KI-Modell-Inferenz und die Ausgabe sofort zu stoppen.
 #13.1.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass die Überschreibungssteuerungen nur für autorisiertes Personal zugänglich sind.
 #13.1.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob Rollback-Verfahren auf vorherige Modellversionen oder sicheren Betriebsmodi zurückgesetzt werden können.
 #13.1.4    Ebene: 3    Rolle: V
 Stellen Sie sicher, dass Überschreibemechanismen regelmäßig getestet werden.

---

### C13.2 Mensch-in-der-Schleife Entscheidungs-Kontrollpunkte

Menschliche Genehmigungen erforderlich, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

 #13.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.
 #13.2.2    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Risiko-Schwellenwerte klar definiert sind und automatisch menschliche Überprüfungsabläufe auslösen.
 #13.2.3    Ebene: 2    Rolle: D
 Überprüfen Sie, ob zeitkritische Entscheidungen Rückfallverfahren haben, wenn innerhalb der erforderlichen Zeiträume keine menschliche Genehmigung eingeholt werden kann.
 #13.2.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Eskalationsverfahren klare Autoritätsstufen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.

---

### C13.3 Kette der Verantwortlichkeit & Prüfpfadfähigkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

 #13.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschlichen Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden.
 #13.3.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Auditprotokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.

---

### C13.4 Erklärbare KI-Techniken

Oberflächen-Feature-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

 #13.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format bereitstellen.
 #13.4.2    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass die Qualität der Erklärung durch menschliche Evaluationsstudien und Metriken validiert wird.
 #13.4.3    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass Merkmalswichtungswerte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.
 #13.4.4    Ebene: 3    Rolle: V
 Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, sofern dies für den Anwendungsfall und die Domäne zutreffend ist.

---

### C13.5 Modellkarten & Nutzungshinweise

Führen Sie Modellkarten für den beabsichtigten Einsatz, Leistungskennzahlen und ethische Überlegungen.

 #13.5.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass Modellkarten die beabsichtigten Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi dokumentieren.
 #13.5.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.
 #13.5.3    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden.
 #13.5.4    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.

---

### C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Vertrauenswerte oder Entropiemaße in den Antworten.

 #13.6.1    Ebene: 1    Rolle: D
 Stellen Sie sicher, dass KI-Systeme mit ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.
 #13.6.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.
 #13.6.3    Ebene: 2    Rolle: V
 Verifizieren Sie, dass Methoden zur Quantifizierung von Unsicherheiten kalibriert und anhand von Referenzdaten validiert werden.
 #13.6.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Unsicherheitsfortpflanzung in mehrstufigen KI-Workflows erhalten bleibt.

---

### C13.7 Transparenzberichte für Endnutzer

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereit.

 #13.7.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Datenschutzrichtlinien und Praktiken zum Management der Benutzerzustimmung den Interessengruppen klar kommuniziert werden.
 #13.7.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.
 #13.7.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessenem Detail offenlegen.

#### Literaturverzeichnis

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Anhang A: Glossar

Dieses umfassende Glossar bietet Definitionen wichtiger Begriffe aus den Bereichen KI, ML und Sicherheit, die im gesamten AISVS verwendet werden, um Klarheit und ein gemeinsames Verständnis zu gewährleisten.

Adversariales Beispiel: Eine absichtlich erzeugte Eingabe, die ein KI-Modell dazu veranlassen soll, einen Fehler zu machen, häufig durch das Hinzufügen subtiler Störungen, die für Menschen nicht wahrnehmbar sind.
​
Gegnerische Robustheit – Gegnerische Robustheit in der KI bezieht sich auf die Fähigkeit eines Modells, seine Leistung aufrechtzuerhalten und nicht durch absichtlich gestaltete, bösartige Eingaben, die Fehler verursachen sollen, getäuscht oder manipuliert zu werden.
​
Agent – KI-Agenten sind Softwaresysteme, die KI einsetzen, um Ziele zu verfolgen und Aufgaben im Auftrag von Benutzern zu erledigen. Sie zeigen Fähigkeiten wie Schlussfolgerungen, Planung und Gedächtnis und besitzen ein gewisses Maß an Autonomie, um Entscheidungen zu treffen, zu lernen und sich anzupassen.
​
Agentische KI: KI-Systeme, die mit einem gewissen Grad an Autonomie operieren können, um Ziele zu erreichen, wobei sie oft Entscheidungen treffen und Maßnahmen ergreifen, ohne direkte menschliche Eingriffe.
​
Attributbasierte Zugriffskontrolle (ABAC): Ein Zugriffskontrollparadigma, bei dem Autorisierungsentscheidungen auf Attributen des Benutzers, der Ressource, der Aktion und der Umgebung basieren und zur Abfragezeit ausgewertet werden.
​
Backdoor-Angriff: Eine Art von Datenvergiftungsangriff, bei dem das Modell darauf trainiert wird, auf bestimmte Auslöser auf eine spezifische Weise zu reagieren, während es sich ansonsten normal verhält.
​
Bias: Systematische Fehler in den Ausgaben von KI-Modellen, die zu unfairen oder diskriminierenden Ergebnissen für bestimmte Gruppen oder in spezifischen Kontexten führen können.
​
Bias-Ausnutzung: Eine Angriffstechnik, die bekannte Verzerrungen in KI-Modellen ausnutzt, um Ausgaben oder Ergebnisse zu manipulieren.
​
Cedar: Amazons Richtliniensprache und Engine für fein abgestufte Berechtigungen, die bei der Implementierung von ABAC für KI-Systeme verwendet wird.
​
Chain of Thought: Eine Technik zur Verbesserung des Denkvermögens in Sprachmodellen durch Generieren von Zwischenschritten des Denkprozesses vor der Ausgabe einer endgültigen Antwort.
​
Circuit Breakers: Mechanismen, die den Betrieb von KI-Systemen automatisch stoppen, wenn bestimmte Risikoschwellen überschritten werden.
​
Datenleckage: Unbeabsichtigte Offenlegung sensibler Informationen durch Ausgaben oder Verhalten von KI-Modellen.
​
Datenvergiftung: Die absichtliche Korruption von Trainingsdaten zur Beeinträchtigung der Modellintegrität, häufig um Hintertüren zu installieren oder die Leistung zu verschlechtern.
​
Differenzielle Privatsphäre – Differenzielle Privatsphäre ist ein mathematisch rigoroser Rahmen zur Veröffentlichung statistischer Informationen über Datensätze, während gleichzeitig die Privatsphäre einzelner Betroffener geschützt wird. Sie ermöglicht einem Dateninhaber, aggregierte Muster der Gruppe zu teilen und dabei die Informationen, die über einzelne Personen preisgegeben werden, zu begrenzen.
​
Einbettungen: Dichte Vektorrepräsentationen von Daten (Text, Bilder usw.), die semantische Bedeutung in einem hochdimensionalen Raum erfassen.
​
Erklärbarkeit – Erklärbarkeit in der KI ist die Fähigkeit eines KI-Systems, menschenverständliche Gründe für seine Entscheidungen und Vorhersagen zu liefern und Einblicke in seine internen Abläufe zu geben.
​
Erklärbare KI (XAI): KI-Systeme, die darauf ausgelegt sind, durch verschiedene Techniken und Rahmenwerke menschenverständliche Erklärungen für ihre Entscheidungen und Verhaltensweisen zu liefern.
​
Föderiertes Lernen: Ein maschinelles Lernverfahren, bei dem Modelle über mehrere dezentralisierte Geräte hinweg trainiert werden, die lokale Datensätze besitzen, ohne dass die Daten selbst ausgetauscht werden.
​
Schutzmaßnahmen: Einschränkungen, die implementiert werden, um zu verhindern, dass KI-Systeme schädliche, voreingenommene oder anderweitig unerwünschte Ergebnisse erzeugen.
​
Halluzination – Eine AI-Halluzination bezeichnet ein Phänomen, bei dem ein KI-Modell falsche oder irreführende Informationen erzeugt, die nicht auf seinen Trainingsdaten oder der tatsächlichen Realität basieren.
​
Human-in-the-Loop (HITL): Systeme, die so konzipiert sind, dass sie menschliche Aufsicht, Überprüfung oder Eingriffe an entscheidenden Entscheidungspunkten erfordern.
​
Infrastructure as Code (IaC): Verwaltung und Bereitstellung von Infrastruktur durch Code statt manueller Prozesse, wodurch Sicherheitsscans und konsistente Bereitstellungen ermöglicht werden.
​
Jailbreak: Techniken, die verwendet werden, um Sicherheitsvorkehrungen in KI-Systemen, insbesondere bei großen Sprachmodellen, zu umgehen, um verbotene Inhalte zu erzeugen.
​
Minimalprinzip: Das Sicherheitsprinzip, bei dem Benutzern und Prozessen nur die unbedingt erforderlichen Zugriffsrechte gewährt werden.
​
LIME (Local Interpretable Model-agnostic Explanations): Eine Technik zur Erklärung der Vorhersagen beliebiger maschineller Lernklassifikatoren, indem diese lokal mit einem interpretierbaren Modell angenähert werden.
​
Membership Inference Attack: Ein Angriff, der darauf abzielt festzustellen, ob ein bestimmter Datenpunkt zum Training eines Machine-Learning-Modells verwendet wurde.
​
MITRE ATLAS: Adversarische Bedrohungslandschaft für Künstliche-Intelligenz-Systeme; eine Wissensdatenbank zu adversarischen Taktiken und Techniken gegen KI-Systeme.
​
Modellkarte – Eine Modellkarte ist ein Dokument, das standardisierte Informationen über die Leistung, Einschränkungen, beabsichtigte Verwendungen und ethische Überlegungen eines KI-Modells bereitstellt, um Transparenz und verantwortungsbewusste KI-Entwicklung zu fördern.
​
Modell-Extraktion: Ein Angriff, bei dem ein Angreifer ein Zielmodell wiederholt abfragt, um ohne Genehmigung eine funktional ähnliche Kopie zu erstellen.
​
Modellinversion: Ein Angriff, der versucht, Trainingsdaten durch Analyse von Modellausgaben zu rekonstruieren.
​
Modelllebenszyklusverwaltung – Die Verwaltung des Lebenszyklus eines KI-Modells ist der Prozess der Überwachung aller Phasen der Existenz eines KI-Modells, einschließlich dessen Entwurf, Entwicklung, Einsatz, Überwachung, Wartung und schließlich Stilllegung, um sicherzustellen, dass es wirksam bleibt und den Zielen entspricht.
​
Modellvergiftung: Direkte Einführung von Schwachstellen oder Hintertüren in ein Modell während des Trainingsprozesses.
​
Modell-Diebstahl/-Kopie: Das Extrahieren einer Kopie oder Annäherung eines proprietären Modells durch wiederholte Abfragen.
​
Multi-Agenten-System: Ein System, das aus mehreren interagierenden KI-Agenten besteht, von denen jeder potenziell unterschiedliche Fähigkeiten und Ziele hat.
​
OPA (Open Policy Agent): Eine Open-Source-Policy-Engine, die eine einheitliche Durchsetzung von Richtlinien über den gesamten Stack hinweg ermöglicht.
​
Privacy-Preserving Machine Learning (PPML): Techniken und Methoden, um ML-Modelle zu trainieren und bereitzustellen, während die Privatsphäre der Trainingsdaten geschützt wird.
​
Prompt Injection: Ein Angriff, bei dem bösartige Anweisungen in Eingaben eingebettet werden, um das beabsichtigte Verhalten eines Modells zu überschreiben.
​
RAG (Retrieval-Augmented Generation): Eine Technik, die große Sprachmodelle verbessert, indem sie relevante Informationen aus externen Wissensquellen abruft, bevor sie eine Antwort generiert.
​
Red-Teaming: Die Praxis, KI-Systeme aktiv durch die Simulation feindlicher Angriffe zu testen, um Schwachstellen zu identifizieren.
​
SBOM (Software Bill of Materials): Ein formaler Nachweis, der die Details und Lieferkettenbeziehungen verschiedener Komponenten enthält, die beim Erstellen von Software oder KI-Modellen verwendet werden.
​
SHAP (SHapley Additive exPlanations): Ein spieltheoretischer Ansatz zur Erklärung der Ausgabe eines beliebigen maschinellen Lernmodells durch Berechnung des Beitrags jeder einzelnen Eigenschaft zur Vorhersage.
​
Lieferkettenangriff: Kompromittierung eines Systems durch das gezielte Anvisieren weniger sicherer Elemente in seiner Lieferkette, wie beispielsweise Drittanbieter-Bibliotheken, Datensätze oder vortrainierte Modelle.
​
Transferlernen: Eine Technik, bei der ein für eine Aufgabe entwickeltes Modell als Ausgangspunkt für ein Modell einer zweiten Aufgabe wiederverwendet wird.
​
Vektor-Datenbank: Eine spezialisierte Datenbank, die darauf ausgelegt ist, hochdimensionale Vektoren (Einbettungen) zu speichern und effiziente Ähnlichkeitssuchen durchzuführen.
​
Schwachstellen-Scanning: Automatisierte Tools, die bekannte Sicherheitslücken in Softwarekomponenten, einschließlich KI-Frameworks und Abhängigkeiten, identifizieren.
​
Wasserzeichen: Techniken zur Einbettung nicht wahrnehmbarer Marker in KI-generierte Inhalte, um deren Ursprung zu verfolgen oder die KI-Erzeugung zu erkennen.
​
Zero-Day-Schwachstelle: Eine zuvor unbekannte Schwachstelle, die Angreifer ausnutzen können, bevor Entwickler einen Patch erstellen und bereitstellen.

## Anhang B: Referenzen

### TODO

## Anhang C: KI-Sicherheitsverwaltung und Dokumentation

### Zielsetzung

Dieser Anhang enthält grundlegende Anforderungen für die Einrichtung organisatorischer Strukturen, Richtlinien und Prozesse zur Steuerung der KI-Sicherheit während des gesamten Systemlebenszyklus.

---

### AC.1 Einführung des KI-Risikomanagement-Rahmenwerks

Bereitstellung eines formalen Rahmens zur Identifizierung, Bewertung und Minderung von KI-spezifischen Risiken über den gesamten Systemlebenszyklus hinweg.

 #AC.1.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass eine KI-spezifische Risikobewertungsmethodik dokumentiert und implementiert ist.
 #AC.1.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Risikoanalysen zu wichtigen Zeitpunkten im KI-Lebenszyklus und vor wesentlichen Änderungen durchgeführt werden.
 #AC.1.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob der Risikomanagementrahmen mit etablierten Standards übereinstimmt (z. B. NIST AI RMF).

---

### AC.2 KI-Sicherheitsrichtlinie & -verfahren

Definieren und Durchsetzen organisatorischer Standards für die sichere Entwicklung, Bereitstellung und den Betrieb von KI.

 #AC.2.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob dokumentierte AI-Sicherheitsrichtlinien vorhanden sind.
 #AC.2.2    Ebene: 2    Rolle: D
 Verifizieren Sie, dass Richtlinien mindestens jährlich und nach wesentlichen Veränderungen der Bedrohungslandschaft überprüft und aktualisiert werden.
 #AC.2.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob die Richtlinien alle AISVS-Kategorien und geltenden gesetzlichen Anforderungen abdecken.

---

### AC.3 Rollen & Verantwortlichkeiten für AI-Sicherheit

Schaffen Sie klare Verantwortlichkeiten für die KI-Sicherheit in der gesamten Organisation.

 #AC.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass die Rollen und Verantwortlichkeiten im Bereich der KI-Sicherheit dokumentiert sind.
 #AC.3.2    Ebene: 2    Rolle: D
 Überprüfen Sie, ob verantwortliche Personen über geeignete Sicherheitsexpertise verfügen.
 #AC.3.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass ein Ethikausschuss für KI oder ein Governance-Gremium für hochriskante KI-Systeme eingerichtet wird.

---

### AC.4 Durchsetzung ethischer KI-Richtlinien

Sicherstellen, dass KI-Systeme gemäß festgelegten ethischen Grundsätzen arbeiten.

 #AC.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass ethische Richtlinien für die Entwicklung und den Einsatz von KI existieren.
 #AC.4.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um ethische Verstöße zu erkennen und zu melden.
 #AC.4.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass regelmäßige ethische Überprüfungen der eingesetzten KI-Systeme durchgeführt werden.

---

### AC.5 Überwachung der Einhaltung von KI-Vorschriften

Bewahren Sie die Aufmerksamkeit für und die Einhaltung der sich entwickelnden KI-Vorschriften.

 #AC.5.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Prozesse zur Identifizierung relevanter KI-Vorschriften vorhanden sind.
 #AC.5.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass die Einhaltung aller gesetzlichen Vorschriften bewertet wird.
 #AC.5.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob regulatorische Änderungen zeitnahe Überprüfungen und Aktualisierungen von KI-Systemen auslösen.

### AC.6 Governance, Dokumentation und Prozess der Trainingsdaten

 #1.1.2    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass nur Datensätze verwendet werden, die auf Qualität, Repräsentativität, ethische Beschaffung und Lizenzkonformität geprüft wurden, um Risiken wie Vergiftung, eingebettete Vorurteile und Verletzung geistigen Eigentums zu reduzieren.
 #1.1.5    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch gegenseitige Überprüfungen der Gutachter oder Konsens gewährleistet ist.
 #1.1.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass für bedeutende Trainingsdatensätze "Datenblätter" oder "Datenkarten für Datensätze" geführt werden, die Merkmale, Motivationen, Zusammensetzung, Erhebungsprozesse, Vorverarbeitung sowie empfohlene bzw. nicht empfohlene Verwendungszwecke detailliert beschreiben.
 #1.3.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die identifizierten Verzerrungen durch dokumentierte Strategien wie Neu-Balancierung, gezielte Datenaugmentation, algorithmische Anpassungen (z. B. Pre-Processing-, In-Processing-, Post-Processing-Techniken) oder Neu-Gewichtung gemindert werden und die Auswirkungen der Minderung sowohl auf die Fairness als auch auf die Gesamtleistung des Modells bewertet werden.
 #1.3.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Fairness-Metriken nach dem Training bewertet und dokumentiert werden.
 #1.3.4    Ebene: 3    Rolle: D/V
 Überprüfen Sie, ob eine Richtlinie zur Verwaltung von Lebenszyklus-Biases Eigentümer und Überprüfungsintervalle zuweist.
 #1.4.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch klare Richtlinien, Kreuzprüfungen durch Gutachter, Konsensmechanismen (z. B. Überwachung der Übereinstimmung zwischen den Annotatoren) und definierte Prozesse zur Behebung von Abweichungen gewährleistet wird.
 #1.4.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Labels, die für Sicherheit, Schutz oder Fairness von entscheidender Bedeutung sind (z. B. die Identifizierung toxischer Inhalte, kritischer medizinischer Befunde), einer obligatorischen unabhängigen Doppelprüfung oder einer gleichwertig robusten Verifizierung unterzogen werden.
 #1.4.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Beschriftungsanleitungen und Anweisungen umfassend, versioniert und peer-reviewed sind.
 #1.4.6    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Datenschemata für Labels klar definiert und versioniert sind.
 #1.3.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Datensätze auf repräsentative Ungleichgewichte und potenzielle Verzerrungen hinsichtlich gesetzlich geschützter Merkmale (z. B. Rasse, Geschlecht, Alter) sowie anderer ethisch sensibler Eigenschaften, die für das Anwendungsgebiet des Modells relevant sind (z. B. sozioökonomischer Status, Standort), profiliert wurden.
 #1.5.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass manuelle Stichprobenprüfungen durch Fachexperten eine statistisch signifikante Stichprobe abdecken (z. B. ≥1% oder 1.000 Stichproben, je nachdem, welcher Wert größer ist, oder wie durch die Risikoabschätzung festgelegt), um subtile Qualitätsprobleme zu identifizieren, die von der Automatisierung nicht erfasst werden.
 #1.8.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob ausgelagerte oder durch die Crowd durchgeführte Kennzeichnungsabläufe technische/prozedurale Schutzmaßnahmen enthalten, um die Vertraulichkeit und Integrität der Daten, die Qualität der Labels zu gewährleisten und Datenlecks zu verhindern.
 #1.5.4    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Behebungsschritte an Herkunftsdatensätze angehängt werden.
 #1.6.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass markierte Proben vor dem Training eine manuelle Überprüfung auslösen.
 #1.6.3    Ebene: 2    Rolle: V
 Überprüfen Sie, dass die Ergebnisse das Sicherheitsdossier des Modells speisen und die fortlaufende Bedrohungsaufklärung unterstützen.
 #1.6.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Erkennungslogik mit neuen Bedrohungsinformationen aktualisiert wird.
 #1.6.5    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Online-Lernpipelines die Verteilungverschiebung überwachen.
 #1.7.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, dass Arbeitsabläufe zum Löschen von Trainingsdaten sowohl Primär- als auch abgeleitete Daten vollständig entfernen und die Auswirkungen auf das Modell bewerten. Stellen Sie sicher, dass die Auswirkungen auf betroffene Modelle bewertet und gegebenenfalls behoben werden (z. B. durch erneutes Training oder Neukalibrierung).
 #1.7.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um den Umfang und den Status der Zustimmung des Nutzers (sowie von Widerrufen) für die zur Schulung verwendeten Daten zu verfolgen und zu respektieren, und dass die Zustimmung validiert wird, bevor Daten in neue Trainingsprozesse oder bedeutende Modellaktualisierungen eingearbeitet werden.
 #1.7.3    Ebene: 2    Rolle: V
 Stellen Sie sicher, dass Workflows jährlich getestet und protokolliert werden.
 #1.8.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Drittanbieterdatenlieferanten, einschließlich Anbieter vortrainierter Modelle und externer Datensätze, einer Sicherheits-, Datenschutz-, ethischen Beschaffung- und Datenqualitätsprüfung unterzogen werden, bevor ihre Daten oder Modelle integriert werden.
 #1.8.2    Ebene: 1    Rolle: D
 Überprüfen Sie, dass externe Übertragungen TLS/Authentifizierung und Integritätsprüfungen verwenden.
 #1.8.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Datenquellen mit hohem Risiko (z. B. Open-Source-Datensätze mit unbekannter Herkunft, nicht geprüfte Lieferanten) vor der Verwendung in sensiblen Anwendungen einer verstärkten Prüfung unterzogen werden, wie z. B. sandboxbasierte Analysen, umfangreiche Qualitäts-/Bias-Überprüfungen und gezielte Erkennung von Datenvergiftung.
 #1.8.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass vor dem Feintuning oder der Bereitstellung vortrainierte Modelle von Drittanbietern auf eingebettete Verzerrungen, potenzielle Hintertüren, die Integrität ihrer Architektur und die Herkunft ihrer ursprünglichen Trainingsdaten überprüft werden.
 #1.5.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob bei Verwendung von adversarialem Training die Erstellung, Verwaltung und Versionierung von adversarialen Datensätzen dokumentiert und kontrolliert wird.
 #1.5.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass die Auswirkung des Trainings zur adversarialen Robustheit auf die Modellleistung (gegenüber sowohl sauberen als auch adversarialen Eingaben) und auf Fairness-Metriken bewertet, dokumentiert und überwacht wird.
 #1.5.4    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Strategien für adversariales Training und Robustheit regelmäßig überprüft und aktualisiert werden, um sich entwickelnden Techniken von adversarialen Angriffen entgegenzuwirken.
 #1.4.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass fehlgeschlagene Datensätze mit Prüfpfaden isoliert werden.
 #1.4.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Qualitätsgrenzen unterdurchschnittliche Datensätze blockieren, es sei denn, Ausnahmen sind genehmigt.
 #1.11.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass der Generierungsprozess, die Parameter und die beabsichtigte Verwendung der synthetischen Daten dokumentiert sind.
 #1.11.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass synthetische Daten vor der Verwendung im Training auf Bias, Datenschutzverletzungen und Repräsentationsprobleme risikobewertet werden.
 #1.12.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Warnmeldungen für verdächtige Zugriffsereignisse generiert und umgehend untersucht werden.
 #1.13.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob für alle Trainingsdatensätze explizite Aufbewahrungsfristen festgelegt sind.
 #1.13.2    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Datensätze am Ende ihres Lebenszyklus automatisch ablaufen, gelöscht oder zur Löschung überprüft werden.
 #1.13.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, dass Aufbewahrungs- und Löschaktionen protokolliert und prüfbar sind.
 #1.14.1    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Anforderungen an den Datenstandort und den grenzüberschreitenden Datentransfer für alle Datensätze identifiziert und durchgesetzt werden.
 #1.14.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass sektorspezifische Vorschriften (z. B. Gesundheitswesen, Finanzen) bei der Datenverarbeitung identifiziert und berücksichtigt werden.
 #1.14.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung relevanter Datenschutzgesetze (z. B. DSGVO, CCPA) dokumentiert und regelmäßig überprüft wird.
 #1.16.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um auf Anfragen von Betroffenen bezüglich Zugriff, Berichtigung, Einschränkung oder Widerspruch zu reagieren.
 #1.16.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass Anfragen innerhalb gesetzlich vorgeschriebener Fristen protokolliert, nachverfolgt und erfüllt werden.
 #1.16.3    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Prozesse zur Wahrung der Rechte der betroffenen Personen regelmäßig auf ihre Wirksamkeit getestet und überprüft werden.
 #1.17.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Aktualisierung oder dem Austausch einer Datensatzversion eine Auswirkungenanalyse durchgeführt wird, die Modellleistung, Fairness und Compliance abdeckt.
 #1.17.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Auswirkungsanalyse dokumentiert und von den relevanten Interessengruppen überprüft werden.
 #1.17.3    Ebene: 2    Rolle: D/V
 Verifizieren Sie, dass Rücksetzpläne vorhanden sind, falls neue Versionen unakzeptable Risiken oder Rückschritte einführen.
 #1.18.1    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass alle am Datenannotieren beteiligten Personen einer Hintergrundüberprüfung unterzogen wurden und in Datensicherheit und Datenschutz geschult sind.
 #1.18.2    Ebene: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Mitarbeiter der Annotation Vertraulichkeits- und Geheimhaltungsvereinbarungen unterschreiben.
 #1.18.3    Ebene: 2    Rolle: D/V
 Überprüfen Sie, ob Annotationsplattformen Zugangskontrollen durchsetzen und Insider-Bedrohungen überwachen.

#### Literaturverzeichnis

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anhang D: KI-gestützte Governance und Verifikation sicherer Programmierung

### Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollmaßnahmen für den sicheren und effektiven Einsatz von KI-unterstützten Codierwerkzeugen während der Softwareentwicklung und stellt dabei Sicherheit und Nachvollziehbarkeit über den gesamten Softwareentwicklungszyklus (SDLC) sicher.

---

### AD.1 KI-gestützter Secure-Coding-Workflow

Integrieren Sie KI-Tools in den sicheren Software-Entwicklungszyklus (SSDLC) der Organisation, ohne bestehende Sicherheitskontrollen zu schwächen.

 #AD.1.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob ein dokumentierter Workflow beschreibt, wann und wie KI-Tools Code generieren, refaktorisieren oder überprüfen dürfen.
 #AD.1.2    Ebene: 2    Rolle: D
 Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).
 #AD.1.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Metriken (z. B. Verwundbarkeitsdichte, mittlere Erkennungszeit) für KI-erzeugten Code erfasst und mit den Basiswerten ausschließlich menschlichen Codes verglichen werden.

---

### AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierungswerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

 #AD.2.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Werkzeug Missbrauch, Modellinversion, Datenleck und Risiken der Abhängigkeitskette identifiziert.
 #AD.2.2    Ebene: 2    Rolle: D
 Überprüfen Sie, dass die Tool-Bewertungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen.
 #AD.2.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.

---

### AD.3 Sichere Eingabeaufforderungs- und Kontextverwaltung

Verhindern Sie das Austreten von Geheimnissen, firmeneigenem Code und persönlichen Daten beim Erstellen von Prompts oder Kontexten für KI-Modelle.

 #AD.3.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass schriftliche Anweisungen das Senden von Geheimnissen, Anmeldeinformationen oder klassifizierten Daten in Eingabeaufforderungen verboten.
 #AD.3.2    Ebene: 2    Rolle: D
 Überprüfen Sie, dass technische Kontrollen (clientseitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.
 #AD.3.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen mit der Datenklassifizierungsrichtlinie übereinstimmen.

---

### AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

 #AD.4.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-generierter Code immer einer menschlichen Codeüberprüfung unterzogen wird.
 #AD.4.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Befunden blockieren.
 #AD.4.3    Ebene: 3    Rolle: D/V
 Verifizieren Sie, dass Differenzial-Fuzz-Tests oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.

---

### AD.5 Erklärbarkeit und Rückverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblick, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

 #AD.5.1    Ebene: 1    Rolle: D/V
 Überprüfen Sie, ob Prompt/Antwort-Paare mit Commit-IDs protokolliert werden.
 #AD.5.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Vorschlag unterstützen.
 #AD.5.3    Ebene: 3    Rolle: D/V
 Überprüfen Sie, dass Erklärbarkeitsberichte zusammen mit Designartefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien von ISO/IEC 42001 zu erfüllen.

---

### AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheit der Modellleistung im Laufe der Zeit und verhindern Sie gleichzeitig negative Abweichungen.

 #AD.6.1    Ebene: 1    Rolle: D/V
 Stellen Sie sicher, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen nachverfolgt werden.
 #AD.6.2    Ebene: 2    Rolle: D
 Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder retrieval-gestützte Generierung mit geprüften sicheren Codierkorpora (z. B. OWASP Cheat Sheets) informiert.
 #AD.6.3    Ebene: 3    Rolle: D/V
 Stellen Sie sicher, dass ein Closed-Loop-Bewertungsharness nach jeder Feinabstimmung Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung mindestens die vorherigen Baselines erreichen oder übertreffen.

---

#### Literaturverzeichnis

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Anhang E: Beispielwerkzeuge und Frameworks

### Zielsetzung

Dieses Kapitel bietet Beispiele für Werkzeuge und Frameworks, die die Umsetzung oder Erfüllung einer bestimmten AISVS-Anforderung unterstützen können. Diese sind nicht als Empfehlungen oder Befürwortungen durch das AISVS-Team oder das OWASP GenAI Security Projekt zu verstehen.

---

### AE.1 Training Data Governance & Bias-Management

Werkzeuge für Datenanalyse, Governance und Bias-Management.

 #AE.1.1    Abschnitt: 1.1
 Dateninventarisierungs-Tools: Tools zur Verwaltung von Dateninventaren wie...
 #AE.1.2    Abschnitt: 1.2
 Verschlüsselung während der Übertragung Verwenden Sie TLS für HTTPS-basierte Anwendungen, mit Werkzeugen wie openSSL und Pythons`ssl` Bibliothek.

---

### AE.2 Benutzereingabevalidierung

Werkzeuge zur Verarbeitung und Validierung von Benutzereingaben.

 #AE.2.1    Abschnitt: 2.1
 Prompt Injection Verteidigungstools: Verwenden Sie Schutzmechanismen wie NVIDIAs NeMo oder Guardrails AI.

---

