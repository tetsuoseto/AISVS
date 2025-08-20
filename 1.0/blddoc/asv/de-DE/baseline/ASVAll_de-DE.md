## Vorsatzblatt

### Über den Standard

Der Artificial Intelligence Security Verification Standard (AISVS) ist ein gemeinschaftlich entwickelter Katalog von Sicherheitsanforderungen, den Data Scientists, MLOps-Ingenieure, Softwarearchitekten, Entwickler, Tester, Sicherheitsexperten, Tool-Anbieter, Regulierungsbehörden und Anwender nutzen können, um vertrauenswürdige KI-gestützte Systeme und Anwendungen zu entwerfen, zu bauen, zu testen und zu verifizieren. Er bietet eine gemeinsame Sprache zur Spezifikation von Sicherheitskontrollen über den gesamten KI-Lebenszyklus hinweg – von der Datenerhebung und Modellentwicklung bis hin zur Implementierung und kontinuierlichen Überwachung – damit Organisationen die Resilienz, den Datenschutz und die Sicherheit ihrer KI-Lösungen messen und verbessern können.

### Urheberrecht und Lizenz

Version 0.1 (Erster öffentlicher Entwurf - Arbeit in Vorbereitung), 2025  

![license](images/license.png)
Copyright © 2025 Das AISVS-Projekt.  

Veröffentlicht unter demCreative Commons Attribution‑ShareAlike 4.0 International License.
Bei jeglicher Wiederverwendung oder Verbreitung müssen Sie die Lizenzbedingungen dieses Werks klar an andere weitergeben.

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

AISVS ist ein brandneuer Standard, der speziell entwickelt wurde, um die einzigartigen Sicherheitsherausforderungen von künstlichen Intelligenzsystemen zu adressieren. Während er sich an allgemeineren Sicherheitsbest Practices orientiert, wurde jede Anforderung in AISVS von Grund auf entwickelt, um die Bedrohungslandschaft der KI widerzuspiegeln und Organisationen dabei zu helfen, sicherere und widerstandsfähigere KI-Lösungen zu entwickeln.

## Vorwort

Willkommen zum Artificial Intelligence Security Verification Standard (AISVS) Version 1.0!

### Einleitung

Die im Jahr 2025 durch eine gemeinschaftliche Zusammenarbeit gegründete AISVS definiert die Sicherheitsanforderungen, die bei der Konzeption, Entwicklung, Implementierung und dem Betrieb moderner KI-Modelle, Pipelines und KI-gestützter Dienste zu berücksichtigen sind.

AISVS v1.0 stellt die gemeinsame Arbeit seiner Projektleiter, Arbeitsgruppe und der breiteren Gemeinschaft von Mitwirkenden dar, um eine pragmatische, testbare Grundlage für die Sicherung von KI-Systemen zu schaffen.

Unser Ziel mit dieser Veröffentlichung ist es, AISVS einfach zu übernehmen, während wir gleichzeitig strikt auf dessen definierten Umfang fokussiert bleiben und die sich schnell entwickelnde Risikolandschaft, die für KI einzigartig ist, adressieren.

### Hauptziele für AISVS Version 1.0

Version 1.0 wird mit mehreren Leitprinzipien erstellt.

#### Gut definierter Umfang

Jede Anforderung muss mit dem Namen und der Mission von AISVS übereinstimmen:

Künstliche Intelligenz – Kontrollen werden auf der AI/ML-Ebene (Daten, Modell, Pipeline oder Inferenz) durchgeführt und liegen in der Verantwortung der AI-Praktiker.
Sicherheit – Anforderungen mildern direkt identifizierte Sicherheits-, Datenschutz- oder Sicherheitsrisiken.
Verifikation – Die Sprache ist so verfasst, dass die Konformität objektiv überprüft werden kann.
Standard – Abschnitte folgen einer konsistenten Struktur und Terminologie, um eine kohärente Referenz zu bilden.
​
---

Durch die Befolgung von AISVS können Organisationen die Sicherheitslage ihrer KI-Lösungen systematisch bewerten und stärken und damit eine Kultur der sicheren KI-Entwicklung fördern.

## Verwendung des AISVS

Der Artificial Intelligence Security Verification Standard (AISVS) definiert Sicherheitsanforderungen für moderne KI-Anwendungen und -Dienste und konzentriert sich dabei auf Aspekte, die im Verantwortungsbereich der Anwendungsentwickler liegen.

Der AISVS richtet sich an alle, die AI-Anwendungen entwickeln oder deren Sicherheit bewerten, einschließlich Entwickler, Architekten, Sicherheitstechniker und Prüfer. Dieses Kapitel stellt die Struktur und Verwendung des AISVS vor, einschließlich seiner Verifizierungsstufen und der vorgesehenen Anwendungsfälle.

### Sicherheitsüberprüfungsstufen für Künstliche Intelligenz

Die AISVS definiert drei aufsteigende Sicherheitsüberprüfungsstufen. Jede Stufe fügt Tiefe und Komplexität hinzu, sodass Organisationen ihre Sicherheitsstrategie an das Risikoniveau ihrer KI-Systeme anpassen können.

Organisationen können auf Stufe 1 beginnen und im Laufe der Zeit nach und nach höhere Stufen übernehmen, wenn die Sicherheitsexpertise und die Bedrohungsexponierung zunehmen.

#### Definition der Ebenen

Jede Anforderung in AISVS v1.0 wird einer der folgenden Stufen zugeordnet:

 Anforderungen der Stufe 1

Level 1 umfasst die kritischsten und grundlegendsten Sicherheitsanforderungen. Diese konzentrieren sich darauf, häufige Angriffe zu verhindern, die nicht auf weiteren Voraussetzungen oder Schwachstellen basieren. Die meisten Kontrollen auf Level 1 sind entweder einfach umzusetzen oder so essentiell, dass der Aufwand gerechtfertigt ist.

 Anforderungen der Stufe 2

Level 2 behandelt fortgeschrittenere oder weniger häufige Angriffe sowie mehrschichtige Abwehrmechanismen gegen weit verbreitete Bedrohungen. Diese Anforderungen können komplexere Logik beinhalten oder spezielle Angriffsvoraussetzungen adressieren.

 Anforderungen der Stufe 3

Level 3 umfasst Kontrollen, die typischerweise schwerer umzusetzen sind oder deren Anwendbarkeit situationsabhängig ist. Diese stellen häufig Verteidigungsmechanismen in der Tiefe oder Gegenmaßnahmen gegen spezielle, zielgerichtete oder hochkomplexe Angriffe dar.

#### Rolle (D/V)

Jede AISVS-Anforderung ist entsprechend der Hauptzielgruppe gekennzeichnet:

D – Entwicklerorientierte Anforderungen
V – Anforderungen mit Fokus auf Verifizierer/Auditoren
D/V – Relevant für sowohl Entwickler als auch Prüfer

## C1 Schulung zu Daten-Governance und Bias-Management

### Kontrollziel

Trainingsdaten müssen so beschafft, gehandhabt und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness gewahrt bleiben. Dies erfüllt rechtliche Verpflichtungen und verringert das Risiko von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinträchtigen könnten.

---

### C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

 #1.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein aktuelles Inventar aller Trainingsdatenquellen (Ursprung, Verantwortlicher/Eigentümer, Lizenz, Erfassungsmethode, Nutzungseinschränkungen und Verarbeitungshistorie) geführt wird.
 #1.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Verarbeitung der Trainingsdaten unnötige Merkmale, Attribute oder Felder ausschließt (z. B. ungenutzte Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).
 #1.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Änderungen am Datensatz einem protokollierten Genehmigungsworkflow unterliegen.
 #1.1.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Datensätze oder Teilmengen, wo möglich, mit Wasserzeichen oder Fingerabdrücken versehen sind.

---

### C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und überprüfen Sie deren Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

 #1.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Zugriffskontrollen den Speicher und die Pipelines der Trainingsdaten schützen.
 #1.2.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass sämtlicher Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeitpunkt und Aktion.
 #1.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand mit branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungspraktiken verschlüsselt sind.
 #1.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten zu gewährleisten.
 #1.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisierte Erkennungstechniken angewendet werden, um unautorisierte Änderungen oder die Beschädigung von Trainingsdaten zu verhindern.
 #1.2.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.
 #1.2.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Trainingsdatensatzversionen eindeutig identifiziert, unveränderlich gespeichert und prüfbar sind, um Rollbacks und forensische Analysen zu unterstützen.

---

### C1.3 Qualität, Integrität und Sicherheit der Trainingsdatenkennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

 #1.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, dass kryptografische Hashes oder digitale Signaturen auf Etikettenartefakte angewendet werden, um deren Integrität und Authentizität zu gewährleisten.
 #1.3.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Kennzeichnungsoberflächen und -plattformen starke Zugriffskontrollen durchsetzen, manipulationssichere Prüfprotokolle aller Kennzeichnungsaktivitäten führen und Schutz gegen unbefugte Änderungen bieten.
 #1.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch während der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.

---

### C1.4 Qualität der Trainingsdaten und Sicherheitsgarantie

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebung, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

 #1.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests Formatfehler und Nullwerte bei jedem Ingest oder jeder signifikanten Datenumwandlung erfassen.
 #1.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Vergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Embedding-Analyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Backdoor-Trigger-Einfügung, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption im Trainingsdatensatz zu identifizieren.
 #1.4.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass geeignete Abwehrmaßnahmen wie adversariales Training (unter Verwendung generierter adversarischer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und für relevante Modelle basierend auf der Risikobewertung abgestimmt sind.
 #1.4.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisch generierte Labels (z. B. über LLMs oder schwache Aufsicht) Confidenz-Schwellenwerten und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Zuverlässigkeit zu erkennen.
 #1.4.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests bei jeder Datenaufnahme oder bedeutenden Datenumwandlung Label-Verschiebungen erkennen.

---

### C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie die gesamte Reise jedes Datenpunkts von der Quelle bis zur Modelleingabe für Prüfbarkeit und Vorfallreaktion.

 #1.5.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Herkunft jedes Datenpunkts, einschließlich aller Transformationen, Erweiterungen und Zusammenführungen, aufgezeichnet wird und rekonstruiert werden kann.
 #1.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Abstammungsdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.
 #1.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Nachverfolgung der Herkunft synthetischer Daten, die durch datenschutzwahrende oder generative Techniken erzeugt wurden, abgedeckt ist und dass alle synthetischen Daten im gesamten Prozess klar gekennzeichnet und von echten Daten unterscheidbar sind.

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

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen außer Kraft setzen, sensible Daten offenlegen oder das Modell zu unerlaubtem Verhalten lenken. Sofern keine dedizierten Filter und Anweisungshierarchien vorhanden sind, zeigt die Forschung, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, wirksam sein werden. Ebenso können subtile adversariale Störangriffe – wie Homoglyph-Vertauschungen oder Leetspeak – die Entscheidungen eines Modells unbemerkt verändern.

---

### C2.1 Prompt-Injection-Abwehr

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung einer Instruktionshierarchie.

 #2.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Benutzereingaben anhand einer kontinuierlich aktualisierten Bibliothek bekannter Prompt-Injektionsmuster (Jailbreak-Stichwörter, „ignore previous“, Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.
 #2.1.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen übersteuern, auch nach Erweiterung des Kontextfensters.
 #2.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass adversariale Bewertungstests (z. B. Red Team „Many-Shot“-Prompts) vor jeder Veröffentlichung eines Modells oder einer Prompt-Vorlage durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Regressionen.
 #2.1.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Eingabeaufforderungen, die aus Inhalten Dritter stammen (Webseiten, PDFs, E-Mails), in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in die Haupt-Eingabeaufforderung zusammengeführt werden.
 #2.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifizierer-Modelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.

---

### C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (Natural Language Processing, NLP) sind weiterhin anfällig für subtile Störungen auf Zeichen- oder Wortebene, die Menschen oft übersehen, die Modelle jedoch typischerweise falsch klassifizieren.

 #2.2.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass grundlegende Eingabenormalisierungsschritte (Unicode NFC, Homoglyphen-Zuordnung, Entfernen von Leerzeichen) vor der Tokenisierung ausgeführt werden.
 #2.2.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßiger Wiederholung von Token oder abnormalen Einbettungsabständen markiert.
 #2.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die Inferenz-Pipeline optionale gegnerische Trainings-härtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für hochriskante Endpunkte unterstützt.
 #2.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass verdächtige adversariale Eingaben isoliert, mit vollständigen Nutzdaten protokolliert (nach PII-Redaktion) werden.
 #2.2.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen einen Veröffentlichungsblocker auslösen.

---

### C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überlaufen von Eingaben über Felder hinweg und Ressourcenerschöpfung verursachen. Eine strikte Schemaüberprüfung ist zudem eine Voraussetzung für die Durchführung deterministischer Werkzeugaufrufe.

 #2.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Zusammenstellung des Prompts validiert werden.
 #2.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einem sicheren Fehler abgelehnt werden und niemals stillschweigend abgeschnitten werden.
 #2.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.
 #2.3.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.
 #2.3.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Validierungsfehler mit anonymisierten Nutzlast-Ausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitsbewertung zu erleichtern.

---

### C2.4 Inhalt- und Richtlinienüberprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die verbotene Inhalte anfordern (wie etwa illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und deren Verbreitung verhindern.

 #2.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass ein Inhaltsklassifizierer (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten.
 #2.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.
 #2.4.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird, wobei neu beobachtete Jailbreak- oder Umgehungsmuster von Richtlinien einbezogen werden.
 #2.4.4    Level: 2    Rolle: D
 Überprüfen Sie, ob das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Einschränkungen) mittels attributbasierter Regeln, die zur Anfragezeit aufgelöst werden, einhält.
 #2.4.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für die SOC-Korrelation und zukünftige Red-Team-Wiederholungen enthalten.

---

### C2.5 Eingangsratebegrenzung & Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenauslastung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

 #2.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob für alle Eingabe-Endpunkte Benutzer-, IP- und API-Schlüssel-spezifische Ratenbegrenzungen durchgesetzt werden.
 #2.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Burst- und Dauerbetragsgrenzen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.
 #2.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflut) automatisierte Sperren oder Eskalationen auslösen.
 #2.5.4    Level: 3    Rolle: V
 Überprüfen Sie, ob Protokolle zur Missbrauchsverhinderung aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.

---

### C2.6 Mehrmodale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektion, Umgehung oder Ressourcenmissbrauch zu verhindern.

 #2.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format validiert werden.
 #2.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganographische Nutzlasten gescannt werden.
 #2.6.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Bild-/Audioeingaben auf adversarielle Störungen oder bekannte Angriffs-muster geprüft werden.
 #2.6.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Validierungsfehler bei multimodalen Eingaben protokolliert werden und Warnmeldungen zur Untersuchung auslösen.

---

### C2.7 Eingabeherkunft und Attribution

KI-Systeme sollten die Prüfung, die Verfolgung von Missbrauch und die Einhaltung von Vorschriften unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

 #2.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.
 #2.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und prüfbar sind.
 #2.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Überprüfung oder Sperrung unterzogen werden.

---

### C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsarten anpassen und durch kompilierte Mustererkennung Echtzeitschutz bieten.

 #2.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine hochleistungsfähige Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.
 #2.8.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Bedrohungserkennungssysteme separate Musterbibliotheken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) unterhalten.
 #2.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die adaptive Bedrohungserkennung Machine-Learning-Modelle integriert, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.
 #2.8.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Bedrohungsintelligenz-Feeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOC (Indicators of Compromise) aktualisieren.
 #2.8.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Fehlalarme der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Störungen legitimer Anwendungsfälle zu minimieren.
 #2.8.6    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die kontextbezogene Bedrohungsanalyse die Eingabequelle, Benutzerverhaltensmuster und Sitzungsverlauf berücksichtigt, um die Genauigkeit der Erkennung zu verbessern.
 #2.8.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.

---

### C2.9 Multi-modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcenisolierung bereitstellen.

 #2.9.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellen verfügt.
 #2.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit), die für jeden Modultyp spezifisch sind, verarbeitet werden und in den Sicherheitsrichtlinien dokumentiert sind.
 #2.9.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von Cross-Modal-Angriffen koordinierte Angriffe erfasst, die mehrere Eingabetypen umfassen (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektion im Text) mithilfe von Korrelationsregeln und Alarmgenerierung.
 #2.9.4    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Multi-Modal-Validierungsfehler eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsscores und Korrelationsanalysen mit strukturierten Protokollformaten zur SIEM-Integration umfasst.
 #2.9.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass modalitiespezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungskennzahlen aktualisiert werden, die über den Basisschwellenwerten liegen.

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

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Integrität des Modells über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerdienststellung – und ermöglicht eine schnelle Reaktion auf Zwischenfälle sowie die Nachvollziehbarkeit aller Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

### C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit überprüfter Integrität gelangen in Produktionsumgebungen.

 #3.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptografisch von autorisierten Stellen signiert sind.
 #3.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.
 #3.1.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Herkunftsaufzeichnungen des Modells die Identität der autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit Bestehen/Nichtbestehen-Status und einen Erstellungszeitstempel enthalten.
 #3.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte eine semantische Versionsnummerierung (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.
 #3.1.5    Level: 2    Rolle: V
 Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller Verbrauchersysteme ermöglicht.

---

### C3.2 Modellvalidierung & Test

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

 #3.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsevaluierungen mit vorab vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen.
 #3.2.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Validierungsfehler nach expliziter Überschreibungsfreigabe durch vordefinierte autorisierte Personen mit dokumentierten geschäftlichen Begründungen automatisch die Modellbereitstellung blockieren.
 #3.2.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash, der validiert wird, verknüpft sind.
 #3.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung durch eine vorab festgelegte Sicherheitsinstanz innerhalb vorab vereinbarter Zeitrahmen erfordern.

---

### C3.3 Kontrollierte Bereitstellung & Rücknahme

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

 #3.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern basierend auf vorab vereinbarten Fehlerquoten, Latenzschwellenwerten oder Sicherheitswarnkriterien implementieren.
 #3.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.
 #3.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen vor der Modellaktivierung berechnen, wobei die Bereitstellung bei jeglicher Abweichung fehlschlägt.
 #3.3.4    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Notfall-Modelabschaltfunktionen Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreisunterbrecher oder manuelle Not-Aus-Schalter deaktivieren können.
 #3.3.5    Level: 2    Rolle: V
 Stellen Sie sicher, dass Rücksetz-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.

---

### C3.4 Änderung Verantwortlichkeit & Prüfung

Alle Änderungen im Lebenszyklus des Modells müssen nachvollziehbar und prüfbar sein.

 #3.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Außerbetriebnahme) unveränderliche Audit-Protokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen ÄnderungsTyp sowie Vorher-/Nachher-Zustände enthalten.
 #3.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass für den Zugriff auf das Audit-Protokoll eine geeignete Autorisierung erforderlich ist und dass alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.
 #3.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten versionskontrolliert in Git-Repositories sind, mit verpflichtender Codeüberprüfung und Genehmigung durch festgelegte Prüfer vor der Bereitstellung.
 #3.4.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die Prüfungsprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitpunkt innerhalb des Aufbewahrungszeitraums zu ermöglichen.

---

### C3.5 Sichere Entwicklungspraktiken

Modellentwicklungs- und Trainingsprozesse müssen sichere Praktiken befolgen, um Kompromittierungen zu verhindern.

 #3.5.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Entwicklungs-, Test- und Produktionsumgebungen des Modells physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.
 #3.5.2    Level: 1    Rolle: D
 Überprüfen Sie, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang stattfinden.
 #3.5.3    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und über vertrauenswürdige Quellen mit dokumentierter Nachweiskette vor der Verwendung in der Modellentwicklung authentifiziert werden.
 #3.5.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionsverwaltung gespeichert werden und eine Genehmigung durch die Peer-Review erforderlich ist, bevor sie im Training verwendet werden.

---

### C3.6 Modellstilllegung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme erkannt werden.

 #3.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Modellstilllegungsprozesse automatisch Abhängigkeitsgraphen scannen, alle verbrauchenden Systeme identifizieren und vor der Außerbetriebnahme vorab vereinbarte Vorankündigungsfristen einhalten.
 #3.6.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass ausgemusterte Modell-Artefakte gemäß dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptografische Löschung oder mehrfaches Überschreiben gelöscht werden, wobei zertifizierte Vernichtungsnachweise vorliegen.
 #3.6.3    Level: 2    Rolle: V
 Überprüfen Sie, ob Modell-Ruhestandsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.
 #3.6.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Notfallabschaltung von Modellen den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiten durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.

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

Die KI-Infrastruktur muss gegen Privilegienerweiterung, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolation, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und -konfigurationen gelangen über kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfprotokolle führen, in die Produktion.

---

### C4.1 Laufzeitumgebungsisolierung

Verhindern Sie das Entkommen aus Containern und die Eskalation von Berechtigungen durch kernelbasierte Isolationsprimitiven und obligatorische Zugriffskontrollen.

 #4.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten deaktivieren.
 #4.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vordefinierten Erlaubnislisten, wobei Verstöße zum Beenden des Containers und zur Generierung von Sicherheitswarnungen führen.
 #4.1.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass KI-Workloads mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.
 #4.1.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass eine auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder Äquivalentes) Versuche zur Privilegienerweiterung erkennt und störende Prozesse automatisch innerhalb der organisatorischen Reaktionszeit-Anforderungen beendet.
 #4.1.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass KI-Workloads mit hohem Risiko in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsüberprüfung ausgeführt werden.

---

### C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

 #4.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools wie tfsec, Checkov oder Terrascan gescannt wird und dass Merges bei CRITICAL- oder HIGH-Schweregrad-Funden blockiert werden.
 #4.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Container-Builds reproduzierbar sind und bei Wiederholungen identische SHA256-Hashes erzeugen, und erstellen Sie SLSA Level 3 Herkunftsbestätigungen, die mit Sigstore signiert sind.
 #4.2.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und vor dem Push in das Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.
 #4.2.4    Level: 2    Rolle: D/V
 Überprüfen Sie, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Laufzeiten die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreiten.
 #4.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Containerausführung überprüft werden und dass Verifizierungsfehler zum Scheitern der Bereitstellung führen.
 #4.2.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Build-Umgebungen in flüchtigen Containern oder VMs ohne persistenten Speicher und mit Netzwerktrennung von Produktions-VPCs ausgeführt werden.

---

### C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit standardmäßigen Verweigerungsrichtlinien und verschlüsselter Kommunikation.

 #4.3.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Kubernetes NetworkPolicies oder ein Äquivalent ein standardmäßiges Verweigern von Ingress/Egress mit expliziten Erlaubnisregeln für erforderliche Ports (443, 8080, etc.) implementieren.
 #4.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatsbasierte Authentifizierung erfordern.
 #4.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Erlaubnislisten gefiltert wird und blockierte Anfragen protokolliert werden.
 #4.3.4    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei Zertifikate gemäß der Organisationsrichtlinie rotiert und die Zertifikatsvalidierung durchgesetzt wird (keine skip-verify-Flaggen).
 #4.3.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und nur über NAT-Gateways oder Bastion-Hosts kommuniziert.

---

### C4.4 Geheimnisse & Verwaltung kryptografischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

 #4.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert werden.
 #4.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) mit Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erzeugt werden.
 #4.4.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Rotation von Geheimnissen automatisiert erfolgt, mit einer unterbrechungsfreien Bereitstellung und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.
 #4.4.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.
 #4.4.5    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Prüfprotokolle mit Benutzeridentitäten und Zeitstempeln dokumentiert wird.
 #4.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, gemountete Volumes oder Init-Container injiziert werden, und stellen Sie sicher, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind.

---

### C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

 #4.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.
 #4.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert sind.
 #4.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Validierung von KI-Modellen automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalysen zur Erkennung von Hintertüren umfasst.
 #4.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse von autorisiertem Sicherheitspersonal kryptografisch signiert und in unveränderlichen Prüfprotokollen gespeichert werden.
 #4.5.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Gold-Images neu erstellt werden, wobei eine vollständige Bereinigung des Dateisystems und des Arbeitsspeichers erfolgt.

---

### C4.6 Infrastruktur-Sicherheitsüberwachung

Infrastruktur kontinuierlich scannen und überwachen mit automatisierter Behebung und Echtzeit-Benachrichtigung.

 #4.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei KRITISCHE Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.
 #4.6.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten und automatischer Behebung bei fehlgeschlagenen Prüfungen erfüllt.
 #4.6.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Schwachstellen mit HÖHERER Kritikalität gemäß den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.
 #4.6.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung der Formate CEF oder STIX/TAXII mit automatischer Anreicherung integriert werden.
 #4.6.5    Level: 3    Rolle: V
 Überprüfen Sie, dass Infrastrukturmetriken mit SLA-Dashboards und Executive-Reporting an Überwachungssysteme (Prometheus, DataDog) exportiert werden.
 #4.6.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) entsprechend den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischem Rollback bei unautorisierten Änderungen.

---

### C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Angriffe durch Ressourcenerschöpfung und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

 #4.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die GPU/TPU-Auslastung überwacht wird, wobei bei organisatorisch definierten Schwellenwerten Warnmeldungen ausgelöst und basierend auf Kapazitätsmanagement-Richtlinien automatische Skalierung oder Lastenausgleich aktiviert werden.
 #4.7.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob AI-Arbeitslastmetriken (Inference-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Infrastruktur-Auslastung korreliert werden.
 #4.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Kubernetes ResourceQuotas oder ein Äquivalent einzelne Workloads gemäß den organisatorischen Richtlinien zur Ressourcenzuteilung mit durchgesetzten harten Grenzwerten begrenzen.
 #4.7.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die Kostenüberwachung die Ausgaben pro Arbeitslast/Mieter verfolgt, mit Warnmeldungen basierend auf den Budgetgrenzen der Organisation und automatisierten Kontrollen bei Budgetüberschreitungen.
 #4.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfragemustern erfolgt.
 #4.7.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Ressourcenerschöpfung entsprechend den organisatorischen Reaktionsanforderungen Circuit Breaker auslöst, einschließlich der Drosselung basierend auf Kapazitätsrichtlinien und Workload-Isolierung.

---

### C4.8 Umgebungstrennung & Promotion-Kontrollen

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Beförderungstoren und Sicherheitsvalidierung.

 #4.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen, ohne gemeinsam genutzte IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.
 #4.8.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Beförderung der Umgebung die Genehmigung von organisatorisch definiertem autorisiertem Personal mit kryptografischen Signaturen und unveränderlichen Prüfpfaden erfordert.
 #4.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Produktionsumgebungen den SSH-Zugang blockieren, Debug-Endpunkte deaktivieren und Änderungsanforderungen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen verlangen.
 #4.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code vor dem Merge in den Hauptzweig eine Peer-Review, automatisierte Tests und eine Sicherheitsüberprüfung durchlaufen.
 #4.8.5    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert wurden, die Generierung synthetischer Daten erfolgt ist oder eine vollständige Datenmaskierung mit Entfernung personenbezogener Informationen (PII) verifiziert wurde.
 #4.8.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Promotion-Gates automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, wobei für die Genehmigung keine CRITICAL-Funde zulässig sind.

---

### C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfunktionen.

 #4.9.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen mit der 3-2-1-Backup-Strategie in geografisch getrennte Regionen gesichert werden.
 #4.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Backup-Systeme in isolierten Netzwerken mit separaten Zugangsdaten und luftgetrenntem Speicher zum Schutz vor Ransomware betrieben werden.
 #4.9.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit automatisierten Tests geprüft und validiert werden, wobei RTO- und RPO-Ziele die organisatorischen Anforderungen erfüllen.
 #4.9.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit der Wiederherstellung der Modellgewichte, dem Wiederaufbau von GPU-Clustern und der Abbildung von Dienstabhängigkeiten umfasst.

---

### C4.10 Infrastruktur-Compliance & Governance

Gewährleisten Sie die Einhaltung gesetzlicher Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollmechanismen.

 #4.10.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand der SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatischer Evidenzsammlung bewertet wird.
 #4.10.2    Level: 2    Rolle: V
 Überprüfen Sie, ob die Infrastruktur-Dokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.
 #4.10.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung unterzogen werden, die bei risikoreichen Änderungen regulatorische Genehmigungsabläufe beinhaltet.

---

### C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

 #4.11.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen überprüft wird und entsprechend den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird.
 #4.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mit TPM 2.0, Intel TXT oder AMD SVM überprüft wird.
 #4.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der GPU-Speicher zwischen den Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen Hardwarepartitionierung mit Speichersanitierung zwischen den Jobs isoliert ist.
 #4.11.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Lieferkette der KI-Hardware eine Herkunftsprüfung mit Herstellungszertifikaten und eine Validierung der manipulationssicheren Verpackung umfasst.
 #4.11.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) KI-Modellgewichte und kryptografische Schlüssel mit FIPS 140-2 Level 3 oder Common Criteria EAL4+-Zertifizierung schützen.

---

### C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Einsätze, einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

 #4.12.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mittels mutual TLS mit Gerätezertifikaten authentifizieren, die gemäß der organisatorischen Zertifikatsverwaltungspolitik rotiert werden.
 #4.12.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und Rollback-Schutz implementieren, um Firmware-Downgrade-Angriffe zu verhindern.
 #4.12.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und bösartiger Knotenerkennung verwendet.
 #4.12.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfähigkeit mit sicherer lokaler Speicherung umfasst.

---

### C4.13 Multi-Cloud- und Hybrid-Infrastruktursicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybridem Cloud- und On-Premises-Betrieb.

 #4.13.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Multi-Cloud-AI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über Anbieter hinweg verwenden.
 #4.13.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Datentransfer zwischen verschiedenen Clouds eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet und die Datenresidenzkontrollen gemäß der jeweiligen Rechtsordnung durchgesetzt werden.
 #4.13.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlicher Überwachung und Alarmierung implementieren.
 #4.13.4    Level: 3    Rolle: V
 Überprüfen Sie, dass die Vermeidung von Cloud-Anbieterabhängigkeit portable Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfasst.
 #4.13.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen beinhaltet, die sowohl die Ausbreitung von Ressourcen verhindern als auch unerlaubte gebührenpflichtige Datentransfers zwischen Clouds.

---

### C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Automatisierungspipelines für Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

 #4.14.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass GitOps-Repositorien signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln implementiert sind, die direkte Pushes auf Hauptzweige verhindern.
 #4.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Behebung und Rückrollfunktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für nicht autorisierte Änderungen ausgelöst werden.
 #4.14.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die automatisierte Bereitstellung der Infrastruktur eine Validierung der Sicherheitsrichtlinien umfasst und die Bereitstellung bei nicht konformen Konfigurationen blockiert wird.
 #4.14.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Infrastruktur-Automatisierungsgeheimnisse durch externe Secret-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.
 #4.14.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die selbstheilende Infrastruktur die Korrelation von Sicherheitsereignissen mit automatisierter Reaktionsauslösung auf Vorfälle und Benachrichtigungsabläufen für Beteiligte umfasst.

---

### C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantum-kryptographische Verfahren und quantensichere Protokolle einsetzen.

 #4.15.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die KI-Infrastruktur NIST-zugelassene postquantensichere kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert.
 #4.15.2    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Quanten-Schlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungprotokollen implementiert sind.
 #4.15.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob kryptografische Agilitätsframeworks eine schnelle Migration zu neuen postquantensicheren Algorithmen mit automatischer Zertifikats- und Schlüsselrotation ermöglichen.
 #4.15.4    Level: 3    Rolle: V
 Verifizieren Sie, dass die Bedrohungsmodellierung durch Quantenrechner die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet und dokumentierte Migrationszeitpläne sowie Risikobewertungen enthält.
 #4.15.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase mit Leistungsüberwachung eine Tiefenverteidigung bieten.

---

### C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe hardwarebasierter vertrauenswürdiger Ausführungsumgebungen und vertraulicher Computertechnologien.

 #4.16.1    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.
 #4.16.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mittels hardwaregestützter Speicher-Verschlüsselung isolieren.
 #4.16.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Remote-Attestation die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität einer Ausführungsumgebung geladen werden.
 #4.16.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass vertrauliche KI-Inferenzdienste die Modellauslesung durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.
 #4.16.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Orchestrierung der Trusted Execution Environment den Lebenszyklus des sicheren Enclaves mit Remote-Attestation und verschlüsselten Kommunikationskanälen verwaltet.
 #4.16.6    Level: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Mehrparteienberechnung (SMPC) kollaboratives KI-Training ermöglicht, ohne einzelne Datensätze oder Modellparameter offenzulegen.

---

### C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche AI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

 #4.17.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings verifizieren, ohne Modellgewichte oder Trainingsdaten offenzulegen.
 #4.17.2    Level: 3    Rolle: D/V
 Verifizieren Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.
 #4.17.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Private-Set-Intersection-(PSI)-Protokolle eine sichere Datenabgleichung für föderierte KI ermöglichen, ohne individuelle Datensätze offenzulegen.
 #4.17.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge-Machine-Learning (ZKML)-Systeme verifizierbare KI-Schlüsse mit kryptografischem Nachweis der korrekten Berechnung ermöglichen.
 #4.17.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass ZK-Rollups eine skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Stapelverifizierung und reduziertem Rechenaufwand bieten.

---

### C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und Cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

 #4.18.1    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die AI-Inferenzzeit mit konstanten Zeitalgorithmen und Padding normalisiert wird, um Timing-basierte Modellextraktionsangriffe zu verhindern.
 #4.18.2    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass der Schutz vor Leistungsanalyse Rauschinjektion, Stromleitungsfilterung und zufällig ausgeführte Muster für KI-Hardware umfasst.
 #4.18.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Abschwächung von Seiteneffekten bei Cache-basierten Angriffen Cache-Partitionierung, Randomisierung und Flush-Befehle verwendet, um Informationslecks zu verhindern.
 #4.18.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass der Schutz vor elektromagnetischen Abstrahlungen Abschirmung, Signalfilterung und zufällige Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.
 #4.18.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob mikroarchitekturelle Seitenkanalabwehrmaßnahmen spekulative Ausführungssteuerungen und die Verschleierung von Speicherzugriffsmustern umfassen.

---

### C4.19 Neuromorphe & Spezialisierte KI-Hardware-Sicherheit

Sichern Sie aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

 #4.19.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Sicherheit neuromorpher Chips Spike-Muster-Verschlüsselung, Schutz der synaptischen Gewichtung und hardwarebasierte Validierung der Lernregel umfasst.
 #4.19.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob FPGA-basierte KI-Beschleuniger Bitstromverschlüsselung, Schutzmechanismen gegen Manipulation und sichere Konfigurationsladeverfahren mit authentifizierten Updates implementieren.
 #4.19.3    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die benutzerdefinierte ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine hardwarebasierte Vertrauenswurzel und sichere Schlüsselverwaltung mit Manipulationserkennung umfasst.
 #4.19.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schalttechnik und geschützte optische Signalverarbeitung implementieren.
 #4.19.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Umwandlung enthalten.

---

### C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

 #4.20.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen auf sensiblen KI-Arbeitslasten unter Gewährleistung der kryptographischen Integritätsprüfung und Leistungsüberwachung ermöglicht.
 #4.20.2    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Systeme für die private Informationsabfrage Datenbankanfragen ermöglichen, ohne Abfragemuster offenzulegen, durch kryptografischen Schutz der Zugriffsmuster.
 #4.20.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Mehrparteienberechnungsprotokolle eine datenschutzwahrende KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenergebnisse offenzulegen.
 #4.20.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwert-Kryptografie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.
 #4.20.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistung der datenschutzfreundlichen Berechnung durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien aufrechterhalten bleiben.

---

### C4.15 Agent Framework Cloud-Integrationssicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises/Cloud-Architekturen.

 #4.15.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Cloud-Speicherintegration End-to-End-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.
 #4.15.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden.
 #4.15.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.
 #4.15.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Anforderungen an den Datenaufenthalt durch kryptographische Bestätigung der Speicherorte durchgesetzt werden.
 #4.15.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sicherheitsbewertungen des Cloud-Anbieters agentenspezifische Bedrohungsmodellierung und Risikobewertung umfassen.

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

## C5 Zugriffskontrolle & Identität für KI-Komponenten & Benutzer

### Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextbewusste Autorisierung und eine Durchsetzung zur Laufzeit nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Zugriffsbereiche interagieren, wobei eine kontinuierliche Überprüfung und Auditierung möglich ist.

---

### C5.1 Identitätsverwaltung & Authentifizierung

Richten Sie kryptografisch gesicherte Identitäten für alle Entitäten ein, mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

 #5.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle menschlichen Nutzer und Dienstprinzipale über einen zentralisierten unternehmensweiten Identitätsanbieter (IdP) mittels der OIDC/SAML-Protokolle mit eindeutigen Identitäts-zu-Token-Zuordnungen (keine gemeinsamen Konten oder Anmeldeinformationen) authentifiziert werden.
 #5.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass hochriskante Operationen (Modelldeployment, Gewichteexport, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine Step-up-Authentifizierung mit Sitzungsnachvalidierung erfordern.
 #5.1.3    Level: 2    Rolle: D
 Vergewissern Sie sich, dass neue Verantwortliche eine Identitätsüberprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.
 #5.1.4    Level: 2    Rolle: V
 Überprüfen Sie, ob Zugriffskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung ruhender Konten, Durchsetzung der Anmeldedatenrotation und De-Provisionierungs-Workflows.
 #5.1.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass föderierte KI-Agenten sich über signierte JWT-Assertionen authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.

---

### C5.2 Ressourcenautorisierung & Prinzip der geringsten Rechte

Implementieren Sie feinkörnige Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

 #5.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Erlaubnislisten und Standard-Ablehnungsrichtlinien durchsetzt.
 #5.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das Prinzip der geringsten Privilegien standardmäßig bei Servicekonten durchgesetzt wird, beginnend mit nur Lesezugriff und dass eine dokumentierte geschäftliche Rechtfertigung für Schreibzugriff erforderlich ist.
 #5.2.3    Level: 1    Rolle: V
 Stellen Sie sicher, dass alle Änderungen der Zugriffskontrolle mit genehmigten Änderungsanfragen verknüpft und unveränderlich protokolliert werden, einschließlich Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsdifferenzen.
 #5.2.4    Level: 2    Rolle: D
 Verifizieren Sie, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden.
 #5.2.5    Level: 2    Rolle: D/V
 Überprüfen Sie, ob unbefugte Zugriffsversuche und Ereignisse zur Rechteerweiterung Echtzeitbenachrichtigungen mit kontextbezogenen Metadaten innerhalb von 5 Minuten an SIEM-Systeme auslösen.

---

### C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffskontrollsysteme (ABAC) für kontextbewusste Autorisierungsentscheidungen mit Prüfungsfunktionen ein.

 #5.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Autorisierungsentscheidungen an eine dedizierte Richtlinien-Engine (OPA, Cedar oder gleichwertig) ausgelagert werden, die über authentifizierte APIs mit kryptografischem Integritätsschutz zugänglich ist.
 #5.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich der Benutzerfreigabestufe, der Sensitivitätsklassifizierung der Ressource, des Anforderungskontexts, der Mandantenisolierung und zeitlicher Beschränkungen.
 #5.3.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtliniendefinitionen versioniert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion eingesetzt werden.
 #5.3.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übertragen werden.
 #5.3.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches 5 Minuten für Ressourcen mit hoher Sensitivität und 1 Stunde für Standardressourcen mit Cache-Invalidierungsfunktionen nicht überschreiten.

---

### C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Zeilenebenen-Sicherheitsrichtlinien.

 #5.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Vektor-Datenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf Ebene der Datenbank-Engine durchgesetzt werden und nicht im Anwendungscode.
 #5.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Richtlinien für die Sicherheit auf Zeilenebene (Row-Level Security, RLS) und Maskierung auf Feldebene mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.
 #5.4.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass fehlgeschlagene Autorisierungsbewertungen "Confused-Deputy-Angriffe" verhindern, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlermeldungen zurückgegeben werden, anstatt leere Ergebnismengen zu liefern.
 #5.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Latenz der Richtlinienauswertung kontinuierlich überwacht wird, mit automatisierten Warnungen für Zeitüberschreitungsbedingungen, die eine Umgehung der Autorisierung ermöglichen könnten.
 #5.4.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Abfrage-Wiederholmechanismen Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.

---

### C5.5 Ausgabe-Filterung & Datenschutz zur Verhinderung von Datenverlust

Setzen Sie Nachbearbeitungskontrollen ein, um die unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

 #5.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen zur Filterung nach der Inferenz nicht autorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anfragende geliefert werden.
 #5.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in den Modellausgaben anhand der Berechtigungen des Aufrufers überprüft und entfernt werden, wenn ein unbefugter Zugriff festgestellt wird.
 #5.5.3    Level: 2    Rolle: D
 Überprüfen Sie, dass die Einschränkungen im Ausgabeformat (bereinigte PDFs, Metadaten-entfernte Bilder, genehmigte Dateitypen) entsprechend den Benutzerberechtigungsstufen und Datenklassifikationen durchgesetzt werden.
 #5.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Redaktionsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.
 #5.5.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Hochrisiko-Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptografische Hashes des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.

---

### C5.6 Multi-Mandanten-Isolation

Gewährleisten Sie kryptografische und logische Isolation zwischen Mandanten in gemeinsamer KI-Infrastruktur.

 #5.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespacesegregiert sind und bei Löschung eines Mandanten oder Beendigung einer Sitzung sicher bereinigt werden.
 #5.6.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandantenkennung enthält, die kryptografisch im Vergleich zum Sitzungszusammenhang und den Benutzerberechtigungen validiert wird.
 #5.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Netzwerk-Richtlinien Standard-Verweigern-Regeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.
 #5.6.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass Verschlüsselungsschlüssel für jeden Mandanten einzigartig sind, mit Unterstützung für kundenseitig verwaltete Schlüssel (CMK) und kryptografischer Isolation zwischen den Datenspeichern der Mandanten.

---

### C5.7 Autonome Agenten-Autorisierung

Steuerung von Berechtigungen für KI-Agenten und autonome Systeme durch scoped Capability-Tokens und kontinuierliche Autorisierung.

 #5.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass autonome Agenten abgegrenzte Berechtigungstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, Zeitgrenzen und betrieblichen Einschränkungen auflisten.
 #5.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass risikoreiche Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, Finanztransaktionen) standardmäßig deaktiviert sind und für ihre Aktivierung eine ausdrückliche Genehmigung mit geschäftlicher Begründung erforderlich ist.
 #5.7.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung enthalten und gewährleisten Sie, dass sie nicht offline gespeichert oder wiederverwendet werden können.
 #5.7.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass von Agenten initiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Auditprotokollierung unterzogen werden.
 #5.7.5    Level: 3    Rolle: V
 Überprüfen Sie, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.

---

### Referenzen

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

## C6 Lieferkettensicherheit für Modelle, Frameworks und Daten

### Kontrollziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, -Frameworks oder -Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzuschleusen. Diese Kontrollen bieten eine durchgängige Herkunftsnachverfolgung, Schwachstellenmanagement und Überwachung, um den gesamten Modellentwicklungszyklus zu schützen.

---

### C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie die Herkunft, Lizenzen und verborgenen Verhaltensweisen von Modellen Dritter, bevor Sie Feinabstimmungen vornehmen oder diese bereitstellen.

 #6.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Drittanbieter-Modellartefakt einen signierten Herkunftsnachweis enthält, der das Quell-Repository und den Commit-Hash identifiziert.
 #6.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojanische Auslöser gescannt werden.
 #6.1.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Transferlernen-Feinabstimmungen eine adversariale Bewertung bestehen, um verborgene Verhaltensweisen zu erkennen.
 #6.1.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Modelllizenzen, Exportkontrollkennzeichnungen und Angaben zur Datenherkunft in einem ML-BOM-Eintrag aufgezeichnet sind.
 #6.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Hochrisikomodelle (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe in Quarantäne bleiben.

---

### C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und -Bibliotheken auf CVEs und bösartigen Code, um den Laufzeit-Stack sicher zu halten.

 #6.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass CI-Pipelines Dependency-Scanner auf KI-Frameworks und kritische Bibliotheken ausführen.
 #6.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass kritische Schwachstellen (CVSS ≥ 7,0) die Freigabe für Produktions-Images blockieren.
 #6.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebundenen ML-Bibliotheken ausgeführt wird.
 #6.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Framework-Upgrade-Vorschläge eine Sicherheitsauswirkungsbewertung enthalten, die sich auf öffentliche CVE-Feeds bezieht.
 #6.2.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksläufen alarmieren, die von der signierten SBOM abweichen.

---

### C6.3 Abhängigkeits-Pinning und -Verifizierung

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationsfreie Artefakte zu garantieren.

 #6.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob alle Paketmanager die Versionssperrung über Lockfiles erzwingen.
 #6.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass unveränderliche Digests anstelle von veränderlichen Tags in Container-Referenzen verwendet werden.
 #6.3.3    Level: 2    Rolle: D
 Überprüfen Sie, dass reproduzierbare Build-Checks Hashes über CI-Durchläufe hinweg vergleichen, um identische Ausgaben sicherzustellen.
 #6.3.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Build-Atteste für 18 Monate zur Audit-Rückverfolgbarkeit gespeichert werden.
 #6.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um angeheftete Versionen zu aktualisieren oder zu forken.

---

### C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlauben Sie den Download von Artefakten nur von kryptographisch verifizierten, von der Organisation genehmigten Quellen und blockieren Sie alle anderen.

 #6.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registrierungen heruntergeladen werden.
 #6.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers überprüfen, bevor Artefakte lokal zwischengespeichert werden.
 #6.4.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Egress-Proxys nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.
 #6.4.4    Level: 2    Rolle: V
 Verifizieren Sie, dass Repository-Allow-Lists vierteljährlich überprüft werden, mit Nachweisen für die geschäftliche Rechtfertigung für jeden Eintrag.
 #6.4.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Richtlinienverstöße zur Quarantäne von Artefakten und zum Zurücksetzen abhängiger Pipeline-Läufe führen.

---

### C6.5 Bewertung von Risiken bei Datensätzen Dritter

Bewerten Sie externe Datensätze auf Vergiftung, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

 #6.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass externe Datensätze einer Bewertung des Vergiftungsrisikos unterzogen werden (z. B. Daten-Fingerprinting, Ausreißererkennung).
 #6.5.2    Level: 1    Rolle: D
 Verifizieren Sie, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.
 #6.5.3    Level: 2    Rolle: V
 Verifizieren Sie, dass Herkunft und Lizenzbedingungen für Datensätze in ML-BOM-Einträgen erfasst werden.
 #6.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die regelmäßige Überwachung Verschiebungen oder Beschädigungen in gehosteten Datensätzen erkennt.
 #6.5.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass nicht erlaubte Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Entfernen entfernt werden.

---

### C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Bedrohungen in der Lieferkette frühzeitig durch CVE-Feeds, Audit-Protokoll-Analysen und Red-Team-Simulationen.

 #6.6.1    Level: 1    Rolle: V
 Überprüfen Sie, dass CI/CD-Auditprotokolle an SIEM-Erkennungen für anomale Paketabrufe oder manipulierte Build-Schritte übertragen werden.
 #6.6.2    Level: 2    Rolle: D
 Überprüfen Sie, ob die Incident-Response-Playbooks Rollback-Verfahren für kompromittierte Modelle oder Bibliotheken enthalten.
 #6.6.3    Level: 3    Rolle: V
 Verifizieren Sie, dass die Bedrohungs-Intelligence-Anreicherung ML-spezifische Indikatoren (z. B. model-poisoning IoCs) bei der Alarmbewertung kennzeichnet.

---

### C6.7 ML‑BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, auf maschinelles Lernen spezialisierte SBOMs (ML‑BOMs), damit nachgelagerte Verbraucher die Integrität der Komponenten zur Bereitstellungszeit überprüfen können.

 #6.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Modellartefakt eine ML-BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.
 #6.7.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass die ML‑BOM-Erstellung und die Cosign-Signierung in der CI automatisiert sind und für das Zusammenführen erforderlich sind.
 #6.7.3    Level: 2    Rolle: D
 Überprüfen Sie, dass die Vollständigkeitsprüfungen von ML‑BOM den Build fehlschlagen lassen, wenn Metadaten eines beliebigen Components (Hash, Lizenz) fehlen.
 #6.7.4    Level: 2    Rolle: V
 Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zum Bereitstellungszeitpunkt zu validieren.
 #6.7.5    Level: 3    Rolle: V
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

## C7 Modellverhalten, Ausgabe­kontrolle & Sicherheits­garantie

### Kontrollziel

Modelausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und kontinuierlich in der Produktion überwacht werden. Dies reduziert Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und außer Kontrolle geratene Aktionen, während es das Vertrauen der Nutzer und die Einhaltung von Vorschriften erhöht.

---

### C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Decodierung und nachgelagerte Validierung stoppen fehlerhafte oder bösartige Inhalte, bevor sie sich ausbreiten.

 #7.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Antwortschemas (z. B. JSON Schema) im System-Prompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben führen zu einer Reparatur oder Ablehnung.
 #7.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die eingeschränkte Dekodierung (Stopptoken, Regex, Max-Tokens) aktiviert ist, um Überläufe oder Prompt-Injection-Seitenkanäle zu verhindern.
 #7.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.
 #7.1.4    Level: 3    Rolle: V
 Überprüfen Sie, dass Ereignisse mit fehlerhaften Ausgaben protokolliert, mit Begrenzung der Rate versehen und in der Überwachung angezeigt werden.

---

### C7.2 Halluzinationserkennung und -minderung

Die Abschätzung der Unsicherheit und Fallback-Strategien begrenzen erfundene Antworten.

 #7.2.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass token-spezifische Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.
 #7.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Antworten unterhalb einer konfigurierbaren Vertrauensschwelle Rückfall-Workflows auslösen (z. B. retrieval-augmented generation, sekundäres Modell oder menschliche Überprüfung).
 #7.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Halluzinationsvorfälle mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungs-Pipelines weitergeleitet werden.
 #7.2.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.
 #7.2.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.

---

### C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

 #7.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass vor- und nachgelagerte Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren.
 #7.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort ausgeführt werden; Verstöße führen zu einem Datenschutzvorfall.
 #7.3.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Vertraulichkeitstags (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg propagiert werden, um eine Weitergabe in Text, Bildern oder Code zu verhindern.
 #7.3.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Umgehungsversuche von Filtern oder Hochrisikoklassifizierungen eine sekundäre Freigabe oder eine erneute Benutzerauthentifizierung erfordern.
 #7.3.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeitsbereiche sowie den Benutzeralter-/Rollen-Kontext widerspiegeln.

---

### C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungsschleusen verhindern Missbrauch und übermäßige Autonomie.

 #7.4.1    Level: 1    Rolle: D
 Überprüfen Sie, ob die Pro-Benutzer- und Pro-API-Schlüssel-Quoten Anfragen, Tokens und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.
 #7.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkaufrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Überprüfung erfordern.
 #7.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Cross-Modal-Konsistenzprüfungen gewährleisten, dass Bilder, Code und Text, die für dieselbe Anfrage generiert werden, nicht verwendet werden können, um bösartigen Inhalt einzuschleusen.
 #7.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Tiefe der Agenten-Delegation, Rekursionsgrenzen und zulässige Werkzeuglisten explizit konfiguriert sind.
 #7.4.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Überschreitung von Grenzen strukturierte Sicherheitsereignisse für die SIEM-Einbindung auslöst.

---

### C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlersuche.

 #7.5.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikobewertung dies als angemessen erachtet.
 #7.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass generierte Erklärungen keine sensiblen Systemaufforderungen oder proprietären Daten offenlegen.
 #7.5.3    Level: 3    Rolle: D
 Verifizieren Sie, dass das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und diese zur autorisierten Prüfung speichert.
 #7.5.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Erklärbarkeitsartefakte zusammen mit Modellversionen versioniert werden, um die Nachvollziehbarkeit zu gewährleisten.

---

### C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt den Kreislauf zwischen Entwicklung und Produktion.

 #7.6.1    Level: 1    Rolle: D
 Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden.
 #7.6.2    Level: 1    Rolle: V
 Stellen Sie sicher, dass für jede Sicherheitsmetrik Alarmgrenzwerte definiert sind, einschließlich Eskalationspfaden für den Bereitschaftsdienst.
 #7.6.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen an den vorgelagerten Daten korrelieren.
 #7.6.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regel-Updates zurückfließen.
 #7.6.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Überwachungspipelines einem Penetrationstest unterzogen und zugriffskontrolliert sind, um das Austreten sensibler Protokolle zu vermeiden.

---

### 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder nicht autorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabevalidierung und Rückverfolgbarkeit durchsetzen.

 #7.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bild, Video, Audio) untersagen.
 #7.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Eingabeaufforderungen auf Versuche überprüft werden, Nachahmungen, sexuell explizite Deepfakes oder Medien, die reale Personen ohne Zustimmung darstellen, zu erzeugen.
 #7.7.3    Level: 2    Rolle: V
 Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Medienmaterial zu verhindern.
 #7.7.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um die Nachverfolgbarkeit im weiteren Verlauf zu gewährleisten.
 #7.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird den Überwachungssystemen gemeldet.

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

## C8-Speicher, Einbettungen & Vektor-Datenbanksicherheit

### Kontrollziel

Embeddings und Vektorspeicher fungieren als das „aktive Gedächtnis“ moderner KI-Systeme, indem sie kontinuierlich vom Benutzer bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in die Kontextverarbeitung der Modelle zurückführen. Wenn diese Gedächtnisfunktion ungezügelt bleibt, können personenbezogene Daten (PII) durchsickern, Einwilligungen verletzt oder durch Inversion der ursprüngliche Text rekonstruiert werden. Ziel dieser Kontrollfamilie ist es, Gedächtnispipelines und Vektordatenbanken so abzusichern, dass der Zugriff nach dem Prinzip der minimalen Berechtigung erfolgt, Embeddings datenschutzkonform sind, gespeicherte Vektoren ein Ablaufdatum haben oder auf Anfrage widerrufen werden können und das pro Benutzer gespeicherte Gedächtnis nicht die Eingaben oder Ausgaben anderer Benutzer beeinträchtigt.

---

### C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzen von fein abgestuften Zugriffskontrollen für jede Vektorensammlung.

 #8.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Zugriffssteuerungsregeln auf Zeilen-/Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokumenten-Tag einschränken.
 #8.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass API-Schlüssel oder JWTs eingeschränkte Berechtigungen (z. B. Sammlungs-IDs, Aktionsverben) tragen und mindestens vierteljährlich rotiert werden.
 #8.1.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Versuche zur Eskalation von Privilegien (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden.
 #8.1.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Vektor-Datenbank Protokolle zu Subjekt-Identifier, Operation, Vektor-ID/-Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.
 #8.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsmängel geprüft werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.

---

### C8.2 Einbettungssanierung & Validierung

Vor der Vektorisierung Text auf personenbezogene Daten (PII) vorab prüfen, diese schwärzen oder pseudonymisieren und optional die Einbettungen nachverarbeiten, um verbleibende Signale zu entfernen.

 #8.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass PII und regulierte Daten durch automatisierte Klassifikatoren erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.
 #8.2.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Einbettungspipelines Eingaben, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder isolieren.
 #8.2.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass eine lokale oder metrische Differential-Privacy-Sanitisierung auf Satz-Embeddings angewendet wird, deren Abstand zu einem bekannten PII-Token unterhalb eines konfigurierbaren Schwellenwerts liegt.
 #8.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückruf der PII-Entfernung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.
 #8.2.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sanitisierungskonfigurationen versioniert sind und Änderungen einer Peer-Review unterzogen werden.

---

### C8.3 Speicherablauf, Widerruf und Löschung

Die DSGVO "Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine zeitnahe Löschung; Vektor-Speicher müssen daher TTLs, endgültige Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

 #8.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass jeder Vektor- und Metadaten-Datensatz eine TTL oder ein explizites Aufbewahrungslabel trägt, das von automatisierten Bereinigungsaufgaben beachtet wird.
 #8.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.
 #8.3.3    Level: 2    Rolle: D
 Überprüfen Sie, ob logische Löschungen von einer kryptographischen Vernichtung der Speicherblöcke gefolgt werden, wenn die Hardware dies unterstützt, oder durch die Zerstörung der Schlüssel im Key-Vault.
 #8.3.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf aus den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.

---

### C8.4 Verhinderung von Einbettungsumkehr und -leckage

Aktuelle Verteidigungen – Rauschüberlagerung, Projektionsnetzwerke, Privacy-Neuron-Perturbation und Anwendungsschichtverschlüsselung – können die Token-Ebenen-Inversionsraten auf unter 5 % senken.

 #8.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass ein formelles Bedrohungsmodell, das Inversions-, Mitgliedschafts- und Attribut-Informationsangriffe abdeckt, existiert und jährlich überprüft wird.
 #8.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Verschlüsselung auf Anwendungsebene oder durchsuchbare Verschlüsselung Vektoren vor direktem Zugriff durch Infrastrukturadministratoren oder Cloud-Mitarbeiter schützt.
 #8.4.3    Level: 3    Rolle: V
 Überprüfen Sie, dass die Verteidigungsparameter (ε für DP, Rausch-σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzen ≤ 3 % Genauigkeitsverlust gewährleisten.
 #8.4.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Inversionsresilienzmetriken Teil der Freigabetore für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.

---

### C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein hohes Risiko für RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden offenlegen.

 #8.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Abrageabfrage vor der Übergabe an den LLM-Prompt nach Mandanten-/Benutzer-ID nachgefiltert wird.
 #8.5.2    Level: 1    Rolle: D
 Überprüfen Sie, ob Sammlungsnamen oder Namespaced-IDs für jeden Benutzer oder Mandanten gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.
 #8.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Ähnlichkeitsergebnisse, die über einem konfigurierbaren Distanzschwellenwert liegen, aber außerhalb des Gültigkeitsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.
 #8.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Multi-Tenant-Stresstests adversarielle Anfragen simulieren, die versuchen, Dokumente außerhalb des zulässigen Bereichs abzurufen, und zeigen Sie eine vollständige Vermeidung von Datenleckagen.
 #8.5.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Verschlüsselungsschlüssel pro Mandant getrennt sind, um kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.

---

### C8.6 Erweiterte Sicherheit von Speichersystemen

Sicherheitskontrollen für anspruchsvolle Speicherarchitekturen einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

 #8.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass verschiedene Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen.
 #8.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherfestigungsprozesse eine Sicherheitsvalidierung beinhalten, um die Einschleusung schädlicher Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor dem Speichern zu verhindern.
 #8.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherabfrageanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse von Abfragemustern, Durchsetzung der Zugriffskontrolle und Filterung der Ergebnisse zu verhindern.
 #8.6.4    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Speichervergessensmechanismen sensible Informationen sicher löschen und dabei kryptografische Löschungsgarantien durch Schlüssellöschung, Mehrfachüberschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten gewährleisten.
 #8.6.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Integrität des Speichersystems kontinuierlich auf unautorisierte Änderungen oder Beschädigungen überwacht wird, durch Prüfsummen, Auditprotokolle und automatisierte Alarme, wenn sich der Speicherinhalt außerhalb der normalen Abläufe ändert.

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

## 9 Autonome Orchestrierung & Agentische Handlungssicherheit

### Kontrollziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb festgelegter Kosten- und Risikoschwellen liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Missbrauch von Werkzeugen, Agentenschleifenerkennung, Kommunikationsübernahme, Identitätsfälschung, Schwarmmanipulation und Manipulation der Absicht.

---

### 9.1 Aufgabenplanung von Agenten & Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

 #9.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass maximale Rekursionstiefe, Breite, Echtzeitdauer, Token und monetäre Kosten pro Agentenausführung zentral konfiguriert und versioniert werden.
 #9.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, Finanztransfers) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern.
 #9.1.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Echtzeit-Ressourcenmonitoren eine Unterbrechung durch den Circuit-Breaker auslösen, wenn eine Budgetschwelle überschritten wird, und dadurch eine weitere Aufgabenerweiterung stoppen.
 #9.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Circuit-Breaker-Ereignisse mit der Agenten-ID, der Auslösebedingung und dem erfassten Planstatus zur forensischen Überprüfung protokolliert werden.
 #9.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Sicherheitstests Szenarien mit Erschöpfung des Budgets und ausufernden Plänen abdecken und ein sicheres Anhalten ohne Datenverlust bestätigen.
 #9.1.6    Level: 3    Rolle: D
 Stellen Sie sicher, dass Budgetrichtlinien als Richtlinien-als-Code formuliert und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.

---

### 9.2 Werkzeug-Plugin-Sandboxing

Isolieren Sie Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

 #9.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Tool/Plugin innerhalb eines Betriebssystems, Containers oder einer WASM-Ebene-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird.
 #9.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Ressourcenkontingente (CPU, Arbeitsspeicher, Festplatte, Netzwerkausgang) und Ausführungszeitüberschreitungen durchgesetzt und protokolliert werden.
 #9.2.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Tool-Binärdateien oder Deskriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.
 #9.2.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Sandbox-Telemetriedaten an ein SIEM übertragen werden; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Alarme aus.
 #9.2.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass hochriskante Plugins vor dem produktiven Einsatz einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden.
 #9.2.6    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Ausbruchsversuche automatisch blockiert werden und das fehlerhafte Plugin bis zur Untersuchung unter Quarantäne gestellt wird.

---

### 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte Agent-zu-Agent-Rekursionen und Kostenexplosionen.

 #9.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Inter-Agent-Aufrufe ein Hop-Limit oder eine TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.
 #9.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Agenten eine eindeutige Aufrufgraph-ID führen, um Selbstaufrufe oder zyklische Muster zu erkennen.
 #9.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass kumulative Compute-Unit- und Ausgabenzähler pro Anfragekette verfolgt werden; das Überschreiten des Limits führt zum Abbruch der Kette.
 #9.3.4    Level: 3    Rolle: V
 Verifizieren Sie, dass formale Analyse oder Modellprüfung das Fehlen von unbeschränkter Rekursion in Agentenprotokollen nachweist.
 #9.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob Schleifen-Abbruchereignisse Alarme erzeugen und kontinuierliche Verbesserungskennzahlen speisen.

---

### 9.4 Protokollebene-Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Übernahmen oder Manipulationen zu verhindern.

 #9.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Nachrichten zwischen Agent und Werkzeug sowie zwischen Agent und Agent authentifiziert sind (z. B. durch gegenseitiges TLS oder JWT) und Ende-zu-Ende verschlüsselt sind.
 #9.4.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Schemata strikt validiert werden; unbekannte Felder oder fehlerhafte Nachrichten werden abgelehnt.
 #9.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nachrichten-Nutzlast einschließlich der Werkzeugparameter abdecken.
 #9.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass der Schutz vor Wiedergabeangriffen (Nonces oder Zeitstempelfenster) auf Protokollebene durchgesetzt wird.
 #9.4.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Protokollimplementierungen einer Fuzzing- und statischen Analyse auf Injektions- oder Deserialisierungsfehler unterzogen werden.

---

### 9.5 Agent-Identität & Manipulationssicherheit

Stellen Sie sicher, dass Aktionen zuordenbar sind und Änderungen erkennbar sind.

 #9.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Agenteninstanz über eine eindeutige kryptografische Identität (Schlüsselpaar oder hardwarebasierte Anmeldeinformationen) verfügt.
 #9.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Agentenaktionen signiert und mit einem Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.
 #9.5.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass manipulationssichere Protokolle in einem nur anfügefähigen oder einmal beschreibbaren Medium gespeichert werden.
 #9.5.4    Level: 3    Rolle: D
 Überprüfen Sie, dass Identitätsschlüssel nach einem definierten Zeitplan und bei Anzeichen eines Kompromisses rotiert werden.
 #9.5.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.

---

### 9.6 Multi-Agent Schwarm-Risikominimierung

Mildern Sie Gefahren kollektiven Verhaltens durch Isolation und formale Sicherheitsmodellierung.

 #9.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten, die in verschiedenen Sicherheitsdomänen operieren, in isolierten Laufzeitsandboxes oder Netzwerkssegmenten ausgeführt werden.
 #9.6.2    Level: 3    Rolle: V
 Stellen Sie sicher, dass Schwarmverhalten modelliert und formell auf Lebendigkeit und Sicherheit vor der Implementierung verifiziert werden.
 #9.6.3    Level: 3    Rolle: D
 Stellen Sie sicher, dass Laufzeit-Monitore auftretende unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und Korrekturmaßnahmen einleiten.

---

### 9.7 Benutzer- und Werkzeugauthentifizierung / -autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede agentenausgelöste Aktion.

 #9.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten sich als erstklassige Hauptakteure gegenüber nachgelagerten Systemen authentifizieren und niemals Endbenutzeranmeldedaten wiederverwenden.
 #9.7.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass fein abgestimmte Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er bereitstellen kann.
 #9.7.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Berechtigungsprüfungen bei jedem Aufruf (kontinuierliche Autorisierung) erneut durchgeführt werden und nicht nur zu Beginn der Sitzung.
 #9.7.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass delegierte Berechtigungen automatisch ablaufen und nach Ablauf der Zeit oder einer Änderung des Geltungsbereichs erneut genehmigt werden müssen.

---

### 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und integritätsschützen Sie alle Nachrichten zwischen Agenten, um Abhören und Manipulation zu verhindern.

 #9.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass gegenseitige Authentifizierung und perfekte Vorwärtsgeheimnis-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.
 #9.8.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Nachrichtenintegrität und die Herkunft vor der Verarbeitung überprüft werden; bei Fehlern werden Warnungen ausgelöst und die Nachricht verworfen.
 #9.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.
 #9.8.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die formale Verifikation oder Modellprüfung bestätigt, dass Protokoll-Zustandsmaschinen nicht in unsichere Zustände gelangen können.

---

### 9.9 Absichtverifizierung & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

 #9.9.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Pre-Execution Constraint Solver vorgeschlagene Aktionen anhand von fest kodierten Sicherheits- und Richtlinienregeln überprüfen.
 #9.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass hochwirksame Aktionen (finanziell, zerstörerisch, datenschutzsensibel) eine ausdrückliche Bestätigung der Absicht durch den initiierenden Benutzer erfordern.
 #9.9.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Nachbedingungsprüfungen bestätigen, dass abgeschlossene Aktionen die beabsichtigten Wirkungen ohne Nebeneffekte erreicht haben; Abweichungen lösen einen Rollback aus.
 #9.9.4    Level: 3    Rolle: V
 Überprüfen Sie, ob formale Methoden (z. B. Model Checking, Theorembeweis) oder eigenschaftsbasierte Tests nachweisen, dass Agentenpläne alle deklarierten Einschränkungen erfüllen.
 #9.9.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass Vorfälle mit Absicht-Abweichungen oder Verstöße gegen Einschränkungen kontinuierliche Verbesserungsprozesse und den Austausch von Bedrohungsinformationen fördern.

---

### 9.10 Sicherheitsstrategie für die Agentenlogik

Sichere Auswahl und Ausführung verschiedener Denkstrategien einschließlich ReAct, Chain-of-Thought und Tree-of-Thoughts Ansätze.

 #9.10.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Auswahl der Reasoning-Strategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und dass identische Eingaben innerhalb desselben Sicherheitskontexts identische Strategiewahlen ergeben.
 #9.10.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) eine dedizierte Eingabevalidierung, Ausgabe-Sanitierung und spezifische Ausführungszeitbegrenzungen entsprechend ihrer kognitiven Vorgehensweise besitzt.
 #9.10.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Übergänge der Denkstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabemerkmalen, Auswahlkriterienwerten und Ausführungsmetadaten zur Rekonstruktion der Prüfpfadspur.
 #9.10.4    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Tree-of-Thoughts-Analyse Verzweigungskürzungsmechanismen umfasst, die die Exploration beenden, wenn Richtlinienverletzungen, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.
 #9.10.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die ReAct (Reason-Act-Observe) Zyklen Validierungspunkte in jeder Phase enthalten: Verifikation des Denkprozesses, Autorisierung der Aktion und Bereinigung der Beobachtung, bevor fortgefahren wird.
 #9.10.6    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Leistungskennzahlen der Reasoning-Strategie (Ausführungszeit, Ressourcennutzung, Ausgabequalität) mit automatisierten Warnmeldungen überwacht werden, wenn die Kennzahlen außerhalb der konfigurierten Schwellenwerte abweichen.
 #9.10.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabeeinschränkungen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.
 #9.10.8    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Sicherheitstests der Argumentationsstrategie Fuzzing mit fehlerhaften Eingaben, adversariale Eingabeaufforderungen, die das Erzwingen eines Strategiewechsels bewirken sollen, sowie Grenzbedingungstests für jeden kognitiven Ansatz umfassen.

---

### 9.11 Agent Lebenszyklus-Zustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Prüfpfaden und definierten Wiederherstellungsverfahren.

 #9.11.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Agenteninitalisierung die Etablierung einer kryptografischen Identität mit hardwaregestützten Anmeldeinformationen sowie unveränderliche Startprotokolle umfasst, die Agenten-ID, Zeitstempel, Konfigurationshash und Initialisierungsparameter enthalten.
 #9.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Agenten-Zustandsübergänge kryptografisch signiert, mit Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich auslösender Ereignisse, Hash des vorherigen Zustands, Hash des neuen Zustands und durchgeführter Sicherheitsüberprüfungen.
 #9.11.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Agenten-Shutdown-Verfahren das sichere Löschen des Speichers mittels kryptografischer Löschung oder mehrfacher Überschreibung, die Widerrufung von Zugangsdaten mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung manipulationssicherer Beendigungszertifikate umfassen.
 #9.11.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Agent-Wiederherstellungsmechanismen die Zustandsintegrität mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Korruption auf bekannte gute Zustände zurücksetzen, wobei automatisierte Warnungen und Anforderungen an manuelle Genehmigungen verwendet werden.
 #9.11.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen zur Agenten-Persistenz sensible Zustandsdaten mit pro Agent verschlüsselten AES-256-Schlüsseln verschlüsseln und eine sichere Schlüsselrotation nach konfigurierbaren Zeitplänen (maximal 90 Tage) mit unterbrechungsfreier Bereitstellung implementieren.

---

### 9.12 Sicherheitsrahmen für die Integration von Tools

Sicherheitskontrollen für das dynamische Laden von Tools, deren Ausführung und Ergebnisvalidierung mit definierten Risikobewertungen und Genehmigungsprozessen.

 #9.12.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Tool-Beschreibungen Sicherheitsmetadaten enthalten, die erforderliche Berechtigungen (Lesen/Schreiben/Ausführen), Risikoniveaus (niedrig/mittel/hoch), Ressourcengrenzen (CPU, Speicher, Netzwerk) sowie Validierungsanforderungen, die in Tool-Manifests dokumentiert sind, angeben.
 #9.12.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Ausführungsergebnisse von Tools vor der Integration innerhalb von Zeitlimits und mit Fehlerbehandlungsverfahren gegen erwartete Schemata (JSON-Schema, XML-Schema) und Sicherheitsrichtlinien (Ausgabesäuberung, Datenklassifizierung) validiert werden.
 #9.12.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Protokolle der Werkzeuginteraktionen einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcenverbrauch und Rückgabecodes, mit strukturiertem Logging für die SIEM-Integration.
 #9.12.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Werkzeuglade-Mechanismen digitale Signaturen mittels PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolation und Berechtigungsprüfung vor der Ausführung implementieren.
 #9.12.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Tool-Sicherheitsbewertungen automatisch für neue Versionen mit obligatorischen Freigabeschritten ausgelöst werden, einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam mit dokumentierten Genehmigungskriterien und SLA-Anforderungen.

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

## 10 Gegnerische Robustheit & Datenschutzabwehr

### Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben, wenn sie Evasions-, Inferenz-, Extraktions- oder Vergiftungsangriffen ausgesetzt sind.

---

### 10.1 Modellabstimmung & Sicherheit

Schützen Sie vor schädlichen oder richtlinienwidrigen Ausgaben.

 #10.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob ein Alignment-Testset (Red-Team-Prompts, Jailbreak-Sonden, nicht erlaubte Inhalte) versioniert wird und bei jeder Modellfreigabe ausgeführt wird.
 #10.1.2    Level: 1    Rolle: D
 Überprüfen Sie, ob Ablehnungs- und sichere Abschluss-Schutzvorrichtungen durchgesetzt werden.
 #10.1.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass ein automatischer Evaluator die Rate schädlicher Inhalte misst und Rückschritte, die einen festgelegten Schwellenwert überschreiten, markiert.
 #10.1.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.
 #10.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass förmliche Nachweise der Richtlinienkonformität oder zertifizierte Überwachungen kritische Bereiche abdecken.

---

### 10.2 Härtung gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes adversariales Training und Benchmark-Bewertungen sind derzeit die beste Praxis.

 #10.2.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Projekt-Repositorien Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.
 #10.2.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines Blockierungswarnungen auslöst.
 #10.2.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate zumindest die wichtigsten kritischen Klassen abdecken.
 #10.2.5    Level: 3    Rolle: V
 Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Robustheitsverlust zu bestätigen.

---

### 10.3 Minderung von Mitgliedschaftsinferenz

Begrenzen Sie die Fähigkeit, zu entscheiden, ob ein Datensatz im Trainingsmaterial enthalten war. Differentielle Privatsphäre und die Maskierung von Konfidenzwerten bleiben die wirksamsten bekannten Abwehrmaßnahmen.

 #10.3.1    Level: 1    Rolle: D
 Überprüfen Sie, ob die Entropieregulierung pro Abfrage oder Temperaturskalierung übermäßig zuversichtliche Vorhersagen reduziert.
 #10.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Training für sensible Datensätze eine ε-begrenzte differentielle Datenschutzoptimierung verwendet.
 #10.3.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Angriffssimulationen (Shadow-Model- oder Black-Box-Methoden) eine Angriffs-AUC ≤ 0,60 auf nicht verwendeten Daten zeigen.

---

### 10.4 Widerstand gegen Modellinversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen heben Ausgabeabschneidung und DP-Garantien als praktische Abwehrmaßnahmen hervor.

 #10.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie, wo erforderlich, Cluster oder Einweg-Transformationen.
 #10.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Abfrageratenbeschränkungen wiederholte adaptive Abfragen desselben Akteurs drosseln.
 #10.4.3    Level: 2    Rolle: D
 Verifizieren Sie, dass das Modell mit datenschutzwahrendem Rauschen trainiert wurde.

---

### 10.5 Verteidigung gegen Modell-Extraktion

Erkennen und verhindern Sie unautorisierte Klonungen. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

 #10.5.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Inferenz-Gateways globale und pro-API-Schlüssel Ratenbegrenzungen durchsetzen, die auf die Merkfähigkeitsschwelle des Modells abgestimmt sind.
 #10.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und Eingabe-Mehrzahl eine automatisierte Extraktionsdetektion unterstützen.
 #10.5.3    Level: 2    Rolle: V
 Verifizieren Sie, dass fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Abfragen gegen einen verdächtigten Klon nachgewiesen werden können.
 #10.5.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöser-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.
 #10.5.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Extraktionswarn-Ereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.

---

### 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Identifizieren und Neutralisieren von hintertürartigen oder vergifteten Eingaben.

 #10.6.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Eingaben einen Anomalie-Detektor (z. B. STRIP, Konsistenzbewertung) durchlaufen, bevor die Modellinferenz erfolgt.
 #10.6.2    Level: 1    Rolle: V
 Überprüfen Sie, ob die Schwellenwerte des Detektors auf sauberen/verseuchten Validierungsdatensätzen so eingestellt sind, dass weniger als 5 % falsch positive Ergebnisse erzielt werden.
 #10.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Eingaben, die als vergiftet markiert sind, Soft-Blocking und menschliche Überprüfungsprozesse auslösen.
 #10.6.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Detektoren mit adaptiven, auslöserlosen Backdoor-Angriffen einem Stresstest unterzogen werden.
 #10.6.5    Level: 3    Rolle: D
 Überprüfen Sie, ob die Wirksamkeitsmetriken der Erkennung protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.

---

### 10.7 Dynamische Anpassung der Sicherheitspolitik

Echtzeit-Aktualisierungen der Sicherheitspolitik basierend auf Bedrohungsinformationen und Verhaltensanalysen.

 #10.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne dass der Agent neu gestartet werden muss, und dabei die Integrität der Richtlinienversion erhalten bleibt.
 #10.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.
 #10.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfprotokollen erfasst werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren.
 #10.7.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.
 #10.7.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Beweispfade für die Überprüfung durch das Sicherheitsteam enthalten.

---

### 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch agenteninterne Selbstreflexion und metakognitive Analyse.

 #10.8.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.
 #10.8.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Reflexionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch adversariale Eingaben zu verhindern.
 #10.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Kompromittierungen in den Denkprozessen von Agenten identifiziert.
 #10.8.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob reflektionsbasierte Sicherheitswarnungen eine erweiterte Überwachung und potenzielle Arbeitsabläufe für menschliches Eingreifen auslösen.
 #10.8.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.

---

### 10.9 Evolution & Selbstverbesserung Sicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

 #10.9.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Selbstmodifikationsfähigkeiten auf festgelegte sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.
 #10.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Entwicklungsvorschläge vor der Umsetzung einer Sicherheitsfolgenabschätzung unterzogen werden.
 #10.9.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Selbstverbesserungsmechanismen Rückrollfähigkeiten mit Integritätsprüfung umfassen.
 #10.9.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.
 #10.9.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen der Konvergenz.

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

## 11 Datenschutz & Verwaltung personenbezogener Daten

### Kontrollziel

Gewährleisten Sie strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg—Erfassung, Training, Inferenz und Vorfallreaktion—damit personenbezogene Daten nur mit klarer Einwilligung, minimalem notwendigen Umfang, nachweisbarer Löschung und formalen Datenschutzgarantien verarbeitet werden.

---

### 11.1 Anonymisierung & Datenminimierung

 #11.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass direkte und quasi-Identifikatoren entfernt oder gehasht werden.
 #11.1.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Alarm schlagen, wenn die Schwellenwerte unter die Richtlinie fallen.
 #11.1.3    Level: 2    Rolle: V
 Verifizieren Sie, dass die Berichte zur Merkmalsbedeutung des Modells keinen Identifier-Leckage über ε = 0,01 gegenseitige Information hinaus nachweisen.
 #11.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise oder die Zertifizierung synthetischer Daten ein Re-Identifikationsrisiko von ≤ 0,05 nachweisen, selbst bei Verknüpfungsangriffen.

---

### 11.2 Recht auf Vergessenwerden & Durchsetzung der Löschung

 #11.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Löschanfragen von Betroffenen bezüglich Daten innerhalb von Service-Level-Agreements von weniger als 30 Tagen auf Rohdatensätze, Checkpoints, Embeddings, Protokolle und Backups übertragen werden.
 #11.2.2    Level: 2    Rolle: D
 Verifizieren Sie, dass „Machine-Unlearning“-Routinen physisch nachtrainieren oder eine Annäherung der Entfernung mithilfe zertifizierter Unlearning-Algorithmen durchführen.
 #11.2.3    Level: 2    Rolle: V
 Überprüfen Sie, dass die Auswertung des Schattenmodells zeigt, dass vergessene Datensätze nach dem Unlearning weniger als 1 % der Ausgaben beeinflussen.
 #11.2.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden prüfbar sind.

---

### 11.3 Differential-Privacy-Schutzmaßnahmen

 #11.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Datenschutz-Verlust-Buchhaltungs-Dashboards Alarm schlagen, wenn die kumulative ε die Richtliniengrenzen überschreitet.
 #11.3.2    Level: 2    Rolle: V
 Überprüfen Sie, dass Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10% des angegebenen Werts schätzen.
 #11.3.3    Level: 3    Rolle: V
 Überprüfen Sie, dass formale Beweise alle nach dem Training durchgeführten Feinabstimmungen und Einbettungen abdecken.

---

### 11.4 Zweckbeschränkung & Schutz vor Umfangserweiterung

 #11.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass jeder Datensatz und jeder Modell-Checkpoint ein maschinenlesbares Zweck-Tag trägt, das mit der ursprünglichen Einwilligung übereinstimmt.
 #11.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Laufzeitmonitore Abfragen erkennen, die mit dem angegebenen Zweck nicht übereinstimmen, und eine weiche Verweigerung auslösen.
 #11.4.3    Level: 3    Rolle: D
 Überprüfen Sie, dass Richtlinien-als-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Prüfung verhindern.
 #11.4.4    Level: 3    Rolle: V
 Überprüfen Sie, dass formale Rückverfolgbarkeitsnachweise zeigen, dass jeder Lebenszyklus personenbezogener Daten innerhalb des genehmigten Umfangs bleibt.

---

### 11.5 Einwilligungsmanagement und rechtmäßige Grundlage der Nachverfolgung

 #11.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro betroffener Person aufzeichnet.
 #11.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass APIs Zustimmungs-Token bereitstellen; Modelle müssen den Token-Bereich vor der Inferenz validieren.
 #11.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungsabläufe innerhalb von 24 Stunden stoppen.

---

### 11.6 Föderiertes Lernen mit Datenschutzkontrollen

 #11.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass bei den Client-Updates vor der Aggregation eine Rauschenaddition mit lokaler differentieller Privatsphäre angewendet wird.
 #11.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients offenlegen.
 #11.6.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass die gegen Manipulationen resistierende Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.
 #11.6.4    Level: 3    Rolle: V
 Überprüfen Sie, dass formale Beweise das gesamte ε-Budget mit einem Nutzenverlust von weniger als 5 nachweisen.

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

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, bewertet und daraus gelernt werden kann.

### C12.1 Anforderungs- und Antwortprotokollierung

 #12.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzeranfragen und Modellantworten mit den entsprechenden Metadaten (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion) protokolliert werden.
 #12.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Sicherungsverfahren gespeichert werden.
 #12.1.3    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Log-Speichersysteme Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen in den Protokollen zu schützen.
 #12.1.4    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben vor dem Protokollieren automatisch unkenntlich gemacht oder maskiert werden, mit konfigurierbaren Regeln zur Unkenntlichmachung für personenbezogene Daten (PII), Anmeldeinformationen und proprietäre Informationen.
 #12.1.5    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Richtlinienentscheidungen und Maßnahmen zur Sicherheitsfilterung mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Inhaltsmoderationssystemen zu ermöglichen.
 #12.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Protokollintegrität durch z. B. kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.

---

### C12.2 Missbrauchserkennung und Alarmierung

 #12.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Prompt-Injektionsversuche und adversariale Eingaben mithilfe von signaturbasierter Erkennung erkennt und meldet.
 #12.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob das System sich mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert.
 #12.2.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass angereicherte Sicherheitsereignisse KI-spezifische Kontexte wie Modellkennungen, Konfidenzwerte und Entscheidungen des Sicherheitsfilters enthalten.
 #12.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abtastverhalten identifiziert.
 #12.2.5    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Benachrichtigungsmechanismen die Sicherheitsteams informieren, wenn potenzielle Richtlinienverletzungen oder Angriffsversuche erkannt werden.
 #12.2.6    Level: 2    Rolle: D/V
 Überprüfen Sie, ob benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modellextraktionsangriffe zu erkennen.
 #12.2.7    Level: 3    Rolle: D/V
 Überprüfen Sie, dass automatisierte Abläufe zur Vorfallreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.

---

### C12.3 Modellabweichungserkennung

 #12.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.
 #12.3.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob automatisierte Benachrichtigungen ausgelöst werden, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder erheblich von den Basiswerten abweichen.
 #12.3.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Halluzinationserkennungsmonitore Instanzen identifizieren und kennzeichnen, bei denen Modelloutputs faktisch falsche, inkonsistente oder erfundene Informationen enthalten.

---

### C12.4 Leistungs- und Verhaltens-Telemetrie

 #12.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass betriebliche Metriken wie Anfragelatenz, Token-Verbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.
 #12.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Erfolgs- und Fehlerquoten mit Kategorisierung der Fehlertypen und ihrer Ursachen verfolgt werden.
 #12.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Überwachung der Ressourcenauslastung die GPU-/CPU-Nutzung, den Speicherverbrauch und die Speicheranforderungen umfasst und bei Überschreiten von Schwellwerten Alarme auslöst.

---

### C12.5 Planung und Durchführung der KI-Zwischenfallreaktion

 #12.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Reaktionspläne für Sicherheitsvorfälle speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversariale Angriffe abdecken.
 #12.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Incident-Response-Teams Zugang zu KI-spezifischen forensischen Werkzeugen und Fachwissen haben, um Modellverhalten und Angriffsvektoren zu untersuchen.
 #12.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Analyse nach Zwischenfällen Überlegungen zur Modellneutrainierung, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst.

---

### C12.5 KI-Leistungsverschlechterungs-Erkennung

Überwachen und Erkennen von Leistungs- und Qualitätsverschlechterungen bei KI-Modellen im Zeitverlauf.

 #12.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basislinien-Schwellenwerten verglichen werden.
 #12.5.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Erkennung von Datenverschiebungen Änderungen in der Eingabeverteilung überwacht, die die Modellleistung beeinflussen könnten.
 #12.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Konzeptdrift-Erkennung Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.
 #12.5.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Leistungsabfälle automatisierte Alarme auslösen und Workflows für das erneute Training oder den Austausch von Modellen einleiten.
 #12.5.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Ursachenanalyse für Leistungsabfälle Leistungseinbußen mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.

---

### C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

 #12.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die DAG-Visualisierungsdaten bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.
 #12.6.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Zugriffssteuerungen bei der Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer Agenten-Entscheidungspfade und Begründungsspuren einsehen können.
 #12.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.
 #12.6.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.
 #12.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen eine Drosselung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.

---

### C12.7 Proaktive Überwachung sicherheitsrelevanten Verhaltens

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

 #12.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung sicherheitsvalidiert sind, einschließlich der Integration einer Risikoanalyse.
 #12.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass autonome Initiativ-Auslöser die Bewertung des Sicherheitskontexts und die Beurteilung der Bedrohungslage umfassen.
 #12.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.
 #12.7.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfprotokollen erfordern.
 #12.7.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Verhaltensanomalie-Erkennung Abweichungen in den proaktiven Agentenmuster identifiziert, die auf eine Kompromittierung hinweisen könnten.

---

### Referenzen

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menschliche Aufsicht, Verantwortlichkeit & Governance

### Kontrollziel

Dieses Kapitel legt Anforderungen für die Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen fest und gewährleistet Erklärbarkeit, Transparenz sowie ethische Verwaltung während des gesamten KI-Lebenszyklus.

---

### C13.1 Not-Aus- und Übersteuerungsmechanismen

Stellen Sie Abschalt- oder Rücksetzpfade bereit, wenn unsicheres Verhalten des KI-Systems beobachtet wird.

 #13.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein manueller Not-Aus-Mechanismus vorhanden ist, um die Inferenz und Ausgabe des KI-Modells sofort zu stoppen.
 #13.1.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Übersteuerungskontrollen nur für autorisiertes Personal zugänglich sind.
 #13.1.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Rücksetzverfahren auf frühere Modellversionen oder den sicheren Betriebsmodus zurücksetzen können.
 #13.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Überschreibemechanismen regelmäßig getestet werden.

---

### C13.2 Mensch-in-der-Schleife Entscheidungs-Checkpoint

Erfordern Sie menschliche Genehmigungen, wenn die Einsätze vordefinierte Risikoschwellen überschreiten.

 #13.2.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass risikoreiche KI-Entscheidungen vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.
 #13.2.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Risikoschwellenwerte klar definiert sind und automatisch menschliche Prüfprozesse auslösen.
 #13.2.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass zeitkritische Entscheidungen über Ausweichverfahren verfügen, falls eine menschliche Genehmigung nicht innerhalb der erforderlichen Fristen eingeholt werden kann.
 #13.2.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.

---

### C13.3 Kette der Verantwortlichkeit & Prüfbarkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

 #13.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden.
 #13.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Audit-Protokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.

---

### C13.4 Erklärbare KI-Techniken

Oberflächenmerkmal-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

 #13.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format bereitstellen.
 #13.4.2    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Qualität der Erklärungen durch menschliche Evaluationsstudien und Metriken validiert wird.
 #13.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Feature-Importance-Werte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.
 #13.4.4    Level: 3    Rolle: V
 Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, falls dies auf den Anwendungsfall und die Domäne zutrifft.

---

### C13.5 Modellkarten & Nutzungsangaben

Pflegen Sie Modelldokumentationen für den vorgesehenen Gebrauch, Leistungskennzahlen und ethische Überlegungen.

 #13.5.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Modellkarten die vorgesehenen Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi dokumentieren.
 #13.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.
 #13.5.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Eigenschaften der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden.
 #13.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und im gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.

---

### C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwahrscheinlichkeiten oder Entropie-Messungen in den Antworten.

 #13.6.1    Level: 1    Rolle: D
 Überprüfen Sie, ob KI-Systeme mit ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.
 #13.6.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.
 #13.6.3    Level: 2    Rolle: V
 Überprüfen Sie, ob Methoden zur Unsicherheitsquantifizierung kalibriert sind und anhand von tatsächlichen Daten validiert wurden.
 #13.6.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Unsicherheitsfortpflanzung durch mehrstufige KI-Workflows erhalten bleibt.

---

### C13.7 Benutzerorientierte Transparenzberichte

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereit.

 #13.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Praktiken des Nutzerzustimmungsmanagements klar an die Interessengruppen kommuniziert werden.
 #13.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.
 #13.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebsmessgrößen in angemessenem Detailgrad offenlegen.

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

Dieses umfassende Glossar liefert Definitionen der wichtigsten Begriffe aus den Bereichen KI, ML und Sicherheit, die im gesamten AISVS verwendet werden, um Klarheit und ein gemeinsames Verständnis zu gewährleisten.

Gegnerisches Beispiel: Eine absichtlich gestaltete Eingabe, die ein KI-Modell zu einem Fehler veranlassen soll, oft durch Hinzufügen subtiler, für Menschen nicht wahrnehmbarer Störungen.
​
Adversarielle Robustheit – Adversarielle Robustheit in der KI bezieht sich auf die Fähigkeit eines Modells, seine Leistung aufrechtzuerhalten und sich gegen absichtlich konstruierte, bösartige Eingaben zu wehren, die darauf ausgelegt sind, Fehler zu verursachen oder das Modell zu täuschen.
​
Agent – KI-Agenten sind Softwaresysteme, die KI nutzen, um Ziele zu verfolgen und Aufgaben im Auftrag von Nutzern zu erledigen. Sie zeigen Fähigkeiten wie Schlussfolgern, Planen und Gedächtnis und verfügen über ein gewisses Maß an Autonomie, um Entscheidungen zu treffen, zu lernen und sich anzupassen.
​
Agentische KI: KI-Systeme, die mit einem gewissen Grad an Autonomie operieren können, um Ziele zu erreichen, und dabei oft Entscheidungen treffen und Maßnahmen ergreifen, ohne direkte menschliche Intervention.
​
Attributbasierte Zugriffskontrolle (ABAC): Ein Zugriffssteuerungsparadigma, bei dem Autorisierungsentscheidungen auf Attributen des Benutzers, der Ressource, der Aktion und der Umgebung basieren, die zur Abfragezeit bewertet werden.
​
Backdoor-Angriff: Eine Art von Datenvergiftungs-Angriff, bei dem das Modell darauf trainiert wird, auf bestimmte Auslöser in einer spezifischen Weise zu reagieren, während es sich sonst normal verhält.
​
Verzerrung: Systematische Fehler in den Ausgaben von KI-Modellen, die zu unfairen oder diskriminierenden Ergebnissen für bestimmte Gruppen oder in spezifischen Kontexten führen können.
​
Bias-Ausnutzung: Eine Angriffstechnik, die bekannte Verzerrungen in KI-Modellen ausnutzt, um Ausgaben oder Ergebnisse zu manipulieren.
​
Cedar: Amazons Richtliniensprache und -engine für fein granulare Zugriffserlaubnisse, die bei der Implementierung von ABAC für KI-Systeme verwendet wird.
​
Chain of Thought: Eine Technik zur Verbesserung des Denkvermögens in Sprachmodellen, indem Zwischenschritte des Denkprozesses erzeugt werden, bevor eine endgültige Antwort gegeben wird.
​
Schutzschalter: Mechanismen, die den Betrieb von KI-Systemen automatisch stoppen, wenn bestimmte Risikoschwellen überschritten werden.
​
Datenleck: Unbeabsichtigte Offenlegung sensibler Informationen durch AI-Modellausgaben oder -verhalten.
​
Datenvergiftung: Die absichtliche Manipulation von Trainingsdaten zur Beeinträchtigung der Modellintegrität, oft um Hintertüren einzubauen oder die Leistung zu verschlechtern.
​
Differenzielle Privatsphäre – Differenzielle Privatsphäre ist ein mathematisch fundierter Rahmen zur Veröffentlichung statistischer Informationen über Datensätze, wobei der Datenschutz einzelner Datenpersonen geschützt wird. Sie ermöglicht es einem Dateninhaber, aggregierte Muster der Gruppe zu teilen, während Informationen, die über einzelne Personen preisgegeben werden, eingeschränkt werden.
​
Embeddings: Dichte Vektor-Darstellungen von Daten (Text, Bilder usw.), die semantische Bedeutungen in einem hochdimensionalen Raum erfassen.
​
Erklärbarkeit – Erklärbarkeit in der KI ist die Fähigkeit eines KI-Systems, für seine Entscheidungen und Vorhersagen für Menschen verständliche Gründe anzugeben und Einblicke in seine internen Abläufe zu bieten.
​
Erklärbare KI (XAI): KI-Systeme, die darauf ausgelegt sind, durch verschiedene Techniken und Rahmenwerke menschlich verständliche Erklärungen für ihre Entscheidungen und Verhaltensweisen zu liefern.
​
Federated Learning: Ein maschinelles Lernverfahren, bei dem Modelle über mehrere dezentralisierte Geräte hinweg trainiert werden, die lokale Datensätze enthalten, ohne dass die Daten selbst ausgetauscht werden.
​
Guardrails: Einschränkungen, die implementiert werden, um zu verhindern, dass KI-Systeme schädliche, voreingenommene oder anderweitig unerwünschte Ausgaben erzeugen.
​
Halluzination – Eine AI-Halluzination bezieht sich auf ein Phänomen, bei dem ein KI-Modell falsche oder irreführende Informationen erzeugt, die nicht auf seinen Trainingsdaten oder der sachlichen Realität basieren.
​
Human-in-the-Loop (HITL): Systeme, die so konzipiert sind, dass sie menschliche Aufsicht, Verifikation oder Eingriffe an entscheidenden Entscheidungspunkten erfordern.
​
Infrastructure as Code (IaC): Verwaltung und Bereitstellung von Infrastruktur durch Code anstelle manueller Prozesse, was Sicherheitsscans und konsistente Bereitstellungen ermöglicht.
​
Jailbreak: Techniken, die verwendet werden, um Sicherheitsvorkehrungen in KI-Systemen, insbesondere in großen Sprachmodellen, zu umgehen und verbotene Inhalte zu erzeugen.
​
Minimalprinzip: Das Sicherheitsprinzip, nur die unbedingt erforderlichen Zugriffsrechte für Benutzer und Prozesse zu gewähren.
​
LIME (Local Interpretable Model-agnostic Explanations): Eine Technik zur Erklärung der Vorhersagen beliebiger maschineller Lernklassifikatoren, indem sie lokal durch ein interpretierbares Modell angenähert werden.
​
Mitgliedschafts-Rückschluss-Angriff: Ein Angriff, der darauf abzielt zu ermitteln, ob ein bestimmter Datenpunkt zum Training eines Machine-Learning-Modells verwendet wurde.
​
MITRE ATLAS: Adversarielle Bedrohungslandschaft für Künstliche-Intelligenz-Systeme; eine Wissensdatenbank für adversarielle Taktiken und Techniken gegen KI-Systeme.
​
Modellkarte – Eine Modellkarte ist ein Dokument, das standardisierte Informationen über die Leistung, Einschränkungen, beabsichtigte Verwendungen und ethische Überlegungen eines KI-Modells bereitstellt, um Transparenz und verantwortungsbewusste KI-Entwicklung zu fördern.
​
Modell-Extraktion: Ein Angriff, bei dem ein Angreifer ein Zielmodell wiederholt abfragt, um ohne Autorisierung eine funktional ähnliche Kopie zu erstellen.
​
Modellinversion: Ein Angriff, der versucht, Trainingsdaten durch Analyse der Modellausgaben zu rekonstruieren.
​
Modell-Lebenszyklus-Management – Das AI Modell-Lebenszyklus-Management ist der Prozess der Überwachung aller Phasen der Existenz eines KI-Modells, einschließlich dessen Entwurf, Entwicklung, Einsatz, Überwachung, Wartung und schließlich Ausmusterung, um sicherzustellen, dass es effektiv bleibt und mit den Zielen übereinstimmt.
​
Modellvergiftung: Das Einführen von Schwachstellen oder Hintertüren direkt in ein Modell während des Trainingsprozesses.
​
Modellraub/-diebstahl: Extrahieren einer Kopie oder Annäherung eines proprietären Modells durch wiederholte Abfragen.
​
Multi-Agenten-System: Ein System, das aus mehreren interagierenden KI-Agenten besteht, von denen jeder potenziell unterschiedliche Fähigkeiten und Ziele hat.
​
OPA (Open Policy Agent): Eine Open-Source-Policy-Engine, die eine einheitliche Durchsetzung von Richtlinien über den gesamten Stack hinweg ermöglicht.
​
Datenschutzbewahrendes Maschinelles Lernen (PPML): Techniken und Methoden zum Trainieren und Bereitstellen von ML-Modellen unter Wahrung der Privatsphäre der Trainingsdaten.
​
Prompt Injection: Ein Angriff, bei dem bösartige Anweisungen in Eingaben eingebettet werden, um das beabsichtigte Verhalten eines Modells zu überschreiben.
​
RAG (Retrieval-Augmented Generation): Eine Technik, die große Sprachmodelle verbessert, indem sie vor der Generierung einer Antwort relevante Informationen aus externen Wissensquellen abruft.
​
Red-Teaming: Die Praxis, KI-Systeme aktiv zu testen, indem simulierte Angriffe durch Gegner durchgeführt werden, um Schwachstellen zu identifizieren.
​
SBOM (Software Bill of Materials): Ein formeller Nachweis, der die Details und Lieferkettenbeziehungen verschiedener Komponenten enthält, die beim Erstellen von Software oder KI-Modellen verwendet werden.
​
SHAP (SHapley Additive exPlanations): Ein spieltheoretischer Ansatz zur Erklärung der Ausgabe eines beliebigen Machine-Learning-Modells durch Berechnung des Beitrags jeder Funktion zur Vorhersage.
​
Lieferkettenangriff: Kompromittierung eines Systems durch das Anvisieren weniger sicherer Elemente in seiner Lieferkette, wie Drittanbieter-Bibliotheken, Datensätze oder vortrainierte Modelle.
​
Transfer Learning: Eine Technik, bei der ein für eine Aufgabe entwickeltes Modell als Ausgangspunkt für ein Modell für eine zweite Aufgabe wiederverwendet wird.
​
Vektor-Datenbank: Eine spezialisierte Datenbank, die entwickelt wurde, um hochdimensionale Vektoren (Embeddings) zu speichern und effiziente Ähnlichkeitssuchen durchzuführen.
​
Schwachstellen-Scan: Automatisierte Werkzeuge, die bekannte Sicherheitslücken in Softwarekomponenten, einschließlich KI-Frameworks und Abhängigkeiten, identifizieren.
​
Wasserzeichen: Techniken zum Einbetten von kaum wahrnehmbaren Markierungen in KI-generierte Inhalte, um deren Ursprung zu verfolgen oder KI-Generierung zu erkennen.
​
Zero-Day-Schwachstelle: Eine zuvor unbekannte Schwachstelle, die Angreifer ausnutzen können, bevor Entwickler einen Patch erstellen und bereitstellen.

## Anhang B: Referenzen

### TODO

## Anhang C: KI-Sicherheitssteuerung und Dokumentation

### Zielsetzung

Dieser Anhang liefert grundlegende Anforderungen zur Einrichtung von Organisationsstrukturen, Richtlinien und Prozessen zur Steuerung der KI-Sicherheit im gesamten Systemlebenszyklus.

---

### AC.1 Übernahme des AI-Risikomanagement-Rahmenwerks

Bieten Sie einen formalen Rahmen zur Identifizierung, Bewertung und Minderung von KI-spezifischen Risiken während des gesamten Systemlebenszyklus.

 #AC.1.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass eine KI-spezifische Risikobewertungsmethodik dokumentiert und implementiert ist.
 #AC.1.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Risikoabschätzungen an wichtigen Punkten im KI-Lebenszyklus und vor wesentlichen Änderungen durchgeführt werden.
 #AC.1.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass der Risikomanagementrahmen mit etablierten Standards (z. B. NIST AI RMF) übereinstimmt.

---

### AC.2 KI-Sicherheitsrichtlinien & -verfahren

Definieren und Durchsetzen von organisatorischen Standards für die sichere Entwicklung, Bereitstellung und den Betrieb von KI.

 #AC.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob dokumentierte KI-Sicherheitsrichtlinien existieren.
 #AC.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtlinien mindestens jährlich und nach erheblichen Änderungen der Bedrohungslandschaft überprüft und aktualisiert werden.
 #AC.2.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Richtlinien alle AISVS-Kategorien und anwendbaren regulatorischen Anforderungen abdecken.

---

### AC.3 Rollen und Verantwortlichkeiten für KI-Sicherheit

Schaffen Sie klare Verantwortlichkeiten für die KI-Sicherheit in der gesamten Organisation.

 #AC.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Rollen und Verantwortlichkeiten im Bereich der KI-Sicherheit dokumentiert sind.
 #AC.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass verantwortliche Personen über entsprechende Sicherheitsexpertise verfügen.
 #AC.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für KI-Systeme mit hohem Risiko ein Ethikkomitee für KI oder ein Governance-Gremium eingerichtet ist.

---

### AC.4 Durchsetzung ethischer KI-Richtlinien

Sicherstellen, dass KI-Systeme gemäß den etablierten ethischen Grundsätzen arbeiten.

 #AC.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ethische Richtlinien für die Entwicklung und den Einsatz von KI vorhanden sind.
 #AC.4.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um ethische Verstöße zu erkennen und zu melden.
 #AC.4.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass regelmäßige ethische Überprüfungen der eingesetzten KI-Systeme durchgeführt werden.

---

### AC.5 Überwachung der Einhaltung von KI-Vorschriften

Behalten Sie das Bewusstsein für und die Einhaltung sich entwickelnder KI-Vorschriften bei.

 #AC.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Prozesse existieren, um anwendbare KI-Vorschriften zu identifizieren.
 #AC.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Einhaltung aller regulatorischen Anforderungen bewertet wird.
 #AC.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass regulatorische Änderungen rechtzeitig Überprüfungen und Aktualisierungen von KI-Systemen auslösen.

### AC.6 Schulung von Datenverwaltung, Dokumentation und Prozess

 #1.1.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass nur Datensätze, die hinsichtlich Qualität, Repräsentativität, ethischer Beschaffung und Lizenzkonformität geprüft wurden, zugelassen werden, um Risiken von Datenmanipulation, eingebetteter Voreingenommenheit und Verletzung geistigen Eigentums zu verringern.
 #1.1.5    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Qualität der Beschriftung/Annotation durch gegenseitige Überprüfungen der Prüfer oder durch Konsens sichergestellt wird.
 #1.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass für bedeutende Trainingsdatensätze „Datenkarten“ oder „Datenblätter für Datensätze“ geführt werden, die Merkmale, Motivationen, Zusammensetzung, Erfassungsprozesse, Vorverarbeitung sowie empfohlene/abgeratene Verwendungszwecke detailliert beschreiben.
 #1.3.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass identifizierte Verzerrungen durch dokumentierte Strategien wie Neu-Balancierung, gezielte Datenaugmentation, algorithmische Anpassungen (z. B. Vorverarbeitung, Verarbeitung während des Lernens, Nachverarbeitungstechniken) oder Neu-Gewichtung gemindert werden und dass die Auswirkungen der Minderung sowohl auf die Fairness als auch auf die Gesamtleistung des Modells bewertet werden.
 #1.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Fairness-Metriken nach dem Training bewertet und dokumentiert werden.
 #1.3.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob eine Lifecycle-Bias-Management-Richtlinie Eigentümer und Überprüfungsrhythmus zuweist.
 #1.4.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch klare Richtlinien, gegenseitige Überprüfungen durch Gutachter, Konsensmechanismen (z. B. Überwachung der Übereinstimmung zwischen Annotatoren) und definierte Prozesse zur Lösung von Diskrepanzen gewährleistet ist.
 #1.4.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für sicherheits-, sicherheitsrelevante oder fairnesskritische Labels (z. B. zur Identifizierung toxischer Inhalte, kritischer medizinischer Befunde) eine verpflichtende unabhängige doppelte Überprüfung oder eine gleichwertige robuste Verifikation durchgeführt wird.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Kennzeichnungsrichtlinien und Anweisungen umfassend, versionskontrolliert und peer-reviewed sind.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Datenschemata für Labels klar definiert und versionskontrolliert sind.
 #1.3.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Datensätze hinsichtlich repräsentativer Ungleichgewichte und potenzieller Verzerrungen in Bezug auf gesetzlich geschützte Merkmale (z. B. Rasse, Geschlecht, Alter) sowie andere ethisch sensible Eigenschaften, die für den Anwendungsbereich des Modells relevant sind (z. B. sozioökonomischer Status, Standort), profiliert werden.
 #1.5.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass manuelle Stichprobenprüfungen durch Fachexperten eine statistisch signifikante Stichprobe abdecken (z. B. ≥1 % oder 1.000 Proben, je nachdem, welcher Wert größer ist, oder wie durch die Risikobewertung bestimmt), um subtile Qualitätsprobleme zu erkennen, die von der Automatisierung nicht erfasst werden.
 #1.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgelagerte oder über Crowdsourcing durchgeführte Kennzeichnungsabläufe technische/prozedurale Schutzmaßnahmen enthalten, um die Vertraulichkeit und Integrität der Daten sowie die Qualität der Labels zu gewährleisten und Datenlecks zu verhindern.
 #1.5.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Maßnahmen zur Behebung an Herkunftsaufzeichnungen angehängt werden.
 #1.6.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob markierte Proben vor dem Training eine manuelle Überprüfung auslösen.
 #1.6.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Ergebnisse den Sicherheitsdossier des Modells speisen und die fortlaufende Bedrohungsaufklärung informieren.
 #1.6.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Erkennungslogik mit neuen Bedrohungsinformationen aktualisiert wird.
 #1.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Online-Lern-Pipelines Verteilungsabweichungen überwachen.
 #1.7.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Workflows zur Löschung von Trainingsdaten sowohl Primär- als auch abgeleitete Daten löschen und bewerten Sie die Auswirkungen auf das Modell, sowie dass die Auswirkungen auf betroffene Modelle bewertet und gegebenenfalls adressiert werden (z. B. durch erneutes Training oder Neukalibrierung).
 #1.7.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um den Umfang und den Status der Nutzereinwilligung (und Widerrufe) für die in der Schulung verwendeten Daten zu verfolgen und zu respektieren, und dass die Einwilligung überprüft wird, bevor Daten in neue Schulungsprozesse oder bedeutende Modellaktualisierungen einfließen.
 #1.7.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Workflows jährlich getestet und protokolliert werden.
 #1.8.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Drittanbieter, einschließlich Anbieter von vortrainierten Modellen und externen Datensätzen, einer Due-Diligence-Prüfung in Bezug auf Sicherheit, Datenschutz, ethische Herkunft und Datenqualität unterzogen werden, bevor deren Daten oder Modelle integriert werden.
 #1.8.2    Level: 1    Rolle: D
 Überprüfen Sie, dass externe Übertragungen TLS/Authentifizierung und Integritätsprüfungen verwenden.
 #1.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Hochrisiko-Datenquellen (z. B. Open-Source-Datensätze mit unbekanntem Herkunftsnachweis, nicht geprüfte Anbieter) einer verstärkten Prüfung unterzogen werden, wie z. B. sandbox-basierte Analyse, umfangreiche Qualitäts-/Bias-Überprüfungen und gezielte Erkennung von Datenmanipulation, bevor sie in sensiblen Anwendungen verwendet werden.
 #1.8.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass vor dem Feintuning oder der Bereitstellung vortrainierte Modelle, die von Dritten stammen, auf eingebettete Vorurteile, potenzielle Hintertüren, die Integrität ihrer Architektur und die Herkunft ihrer ursprünglichen Trainingsdaten überprüft werden.
 #1.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass bei Verwendung von adversarial Training die Generierung, Verwaltung und Versionierung von adversarial Datensätzen dokumentiert und kontrolliert wird.
 #1.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Auswirkungen des Trainings zur adversarialen Robustheit auf die Modellleistung (sowohl bei sauberen als auch bei adversarialen Eingaben) und die Fairness-Metriken bewertet, dokumentiert und überwacht werden.
 #1.5.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Strategien für adversariales Training und Robustheit regelmäßig überprüft und aktualisiert werden, um sich entwickelnden Techniken adversarialer Angriffe entgegenzuwirken.
 #1.4.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass fehlgeschlagene Datensätze mit Prüfpfaden isoliert werden.
 #1.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Qualitätsprüfungen minderwertige Datensätze blockieren, es sei denn, Ausnahmen werden genehmigt.
 #1.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Erzeugungsprozess, die Parameter und der beabsichtigte Verwendungszweck von synthetischen Daten dokumentiert sind.
 #1.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass synthetische Daten vor der Verwendung im Training auf Risiken wie Verzerrungen, Datenschutzverletzungen und Repräsentationsprobleme bewertet werden.
 #1.12.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Warnungen für verdächtige Zugriffsereignisse generiert und umgehend untersucht werden.
 #1.13.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass für alle Trainingsdatensätze explizite Aufbewahrungsfristen definiert sind.
 #1.13.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Datensätze am Ende ihres Lebenszyklus automatisch ablaufen, gelöscht oder zur Löschung überprüft werden.
 #1.13.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Aufbewahrungs- und Löschaktionen protokolliert und prüfbar sind.
 #1.14.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Anforderungen an den Datenstandort und grenzüberschreitende Datenübertragungen für alle Datensätze identifiziert und durchgesetzt werden.
 #1.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass branchenspezifische Vorschriften (z. B. Gesundheitswesen, Finanzen) bei der Datenverarbeitung identifiziert und berücksichtigt werden.
 #1.14.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Einhaltung der relevanten Datenschutzgesetze (z. B. DSGVO, CCPA) dokumentiert und regelmäßig überprüft wird.
 #1.16.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um auf Anfragen von betroffenen Personen bezüglich Zugang, Berichtigung, Einschränkung oder Widerspruch zu reagieren.
 #1.16.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Anfragen innerhalb der gesetzlich vorgeschriebenen Fristen protokolliert, nachverfolgt und erfüllt werden.
 #1.16.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Prozesse für die Rechte der betroffenen Personen regelmäßig auf ihre Wirksamkeit getestet und überprüft werden.
 #1.17.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass eine Auswirkungsanalyse durchgeführt wird, bevor eine Datensatzversion aktualisiert oder ersetzt wird, die Modellleistung, Fairness und Compliance abdeckt.
 #1.17.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Auswirkungsanalyse dokumentiert und von den relevanten Interessengruppen überprüft werden.
 #1.17.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Rücksetzungspläne vorhanden sind, falls neue Versionen unakzeptable Risiken oder Rückschritte einführen.
 #1.18.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle an der Datenannotation beteiligten Mitarbeiter einer Hintergrundüberprüfung unterzogen und in Datensicherheit und Datenschutz geschult sind.
 #1.18.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Annotation-Mitarbeiter Vertraulichkeits- und Geheimhaltungsvereinbarungen unterschreiben.
 #1.18.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Annotationsplattformen Zugriffskontrollen durchsetzen und auf Insider-Bedrohungen überwachen.

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anhang D: KI-unterstützte Governance und Verifikation für sicheres Codieren

### Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-unterstützten Codierungstools während der Softwareentwicklung und gewährleistet Sicherheit und Rückverfolgbarkeit im gesamten Softwareentwicklungslebenszyklus (SDLC).

---

### AD.1 KI-unterstützter sicherer Programmier-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Softwareentwicklungszyklus (SSDLC) der Organisation, ohne die bestehenden Sicherheitsbarrieren zu schwächen.

 #AD.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein dokumentierter Arbeitsablauf beschreibt, wann und wie KI-Tools Code generieren, refaktorisieren oder überprüfen dürfen.
 #AD.1.2    Level: 2    Rolle: D
 Überprüfen Sie, ob der Workflow jeder SSDLC-Phase (Design, Implementierung, Code-Review, Test, Bereitstellung) zugeordnet ist.
 #AD.1.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Metriken (z. B. Verwundbarkeitsdichte, mittlere Erkennungszeit) für KI-erstellten Code erfasst und mit menschlichen Ausgangswerten verglichen werden.

---

### AD.2 KI-Werkzeugqualifizierung & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

 #AD.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Tool Missbrauch, Modellinversion, Datenleck und Abhängigkeitskettenrisiken identifiziert.
 #AD.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Toolbewertungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen.
 #AD.2.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.

---

### AD.3 Sicheres Prompt- und Kontextmanagement

Verhindern Sie das Lecken von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Aufforderungen oder Kontexten für KI-Modelle.

 #AD.3.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass schriftliche Anweisungen das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen verbieten.
 #AD.3.2    Level: 2    Rolle: D
 Überprüfen Sie, dass technische Kontrollen (clientseitige Redaktion, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.
 #AD.3.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen der Datenklassifizierungspolitik entsprechen.

---

### AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von durch KI-Ergebnisse eingeführten Schwachstellen, bevor der Code zusammengeführt oder bereitgestellt wird.

 #AD.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass von KI generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.
 #AD.4.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und Zusammenführungen bei kritischen Befunden blockieren.
 #AD.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Differential-Fuzz-Tests oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen nachweisen (z. B. Eingabevalidierung, Autorisierungslogik).

---

### AD.5 Erklärbarkeit & Nachverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblick darin, warum eine Empfehlung gemacht wurde und wie sie sich entwickelt hat.

 #AD.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Prompt-/Antwortpaare mit Commit-IDs protokolliert werden.
 #AD.5.2    Level: 2    Rolle: D
 Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) anzeigen können, die eine Empfehlung unterstützen.
 #AD.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Design-Artefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien nach ISO/IEC 42001 zu erfüllen.

---

### AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie gleichzeitig negative Drift.

 #AD.6.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen verfolgt werden.
 #AD.6.2    Level: 2    Rolle: D
 Verifizieren Sie, dass aggregiertes Feedback periodisch für Feinabstimmungen oder retrieval-unterstützte Generierung mit geprüften sicheren Codierungs-Korpora (z. B. OWASP Cheat Sheets) verwendet wird.
 #AD.6.3    Level: 3    Rolle: D/V
 Verifizieren Sie, dass ein Closed-Loop-Evaluations-Framework nach jeder Feinabstimmung Regressionstests durchführt; Sicherheitsmetriken müssen vor der Bereitstellung mindestens die vorherigen Basiswerte erreichen oder übertreffen.

---

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Anhang E: Beispielwerkzeuge und -frameworks

### Zielsetzung

Dieses Kapitel enthält Beispiele für Werkzeuge und Frameworks, die die Implementierung oder Erfüllung einer bestimmten AISVS-Anforderung unterstützen können. Diese sind nicht als Empfehlungen oder Befürwortungen durch das AISVS-Team oder das OWASP GenAI Security Project zu verstehen.

---

### AE.1 Verwaltung von Trainingsdaten und Bias-Management

Werkzeuge für Datenanalyse, Governance und Bias-Management.

 #AE.1.1    Abschnitt: 1.1
 Datenbestandsverwaltungstools: Werkzeuge zur Verwaltung von Datenbeständen wie...
 #AE.1.2    Abschnitt: 1.2
 Verschlüsselung während der Übertragung Verwenden Sie TLS für HTTPS-basierte Anwendungen, mit Tools wie openSSL und Pythons`ssl`Bibliothek.

---

### AE.2 Benutzereingabevalidierung

Werkzeuge zur Verarbeitung und Validierung von Benutzereingaben.

 #AE.2.1    Abschnitt: 2.1
 Werkzeuge zur Abwehr von Prompt-Injection: Verwenden Sie Guardrail-Werkzeuge wie NVIDIA's NeMo oder Guardrails AI.

---

