## Frontispiz

### Über den Standard

Der Artificial Intelligence Security Verification Standard (AISVS) ist ein gemeinschaftlich entwickelter Katalog von Sicherheitsanforderungen, den Data Scientists, MLOps-Ingenieure, Softwarearchitekten, Entwickler, Tester, Sicherheitsexperten, Tool-Anbieter, Regulierungsbehörden und Anwender nutzen können, um vertrauenswürdige KI-gestützte Systeme und Anwendungen zu entwerfen, zu entwickeln, zu testen und zu verifizieren. Er bietet eine gemeinsame Sprache zur Spezifikation von Sicherheitskontrollen über den gesamten KI-Lebenszyklus hinweg – von der Datenerfassung und Modellentwicklung bis hin zur Bereitstellung und laufenden Überwachung – sodass Organisationen die Widerstandsfähigkeit, Privatsphäre und Sicherheit ihrer KI-Lösungen messen und verbessern können.

### Urheberrecht und Lizenz

Version 0.1 (Erster öffentlicher Entwurf - In Bearbeitung), 2025  

![license](images/license.png)
Copyright © 2025 Das AISVS-Projekt.  

Veröffentlicht unter derCreative Commons Attribution‑ShareAlike 4.0 International License.
Für jegliche Wiederverwendung oder Verbreitung müssen Sie die Lizenzbedingungen dieses Werkes klar an andere kommunizieren.

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

AISVS ist ein brandneuer Standard, der speziell entwickelt wurde, um die einzigartigen Sicherheitsherausforderungen von künstlichen Intelligenzsystemen zu adressieren. Während er sich von allgemeinen bewährten Sicherheitspraktiken inspirieren lässt, wurde jede Anforderung in AISVS von Grund auf entwickelt, um die Bedrohungslandschaft im Bereich der KI widerzuspiegeln und Organisationen dabei zu unterstützen, sicherere und widerstandsfähigere KI-Lösungen zu entwickeln.

## Vorwort

Willkommen zum Artificial Intelligence Security Verification Standard (AISVS) Version 1.0!

### Einführung

AISVS wurde 2025 durch eine gemeinschaftliche Zusammenarbeit gegründet und definiert die Sicherheitsanforderungen, die bei der Gestaltung, Entwicklung, Bereitstellung und dem Betrieb moderner KI-Modelle, Pipelines und KI-gestützter Dienste berücksichtigt werden müssen.

AISVS v1.0 stellt die gemeinsame Arbeit seiner Projektleiter, der Arbeitsgruppe und der weiteren Community-Beiträge dar, um eine pragmatische, testbare Basis für die Absicherung von KI-Systemen zu schaffen.

Unser Ziel mit dieser Veröffentlichung ist es, AISVS leicht verständlich und anwendbar zu machen, dabei jedoch strikt auf den definierten Umfang fokussiert zu bleiben und die sich schnell entwickelnde, einzigartige Risikolandschaft im Bereich der KI zu adressieren.

### Hauptziele für AISVS Version 1.0

Version 1.0 wird nach mehreren Leitprinzipien erstellt.

#### Gut definierter Umfang

Jede Anforderung muss mit dem Namen und der Mission von AISVS übereinstimmen:

Künstliche Intelligenz – Die Kontrollen arbeiten auf der AI/ML-Ebene (Daten, Modell, Pipeline oder Inferenz) und liegen in der Verantwortung der KI-Fachleute.
Sicherheit – Anforderungen mindern direkt identifizierte Sicherheits-, Datenschutz- oder Sicherheitsrisiken.
Verifikation – Die Sprache ist so geschrieben, dass die Konformität objektiv überprüfbar ist.
Standard – Abschnitte folgen einer konsistenten Struktur und Terminologie, um eine kohärente Referenz zu bilden.
​
---

Durch die Befolgung von AISVS können Organisationen systematisch die Sicherheitslage ihrer KI-Lösungen bewerten und stärken und so eine Kultur der sicheren KI-Entwicklung fördern.

## Verwendung des AISVS

Der Artificial Intelligence Security Verification Standard (AISVS) definiert Sicherheitsanforderungen für moderne KI-Anwendungen und -Dienste mit Fokus auf Aspekte, die unter der Kontrolle der Anwendungsentwickler liegen.

Das AISVS richtet sich an alle, die die Sicherheit von KI-Anwendungen entwickeln oder bewerten, einschließlich Entwicklern, Architekten, Sicherheitsingenieuren und Prüfern. Dieses Kapitel stellt die Struktur und die Verwendung des AISVS vor, einschließlich seiner Verifikationsstufen und vorgesehenen Anwendungsfälle.

### Sicherheitsüberprüfungsstufen für Künstliche Intelligenz

Das AISVS definiert drei aufsteigende Stufen der Sicherheitsüberprüfung. Jede Stufe fügt Tiefe und Komplexität hinzu, wodurch Organisationen ihre Sicherheitsstrategie an das Risikoniveau ihrer KI-Systeme anpassen können.

Organisationen können auf Level 1 beginnen und mit zunehmender Sicherheitsreife und Bedrohungsaussetzung schrittweise höhere Level übernehmen.

#### Definition der Ebenen

Jede Anforderung in AISVS v1.0 wird einer der folgenden Stufen zugeordnet:

 Anforderungen der Stufe 1

Level 1 umfasst die kritischsten und grundlegendsten Sicherheitsanforderungen. Diese konzentrieren sich darauf, häufige Angriffe zu verhindern, die nicht von anderen Voraussetzungen oder Schwachstellen abhängen. Die meisten Kontrollen auf Level 1 sind entweder einfach umzusetzen oder so wichtig, dass der Aufwand gerechtfertigt ist.

 Anforderungen der Stufe 2

Level 2 behandelt fortgeschrittenere oder weniger verbreitete Angriffe sowie mehrschichtige Verteidigungen gegen weitverbreitete Bedrohungen. Diese Anforderungen können komplexere Logik enthalten oder spezifische Angriffsvoraussetzungen ansprechen.

 Level 3 Anforderungen

Level 3 umfasst Kontrollen, die typischerweise schwerer umzusetzen oder situationsabhängig anwendbar sind. Diese stellen häufig Verteidigungsmechanismen in der Tiefe oder Gegenmaßnahmen gegen spezielle, zielgerichtete oder hochkomplexe Angriffe dar.

#### Rolle (D/V)

Jede AISVS-Anforderung ist entsprechend dem Hauptpublikum gekennzeichnet:

D – Entwicklerorientierte Anforderungen
V – Anforderungen mit Fokus auf Prüfer/Auditor
D/V – Relevant für sowohl Entwickler als auch Prüfer

## C1 Trainingsdatenverwaltung & Bias-Management

### Kontrollziel

Trainingsdaten müssen so beschafft, verarbeitet und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness gewährleistet sind. Dies erfüllt rechtliche Pflichten und verringert das Risiko von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinträchtigen könnten.

---

### C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

 #1.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Herkunft, Verantwortlicher/Eigentümer, Lizenz, Erhebungsmethode, Verwendungsbeschränkungen und Verarbeitungshistorie) geführt wird.
 #1.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Trainingsdatenprozesse unnötige Merkmale, Attribute oder Felder ausschließen (z. B. ungenutzte Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).
 #1.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Änderungen am Datensatz einem protokollierten Genehmigungsworkflow unterliegen.
 #1.1.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Datensätze oder Datensatzuntergruppen dort, wo es möglich ist, mit Wasserzeichen oder Fingerabdrücken versehen sind.

---

### C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und prüfen Sie ihre Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

 #1.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Zugriffskontrollen die Speicherung und Pipelines der Trainingsdaten schützen.
 #1.2.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass jeder Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeit und Aktion.
 #1.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand mit branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungsmethoden verschlüsselt sind.
 #1.2.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten sicherzustellen.
 #1.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisierte Erkennungstechniken angewendet werden, um unbefugte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.
 #1.2.6    Level: 2    Rolle: D/V
 Verifizieren Sie, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.
 #1.2.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Versionen des Trainingsdatensatzes eindeutig identifiziert, unveränderlich gespeichert und prüfbar sind, um eine Rücksetzung und forensische Analysen zu unterstützen.

---

### C1.3 Qualität, Integrität und Sicherheit der Trainingsdatenkennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

 #1.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität sicherzustellen.
 #1.3.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Beschriftungsschnittstellen und -plattformen starke Zugriffskontrollen durchsetzen, manipulationssichere Audit-Protokolle aller Beschriftungsaktivitäten führen und Schutz vor unbefugten Änderungen bieten.
 #1.3.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch während der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.

---

### C1.4 Qualität der Trainingsdaten und Sicherheitsgarantie

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebungen, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

 #1.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests Formatfehler und Nullwerte bei jeder Datenaufnahme oder bedeutenden Datenumwandlung erfassen.
 #1.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Datenvergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Einbettungsanalyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügen von Backdoor-Auslösern, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren.
 #1.4.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass geeignete Schutzmaßnahmen wie adversariales Training (unter Verwendung erzeugter adversarialer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und basierend auf der Risikobewertung für relevante Modelle abgestimmt sind.
 #1.4.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisch generierte Labels (z. B. durch LLMs oder schwache Überwachung) Konfidenzschwellen und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Konfidenz zu erkennen.
 #1.4.5    Level: 3    Rolle: D
 Verifizieren Sie, dass automatisierte Tests bei jeder Datenaufnahme oder jeder signifikanten Datenumwandlung Label-Skews erkennen.

---

### C1.5 Datenherkunft und Nachverfolgbarkeit

Verfolgen Sie den vollständigen Weg jedes einzelnen Datenpunkts vom Ursprung bis zur Modelleingabe für Nachvollziehbarkeit und Vorfallreaktion.

 #1.5.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Ursprung jedes Datenpunkts, einschließlich aller Transformationen, Erweiterungen und Zusammenführungen, dokumentiert ist und rekonstruiert werden kann.
 #1.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.
 #1.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Nachverfolgung der Herkunft synthetischer Daten, die mittels datenschutzschützender oder generativer Techniken erzeugt wurden, abdeckt, und dass alle synthetischen Daten im gesamten Prozess klar gekennzeichnet und von realen Daten unterscheidbar sind.

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

Robuste Validierung von Benutzereingaben ist die erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten preisgeben oder das Modell zu unerlaubtem Verhalten lenken. Ohne dedizierte Filter und Anweisungshierarchien zeigen Untersuchungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, wirksam sein werden. Auch subtile adversariale Störangriffe – wie Homoglyphen-Tauschaktionen oder Leetspeak – können die Entscheidungen eines Modells unbemerkt verändern.

---

### C2.1 Schutz vor Prompt-Injektion

Prompt Injection ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und Durchsetzung der Befehlshierarchie.

 #2.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektion-Muster (Jailbreak-Schlüsselwörter, "ignore previous", Rollenspielketten, indirekte HTML/URL-Angriffe) überprüft werden.
 #2.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob das System eine Befehls-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überschreiben, selbst nach Erweiterung des Kontextfensters.
 #2.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass adversariale Evaluierungstests (z. B. Red Team "Many-Shot"-Prompts) vor jeder Veröffentlichung eines Modells oder Prompt-Templates durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Regressionen.
 #2.1.4    Level: 2    Rolle: D
 Verifizieren Sie, dass Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Parsing-Kontext bereinigt werden, bevor sie zum Hauptprompt hinzugefügt werden.
 #2.1.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifikationsmodelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.

---

### C2.2 Widerstandsfähigkeit gegen Adversarial-Beispiele

Modelle der natürlichen Sprachverarbeitung (NLP) sind nach wie vor anfällig für subtile Zeichen- oder Wortebenenstörungen, die Menschen oft übersehen, die von Modellen jedoch häufig falsch klassifiziert werden.

 #2.2.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass grundlegende Schritte der Eingabenormalisierung (Unicode NFC, Homoglyphenabbildung, Abschneiden von Leerzeichen) vor der Tokenisierung ausgeführt werden.
 #2.2.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßigen Wiederholungen von Token oder abnormen Einbettungsdistanzen kennzeichnet.
 #2.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die Inferenzpipeline optionale, adversarial-trainingsgehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für Hochrisiko-Endpunkte unterstützt.
 #2.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass vermutete feindliche Eingaben isoliert, mit vollständigen Payloads (nach der PII-Redaktion) protokolliert werden.
 #2.2.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen eine Freigabesperre auslösen.

---

### C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Prompt-Überläufe zwischen Feldern und Ressourcenerschöpfung verursachen. Eine strikte Schemaüberprüfung ist zudem Voraussetzung für die Durchführung deterministischer Tool-Aufrufe.

 #2.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabe-Schema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Zusammenstellung der Eingabeaufforderung validiert werden.
 #2.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einer sicheren Fehlermeldung abgelehnt werden und niemals stillschweigend abgeschnitten werden.
 #2.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.
 #2.3.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.
 #2.3.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Validierungsfehler mit redigierten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitsanalyse zu unterstützen.

---

### C2.4 Inhalts- und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Eingabeaufforderungen zu erkennen, die unerlaubte Inhalte anfordern (wie zum Beispiel illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text) und deren Verbreitung zu verhindern.

 #2.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten.
 #2.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.
 #2.4.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Screening-Modell oder die Regelmenge mindestens vierteljährlich neu trainiert/aktualisiert wird, wobei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster einbezogen werden.
 #2.4.4    Level: 2    Rolle: D
 Überprüfen Sie, dass das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Beschränkungen) durch attributbasierte Regeln, die zur Anforderungszeit aufgelöst werden, einhält.
 #2.4.5    Level: 3    Rolle: V
 Verifizieren Sie, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für SOC-Korrelation und zukünftige Red-Team-Wiedergaben enthalten.

---

### C2.5 Eingabebeschränkung der Datenrate und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

 #2.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob pro Benutzer, pro IP und pro API-Schlüssel Ratenbegrenzungen für alle Eingabeendpunkte durchgesetzt werden.
 #2.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Burst- und Dauer-Drosselungsgrenzen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.
 #2.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Rapid-Fire-Anfragen, Input-Fluten) automatisierte Sperren oder Eskalationen auslösen.
 #2.5.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und auf neue Angriffsmuster überprüft werden.

---

### C2.6 Multi-modale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

 #2.6.1    Level: 1    Rolle: D
 Vergewissern Sie sich, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden.
 #2.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganografische Nutzlasten gescannt werden.
 #2.6.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Bild- und Audioeingaben auf adversariale Störungen oder bekannte Angriffsmuster überprüft werden.
 #2.6.4    Level: 3    Rolle: V
 Überprüfen Sie, ob Fehler bei der Validierung multimodaler Eingaben protokolliert werden und Alarme zur Untersuchung auslösen.

---

### C2.7 Eingabeherkunft & Attribution

KI-Systeme sollten Prüfungen, Missbrauchsverfolgung und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

 #2.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.
 #2.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und prüfbar sind.
 #2.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Überprüfung oder Blockierung unterzogen werden.

---

### C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsmuster anpassen und durch kompiliertes Musterabgleich Echtzeitschutz bieten.

 #2.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine leistungsstarke Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.
 #2.8.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Bedrohungserkennungssysteme separate Musterdatenbanken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) führen.
 #2.8.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass die adaptive Bedrohungserkennung Machine-Learning-Modelle einbezieht, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.
 #2.8.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Bedrohungsinformationsquellen die Musterdatenbanken automatisch mit neuen Angriffssignaturen und IOCs (Indicators of Compromise) aktualisieren.
 #2.8.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Fehlalarmraten bei der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Interferenzen bei legitimen Anwendungsfällen zu minimieren.
 #2.8.6    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die kontextuelle Bedrohungsanalyse die Eingabequelle, das Benutzerverhalten und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.
 #2.8.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen zur Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.

---

### C2.9 Multi-modale Sicherheitsvalidierungs-Pipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcenisolierung bereitstellen.

 #2.9.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellen verfügt.
 #2.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die spezifisch für jeden Modalitätstyp sind und in den Sicherheitsrichtlinien dokumentiert sind.
 #2.9.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass die Erkennung von cross-modal Angriffen koordinierte Angriffe über mehrere Eingabetypen hinweg identifiziert (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektionen im Text) durch Korrelationsregeln und die Generierung von Warnmeldungen.
 #2.9.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass bei multi-modalem Validierungsfehlern eine detaillierte Protokollierung ausgelöst wird, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungswerte und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst.
 #2.9.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass modalitätsspezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, gegnerischen Beispielen und Leistungsbenchmarks, die über den Basisschwellenwerten liegen, aktualisiert werden.

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

## C3 Modell-Lebenszyklusmanagement & Änderungssteuerung

### Kontrollziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerbetriebnahme – und ermöglicht eine schnelle Reaktion auf Vorfälle sowie die Aufrechterhaltung der Verantwortlichkeit für alle Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

### C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit überprüfter Integrität gelangen in Produktionsumgebungen.

 #3.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptografisch von autorisierten Stellen signiert sind.
 #3.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.
 #3.1.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass die Modellherkunftsdaten die Identität der autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstest-Ergebnisse mit Bestehens-/Nichtbestehens-Status und einen Erstellungszeitstempel enthalten.
 #3.1.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass alle Modellartefakte semantische Versionsnummern (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.
 #3.1.5    Level: 2    Rolle: V
 Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar pflegt, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.

---

### C3.2 Modellvalidierung & Testen

Modelle müssen definierte Sicherheits- und Schutzvalidierungen vor der Bereitstellung bestehen.

 #3.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsbewertungen mit vorab festgelegten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen.
 #3.2.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Validierungsfehler die Modellbereitstellung automatisch blockieren, nachdem eine ausdrückliche Ausnahmegenehmigung von vorab benannten autorisierten Personen mit dokumentierten geschäftlichen Begründungen vorliegt.
 #3.2.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash, der validiert wird, verknüpft sind.
 #3.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung einer vorab benannten Sicherheitsbehörde innerhalb vorab vereinbarter Zeitrahmen erfordern.

---

### C3.3 Kontrollierte Bereitstellung & Rückrollung

Modelbereitstellungen müssen kontrolliert, überwacht und reversibel sein.

 #3.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Produktionseinsätze schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern basierend auf vorher vereinbarten Fehlerraten, Latenzschwellenwerten oder Sicherheitsalarmkriterien implementieren.
 #3.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Rückrollfunktionen den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.
 #3.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und die Bereitstellung bei jeglicher Abweichung fehlschlägt.
 #3.3.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Notabschaltfunktionen für Modelle Modellendpunkte innerhalb vordefinierter Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltvorrichtungen deaktivieren können.
 #3.3.5    Level: 2    Rolle: V
 Stellen Sie sicher, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderlichem Speicher für die Vorfallreaktion aufbewahrt werden.

---

### C3.4 Änderung der Verantwortlichkeit & Prüfung

Alle Änderungen am Modelllebenszyklus müssen nachvollziehbar und prüfbar sein.

 #3.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Außerdienststellung) unveränderliche Prüfprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteur-Identität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.
 #3.4.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf das Auditprotokoll eine geeignete Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.
 #3.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Aufforderungsvorlagen und Systemmeldungen in Git-Repositories versionskontrolliert sind und vor der Bereitstellung eine obligatorische Codeüberprüfung und Genehmigung durch festgelegte Prüfer erfolgt.
 #3.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Prüfprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen.

---

### C3.5 Sichere Entwicklungsmethoden

Modellentwicklungs- und Trainingsprozesse müssen sicheren Praktiken folgen, um eine Kompromittierung zu verhindern.

 #3.5.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Umgebungen für Modellentwicklung, -test und -produktion physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.
 #3.5.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.
 #3.5.3    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachweiskette authentifiziert werden.
 #3.5.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Entwicklungsartefakte des Modells (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert sind und vor der Verwendung im Training eine Peer-Review-Freigabe erforderlich ist.

---

### C3.6 Modell-Pensionierung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

 #3.6.1    Level: 1    Rolle: D
 Überprüfen Sie, dass die Model-Rentierungsprozesse automatisch Abhängigkeitsgraphen scannen, alle konsumierenden Systeme identifizieren und vor der Stilllegung vorab vereinbarte Vorankündigungsfristen einhalten.
 #3.6.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass archivierte Modellartefakte gemäß den dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptographische Löschung oder mehrfaches Überschreiben gelöscht werden, wobei verifizierte Vernichtungszertifikate vorliegen.
 #3.6.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Ereignisse zur Stilllegung von Modellen mit Zeitstempel und Akteur-Identität protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.
 #3.6.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Notfall-Modelldeaktivierung den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiträume durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.

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

## C4 Infrastruktur, Konfiguration & Bereitstellungssicherheit

### Kontrollziel

Die KI-Infrastruktur muss gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassendes Monitoring gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und Konfigurationen gelangen über kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptographisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen über automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfpfade aufrechterhalten, in die Produktion.

---

### C4.1 Laufzeitumgebungsisolation

Verhindern Sie Container-Ausbrüche und Privilegieneskalationen durch kernelbasierte Isolationsprimitive und zwingende Zugriffskontrollen.

 #4.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten, erforderlichen Fähigkeiten deaktivieren.
 #4.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vorab genehmigten Allowlisten, wobei Verstöße zur Beendigung des Containers und zur Generierung von Sicherheitswarnungen führen.
 #4.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.
 #4.1.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die eBPF-basierte Laufzeitüberwachung (Falco, Tetragon oder ein Äquivalent) Versuche zur Rechteerweiterung erkennt und automatisch die verursachenden Prozesse innerhalb der organisatorischen Reaktionszeitvorgaben beendet.
 #4.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass KI-Arbeitslasten mit hohem Risiko in hardwareisolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestationsüberprüfung ausgeführt werden.

---

### C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

 #4.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools wie tfsec, Checkov oder Terrascan gescannt wird und Merge-Vorgänge bei CRITICAL- oder HIGH-Schweregrad-Funden blockiert werden.
 #4.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Container-Builds mit identischen SHA256-Hashes über mehrere Builds hinweg reproduzierbar sind, und erzeugen Sie SLSA Level 3 Provenance-Attestierungen, die mit Sigstore signiert sind.
 #4.2.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und mit Cosign signiert sind, bevor sie in das Registry hochgeladen werden, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.
 #4.2.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob CI/CD-Pipelines OIDC-Tokens von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity mit Lebensdauern verwenden, die die Grenzwerte der organisatorischen Sicherheitsrichtlinien nicht überschreiten.
 #4.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenienz während des Bereitstellungsprozesses vor der Containerausführung validiert werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt.
 #4.2.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Build-Umgebungen in flüchtigen Containern oder VMs ohne persistenten Speicher und mit Netzwerkisolation von Produktions-VPCs ausgeführt werden.

---

### C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit Standard-Verweigerungsrichtlinien und verschlüsselter Kommunikation.

 #4.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Kubernetes NetworkPolicies oder eine gleichwertige Lösung ein Standard-Deny für Ingress/Egress mit expliziten Zulassungsregeln für erforderliche Ports (443, 8080 usw.) implementiert.
 #4.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.
 #4.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Whitelists gefiltert wird und blockierte Anfragen protokolliert werden.
 #4.3.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei Zertifikate gemäß der Organisationsrichtlinie rotiert werden und die Zertifikatsvalidierung durchgesetzt wird (keine Skip-Verify-Flags).
 #4.3.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und ausschließlich über NAT-Gateways oder Bastion Hosts kommuniziert.

---

### C4.4 Geheimnisse & Verwaltung kryptografischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

 #4.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert sind.
 #4.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) generiert werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.
 #4.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Rotation von Secrets automatisiert ist, mit einer Zero-Downtime-Bereitstellung und sofortiger Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.
 #4.4.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds mit API-Schlüsseln, Passwörtern oder Zertifikaten blockieren.
 #4.4.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Audit-Logs mit Benutzeridentitäten und Zeitstempeln protokolliert wird.
 #4.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, eingehängte Volumes oder Init-Container injiziert werden, und vergewissern Sie sich, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind.

---

### C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

 #4.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.
 #4.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert sind.
 #4.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalyse zur Erkennung von Hintertüren umfasst.
 #4.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden.
 #4.5.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Gold-Images mit vollständiger Bereinigung des Dateisystems und des Speichers neu erstellt werden.

---

### C4.6 Infrastruktur-Sicherheitsüberwachung

Die Infrastruktur kontinuierlich mit automatisierter Behebung und Echtzeit-Benachrichtigungen scannen und überwachen.

 #4.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITICAL-Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.
 #4.6.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen bei fehlgeschlagenen Prüfungen durchgeführt werden.
 #4.6.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Sicherheitslücken mit hoher Kritikalität gemäß den zeitlichen Vorgaben des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.
 #4.6.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung der CEF- oder STIX/TAXII-Formate mit automatischer Anreicherung integriert sind.
 #4.6.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Infrastrukturmetriken an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Managementberichten exportiert werden.
 #4.6.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Konfigurationsabweichungen gemäß den organisatorischen Überwachungsanforderungen mit Werkzeugen (Chef InSpec, AWS Config) erkannt werden und eine automatische Rücksetzung für unautorisierte Änderungen erfolgt.

---

### C4.7 KI-Infrastruktur Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

 #4.7.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass die GPU/TPU-Auslastung überwacht wird, wobei bei organisationsweit definierten Schwellenwerten Alarme ausgelöst und automatische Skalierung oder Lastenausgleich basierend auf Kapazitätsmanagementrichtlinien aktiviert werden.
 #4.7.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob KI-Arbeitslastmetriken (Inferenzlatenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Infrastruktur-Auslastung korreliert werden.
 #4.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Kubernetes ResourceQuotas oder entsprechende Mechanismen einzelne Workloads gemäß den organisatorischen Ressourcenallokationsrichtlinien mit durchgesetzten harten Grenzwerten begrenzen.
 #4.7.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant erfasst, mit Warnmeldungen basierend auf den Budgetgrenzen der Organisation und automatisierten Kontrollen für Budgetüberschreitungen.
 #4.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfrage mustern erfolgt.
 #4.7.6    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Ressourcenerschöpfung gemäß den organisatorischen Reaktionsanforderungen Circuit Breaker auslöst, einschließlich der Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.

---

### C4.8 Umgebungstrennung & Förderkontrollen

Erzwingen Sie strenge Umgebungsgrenzen mit automatisierten Freigabe-Gates und Sicherheitsvalidierung.

 #4.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets betrieben werden, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.
 #4.8.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Förderung von Umgebungen die Genehmigung von organisatorisch definiertem autorisiertem Personal erfordert, mit kryptografischen Signaturen und unveränderbaren Prüfpfaden.
 #4.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Produktionsumgebungen den SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanforderungen mit organisatorischen Vorankündigungsanforderungen außer bei Notfällen erforderlich sind.
 #4.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Änderungen an der Infrastruktur als Code eine Peer-Review mit automatisierten Tests und Sicherheitsüberprüfungen erfordern, bevor sie in den Main-Branch zusammengeführt werden.
 #4.8.5    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert sind, synthetische Datengenerierung oder vollständige Datenmaskierung mit Entfernung von personenbezogenen Identifikationsmerkmalen (PII) verifiziert wurde.
 #4.8.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Beförderungstore automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, bei denen keine CRITICAL-Funde für die Genehmigung erforderlich sind.

---

### C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfähigkeiten.

 #4.9.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen in geografisch getrennte Regionen gesichert werden, unter Umsetzung der 3-2-1-Sicherungsstrategie.
 #4.9.2    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Backup-Systeme in isolierten Netzwerken mit separaten Zugangsdaten und luftgetrenntem Speicher zum Schutz vor Ransomware betrieben werden.
 #4.9.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit RTO- und RPO-Zielen, die den organisatorischen Anforderungen entsprechen, durch automatisierte Tests geprüft und validiert werden.
 #4.9.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit Wiederherstellung der Modellgewichte, Wiederaufbau des GPU-Clusters und Abbildung der Serviceabhängigkeiten umfasst.

---

### C4.10 Infrastruktur-Compliance & Governance

Erhalten Sie die Einhaltung von Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

 #4.10.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand von SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatisierter Erfassung von Nachweisen bewertet wird.
 #4.10.2    Level: 2    Rolle: V
 Verifizieren Sie, dass die Infrastrukturdokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die entsprechend den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.
 #4.10.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung mit regulatorischen Genehmigungsabläufen für risikoreiche Änderungen unterzogen werden.

---

### C4.11 KI-Hardware-Sicherheit

Sichern Sie AI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter AI-Beschleuniger.

 #4.11.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den zeitlichen Vorgaben des organisatorischen Patch-Managements aktualisiert wird.
 #4.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mittels TPM 2.0, Intel TXT oder AMD SVM überprüft wird.
 #4.11.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der GPU-Speicher zwischen den Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen Hardwarepartitionierung isoliert ist, wobei eine Speicherbereinigung zwischen den Aufgaben erfolgt.
 #4.11.4    Level: 3    Rolle: V
 Überprüfen Sie, ob die Lieferkette der KI-Hardware eine Herkunftsverifizierung mit Herstellerzertifikaten und eine Validierung der manipulationssicheren Verpackung umfasst.
 #4.11.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) die KI-Modellgewichte und kryptografischen Schlüssel mit FIPS 140-2 Level 3 oder Common Criteria EAL4+ Zertifizierung schützen.

---

### C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

 #4.12.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mithilfe von mutual TLS authentifizieren, wobei die Gerätezertifikate gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie regelmäßig ausgetauscht werden.
 #4.12.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und Rollback-Schutz implementieren, um Firmware-Downgrade-Angriffe zu verhindern.
 #4.12.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.
 #4.12.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfunktionen mit sicherer lokaler Speicherung umfasst.

---

### C4.13 Mehrfach-Cloud- und hybride Infrastruktur-Sicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybriden Cloud- und On-Premises-Bereitstellungen.

 #4.13.1    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.
 #4.13.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der plattformübergreifende Datentransfer eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet und dass Datenresidenzkontrollen je nach Rechtsgebiet durchgesetzt werden.
 #4.13.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlicher Überwachung und Alarmierung implementieren.
 #4.13.4    Level: 3    Rolle: V
 Überprüfen Sie, dass die Verhinderung von Anbieterbindung in der Cloud tragbare Infrastruktur-als-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungswerkzeugen umfasst.
 #4.13.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausweitung von Ressourcen als auch unautorisierte Gebühren für Datenübertragungen zwischen Clouds verhindern.

---

### C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Infrastrukturautomatisierungspipelines und GitOps-Workflows für das Management von KI-Infrastrukturen.

 #4.14.1    Level: 2    Rolle: D/V
 Überprüfen Sie, dass GitOps-Repositorys signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln vorhanden sind, die direkte Pushes zu den Haupt-Branches verhindern.
 #4.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Fehlerbehebung und Rückrollfunktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für unautorisierte Änderungen ausgelöst werden.
 #4.14.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die automatisierte Infrastrukturbereitstellung eine Sicherheitsrichtlinienvalidierung beinhaltet, die bei nicht konformen Konfigurationen den Einsatz blockiert.
 #4.14.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Geheimnisse der Infrastrukturautomatisierung durch externe Secret-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.
 #4.14.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die selbstheilende Infrastruktur die Korrelation von Sicherheitsereignissen mit automatisierter Vorfallreaktion und Workflows zur Benachrichtigung der Stakeholder umfasst.

---

### C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor mittels postquantischer Kryptographie und quantensicherer Protokolle.

 #4.15.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die KI-Infrastruktur NIST-zugelassene postquantum-kryptographische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für Schlüsselaustausch und digitale Signaturen implementiert.
 #4.15.2    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Quantenschlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikation mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.
 #4.15.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Agilitätsframeworks eine schnelle Migration zu neuen postquantenalgorithmen mit automatischer Zertifikats- und Schlüsselrotation ermöglichen.
 #4.15.4    Level: 3    Rolle: V
 Überprüfen Sie, ob die Quanten-Bedrohungsmodellierung die Anfälligkeit der KI-Infrastruktur für Quantenangriffe bewertet, mit dokumentierten Migrationszeitplänen und Risikobewertungen.
 #4.15.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsperiode mit Leistungsüberwachung eine Tiefenverteidigung bieten.

---

### C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe von hardwarebasierten vertrauenswürdigen Ausführungsumgebungen und Technologien für vertrauliches Rechnen.

 #4.16.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsprüfung ausgeführt werden.
 #4.16.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mit hardware-gestützter Speicher-Verschlüsselung isolieren.
 #4.16.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Remote-Attestation die Integrität der Enklave überprüft, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität der Ausführungsumgebung geladen werden.
 #4.16.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass vertrauliche KI-Inferenzdienste Modellextraktion durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.
 #4.16.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus der sicheren Enklave mit Fernattestierung und verschlüsselten Kommunikationskanälen verwaltet.
 #4.16.6    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Secure Multi-Party Computation (SMPC) kollaboratives KI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.

---

### C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

 #4.17.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings bestätigen, ohne Modellgewichte oder Trainingsdaten offenzulegen.
 #4.17.2    Level: 3    Rolle: D/V
 Überprüfen Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.
 #4.17.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderiertes KI ermöglichen, ohne einzelne Datensätze offenzulegen.
 #4.17.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Zero-Knowledge-Maschinenlern (ZKML)-Systeme überprüfbare KI-Schlüsse mit kryptografischem Nachweis korrekter Berechnungen ermöglichen.
 #4.17.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Batch-Verifikation und reduziertem Rechenaufwand bieten.

---

### C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Energie-, elektromagnetischen und cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

 #4.18.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die AI-Inferenzzeit mit Hilfe von Algorithmen konstanter Zeit und Padding normalisiert wird, um Timing-basierte Modell-Extraktionsangriffe zu verhindern.
 #4.18.2    Level: 3    Rolle: D/V
 Überprüfen Sie, dass der Schutz vor Leistungsanalyse Rauschinjektion, Stromlinienfilterung und zufällige Ausführungsmuster für KI-Hardware umfasst.
 #4.18.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die auf dem Cache basierende Seitenkanal-Minderung Cache-Partitionierung, Randomisierung und Flush-Befehle verwendet, um Informationslecks zu verhindern.
 #4.18.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.
 #4.18.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob mikroarchitekturelle Seitenkanalabwehrmaßnahmen spekulative Ausführungssteuerungen und Verschleierung von Speicherzugriffsmustern umfassen.

---

### C4.19 Neuromorphe & Spezialisierte KI-Hardware-Sicherheit

Sichern Sie aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

 #4.19.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sicherheit neuromorpher Chips Spike-Muster-Verschlüsselung, Schutz der synaptischen Gewichte und hardwarebasierte Validierung der Lernregel umfasst.
 #4.19.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Manipulationsschutzmechanismen und sicheres Konfigurationsladen mit authentifizierten Updates implementieren.
 #4.19.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root-of-Trust und sichere Schlüsselspeicherung mit Manipulationserkennung umfasst.
 #4.19.4    Level: 3    Rolle: D/V
 Verifizieren Sie, dass optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.
 #4.19.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung enthalten.

---

### C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzbewahrende Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

 #4.20.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen bei sensiblen KI-Workloads mit kryptographischer Integritätsprüfung und Leistungsüberwachung ermöglicht.
 #4.20.2    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Private Information Retrieval (PIR)-Systeme Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, durch kryptographischen Schutz der Zugriffs Muster.
 #4.20.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass sichere Multi-Party-Computing-Protokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.
 #4.20.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die datenschutzfreundliche Schlüsselverwaltung die verteilte Schlüsselerzeugung, Schwellenwert-Kryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.
 #4.20.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die leistungsfähige Verarbeitung mit Datenschutz durch Batch-Verarbeitung, Zwischenspeicherung und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien beibehalten werden.

---

### C4.15 Agent Framework Cloud-Integrationssicherheit & Hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises-/Cloud-Architekturen.

 #4.15.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Cloud-Speicherintegration End-to-End-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.
 #4.15.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitsgrenzen der Hybridbereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden.
 #4.15.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.
 #4.15.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Anforderungen an den Datenaufenthaltsort durch kryptografische Bestätigung der Speicherorte durchgesetzt werden.
 #4.15.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Sicherheitsbewertungen von Cloud-Anbietern agentspezifische Bedrohungsmodellierung und Risikoanalysen umfassen.

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

## C5 Zugriffskontrolle & Identität für KI-Komponenten & Nutzer

### Kontrollziel

Effektive Zugriffskontrolle für KI-Systeme erfordert ein robustes Identitätsmanagement, kontextabhängige Autorisierung und eine Laufzeitdurchsetzung nach Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten nur innerhalb ausdrücklich genehmigter Bereiche mit Modellen, Daten und Rechenressourcen interagieren, wobei eine kontinuierliche Überprüfung und Auditfähigkeit gewährleistet ist.

---

### C5.1 Identitätsmanagement & Authentifizierung

Erstellen Sie kryptografisch gesicherte Identitäten für alle Einheiten mit Multi-Faktor-Authentifizierung für privilegierte Operationen.

 #5.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle menschlichen Benutzer und Dienstprinzipale sich über einen zentralen unternehmensweiten Identitätsanbieter (IdP) mithilfe von OIDC-/SAML-Protokollen authentifizieren, wobei eindeutige Identitäts-zu-Token-Zuordnungen verwendet werden (keine geteilten Konten oder Anmeldeinformationen).
 #5.1.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass risikoreiche Operationen (Modelldeployment, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen der Produktionskonfiguration) eine Multi-Faktor-Authentifizierung oder eine Step-up-Authentifizierung mit Sitzungsnevalidierung erfordern.
 #5.1.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass neue Hauptbenutzer eine Identitätsprüfung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.
 #5.1.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Zugangskontrollen vierteljährlich durchgeführt werden, einschließlich automatischer Erkennung inaktiver Konten, Durchsetzung der Anmeldeinformationsrotation und De-Provisioning-Workflows.
 #5.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass föderierte KI-Agenten sich über signierte JWT-Assertions authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.

---

### C5.2 Ressourcenautorisierung & geringste Privilegien

Implementieren Sie fein abgestufte Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Prüfpfaden.

 #5.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Recheninstanzen) rollenbasierte Zugriffskontrollen mit expliziten Allow-Listen und Standard-Deny-Richtlinien durchsetzt.
 #5.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das Prinzip der geringsten Privilegien standardmäßig bei Dienstkonten durchgesetzt wird, beginnend mit schreibgeschützten Berechtigungen, und dass eine dokumentierte geschäftliche Rechtfertigung für Schreibzugriff erforderlich ist.
 #5.2.3    Level: 1    Rolle: V
 Verifizieren Sie, dass alle Änderungen an der Zugriffskontrolle mit genehmigten Änderungsanforderungen verknüpft sind und unveränderlich mit Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsdifferenzen protokolliert werden.
 #5.2.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Datenklassifizierungskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Embeddings, Prompt-Caches, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden.
 #5.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass unautorisierte Zugriffsversuche und Ereignisse zur Eskalation von Berechtigungen Echtzeitwarnungen mit kontextuellen Metadaten an SIEM-Systeme innerhalb von 5 Minuten auslösen.

---

### C5.3 Dynamische Richtlinienbewertung

Setzen Sie attributbasierte Zugriffssteuerungs- (ABAC-) Engines für kontextbewusste Autorisierungsentscheidungen mit Audit-Funktionalitäten ein.

 #5.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Autorisierungsentscheidungen an eine dedizierte Policy-Engine (OPA, Cedar oder gleichwertig) ausgelagert werden, die über authentifizierte APIs mit kryptographischem Integritätsschutz zugänglich ist.
 #5.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit bewerten, einschließlich Benutzerfreigabestufe, Sensitivitätsklassifizierung der Ressourcen, Anforderungskontext, Mandantentrennung und zeitliche Einschränkungen.
 #5.3.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, von Kollegen überprüft und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in der Produktion eingesetzt werden.
 #5.3.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Ergebnisse der Richtlinienbewertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übermittelt werden.
 #5.3.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Time-to-Live (TTL)-Werte des Richtlinien-Caches für hochsensible Ressourcen 5 Minuten und für Standardressourcen mit Cache-Invalidierungsfunktionen 1 Stunde nicht überschreiten.

---

### C5.4 Sicherheitsdurchsetzung zur Abfragezeit

Implementieren Sie Sicherheitskontrollen auf Datenbankebene mit verpflichtender Filterung und Zeilenebene-Sicherheitsrichtlinien.

 #5.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Vektordatenbank- und SQL-Abfragen obligatorische Sicherheitsfilter (Mandanten-ID, Sensitivitätskennzeichnungen, Benutzerbereich) enthalten, die auf der Ebene der Datenbank-Engine und nicht im Anwendungscode durchgesetzt werden.
 #5.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass zeilenbasierte Sicherheit (RLS)-Richtlinien und feldbasierte Maskierung mit Richtlinienvererbung für alle Vektor-Datenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.
 #5.4.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass fehlgeschlagene Autorisierungsbewertungen "Confused-Deputy-Angriffe" verhindern, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlercodes zurückgegeben werden, anstatt leere Ergebnismengen zurückzugeben.
 #5.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Auswertungsverzögerung der Richtlinie kontinuierlich überwacht wird und automatisierte Warnmeldungen für Zeitüberschreitungsbedingungen erfolgen, die eine Umgehung der Autorisierung ermöglichen könnten.
 #5.4.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Abfrage-Wiederholungsmechanismen die Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.

---

### C5.5 Ausgabe-Filterung & Verhinderung von Datenverlust

Setzen Sie Nachbearbeitungskontrollen ein, um eine unbefugte Datenfreigabe in KI-generierten Inhalten zu verhindern.

 #5.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Post-Inferenz-Filtermechanismen unautorisierte personenbezogene Daten (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer geliefert werden.
 #5.5.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Zitate, Verweise und Quellenangaben in Modellausgaben anhand der Berechtigungen des Aufrufers validiert werden, und entfernen Sie diese, wenn ein unbefugter Zugriff festgestellt wird.
 #5.5.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die Einschränkungen des Ausgabeformats (sichere PDFs, metadatenfreie Bilder, genehmigte Dateitypen) gemäß den Benutzerberechtigungsstufen und Datenklassifikationen durchgesetzt werden.
 #5.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch, versionskontrolliert sind und Prüfprotokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.
 #5.5.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Hochrisiko-Schwarzungen adaptive Protokolle erzeugen, die kryptografische Hashwerte des Originalinhalts für die forensische Wiederherstellung ohne Datenexposition enthalten.

---

### C5.6 Mehrmandanten-Isolierung

Sicherstellung kryptografischer und logischer Isolation zwischen Mandanten in gemeinsamer KI-Infrastruktur.

 #5.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Speicherbereiche, Einbettungsspeicher, Cache-Einträge und temporäre Dateien pro Mandant namespace-separiert sind und beim Löschen des Mandanten oder bei Beendigung der Sitzung sicher gelöscht werden.
 #5.6.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede API-Anfrage einen authentifizierten Mandantenbezeichner enthält, der kryptografisch gegen den Sitzungs kontext und die Benutzerberechtigungen validiert wird.
 #5.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Netzwerk-Richtlinien Default-Deny-Regeln für die Kommunikation zwischen Mandanten innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.
 #5.6.4    Level: 3    Rolle: D
 Überprüfen Sie, dass Verschlüsselungsschlüssel pro Mandant eindeutig sind, mit Unterstützung für kundengesteuerte Schlüssel (CMK) und kryptographischer Isolation zwischen den Mandantendatenspeichern.

---

### C5.7 Autonome Agentenautorisierung

Steuerung von Berechtigungen für KI-Agenten und autonome Systeme durch eingeschränkte Fähigkeits-Token und kontinuierliche Autorisierung.

 #5.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass autonome Agenten bereichsspezifische Berechtigungstoken erhalten, die ausdrücklich die erlaubten Aktionen, zugänglichen Ressourcen, zeitlichen Begrenzungen und betrieblichen Einschränkungen auflisten.
 #5.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass hochriskante Funktionen (Dateisystemzugriff, Codeausführung, externe API-Aufrufe, Finanztransaktionen) standardmäßig deaktiviert sind und eine explizite Autorisierung zur Aktivierung mit geschäftlichen Begründungen erfordern.
 #5.7.3    Level: 2    Rolle: D
 Überprüfen Sie, dass Fähigkeitstoken an Benutzersitzungen gebunden sind, eine kryptografische Integritätssicherung beinhalten und stellen Sie sicher, dass sie nicht offline gespeichert oder wiederverwendet werden können.
 #5.7.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass agenteninitiierte Aktionen einer sekundären Autorisierung durch die ABAC-Richtlinien-Engine mit vollständiger Kontextbewertung und Audit-Protokollierung unterzogen werden.
 #5.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Agentenfehlerbedingungen und Ausnahmebehandlungen Informationen zum Fähigkeitsumfang enthalten, um die Vorfallanalyse und forensische Untersuchung zu unterstützen.

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

KI-Lieferkettenangriffe nutzen Modelle, Frameworks oder Datensätze von Drittanbietern aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzuschleusen. Diese Kontrollen bieten eine durchgängige Herkunftsnachverfolgung, Schwachstellenmanagement und Überwachung, um den gesamten Modelllebenszyklus zu schützen.

---

### C6.1 Vorabprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie Herkunft, Lizenzen und verborgene Verhaltensweisen von Modellen Dritter, bevor Sie eine Feinabstimmung oder den Einsatz vornehmen.

 #6.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Drittanbieter-Modell-Artefakt einen signierten Herkunftsnachweis enthält, der das Quell-Repository und den Commit-Hash identifiziert.
 #6.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojaner-Auslöser gescannt werden.
 #6.1.3    Level: 2    Rolle: D
 Verifizieren Sie, dass Transfer-Learning-Feinabstimmungen die adversariale Bewertung bestehen, um verborgene Verhaltensweisen zu erkennen.
 #6.1.4    Level: 2    Rolle: V
 Überprüfen Sie, ob Modelllizenzen, Exportkontrollkennzeichnungen und Angaben zur Datenherkunft in einem ML-BOM-Eintrag aufgezeichnet sind.
 #6.1.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Hochrisikomodelle (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) weiterhin unter Quarantäne bleiben, bis eine menschliche Überprüfung und Freigabe erfolgt ist.

---

### C6.2 Framework- und Bibliotheksscanning

Kontinuierliche Überwachung von ML-Frameworks und -Bibliotheken auf CVEs und bösartigen Code, um den Laufzeit-Stack sicher zu halten.

 #6.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass CI-Pipelines Abhängigkeits-Scanner für KI-Frameworks und kritische Bibliotheken ausführen.
 #6.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob kritische Schwachstellen (CVSS ≥ 7,0) die Freigabe von Produktions-Images blockieren.
 #6.2.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass die statische Codeanalyse bei geforkten oder eingebundenen ML-Bibliotheken durchgeführt wird.
 #6.2.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Vorschläge für Framework-Upgrades eine Sicherheitsauswirkungsbewertung enthalten, die sich auf öffentliche CVE-Feeds bezieht.
 #6.2.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksladungen, die von der signierten SBOM abweichen, eine Warnung ausgeben.

---

### C6.3 Abhängigkeits-Pinning & Verifizierung

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationsfreie Artefakte zu gewährleisten.

 #6.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob alle Paketmanager Versionssperrungen über Lockfiles durchsetzen.
 #6.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass in Containerverweisen unveränderliche Digests anstelle von veränderlichen Tags verwendet werden.
 #6.3.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Prüfungen für reproduzierbare Builds Hashes über CI-Durchläufe hinweg vergleichen, um identische Ausgaben zu gewährleisten.
 #6.3.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Build-Atteste für 18 Monate zur Audit-Nachvollziehbarkeit gespeichert werden.
 #6.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um aktualisierte oder geforkte festgelegte Versionen zu erstellen.

---

### C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlauben Sie den Download von Artefakten nur von kryptografisch verifizierten, von der Organisation genehmigten Quellen und blockieren Sie alle anderen.

 #6.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registrierungen heruntergeladen werden.
 #6.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers validieren, bevor Artefakte lokal zwischengespeichert werden.
 #6.4.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Egress-Proxies nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.
 #6.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Repository-Erlaubnislisten vierteljährlich überprüft werden, mit Nachweisen für die geschäftliche Rechtfertigung jeder Eintragung.
 #6.4.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Richtlinienverletzungen die Isolierung von Artefakten und das Zurücksetzen abhängiger Pipeline-Ausführungen auslösen.

---

### C6.5 Bewertung von Risiken bei Datensätzen Dritter

Bewerten Sie externe Datensätze auf Vergiftung, Verzerrung und rechtliche Konformität und überwachen Sie sie während ihres gesamten Lebenszyklus.

 #6.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass externe Datensätze einer Bewertung des Vergiftungsrisikos unterzogen werden (z. B. Daten-Fingerprinting, Ausreißererkennung).
 #6.5.2    Level: 1    Rolle: D
 Verifizieren Sie, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Freigabe des Datensatzes berechnet werden.
 #6.5.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Herkunft und Lizenzbedingungen für Datensätze in ML-BOM-Einträgen erfasst sind.
 #6.5.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die regelmäßige Überwachung Abweichungen oder Beschädigungen in gehosteten Datensätzen erkennt.
 #6.5.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass nicht zulässige Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisches Bereinigen entfernt werden.

---

### C6.6 Überwachung von Angriffen auf die Lieferkette

Erkennen Sie Bedrohungen in der Lieferkette frühzeitig durch CVE-Feeds, Audit-Log-Analysen und Red-Team-Simulationen.

 #6.6.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass CI/CD-Auditprotokolle an SIEM-Erkennungen für anomale Paketabrufe oder manipulierte Build-Schritte übertragen werden.
 #6.6.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Incident-Response-Playbooks Rücksetzverfahren für kompromittierte Modelle oder Bibliotheken enthalten.
 #6.6.3    Level: 3    Rolle: V
 Überprüfen Sie, ob die Bedrohungsinformationen-Anreicherungs-Tags ML-spezifische Indikatoren (z. B. IoCs für Modellvergiftung) bei der Alarm-Sortierung markieren.

---

### C6.7 ML‑BOM für Modell-Artefakte

Erstellen und signieren Sie detaillierte, ML-spezifische SBOMs (ML-BOMs), damit nachgelagerte Verbraucher die Komponentenintegrität zur Bereitstellungszeit überprüfen können.

 #6.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Modell-Artefakt eine ML-BOM veröffentlicht, die Datensätze, Gewichtungen, Hyperparameter und Lizenzen auflistet.
 #6.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die ML‑BOM-Erstellung und die Cosign-Signierung im CI automatisiert sind und für das Zusammenführen erforderlich sind.
 #6.7.3    Level: 2    Rolle: D
 Überprüfen Sie, dass die ML-BOM-Vollständigkeitsprüfungen den Build fehlschlagen lassen, wenn Metadaten zu einer Komponente (Hash, Lizenz) fehlen.
 #6.7.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zur Bereitstellungszeit zu validieren.
 #6.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass ML-BOMs versionskontrolliert und verglichen werden, um unautorisierte Änderungen zu erkennen.

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

## C7 Modellverhalten, Ausgabeüberwachung & Sicherheitsgarantie

### Kontrollziel

Modellausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und in der Produktion kontinuierlich überwacht werden. Dies verringert Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen, während es das Vertrauen der Benutzer und die Einhaltung gesetzlicher Vorschriften erhöht.

---

### C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Decodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte verbreitet werden.

 #7.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Antwortschemata (z. B. JSON-Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus.
 #7.1.2    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass die eingeschränkte Decodierung (Stopp-Token, Regex, Max-Token) aktiviert ist, um Überläufe oder Prompt-Injektions-Nebenkanäle zu verhindern.
 #7.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese anhand von Schemata oder gegen Injektionen gesicherten Deserialisierern validieren.
 #7.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Ereignisse mit fehlerhaften Ausgaben protokolliert, rate-begrenzt und der Überwachung zugänglich gemacht werden.

---

### C7.2 Halluzinations­erkennung und -minderung

Unsicherheitsabschätzung und Fallback-Strategien begrenzen erfundene Antworten.

 #7.2.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Token-Ebenen-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.
 #7.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Antworten unterhalb eines konfigurierbaren Vertrauensschwellenwerts Rückfall-Workflows auslösen (z. B. retrieval-augmented Generation, sekundäres Modell oder menschliche Überprüfung).
 #7.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Halluzinationsvorfälle mit Ursachen-Metadaten gekennzeichnet und an Post-Mortem- und Fine-Tuning-Pipelines weitergeleitet werden.
 #7.2.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Aktualisierungen neu kalibriert werden.
 #7.2.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten erfassen.

---

### C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

 #7.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Pre- und Post-Generation-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren.
 #7.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Erkennung von PII/PCI und die automatische Schwärzung in jeder Antwort ausgeführt werden; Verstöße führen zu einem Datenschutzvorfall.
 #7.3.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Vertraulichkeitskennzeichnungen (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg übertragen werden, um ein Leck in Texten, Bildern oder Code zu verhindern.
 #7.3.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Versuche zur Umgehung von Filtern oder Klassifizierungen mit hohem Risiko eine sekundäre Genehmigung oder eine erneute Benutzer-Authentifizierung erfordern.
 #7.3.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Benutzeralter- und Rollen-Kontext berücksichtigen.

---

### C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungskontrollen verhindern Missbrauch und übermäßige Autonomie.

 #7.4.1    Level: 1    Rolle: D
 Überprüfen Sie, dass Kontingente pro Benutzer und pro API-Schlüssel die Anfragen, Tokens und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.
 #7.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkaufrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Überprüfung erfordern.
 #7.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Cross-Modal-Konsistenzprüfungen gewährleisten, dass Bilder, Code und Text, die für dieselbe Anfrage generiert werden, nicht verwendet werden können, um bösartige Inhalte zu schmuggeln.
 #7.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Tiefe der Agentendelegation, Rekursionsgrenzen und erlaubte Tool-Listen explizit konfiguriert sind.
 #7.4.5    Level: 3    Rolle: V
 Überprüfen Sie, dass die Überschreitung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Aufnahme auslöst.

---

### C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlersuche.

 #7.5.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikobewertung dies für angemessen hält.
 #7.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass generierte Erklärungen keine sensiblen Systemanweisungen oder proprietären Daten offenbaren.
 #7.5.3    Level: 3    Rolle: D
 Überprüfen Sie, ob das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und sie für autorisierte Inspektionen speichert.
 #7.5.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Erklärbarkeits-Artefakte zusammen mit Modellversionen versioniert werden, um die Prüfbarkeit zu gewährleisten.

---

### C7.6 Überwachungsintegration

Echtzeit-Beobachtbarkeit schließt den Kreislauf zwischen Entwicklung und Produktion.

 #7.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Metriken (Schemaverstöße, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden.
 #7.6.2    Level: 1    Rolle: V
 Stellen Sie sicher, dass für jede Sicherheitsmetrik Alarmgrenzwerte definiert sind, einschließlich der Eskalationswege für Bereitschaftsdienste.
 #7.6.3    Level: 2    Rolle: V
 Überprüfen Sie, ob Dashboards Ausgabestörungen mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.
 #7.6.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regel-Updates zurückfließen.
 #7.6.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Überwachungspipelines Penetrationstests unterzogen werden und Zugangskontrollen implementiert sind, um das Austreten sensibler Protokolle zu vermeiden.

---

### 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabeverifizierung und Rückverfolgbarkeit durchsetzen.

 #7.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung von illegalen, schädlichen oder nicht einvernehmlichen Deepfake-Medien (z. B. Bild, Video, Audio) verbieten.
 #7.7.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Eingabeaufforderungen auf Versuche gefiltert werden, Nachahmungen, sexuell explizite Deepfakes oder Medien, die reale Personen ohne deren Zustimmung darstellen, zu generieren.
 #7.7.3    Level: 2    Rolle: V
 Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Material zu verhindern.
 #7.7.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunfts-Metadaten eingebettet sind, um die Nachverfolgbarkeit im weiteren Verlauf zu gewährleisten.
 #7.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Umgehungsversuche (z. B. Aufforderungsverschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird an Überwachungssysteme gemeldet.

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

## C8 Speicher, Einbettungen & Vektordatenbank-Sicherheit

### Kontrollziel

Embeddings und Vektorspeicher fungieren als das „lebendige Gedächtnis“ moderner KI-Systeme, die kontinuierlich von Benutzern bereitgestellte Daten aufnehmen und diese über Retrieval-Augmented Generation (RAG) in Modellkontexte zurückführen. Wenn diese Gedächtnisstrukturen nicht reguliert werden, können sie personenbezogene Daten (PII) preisgeben, Einwilligungen verletzen oder so manipuliert werden, dass der Originaltext rekonstruiert wird. Das Ziel dieser Kontrollfamilie ist es, Gedächtnis-Pipelines und Vektordatenbanken so abzusichern, dass der Zugang nach dem Prinzip der minimalen Rechtevergabe erfolgt, Embeddings datenschutzkonform sind, gespeicherte Vektoren ablaufen oder auf Abruf widerrufen werden können, und das Gedächtnis eines Nutzers niemals die Eingaben oder Ausgaben eines anderen Nutzers beeinträchtigt.

---

### C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzung fein abgestufter Zugriffskontrollen für jede Vektorsammlung.

 #8.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Zugriffskontrollregeln auf Zeilen-/Namespace-Ebene Einfüge-, Lösch- und Abfrageoperationen pro Mandant, Sammlung oder Dokument-Tag einschränken.
 #8.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass API-Schlüssel oder JWTs eingeschränkte Ansprüche enthalten (z. B. Sammlungs-IDs, Aktionsverben) und mindestens vierteljährlich ausgetauscht werden.
 #8.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Versuche zur Eskalation von Rechten (z. B. Ähnlichkeitsabfragen über Namespace-Grenzen hinweg) innerhalb von 5 Minuten erkannt und an ein SIEM protokolliert werden.
 #8.1.4    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Vektor-Datenbank Protokolle mit Subjekt-Kennung, Operation, Vektor-ID/-Namespace, Ähnlichkeitsschwelle und Ergebnisanzahl führt.
 #8.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Zugriffentscheidungen auf Umgehungsmöglichkeiten geprüft werden, wann immer Engines aktualisiert oder Index-Sharding-Regeln geändert werden.

---

### C8.2 Einbettungsbereinigung und Validierung

Überprüfen Sie den Text vor der Vektorisierung auf personenbezogene Daten (PII), schwärzen oder pseudonymisieren Sie diese und bearbeiten Sie die Einbettungen optional nach, um verbleibende Signale zu entfernen.

 #8.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob personenbezogene Daten (PII) und regulierte Daten durch automatisierte Klassifikatoren erkannt und vor der Einbettung maskiert, tokenisiert oder entfernt werden.
 #8.2.2    Level: 1    Rolle: D
 Verifizieren Sie, dass Einbettungspipelines Eingaben, die ausführbaren Code oder Nicht-UTF-8-Artefakte enthalten und den Index vergiften könnten, ablehnen oder in Quarantäne stellen.
 #8.2.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob auf Satz-Einbettungen, deren Abstand zu einem bekannten PII-Token unter einem konfigurierbaren Schwellenwert liegt, eine lokale oder metrische Differential-Datenschutzbereinigung angewendet wird.
 #8.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Wirksamkeit der Bereinigung (z. B. Rückrufquote der PII-Radikalisierung, semantische Abweichung) mindestens halbjährlich anhand von Benchmark-Korpora validiert wird.
 #8.2.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Sanitierungskonfigurationen versioniert sind und Änderungen einer Peer-Review unterzogen werden.

---

### C8.3 Speicherablauf, Widerruf & Löschung

Die DSGVO-"Recht auf Vergessenwerden" und ähnliche Gesetze erfordern eine rechtzeitige Löschung; Vektor-Speicher müssen daher TTLs, endgültige Löschungen und Tombstoning unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

 #8.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jeder Vektor- und Metadaten-Datensatz eine TTL oder ein explizites Aufbewahrungsetikett trägt, das von automatisierten Bereinigungsaufgaben eingehalten wird.
 #8.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass von Benutzern initiierte Löschanforderungen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen löschen.
 #8.3.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass logische Löschvorgänge entweder von einer kryptografischen Löschung der Speicherblöcke begleitet werden, falls die Hardware dies unterstützt, oder durch die Zerstörung des Schlüssels im Schlüssel-Tresor.
 #8.3.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass abgelaufene Vektoren innerhalb von < 500 ms nach Ablauf in den Ergebnissen der nächsten-Nachbar-Suche ausgeschlossen werden.

---

### C8.4 Verhinderung von Einbettungsumkehr und Datenleckage

Aktuelle Abwehrmethoden—Rauschüberlagerung, Projektionsnetzwerke, Störung von Privatsphäre-Neuronen und Verschlüsselung auf Anwendungsschicht—können die Inversionsraten auf Token-Ebene unter 5 % senken.

 #8.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass ein formelles Bedrohungsmodell existiert, das Umkehrungs-, Mitgliedschafts- und Attributinferenzangriffe abdeckt und jährlich überprüft wird.
 #8.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Verschlüsselung auf Anwendungsebene oder die durchsuchbare Verschlüsselung Vektoren vor direktem Zugriff durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt.
 #8.4.3    Level: 3    Rolle: V
 Überprüfen Sie, ob die Abwehrparameter (ε für DP, Rauschpegel σ, Projektionsrang k) ein Gleichgewicht zwischen Datenschutz ≥ 99 % Token-Schutz und Nutzbarkeit ≤ 3 % Genauigkeitsverlust gewährleisten.
 #8.4.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Metriken zur Inversionsresistenz Teil der Freigabekriterien für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.

---

### C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Cross-Tenant-Lecks bleiben ein großes Risiko bei RAG: Unsachgemäß gefilterte Ähnlichkeitsabfragen können private Dokumente eines anderen Kunden offenlegen.

 #8.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Abfrage zur Datenabfrage nach der Mandanten-/Benutzer-ID gefiltert wird, bevor sie an das LLM-Prompt weitergegeben wird.
 #8.5.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Sammlungsnamen oder mit einem Namespace versehene IDs pro Benutzer oder Mandant gesalzen sind, damit Vektoren über verschiedene Bereiche hinweg nicht kollidieren können.
 #8.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Ähnlichkeitsergebnisse, die über einem konfigurierbaren Distanzschwellenwert liegen, jedoch außerhalb des Bereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.
 #8.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Multi-Tenant-Stresstests adversariale Anfragen simulieren, die versuchen, auf nicht autorisierte Dokumente zuzugreifen, und zeigen Sie eine vollständige Vermeidung von Informationslecks.
 #8.5.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Verschlüsselungsschlüssel pro Mandant getrennt sind, um eine kryptografische Isolation zu gewährleisten, selbst wenn der physische Speicher gemeinsam genutzt wird.

---

### C8.6 Fortgeschrittene Speichersystem-Sicherheit

Sicherheitskontrollen für anspruchsvolle Speicherarchitekturen, einschließlich episodischem, semantischem und Arbeitsgedächtnis mit spezifischen Anforderungen an Isolierung und Validierung.

 #8.6.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die verschiedenen Speichertypen (episodisch, semantisch, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jeden Speichertyp aufweisen.
 #8.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherkonsolidierungsprozesse eine Sicherheitsvalidierung umfassen, um die Einspeisung bösartiger Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.
 #8.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherabrufanfragen validiert und bereinigt werden, um die Extraktion unautorisierter Informationen durch Analyse von Abfragemustern, Durchsetzung von Zugriffskontrollen und Ergebnisfilterung zu verhindern.
 #8.6.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Mechanismen zum Vergessen von Speicher sensible Informationen sicher mit kryptografischen Löschgarantien löschen, indem Sie Schlüssel löschen, mehrfach überschreiben oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten verwenden.
 #8.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich auf unbefugte Änderungen oder Beschädigungen überwacht wird, indem Prüfsummen, Audit-Protokolle und automatische Benachrichtigungen verwendet werden, wenn sich der Speicherinhalt außerhalb der normalen Abläufe ändert.

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

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb festgelegter Kosten- und Risikoschwellen liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Missbrauch von Werkzeugen, Agentenschleifen-Erkennung, Kommunikationsübernahme, Identitätsfälschung, Schwarmmanipulation und Absichtsmanipulation.

---

### 9.1 Aufgabenplanung von Agenten und Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

 #9.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass maximale Rekursionstiefe, Breite, Echtzeitdauer, Tokens und monetäre Kosten pro Agentenausführung zentral konfiguriert und versioniert sind.
 #9.1.2    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass privilegierte oder unumkehrbare Aktionen (z. B. Code-Commits, finanzielle Überweisungen) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern.
 #9.1.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Echtzeit-Ressourcenmonitoren eine Circuit-Breaker-Unterbrechung auslösen, wenn eine Budgetgrenze überschritten wird, und dadurch die weitere Aufgabenerweiterung stoppen.
 #9.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Circuit-Breaker-Ereignisse mit Agenten-ID, auslösendem Zustand und erfasstem Planstatus zur forensischen Überprüfung protokolliert werden.
 #9.1.5    Level: 3    Rolle: V
 Verifizieren Sie, dass Sicherheitstests Szenarien der Budgeterschöpfung und des Ausbruchs von Plänen abdecken und einen sicheren Stopp ohne Datenverlust bestätigen.
 #9.1.6    Level: 3    Rolle: D
 Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code formuliert und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.

---

### 9.2 Tool-Plugin-Sandboxing

Isoliere Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

 #9.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jedes Tool/Plugin innerhalb eines Betriebssystems, Containers oder einer WASM-Ebene-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird.
 #9.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Ressourcenkontingente (CPU, Speicher, Festplatte, Netzwerkausgang) und Ausführungszeitlimits durchgesetzt und protokolliert werden.
 #9.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Werkzeug-Binärdateien oder Beschreibungen digital signiert sind; die Signaturen werden vor dem Laden überprüft.
 #9.2.4    Level: 2    Rolle: V
 Überprüfen Sie, ob die Sandbox-Telemetrie an ein SIEM übertragen wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Alarme aus.
 #9.2.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Plugins mit hohem Risiko vor dem produktiven Einsatz einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden.
 #9.2.6    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Sandbox-Ausbruchsversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung unter Quarantäne gestellt wird.

---

### 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte Agent-zu-Agent-Rekursionen und Kostenexplosionen.

 #9.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.
 #9.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Agenten eine eindeutige Invocation-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.
 #9.3.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass kumulative Compute-Unit- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits führt zum Abbruch der Kette.
 #9.3.4    Level: 3    Rolle: V
 Überprüfen Sie, dass die formale Analyse oder das Model Checking das Fehlen von unbeschränkter Rekursion in Agentenprotokollen nachweist.
 #9.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob Schleifen-Abbruchereignisse Warnungen generieren und kontinuierliche Verbesserungskennzahlen speisen.

---

### 9.4 Schutz vor Protokollebene-Missbrauch

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Entführung oder Manipulation zu verhindern.

 #9.4.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass alle Nachrichten von Agent zu Tool und von Agent zu Agent authentifiziert sind (z. B. Mutual TLS oder JWT) und Ende-zu-Ende verschlüsselt sind.
 #9.4.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Schemata strikt validiert werden; unbekannte Felder oder fehlerhafte Nachrichten werden abgelehnt.
 #9.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) den gesamten Nachrichteninhalt einschließlich der Werkzeugparameter abdecken.
 #9.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass der Wiedergabeschutz (Nonces oder Zeitstempelfenster) auf der Protokollebene durchgesetzt wird.
 #9.4.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Protokollimplementierungen einem Fuzzing und einer statischen Analyse auf Injektions- oder Deserialisierungsfehler unterzogen werden.

---

### 9.5 Agentenidentität & Manipulationsnachweis

Stellen Sie sicher, dass Aktionen zurückverfolgbar sind und Änderungen erkennbar bleiben.

 #9.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob jede Agenteninstanz eine eindeutige kryptografische Identität besitzt (Schlüsselpaar oder hardwarebasierte Anmeldeinformationen).
 #9.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass alle Agentenaktionen signiert und mit Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.
 #9.5.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass manipulationssichere Protokolle in einem nur-anhängbaren oder einmal beschreibbaren Medium gespeichert werden.
 #9.5.4    Level: 3    Rolle: D
 Überprüfen Sie, dass Identitätsschlüssel gemäß einem definierten Zeitplan und bei Anzeichen einer Kompromittierung rotieren.
 #9.5.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agents auslösen.

---

### 9.6 Multi-Agent Schwarm-Risikoreduzierung

Mildern Sie kollektives Verhaltensrisiken durch Isolation und formale Sicherheitsmodellierung.

 #9.6.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden.
 #9.6.2    Level: 3    Rolle: V
 Stellen Sie sicher, dass Schwarmverhalten modelliert und formell auf Lebendigkeit und Sicherheit vor der Bereitstellung überprüft werden.
 #9.6.3    Level: 3    Rolle: D
 Überprüfen Sie, ob Laufzeit-Monitore aufkommende unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und Korrekturmaßnahmen einleiten.

---

### 9.7 Benutzer- und Werkzeugauthentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede agenteninitiierte Aktion.

 #9.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale bei nachgelagerten Systemen authentifizieren und niemals Endbenutzeranmeldeinformationen wiederverwenden.
 #9.7.2    Level: 2    Rolle: D
 Überprüfen Sie, dass feinkörnige Autorisierungsrichtlinien einschränken, welche Tools ein Agent aufrufen darf und welche Parameter er angeben darf.
 #9.7.3    Level: 2    Rolle: V
 Überprüfen Sie, dass die Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.
 #9.7.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass delegierte Privilegien automatisch ablaufen und nach Ablauf der Frist oder einer Änderung des Umfangs eine erneute Zustimmung erforderlich ist.

---

### 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und integritätssichern Sie alle Nachrichten zwischen Agenten, um Abhören und Manipulation zu verhindern.

 #9.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass gegenseitige Authentifizierung und perfekte Vorwärtsgeheimnis-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.
 #9.8.2    Level: 1    Rolle: D
 Überprüfen Sie, dass die Nachrichtenintegrität und der Ursprung validiert werden, bevor die Verarbeitung erfolgt; Fehler lösen Warnungen aus und führen zum Verwerfen der Nachricht.
 #9.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.
 #9.8.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die formale Verifikation oder Modellüberprüfung bestätigt, dass Protokoll-Zustandsautomaten nicht in unsichere Zustände geführt werden können.

---

### 9.9 Absichtsüberprüfung und Durchsetzung von Einschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

 #9.9.1    Level: 1    Rolle: D
 Überprüfen Sie, dass vor der Ausführung Constraint-Solver vorgeschlagene Aktionen anhand von fest programmierten Sicherheits- und Richtlinienregeln prüfen.
 #9.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Maßnahmen mit hoher Auswirkung (finanziell, destruktiv, datenschutzsensibel) eine ausdrückliche Intentionbestätigung des initiierenden Benutzers erfordern.
 #9.9.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Nachbedingungsprüfungen bestätigen, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebenwirkungen erreicht haben; Abweichungen lösen eine Rückrollaktion aus.
 #9.9.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Methoden (z. B. Modellprüfung, Theorembeweis) oder eigenschaftsbasierte Tests nachweisen, dass Agentenpläne alle deklarierten Einschränkungen erfüllen.
 #9.9.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass Vorfälle mit Absichtsabweichungen oder Verstoß gegen Auflagen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.

---

### 9.10 Sicherheitsstrategie für die Agentenlogik

Sichere Auswahl und Ausführung verschiedener Denkstrategien, einschließlich ReAct-, Chain-of-Thought- und Tree-of-Thoughts-Ansätzen.

 #9.10.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Auswahl der Reasoning-Strategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und dass identische Eingaben innerhalb desselben Sicherheitskontexts identische Strategiewahlen ergeben.
 #9.10.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) eine dedizierte Eingabevalidierung, Ausgabe-Säuberung und spezifische Ausführungszeitbegrenzungen entsprechend ihrem kognitiven Ansatz besitzt.
 #9.10.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Übergänge der Argumentationsstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabeeigenschaften, Auswahlkriterienwerten und Ausführungsmetadaten zur Nachverfolgung des Prüfpfads.
 #9.10.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Tree-of-Thoughts-Argumentation Verzweigungsbeschneidungsmechanismen beinhaltet, die die Exploration beenden, wenn Richtlinienverstöße, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.
 #9.10.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ReAct (Reason-Act-Observe)-Zyklen Validierungskontrollpunkte in jeder Phase beinhalten: Verifikation des Denkprozesses, Autorisierung der Handlung und Bereinigung der Beobachtung vor dem Fortfahren.
 #9.10.6    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistungskennzahlen der Argumentationsstrategie (Ausführungszeit, Ressourcenverbrauch, Ausgabequalität) überwacht werden und automatisierte Warnungen ausgelöst werden, wenn die Kennzahlen die konfigurierten Schwellenwerte überschreiten.
 #9.10.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.
 #9.10.8    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitstests der Reasoning-Strategie Fuzzing mit fehlerhaften Eingaben, adversariale Eingabeaufforderungen, die darauf ausgelegt sind, einen Strategiewechsel zu erzwingen, sowie Grenzwerttests für jeden kognitiven Ansatz umfassen.

---

### 9.11 Agent-Lebenszyklus Zustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Prüfpfaden und definierten Wiederherstellungsverfahren.

 #9.11.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Agenteninitialisierung die Einrichtung einer kryptografischen Identität mit hardwaregestützten Anmeldeinformationen und unveränderlichen Start-Auditprotokollen umfasst, die die Agenten-ID, den Zeitstempel, den Konfigurations-Hash und die Initialisierungsparameter enthalten.
 #9.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Zustandsübergänge des Agenten kryptografisch signiert, mit Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich auslösender Ereignisse, Hash des vorherigen Zustands, Hash des neuen Zustands und durchgeführter Sicherheitsüberprüfungen.
 #9.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Agenten-Abschaltverfahren eine sichere Speicherlöschung mittels kryptografischer Vernichtung oder mehrfacher Überschreibung, die Widerrufung von Anmeldeinformationen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen.
 #9.11.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Agent-Wiederherstellungsmechanismen die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Beschädigung auf bekannte intakte Zustände zurücksetzen, wobei automatisierte Warnungen und manuelle Genehmigungsanforderungen erforderlich sind.
 #9.11.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Agenten-Persistenzmechanismen sensible Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und eine sichere Schlüsselrotation nach konfigurierbaren Zeitplänen (maximal 90 Tage) mit unterbrechungsfreier Bereitstellung implementieren.

---

### 9.12 Sicherheitsrahmen für Werkzeugintegration

Sicherheitskontrollen für das dynamische Laden von Tools, deren Ausführung und Ergebnisvalidierung mit definierten Risikoabschätzungs- und Genehmigungsverfahren.

 #9.12.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Tool-Beschreibungen Sicherheits-Metadaten enthalten, die erforderliche Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcenbeschränkungen (CPU, Speicher, Netzwerk) und Validierungsanforderungen dokumentiert in Tool-Manifests angeben.
 #9.12.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Toolausführung vor der Integration anhand der erwarteten Schemata (JSON-Schema, XML-Schema) und Sicherheitsrichtlinien (Ausgabereinigung, Datenklassifizierung) validiert werden, unter Einhaltung von Zeitlimits und Fehlerbehandlungsverfahren.
 #9.12.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Interaktionsprotokolle des Werkzeugs einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcennutzung und Rückgabecodes, mit strukturierter Protokollierung für die SIEM-Integration.
 #9.12.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob dynamische Werkzeuglade-Mechanismen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung und Berechtigungsverifizierung vor der Ausführung implementieren.
 #9.12.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Sicherheitsbewertungen von Tools automatisch für neue Versionen ausgelöst werden, mit obligatorischen Genehmigungsschritten, einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, mit dokumentierten Genehmigungskriterien und SLA-Anforderungen.

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

## 10 Gegnerschaftliche Robustheit & Datenschutzverteidigung

### Kontrollziel

Stellen Sie sicher, dass KI-Modelle auch bei Umgehungs-, Rückschluss-, Extraktions- oder Vergiftungsangriffen zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben.

---

### 10.1 Modellabstimmung & Sicherheit

Schützen Sie vor schädlichen oder gegen Richtlinien verstoßenden Ausgaben.

 #10.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Alignment-Testset (Red-Team-Eingabeaufforderungen, Jailbreak-Prüfungen, nicht erlaubte Inhalte) versioniert und bei jeder Modellfreigabe ausgeführt wird.
 #10.1.2    Level: 1    Rolle: D
 Überprüfen Sie, ob Verweigerungs- und sichere Abschluss-Schutzmaßnahmen durchgesetzt werden.
 #10.1.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob ein automatisierter Evaluator die Rate schädlicher Inhalte misst und Rückschritte über eine festgelegte Schwelle hinaus markiert.
 #10.1.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Training zur Gegen-Jailbreak-Maßnahme dokumentiert und reproduzierbar ist.
 #10.1.5    Level: 3    Rolle: V
 Überprüfen Sie, ob formale Nachweise der Einhaltung von Richtlinien oder zertifizierte Überwachungen kritische Bereiche abdecken.

---

### 10.2 Härtung gegen adversarielle Beispiele

Erhöhen Sie die Resilienz gegenüber manipulierten Eingaben. Robustes adversariales Training und Benchmark-Bewertung sind die derzeit besten Praktiken.

 #10.2.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Projekt-Repositorien adversariale Trainingskonfigurationen mit reproduzierbaren Seeds enthalten.
 #10.2.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung adversarialer Beispiele in Produktionspipelines Blockierungswarnungen auslöst.
 #10.2.4    Level: 3    Rolle: V
 Verifizieren Sie, dass zertifizierte Robustheitsnachweise oder Intervallgrenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken.
 #10.2.5    Level: 3    Rolle: V
 Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um keinen messbaren Verlust an Robustheit zu bestätigen.

---

### 10.3 Maßnahmen zur Minderung von Mitgliedschafts-Inferenz

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsmaterial enthalten war. Differentielle Privatsphäre und das Maskieren von Vertrauensscores bleiben die effektivsten bekannten Schutzmaßnahmen.

 #10.3.1    Level: 1    Rolle: D
 Überprüfen Sie, ob die Entropieregulierung pro Abfrage oder die Temperaturskalierung übermäßig selbstsichere Vorhersagen reduziert.
 #10.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Training eine ε-beschränkte differentielle Datenschutz-Optimierung für sensible Datensätze verwendet.
 #10.3.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Angriffssimulationen (Shadow-Modell oder Blackbox) einen Angriff-AUC ≤ 0,60 auf zurückgehaltenen Daten zeigen.

---

### 10.4 Modell-Inversionsresistenz

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen heben die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen hervor.

 #10.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; falls erforderlich, verwenden Sie Kategorien oder Einweg-Transformationen.
 #10.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen vom selben Principal drosseln.
 #10.4.3    Level: 2    Rolle: D
 Überprüfen Sie, ob das Modell mit datenschutzwahrendem Rauschen trainiert wurde.

---

### 10.5 Modell-Extraktionsabwehr

Erkennen und Verhindern unautorisierter Klonungen. Wasserzeichen und Abfrage-Musteranalyse werden empfohlen.

 #10.5.1    Level: 1    Rolle: D
 Überprüfen Sie, dass Inferenz-Gateways globale und pro-API-Schlüssel festgelegte Ratenbegrenzungen durchsetzen, die an die Memorierungsschwelle des Modells angepasst sind.
 #10.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Statistik der Abfrage-Entropie und der Eingabe-Mehrzahl eine automatisierte Extraktionsdetektion speisen.
 #10.5.3    Level: 2    Rolle: V
 Überprüfen Sie, dass fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Abfragen gegen einen verdächtigen Klon nachgewiesen werden können.
 #10.5.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich rotiert werden.
 #10.5.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Extraction-Alert-Ereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.

---

### 10.6 Erkennung von zur Inferenzzeit vergifteten Daten

Identifizieren und Neutralisieren von mit Hintertüren verseuchten oder vergifteten Eingaben.

 #10.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Eingaben vor der Modellausführung durch einen Anomalieerkenner (z. B. STRIP, Konsistenzbewertung) geprüft werden.
 #10.6.2    Level: 1    Rolle: V
 Stellen Sie sicher, dass die Schwellenwerte des Detektors an sauberen/verseuchten Validierungsdatensätzen angepasst sind, um weniger als 5 % falsch positive Ergebnisse zu erreichen.
 #10.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob als vergiftet gekennzeichnete Eingaben eine Soft-Blockierung und menschliche Prüfungsabläufe auslösen.
 #10.6.4    Level: 2    Rolle: V
 Verifizieren Sie, dass Detektoren mit adaptiven, triggerlosen Hintertür-Angriffen auf Stress getestet werden.
 #10.6.5    Level: 3    Rolle: D
 Überprüfen Sie, ob Wirksamkeitsmetriken der Erkennung protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.

---

### 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Sicherheitsrichtlinienaktualisierungen basierend auf Bedrohungsinformationen und Verhaltensanalysen.

 #10.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion gewahrt bleibt.
 #10.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Richtlinienaktualisierungen kryptographisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.
 #10.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren.
 #10.7.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Sensitivität der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.
 #10.7.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Beweispfade für die Überprüfung durch das Sicherheitsteam enthalten.

---

### 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

 #10.8.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen beinhalten.
 #10.8.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Reflexionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch feindliche Eingaben zu verhindern.
 #10.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Beeinträchtigungen in den Denkprozessen von Agenten erkennt.
 #10.8.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob sicherheitsbezogene Warnungen auf Reflection-Basis eine erweiterte Überwachung und potenzielle Workflows für menschliche Eingriffe auslösen.
 #10.8.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.

---

### 10.9 Evolution & Selbstverbesserung Sicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

 #10.9.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.
 #10.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Entwicklungsvorschläge vor der Umsetzung einer Sicherheitsauswirkungsbewertung unterzogen werden.
 #10.9.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Selbstverbesserungsmechanismen Rückrollfunktionen mit Integritätsüberprüfung enthalten.
 #10.9.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Meta-Learning-Sicherheit manipulativem Eingreifen in Verbesserungsalgorithmen entgegenwirkt.
 #10.9.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mittels mathematischer Beweise für die Konvergenz.

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

## 11 Datenschutz & Verwaltung persönlicher Daten

### Kontrollziel

Gewährleisten Sie strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg—Erfassung, Training, Inferenz und Vorfallreaktion—sodass personenbezogene Daten nur mit eindeutiger Zustimmung, minimalem erforderlichen Umfang, nachweisbarer Löschung und formellen Datenschutzgarantien verarbeitet werden.

---

### 11.1 Anonymisierung & Datenminimierung

 #11.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass direkte und Quasi-Identifikatoren entfernt oder gehasht werden.
 #11.1.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und benachrichtigen, wenn die Schwellenwerte unter die Richtlinie fallen.
 #11.1.3    Level: 2    Rolle: V
 Überprüfen Sie, dass die Berichte zur Merkmalwichtigkeit des Modells keine Kennungsweitergabe über ε = 0,01 wechselseitige Information hinaus nachweisen.
 #11.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise oder Zertifizierungen mit synthetischen Daten zeigen, dass das Risiko der Re-Identifikation selbst bei Verknüpfungsangriffen ≤ 0,05 beträgt.

---

### 11.2 Recht auf Vergessenwerden & Durchsetzung der Löschung

 #11.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Anfragen zur Löschung von Datenbetroffenen auf Rohdatensätze, Checkpoints, Einbettungen, Protokolle und Sicherungskopien innerhalb von Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden.
 #11.2.2    Level: 2    Rolle: D
 Überprüfen Sie, dass „Machine-Unlearning“-Routinen physisch eine Neu-Trainierung durchführen oder eine Annäherung der Entfernung mithilfe zertifizierter Unlearning-Algorithmen vornehmen.
 #11.2.3    Level: 2    Rolle: V
 Überprüfen Sie, dass die Evaluierung des Schattenmodells nachweist, dass vergessene Datensätze weniger als 1 % der Ausgaben nach dem Unlearning beeinflussen.
 #11.2.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden prüfbar sind.

---

### 11.3 Differenzielle Datenschutzmaßnahmen

 #11.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Datenschutz-Verlustabrechnungs-Dashboards alarmieren, wenn der kumulative ε die Richtliniengrenzen überschreitet.
 #11.3.2    Level: 2    Rolle: V
 Überprüfen Sie, ob Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10 % des angegebenen Werts schätzen.
 #11.3.3    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen nach dem Training und Einbettungen abdecken.

---

### 11.4 Zweckbindung & Schutz vor Scope Creep

 #11.4.1    Level: 1    Rolle: D
 Überprüfen Sie, dass jeder Datensatz und jeder Modell-Checkpoint mit einem maschinenlesbaren Zweck-Tag versehen ist, das mit der ursprünglichen Einwilligung übereinstimmt.
 #11.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Laufzeitüberwachungen Anfragen erkennen, die mit dem angegebenen Zweck unvereinbar sind, und eine weiche Ablehnung auslösen.
 #11.4.3    Level: 3    Rolle: D
 Verifizieren Sie, dass Richtlinien-als-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.
 #11.4.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Rückverfolgbarkeitsnachweise zeigen, dass sich jeder Lebenszyklus personenbezogener Daten im einwilligungsgemäßen Umfang bewegt.

---

### 11.5 Einwilligungsmanagement & rechtmäßige Grundlagenverfolgung

 #11.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro betroffener Person speichert.
 #11.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass APIs Einwilligungstoken bereitstellen; Modelle müssen den Token-Bereich vor der Inferenz validieren.
 #11.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungsprozesse innerhalb von 24 Stunden stoppen.

---

### 11.6 Föderiertes Lernen mit Datenschutzkontrollen

 #11.6.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Client-Updates vor der Aggregation eine lokale Differentielle-Privatsphäre-Rauschunterdrückung verwenden.
 #11.6.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients offenlegen.
 #11.6.3    Level: 2    Rolle: V
 Verifizieren Sie, dass eine gegen Datenvergiftung resistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.
 #11.6.4    Level: 3    Rolle: V
 Verifizieren Sie, dass formale Beweise das gesamte ε-Budget mit einem Nutzungsverlust von weniger als 5 nachweisen.

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

## C12 Überwachung, Protokollierung & Anomalieerkennung

### Kontrollziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit dessen, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, eingestuft und daraus gelernt werden kann.

### C12.1 Anforderungs- und Antwortprotokollierung

 #12.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzeranfragen und Modellantworten mit geeigneten Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).
 #12.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Protokolle in sicheren, zugriffskontrollierten Repositorien mit angemessenen Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.
 #12.1.3    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Log-Speichersysteme Verschlüsselung sowohl im Ruhezustand als auch während der Übertragung implementieren, um sensible Informationen in den Logs zu schützen.
 #12.1.4    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben vor der Protokollierung automatisch geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen.
 #12.1.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienentscheidungen und Maßnahmen zur Sicherheitssfilterung mit ausreichenden Details protokolliert werden, um die Prüfung und Fehlerbehebung von Inhaltenmoderationssystemen zu ermöglichen.
 #12.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Protokollintegrität beispielsweise durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.

---

### C12.2 Missbrauchserkennung und Alarmierung

 #12.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass das System bekannte Jailbreak-Muster, Versuche der Prompt-Injektion und adversariale Eingaben mithilfe der signaturbasierten Erkennung erkennt und meldet.
 #12.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das System mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert wird.
 #12.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifische Kontexte wie Modellkennungen, Vertrauenswerte und Entscheidungen des Sicherheitsfilters enthalten.
 #12.2.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Erkundungsverhalten erkennt.
 #12.2.5    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Alarmmechanismen die Sicherheitsteams benachrichtigen, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.
 #12.2.6    Level: 2    Rolle: D/V
 Überprüfen Sie, ob benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modell-Extraktionsangriffe.
 #12.2.7    Level: 3    Rolle: D/V
 Überprüfen Sie, ob automatisierte Abläufe zur Vorfallreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.

---

### C12.3 Modellerkennungsverschiebung

 #12.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.
 #12.3.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass automatisierte Warnmeldungen ausgelöst werden, wenn Leistungskennzahlen vordefinierte Schwellenwerte für Verschlechterungen überschreiten oder erheblich von Basiswerten abweichen.
 #12.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Halluzinations-Erkennungsmonitore Fälle identifizieren und markieren, in denen die Modellausgaben faktisch falsche, inkonsistente oder erfundene Informationen enthalten.

---

### C12.4 Leistungs- und Verhaltens-Telemetrie

 #12.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Betriebsmetriken wie Anforderungsverzögerung, Token-Verbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.
 #12.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Erfolgs- und Fehlerraten mit Kategorisierung der Fehlertypen und deren Ursachen erfasst werden.
 #12.4.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Überwachung der Ressourcenauslastung die GPU-/CPU-Nutzung, den Speicherverbrauch und die Speicheranforderungen umfasst und bei Überschreiten von Schwellenwerten Alarmmeldungen ausgibt.

---

### C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

 #12.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Reaktionspläne für Vorfälle speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversarielle Angriffe abdecken.
 #12.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Incident-Response-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachkenntnisse haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.
 #12.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Analyse nach dem Vorfall Überlegungen zur Modellneuschulung, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst.

---

### C12.5 Erkennung von Leistungsabfällen bei KI

Überwachen und Erkennen von Verschlechterungen in der Leistungsfähigkeit und Qualität von KI-Modellen im Zeitverlauf.

 #12.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.
 #12.5.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass die Erkennung von Datenverschiebungen Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.
 #12.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Erkennung von Konzeptveränderungen Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.
 #12.5.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Leistungsabfälle automatisierte Warnungen auslösen und Workflows für die Modellneu- oder -ersetzung einleiten.
 #12.5.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Ursachenanalyse der Leistungsverschlechterung Leistungsabfälle mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.

---

### C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

 #12.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die DAG-Visualisierungsdaten vor der Speicherung oder Übertragung bereinigt werden, um sensible Informationen zu entfernen.
 #12.6.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Zugriffssteuerungen für die Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer die Entscheidungswege des Agenten und die Begründungsspuren einsehen können.
 #12.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.
 #12.6.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injections-Angriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.
 #12.6.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Echtzeit-Updates des DAG einer Ratenbegrenzung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.

---

### C12.7 Proaktives Verhalten zur Sicherheitsüberwachung

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

 #12.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit einer Risikoabschätzung validiert werden.
 #12.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob autonome Initiativauslöser die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.
 #12.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Konsequenzen analysiert werden.
 #12.7.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Audit-Trails erfordern.
 #12.7.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hinweisen können.

---

### Referenzen

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menschliche Aufsicht, Verantwortlichkeit und Governance

### Kontrollziel

Dieses Kapitel stellt Anforderungen für die Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen bereit und gewährleistet Erklärbarkeit, Transparenz und ethische Fürsorge während des gesamten KI-Lebenszyklus.

---

### C13.1 Kill-Switch- und Überschreibmechanismen

Stellen Sie Abschalt- oder Rollback-Pfade bereit, wenn ein unsicheres Verhalten des KI-Systems beobachtet wird.

 #13.1.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass ein manueller Not-Aus-Mechanismus vorhanden ist, um die AI-Modell-Inferenz und Ausgaben sofort zu stoppen.
 #13.1.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Übersteuerungskontrollen nur für autorisiertes Personal zugänglich sind.
 #13.1.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Rollback-Verfahren zu vorherigen Modellversionen oder sicheren Betriebsmodi zurückkehren können.
 #13.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Override-Mechanismen regelmäßig getestet werden.

---

### C13.2 Mensch-im-Loop-Entscheidungsüberprüfungspunkte

Menschliche Genehmigungen erforderlich, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

 #13.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.
 #13.2.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Risikoschwellen klar definiert sind und automatisch menschliche Prüfabläufe auslösen.
 #13.2.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass zeitkritische Entscheidungen über Ausweichverfahren verfügen, wenn eine menschliche Genehmigung innerhalb der erforderlichen Zeitrahmen nicht eingeholt werden kann.
 #13.2.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.

---

### C13.3 Verantwortlichkeitskette & Prüfbarkeit

Protokollieren Sie Bedieneraktionen und Modellentscheidungen.

 #13.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden.
 #13.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Prüfprotokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.

---

### C13.4 Erklärbare KI-Techniken

Oberflächenmerkmal-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

 #13.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format liefern.
 #13.4.2    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Qualität der Erklärungen durch menschliche Evaluationsstudien und Metriken validiert wird.
 #13.4.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für kritische Entscheidungen Merkmalswichtigkeitswerte oder Attributionsmethoden (SHAP, LIME usw.) verfügbar sind.
 #13.4.4    Level: 3    Rolle: V
 Überprüfen Sie, dass kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu verändern, sofern dies für den Anwendungsfall und die Domäne zutreffend ist.

---

### C13.5 Modellkarten & Verwendungshinweise

Pflegen Sie Model Cards für den vorgesehenen Gebrauch, Leistungskennzahlen und ethische Überlegungen.

 #13.5.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Modelldokumentationen die vorgesehenen Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi beschreiben.
 #13.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.
 #13.5.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden.
 #13.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.

---

### C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwerte oder Entropie-Messungen in Antworten.

 #13.6.1    Level: 1    Rolle: D
 Überprüfen Sie, ob KI-Systeme Vertrauenswerte oder Unsicherheitsmaße zusammen mit ihren Ausgaben bereitstellen.
 #13.6.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Unsicherheitsschwellen eine zusätzliche menschliche Überprüfung oder alternative Entscheidungswege auslösen.
 #13.6.3    Level: 2    Rolle: V
 Überprüfen Sie, ob Unsicherheitsquantifizierungsmethoden kalibriert und anhand von Grundwahrscheinlichkeitsdaten validiert sind.
 #13.6.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Unsicherheitsfortpflanzung durch mehrstufige KI-Workflows erhalten bleibt.

---

### C13.7 Nutzerorientierte Transparenzberichte

Geben Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung.

 #13.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Praktiken zur Verwaltung der Einwilligung der Nutzer klar an die Stakeholder kommuniziert werden.
 #13.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.
 #13.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass regelmäßig veröffentlichte Transparenzberichte AI-Zwischenfälle und betriebliche Metriken in angemessenem Umfang offenlegen.

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

Dieses umfassende Glossar bietet Definitionen der wichtigsten Begriffe aus den Bereichen KI, ML und Sicherheit, die im gesamten AISVS verwendet werden, um Klarheit und ein gemeinsames Verständnis zu gewährleisten.

Adversarisches Beispiel: Eine Eingabe, die absichtlich erstellt wurde, um ein KI-Modell dazu zu bringen, einen Fehler zu machen, oft durch das Hinzufügen subtiler Störungen, die für Menschen nicht wahrnehmbar sind.
​
Gegnerische Robustheit – Gegnerische Robustheit in der KI bezieht sich auf die Fähigkeit eines Modells, seine Leistung aufrechtzuerhalten und Widerstand gegen absichtlich gestaltete, bösartige Eingaben zu leisten, die darauf abzielen, Fehler zu verursachen oder das Modell zu manipulieren.
​
Agent – KI-Agenten sind Softwaresysteme, die KI nutzen, um Ziele zu verfolgen und Aufgaben im Auftrag von Benutzern zu erledigen. Sie zeigen Fähigkeiten in Argumentation, Planung und Gedächtnis und verfügen über ein Maß an Autonomie, um Entscheidungen zu treffen, zu lernen und sich anzupassen.
​
Agentische KI: KI-Systeme, die mit einem gewissen Grad an Autonomie arbeiten können, um Ziele zu erreichen, dabei oft Entscheidungen treffen und Handlungen ausführen, ohne direkte menschliche Eingriffe.
​
Attributbasierte Zugriffskontrolle (ABAC): Ein Zugriffskontrollparadigma, bei dem Autorisierungsentscheidungen auf Attributen des Nutzers, der Ressource, der Aktion und der Umgebung basieren, die zur Abfragezeit bewertet werden.
​
Backdoor-Angriff: Eine Art von Datenvergiftungsangriff, bei dem das Modell so trainiert wird, auf bestimmte Auslöser auf eine bestimmte Weise zu reagieren, während es sich ansonsten normal verhält.
​
Bias: Systematische Fehler in den Ausgaben von KI-Modellen, die zu unfairen oder diskriminierenden Ergebnissen für bestimmte Gruppen oder in bestimmten Kontexten führen können.
​
Bias-Ausnutzung: Eine Angriffstechnik, die bekannte Verzerrungen in KI-Modellen ausnutzt, um Ausgaben oder Ergebnisse zu manipulieren.
​
Cedar: Amazons Richtliniensprache und -engine für fein granulare Berechtigungen, die bei der Umsetzung von ABAC für KI-Systeme verwendet wird.
​
Gedankenkette: Eine Technik zur Verbesserung des Denkvermögens in Sprachmodellen durch Erzeugung von Zwischenschritten des Denkprozesses vor der Ausgabe einer endgültigen Antwort.
​
Circuit Breaker: Mechanismen, die den Betrieb von KI-Systemen automatisch stoppen, wenn bestimmte Risikoschwellen überschritten werden.
​
Datenleck: Unbeabsichtigte Offenlegung sensibler Informationen durch Ausgaben oder Verhalten von KI-Modellen.
​
Datenvergiftung: Die absichtliche Korruption von Trainingsdaten, um die Modellintegrität zu gefährden, häufig um Hintertüren einzubauen oder die Leistung zu verschlechtern.
​
Differenzielle Privatsphäre – Differenzielle Privatsphäre ist ein mathematisch rigoroses Rahmenwerk zur Veröffentlichung statistischer Informationen über Datensätze, während die Privatsphäre einzelner Datenpersonen geschützt wird. Es ermöglicht einem Dateninhaber, aggregierte Muster der Gruppe zu teilen und gleichzeitig die Informationen, die über spezifische Individuen preisgegeben werden, zu begrenzen.
​
Einbettungen: Dichte Vektor-Darstellungen von Daten (Text, Bilder usw.), die die semantische Bedeutung in einem hochdimensionalen Raum erfassen.
​
Erklärbarkeit – Erklärbarkeit in der KI ist die Fähigkeit eines KI-Systems, menschenverständliche Gründe für seine Entscheidungen und Vorhersagen zu liefern und Einblicke in seine internen Arbeitsweisen zu geben.
​
Erklärbare KI (XAI): KI-Systeme, die entwickelt wurden, um durch verschiedene Techniken und Frameworks menschlich verständliche Erklärungen für ihre Entscheidungen und Verhaltensweisen zu liefern.
​
Federiertes Lernen: Ein Ansatz im maschinellen Lernen, bei dem Modelle über mehrere dezentralisierte Geräte hinweg mit lokalen Datensätzen trainiert werden, ohne dass die Daten selbst ausgetauscht werden.
​
Guardrails: Einschränkungen, die implementiert werden, um zu verhindern, dass KI-Systeme schädliche, voreingenommene oder anderweitig unerwünschte Ausgaben erzeugen.
​
Halluzination – Eine KI-Halluzination bezieht sich auf ein Phänomen, bei dem ein KI-Modell falsche oder irreführende Informationen erzeugt, die nicht auf seinen Trainingsdaten oder der faktischen Realität basieren.
​
Human-in-the-Loop (HITL): Systeme, die darauf ausgelegt sind, menschliche Aufsicht, Überprüfung oder Eingriffe an entscheidenden Entscheidungspunkten zu erfordern.
​
Infrastructure as Code (IaC): Verwaltung und Bereitstellung von Infrastruktur durch Code statt manueller Prozesse, was Sicherheitsscans und konsistente Bereitstellungen ermöglicht.
​
Jailbreak: Techniken, die verwendet werden, um Sicherheitsvorkehrungen in KI-Systemen, insbesondere in großen Sprachmodellen, zu umgehen und verbotene Inhalte zu erzeugen.
​
Least Privilege: Das Sicherheitsprinzip, nur die minimal notwendigen Zugriffsrechte für Benutzer und Prozesse zu gewähren.
​
LIME (Local Interpretable Model-agnostic Explanations): Eine Technik zur Erklärung der Vorhersagen eines beliebigen maschinellen Lernklassifikators durch lokale Approximation mit einem interpretierbaren Modell.
​
Mitgliedschaftsinferenzangriff: Ein Angriff, der darauf abzielt festzustellen, ob ein bestimmter Datenpunkt zum Trainieren eines maschinellen Lernmodells verwendet wurde.
​
MITRE ATLAS: Bedrohungslandschaft durch Angreifer für künstliche Intelligenzsysteme; eine Wissensdatenbank zu gegnerischen Taktiken und Techniken gegen KI-Systeme.
​
Modellkarte – Eine Modellkarte ist ein Dokument, das standardisierte Informationen über die Leistung, Einschränkungen, beabsichtigte Verwendungszwecke und ethische Überlegungen eines KI-Modells bereitstellt, um Transparenz und verantwortungsbewusste KI-Entwicklung zu fördern.
​
Modell-Extraktion: Ein Angriff, bei dem ein Angreifer ein Zielmodell wiederholt abfragt, um ohne Genehmigung eine funktional ähnliche Kopie zu erstellen.
​
Modellinversion: Ein Angriff, der versucht, Trainingsdaten durch die Analyse von Modellausgaben zu rekonstruieren.
​
Modell-Lebenszyklus-Management – Das AI Modell-Lebenszyklus-Management ist der Prozess der Überwachung aller Phasen der Existenz eines AI Modells, einschließlich Design, Entwicklung, Bereitstellung, Überwachung, Wartung und schlussendliche Außerdienststellung, um sicherzustellen, dass es effektiv bleibt und den Zielen entspricht.
​
Modellvergiftung: Einführung von Schwachstellen oder Hintertüren direkt in ein Modell während des Trainingsprozesses.
​
Modell-Diebstahl/-Entwendung: Das Extrahieren einer Kopie oder Annäherung eines proprietären Modells durch wiederholte Abfragen.
​
Multi-Agenten-System: Ein System, das aus mehreren interagierenden KI-Agenten besteht, von denen jeder potenziell unterschiedliche Fähigkeiten und Ziele hat.
​
OPA (Open Policy Agent): Eine Open-Source-Richtlinien-Engine, die eine einheitliche Durchsetzung von Richtlinien über den gesamten Stack hinweg ermöglicht.
​
Datenschutzwahrendes Maschinelles Lernen (Privacy-Preserving Machine Learning, PPML): Techniken und Methoden zum Trainieren und Bereitstellen von ML-Modellen unter Wahrung der Privatsphäre der Trainingsdaten.
​
Prompt Injection: Ein Angriff, bei dem bösartige Anweisungen in Eingaben eingebettet werden, um das beabsichtigte Verhalten eines Modells zu überschreiben.
​
RAG (Retrieval-Augmented Generation): Eine Technik, die große Sprachmodelle verbessert, indem relevante Informationen aus externen Wissensquellen abgerufen werden, bevor eine Antwort generiert wird.
​
Red-Teaming: Die Praxis, KI-Systeme aktiv zu testen, indem simulierte Angriffe durchgeführt werden, um Schwachstellen zu identifizieren.
​
SBOM (Software Bill of Materials): Eine formale Aufzeichnung, die die Details und Lieferkettenbeziehungen verschiedener Komponenten enthält, die beim Erstellen von Software oder KI-Modellen verwendet werden.
​
SHAP (SHapley Additive exPlanations): Ein spieltheoretischer Ansatz zur Erklärung der Ausgabe eines beliebigen Machine-Learning-Modells durch Berechnung des Beitrags jeder Eigenschaft zur Vorhersage.
​
Supply-Chain-Angriff: Kompromittierung eines Systems durch Angriff auf weniger sichere Elemente in seiner Lieferkette, wie z. B. Drittanbieter-Bibliotheken, Datensätze oder vortrainierte Modelle.
​
Transferlernen: Eine Technik, bei der ein für eine Aufgabe entwickeltes Modell als Ausgangspunkt für ein Modell zu einer zweiten Aufgabe wiederverwendet wird.
​
Vektor-Datenbank: Eine spezialisierte Datenbank, die zur Speicherung hochdimensionaler Vektoren (Embeddings) entwickelt wurde und effiziente Ähnlichkeitssuchen ermöglicht.
​
Schwachstellen-Scan: Automatisierte Werkzeuge, die bekannte Sicherheitsschwachstellen in Softwarekomponenten, einschließlich KI-Frameworks und Abhängigkeiten, identifizieren.
​
Wasserzeichen: Techniken zum Einbetten von nicht wahrnehmbaren Markierungen in KI-generierte Inhalte, um deren Herkunft zu verfolgen oder die KI-Generierung zu erkennen.
​
Zero-Day-Schwachstelle: Eine zuvor unbekannte Schwachstelle, die Angreifer ausnutzen können, bevor Entwickler einen Patch erstellen und bereitstellen.

## Anhang B: Referenzen

### TODO

## Anhang C: KI-Sicherheitssteuerung & Dokumentation

### Zielsetzung

Dieser Anhang liefert grundlegende Anforderungen für die Einrichtung organisatorischer Strukturen, Richtlinien und Prozesse zur Steuerung der KI-Sicherheit während des gesamten Systemlebenszyklus.

---

### AC.1 AI-Risikomanagement-Rahmenwerk-Einführung

Bereitstellung eines formalen Rahmens zur Identifizierung, Bewertung und Minderung von KI-spezifischen Risiken im gesamten Systemlebenszyklus.

 #AC.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass eine KI-spezifische Risikobewertungsmethodik dokumentiert und umgesetzt wird.
 #AC.1.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Risikobewertungen zu wichtigen Zeitpunkten im KI-Lebenszyklus und vor wesentlichen Änderungen durchgeführt werden.
 #AC.1.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob der Risikomanagementrahmen mit den etablierten Standards (z. B. NIST AI RMF) übereinstimmt.

---

### AC.2 KI-Sicherheitsrichtlinie & -verfahren

Definieren und durchsetzen von organisatorischen Standards für die sichere Entwicklung, Bereitstellung und den Betrieb von KI.

 #AC.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob dokumentierte KI-Sicherheitsrichtlinien vorhanden sind.
 #AC.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtlinien mindestens einmal jährlich und nach wesentlichen Änderungen der Bedrohungslandschaft überprüft und aktualisiert werden.
 #AC.2.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Richtlinien alle AISVS-Kategorien und anwendbaren regulatorischen Anforderungen abdecken.

---

### AC.3 Rollen und Verantwortlichkeiten für AI-Sicherheit

Etablieren Sie eine klare Verantwortlichkeit für die KI-Sicherheit in der gesamten Organisation.

 #AC.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Sicherheitsrollen und -verantwortlichkeiten dokumentiert sind.
 #AC.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass verantwortliche Personen über die entsprechende Sicherheitsexpertise verfügen.
 #AC.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für KI-Systeme mit hohem Risiko ein KI-Ethikausschuss oder ein Governance-Gremium eingerichtet wird.

---

### AC.4 Durchsetzung der Ethikrichtlinien für Künstliche Intelligenz

Sichern Sie, dass KI-Systeme gemäß den festgelegten ethischen Prinzipien arbeiten.

 #AC.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ethische Richtlinien für die Entwicklung und den Einsatz von KI vorhanden sind.
 #AC.4.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um ethische Verstöße zu erkennen und zu melden.
 #AC.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob regelmäßige ethische Bewertungen der eingesetzten KI-Systeme durchgeführt werden.

---

### AC.5 Überwachung der Einhaltung von KI-Vorschriften

Behalten Sie die Einhaltung und das Bewusstsein für sich entwickelnde KI-Vorschriften bei.

 #AC.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Prozesse vorhanden sind, um anwendbare KI-Vorschriften zu identifizieren.
 #AC.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Einhaltung aller gesetzlichen Anforderungen bewertet wird.
 #AC.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass regulatorische Änderungen zeitnahe Überprüfungen und Aktualisierungen von KI-Systemen auslösen.

### AC.6 Governance, Dokumentation und Prozess von Trainingsdaten

 #1.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass nur Datensätze, die auf Qualität, Repräsentativität, ethische Herkunft und Lizenzkonformität überprüft wurden, zugelassen werden, um Risiken wie Manipulation, eingebettete Voreingenommenheit und Verletzung geistigen Eigentums zu reduzieren.
 #1.1.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch gegenseitige Überprüfungen der Gutachter oder durch Konsens gewährleistet ist.
 #1.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass für bedeutende Trainingsdatensätze „Datenkarten“ oder „Datenblätter für Datensätze“ geführt werden, die Merkmale, Motivation, Zusammensetzung, Erhebungsprozesse, Vorverarbeitung sowie empfohlene und nicht empfohlene Verwendungszwecke detailliert beschreiben.
 #1.3.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass identifizierte Verzerrungen durch dokumentierte Strategien wie Neuausgleich, gezielte Datenaugmentation, algorithmische Anpassungen (z. B. Pre-Processing-, In-Processing-, Post-Processing-Techniken) oder Neugewichtung gemindert werden und die Auswirkungen der Minderung sowohl auf die Fairness als auch auf die Gesamtleistung des Modells bewertet werden.
 #1.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Fairness-Metriken nach dem Training bewertet und dokumentiert werden.
 #1.3.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob eine Lifecycle-Bias-Management-Richtlinie Verantwortliche und Überprüfungsintervalle zuweist.
 #1.4.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch klare Richtlinien, gegenseitige Überprüfungen durch Gutachter, Konsensmechanismen (z. B. Überwachung der Übereinstimmung zwischen den Annotatoren) und definierte Prozesse zur Lösung von Diskrepanzen gewährleistet ist.
 #1.4.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für die Sicherheit, den Schutz oder die Fairness kritische Labels (z. B. die Identifizierung toxischer Inhalte, kritische medizinische Befunde) einer obligatorischen unabhängigen Doppelprüfung oder einer gleichwertigen robusten Überprüfung unterzogen werden.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Kennzeichnungsrichtlinien und Anweisungen umfassend, versioniert und von Kollegen überprüft sind.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Datenschemata für Labels klar definiert und versioniert sind.
 #1.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Datensätze auf darstellungsbedingte Ungleichgewichte und potenzielle Vorurteile hinsichtlich gesetzlich geschützter Merkmale (z. B. Rasse, Geschlecht, Alter) sowie anderer ethisch sensibler Merkmale, die für das Anwendungsgebiet des Modells relevant sind (z. B. sozioökonomischer Status, Standort), profiliert werden.
 #1.5.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass manuelle Stichprobenprüfungen durch Fachexperten eine statistisch signifikante Stichprobe abdecken (z. B. ≥1 % oder 1.000 Proben, je nachdem, was größer ist, oder gemäß Risikobewertung), um subtile Qualitätsprobleme zu identifizieren, die von der Automatisierung nicht erfasst werden.
 #1.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ausgelagerte oder crowdsourcede Kennzeichnungsworkflows technische/prozedurale Schutzmaßnahmen enthalten, um die Vertraulichkeit und Integrität der Daten, die Qualität der Kennzeichnungen zu gewährleisten und Datenlecks zu verhindern.
 #1.5.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Abhilfeschritte an Provenanzaufzeichnungen angehängt sind.
 #1.6.2    Level: 2    Rolle: D/V
 Verifizieren Sie, dass markierte Proben vor dem Training eine manuelle Überprüfung auslösen.
 #1.6.3    Level: 2    Rolle: V
 Überprüfen Sie, dass die Ergebnisse in das Sicherheitsdossier des Modells einfließen und die fortlaufende Bedrohungsaufklärung informieren.
 #1.6.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Erkennungslogik mit neuen Bedrohungsinformationen aktualisiert wird.
 #1.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Online-Lernpipelines die Verteilungsverschiebung überwachen.
 #1.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Workflows zum Löschen von Trainingsdaten sowohl Primär- als auch abgeleitete Daten löschen und die Auswirkungen auf das Modell bewertet werden, und dass die Auswirkungen auf betroffene Modelle bewertet und gegebenenfalls behoben werden (z. B. durch erneutes Training oder Neukalibrierung).
 #1.7.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um den Umfang und den Status der Zustimmung des Benutzers (und deren Widerruf) für in der Schulung verwendete Daten nachzuverfolgen und zu respektieren, und dass diese Zustimmung validiert wird, bevor Daten in neue Trainingsprozesse oder bedeutende Modellaktualisierungen einfließen.
 #1.7.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Workflows jährlich getestet und protokolliert werden.
 #1.8.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Drittanbieter von Daten, einschließlich Anbieter vortrainierter Modelle und externer Datensätze, eine Überprüfung der Sicherheit, des Datenschutzes, der ethischen Beschaffung und der Datenqualität durchlaufen, bevor deren Daten oder Modelle integriert werden.
 #1.8.2    Level: 1    Rolle: D
 Überprüfen Sie, ob externe Übertragungen TLS/Authentifizierung und Integritätsprüfungen verwenden.
 #1.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass hochriskante Datenquellen (z. B. Open-Source-Datensätze mit unbekannter Herkunft, nicht geprüfte Anbieter) einer verstärkten Prüfung unterzogen werden, wie beispielsweise einer isolierten Analyse, umfangreichen Qualitäts- und Bias-Überprüfungen sowie gezielter Erkennung von Vergiftungen, bevor sie in sensiblen Anwendungen verwendet werden.
 #1.8.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass vor dem Feinabstimmen oder der Bereitstellung vortrainierte Modelle, die von Dritten stammen, auf eingebettete Verzerrungen, potenzielle Hintertüren, die Integrität ihrer Architektur und die Herkunft der ursprünglichen Trainingsdaten bewertet werden.
 #1.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass bei Verwendung von adversarialem Training die Erstellung, Verwaltung und Versionierung von adversarialen Datensätzen dokumentiert und kontrolliert wird.
 #1.5.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass der Einfluss des Trainings zur adversarialen Robustheit auf die Modellleistung (sowohl bei sauberen als auch bei adversarialen Eingaben) und die Fairness-Metriken bewertet, dokumentiert und überwacht wird.
 #1.5.4    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass Strategien für adversariales Training und Robustheit periodisch überprüft und aktualisiert werden, um sich entwickelnden Techniken von adversarialen Angriffen entgegenzuwirken.
 #1.4.2    Level: 2    Rolle: D/V
 Verifizieren Sie, dass fehlgeschlagene Datensätze mit Prüfpfaden isoliert werden.
 #1.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Qualitätskontrollen minderwertige Datensätze blockieren, es sei denn, Ausnahmen werden genehmigt.
 #1.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Generierungsprozess, die Parameter und der beabsichtigte Verwendungszweck der synthetischen Daten dokumentiert sind.
 #1.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass synthetische Daten vor der Verwendung im Training auf Bias, Datenschutzverletzungen und Repräsentationsprobleme risikobewertet werden.
 #1.12.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Warnungen für verdächtige Zugriffsereignisse erzeugt und umgehend untersucht werden.
 #1.13.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob für alle Trainingsdatensätze explizite Aufbewahrungsfristen definiert sind.
 #1.13.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Datensätze am Ende ihres Lebenszyklus automatisch ablaufen, gelöscht oder zur Löschung überprüft werden.
 #1.13.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Aufbewahrungs- und Löschaktionen protokolliert und überprüfbar sind.
 #1.14.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Anforderungen an die Datenresidenz und grenzüberschreitende Übertragungen für alle Datensätze identifiziert und durchgesetzt werden.
 #1.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass branchenspezifische Vorschriften (z. B. Gesundheitswesen, Finanzwesen) bei der Datenverarbeitung identifiziert und berücksichtigt werden.
 #1.14.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Einhaltung der relevanten Datenschutzgesetze (z. B. DSGVO, CCPA) dokumentiert und regelmäßig überprüft wird.
 #1.16.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Mechanismen vorhanden sind, um auf Anfragen von betroffenen Personen bezüglich Zugang, Berichtigung, Einschränkung oder Widerspruch zu reagieren.
 #1.16.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Anfragen innerhalb der gesetzlich vorgeschriebenen Fristen protokolliert, verfolgt und erfüllt werden.
 #1.16.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Prozesse für die Rechte der betroffenen Personen regelmäßig auf Wirksamkeit getestet und überprüft werden.
 #1.17.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass eine Auswirkungsanalyse durchgeführt wird, bevor eine Datensatzversion aktualisiert oder ersetzt wird, die Modellleistung, Fairness und Compliance abdeckt.
 #1.17.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Auswirkungsanalyse dokumentiert und von den relevanten Interessengruppen überprüft werden.
 #1.17.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Rollback-Pläne vorhanden sind, falls neue Versionen unakzeptable Risiken oder Rückschritte einführen.
 #1.18.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle an der Datenannotation beteiligten Mitarbeiter auf ihren Hintergrund überprüft wurden und in Datensicherheit sowie Datenschutz geschult sind.
 #1.18.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Mitarbeiter, die mit der Annotation beschäftigt sind, Vertraulichkeits- und Geheimhaltungsvereinbarungen unterschreiben.
 #1.18.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Annotationsplattformen Zugangskontrollen durchsetzen und Insider-Bedrohungen überwachen.

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anhang D: KI-gestützte Governance und Verifikation der sicheren Programmierung

### Zielsetzung

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für die sichere und effektive Nutzung von KI-unterstützten Codierwerkzeugen während der Softwareentwicklung, um Sicherheit und Rückverfolgbarkeit über den gesamten SDLC hinweg zu gewährleisten.

---

### AD.1 KI-unterstützter Secure-Coding-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Software-Entwicklungslebenszyklus (SSDLC) der Organisation, ohne bestehende Sicherheitsbarrieren zu schwächen.

 #AD.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob ein dokumentierter Workflow beschreibt, wann und wie KI-Tools Code generieren, umgestalten oder überprüfen dürfen.
 #AD.1.2    Level: 2    Rolle: D
 Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Testen, Bereitstellung).
 #AD.1.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Metriken (z. B. Schwachstellendichte, mittlere Erkennungszeit) für KI-generierten Code erfasst und mit ausschließlich menschlichen Basiswerten verglichen werden.

---

### AD.2 Qualifizierung von KI-Tools & Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Codierwerkzeuge vor der Einführung auf Sicherheitsfunktionen, Risiken und Auswirkungen auf die Lieferkette bewertet werden.

 #AD.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI-Werkzeug Missbrauch, Modell-Inversion, Datenleckage und Risiken in der Abhängigkeitskette identifiziert.
 #AD.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Tool-Evaluierungen statische/dynamische Analysen aller lokalen Komponenten sowie die Bewertung von SaaS-Endpunkten (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen.
 #AD.2.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Bewertungen einem anerkannten Rahmenwerk folgen und nach großen Versionsänderungen erneut durchgeführt werden.

---

### AD.3 Sicheres Prompt- und Kontextmanagement

Verhindern Sie die Weitergabe von Geheimnissen, proprietärem Code und persönlichen Daten beim Erstellen von Eingabeaufforderungen oder Kontexten für KI-Modelle.

 #AD.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass schriftliche Anweisungen das Senden von Geheimnissen, Zugangsdaten oder klassifizierten Daten in Eingabeaufforderungen untersagen.
 #AD.3.2    Level: 2    Rolle: D
 Überprüfen Sie, ob technische Kontrollen (clientseitige Schwärzung, genehmigte Kontextfilter) sensible Artefakte automatisch entfernen.
 #AD.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Eingabeaufforderungen und Antworten tokenisiert, während der Übertragung und im Ruhezustand verschlüsselt sind und die Aufbewahrungsfristen der Datenklassifizierungsrichtlinie entsprechen.

---

### AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt wurden, bevor der Code zusammengeführt oder bereitgestellt wird.

 #AD.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass von KI generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.
 #AD.4.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass automatisierte Scanner (SAST/IAST/DAST) bei jedem Pull Request mit KI-generiertem Code ausgeführt werden und bei kritischen Ergebnissen das Zusammenführen blockieren.
 #AD.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob differentielles Fuzz-Testing oder eigenschaftsbasierte Tests sicherheitskritische Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.

---

### AD.5 Erklärbarkeit und Rückverfolgbarkeit von Code-Vorschlägen

Geben Sie Prüfern und Entwicklern Einblicke darüber, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

 #AD.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Aufforderungs-/Antwortpaare mit Commit-IDs protokolliert werden.
 #AD.5.2    Level: 2    Rolle: D
 Überprüfen Sie, ob Entwickler Modellzitate (Trainingsausschnitte, Dokumentation) bereitstellen können, die eine Empfehlung unterstützen.
 #AD.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Erklärbarkeitsberichte zusammen mit Designartefakten gespeichert und in Sicherheitsüberprüfungen referenziert werden, um die Rückverfolgbarkeitsprinzipien der ISO/IEC 42001 zu erfüllen.

---

### AD.6 Kontinuierliches Feedback & Modell-Feinabstimmung

Verbessern Sie die Sicherheitsleistung des Modells im Laufe der Zeit und verhindern Sie gleichzeitig negative Abweichungen.

 #AD.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Entwickler unsichere oder nicht konforme Vorschläge markieren können und dass diese Markierungen nachverfolgt werden.
 #AD.6.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass aggregiertes Feedback die periodische Feinabstimmung oder retrieval-unterstützte Generierung mit geprüften Secure-Coding-Korpora (z. B. OWASP Cheat Sheets) informiert.
 #AD.6.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass ein Closed-Loop-Evaluierungsharness nach jedem Fine-Tune Regressionsprüfungen durchführt; Sicherheitsmetriken müssen vor der Bereitstellung frühere Baselines erreichen oder übertreffen.

---

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Anhang E: Beispielhafte Werkzeuge und Frameworks

### Zielsetzung

Dieses Kapitel enthält Beispiele für Werkzeuge und Frameworks, die die Umsetzung oder Erfüllung einer bestimmten AISVS-Anforderung unterstützen können. Diese sind nicht als Empfehlungen oder Befürwortungen durch das AISVS-Team oder das OWASP GenAI Security Project zu verstehen.

---

### AE.1 Governance von Trainingsdaten und Bias-Management

Werkzeuge für Datenanalyse, Governance und Bias-Management.

 #AE.1.1    Abschnitt: 1.1
 Dateninventar-Tooling: Tooling für das Management des Dateninventars wie...
 #AE.1.2    Abschnitt: 1.2
 Verschlüsselung während der Übertragung Verwenden Sie TLS für HTTPS-basierte Anwendungen, mit Werkzeugen wie openSSL und Python's`ssl`Bibliothek.

---

### AE.2 Benutzer-Input-Validierung

Werkzeuge zur Verarbeitung und Validierung von Benutzereingaben.

 #AE.2.1    Abschnitt: 2.1
 Prompt-Injection-Abwehrwerkzeuge: Verwenden Sie Guardrail-Werkzeuge wie NVIDIAs NeMo oder Guardrails AI.

---

