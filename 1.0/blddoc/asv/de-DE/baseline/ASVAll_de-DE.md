## Frontispiz

### Über den Standard

Der Artificial Intelligence Security Verification Standard (AISVS) ist ein gemeinschaftlich erstellter Katalog von Sicherheitsanforderungen, den Data Scientists, MLOps-Ingenieure, Softwarearchitekten, Entwickler, Tester, Sicherheitsexperten, Tool-Anbieter, Regulierungsbehörden und Anwender nutzen können, um vertrauenswürdige KI-basierte Systeme und Anwendungen zu entwerfen, zu entwickeln, zu testen und zu verifizieren. Er bietet eine gemeinsame Sprache zur Spezifizierung von Sicherheitskontrollen über den gesamten KI-Lebenszyklus hinweg – von der Datenerfassung und Modellentwicklung bis hin zu Einsatz und fortlaufender Überwachung – damit Organisationen die Belastbarkeit, den Datenschutz und die Sicherheit ihrer KI-Lösungen messen und verbessern können.

### Urheberrecht und Lizenz

Version 0.1 (Erster öffentlicher Entwurf - Arbeit im Gange), 2025  

![license](images/license.png)
Copyright © 2025 Das AISVS-Projekt.  

Veröffentlicht unter derCreative Commons Attribution‑ShareAlike 4.0 International License.
Für jede Wiederverwendung oder Verbreitung müssen Sie die Lizenzbedingungen dieses Werks anderen klar kommunizieren.

### Projektleiter

Jim Manico
Aras „Russ“ Memisyazici

### Mitwirkende und Gutachter

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS ist ein brandneuer Standard, der speziell entwickelt wurde, um die einzigartigen Sicherheitsherausforderungen von Systemen der künstlichen Intelligenz zu adressieren. Obwohl er sich an allgemeineren Sicherheits-Best Practices orientiert, wurde jeder einzelne Anforderungspunkt in AISVS von Grund auf neu entwickelt, um die Bedrohungslandschaft im Bereich der KI widerzuspiegeln und Organisationen dabei zu helfen, sicherere und widerstandsfähigere KI-Lösungen zu entwickeln.

## Vorwort

Willkommen beim Artificial Intelligence Security Verification Standard (AISVS) Version 1.0!

### Einführung

AISVS wurde im Jahr 2025 durch eine gemeinsame Gemeinschaftsinitiative gegründet und definiert die Sicherheitsanforderungen, die bei der Gestaltung, Entwicklung, Bereitstellung und dem Betrieb moderner KI-Modelle, Pipelines und KI-gestützter Dienste zu berücksichtigen sind.

AISVS v1.0 stellt die gemeinsame Arbeit seiner Projektleiter, der Arbeitsgruppe und der breiteren Gemeinschaft von Beitragenden dar, um eine pragmatische, überprüfbare Grundlage für die Sicherung von KI-Systemen zu schaffen.

Unser Ziel mit dieser Veröffentlichung ist es, AISVS einfach anwendbar zu machen, dabei aber den definierten Umfang strikt einzuhalten und die sich schnell entwickelnde, einzigartige Risikolandschaft im Bereich der KI zu adressieren.

### Schlüsselziele für AISVS Version 1.0

Version 1.0 wird mit mehreren Leitprinzipien erstellt.

#### Gut definierter Umfang

Jede Anforderung muss mit dem Namen und der Mission von AISVS übereinstimmen:

Künstliche Intelligenz – Kontrollen erfolgen auf der AI/ML-Ebene (Daten, Modell, Pipeline oder Inferenz) und liegen in der Verantwortung der AI-Fachleute.
Sicherheit – Anforderungen mindern direkt identifizierte Sicherheits-, Datenschutz- oder Sicherheitsrisiken.
Verifizierung – Die Sprache ist so verfasst, dass die Übereinstimmung objektiv validiert werden kann.
Standard – Abschnitte folgen einer einheitlichen Struktur und Terminologie, um eine kohärente Referenz zu bilden.
​
---

Indem sie AISVS befolgen, können Organisationen systematisch die Sicherheitslage ihrer KI-Lösungen bewerten und stärken, wodurch eine Kultur der sicheren KI-Entwicklung gefördert wird.

## Verwendung des AISVS

Der Artificial Intelligence Security Verification Standard (AISVS) definiert Sicherheitsanforderungen für moderne KI-Anwendungen und -Dienste, wobei der Fokus auf Aspekten liegt, die innerhalb der Kontrolle der Anwendungsentwickler stehen.

Das AISVS richtet sich an alle, die Sicherheitsaspekte von KI-Anwendungen entwickeln oder bewerten, einschließlich Entwickler, Architekten, Sicherheitsingenieure und Prüfer. Dieses Kapitel stellt die Struktur und Nutzung des AISVS vor, einschließlich seiner Verifikationsstufen und vorgesehenen Anwendungsfälle.

### Sicherheitsüberprüfungsstufen für Künstliche Intelligenz

Das AISVS definiert drei aufsteigende Stufen der Sicherheitsüberprüfung. Jede Stufe fügt Tiefe und Komplexität hinzu, sodass Organisationen ihre Sicherheitsstrategie an das Risikoniveau ihrer KI-Systeme anpassen können.

Organisationen können auf Level 1 beginnen und mit zunehmender Sicherheitsexpertise und Bedrohungsexposition schrittweise höhere Level übernehmen.

#### Definition der Ebenen

Jede Anforderung in AISVS v1.0 wird einer der folgenden Stufen zugeordnet:

 Anforderungen der Stufe 1

Level 1 umfasst die kritischsten und grundlegendsten Sicherheitsanforderungen. Diese konzentrieren sich darauf, häufige Angriffe zu verhindern, die nicht von anderen Voraussetzungen oder Schwachstellen abhängen. Die meisten Kontrollen auf Level 1 sind entweder einfach umzusetzen oder so wichtig, dass der Aufwand gerechtfertigt ist.

 Anforderungen der Stufe 2

Level 2 behandelt fortgeschrittenere oder weniger häufige Angriffe sowie mehrschichtige Verteidigungen gegen weit verbreitete Bedrohungen. Diese Anforderungen können komplexere Logik beinhalten oder auf spezifische Voraussetzungen von Angriffen abzielen.

 Anforderungen der Stufe 3

Level 3 umfasst Kontrollen, die in der Regel schwerer umzusetzen sind oder situationsabhängig angewendet werden. Diese stellen häufig mehrschichtige Verteidigungsmechanismen oder Gegenmaßnahmen gegen spezialisierte, gezielte oder komplexe Angriffe dar.

#### Rolle (D/V)

Jede AISVS-Anforderung ist entsprechend dem Hauptzielpublikum gekennzeichnet:

D – Entwicklerorientierte Anforderungen
V – Anforderungen für Prüfer/Auditoren
D/V – Relevant sowohl für Entwickler als auch für Prüfer

## C1 Training Datenverwaltung & Bias-Management

### Kontrollziel

Trainingsdaten müssen so bezogen, gehandhabt und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness gewährleistet sind. Dadurch werden rechtliche Verpflichtungen erfüllt und Risiken wie Verzerrungen, Datenmanipulation oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten Lebenszyklus der KI beeinflussen könnten, reduziert.

---

### C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Auditierbarkeit.

 #1.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass eine aktuelle Inventarliste aller Trainingsdatenquellen (Ursprung, Verwalter/Eigentümer, Lizenz, Erhebungsmethode, beabsichtigte Nutzungseinschränkungen und Verarbeitungshistorie) geführt wird.
 #1.1.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass die Verarbeitungsprozesse der Trainingsdaten unnötige Merkmale, Attribute oder Felder ausschließen (z. B. ungenutzte Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).
 #1.1.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Änderungen am Datensatz einem protokollierten Genehmigungsworkflow unterliegen.
 #1.1.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Datensätze oder Teilmengen dort, wo möglich, mit Wasserzeichen oder Fingerprints versehen sind.

---

### C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung, und validieren Sie ihre Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

 #1.2.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Zugriffskontrollen den Speicher und die Pipelines der Trainingsdaten schützen.
 #1.2.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass jeder Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeitpunkt und Aktion.
 #1.2.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Trainingsdatensätze während der Übertragung und im Ruhezustand mit branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungspraktiken verschlüsselt sind.
 #1.2.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten sicherzustellen.
 #1.2.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisierte Erkennungstechniken angewendet werden, um unbefugte Änderungen oder Korruption der Trainingsdaten zu verhindern.
 #1.2.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.
 #1.2.7    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Versionen des Trainingsdatensatzes eindeutig identifiziert, unveränderlich gespeichert und überprüfbar sind, um eine Rücksetzung und forensische Analyse zu unterstützen.

---

### C1.3 Qualität, Integrität und Sicherheit der Kennzeichnung von Trainingsdaten

Schützen Sie Etiketten und verlangen Sie eine technische Überprüfung für kritische Daten.

 #1.3.1    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass kryptografische Hashes oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität sicherzustellen.
 #1.3.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Kennzeichnungsoberflächen und -plattformen strenge Zugriffskontrollen durchsetzen, manipulationssichere Prüfprotokolle aller Kennzeichnungsaktivitäten führen und vor unautorisierten Änderungen schützen.
 #1.3.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass sensible Informationen in Beschriftungen auf Feldebene sowohl im Ruhezustand als auch während der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.

---

### C1.4 Qualität der Trainingsdaten und Sicherheitsgarantie

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Korrekturmaßnahmen, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

 #1.4.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests Formatfehler und Nullwerte bei jeder Datenaufnahme oder wesentlichen Datenumwandlung erfassen.
 #1.4.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Datenvergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Einbettungsanalysen), um potenzielle Datenvergiftungsangriffe (z. B. Label-Flipping, Einfügen von Backdoor-Triggern, Befehlswechsel, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption im Trainingsdatensatz zu identifizieren.
 #1.4.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass geeignete Schutzmaßnahmen, wie adversariales Training (unter Verwendung generierter adversarialer Beispiele), Datenaugmentation mit veränderten Eingaben oder robuste Optimierungstechniken, implementiert und basierend auf der Risikobewertung für die relevanten Modelle abgestimmt sind.
 #1.4.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisch generierte Labels (z. B. durch LLMs oder schwache Überwachung) Schwellenwerte für die Zuversicht und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Zuversicht zu erkennen.
 #1.4.5    Niveau: 3    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests bei jedem Import oder bedeutenden Datentransformationen Label-Verschiebungen erkennen.

---

### C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie die vollständige Reise jedes Datenpunkts von der Quelle bis zum Modelleingang zur Nachvollziehbarkeit und für die Vorfallreaktion.

 #1.5.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Herkunft jedes Datenpunkts, einschließlich aller Transformationen, Erweiterungen und Zusammenführungen, dokumentiert ist und rekonstruiert werden kann.
 #1.5.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsaufzeichnungen unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.
 #1.5.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Nachverfolgung der Herkunft synthetische Daten, die mittels datenschutzfreundlicher oder generativer Techniken erzeugt wurden, abdeckt und dass alle synthetischen Daten im gesamten Prozess klar gekennzeichnet und von realen Daten unterscheidbar sind.

---

### Referenzen

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

## C2 Benutzereingabevalidierung

### Kontrollziel

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten preisgeben oder das Modell zu unerlaubtem Verhalten lenken. Wenn keine speziellen Filter und Anweisungshierarchien vorhanden sind, zeigen Untersuchungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, effektiv sein werden. Ebenso können subtile adversarial perturbation attacks – wie Homoglyphentausch oder Leetspeak – die Entscheidungen eines Modells unbemerkt verändern.

---

### C2.1 Abwehr von Prompt-Injektionen

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Verteidigungsmechanismen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung von Befehlen in hierarchischer Reihenfolge.

 #2.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Benutzereingaben anhand einer kontinuierlich aktualisierten Bibliothek bekannter Prompt-Injektion-Muster (Jailbreak-Schlüsselwörter, „ignore previous“, Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.
 #2.1.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überschreiben, selbst nach Erweiterung des Kontextfensters.
 #2.1.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass adversariale Evaluierungstests (z. B. Red Team "many-shot" Prompts) vor jeder Veröffentlichung eines Modells oder Prompt-Templates durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatischen Blockaden bei Regressionen.
 #2.1.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in die Hauptaufforderung eingefügt werden.
 #2.1.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifizierungsmodelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.

---

### C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (Natural Language Processing, NLP) sind weiterhin anfällig für subtile Zeichen- oder Wort-Ebene-Störungen, die Menschen häufig übersehen, die Modelle jedoch oft falsch klassifizieren.

 #2.2.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass grundlegende Eingabe-Normalisierungsschritte (Unicode NFC, Homoglyph-Mapping, Entfernen von Leerzeichen) vor der Tokenisierung durchgeführt werden.
 #2.2.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßiger Wiederholung von Tokens oder abnormalen Einbettungsdistanzen kennzeichnet.
 #2.2.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob die Inferenz-Pipeline optionale adversarial-trainingsgehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für Hochrisiko-Endpunkte unterstützt.
 #2.2.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass vermutete adversariale Eingaben isoliert, mit vollständigen Nutzdaten (nach PII-Redaktion) protokolliert werden.
 #2.2.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuiten) im Zeitverlauf verfolgt werden und Regressionen einen Release-Blocker auslösen.

---

### C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überschreitungen von Aufforderungen über Felder hinweg und Ressourcenerschöpfung verursachen. Eine strikte Durchsetzung des Schemas ist zudem Voraussetzung für die Ausführung deterministischer Werkzeugaufrufe.

 #2.3.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder ein multimodales Äquivalent) definiert und dass die Eingaben vor der Zusammenstellung des Prompts validiert werden.
 #2.3.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einer sicheren Fehlermeldung abgelehnt werden und niemals stillschweigend abgeschnitten werden.
 #2.3.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Typprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.
 #2.3.4    Niveau: 2    Rolle: D
 Überprüfen Sie, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.
 #2.3.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass Validierungsfehler mit geschwärzten Nutzdaten-Ausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitstriage zu unterstützen.

---

### C2.4 Inhalts- und Richtlinienüberprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die unerlaubte Inhalte anfordern (wie illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und dann verhindern, dass diese weiterverbreitet werden.

 #2.4.1    Niveau: 1    Rolle: D
 Überprüfen Sie, ob ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstschädigung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten.
 #2.4.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.
 #2.4.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster berücksichtigt.
 #2.4.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass die Prüfung benutzerspezifische Richtlinien (Alter, regionale gesetzliche Einschränkungen) durch attributbasierte Regeln respektiert, die zur Anforderungszeit aufgelöst werden.
 #2.4.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorietags für SOC-Korrelation und zukünftige Red-Team-Wiedergaben enthalten.

---

### C2.5 Eingangsratengrenzung & Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

 #2.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob für alle Eingabeendpunkte benutzerbezogene, IP-bezogene und API-Schlüssel-bezogene Ratenbegrenzungen durchgesetzt werden.
 #2.5.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Burst- und Dauer-Drosselungsraten so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.
 #2.5.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflut) automatisierte Sperren oder Eskalationen auslösen.
 #2.5.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.

---

### C2.6 Multimodale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

 #2.6.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden.
 #2.6.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganografische Nutzlasten gescannt werden.
 #2.6.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Bild-/Audioeingaben auf adversarielle Störungen oder bekannte Angriffsmuster überprüft werden.
 #2.6.4    Niveau: 3    Rolle: V
 Verifizieren Sie, dass Fehler bei der Validierung multimodaler Eingaben protokolliert werden und Alarme zur Untersuchung auslösen.

---

### C2.7 Eingabeherkunft & Attribution

KI-Systeme sollten die Prüfung, Verfolgung von Missbrauch und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

 #2.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.
 #2.7.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und überprüfbar sind.
 #2.7.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen erkannt und einer verstärkten Prüfung oder Blockierung unterzogen werden.

---

### C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsvektoren anpassen und Echtzeitschutz durch kompiliertes Musterabgleichen bieten.

 #2.8.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Bedrohungserkennungsmuster in optimierte reguläre Ausdrucks-Engines kompiliert werden, um eine hochleistungsfähige Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.
 #2.8.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Bedrohungserkennungssysteme separate Musterdatenbanken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) führen.
 #2.8.3    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass die adaptive Bedrohungserkennung maschinelle Lernmodelle integriert, die die Bedrohungssensitivität basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.
 #2.8.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Bedrohungsdatenfeeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.
 #2.8.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Fehlalarmrate bei der Bedrohungserkennung kontinuierlich überwacht wird und die Musterspezifität automatisch angepasst wird, um Beeinträchtigungen legitimer Anwendungsfälle zu minimieren.
 #2.8.6    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die kontextbezogene Bedrohungsanalyse die Eingabequelle, das Verhaltensmuster des Benutzers und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.
 #2.8.7    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcennutzung) in Echtzeit überwacht und optimiert werden.

---

### C2.9 Multi-Modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsüberprüfungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcentrennung bereitstellen.

 #2.9.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogrammangriffe) und Erkennungsschwellen verfügt.
 #2.9.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die für jeden Modalitätstyp spezifisch sind und in den Sicherheitsrichtlinien dokumentiert werden.
 #2.9.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von cross-modal Angriffen koordinierte Angriffe identifiziert, die sich über mehrere Eingabetypen erstrecken (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektionen im Text) mithilfe von Korrelationsregeln und Alarmgenerierung.
 #2.9.4    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass mehrdimensionale Validierungsfehler detaillierte Protokollierungen auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungswerte und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfassen.
 #2.9.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass modalitätsspezifische Inhaltsklassifikatoren gemäß dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks, die über den Basisschwellenwerten liegen, aktualisiert werden.

---

### Referenzen

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

### Kontrollziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerbetriebnahme – was eine schnelle Reaktion auf Vorfälle ermöglicht und die Verantwortlichkeit für alle Änderungen sicherstellt.

Wichtigstes Sicherheitsziel: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

### C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität erreichen Produktionsumgebungen.

 #3.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptographisch von autorisierten Stellen signiert sind.
 #3.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.
 #3.1.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Herkunftsaufzeichnungen des Modells die Identität der autorisierenden Instanz, Prüfsummen der Trainingsdaten, Ergebnisse der Validierungstests mit Bestehen/Nichtbestehen-Status sowie einen Erstellungszeitstempel enthalten.
 #3.1.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte semantische Versionierung (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.
 #3.1.5    Niveau: 2    Rolle: V
 Überprüfen Sie, dass die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller konsumierenden Systeme ermöglicht.

---

### C3.2 Modellvalidierung & Testen

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

 #3.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabereinigung und Sicherheitsevaluierungen mit vorab vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzwerten vor der Bereitstellung umfassen.
 #3.2.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Validierungsfehler nach ausdrücklicher Genehmigung durch vorab bestimmte autorisierte Personen mit dokumentierten geschäftlichen Begründungen automatisch die Bereitstellung des Modells blockieren.
 #3.2.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass die Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash verknüpft sind, der validiert wird.
 #3.2.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung einer vorab festgelegten Sicherheitsinstanz innerhalb vorab vereinbarter Zeitrahmen erfordern.

---

### C3.3 Kontrollierte Bereitstellung & Rücksetzung

Modellbereitstellungen müssen kontrolliert, überwacht und reversibel sein.

 #3.3.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatisierten Rollback-Auslösern implementieren, die auf vorab vereinbarten Fehlerquoten, Latenzschwellen oder Sicherheitsalarmkriterien basieren.
 #3.3.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass die Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vorgegebener organisatorischer Zeitfenster wiederherstellen.
 #3.3.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und dass die Bereitstellung bei jeglicher Abweichung fehlschlägt.
 #3.3.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Notfall-Abschaltfunktionen des Modells Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltvorrichtungen deaktivieren können.
 #3.3.5    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.

---

### C3.4 Änderung der Verantwortlichkeit & Prüfung

Alle Änderungen im Modelllebenszyklus müssen nachvollziehbar und prüfbar sein.

 #3.4.1    Niveau: 1    Rolle: V
 Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Prüfaufzeichnungen erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.
 #3.4.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob der Zugriff auf das Audit-Protokoll eine angemessene Autorisierung erfordert und ob alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.
 #3.4.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten in Git-Repositories versioniert sind und vor der Bereitstellung eine obligatorische Code-Überprüfung sowie die Genehmigung durch festgelegte Prüfer erfolgen.
 #3.4.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob die Audit-Protokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen.

---

### C3.5 Sichere Entwicklungspraktiken

Modelentwicklungs- und Trainingsprozesse müssen sicheren Verfahren folgen, um eine Kompromittierung zu verhindern.

 #3.5.1    Niveau: 1    Rolle: D
 Verifizieren Sie, dass die Entwicklungs-, Test- und Produktionsumgebungen für Modelle physisch oder logisch getrennt sind. Sie dürfen keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher besitzen.
 #3.5.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Modelltraining und Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang stattfinden.
 #3.5.3    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachverfolgbarkeit authentifiziert werden.
 #3.5.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Entwicklungsartefakte des Modells (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionsverwaltung gespeichert sind und vor der Verwendung im Training eine Genehmigung durch Kollegenprüfung erforderlich ist.

---

### C3.6 Modellrücknahme und Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

 #3.6.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Modell-Ruhestandsprozesse automatisch Abhängigkeitsgraphen scannen, alle verbrauchenden Systeme identifizieren und vor der Stilllegung vorab vereinbarte Vorankündigungsfristen einhalten.
 #3.6.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass ausgemusterte Modellartefakte gemäß dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptografische Löschung oder mehrfaches Überschreiben gelöscht werden, und verwenden Sie verifizierte Vernichtungszertifikate.
 #3.6.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Modellstilllegungsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden und Modellsignaturen widerrufen werden, um eine Wiederverwendung zu verhindern.
 #3.6.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Notfallabschaltung von Modellen den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiten durch automatisierte Abschaltvorrichtungen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.

---

### Referenzen

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

## C4-Infrastruktur, Konfigurations- und Bereitstellungssicherheit

### Kontrollziel

Die KI-Infrastruktur muss gegen Privilegienerweiterung, Manipulation der Lieferkette und laterale Bewegung durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturbestandteile und Konfigurationen gelangen über kontrollierte Prozesse in die Produktion, die Sicherheit, Integrität und Prüfbarkeit gewährleisten.

Kern-Sicherheitsziel: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfpfade aufrechterhalten, in die Produktion.

---

### C4.1 Laufzeitumgebungsisolation

Verhindern Sie Container-Ausbrüche und Privilegieneskalationen durch kernelbasierte Isolationsprimitiven und obligatorische Zugriffskontrollen.

 #4.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und den ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten entfernen.
 #4.1.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vorab genehmigten Allow-Lists, wobei Verstöße den Container beenden und Sicherheitswarnungen erzeugen.
 #4.1.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei die noexec-Mount-Optionen durchgesetzt werden.
 #4.1.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass die auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder gleichwertig) Versuche zur Privilegienerweiterung erkennt und die verursachenden Prozesse automatisch innerhalb der organisatorischen Reaktionszeitanforderungen beendet.
 #4.1.5    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass KI-Arbeitslasten mit hohem Risiko in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsprüfung ausgeführt werden.

---

### C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

 #4.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und dass Merges bei FINDUNGEN mit CRITICAL oder HIGH Schweregrad blockiert werden.
 #4.2.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Container-Builds reproduzierbar sind mit identischen SHA256-Hashes über Builds hinweg, und erstellen Sie SLSA Level 3 Herkunftsbescheinigungen, die mit Sigstore signiert sind.
 #4.2.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und vor dem Push ins Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.
 #4.2.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Lebensdauer die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreitet.
 #4.2.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Herkunft während des Bereitstellungsprozesses vor der Containerausführung überprüft werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt.
 #4.2.6    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Build-Umgebungen in temporären Containern oder VMs ohne persistenten Speicher ausgeführt werden und eine Netzwerkisolierung von produktiven VPCs besteht.

---

### C4.3 Netzwerksicherheit & Zugangskontrolle

Implementieren Sie eine Zero-Trust-Netzwerkarchitektur mit Standard-Deny-Richtlinien und verschlüsselter Kommunikation.

 #4.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Kubernetes NetworkPolicies oder eine äquivalente Lösung standardmäßig den Ingress/Egress blockiert und explizite Zulassungsregeln für erforderliche Ports (443, 8080 usw.) implementiert.
 #4.3.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.
 #4.3.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Zulassungslisten gefiltert wird und blockierte Anfragen protokolliert werden.
 #4.3.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation zwischen den Diensten Mutual TLS verwendet, die Zertifikate gemäß der organisatorischen Richtlinie regelmäßig ausgetauscht werden und die Zertifikatsvalidierung durchgesetzt wird (keine skip-verify-Flags).
 #4.3.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und nur über NAT-Gateways oder Bastion Hosts kommuniziert.

---

### C4.4 Geheimnis- und kryptografisches Schlüsselmanagement

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

 #4.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert werden.
 #4.4.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) erzeugt werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.
 #4.4.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Rotation von Geheimnissen automatisiert ist mit einer Zero-Downtime-Bereitstellung und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.
 #4.4.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.
 #4.4.5    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Prüfprotokolle mit Benutzeridentitäten und Zeitstempeln aufgezeichnet wird.
 #4.4.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, eingehängte Volumes oder Init-Container injiziert werden, und gewährleisten Sie, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind.

---

### C4.5 AI Workload-Sandboxing und Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

 #4.5.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.
 #4.5.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert werden.
 #4.5.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalysen zur Backdoor-Erkennung umfasst.
 #4.5.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Ergebnisse der Sandbox kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden.
 #4.5.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus goldenen Images mit vollständiger Bereinigung von Dateisystem und Arbeitsspeicher neu erstellt werden.

---

### C4.6 Überwachung der Infrastruktur-Sicherheit

Infrastruktur kontinuierlich mit automatisierter Behebung und Echtzeit-Benachrichtigung scannen und überwachen.

 #4.6.1    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITISCHE Schwachstellen basierend auf den organisatorischen Risikoschwellen den Einsatz blockieren.
 #4.6.2    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Steuerungen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen für nicht bestandene Prüfungen vorhanden sind.
 #4.6.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Schwachstellen mit hoher Schwere entsprechend den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.
 #4.6.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung von CEF- oder STIX/TAXII-Formaten mit automatischer Anreicherung integriert werden.
 #4.6.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass Infrastrukturmetriken mit SLA-Dashboards und Managementberichten an Überwachungssysteme (Prometheus, DataDog) exportiert werden.
 #4.6.6    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) gemäß den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischer Rücksetzung bei nicht autorisierten Änderungen.

---

### C4.7 KI-Infrastruktur Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und stellen Sie durch Quoten und Überwachung eine faire Ressourcenzuteilung sicher.

 #4.7.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die GPU/TPU-Auslastung überwacht wird, wobei bei organisationsweit definierten Schwellenwerten Alarme ausgelöst werden und basierend auf Kapazitätsmanagementrichtlinien automatische Skalierung oder Lastenausgleich aktiviert wird.
 #4.7.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Kennzahlen der KI-Arbeitslasten (Inferenze-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Auslastung der Infrastruktur korreliert werden.
 #4.7.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Kubernetes ResourceQuotas oder gleichwertige Mechanismen einzelne Workloads gemäß den organisatorischen Richtlinien zur Ressourcenverteilung mit durchgesetzten Hard-Limits begrenzen.
 #4.7.4    Niveau: 2    Rolle: V
 Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mieter verfolgt, mit Warnmeldungen basierend auf den organisatorischen Budgetgrenzen und automatisierten Kontrollen zur Vermeidung von Budgetüberschreitungen.
 #4.7.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfragemustern erfolgt.
 #4.7.6    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Ressourcenerschöpfung gemäß den organisatorischen Reaktionsanforderungen zu Auslösern von Circuit Breakern führt, einschließlich der Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.

---

### C4.8 Trennung der Umgebungen und Steuerung der Promotion

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Freigabeschranken und Sicherheitsvalidierung.

 #4.8.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass die Entwicklungs-, Test- und Produktionsumgebungen in getrennten VPCs/VNets ausgeführt werden, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.
 #4.8.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Freigabe einer Umgebung die Genehmigung durch organisatorisch definierte autorisierte Personen mit kryptografischen Signaturen und unveränderbaren Prüfpfaden erfordert.
 #4.8.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Produktionsumgebungen den SSH-Zugang blockieren, Debug-Endpunkte deaktivieren und Änderungsanfragen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen vorschreiben.
 #4.8.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code vor dem Zusammenführen in den Hauptzweig eine Peer-Review mit automatisierten Tests und Sicherheitsprüfungen erfordern.
 #4.8.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert, synthetische Datengenerierung durchgeführt oder eine vollständige Datenmaskierung mit Entfernung von personenbezogenen Daten (PII) verifiziert wurde.
 #4.8.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Beförderungspunkte automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, bei denen keine KRISELNDE Befunde zur Genehmigung erforderlich sind.

---

### C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Widerstandsfähigkeit der Infrastruktur durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfähigkeiten.

 #4.9.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen mit der Implementierung der 3-2-1-Sicherungsstrategie in geografisch getrennte Regionen gesichert werden.
 #4.9.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Backup-Systeme in isolierten Netzwerken mit separaten Anmeldeinformationen und air-gapped Speicherlösungen für den Schutz vor Ransomware betrieben werden.
 #4.9.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit RTO- und RPO-Zielen, die den organisatorischen Anforderungen entsprechen, durch automatisierte Tests überprüft und validiert werden.
 #4.9.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Notfallwiederherstellung KI-spezifische Runbooks mit der Wiederherstellung von Modellgewichten, dem Wiederaufbau von GPU-Clustern und der Abbildung von Dienstabhängigkeiten umfasst.

---

### C4.10 Infrastruktur-Compliance & Governance

Erhalten Sie die Einhaltung gesetzlicher Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

 #4.10.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand der SOC 2-, ISO 27001- oder FedRAMP-Kontrollen bewertet wird, einschließlich der automatisierten Erfassung von Nachweisen.
 #4.10.2    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass die Infrastruktur-Dokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.
 #4.10.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Bewertung der Compliance-Auswirkungen unterzogen werden, einschließlich regulatorischer Genehmigungsprozesse für risikoreiche Änderungen.

---

### C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten, einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

 #4.11.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird.
 #4.11.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mit TPM 2.0, Intel TXT oder AMD SVM validiert wird.
 #4.11.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass der GPU-Speicher zwischen Arbeitslasten mittels SR-IOV, MIG (Multi-Instance GPU) oder einer entsprechenden Hardware-Partitionierung isoliert ist, wobei eine Speicherbereinigung zwischen den Jobs erfolgt.
 #4.11.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Lieferkette für AI-Hardware eine Herkunftsüberprüfung mit Herstellerzertifikaten und eine Validierung von manipulationssicherer Verpackung beinhaltet.
 #4.11.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Hardware-Sicherheitsmodule (HSMs) AI-Modellgewichte und kryptografische Schlüssel mit einer FIPS 140-2 Level 3- oder Common Criteria EAL4+-Zertifizierung schützen.

---

### C4.12 Kanten- und verteilte KI-Infrastruktur

Sichere verteilte KI-Einsätze, einschließlich Edge Computing, föderiertem Lernen und Multi-Site-Architekturen.

 #4.12.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-AI-Geräte sich mit der zentralen Infrastruktur über mutual TLS authentifizieren und dass die Gerätezertifikate gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie ausgetauscht werden.
 #4.12.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-Geräte einen sicheren Start mit verifizierten Signaturen und einer Rollback-Schutzfunktion implementieren, um Firmware-Abwärtstransferangriffe zu verhindern.
 #4.12.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.
 #4.12.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfähigkeiten mit sicherer lokaler Speicherung umfasst.

---

### C4.13 Multi-Cloud- und Hybrid-Infrastruktur-Sicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybriden Cloud-On-Premises-Bereitstellungen.

 #4.13.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.
 #4.13.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass der Cloud-übergreifende Datentransfer Ende-zu-Ende-Verschlüsselung mit kundenseitig verwalteten Schlüsseln verwendet und Datenresidenzkontrollen gemäß der jeweiligen Gerichtsbarkeit durchgesetzt werden.
 #4.13.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass hybride Cloud-AI-Workloads konsistente Sicherheitsrichtlinien sowohl in On-Premise- als auch in Cloud-Umgebungen mit einheitlichem Monitoring und Alarme implementieren.
 #4.13.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Vermeidung von Cloud-Anbieter-Bindung tragbare Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfasst.
 #4.13.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausbreitung von Ressourcen verhindern als auch unautorisierte Kosten für datenübergreifende Cloud-Übertragungen unterbinden.

---

### C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Automatisierungspipelines für die Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

 #4.14.1    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob GitOps-Repositories signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln implementiert sind, die direkte Pushes zu Hauptzweigen verhindern.
 #4.14.2    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass die Infrastrukturautomatisierung Drift-Erkennung mit automatischen Behebungs- und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für unautorisierte Änderungen ausgelöst werden.
 #4.14.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die automatisierte Bereitstellung der Infrastruktur eine Überprüfung der Sicherheitsrichtlinien beinhaltet und die Bereitstellung bei nicht konformen Konfigurationen blockiert.
 #4.14.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse der Infrastrukturautomatisierung über externe Geheimnis-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.
 #4.14.5    Niveau: 3    Rolle: V
 Überprüfen Sie, ob die selbstheilende Infrastruktur Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Beteiligte umfasst.

---

### C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantum Kryptographie und quantensichere Protokolle einsetzen.

 #4.15.1    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur NIST-zertifizierte postquantum-kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert.
 #4.15.2    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass Quanten-Schlüsselaustauschsysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.
 #4.15.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Agilitätsrahmen eine schnelle Migration zu neuen postquanten Algorithmus ermöglichen, einschließlich automatisierter Zertifikats- und Schlüsselrotation.
 #4.15.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass die Quanten-Bedrohungsmodellierung die Anfälligkeit der KI-Infrastruktur für Quantenangriffe bewertet und dokumentierte Migrationszeitpläne sowie Risikoanalysen enthält.
 #4.15.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase einen Schutz-in-Tiefe bieten und eine Leistungsüberwachung durchführen.

---

### C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie AI-Arbeitslasten und Modellgewichte mithilfe von hardwarebasierten Trusted Execution Environments und Technologien für vertrauliches Computing.

 #4.16.1    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.
 #4.16.2    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit vertraulichem Computing) KI-Workloads mit hardwaregestützter Speicher­verschlüsselung isolieren.
 #4.16.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Remote-Attestierung die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität der Ausführungsumgebung geladen werden.
 #4.16.4    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass vertrauliche KI-Inferenzdienste die Modellextraktion durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.
 #4.16.5    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus der sicheren Enklave mit Fernattestierung und verschlüsselten Kommunikationskanälen verwaltet.
 #4.16.6    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Mehrparteienberechnung (SMPC) gemeinsames KI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.

---

### C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme zur datenschutzfreundlichen KI-Verifikation und -Authentifizierung, ohne sensible Informationen preiszugeben.

 #4.17.1    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität des KI-Modells und die Herkunft des Trainings verifizieren, ohne Modellgewichte oder Trainingsdaten offenzulegen.
 #4.17.2    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.
 #4.17.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderiertes KI ermöglichen, ohne einzelne Datensätze offenzulegen.
 #4.17.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge Machine Learning (ZKML)-Systeme überprüfbare KI-Schlussfolgerungen mit kryptografischem Nachweis der korrekten Berechnung ermöglichen.
 #4.17.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Sammelverifizierung und reduziertem Rechenaufwand bieten.

---

### C4.18 Schutz vor Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor zeitlichen, leistungsbezogenen, elektromagnetischen und cache-basierten Seitenkanalangriffen, die sensible Informationen preisgeben könnten.

 #4.18.1    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die AI-Inferenzzeit durch Algorithmen mit konstanter Laufzeit und Padding normalisiert wird, um zeitbasierte Modellextraktionsangriffe zu verhindern.
 #4.18.2    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass der Schutz vor Leistungsanalyse Rauschinjektion, Netzleitungsfilterung und randomisierte Ausführungsmuster für KI-Hardware umfasst.
 #4.18.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Seiteneffektminderung basierend auf dem Cache Cache-Partitionierung, Zufallszuweisung und Flush-Befehle verwendet, um Informationslecks zu verhindern.
 #4.18.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.
 #4.18.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass mikroarchitektonische Seitenkanalabwehrmechanismen spekulative Ausführungssteuerungen und die Verschleierung von Speicherzugriffsmustern beinhalten.

---

### C4.19 Neuromorphe & spezialisierte KI-Hardware-Sicherheit

Sichern Sie neu aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

 #4.19.1    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Sicherheit von neuromorphen Chips die Verschlüsselung von Spike-Mustern, den Schutz der synaptischen Gewichte und die hardwarebasierte Validierung der Lernregeln umfasst.
 #4.19.2    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Tamper-Mechanismen und sicheres Laden der Konfiguration mit authentifizierten Updates implementieren.
 #4.19.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root of Trust und eine sichere Schlüsselspeicherung mit Manipulationserkennung umfasst.
 #4.19.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass optische Computersysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.
 #4.19.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung umfassen.

---

### C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

 #4.20.1    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Infrastruktur für homomorphe Verschlüsselung verschlüsselte Berechnungen bei sensiblen KI-Arbeitslasten mit kryptographischer Integritätsprüfung und Leistungsüberwachung ermöglicht.
 #4.20.2    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Systeme für private Informationsabfrage Datenbankabfragen ermöglichen, ohne Abfragemuster preiszugeben, und dabei den Zugriffsmustern kryptografischen Schutz bieten.
 #4.20.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Mehrparteienberechnungsprotokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.
 #4.20.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwert-Kryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.
 #4.20.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Leistung des datenschutzwahrenden Rechnens durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert ist, während kryptografische Sicherheitsgarantien erhalten bleiben.

---

### C4.15 Agent Framework Cloud-Integration Sicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises-/Cloud-Architekturen.

 #4.15.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Integration der Cloud-Speicherung eine Ende-zu-Ende-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.
 #4.15.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden.
 #4.15.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung beinhaltet.
 #4.15.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Anforderungen an den Datenaufenthalt durch kryptografische Bestätigung der Speicherorte durchgesetzt werden.
 #4.15.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Sicherheitsbewertungen von Cloud-Anbietern agentenspezifische Bedrohungsmodellierung und Risikoanalyse beinhalten.

---

### Referenzen

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

## C5 Zugriffskontrolle und Identität für KI-Komponenten und Benutzer

### Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und Laufzeitdurchsetzung gemäß Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Bereiche interagieren, mit kontinuierlicher Überprüfung und Auditmöglichkeiten.

---

### C5.1 Identitätsverwaltung & Authentifizierung

Richten Sie kryptografisch gesicherte Identitäten für alle Entitäten ein, mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

 #5.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale sich über einen zentralisierten unternehmensweiten Identitätsanbieter (IdP) unter Verwendung der OIDC/SAML-Protokolle mit eindeutigen Identitäts-zu-Token-Zuordnungen authentifizieren (keine gemeinsamen Konten oder Zugangsdaten).
 #5.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass bei risikoreichen Vorgängen (Modelldeployment, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen an Produktionskonfigurationen) Multi-Faktor-Authentifizierung oder Step-up-Authentifizierung mit Sitzungsnevalidierung erforderlich ist.
 #5.1.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass neue Verantwortliche eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugang zu Produktionssystemen erhalten.
 #5.1.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Zugriffsüberprüfungen vierteljährlich durchgeführt werden, mit automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und Workflows zur De-Provisionierung.
 #5.1.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Laufzeit von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.

---

### C5.2 Ressourcenautorisierung & Prinzip der minimalen Rechte

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

 #5.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Erlaubnislisten und Standard-Ablehnungsrichtlinien durchsetzt.
 #5.2.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Prinzipien der geringsten Privilegien standardmäßig bei Dienstkonten durchgesetzt werden, beginnend mit Lesezugriffsrechten, und dass für Schreibzugriffe eine dokumentierte geschäftliche Begründung erforderlich ist.
 #5.2.3    Niveau: 1    Rolle: V
 Überprüfen Sie, ob alle Änderungen der Zugriffskontrolle mit genehmigten Änderungsanforderungen verknüpft und unveränderlich protokolliert sind, einschließlich Zeitstempel, Akteur-Identitäten, Ressourcenkennungen und Berechtigungsdifferenzen.
 #5.2.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) übertragen werden und eine konsistente Durchsetzung der Richtlinien gewährleistet ist.
 #5.2.5    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob unautorisierte Zugriffsversuche und Privilegienerhöhungen Echtzeitwarnungen mit kontextbezogenen Metadaten an SIEM-Systeme innerhalb von 5 Minuten auslösen.

---

### C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollmotoren (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

 #5.3.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder vergleichbar) ausgelagert werden, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist.
 #5.3.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Richtlinien dynamische Attribute zur Laufzeit auswerten, einschließlich Benutzerfreigabestufe, Ressourcensensitivitätsklassifikation, Anforderungskontext, Mandantenisolation und zeitlichen Beschränkungen.
 #5.3.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Richtliniendefinitionen versioniert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion bereitgestellt werden.
 #5.3.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob die Ergebnisse der Policy-Auswertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.
 #5.3.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Zeitüberschreitungswerte (TTL) des Richtlinien-Caches für hochsensible Ressourcen 5 Minuten und für Standardressourcen mit Cache-Invalidierungsmöglichkeiten 1 Stunde nicht überschreiten.

---

### C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Richtlinien für Zeilenebenen-Sicherheit.

 #5.4.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass alle Vektor-Datenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode.
 #5.4.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass zeilenbasierte Sicherheitsrichtlinien (RLS) und feldbasierte Maskierung mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.
 #5.4.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen "Confused Deputy-Angriffe" verhindern, indem sie Abfragen sofort abbrechen und explizite Autorisierungsfehlercodes zurückgeben, anstatt leere Ergebnismengen zu liefern.
 #5.4.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass die Latenzzeit der Richtlinienbewertung kontinuierlich überwacht wird und automatisierte Warnungen bei Zeitüberschreitungen ausgelöst werden, die eine Umgehung der Autorisierung ermöglichen könnten.
 #5.4.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Abfrage-Wiederholungsmechanismen Autorisierungsrichtlinien neu bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.

---

### C5.5 Ausgabe-Filterung & Datenschutzmaßnahmen

Implementieren Sie Nachbearbeitungskontrollen, um die unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

 #5.5.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Post-Inferenz-Filtermechanismen unautorisierte PII, klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden.
 #5.5.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in Modellausgaben gegen die Berechtigungen des Aufrufers überprüft und entfernt werden, wenn ein unautorisierter Zugriff festgestellt wird.
 #5.5.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Ausgabeformatbeschränkungen (bereinigte PDFs, metadatenfreie Bilder, genehmigte Dateitypen) basierend auf Benutzerberechtigungsstufen und Datenklassifizierungen durchgesetzt werden.
 #5.5.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.
 #5.5.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass hochriskante Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptografische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenoffenlegung enthalten.

---

### C5.6 Mandanten-Isolierung

Sorgen Sie für kryptografische und logische Isolation zwischen Mietern in gemeinsamer KI-Infrastruktur.

 #5.6.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-getrennt sind und bei Löschung des Mandanten oder Beendigung der Sitzung sicher gelöscht werden.
 #5.6.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jede API-Anfrage einen authentifizierten Mandantenbezeichner enthält, der kryptographisch gegen den Sitzungskontext und die Benutzerberechtigungen validiert wird.
 #5.6.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Netzwerkrichtlinien Standard-Verweigerungsregeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.
 #5.6.4    Niveau: 3    Rolle: D
 Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für kundenverwaltete Schlüssel (CMK) und kryptografischer Isolation zwischen den Datenspeichern der Mandanten.

---

### C5.7 Autonome Agenten-Autorisierung

Steuern Sie Berechtigungen für KI-Agenten und autonome Systeme durch segmentierte Fähigkeitstoken und kontinuierliche Autorisierung.

 #5.7.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass autonome Agenten scopespezifische Fähigkeitstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Einschränkungen auflisten.
 #5.7.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass risikoreiche Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, finanzielle Transaktionen) standardmäßig deaktiviert sind und eine explizite Autorisierung zur Aktivierung mit geschäftlichen Begründungen erforderlich ist.
 #5.7.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass Zugriffstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und sicherstellen, dass sie nicht offline gespeichert oder wiederverwendet werden können.
 #5.7.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass von Agenten initiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine unterzogen werden, mit vollständiger Kontextbewertung und Prüfprotokollierung.
 #5.7.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.

---

### Referenzen

#### Standards & Rahmenwerke

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Implementierungsanleitungen

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### KI-spezifische Sicherheit

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Lieferkettensicherheit für Modelle, Frameworks und Daten

### Kontrollziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, Frameworks oder Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzubetten. Diese Kontrollen bieten durchgehende Herkunftsnachweise, Schwachstellenmanagement und Überwachung zum Schutz des gesamten Modelllebenszyklus.

---

### C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie Herkunft, Lizenzen und versteckte Verhaltensweisen von Modellen Dritter, bevor Sie eine Feinabstimmung oder Bereitstellung vornehmen.

 #6.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass jedes Drittanbieter-Modell-Artefakt eine signierte Herkunftsaufzeichnung enthält, die das Quellrepository und den Commit-Hash identifiziert.
 #6.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojaner-Auslöser gescannt werden.
 #6.1.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Transfer-Learning-Feinabstimmungen die adversariale Bewertung bestehen, um versteckte Verhaltensweisen zu erkennen.
 #6.1.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Modelllizenzen, Exportkontrollmarkierungen und Datenherkunftserklärungen in einem ML-BOM-Eintrag erfasst werden.
 #6.1.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Modelle mit hohem Risiko (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe weiterhin unter Quarantäne bleiben.

---

### C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und Bibliotheken nach CVEs und schädlichem Code, um den Laufzeit-Stack sicher zu halten.

 #6.2.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass CI-Pipelines Abhängigkeits-Scanner für KI-Frameworks und kritische Bibliotheken ausführen.
 #6.2.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob kritische Schwachstellen (CVSS ≥ 7,0) die Freigabe von Produktionsabbildern verhindern.
 #6.2.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebetteten ML-Bibliotheken ausgeführt wird.
 #6.2.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Vorschläge für Framework-Upgrades eine Sicherheitsauswirkungsbewertung enthalten, die sich auf öffentliche CVE-Feeds bezieht.
 #6.2.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksladungen, die von der signierten SBOM abweichen, Alarm schlagen.

---

### C6.3 Abhängigkeiten Festlegen und Verifizieren

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationsfreie Artefakte zu garantieren.

 #6.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob alle Paketmanager Versionsfixierung über Lockfiles durchsetzen.
 #6.3.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass unveränderliche Digests anstelle von veränderlichen Tags in Containerreferenzen verwendet werden.
 #6.3.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass die Reproducible-Build-Prüfungen Hashes über CI-Durchläufe hinweg vergleichen, um identische Ergebnisse sicherzustellen.
 #6.3.4    Niveau: 2    Rolle: V
 Überprüfen Sie, dass Build-Bescheinigungen für 18 Monate zur Audit-Nachverfolgbarkeit gespeichert werden.
 #6.3.5    Niveau: 3    Rolle: D
 Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um aktualisierte oder geforkte feste Versionen zu erstellen.

---

### C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlaube den Download von Artefakten nur von kryptografisch verifizierten, von der Organisation genehmigten Quellen und blockiere alles andere.

 #6.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registern heruntergeladen werden.
 #6.4.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers validieren, bevor Artefakte lokal zwischengespeichert werden.
 #6.4.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Auswärtsproxies nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie vertrauenswürdiger Quellen durchzusetzen.
 #6.4.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob die Repository-Whitelist vierteljährlich überprüft wird und für jeden Eintrag ein Nachweis über die geschäftliche Rechtfertigung vorliegt.
 #6.4.5    Niveau: 3    Rolle: V
 Überprüfen Sie, ob Richtlinienverstöße die Quarantäne von Artefakten und den Rollback abhängiger Pipeline-Ausführungen auslösen.

---

### C6.5 Bewertung der Risiken bei Drittanbieter-Datensätzen

Bewerten Sie externe Datensätze auf Vergiftung, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

 #6.5.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass externe Datensätze einer Bewertung des Poisoning-Risikos unterzogen werden (z. B. Daten-Fingerabdruck, Ausreißererkennung).
 #6.5.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.
 #6.5.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Herkunft und Lizenzbedingungen für Datensätze in ML-BOM-Einträgen erfasst werden.
 #6.5.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob die regelmäßige Überwachung Verschiebungen oder Korruption in gehosteten Datensätzen erkennt.
 #6.5.5    Niveau: 3    Rolle: D
 Stellen Sie sicher, dass nicht erlaubte Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Bereinigen entfernt werden.

---

### C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Lieferkettenbedrohungen frühzeitig durch CVE-Feeds, Audit-Log-Analysen und Red-Team-Simulationen.

 #6.6.1    Niveau: 1    Rolle: V
 Stellen Sie sicher, dass CI/CD-Auditprotokolle an SIEM-Systeme übertragen werden, um anomale Paketabrufe oder manipulierte Build-Schritte zu erkennen.
 #6.6.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Vorfallsreaktions-Playbooks Rücksetzverfahren für kompromittierte Modelle oder Bibliotheken enthalten.
 #6.6.3    Niveau: 3    Rolle: V
 Überprüfen Sie, ob die Threat‑Intel‑Anreicherung ML‑spezifische Indikatoren (z. B. IoCs für Modellvergiftung) bei der Alarmbearbeitung kennzeichnet.

---

### C6.7 ML-BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, ML-spezifische SBOMs (ML-BOMs), damit nachgelagerte Anwender die Integrität der Komponenten bei der Bereitstellung überprüfen können.

 #6.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Modell-Artefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.
 #6.7.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die ML-BOM-Erstellung und die Cosign-Signierung im CI automatisiert sind und für das Zusammenführen erforderlich sind.
 #6.7.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass die Vollständigkeitsprüfungen von ML-BOM den Build abbrechen, wenn Metadaten zu Komponenten (Hash, Lizenz) fehlen.
 #6.7.4    Niveau: 2    Rolle: V
 Überprüfen Sie, dass nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zur Bereitstellungszeit zu validieren.
 #6.7.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass ML‑BOMs versioniert und verglichen werden, um unautorisierte Änderungen zu erkennen.

---

### Referenzen

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

## C7 Modellverhalten, Ausgabe Steuerung & Sicherheitsgarantie

### Kontrollziel

Modelausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und kontinuierlich in der Produktion überwacht werden. Dadurch werden Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen reduziert, während das Vertrauen der Nutzer und die Einhaltung von Vorschriften erhöht werden.

---

### C7.1 Durchsetzung des Ausgabeformats

Strenge Schemata, eingeschränkte Decodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte sich ausbreiten.

 #7.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Antwortschemata (z. B. JSON-Schema) im System-Prompt angegeben sind und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus.
 #7.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass das eingeschränkte Decodieren (Stoppzeichen, Regex, Maximalanzahl an Tokens) aktiviert ist, um Overflow- oder Prompt-Injection-Seitenkanäle zu verhindern.
 #7.1.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.
 #7.1.4    Niveau: 3    Rolle: V
 Überprüfen Sie, dass falsche Ausgabeereignisse protokolliert, mit einer Ratenbegrenzung versehen und im Monitoring sichtbar gemacht werden.

---

### C7.2 Halluzinationserkennung und -minderung

Unsicherheitsabschätzung und Fallback-Strategien begrenzen erfundene Antworten.

 #7.2.1    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Token-Level-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Konfidenzbewertung zuweisen.
 #7.2.2    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Antworten unterhalb eines konfigurierbaren Vertrauensschwellenwerts Rückfall-Workflows auslösen (z. B. retrieval-augmented Generation, sekundäres Modell oder manuelle Überprüfung).
 #7.2.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Halluzinationsvorfälle mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungspipelines weitergeleitet werden.
 #7.2.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.
 #7.2.5    Niveau: 3    Rolle: V
 Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.

---

### C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

 #7.3.1    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Vor- und Nachgenerierungs-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren.
 #7.3.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort durchgeführt werden; Verstöße führen zu einem Datenschutzvorfall.
 #7.3.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Vertraulichkeitsetiketten (z. B. Geschäftsgeheimnisse) modalitätsübergreifend weitergegeben werden, um ein Leck in Text, Bildern oder Code zu verhindern.
 #7.3.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Versuche zum Umgehen von Filtern oder Klassifizierungen mit hohem Risiko eine sekundäre Genehmigung oder eine erneute Benutzer-Authentifizierung erfordern.
 #7.3.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Benutzeralter-/Rollen-Kontext widerspiegeln.

---

### C7.4 Ausgabe- und Handlungseinschränkung

Ratenbegrenzungen und Genehmigungsschranken verhindern Missbrauch und übermäßige Autonomie.

 #7.4.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass die Kontingente pro Benutzer und pro API-Schlüssel Anfragen, Tokens und Kosten mit exponentiellem Backoff bei 429-Fehlern begrenzen.
 #7.4.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkanrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Genehmigung erfordern.
 #7.4.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob cross-modale Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht verwendet werden können, um schädliche Inhalte einzuschleusen.
 #7.4.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass die Agentendelegationstiefe, Rekursionsgrenzen und erlaubte Werkzeuglisten explizit konfiguriert sind.
 #7.4.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass die Überschreitung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Erfassung auslöst.

---

### C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlerbehebung.

 #7.5.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass benutzerseitige Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikoabschätzung dies für angemessen hält.
 #7.5.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass erzeugte Erklärungen keine sensiblen Systemaufforderungen oder proprietären Daten preisgeben.
 #7.5.3    Niveau: 3    Rolle: D
 Überprüfen Sie, ob das System Token-Ebenen-Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und für autorisierte Prüfungen speichert.
 #7.5.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Erklärbarkeitsartefakte zusammen mit Modellversionen versionskontrolliert werden, um Prüfbarkeit zu gewährleisten.

---

### C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt den Kreis zwischen Entwicklung und Produktion.

 #7.6.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden.
 #7.6.2    Niveau: 1    Rolle: V
 Stellen Sie sicher, dass für jede Sicherheitsmetrik Warnschwellen definiert sind, einschließlich Eskalationspfaden für Bereitschaftspersonal.
 #7.6.3    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.
 #7.6.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder die Regelaktualisierung zurückfließen.
 #7.6.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Überwachungspipelines auf Penetration getestet sind und zugangskontrolliert werden, um das Lecken sensibler Protokolle zu vermeiden.

---

### 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabekontrollen und Rückverfolgbarkeit durchsetzen.

 #7.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bild, Video, Audio) untersagen.
 #7.7.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Aufforderungen darauf gefiltert werden, Versuche zur Erzeugung von Nachahmungen, sexuell expliziten Deepfakes oder Medien, die reale Personen ohne deren Zustimmung darstellen, zu erkennen.
 #7.7.3    Niveau: 2    Rolle: V
 Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unautorisierte Vervielfältigung von urheberrechtlich geschütztem Medium zu verhindern.
 #7.7.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um eine nachgelagerte Rückverfolgbarkeit zu gewährleisten.
 #7.7.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und durch eine Ratenbegrenzung eingeschränkt werden; wiederholter Missbrauch wird zur Überwachung gemeldet.

### Referenzen

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

## C8 Speicher, Embeddings & Vektordatenbanksicherheit

### Kontrollziel

Embeddings und Vektorspeicher fungieren als das „lebendige Gedächtnis“ zeitgenössischer KI-Systeme, indem sie kontinuierlich vom Benutzer bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) wieder in Modellkontexte einbringen. Wenn dieses Gedächtnis unbeaufsichtigt bleibt, kann es personenbezogene Daten (PII) preisgeben, gegen Einwilligungen verstoßen oder umgekehrt genutzt werden, um den Originaltext zu rekonstruieren. Ziel dieser Kontrollfamilie ist es, Memory-Pipelines und Vektordatenbanken so zu härten, dass der Zugriff nach dem Prinzip der geringsten Privilegien gewährt wird, Embeddings datenschutzfreundlich sind, gespeicherte Vektoren ablaufen oder auf Anforderung widerrufen werden können und das Gedächtnis eines Nutzers niemals die Eingaben oder Ausgaben eines anderen Nutzers beeinträchtigt.

---

### C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzung feinkörniger Zugriffskontrollen für jede Vektorensammlung.

 #8.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Zugriffssteuerungsregeln auf Zeilen-/Namensraumebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokumenten-Tag einschränken.
 #8.1.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass API-Schlüssel oder JWTs bereichsspezifische Claims enthalten (z. B. Sammlungs-IDs, Aktionsverben) und mindestens vierteljährlich rotiert werden.
 #8.1.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Versuche zur Eskalation von Berechtigungen (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und in einem SIEM protokolliert werden.
 #8.1.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Vektor-Datenbank das Protokoll mit folgenden Angaben führt: Subjekt-Identifier, Operation, Vektor-ID/Namensraum, Ähnlichkeitsgrenzwert und Ergebnisanzahl.
 #8.1.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsmängel getestet werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.

---

### C8.2 Einbettungsbereinigung und Validierung

Vor der Vektorisierung Text auf PII (personenbezogene Daten) vorab prüfen, schwärzen oder pseudonymisieren und optional die Einbettungen nachverarbeiten, um verbleibende Signale zu entfernen.

 #8.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass personenbezogene Daten (PII) und regulierte Daten durch automatisierte Klassifizierer erkannt und vor dem Embedding maskiert, tokenisiert oder entfernt werden.
 #8.2.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Embedding-Pipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder in Quarantäne stellen.
 #8.2.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Privacy-Sanitierung angewendet wird.
 #8.2.4    Niveau: 2    Rolle: V
 Vergewissern Sie sich, dass die Wirksamkeit der Bereinigung (z. B. Rückruf bei der PII-Radikalisierung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.
 #8.2.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Sanitierungskonfigurationen versioniert werden und Änderungen einer Peer-Review unterzogen werden.

---

### C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO „Recht auf Vergessenwerden“ und ähnliche Gesetze erfordern eine zeitnahe Löschung; Vektorspeicher müssen daher TTLs, harte Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

 #8.3.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jeder Vektor- und Metadatensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.
 #8.3.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.
 #8.3.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass logische Löschungen durch kryptografisches Zerstören der Speicherblöcke gefolgt werden, wenn die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssel-Tresorschlüssels.
 #8.3.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach dem Ablauf bei der Suche nach den nächsten Nachbarn ausgeschlossen werden.

---

### C8.4 Verhinderung von Embedding-Inversion und Datenleckage

Neuere Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Störung von Datenschutz-Neuronen und Verschlüsselung auf Anwendungsebene—können die Inversionsrate auf Token-Ebene auf unter 5 % senken.

 #8.4.1    Niveau: 1    Rolle: V
 Stellen Sie sicher, dass ein formelles Bedrohungsmodell, das Inversions-, Mitgliedschafts- und Attributinferenzangriffe abdeckt, existiert und jährlich überprüft wird.
 #8.4.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direkten Zugriffen durch Infrastrukturadministratoren oder Cloud-Mitarbeiter schützt.
 #8.4.3    Niveau: 3    Rolle: V
 Überprüfen Sie, ob die Abwehrparameter (ε für DP, Rauschσ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten.
 #8.4.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Inversionsresistenzmetriken Teil der Freigabetore für Modellaktualisierungen sind und dabei Regressionsbudgets definiert werden.

---

### C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Leckagen bleiben ein großes Risiko bei RAG: unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden sichtbar machen.

 #8.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass jede Abfrage zur Datenabruf vor der Übergabe an das LLM-Prompt anhand der Mandanten-/Benutzer-ID nachgefiltert wird.
 #8.5.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Sammlungsnamen oder Namespaced-IDs pro Benutzer oder Mandant gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.
 #8.5.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Ähnlichkeitsergebnisse oberhalb eines konfigurierbaren Entfernungsgrenzwerts, die jedoch außerhalb des Anwendungsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.
 #8.5.4    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Multi-Tenant-Stresstests adversarielle Abfragen simulieren, die versuchen, Dokumente außerhalb des Geltungsbereichs abzurufen, und dabei keine Datenlecks aufweisen.
 #8.5.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.

---

### C8.6 Erweiterte Sicherheit von Speichersystemen

Sicherheitskontrollen für komplexe Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolation und Validierung.

 #8.6.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp haben.
 #8.6.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Speicher-Konsolidierungsprozesse eine Sicherheitsvalidierung beinhalten, um das Einspeisen bösartiger Erinnerungen durch Inhaltsbereinigung, Quellverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.
 #8.6.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherabrufanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse des Abfragemusters, Durchsetzung der Zugriffskontrolle und Filterung der Ergebnisse zu verhindern.
 #8.6.4    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass Mechanismen zum Vergessen von Speicher sensible Informationen sicher mit kryptografischen Löschungsgarantien löschen, indem Sie Schlüssel-Löschung, mehrfache Überschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten verwenden.
 #8.6.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Prüfprotokolle und automatische Warnmeldungen verwendet werden, wenn sich der Speicherinhalt außerhalb der normalen Betriebsbedingungen ändert.

---

### Referenzen

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

## 9 Autonome Orchestrierung & agentische Handlungssicherheit

### Kontrollziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb begrenzter Kosten- und Risiko-Schwellenwerte liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Werkzeugmissbrauch, Agentenschleifenerkennung, Kommunikationsentführung, Identitätsfälschung, Schwarmmanipulation und Absichtsmanipulation.

---

### 9.1 Agent-Aufgabenplanung und Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

 #9.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob maximale Rekursionstiefe, Breite, Echtzeit, Token und monetäre Kosten pro Agenten-Ausführung zentral konfiguriert und versionskontrolliert sind.
 #9.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, Finanztransfers) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern.
 #9.1.3    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Echtzeit-Ressourcenmonitore eine Circuit-Breaker-Unterbrechung auslösen, wenn eine Budgetschwelle überschritten wird, und dadurch eine weitere Aufgabenerweiterung stoppen.
 #9.1.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Circuit-Breaker-Ereignisse mit Agenten-ID, Auslösebedingung und erfasstem Planzustand für die forensische Überprüfung protokolliert werden.
 #9.1.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass Sicherheitstests Szenarien mit Budgeterschöpfung und ausufernden Plänen abdecken und ein sicheres Anhalten ohne Datenverlust bestätigen.
 #9.1.6    Niveau: 3    Rolle: D
 Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code ausgedrückt und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.

---

### 9.2 Tool-Plugin-Sandboxing

Isoliere Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

 #9.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Werkzeug/Plugin in einem Betriebssystem-, Container- oder WASM-Level-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird.
 #9.2.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Ressourcenkontingente (CPU, Arbeitsspeicher, Festplatte, Netzwerkausgang) und Ausführungs-Timeouts durchgesetzt und protokolliert werden.
 #9.2.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Tool-Binärdateien oder Descriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.
 #9.2.4    Niveau: 2    Rolle: V
 Verifizieren Sie, dass die Sandbox-Telemetrie in ein SIEM gestreamt wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Alarme aus.
 #9.2.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass risikoreiche Plugins vor der Produktivsetzung einer Sicherheitsüberprüfung und einem Penetrationstest unterzogen werden.
 #9.2.6    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Versuche, die Sandbox zu umgehen, automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung in Quarantäne gestellt wird.

---

### 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und Stoppen von unkontrollierter Agent-zu-Agent-Rekursion und Kostenexplosionen.

 #9.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.
 #9.3.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Agenten eine eindeutige Invocation-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.
 #9.3.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass kumulative Compute-Unit- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits bricht die Kette ab.
 #9.3.4    Niveau: 3    Rolle: V
 Überprüfen Sie, dass die formale Analyse oder Modellprüfung die Abwesenheit von unbeschränkter Rekursion in Agentenprotokollen nachweist.
 #9.3.5    Niveau: 3    Rolle: D
 Überprüfen Sie, ob Loop-Abbruch-Ereignisse Warnmeldungen erzeugen und kontinuierliche Verbesserungsmetriken speisen.

---

### 9.4 Protokollebene-Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Entführungen oder Manipulationen zu verhindern.

 #9.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Nachrichten zwischen Agent und Werkzeug sowie zwischen Agenten authentifiziert sind (z. B. durch gegenseitiges TLS oder JWT) und durchgängig verschlüsselt sind.
 #9.4.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Schemata strikt validiert werden; unbekannte Felder oder fehlerhaft formatierte Nachrichten werden abgelehnt.
 #9.4.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nachrichtenlast einschließlich der Werkzeugparameter abdecken.
 #9.4.4    Niveau: 2    Rolle: D
 Überprüfen Sie, ob der Replay-Schutz (Nonces oder Zeitstempelfenster) auf Protokollebene durchgesetzt wird.
 #9.4.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Protokollimplementierungen durch Fuzzing und statische Analyse auf Injektions- oder Deserialisierungsfehler überprüft werden.

---

### 9.5 Agent-Identität & Manipulationssicherheit

Stellen Sie sicher, dass Handlungen zuordenbar und Änderungen erkennbar sind.

 #9.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass jede Agenteninstanz eine eindeutige kryptografische Identität (Schlüsselpaar oder hardwaregebundene Anmeldeinformationen) besitzt.
 #9.5.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass alle Agentenaktionen signiert und mit einem Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.
 #9.5.3    Niveau: 2    Rolle: V
 Überprüfen Sie, ob manipulationssichere Protokolle in einem nur-anhängbaren oder einmal beschreibbaren Medium gespeichert werden.
 #9.5.4    Niveau: 3    Rolle: D
 Überprüfen Sie, ob Identitätsschlüssel nach einem definierten Zeitplan und bei Anzeichen eines Kompromisses wechseln.
 #9.5.5    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.

---

### 9.6 Multi-Agent-Schwarm-Risiko-Reduzierung

Mildern Sie Gefahren des kollektiven Verhaltens durch Isolierung und formale Sicherheitsmodellierung.

 #9.6.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden.
 #9.6.2    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Schwarmverhalten modelliert und formal auf Lebendigkeit und Sicherheit verifiziert werden, bevor sie eingesetzt werden.
 #9.6.3    Niveau: 3    Rolle: D
 Verifizieren Sie, dass Laufzeit-Monitore emergente unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und korrigierende Maßnahmen einleiten.

---

### 9.7 Benutzer- und Werkzeugauthentifizierung / -autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede agentengesteuerte Aktion.

 #9.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale gegenüber nachgelagerten Systemen authentifizieren und Endbenutzeranmeldeinformationen niemals wiederverwenden.
 #9.7.2    Niveau: 2    Rolle: D
 Überprüfen Sie, dass fein granulare Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er dabei übergeben darf.
 #9.7.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Berechtigungsprüfungen bei jedem Aufruf erneut durchgeführt werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.
 #9.7.4    Niveau: 3    Rolle: D
 Überprüfen Sie, ob delegierte Berechtigungen automatisch ablaufen und nach Zeitüberschreitung oder Umfangsänderung eine erneute Zustimmung erfordern.

---

### 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und mit Integritätsschutz versehen Sie alle Nachrichten zwischen Agenten, um Abhören und Manipulationen zu verhindern.

 #9.8.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass gegenseitige Authentifizierung und perfect-forward-secret-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.
 #9.8.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Fehler führen zu Warnungen und zum Verwerfen der Nachricht.
 #9.8.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.
 #9.8.4    Niveau: 3    Rolle: V
 Überprüfen Sie, ob die formale Verifikation oder Modellprüfung bestätigt, dass Protokoll-Zustandsmaschinen nicht in unsichere Zustände gebracht werden können.

---

### 9.9 Absichtüberprüfung & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

 #9.9.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Pre-Execution-Constraint-Solver vorgeschlagene Aktionen anhand von fest codierten Sicherheits- und Richtlinienregeln prüfen.
 #9.9.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Aktionen mit hoher Auswirkung (finanziell, destruktiv, datenschutzsensitiv) eine ausdrückliche Bestätigung der Absicht vom ausführenden Benutzer erfordern.
 #9.9.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass Nachbedingungsprüfungen validieren, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebeneffekte erreicht haben; Abweichungen lösen einen Rollback aus.
 #9.9.4    Niveau: 3    Rolle: V
 Verifizieren Sie, dass formale Methoden (z. B. Model Checking, Theorembeweise) oder eigenschaftsbasierte Tests nachweisen, dass Agentenpläne alle deklarierten Einschränkungen erfüllen.
 #9.9.5    Niveau: 3    Rolle: D
 Stellen Sie sicher, dass Absichtsdiskrepanzen oder Verletzungen von Einschränkungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.

---

### 9.10 Sicherheitsstrategie für Agentenlogik

Sichere Auswahl und Ausführung verschiedener Schlussfolgerungsstrategien, einschließlich ReAct-, Chain-of-Thought- und Tree-of-Thoughts-Ansätzen.

 #9.10.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Auswahl der Vorgehensweise zur Argumentation deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und ob identische Eingaben innerhalb desselben Sicherheitskontexts zu identischen Strategiewahlen führen.
 #9.10.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) über eine spezifische Eingabevalidierung, Ausgabereinigung und Ausführungszeitbegrenzung verfügt, die auf ihren jeweiligen kognitiven Ansatz abgestimmt ist.
 #9.10.3    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass Übergänge der Denkstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabeeigenschaften, Auswahlkriterienwerten und Ausführungsmetadaten, um die Rekonstruktion der Prüfpfadnachverfolgung zu gewährleisten.
 #9.10.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Tree-of-Thoughts-Argumentation Mechanismen zum Beschneiden von Ästen enthält, die die Erkundung beenden, wenn Richtlinienverstöße, Ressourcengrenzen oder Sicherheitsgrenzen erkannt werden.
 #9.10.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass ReAct (Reason-Act-Observe)-Zyklen Validierungspunkte in jeder Phase enthalten: Überprüfung des Denkschritts, Autorisierung der Handlung und Bereinigung der Beobachtung, bevor fortgefahren wird.
 #9.10.6    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistungskennzahlen der Reasoning-Strategie (Ausführungszeit, Ressourcennutzung, Ausgabequalität) mit automatisierten Warnungen überwacht werden, wenn die Kennzahlen über die konfigurierten Schwellenwerte hinaus abweichen.
 #9.10.7    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.
 #9.10.8    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Sicherheitstests der Denkstrategie Fuzzing mit fehlerhaften Eingaben, gegnerische Eingabeaufforderungen, die darauf abzielen, einen Strategiewechsel zu erzwingen, und Grenzwerttests für jeden kognitiven Ansatz umfassen.

---

### 9.11 Agentlebenszyklus-Zustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Prüfpfaden und definierten Wiederherstellungsverfahren.

 #9.11.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Agenteninitalisierung die Einrichtung einer kryptografischen Identität mit hardware-gesicherten Anmeldeinformationen und unveränderlichen Start-Protokollen umfasst, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter enthalten.
 #9.11.2    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass Agentenzustandsübergänge kryptographisch signiert, mit Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich der auslösenden Ereignisse, des Hashs des vorherigen Zustands, des Hashs des neuen Zustands und der durchgeführten Sicherheitsüberprüfungen.
 #9.11.3    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass die Agent-Abschaltverfahren eine sichere Speicherlöschung mittels kryptografischer Löschung oder mehrmaligem Überschreiben, die Widerrufung von Berechtigungsnachweisen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen.
 #9.11.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Agenten-Wiederherstellungsmechanismen die Zustandsintegrität mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Korruption auf bekannte gute Zustände zurücksetzen, wobei automatisierte Warnungen und manuelle Genehmigungsanforderungen verwendet werden.
 #9.11.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Agent-Persistenzmechanismen sensible Zustandsdaten mit individuellen AES-256-Schlüsseln pro Agent verschlüsseln und eine sichere Schlüsselrotation entsprechend konfigurierbaren Zeitplänen (maximal 90 Tage) mit unterbrechungsfreier Bereitstellung implementieren.

---

### 9.12 Sicherheitsrahmen für die Integration von Werkzeugen

Sicherheitskontrollen für das dynamische Laden von Werkzeugen, deren Ausführung und Ergebnisvalidierung mit definierten Risiko-Bewertungs- und Genehmigungsprozessen.

 #9.12.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Tool-Beschreibungen Sicherheitsmetadaten enthalten, die die erforderlichen Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcenlimits (CPU, Speicher, Netzwerk) und Validierungsanforderungen, die in den Tool-Manifests dokumentiert sind, angeben.
 #9.12.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Werkzeugausführung gegen erwartete Schemata (JSON-Schema, XML-Schema) und Sicherheitsrichtlinien (Ausgabe-Sanitierung, Datenklassifizierung) validiert werden, bevor sie mit Zeitlimitvorgaben und Fehlerbehandlungsverfahren integriert werden.
 #9.12.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcenverbrauch und Rückgabecodes mit strukturiertem Logging für die SIEM-Integration.
 #9.12.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob dynamische Mechanismen zum Laden von Werkzeugen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung sowie Berechtigungsüberprüfung vor der Ausführung implementieren.
 #9.12.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Sicherheitsbewertungen von Tools automatisch für neue Versionen ausgelöst werden, mit verpflichtenden Genehmigungsschritten einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, mit dokumentierten Genehmigungskriterien und SLA-Anforderungen.

---

#### Referenzen

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

## 10 Adversarielle Robustheit & Datenschutzabwehr

### Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchssicher bleiben, wenn sie auf Umgehungs-, Inferenz-, Extraktions- oder Vergiftungsangriffe treffen.

---

### 10.1 Modell-Ausrichtung & Sicherheit

Sichern Sie sich gegen schädliche oder gegen Richtlinien verstoßende Ausgaben ab.

 #10.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass eine Ausrichtungstest-Suite (Red-Team-Eingabeaufforderungen, Jailbreak-Prüfungen, nicht erlaubte Inhalte) versioniert wird und bei jeder Modellfreigabe ausgeführt wird.
 #10.1.2    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Ablehnungs- und sichere Abschluss-Schutzmaßnahmen durchgesetzt werden.
 #10.1.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass ein automatischer Evaluator die Rate schädlicher Inhalte misst und Rückschritte über einen festgelegten Schwellenwert hinaus kennzeichnet.
 #10.1.4    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass das Training zur Gegenmaßnahme gegen Jailbreaks dokumentiert und reproduzierbar ist.
 #10.1.5    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachungen kritische Bereiche abdecken.

---

### 10.2 Härten gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegen manipulierte Eingaben. Robustes adversariales Training und Benchmark-Bewertung sind derzeit der beste Ansatz.

 #10.2.1    Niveau: 1    Rolle: D
 Überprüfen Sie, ob die Projekt-Repositorys Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.
 #10.2.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines Blockierungswarnungen auslöst.
 #10.2.4    Niveau: 3    Rolle: V
 Überprüfen Sie, ob zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken.
 #10.2.5    Niveau: 3    Rolle: V
 Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Robustheitsverlust zu bestätigen.

---

### 10.3 Mitgliedschaftsinferenz-Minderung

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsdatensatz enthalten war. Differentielle Privatsphäre und Maskierung des Vertrauensscores bleiben die effektivsten bekannten Schutzmaßnahmen.

 #10.3.1    Niveau: 1    Rolle: D
 Überprüfen Sie, ob eine pro-Abfrage-Entropie-Regularisierung oder Temperaturskalierung übermäßig zuversichtliche Vorhersagen reduziert.
 #10.3.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob das Training eine ε-begrenzte differentielle Datenschutzoptimierung für sensible Datensätze verwendet.
 #10.3.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass Angriffssimulationen (Shadow-Model- oder Black-Box-Methoden) eine Angriff-AUC von ≤ 0,60 bei nicht verwendeten Daten zeigen.

---

### 10.4 Widerstand gegen Modellinversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen betonen die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen.

 #10.4.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie bei Bedarf Buckets oder Einwegtransformationen.
 #10.4.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen von derselben Instanz drosseln.
 #10.4.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass das Modell mit datenschutzförderndem Rauschen trainiert wurde.

---

### 10.5 Verteidigung gegen Modell-Extraktion

Erkennen und Verhindern unbefugter Klonierung. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

 #10.5.1    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Inferenz-Gateways globale und pro-API-Schlüssel festgelegte Ratenbegrenzungen durchsetzen, die auf den Memorierungsschwellenwert des Modells abgestimmt sind.
 #10.5.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und Eingabe-Pluralität einen automatisierten Extraktionsdetektor speisen.
 #10.5.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass zerbrechliche oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Anfragen gegen einen verdächtigen Klon nachgewiesen werden können.
 #10.5.4    Niveau: 3    Rolle: D
 Überprüfen Sie, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.
 #10.5.5    Niveau: 3    Rolle: V
 Überprüfen Sie, ob Extraktionswarnereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.

---

### 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Erkennen und Neutralisieren von mit Hintertüren versehenen oder vergifteten Eingaben.

 #10.6.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Eingaben vor der Modellausführung durch einen Anomalie-Detektor (z. B. STRIP, Konsistenzbewertung) laufen.
 #10.6.2    Niveau: 1    Rolle: V
 Überprüfen Sie, dass die Schwellenwerte des Detektors auf sauberen/vergifteten Validierungsdatensätzen so eingestellt sind, dass weniger als 5 % Falsch-Positive erreicht werden.
 #10.6.3    Niveau: 2    Rolle: D
 Überprüfen Sie, dass als vergiftet gekennzeichnete Eingaben eine Soft-Sperrung und einen Workflow zur menschlichen Überprüfung auslösen.
 #10.6.4    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass Detektoren mit adaptiven, triggerlosen Backdoor-Angriffen einem Stresstest unterzogen werden.
 #10.6.5    Niveau: 3    Rolle: D
 Stellen Sie sicher, dass Erkennungsleistungsmetriken protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.

---

### 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Aktualisierungen der Sicherheitspolitik basierend auf Bedrohungsinformationen und Verhaltensanalyse.

 #10.7.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion beibehalten wird.
 #10.7.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.
 #10.7.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren.
 #10.7.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.
 #10.7.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Nachweise für die Überprüfung durch das Sicherheitsteam enthalten.

---

### 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

 #10.8.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Reflexionsmechanismen von Agenten eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen enthalten.
 #10.8.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Reflexionsausgaben validiert werden, um eine Manipulation der Selbstbewertungsmechanismen durch feindliche Eingaben zu verhindern.
 #10.8.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die meta-kognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Beeinträchtigungen in den Denkprozessen von Agenten erkennt.
 #10.8.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob sicherheitsrelevante Warnungen basierend auf Reflection eine erweitere Überwachung und potenzielle Workflows für menschliches Eingreifen auslösen.
 #10.8.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitserkenntnissen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.

---

### 10.9 Sicherheit bei Evolution und Selbstverbesserung

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

 #10.9.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.
 #10.9.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Evolutionvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.
 #10.9.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Selbstverbesserungsmechanismen Rückrollfunktionen mit Integritätsprüfung enthalten.
 #10.9.4    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.
 #10.9.5    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen für die Konvergenz.

---

#### Referenzen

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

## 11 Datenschutz und Verwaltung personenbezogener Daten

### Kontrollziel

Gewährleisten Sie strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg – Erfassung, Training, Inferenz und Vorfallsreaktion – damit personenbezogene Daten nur mit klarer Einwilligung, minimalem notwendigem Umfang, nachweisbarer Löschung und formellen Datenschutzgarantien verarbeitet werden.

---

### 11.1 Anonymisierung & Datenminimierung

 #11.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass direkte und Quasi-Identifier entfernt oder gehasht werden.
 #11.1.2    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Alarm schlagen, wenn Schwellenwerte unter die Richtlinie fallen.
 #11.1.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass die Berichte zur Merkmalswichtigkeit des Modells keinen Identifikator-Leckage jenseits von ε = 0,01 wechselseitiger Information nachweisen.
 #11.1.4    Niveau: 3    Rolle: V
 Verifizieren Sie, dass formale Beweise oder die Zertifizierung synthetischer Daten das Re-Identifikationsrisiko ≤ 0,05 selbst bei Verknüpfungsangriffen nachweisen.

---

### 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

 #11.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Löschanfragen von Datenpersonen auf Rohdatensätze, Checkpoints, Einbettungen, Protokolle und Backups innerhalb der Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden.
 #11.2.2    Niveau: 2    Rolle: D
 Verifizieren Sie, dass „Machine-Unlearning“-Routinen physisch neu trainieren oder eine angenäherte Entfernung unter Verwendung zertifizierter Unlearning-Algorithmen durchführen.
 #11.2.3    Niveau: 2    Rolle: V
 Überprüfen Sie, dass die Bewertung des Schattenmodells beweist, dass vergessene Datensätze nach dem Unlearning weniger als 1 % der Ausgaben beeinflussen.
 #11.2.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Löschvorgänge unveränderlich protokolliert und für Regulierungsbehörden prüfbar sind.

---

### 11.3 Differenzielle Datenschutzmaßnahmen

 #11.3.1    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Datenschutzverlust-Abrechnungs-Dashboards Alarm schlagen, wenn die kumulative ε die Richtliniengrenzen überschreitet.
 #11.3.2    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Black-Box-Datenschutzprüfungen ε̂ auf innerhalb von 10 % des angegebenen Werts schätzen.
 #11.3.3    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen und Einbettungen nach dem Training abdecken.

---

### 11.4 Zweckbeschränkung und Schutz vor Umfangserweiterung

 #11.4.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass jeder Datensatz und jeder Modell-Checkpoint einen maschinenlesbaren Zweck-Tag trägt, der mit der ursprünglichen Zustimmung übereinstimmt.
 #11.4.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Laufzeitmonitore Abfragen erkennen, die mit dem angegebenen Zweck unvereinbar sind, und eine sanfte Ablehnung auslösen.
 #11.4.3    Niveau: 3    Rolle: D
 Überprüfen Sie, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.
 #11.4.4    Niveau: 3    Rolle: V
 Überprüfen Sie, dass formale Rückverfolgbarkeitsnachweise zeigen, dass jeder Ablauf personenbezogener Daten innerhalb des genehmigten Rahmens bleibt.

---

### 11.5 Einwilligungsverwaltung & rechtmäßige Grundlage der Nachverfolgung

 #11.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Verwendungszweck und die Aufbewahrungsdauer pro betroffener Person erfasst.
 #11.5.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob APIs Konsenttokene bereitstellen; Modelle müssen den Token-Bereich vor der Inferenz validieren.
 #11.5.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungspipelines innerhalb von 24 Stunden stoppen.

---

### 11.6 Föderiertes Lernen mit Datenschutzkontrollen

 #11.6.1    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass bei Client-Updates vor der Aggregation lokal differentielle Datenschutzrauschaddition verwendet wird.
 #11.6.2    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust einzelner Kunden offenlegen.
 #11.6.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass eine vergiftungsresistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.
 #11.6.4    Niveau: 3    Rolle: V
 Überprüfen Sie, dass formale Beweise das gesamte ε-Budget mit einem Nutzungsverlust von weniger als 5 nachweisen.

---

#### Referenzen

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

## C12 Überwachung, Protokollierung und Anomalieerkennung

### Kontrollziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, eingestuft und analysiert werden können.

### C12.1 Anforderungs- und Antwortprotokollierung

 #12.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit den entsprechenden Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).
 #12.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositorien mit geeigneten Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.
 #12.1.3    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Log-Speichersysteme eine Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um vertrauliche Informationen in den Logs zu schützen.
 #12.1.4    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben automatisch vor der Protokollierung geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen.
 #12.1.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfiltermaßnahmen mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Content-Moderationssystemen zu ermöglichen.
 #12.1.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der Protokolle z. B. durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.

---

### C12.2 Missbrauchserkennung und Alarmierung

 #12.2.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Versuche der Prompt-Injektion und adversariale Eingaben mithilfe einer signaturbasierten Erkennung erkennt und meldet.
 #12.2.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob das System mit vorhandenen Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert ist.
 #12.2.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass angereicherte Sicherheitsereignisse KI-spezifischen Kontext wie Modell-Identifikatoren, Vertrauenswerte und Entscheidungen von Sicherheitsfiltern enthalten.
 #12.2.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abfrageverhalten identifiziert.
 #12.2.5    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Benachrichtigungsmechanismen die Sicherheitsteams informieren, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.
 #12.2.6    Niveau: 2    Rolle: D/V
 Verifizieren Sie, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modell-Extraktionsangriffe.
 #12.2.7    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass automatisierte Incident-Response-Workflows kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.

---

### C12.3 Modellverschiebungserkennung

 #12.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenzzeiten und Fehlerquoten über Modellversionen und Zeiträume hinweg verfolgt.
 #12.3.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder erheblich von den Baselines abweichen.
 #12.3.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Halluzinationsdetektionsmonitore Instanzen erkennen und kennzeichnen, wenn Modell-Ausgaben faktisch inkorrekte, inkonsistente oder erfundene Informationen enthalten.

---

### C12.4 Leistungs- und Verhaltens-Telemetrie

 #12.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Betriebsmetriken wie Anforderungsverzögerung, Token-Verbrauch, Speicherverbrauch und Durchsatz kontinuierlich erfasst und überwacht werden.
 #12.4.2    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Erfolgs- und Fehlerraten mit Kategorisierung der Fehlertypen und deren Ursachen nachverfolgt werden.
 #12.4.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Überwachung der Ressourcennutzung die GPU-/CPU-Auslastung, den Speicherverbrauch und die Speicheranforderungen umfasst und ob bei Überschreitung von Schwellenwerten eine Alarmierung erfolgt.

---

### C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

 #12.5.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Vorfallreaktionspläne speziell auf KI-bezogene Sicherheitsereignisse eingehen, einschließlich Modellkompromittierung, Datenvergiftung und adversarialen Angriffen.
 #12.5.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Vorfallreaktionsteams Zugang zu KI-spezifischen forensischen Werkzeugen und Fachwissen haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.
 #12.5.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass die Analyse nach dem Vorfall Überlegungen zur Nachtrainierung des Modells, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst.

---

### C12.5 Erkennung der Leistungsverschlechterung von KI

Überwachen und Erkennen von Verschlechterungen der Leistung und Qualität eines KI-Modells im Laufe der Zeit.

 #12.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, dass die Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.
 #12.5.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Erkennung von Datenverschiebungen Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.
 #12.5.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob die Konzeptverschiebungserkennung Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.
 #12.5.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass Leistungsabfälle automatisierte Warnungen auslösen und Workflows für die Modellneuschulung oder -ersetzung starten.
 #12.5.5    Niveau: 3    Rolle: V
 Verifizieren Sie, dass die Ursachenanalyse für Leistungsabfälle Leistungsverschlechterungen mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.

---

### C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie System zur Visualisierung von Arbeitsabläufen vor Informationslecks und Manipulationsangriffen.

 #12.6.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Visualisierungsdaten des DAG bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.
 #12.6.2    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Zugriffskontrollen für die Workflow-Visualisierung sicherstellen, dass nur autorisierte Benutzer die Entscheidungswege der Agenten und die Nachvollziehbarkeit der Entscheidungsprozesse einsehen können.
 #12.6.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermethoden geschützt ist.
 #12.6.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.
 #12.6.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen mengenbegrenzten und validierten werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.

---

### C12.7 Proaktive Überwachung des Sicherheitsverhaltens

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

 #12.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit Integration der Risikobewertung sicherheitsvalidiert werden.
 #12.7.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob selbstständige Initiativen die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.
 #12.7.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.
 #12.7.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfpfaden erfordern.
 #12.7.5    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hinweisen könnten.

---

### Referenzen

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menschliche Aufsicht, Verantwortlichkeit und Governance

### Kontrollziel

Dieses Kapitel enthält Anforderungen zur Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen und gewährleistet Erklärbarkeit, Transparenz und ethische Verantwortung während des gesamten KI-Lebenszyklus.

---

### C13.1 Not-Aus-Schalter & Übersteuerungsmechanismen

Stellen Sie bei Beobachtung eines unsicheren Verhaltens des KI-Systems Abschalt- oder Rückrollpfade bereit.

 #13.1.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob ein manueller Not-Aus-Mechanismus vorhanden ist, um die KI-Modell-Inferenz und Ausgaben sofort zu stoppen.
 #13.1.2    Niveau: 1    Rolle: D
 Überprüfen Sie, dass Override-Kontrollen nur für autorisiertes Personal zugänglich sind.
 #13.1.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Rücksetzverfahren auf vorherige Modellversionen oder den sicheren Betriebsmodus zurückkehren können.
 #13.1.4    Niveau: 3    Rolle: V
 Stellen Sie sicher, dass Übersteuerungsmechanismen regelmäßig getestet werden.

---

### C13.2 Mensch-in-der-Schleife Entscheidungs-Kontrollpunkte

Erfordern Sie menschliche Genehmigungen, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

 #13.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.
 #13.2.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass Risikoschwellenwerte klar definiert sind und automatisch menschliche Überprüfungsarbeitsabläufe auslösen.
 #13.2.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass zeitkritische Entscheidungen Ausweichverfahren haben, wenn eine menschliche Genehmigung nicht innerhalb der erforderlichen Zeitrahmen eingeholt werden kann.
 #13.2.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, sofern zutreffend.

---

### C13.3 Verantwortlichkeitskette & Prüfbarkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

 #13.3.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden.
 #13.3.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Prüfprotokolle nicht manipuliert werden können und Integritätsüberprüfungsmechanismen enthalten.

---

### C13.4 Erklärbare KI-Techniken

Oberflächenmerkmalbedeutung, kontrafaktische Analysen und lokale Erklärungen.

 #13.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in menschenlesbarem Format liefern.
 #13.4.2    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass die Qualität der Erklärung durch menschliche Evaluationsstudien und Metriken validiert wird.
 #13.4.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Wichtigkeitsscores für Merkmale oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.
 #13.4.4    Niveau: 3    Rolle: V
 Überprüfen Sie, ob kontrafaktische Erklärungen aufzeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, sofern dies für den Anwendungsfall und die Domäne zutrifft.

---

### C13.5 Modellkarten & Nutzungsangaben

Pflegen Sie Modellkarten für den beabsichtigten Gebrauch, Leistungskennzahlen und ethische Überlegungen.

 #13.5.1    Niveau: 1    Rolle: D
 Überprüfen Sie, ob Modellkarten die vorgesehenen Anwendungsfälle, Einschränkungen und bekannte Ausfallmodi dokumentieren.
 #13.5.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.
 #13.5.3    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Trainingsdatenbeschränkungen dokumentiert und regelmäßig aktualisiert werden.
 #13.5.4    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.

---

### C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwerte oder Entropiemessungen in den Antworten.

 #13.6.1    Niveau: 1    Rolle: D
 Verifizieren Sie, dass KI-Systeme ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.
 #13.6.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.
 #13.6.3    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Methoden zur Unsicherheitsquantifizierung kalibriert sind und anhand von Ground-Truth-Daten validiert wurden.
 #13.6.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Unsicherheitsfortpflanzung in mehrstufigen KI-Workflows beibehalten wird.

---

### C13.7 Transparenzberichte für Benutzer

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Abweichungen und Datennutzung bereit.

 #13.7.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Verfahren zum Management der Benutzerzustimmung den Beteiligten klar kommuniziert werden.
 #13.7.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in die Berichterstattung aufgenommen werden.
 #13.7.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessenem Detailgrad offenlegen.

#### Referenzen

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

Adversariales Beispiel: Eine absichtlich gestaltete Eingabe, die ein KI-Modell dazu bringt, einen Fehler zu machen, oft durch Hinzufügen subtiler Störungen, die für Menschen nicht wahrnehmbar sind.
​
Adversarielle Robustheit – Adversarielle Robustheit in der KI bezieht sich auf die Fähigkeit eines Modells, seine Leistung aufrechtzuerhalten und sich gegen absichtlich gestaltete, bösartige Eingaben zu wehren, die dazu dienen, Fehler zu verursachen oder es zu täuschen.
​
Agent – KI-Agenten sind Softwaresysteme, die KI verwenden, um Ziele zu verfolgen und Aufgaben im Auftrag von Benutzern zu erfüllen. Sie zeigen Fähigkeiten im Bereich des Denkens, der Planung und des Gedächtnisses und besitzen ein gewisses Maß an Autonomie, um Entscheidungen zu treffen, zu lernen und sich anzupassen.
​
Agentische KI: KI-Systeme, die mit einem gewissen Grad an Autonomie agieren können, um Ziele zu erreichen, häufig Entscheidungen treffen und Maßnahmen ergreifen, ohne direkte menschliche Intervention.
​
Attributbasierte Zugriffskontrolle (ABAC): Ein Zugriffssteuerungsparadigma, bei dem Autorisierungsentscheidungen auf Attributen des Benutzers, der Ressource, der Aktion und der Umgebung basieren, die zur Abfragezeit bewertet werden.
​
Backdoor-Angriff: Eine Art von Datenvergiftungsangriff, bei dem das Modell darauf trainiert wird, auf bestimmte Auslöser in einer bestimmten Weise zu reagieren, während es sich sonst normal verhält.
​
Bias: Systematische Fehler in den Ausgaben von KI-Modellen, die zu unfairen oder diskriminierenden Ergebnissen für bestimmte Gruppen oder in speziellen Kontexten führen können.
​
Bias-Ausnutzung: Eine Angriffsstrategie, die bekannte Verzerrungen in KI-Modellen ausnutzt, um Ausgaben oder Ergebnisse zu manipulieren.
​
Cedar: Amazons Richtliniensprache und Engine für fein abgestufte Berechtigungen, die bei der Implementierung von ABAC für KI-Systeme verwendet wird.
​
Chain of Thought: Eine Technik zur Verbesserung des Denkprozesses in Sprachmodellen durch Generierung von Zwischenschritten des Denkens vor der Ausgabe einer endgültigen Antwort.
​
Circuit Breaker: Mechanismen, die den Betrieb von KI-Systemen automatisch stoppen, wenn bestimmte Risikoschwellen überschritten werden.
​
Datenleck: Unbeabsichtigte Offenlegung sensibler Informationen durch Ausgaben oder Verhalten von KI-Modellen.
​
Datenvergiftung: Die absichtliche Korruption von Trainingsdaten, um die Integrität des Modells zu beeinträchtigen, häufig um Hintertüren zu installieren oder die Leistung zu verschlechtern.
​
Differential Privacy – Differential Privacy ist ein mathematisch rigoroser Rahmen zur Veröffentlichung statistischer Informationen über Datensätze, wobei der Datenschutz einzelner Datenpersonen geschützt wird. Es ermöglicht einem Datenhalter, aggregierte Muster der Gruppe zu teilen und gleichzeitig die Informationsweitergabe über spezifische Individuen zu begrenzen.
​
Einbettungen: Dichte Vektor-Darstellungen von Daten (Text, Bilder usw.), die semantische Bedeutung in einem hochdimensionalen Raum erfassen.
​
Erklärbarkeit – Erklärbarkeit in der KI ist die Fähigkeit eines KI-Systems, menschlich verständliche Gründe für seine Entscheidungen und Vorhersagen zu liefern und Einblicke in seine internen Abläufe zu geben.
​
Erklärbare KI (XAI): KI-Systeme, die entwickelt wurden, um durch verschiedene Techniken und Rahmenwerke menschenverständliche Erklärungen für ihre Entscheidungen und Verhaltensweisen zu liefern.
​
Federated Learning: Ein maschinelles Lernverfahren, bei dem Modelle über mehrere dezentralisierte Geräte hinweg trainiert werden, die lokale Datensätze besitzen, ohne dass die Daten selbst ausgetauscht werden.
​
Leitplanken: Einschränkungen, die implementiert werden, um zu verhindern, dass KI-Systeme schädliche, voreingenommene oder anderweitig unerwünschte Ausgaben erzeugen.
​
Halluzination – Eine AI-Halluzination bezieht sich auf ein Phänomen, bei dem ein AI-Modell falsche oder irreführende Informationen generiert, die nicht auf seinen Trainingsdaten oder der tatsächlichen Realität basieren.
​
Human-in-the-Loop (HITL): Systeme, die so konzipiert sind, dass sie menschliche Aufsicht, Verifizierung oder Eingriffe an entscheidenden Entscheidungspunkten erfordern.
​
Infrastructure as Code (IaC): Verwaltung und Bereitstellung von Infrastruktur durch Code anstelle manueller Prozesse, wodurch Sicherheitsscans und konsistente Bereitstellungen ermöglicht werden.
​
Jailbreak: Techniken, die verwendet werden, um Sicherheitsmaßnahmen in KI-Systemen, insbesondere in großen Sprachmodellen, zu umgehen, um verbotenes Material zu erzeugen.
​
Minimalberechtigung: Das Sicherheitsprinzip, nur die unbedingt notwendigen Zugriffsrechte für Benutzer und Prozesse zu gewähren.
​
LIME (Local Interpretable Model-agnostic Explanations): Eine Technik zur Erklärung der Vorhersagen eines beliebigen Machine-Learning-Klassifikators, indem dieser lokal mit einem interpretierbaren Modell approximiert wird.
​
Membership Inference Attack: Ein Angriff, der darauf abzielt festzustellen, ob ein bestimmter Datenpunkt zum Training eines maschinellen Lernmodells verwendet wurde.
​
MITRE ATLAS: Adversarielle Bedrohungslandschaft für künstliche Intelligenzsysteme; eine Wissensdatenbank adversarieller Taktiken und Techniken gegen KI-Systeme.
​
Modellkarte – Eine Modellkarte ist ein Dokument, das standardisierte Informationen über die Leistung, Einschränkungen, beabsichtigte Anwendungen und ethische Überlegungen eines KI-Modells bereitstellt, um Transparenz und verantwortungsbewusste KI-Entwicklung zu fördern.
​
Modell-Extraktion: Ein Angriff, bei dem ein Angreifer ein Zielmodell wiederholt abfragt, um ohne Autorisierung eine funktional ähnliche Kopie zu erstellen.
​
Modellinversion: Ein Angriff, der versucht, Trainingsdaten durch Analyse von Modellausgaben zu rekonstruieren.
​
Modelllebenszyklusverwaltung – Die Verwaltung des Lebenszyklus von KI-Modellen ist der Prozess der Überwachung aller Phasen der Existenz eines KI-Modells, einschließlich dessen Gestaltung, Entwicklung, Implementierung, Überwachung, Wartung und eventualer Außerbetriebnahme, um sicherzustellen, dass es effektiv bleibt und mit den Zielen übereinstimmt.
​
Modellvergiftung: Einführung von Schwachstellen oder Hintertüren direkt in ein Modell während des Trainingsprozesses.
​
Modellraub/Diebstahl: Das Extrahieren einer Kopie oder Annäherung eines proprietären Modells durch wiederholte Anfragen.
​
Multi-Agenten-System: Ein System, das aus mehreren interagierenden KI-Agenten besteht, von denen jeder potenziell unterschiedliche Fähigkeiten und Ziele hat.
​
OPA (Open Policy Agent): Eine Open-Source-Richtlinien-Engine, die eine einheitliche Durchsetzung von Richtlinien über den gesamten Stack ermöglicht.
​
Datenschutzwahrendes maschinelles Lernen (PPML): Techniken und Methoden zum Trainieren und Bereitstellen von ML-Modellen unter Wahrung der Privatsphäre der Trainingsdaten.
​
Prompt Injection: Ein Angriff, bei dem bösartige Anweisungen in Eingaben eingebettet werden, um das beabsichtigte Verhalten eines Modells zu überschreiben.
​
RAG (Retrieval-Augmented Generation): Eine Technik, die große Sprachmodelle verbessert, indem sie vor der Generierung einer Antwort relevante Informationen aus externen Wissensquellen abruft.
​
Red-Teaming: Die Praxis, KI-Systeme aktiv zu testen, indem adversariale Angriffe simuliert werden, um Schwachstellen zu identifizieren.
​
SBOM (Software Bill of Materials): Eine formelle Aufzeichnung, die die Details und Lieferkettenbeziehungen verschiedener Komponenten enthält, die beim Erstellen von Software oder KI-Modellen verwendet werden.
​
SHAP (SHapley Additive Erklärungen): Ein spieltheoretischer Ansatz zur Erklärung der Ausgabe eines beliebigen Machine-Learning-Modells durch Berechnung des Beitrags jeder Eigenschaft zur Vorhersage.
​
Lieferkettenangriff: Kompromittierung eines Systems durch gezielten Angriff auf weniger sichere Elemente in seiner Lieferkette, wie Drittanbieter-Bibliotheken, Datensätze oder vortrainierte Modelle.
​
Transfer Learning: Eine Technik, bei der ein für eine Aufgabe entwickeltes Modell als Ausgangspunkt für ein Modell einer zweiten Aufgabe wiederverwendet wird.
​
Vektordatenbank: Eine spezialisierte Datenbank, die dafür entwickelt wurde, hochdimensionale Vektoren (Embeddings) zu speichern und effiziente Ähnlichkeitssuchen durchzuführen.
​
Schwachstellenscanning: Automatisierte Werkzeuge, die bekannte Sicherheitslücken in Softwarekomponenten, einschließlich KI-Frameworks und Abhängigkeiten, identifizieren.
​
Wasserzeichen: Techniken zum Einbetten von für das menschliche Auge nicht wahrnehmbaren Markierungen in KI-generierte Inhalte, um deren Ursprung zu verfolgen oder KI-Generierung zu erkennen.
​
Zero-Day-Schwachstelle: Eine zuvor unbekannte Schwachstelle, die Angreifer ausnutzen können, bevor Entwickler einen Fix erstellen und bereitstellen.

## Anhang B: Referenzen

### TODO

## Anhang C: KI-Sicherheits-Governance & Dokumentation

### Zielsetzung

Dieser Anhang enthält grundlegende Anforderungen zur Einrichtung organisatorischer Strukturen, Richtlinien und Prozesse zur Steuerung der AI-Sicherheit während des gesamten Systemlebenszyklus.

---

### AC.1 Annahme des AI-Risikomanagementrahmens

Stellen Sie ein formelles Rahmenwerk bereit, um KI-spezifische Risiken während des gesamten Systemlebenszyklus zu identifizieren, zu bewerten und zu mindern.

 #AC.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass eine auf KI spezialisierte Risikobewertungsmethodik dokumentiert und implementiert ist.
 #AC.1.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Risikoanalysen an wichtigen Punkten im KI-Lebenszyklus und vor wesentlichen Änderungen durchgeführt werden.
 #AC.1.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob der Risikomanagementrahmen mit etablierten Standards (z. B. NIST AI RMF) übereinstimmt.

---

### AC.2 KI-Sicherheitsrichtlinie & -verfahren

Definieren und Durchsetzen organisatorischer Standards für die sichere Entwicklung, Bereitstellung und den Betrieb von KI.

 #AC.2.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob dokumentierte KI-Sicherheitsrichtlinien vorliegen.
 #AC.2.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Richtlinien mindestens jährlich und nach erheblichen Veränderungen der Bedrohungslandschaft überprüft und aktualisiert werden.
 #AC.2.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Richtlinien alle AISVS-Kategorien und anwendbaren regulatorischen Anforderungen abdecken.

---

### AC.3 Rollen und Verantwortlichkeiten für AI-Sicherheit

Schaffen Sie klare Verantwortlichkeiten für die KI-Sicherheit in der gesamten Organisation.

 #AC.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Sicherheitsrollen und -verantwortlichkeiten von KI dokumentiert sind.
 #AC.3.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass verantwortliche Personen über die entsprechende Sicherheitsexpertise verfügen.
 #AC.3.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass ein KI-Ethikkomitee oder ein Governance-Gremium für Hochrisiko-KI-Systeme eingerichtet wird.

---

### AC.4 Durchsetzung ethischer KI-Richtlinien

Sicherstellen, dass KI-Systeme gemäß den etablierten ethischen Grundsätzen arbeiten.

 #AC.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass ethische Richtlinien für die Entwicklung und den Einsatz von KI vorhanden sind.
 #AC.4.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um ethische Verstöße zu erkennen und zu melden.
 #AC.4.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass regelmäßige ethische Überprüfungen der eingesetzten KI-Systeme durchgeführt werden.

---

### AC.5 Überwachung der Einhaltung von KI-Vorschriften

Behalten Sie das Bewusstsein für und die Einhaltung der sich entwickelnden KI-Vorschriften bei.

 #AC.5.1    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass Prozesse vorhanden sind, um anwendbare KI-Vorschriften zu identifizieren.
 #AC.5.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass die Einhaltung aller regulatorischen Anforderungen bewertet wird.
 #AC.5.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass regulatorische Änderungen rechtzeitige Überprüfungen und Aktualisierungen von KI-Systemen auslösen.

### AC.6 Training-Datengovernance, Dokumentation und Prozess

 #1.1.2    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass nur Datensätze verwendet werden, die bezüglich Qualität, Repräsentativität, ethischer Beschaffung und Lizenzkonformität überprüft wurden, um Risiken wie Vergiftung, eingebettete Verzerrungen und Verletzungen geistigen Eigentums zu reduzieren.
 #1.1.5    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch gegenseitige Überprüfungen oder Konsens der Prüfer gewährleistet ist.
 #1.1.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass für bedeutende Trainingsdatensätze "Datenkarten" oder "Datenblätter für Datensätze" geführt werden, in denen Merkmale, Ziele, Zusammensetzung, Erhebungsprozesse, Vorverarbeitung sowie empfohlene und abzuratende Verwendungszwecke detailliert beschrieben sind.
 #1.3.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass identifizierte Verzerrungen durch dokumentierte Strategien wie Ausgleich, gezielte Datenaugmentation, algorithmische Anpassungen (z. B. Pre-Processing-, In-Processing- und Post-Processing-Techniken) oder Neugewichtung gemindert werden und die Auswirkungen der Minderung sowohl auf die Fairness als auch auf die Gesamtleistung des Modells bewertet werden.
 #1.3.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass nach dem Training Fairness-Metriken bewertet und dokumentiert werden.
 #1.3.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob eine Lifecycle-Bias-Management-Richtlinie Verantwortliche und Überprüfungsintervall festlegt.
 #1.4.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch klare Richtlinien, gegenseitige Überprüfungen durch Gutachter, Konsensmechanismen (z. B. Überwachung der Übereinstimmung zwischen Annotatoren) und definierte Prozesse zur Behebung von Abweichungen gewährleistet ist.
 #1.4.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Kennzeichnungen, die für Sicherheit, Schutz oder Fairness entscheidend sind (z. B. die Identifizierung von toxischen Inhalten, kritischen medizinischen Befunden), einer obligatorischen unabhängigen doppelten Überprüfung oder einer gleichwertigen robusten Verifizierung unterzogen werden.
 #1.4.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Beschriftungsrichtlinien und Anweisungen umfassend, versionskontrolliert und von Kollegen überprüft sind.
 #1.4.6    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Datenschemata für Labels klar definiert und versionskontrolliert sind.
 #1.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Datensätze auf repräsentative Ungleichgewichte und potenzielle Verzerrungen hinsichtlich rechtlich geschützter Merkmale (z. B. Rasse, Geschlecht, Alter) sowie anderer ethisch sensibler Merkmale überprüft werden, die für den Anwendungsbereich des Modells relevant sind (z. B. sozioökonomischer Status, Standort).
 #1.5.3    Niveau: 2    Rolle: V
 Stellen Sie sicher, dass manuelle Stichprobenprüfungen durch Fachexperten eine statistisch signifikante Stichprobe abdecken (z. B. ≥1 % oder 1.000 Proben, je nachdem, welcher Wert höher ist, oder wie durch die Risikoanalyse festgelegt), um subtile Qualitätsprobleme zu identifizieren, die von der Automatisierung nicht erfasst werden.
 #1.8.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass ausgelagerte oder Crowdsourcing-Kennzeichnungs-Workflows technische/prozedurale Schutzmaßnahmen enthalten, um die Vertraulichkeit der Daten, die Integrität, die Qualität der Kennzeichnungen sicherzustellen und einen Datenverlust zu verhindern.
 #1.5.4    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Behebungsschritte an die Herkunftsdatensätze angehängt werden.
 #1.6.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass markierte Proben vor dem Training eine manuelle Überprüfung auslösen.
 #1.6.3    Niveau: 2    Rolle: V
 Verifizieren Sie, dass die Ergebnisse das Sicherheitsdossier des Modells speisen und die fortlaufende Bedrohungsaufklärung informieren.
 #1.6.4    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob die Erkennungslogik mit neuen Bedrohungsinformationen aktualisiert wird.
 #1.6.5    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Online-Lernpipelines die Verteilungsschwankung überwachen.
 #1.7.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die Workflows zur Löschung von Trainingsdaten sowohl primäre als auch abgeleitete Daten löschen und den Modelleffekt bewerten, und dass der Einfluss auf die betroffenen Modelle bewertet und gegebenenfalls behoben wird (z. B. durch erneutes Training oder Neukalibrierung).
 #1.7.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um den Umfang und den Status der Zustimmung der Nutzer (einschließlich Widerrufe) für Daten, die im Training verwendet werden, zu verfolgen und zu respektieren, und dass die Zustimmung validiert wird, bevor Daten in neue Trainingsprozesse oder bedeutende Modellaktualisierungen einbezogen werden.
 #1.7.3    Niveau: 2    Rolle: V
 Überprüfen Sie, ob Workflows jährlich getestet und protokolliert werden.
 #1.8.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Drittanbieterdatenlieferanten, einschließlich Anbieter von vortrainierten Modellen und externen Datensätzen, vor der Integration ihrer Daten oder Modelle einer Sicherheits-, Datenschutz-, ethischen Beschaffungs- und Datenqualitätsprüfung unterzogen werden.
 #1.8.2    Niveau: 1    Rolle: D
 Stellen Sie sicher, dass externe Übertragungen TLS/Authentifizierung und Integritätsprüfungen verwenden.
 #1.8.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Datenquellen mit hohem Risiko (z. B. Open-Source-Datensätze mit unbekannter Herkunft, nicht geprüfte Anbieter) vor der Verwendung in sensiblen Anwendungen verstärkt geprüft werden, beispielsweise durch isolierte Analysen, umfangreiche Qualitäts- und Bias-Checks sowie gezielte Erkennung von Datenmanipulation.
 #1.8.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass vor dem Finetuning oder der Bereitstellung vortrainierte Modelle, die von Dritten stammen, auf eingebettete Verzerrungen, potenzielle Hintertüren, die Integrität ihrer Architektur und die Herkunft ihrer ursprünglichen Trainingsdaten bewertet werden.
 #1.5.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob bei Verwendung von adversarialem Training die Erstellung, Verwaltung und Versionierung von adversarialen Datensätzen dokumentiert und kontrolliert wird.
 #1.5.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass die Auswirkung des Trainings zur adversarialen Robustheit auf die Modellleistung (sowohl bei sauberen als auch bei adversarialen Eingaben) und auf Fairness-Metriken bewertet, dokumentiert und überwacht wird.
 #1.5.4    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Strategien für adversariales Training und Robustheit regelmäßig überprüft und aktualisiert werden, um sich entwickelnden adversarialen Angriffstechniken entgegenzuwirken.
 #1.4.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, dass fehlgeschlagene Datensätze mit Prüfpfaden isoliert werden.
 #1.4.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Qualitätsprüfungen minderwertige Datensätze blockieren, es sei denn, Ausnahmen werden genehmigt.
 #1.11.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass der Generierungsprozess, die Parameter und die beabsichtigte Verwendung der synthetischen Daten dokumentiert sind.
 #1.11.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass synthetische Daten vor der Verwendung im Training auf Bias, Datenschutzverletzungen und Repräsentationsprobleme einer Risikoabschätzung unterzogen werden.
 #1.12.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Warnmeldungen für verdächtige Zugriffsereignisse generiert und umgehend untersucht werden.
 #1.13.1    Niveau: 1    Rolle: D/V
 Verifizieren Sie, dass für alle Trainingsdatensätze explizite Aufbewahrungsfristen festgelegt sind.
 #1.13.2    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Datensätze am Ende ihres Lebenszyklus automatisch ablaufen, gelöscht oder zur Löschung überprüft werden.
 #1.13.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Aufbewahrungs- und Löschaktionen protokolliert und überprüfbar sind.
 #1.14.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Anforderungen an die Datenresidenz und den grenzüberschreitenden Datentransfer für alle Datensätze identifiziert und durchgesetzt werden.
 #1.14.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass branchenspezifische Vorschriften (z. B. Gesundheitswesen, Finanzen) bei der Datenverarbeitung identifiziert und berücksichtigt werden.
 #1.14.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung relevanter Datenschutzgesetze (z. B. DSGVO, CCPA) dokumentiert und regelmäßig überprüft wird.
 #1.16.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um auf Anfragen von betroffenen Personen bezüglich Zugang, Berichtigung, Einschränkung oder Widerspruch zu reagieren.
 #1.16.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Anfragen innerhalb der gesetzlich vorgeschriebenen Fristen protokolliert, nachverfolgt und erfüllt werden.
 #1.16.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Prozesse zu den Rechten der betroffenen Personen regelmäßig auf ihre Wirksamkeit getestet und überprüft werden.
 #1.17.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass eine Auswirkungsanalyse durchgeführt wird, bevor eine Datensatzversion aktualisiert oder ersetzt wird, die Modellleistung, Fairness und Compliance abdeckt.
 #1.17.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Auswirkungsanalyse dokumentiert und von den relevanten Stakeholdern überprüft werden.
 #1.17.3    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass Rollback-Pläne existieren, falls neue Versionen unakzeptable Risiken oder Rückschritte einführen.
 #1.18.1    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass alle am Datenannotieren beteiligten Personen eine Hintergrundüberprüfung durchlaufen haben und in Datensicherheit sowie Datenschutz geschult sind.
 #1.18.2    Niveau: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Annotationsmitarbeiter Vertraulichkeits- und Geheimhaltungsvereinbarungen unterzeichnen.
 #1.18.3    Niveau: 2    Rolle: D/V
 Überprüfen Sie, ob Annotationsplattformen Zugriffskontrollen durchsetzen und Insider-Bedrohungen überwachen.

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anhang D: KI-gestützte Governance und Verifizierung sicherer Codierung

### Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-gestützten Codierwerkzeugen während der Softwareentwicklung und gewährleistet Sicherheit und Rückverfolgbarkeit über den gesamten SDLC.

---

### AD.1 KI-unterstützter Secure-Coding-Workflow

Integrieren Sie KI-Tools in den sicheren Software-Entwicklungszyklus (SSDLC) der Organisation, ohne die bestehenden Sicherheitsschranken zu schwächen.

 #AD.1.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass ein dokumentierter Arbeitsablauf beschreibt, wann und wie KI-Tools Code erzeugen, überarbeiten oder überprüfen dürfen.
 #AD.1.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob der Arbeitsablauf jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).
 #AD.1.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, ob Metriken (z. B. Verwundbarkeitsdichte, mittlere Zeit bis zur Erkennung) für KI-generierten Code erfasst und mit rein menschlichen Basiswerten verglichen werden.

---

### AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung hinsichtlich Sicherheitsfähigkeiten, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

 #AD.2.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Tool Missbrauch, Modell-Inversion, Datenleckage und Risiken in der Abhängigkeitskette identifiziert.
 #AD.2.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass die Bewertung der Tools eine statische/dynamische Analyse aller lokalen Komponenten sowie eine Bewertung der SaaS-Endpunkte (TLS, Authentifizierung/Autorisierung, Protokollierung) umfasst.
 #AD.2.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.

---

### AD.3 Sichere Verwaltung von Eingabeaufforderungen und Kontext

Verhindern Sie das Leaken von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Eingabeaufforderungen oder Kontexten für KI-Modelle.

 #AD.3.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob die schriftlichen Richtlinien das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen untersagen.
 #AD.3.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob technische Kontrollen (Client-seitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.
 #AD.3.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen den Datenklassifizierungsrichtlinien entsprechen.

---

### AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch AI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

 #AD.4.1    Niveau: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.
 #AD.4.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Ergebnissen blockieren.
 #AD.4.3    Niveau: 3    Rolle: D/V
 Überprüfen Sie, dass differentialer Fuzz-Testing oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen nachweisen (z. B. Eingabevalidierung, Autorisierungslogik).

---

### AD.5 Erklärbarkeit und Nachverfolgbarkeit von Code-Vorschlägen

Bieten Sie Prüfern und Entwicklern Einblick darin, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

 #AD.5.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Eingabeaufforderungs-/Antwortpaare mit Commit-IDs protokolliert werden.
 #AD.5.2    Niveau: 2    Rolle: D
 Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Empfehlung unterstützen.
 #AD.5.3    Niveau: 3    Rolle: D/V
 Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Design-Artefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien der ISO/IEC 42001 zu erfüllen.

---

### AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie dabei Leistungsverschlechterungen.

 #AD.6.1    Niveau: 1    Rolle: D/V
 Überprüfen Sie, ob Entwickler unsichere oder nicht konforme Vorschläge markieren können und ob diese Markierungen nachverfolgt werden.
 #AD.6.2    Niveau: 2    Rolle: D
 Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder die retrieval-ergänzte Generierung mit geprüften, sicherheitsorientierten Programmier-Korpora (z. B. OWASP Cheat Sheets) informiert.
 #AD.6.3    Niveau: 3    Rolle: D/V
 Verifizieren Sie, dass ein Closed-Loop-Evaluierungs-Framework nach jedem Fine-Tuning Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung die vorherigen Baselines erreichen oder übertreffen.

---

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Anhang E: Beispielwerkzeuge und -frameworks

### Zielsetzung

Dieses Kapitel liefert Beispiele für Tools und Frameworks, die die Umsetzung oder Erfüllung einer bestimmten AISVS-Anforderung unterstützen können. Diese sind nicht als Empfehlungen oder Befürwortungen durch das AISVS-Team oder das OWASP GenAI Security Project zu verstehen.

---

### AE.1 Trainingsdaten-Governance & Bias-Management

Werkzeuge für Datenanalyse, Governance und Bias-Management.

 #AE.1.1    Abschnitt: 1.1
 Werkzeuge zur Dateninventarisierung: Werkzeuge zur Verwaltung des Dateninventars wie...
 #AE.1.2    Abschnitt: 1.2
 Verschlüsselung während der Übertragung Verwenden Sie TLS für HTTPS-basierte Anwendungen, mit Werkzeugen wie openSSL und Pythons`ssl`Bibliothek.

---

### AE.2 Benutzer-Eingabevalidierung

Werkzeuge zur Verarbeitung und Validierung von Benutzereingaben.

 #AE.2.1    Abschnitt: 2.1
 Werkzeuge zur Verteidigung gegen Prompt Injection: Verwenden Sie Schutzwerkzeuge wie NVIDIAs NeMo oder Guardrails AI.

---

