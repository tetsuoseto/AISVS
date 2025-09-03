## Frontispiz

### Über den Standard

Der Artificial Intelligence Security Verification Standard (AISVS) ist ein gemeinschaftsgetriebenes Verzeichnis von Sicherheitsanforderungen, das Datenwissenschaftlerinnen und Datenwissenschaftler, MLOps-Ingenieurinnen und -Ingenieure, Softwarearchitektinnen und -Architekten, Entwicklerinnen und Entwickler, Testerinnen und Tester, Sicherheitsfachleute, Tool-Anbieter, Regulierungsbehörden und Verbraucherinnen und Verbraucher verwenden können, um vertrauenswürdige KI‑gestützte Systeme und Anwendungen zu entwerfen, zu erstellen, zu testen und zu verifizieren. Es bietet eine gemeinsame Sprache zur Festlegung von Sicherheitskontrollen über den gesamten KI‑Lebenszyklus hinweg – von der Datenerfassung und Modellentwicklung bis zur Bereitstellung und fortlaufender Überwachung – damit Organisationen die Widerstandsfähigkeit, Privatsphäre und Sicherheit ihrer KI‑Lösungen messen und verbessern können.

### Urheberrecht und Lizenz

Version 0.1 (Erste öffentliche Fassung - In Bearbeitung), 2025  

![license](images/license.png)
Urheberrecht © 2025 The AISVS Project.  

Veröffentlicht unter derCreative Commons Attribution‑ShareAlike 4.0 International License.
Für jede Wiederverwendung oder Weiterverteilung müssen Sie anderen eindeutig die Lizenzbedingungen dieses Werks mitteilen.

### Projektleiter

Jim Manico
Aras “Russ” Memisyazici

### Mitwirkende und Gutachter

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS ist ein brand‑new Standard, der speziell entwickelt wurde, um die einzigartigen Sicherheitsherausforderungen von artificial‑intelligence Systemen anzugehen. Während es sich von breiteren Best Practices der Sicherheit inspirieren lässt, wurde jede Anforderung in AISVS von Grund auf entwickelt, um das KI-Bedrohungsumfeld abzubilden und Organisationen dabei zu helfen, sicherere und widerstandsfähigere KI-Lösungen zu entwickeln.

## Vorwort

Willkommen beim Sicherheitsverifizierungsstandard für Künstliche Intelligenz (AISVS) Version 1.0!

### Einführung

Im Jahr 2025 durch eine gemeinschaftliche Anstrengung der Community gegründet, definiert AISVS die Sicherheitsanforderungen, die bei der Gestaltung, Entwicklung, Bereitstellung und dem Betrieb moderner KI‑Modelle, Pipelines und KI‑gestützter Dienste zu beachten sind.

AISVS v1.0 repräsentiert die gemeinsame Arbeit seiner Projektleitungen, der Arbeitsgruppe und der breiten Community-Beiträge, um eine pragmatische, testbare Basis zur Absicherung von KI-Systemen zu schaffen.

Unser Ziel mit dieser Veröffentlichung ist es, AISVS einfach einführbar zu machen, während wir uns gleichzeitig eng auf den definierten Umfang konzentrieren und die sich rasch entwickelnde Risikolandschaft, die für KI einzigartig ist, adressieren.

### Kernziele für AISVS Version 1.0

Version 1.0 wird mit mehreren Leitprinzipien erstellt.

#### Gut definierter Umfang

Jede Anforderung muss mit dem Namen und der Mission von AISVS übereinstimmen:

Künstliche Intelligenz – Kontrollen arbeiten auf der KI/ML-Ebene (Daten, Modell, Pipeline oder Inferenz) und liegen in der Verantwortung der KI-Praktiker.
Sicherheit – Anforderungen mindern direkt identifizierte Sicherheits-, Datenschutz- oder Sicherheitsrisiken.
Verifikation – Die Sprache ist so verfasst, dass die Konformität objektiv verifiziert werden kann.
Standard – Abschnitte folgen einer konsistenten Struktur und Terminologie, um eine kohärente Referenz zu bilden.
​
---

Durch die Befolgung von AISVS können Organisationen systematisch die Sicherheitslage ihrer KI-Lösungen bewerten und stärken und so eine Kultur der sicheren KI-Entwicklung fördern.

## Verwendung der AISVS

Der Artificial Intelligence Security Verification Standard (AISVS) definiert Sicherheitsanforderungen für moderne KI-Anwendungen und -Dienste und fokussiert sich auf Aspekte, die unter der Kontrolle der Anwendungsentwickler stehen.

Der AISVS richtet sich an alle, die die Sicherheit von KI-Anwendungen entwickeln oder bewerten, einschließlich Entwickler, Architekten, Sicherheitsingenieure und Auditoren. Dieses Kapitel stellt die Struktur und Anwendung des AISVS vor, einschließlich seiner Verifizierungsstufen und der vorgesehenen Anwendungsfälle.

### Sicherheitsverifizierungsstufen der Künstlichen Intelligenz

Die AISVS definiert drei aufsteigende Stufen der Sicherheitsüberprüfung. Jede Stufe fügt Tiefe und Komplexität hinzu und ermöglicht es Organisationen, ihre Sicherheitslage an das Risikoniveau ihrer KI-Systeme anzupassen.

Organisationen können auf Stufe 1 beginnen und schrittweise höhere Stufen übernehmen, wenn die Sicherheitsreife zunimmt und die Bedrohungsbelastung steigt.

#### Definition der Ebenen

Jede Anforderung in AISVS v1.0 ist einer der folgenden Ebenen zugewiesen:

 Level 1 Anforderungen

Stufe 1 umfasst die kritischsten und grundlegendsten Sicherheitsanforderungen. Diese konzentrieren sich darauf, gängige Angriffe zu verhindern, die nicht von anderen Voraussetzungen oder Schwachstellen abhängen. Die meisten Kontrollen der Stufe 1 sind entweder einfach umzusetzen oder so wesentlich, dass sich der Aufwand lohnt.

 Anforderungen der Stufe 2

Stufe 2 behandelt fortgeschrittene oder weniger gängige Angriffe sowie mehrschichtige Verteidigungen gegen weit verbreitete Bedrohungen. Diese Anforderungen können eine komplexere Logik erfordern oder auf spezifische Angriffs-Voraussetzungen abzielen.

 Anforderungen der Stufe 3

Stufe 3 umfasst Kontrollen, die in der Regel schwerer umzusetzen sind oder deren Anwendbarkeit situativ ist. Diese stellen oft mehrschichtige Verteidigungsmaßnahmen dar oder Gegenmaßnahmen gegen Nischenangriffe, gezielte Angriffe oder hochkomplexe Angriffe.

#### Rolle (D/V)

Jede AISVS-Anforderung ist entsprechend dem primären Publikum gekennzeichnet:

D – entwicklerorientierte Anforderungen
V – Verifizierer-/prüferorientierte Anforderungen
D/V – Relevant für Entwickler und Verifizierer.

## C1 Trainingsdaten-Governance und Bias-Management

### Kontrollziel

Trainingsdaten müssen beschafft, verarbeitet und gepflegt werden, um Provenienz, Sicherheit, Qualität und Fairness zu bewahren. Dadurch werden gesetzliche Pflichten erfüllt und das Risiko von Voreingenommenheit, Datenvergiftung oder Datenschutzverletzungen reduziert, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinflussen könnten.

---

### C1.1 Provenienz der Trainingsdaten

Führen Sie ein verifizierbares Inventar aller Datensätze, akzeptieren Sie ausschließlich vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Auditierbarkeit.

 #1.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Ursprung, Verwalter/Eigentümer, Lizenz, Sammlungsmethode, Verwendungsbeschränkungen und Verarbeitungshistorie) gepflegt wird.
 #1.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Verarbeitung von Trainingsdaten unnötige Merkmale, Attribute oder Felder ausschließt (z. B. ungenutzte Metadaten, sensible PII, geleakte Testdaten).
 #1.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Datensatzänderungen einem protokollierten Genehmigungs-Workflow unterliegen.
 #1.1.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Datensätze oder Teilmengen, soweit möglich, mit Wasserzeichen versehen oder durch Fingerprinting gekennzeichnet werden.

---

### C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie sie im Ruhezustand und bei der Übertragung und validieren Sie deren Integrität, um Manipulationen, Diebstahl oder Datenvergiftung zu verhindern.

 #1.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Zugriffskontrollen die Speicherung von Trainingsdaten und Datenpipelines schützen.
 #1.2.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Zugriffe auf Trainingsdaten protokolliert werden, einschließlich Benutzer, Zeit und Aktion.
 #1.2.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Trainingsdatensätze sowohl bei der Übertragung als auch im Ruhezustand verschlüsselt sind, unter Verwendung branchenüblicher kryptografischer Algorithmen und Praktiken der Schlüsselverwaltung.
 #1.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Hashwerte oder digitale Signaturen verwendet werden, um die Integrität der Trainingsdaten während der Speicherung und Übertragung sicherzustellen.
 #1.2.5    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass automatisierte Erkennungstechniken angewendet werden, um unautorisierte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.
 #1.2.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.
 #1.2.7    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Versionen von Trainingsdatensätzen eindeutig identifiziert, unveränderlich gespeichert und nachprüfbar sind, um Rollback und forensische Analysen zu unterstützen.

---

### C1.3 Qualität, Integrität und Sicherheit der Beschriftung von Trainingsdaten

Schützen Sie Labels und verlangen Sie eine technische Prüfung für kritische Daten.

 #1.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, dass kryptografische Hashwerte oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität sicherzustellen.
 #1.3.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Beschriftungsschnittstellen und Beschriftungsplattformen strenge Zugriffskontrollen durchsetzen, manipulationssichere Audit-Protokolle aller Beschriftungsvorgänge führen und vor unbefugten Änderungen schützen.
 #1.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch bei der Übertragung geschwärzt, anonymisiert oder verschlüsselt werden.

---

### C1.4 Qualität der Trainingsdaten und Sicherheitsgarantien

Kombinieren Sie automatisierte Validierung, manuelle Spot-Checks und protokollierte Behebungsmaßnahmen, um die Zuverlässigkeit des Datensatzes sicherzustellen.

 #1.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests bei jeder Datenaufnahme oder wesentlichen Datenumwandlung Formatfehler und Nullwerte erkennen.
 #1.4.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Datenvergiftung und Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Embedding-Analyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügung von Backdoor-Auslösern, Rollenwechsel-Befehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren.
 #1.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass geeignete Abwehrmaßnahmen implementiert und basierend auf der Risikobewertung auf relevante Modelle abgestimmt sind, z. B. Adversarial Training (unter Verwendung generierter adversarischer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken.
 #1.4.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass automatisch generierte Labels (z. B. mittels LLMs oder schwacher Überwachung) Konfidenzschwellen und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit niedriger Konfidenz zu erkennen.
 #1.4.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass automatisierte Tests Label-Verzerrungen bei jeder Datenaufnahme oder jeder signifikanten Datenumwandlung erkennen.

---

### C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie den vollständigen Weg jedes Datenpunkts vom Ursprung zur Modell-Eingabe, um Nachvollziehbarkeit und Vorfallreaktion zu ermöglichen.

 #1.5.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Herkunft jedes Datenpunkts, einschließlich aller Transformationen, Datenaugmentationen und Zusammenführungen, aufgezeichnet wird und rekonstruiert werden kann.
 #1.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Datenherkunftsaufzeichnungen unveränderlich, sicher gespeichert und für Audits zugänglich sind.
 #1.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Datenherkunftsnachverfolgung auch synthetische Daten abdeckt, die mittels datenschutzfreundlicher oder generativer Techniken erzeugt werden, und dass alle synthetischen Daten in der gesamten Pipeline deutlich gekennzeichnet und von echten Daten unterscheidbar sind.

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

## C2 Validierung von Benutzereingaben

### Kontrollziel

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injektionsangriffe können Systemanweisungen außer Kraft setzen, sensible Daten offenlegen oder das Modell auf ein Verhalten lenken, das nicht erlaubt ist. Sofern dedizierte Filter und Instruktionshierarchien vorhanden sind, zeigt die Forschung, dass „Multi-Shot“-Jailbreaks, die sehr langen Kontextfenster ausnutzen, wirksam sein werden. Auch subtile adversariale Perturbationsangriffe – wie Homoglyphen-Tausch oder Leetspeak – können unauffällig die Entscheidungen eines Modells verändern.

---

### C2.1 Verteidigung gegen Prompt-Injektion

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik setzen eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung der Anweisungs-Hierarchie ein.

 #2.1.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektionsmuster gefiltert werden (Jailbreak-Schlüsselwörter, "ignore previous", Rollenspiel-Ketten, indirekte HTML/URL-Angriffe).
 #2.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob das System eine Anweisungshierarchie durchsetzt, in der System- oder Entwicklermeldungen Benutzeranweisungen überschreiben, auch nach der Erweiterung des Kontextfensters.
 #2.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass adversarische Evaluierungstests (z. B. Red-Team „many-shot“-Prompts) vor jeder Veröffentlichung eines Modells oder eines Prompt-Templates durchgeführt werden, mit Schwellenwerten der Erfolgsrate und automatischen Blockern zur Verhinderung von Regressionen.
 #2.1.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Prompts, die aus Inhalten Dritter stammen (Webseiten, PDFs, E-Mails), in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in den Hauptprompt zusammengeführt werden.
 #2.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filter-Regeln, alle Versionen von Klassifikator-Modellen und alle Änderungen der Blockliste versionskontrolliert und auditierbar sind.

---

### C2.2 Widerstand gegen adversarische Beispiele

Modelle der Verarbeitung natürlicher Sprache (NLP) sind nach wie vor anfällig für subtile Zeichen- oder Wortebenen-Perturbationen, die Menschen oft übersehen, während die Modelle dazu neigen, sie falsch zu klassifizieren.

 #2.2.1    Level: 1    Rolle: D
 Überprüfen Sie, dass grundlegende Schritte zur Eingabennormalisierung (Unicode NFC, Homoglyphenabbildung, Leerzeichenbereinigung) vor der Tokenisierung ausgeführt werden.
 #2.2.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die statistische Anomalieerkennung Eingaben mit einem ungewöhnlich hohen Editierabstand zu Sprachnormen, übermäßig vielen wiederholten Tokens oder abnormalen Embedding-Distanzen kennzeichnet.
 #2.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die Inferenz-Pipeline optionale adversarial-training–gehärtete Modellvarianten oder Verteidigungsschichten unterstützt (z. B. Randomisierung, defensive Distillation) für Hochrisiko-Endpunkte.
 #2.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass verdächtige adversarische Eingaben isoliert werden und mit vollständigen Payloads protokolliert werden (nach PII-Redaktion).
 #2.2.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsquote bekannter Angriffs-Suiten) über die Zeit verfolgt werden und Regressionen einen Release-Blocker auslösen.

---

### C2.3 Schema, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler verursachen, Prompt-Spillage über Felder hinweg auslösen und Ressourcenerschöpfung verursachen.  Strikte Schema-Durchsetzung ist ebenfalls eine Voraussetzung, wenn deterministische Tool-Aufrufe durchgeführt werden.

 #2.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabenschema definiert (JSON-Schema, Protobuf oder multimodale Entsprechung) und dass die Eingaben vor der Erstellung des Prompts validiert werden.
 #2.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Bytegrenzen überschreiten, mit einer sicheren Fehlermeldung abgewiesen werden und niemals stillschweigend abgeschnitten werden.
 #2.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Typprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder und Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.
 #2.3.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um einen algorithmischen DoS-Angriff zu verhindern.
 #2.3.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Validierungsfehler mit geschwärzten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheits-Triage zu unterstützen.

---

### C2.4 Inhalt und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die verbotenen Inhalte anfordern (wie illegale Anleitungen, Hassrede und urheberrechtlich geschützte Texte) und sie dann daran zu hindern, sich zu verbreiten.

 #2.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jeden Input auf Gewalt, Selbstverletzung, Hassrede, sexuelle Inhalte und illegale Anfragen bewertet, mit konfigurierbaren Schwellenwerten.
 #2.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Vervollständigungen erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergegeben werden.
 #2.4.3    Level: 2    Rolle: D
 Vergewissern Sie sich, dass das Screening-Modell oder der Regelsatz mindestens quartalsweise neu trainiert oder aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinien-Umgehungsmuster berücksichtigt werden.
 #2.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Screening benutzerspezifische Richtlinien (Alter, regionale Rechtsvorschriften) durch attributbasierte Regeln einhält, die zum Zeitpunkt der Anforderung aufgelöst werden.
 #2.4.5    Level: 3    Rolle: V
 Verifizieren Sie, dass Screening-Protokolle Konfidenzwerte des Klassifikators und Richtlinienkategorietags enthalten, die für SOC-Korrelation und zukünftige Red-Team-Wiederholungen verwendet werden.

---

### C2.5 Eingabe-Ratenbegrenzung und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe gegen KI-Systeme verhindern, indem sie die Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

 #2.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass pro Benutzer, pro IP und pro API-Schlüssel die Ratenbegrenzungen für alle Eingabe-Endpunkte durchgesetzt werden.
 #2.5.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Burst- und Dauer-Ratenbegrenzungen so abgestimmt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.
 #2.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Anfragen in schneller Folge, Eingabeüberflutung) automatisierte Blockierungen oder Eskalationen auslösen.
 #2.5.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und aufkommende Angriffsformen geprüft werden.

---

### C2.6 Multi-Modal Eingabevalidierung

KI-Systeme sollten eine robuste Validierung von nicht-textuellen Eingaben (Bilder, Audio, Dateien) vorsehen, um Injektion, Umgehung oder Ressourcenmissbrauch zu verhindern.

 #2.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audiodateien, Dateien) vor der Verarbeitung auf Typ, Größe und Format validiert werden.
 #2.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Dateien vor dem Import auf Malware und steganografische Nutzlasten gescannt werden.
 #2.6.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Bild- und Audioeingaben auf adversariale Perturbationen oder bekannte Angriffsmuster geprüft werden.
 #2.6.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass multimodale Eingabevalidierungsfehler protokolliert werden und Alarme zur Untersuchung auslösen.

---

### C2.7 Eingabenherkunft und Attribution

KI-Systeme sollten Auditing, Missbrauchsverfolgung und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

 #2.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.
 #2.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Provenienzmetadaten für alle verarbeiteten Eingaben beibehalten und nachprüfbar sind.
 #2.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Prüfung oder Blockierung unterzogen werden.

---

### C2.8 Echtzeit-adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsartenmuster anpassen und Echtzeitschutz mit kompiliertem Musterabgleich bieten.

 #2.8.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine hochleistungsfähige Echtzeit-Filterung mit minimaler Latenzbelastung zu ermöglichen.
 #2.8.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Bedrohungserkennungssysteme getrennte Musterbibliotheken für verschiedene Bedrohungskategorien pflegen (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle).
 #2.8.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die adaptive Bedrohungserkennung Machine-Learning-Modelle integriert, die die Bedrohungssensitivität basierend auf Angriffsfrequenz und Erfolgsraten aktualisieren.
 #2.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Echtzeit-Bedrohungsintelligenz-Feeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.
 #2.8.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass die Fehlalarmraten bei der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Beeinträchtigungen legitimer Anwendungsfälle zu minimieren.
 #2.8.6    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass kontextbezogene Bedrohungsanalyse die Eingabequelle, Verhaltensmuster des Benutzers und die Sitzungshistorie berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.
 #2.8.7    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungslatenz, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.

---

### C2.9 Multimodale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierung für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten bereitstellen, einschließlich spezifischer Arten der Bedrohungserkennung und Ressourcenisolierung.

 #2.9.1    Level: 1    Rolle: D/V
 Vergewissere dich, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren verfügt, die dokumentierte Bedrohungsmuster (Text: Prompt-Injektion, Bilder: Steganografie, Audio: Spektrogramm-Angriffe) sowie Erkennungsschwellen aufweisen.
 #2.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxen mit festgelegten Ressourcenlimits (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die jeweils für jeden Modalitätstyp spezifisch festgelegt sind und in Sicherheitsrichtlinien dokumentiert sind.
 #2.9.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Cross-Modal-Angriffserkennung koordinierte Angriffe erkennt, die sich über mehrere Eingabetypen hinweg erstrecken (z. B. steganografische Payloads in Bildern, kombiniert mit Prompt-Injektion im Text) und Korrelationsregeln sowie Alarmgenerierung verwendet.
 #2.9.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass multimodale Validierungsfehler eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsscores und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst.
 #2.9.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass modalitätsspezifische Inhaltsklassifizierer gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks aktualisiert werden, die über den Basisgrenzwerten liegen.

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

## C3 Modell-Lebenszyklus-Verwaltung & Änderungssteuerung

### Kontrollziel

KI-Systeme müssen Änderungskontrollprozesse implementieren, die unbefugte oder unsichere Modelländerungen daran hindern, die Produktion zu erreichen. Diese Kontrolle gewährleistet die Integrität des Modells über den gesamten Lebenszyklus--von der Entwicklung über den Einsatz bis zur Außerbetriebnahme--was eine schnelle Reaktion auf Vorfälle ermöglicht und die Verantwortlichkeit für alle Änderungen sicherstellt.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch den Einsatz kontrollierter Prozesse in die Produktion, wodurch Integrität, Nachvollziehbarkeit und Wiederherstellbarkeit gewährleistet werden.

---

### C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität gelangen in Produktionsumgebungen.

 #3.1.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizers) vor der Bereitstellung kryptografisch von autorisierten Parteien signiert sind.
 #3.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Modells zum Zeitpunkt der Bereitstellung validiert wird, und dass Fehler bei der Signaturprüfung das Laden des Modells verhindern.
 #3.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Modellprovenienzaufzeichnungen die Identität einer autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit dem Status Bestanden bzw. Nicht bestanden sowie einen Erstellungszeitstempel enthalten.
 #3.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Modellartefakte semantische Versionsnummern verwenden (MAJOR.MINOR.PATCH) und dass dokumentierte Kriterien vorliegen, die festlegen, wann jede Versionsebene erhöht wird.
 #3.1.5    Level: 2    Rolle: V
 Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar aufrechterhält, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.

---

### C3.2 Modellvalidierung und Tests

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Zuverlässigkeitsprüfungen bestehen.

 #3.2.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Modelle automatisierte Sicherheitsprüfungen durchlaufen, die Eingabevalidierung, Ausgabensanitisierung und Sicherheitsbewertungen umfassen, mit vorab vereinbarten organisatorischen Bestehen/Nichtbestehen-Schwellenwerten vor der Bereitstellung.
 #3.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Validierungsfehler die Bereitstellung des Modells automatisch blockieren, nachdem eine ausdrückliche Ausnahmengenehmigung durch vordefiniertes befugtes Personal mit dokumentierten geschäftlichen Begründungen erteilt wurde.
 #3.2.3    Level: 2    Rolle: V
 Verifizieren Sie, dass Testergebnisse kryptografisch signiert sind und unveränderlich mit dem spezifischen Modellversions-Hash verknüpft sind, der validiert wird.
 #3.2.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Notfallbereitstellungen eine dokumentierte Sicherheitsrisikobewertung sowie die Genehmigung durch eine vorher festgelegte Sicherheitsbehörde innerhalb der vorab vereinbarten Fristen erfordern.

---

### Kontrollierte Bereitstellung und Rollback

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

 #3.3.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern implementieren, basierend auf vorab vereinbarten Fehlerraten, Latenzschwellen oder Sicherheitswarnkriterien.
 #3.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Rollback-Funktionen den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.
 #3.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und dass die Bereitstellung bei jeder Abweichung fehlschlägt.
 #3.3.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Notabschaltfunktionen des Modells die Endpunkte innerhalb vordefinierter Reaktionszeiten deaktivieren können – entweder durch automatisierte Circuit-Breaker oder durch manuelle Kill-Schalter.
 #3.3.5    Level: 2    Rolle: V
 Überprüfen Sie, ob Rollback-Artefakte (frühere Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderlichem Speicher für die Vorfallreaktion aufbewahrt werden.

---

### C3.4 Änderungsverantwortlichkeit & Audit

Alle Änderungen am Lebenszyklus des Modells müssen nachvollziehbar und auditierbar sein.

 #3.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Auditprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Identität des Akteurs, eine Änderungsart und Vorher- und Nachherzustände enthalten.
 #3.4.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass der Zugriff auf das Audit-Log eine angemessene Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und einem Zeitstempel protokolliert werden.
 #3.4.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Prompt-Vorlagen und Systemmeldungen in Git-Repositories versioniert sind, mit obligatorischer Code-Review und Freigabe durch festgelegte Prüfer vor dem Deployment.
 #3.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Auditprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Schnappschüsse und Versionsangaben der Abhängigkeiten), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen.

---

### C3.5 Sichere Softwareentwicklungspraktiken

Die Modellentwicklung und die Trainingsprozesse müssen sicheren Praktiken folgen, um eine Kompromittierung zu verhindern.

 #3.5.1    Level: 1    Rolle: D
 Überprüfen Sie, ob Modellentwicklungs-, Test- und Produktionsumgebungen physisch oder logisch voneinander getrennt sind. Sie haben keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.
 #3.5.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.
 #3.5.3    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Trainingsdatenquellen vor der Verwendung in der Modellentwicklung durch Integritätsprüfungen validiert und über vertrauenswürdige Quellen authentifiziert werden, mit einer dokumentierten Herkunftskette.
 #3.5.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert werden und vor dem Training eine Peer-Review-Genehmigung erforderlich ist.

---

### C3.6 Modellstilllegung und Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme identifiziert werden.

 #3.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Modellstilllegungsprozesse automatisch Abhängigkeitsgraphen scannen, alle darauf zugreifenden Systeme identifizieren und vorab vereinbarte Vorankündigungsfristen vor der Stilllegung bereitstellen.
 #3.6.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ausrangierte Modellartefakte gemäß dokumentierter Richtlinien zur Datenaufbewahrung sicher gelöscht werden, entweder durch kryptografische Vernichtung oder durch Überschreibung mit mehreren Durchgängen, und dass verifizierte Vernichtungszertifikate vorliegen.
 #3.6.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Modellstilllegungsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden, und dass Modellsignaturen widerrufen werden, um eine Wiederverwendung zu verhindern.
 #3.6.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Notfall-Modellabschaltung den Zugriff auf das Modell innerhalb der vorab festgelegten Notfall-Reaktionszeiträume durch automatisierte Kill-Schalter deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.

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

## C4 Infrastruktur, Konfiguration und Bereitstellungssicherheit

### Kontrollziel

KI-Infrastruktur muss gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und Konfigurationen gelangen durch kontrollierte Prozesse in die Produktion, die Sicherheit, Integrität und Auditierbarkeit gewährleisten.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines in die Produktion, die Sicherheitsrichtlinien durchsetzen und unveränderliche Audit-Trails aufrechterhalten.

---

### C4.1 Laufzeitumgebungs-Isolation

Verhindern Sie Container-Ausbrüche und Privilegien-Eskalationen durch Kernel-Ebene-Isolationsprimitiven und Mandatory Access Controls.

 #4.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass alle KI-Container alle Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsbaselines dokumentierte erforderliche Fähigkeiten ablegen.
 #4.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denjenigen in vorab genehmigten Freigabelisten; bei Verstößen wird der Container beendet und Sicherheitswarnungen ausgelöst.
 #4.1.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt werden.
 #4.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die eBPF-basierte Laufzeitüberwachung (Falco, Tetragon oder Äquivalent) Versuche der Privilegienerhöhung erkennt und automatisch die betroffenen Prozesse innerhalb der organisatorischen Reaktionszeitvorgaben beendet.
 #4.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass hochrisikoreiche KI-Workloads in hardwareisolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsprüfung ausgeführt werden.

---

### C4.2 Sichere Build- und Deployment-Pipelines

Gewährleisten Sie kryptografische Integrität und Lieferkettensicherheit durch reproduzierbare Builds und signierte Artefakte.

 #4.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Infrastruktur als Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und Merge-Vorgänge mit CRITICAL- oder HIGH-Schweregradbefunden blockiert werden.
 #4.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Container-Builds reproduzierbar sind und über Builds hinweg identische SHA256 Hashes aufweisen, und erzeugen Sie SLSA Level 3 Provenanceattestationen, die mit Sigstore signiert sind.
 #4.2.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs enthalten und mit Cosign signiert sind, bevor der Push in die Registry erfolgt, und dass unsignierte Images bei der Bereitstellung abgelehnt werden.
 #4.2.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass CI/CD-Pipelines OIDC-Tokens von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Gültigkeitsdauer die in den organisatorischen Sicherheitsrichtlinien festgelegten Grenzwerte nicht überschreitet.
 #4.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Ausführung des Containers validiert werden, und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt.
 #4.2.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Build-Umgebungen in flüchtigen Containern oder VMs laufen, die keinen persistenten Speicher haben und vom Produktions-VPC-Netzwerk isoliert sind.

---

### C4.3 Netzwerksicherheit und Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerk mit Standard-Verweigerungsrichtlinien und verschlüsselter Kommunikation.

 #4.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Kubernetes-Netzwerkrichtlinien oder eine äquivalente Implementierung standardmäßig eingehenden und ausgehenden Verkehr verweigern und explizite Zulassungsregeln für erforderliche Ports (443, 8080 usw.) enthalten.
 #4.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.
 #4.3.3    Level: 2    Rolle: D/V
 Verifizieren Sie, dass ausgehender Verkehr durch HTTP/HTTPS-Proxys (Squid, Istio oder Cloud NAT-Gateways) mit Domänen-Whitelists gefiltert wird und blockierte Anfragen protokolliert werden.
 #4.3.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Inter-Service-Kommunikation mutual TLS verwendet, Zertifikate gemäß den organisatorischen Richtlinien rotiert werden und die Zertifikatvalidierung durchgesetzt wird (keine Skip-Verify-Flags).
 #4.3.5    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die KI-Infrastruktur in dedizierten VPCs/VNets läuft, keinen direkten Internetzugang hat und ausschließlich über NAT-Gateways oder Bastion-Hosts kommuniziert.

---

### C4.4 Geheimnisse & Kryptografische Schlüsselverwaltung

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatische Rotation mit Zero-Trust-Zugriff.

 #4.4.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager gespeichert sind und dort im Ruhezustand durch AES-256-Verschlüsselung geschützt sind.
 #4.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) mit Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie generiert werden.
 #4.4.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die Geheimnisrotation automatisiert erfolgt, dass die Bereitstellung ohne Ausfallzeit erfolgt und dass die Rotation sofort durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.
 #4.4.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.
 #4.4.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Auditprotokolle mit Benutzeridentitäten und Zeitstempeln aufgezeichnet wird.
 #4.4.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Secrets über Kubernetes-Secrets, gemountete Volumes oder Init-Containeren injiziert werden, und stellen Sie sicher, dass Secrets niemals in Umgebungsvariablen oder Images eingebettet werden.

---

### C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie unvertrauenswürdige KI-Modelle in sicheren Sandbox-Umgebungen mit umfassender Verhaltensanalyse.

 #4.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit --security-opt=no-new-privileges und --read-only ausgeführt werden.
 #4.5.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost ermöglichen, wobei alle externen Anfragen durch iptables-Regeln blockiert werden.
 #4.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Validierung von KI-Modellen automatisierte Red-Team-Tests mit organisationsweit festgelegter Testabdeckung und Verhaltensanalyse zur Backdoor-Erkennung umfasst.
 #4.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass ein KI-Modell erst dann in die Produktion überführt wird, wenn seine Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Auditprotokollen gespeichert sind.
 #4.5.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Umgebungen zwischen Evaluierungen vollständig gelöscht und aus Golden-Images neu erstellt werden, wobei das Dateisystem und der Arbeitsspeicher vollständig bereinigt werden.

---

### C4.6 Infrastruktur-Sicherheitsüberwachung

Infrastruktur kontinuierlich scannen und überwachen, mit automatisierter Behebung und Echtzeit-Alarmierung.

 #4.6.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Container-Images gemäß den organisatorischen Zeitplänen auf kritische Schwachstellen gescannt werden, die die Bereitstellung basierend auf organisatorischen Risikogrenzen blockieren.
 #4.6.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Infrastruktur die CIS-Benchmarks oder NIST SP 800-53-Kontrollen erfüllt, mit organisatorisch definierten Compliance-Schwellenwerten und automatisierter Behebung für fehlgeschlagene Prüfungen.
 #4.6.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Schwachstellen mit hohem Schweregrad gemäß den Zeitplänen des organisatorischen Risikomanagements behoben werden, mit Notfallmaßnahmen für aktiv ausgenutzte CVEs.
 #4.6.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Sicherheitswarnungen in SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung von CEF- oder STIX/TAXII-Formaten mit automatischer Anreicherung integriert werden.
 #4.6.5    Level: 3    Rolle: V
 Verifizieren Sie, dass Infrastrukturmetriken an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Berichten für das Management exportiert werden.
 #4.6.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) gemäß den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischem Rollback bei unbefugten Änderungen.

---

### C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

 #4.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die GPU-/TPU-Auslastung überwacht wird, Warnmeldungen bei organisatorisch festgelegten Schwellenwerten ausgelöst werden und automatische Skalierung oder Lastenausgleich gemäß Kapazitätsmanagementrichtlinien aktiviert ist.
 #4.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-Arbeitslastkennzahlen (Inferenzlatenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Monitoring-Anforderungen erfasst werden und mit der Auslastung der Infrastruktur korreliert sind.
 #4.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Kubernetes ResourceQuotas oder äquivalente Mechanismen einzelne Arbeitslasten gemäß organisatorischen Ressourcenallokationsrichtlinien mit harten Grenzwerten durchgesetzt werden.
 #4.7.4    Level: 2    Rolle: V
 Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant verfolgt, Warnungen basierend auf organisatorischen Budgetgrenzen bereitstellt und automatisierte Kontrollen bei Budgetüberschreitungen ermöglicht.
 #4.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Kapazitätsplanung historische Daten verwendet, mit organisatorisch festgelegten Prognosezeiträumen und automatisierter Ressourcenbereitstellung basierend auf Nachfragemustern.
 #4.7.6    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Ressourcenerschöpfung Circuit-Breaker gemäß den organisatorischen Reaktionsanforderungen auslöst, einschließlich Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.

---

### C4.8 Trennung der Umgebungen und Freigabekontrollen

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Freigabe-Toren und Sicherheitsvalidierung.

 #4.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen und keine gemeinsamen IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen bestehen.
 #4.8.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Umgebungsfreigabe eine Genehmigung durch organisatorisch definierte befugte Personen mit kryptografischen Signaturen und unveränderlichen Audit-Trails erfordert.
 #4.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Produktionsumgebungen SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanträge mit organisatorischen Vorankündigungsfristen verlangen, außer bei Notfällen.
 #4.8.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code (IaC) eine Peer-Review mit automatisierten Tests und Sicherheitsprüfungen erfordern, bevor sie in den Hauptzweig zusammengeführt werden.
 #4.8.5    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Nichtproduktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert sind, dass die Erzeugung synthetischer Daten erfolgt bzw. dass eine vollständige Datenmaskierung mit Entfernung personenbezogener Daten verifiziert ist.
 #4.8.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Freigabetore automatisierte Sicherheitsprüfungen (SAST, DAST, Container-Scanning) enthalten, bei denen für die Freigabe keine kritischen Befunde erforderlich sind.

---

### C4.9 Infrastruktur-Backup und Wiederherstellung

Gewährleisten Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Fähigkeiten zur Notfallwiederherstellung.

 #4.9.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Infrastrukturkonfigurationen gemäß den Backup-Zeitplänen der Organisation gesichert werden, um räumlich getrennte Regionen mit der Implementierung der 3-2-1-Backup-Strategie zu erreichen.
 #4.9.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Backup-Systeme in isolierten Netzwerken mit separaten Anmeldeinformationen betrieben werden und über luftgetrennte Speicher verfügen, zum Schutz vor Ransomware.
 #4.9.3    Level: 2    Rolle: V
 Vergewissern Sie sich, dass Wiederherstellungsverfahren durch automatisierte Tests gemäß den organisatorischen Zeitplänen getestet und validiert werden, wobei RTO- und RPO-Ziele den organisatorischen Anforderungen entsprechen.
 #4.9.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Katastrophenwiederherstellung KI-spezifische Runbooks mit der Wiederherstellung der Modellgewichte, dem Neuaufbau des GPU-Clusters und der Kartierung der Dienstabhängigkeiten umfasst.

---

### C4.10 Infrastruktur-Compliance und Governance

Sicherstellung der Einhaltung regulatorischer Vorgaben durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

 #4.10.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Compliance der Infrastruktur gemäß den organisatorischen Zeitplänen gegen SOC 2, ISO 27001 oder FedRAMP-Kontrollen bewertet wird, mit automatisierter Beweiserhebung.
 #4.10.2    Level: 2    Rolle: V
 Überprüfen Sie, ob die Infrastrukturdokumentation Netzwerkdiagramme, Datenflussdiagramme und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.
 #4.10.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Infrastrukturänderungen einer automatisierten Compliance-Folgenabschätzung unterzogen werden, zusammen mit regulatorischen Freigabeprozessen für risikoreiche Änderungen.

---

### C4.11 KI-Hardware-Sicherheit

Sichere KI-spezifische Hardwarekomponenten, einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

 #4.11.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Firmware von KI-Beschleunigern (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des Patch-Managements der Organisation aktualisiert wird.
 #4.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestation mittels TPM 2.0, Intel TXT oder AMD SVM validiert wird.
 #4.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der GPU-Speicher zwischen Arbeitslasten isoliert ist, indem Sie SR-IOV, MIG (Multi-Instance GPU) oder eine gleichwertige hardwarebasierte Partitionierung mit Speichersanitisierung zwischen den Jobs verwenden.
 #4.11.4    Level: 3    Rolle: V
 Überprüfen Sie, dass die KI-Hardware-Lieferkette eine Provenienzverifikation mit Herstellerzertifikaten sowie eine Validierung manipulationssicherer Verpackungen umfasst.
 #4.11.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) KI-Modellgewichte und kryptografische Schlüssel mit FIPS-140-2 Stufe 3 bzw. Common Criteria EAL4+ Zertifizierung geschützt sind.

---

### C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen, einschließlich Edge-Computing, föderiertes Lernen und Architekturen mit mehreren Standorten.

 #4.12.1    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Edge-KI-Geräte sich gegenüber der zentralen Infrastruktur durch gegenseitige TLS-Authentifizierung authentifizieren, wobei Gerätezertifikate gemäß der Organisationspolitik zum Zertifikatsmanagement rotiert werden.
 #4.12.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Edge-Geräte Secure Boot mit verifizierten Signaturen implementieren und einen Rollback-Schutz bieten, der Firmware-Downgrade-Angriffe verhindert.
 #4.12.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die verteilte KI-Koordination byzantinische Fehlertoleranz-Konsensalgorithmen mit Teilnehmervalidierung und Erkennung böswilliger Knoten verwendet.
 #4.12.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Edge-to-Cloud-Kommunikation Bandbreiten-Drosselung, Datenkompression und Offline-Betriebsfunktionen mit sicherem lokalem Speicher umfasst.

---

### C4.13 Sicherheit von Multi-Cloud- und Hybrid-Infrastrukturen

Sichere KI-Workloads über mehrere Cloud-Anbieter hinweg und hybride Cloud- und On-Premises-Bereitstellungen.

 #4.13.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen eine cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralisiertem Richtlinienmanagement über Anbieter hinweg verwenden.
 #4.13.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass bei der cloud-übergreifenden Datenübertragung eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet wird und dass Datenresidenzkontrollen je Rechtsordnung durchgesetzt werden.
 #4.13.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien über On-Premises- und Cloud-Umgebungen hinweg implementieren, mit einheitlicher Überwachung und Alarmierung.
 #4.13.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Maßnahmen zur Verhinderung von Cloud-Anbieter-Lock-in portables Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfassen.
 #4.13.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Kostenoptimierung in Multi-Cloud-Umgebungen Sicherheitskontrollen umfasst, die eine Ressourcenverbreitung verhindern, sowie unautorisierte Datenübertragungskosten zwischen Clouds verhindern.

---

### C4.14 Infrastrukturautomatisierung & GitOps-Sicherheit

Sichern Sie Infrastruktur-Automatisierungspipelines und GitOps-Workflows für das KI-Infrastrukturmanagement.

 #4.14.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass GitOps-Repositories signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln vorsehen, die das direkte Pushen auf Hauptzweige verhindern.
 #4.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatisierter Behebung und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen bei unbefugten Änderungen ausgelöst werden.
 #4.14.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die automatisierte Infrastruktur-Bereitstellung eine Validierung der Sicherheitsrichtlinien umfasst, die bei nicht konformen Konfigurationen die Bereitstellung blockiert.
 #4.14.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Geheimnisse der Infrastrukturautomatisierung durch externe Secrets-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.
 #4.14.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die selbstheilende Infrastruktur die Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Stakeholder umfasst.

---

### C4.15 Quantenresistente Infrastruktur-Sicherheit

Bereiten Sie eine KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie Post-Quanten-Kryptografie und quantenresistente Protokolle einsetzen.

 #4.15.1    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die KI-Infrastruktur NIST-anerkannte postquantenkryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für Schlüsselaustausch und digitale Signaturen implementiert.
 #4.15.2    Level: 3    Rolle: D/V
 Überprüfen Sie, dass QKD-Systeme für die hochsichere KI-Kommunikation mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.
 #4.15.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Rahmenwerke kryptografischer Agilität eine schnelle Migration zu neuen Post-Quanten-Algorithmen mit automatisierter Zertifikats- und Schlüsselrotation ermöglichen.
 #4.15.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Quantenbedrohungsmodellierung die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet und dass dokumentierte Migrationszeitpläne sowie Risikobewertungen vorliegen.
 #4.15.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass hybride klassische-quantische kryptografische Systeme während der Quantenübergangsphase eine Verteidigung in der Tiefe bieten und Leistungsüberwachung implementieren.

---

### C4.16 Vertrauliches Computing & Sichere Enklaven

Schützen Sie KI-Workloads und Modellgewichte durch hardwarebasierte vertrauenswürdige Ausführungsumgebungen und Technologien des vertraulichen Computings.

 #4.16.1    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass empfindliche KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsprüfung ausgeführt werden.
 #4.16.2    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass vertrauliche Container (Kata Containers, gVisor mit vertraulichem Computing) KI-Arbeitslasten mit hardwaregestützter Speicherverschlüsselung isolieren.
 #4.16.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Remote-Attestation die Integrität der Enklave überprüft, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität einer Ausführungsumgebung geladen werden.
 #4.16.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob vertrauliche KI-Inferenzdienste eine Modellextraktion durch verschlüsselte Berechnungen mit versiegelten Modellgewichten und geschützter Ausführung verhindern.
 #4.16.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Orchestrierung der Trusted Execution Environment (TEE) den Lebenszyklus sicherer Enklaven mit Remote-Attestation und verschlüsselten Kommunikationskanälen verwaltet.
 #4.16.6    Level: 3    Rolle: D/V
 Verifizieren Sie, dass sichere Mehrparteienberechnung (SMPC) kooperatives KI-Training ermöglicht, ohne einzelne Datensätze oder Modellparameter offenzulegen.

---

### C4.17 Infrastruktur für Nullwissen

Implementieren Sie Null-Wissens-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen offenzulegen.

 #4.17.1    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Null-Wissens-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität des KI-Modells und die Provenienz des Trainings belegen, ohne Modellgewichte oder Trainingsdaten offenzulegen.
 #4.17.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerauthentifizierung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen offenzulegen.
 #4.17.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Private Set Intersection (PSI)-Protokolle einen sicheren Datenabgleich für föderierte KI ermöglichen, ohne einzelne Datensätze offenzulegen.
 #4.17.4    Level: 3    Rolle: D/V
 Bestätigen Sie, dass Null-Wissens-Maschinelles Lernen (ZKML)-Systeme verifizierbare KI-Inferenzen mit kryptografischem Beweis der korrekten Berechnung ermöglichen.
 #4.17.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass ZK-rollups skalierbare datenschutzfreundliche KI-Transaktionsverarbeitung mit Batch-Verifikation und reduziertem Rechenaufwand bieten.

---

### C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und Cache-basierten Seitenkanalangriffen, die sensible Informationen preisgeben könnten.

 #4.18.1    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Inferenzzeit der KI durch Algorithmen mit konstanter Laufzeit und Padding normalisiert wird, um Timing-basierte Modellextraktionsangriffe zu verhindern.
 #4.18.2    Level: 3    Rolle: D/V
 Überprüfen Sie, dass der Schutz gegen Stromverbrauchsanalyse Rauschinjektion, Netzspannungsfilterung und randomisierte Ausführungsabläufe für KI-Hardware umfasst.
 #4.18.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Cache-basierte Gegenmaßnahmen gegen Seitenkanäle Cache-Partitionierung, Randomisierung und Flush-Instruktionen verwenden, um Informationsleckagen zu verhindern.
 #4.18.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.
 #4.18.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob mikroarchitektonische Seitenkanal-Schutzmaßnahmen spekulative Ausführungskontrollen und Obfuskation von Speicherzugriffs-Mustern umfassen.

---

### C4.19 Neuromorphische & spezialisierte KI-Hardware-Sicherheit

Schützen Sie aufkommende KI-Hardware-Architekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

 #4.19.1    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sicherheit neuromorpher Chips die Verschlüsselung von Spikemustern, den Schutz synaptischer Gewichte und die hardwarebasierte Validierung von Lernregeln umfasst.
 #4.19.2    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Tamper-Mechanismen und sicheres Laden von Konfigurationen mit authentifizierten Updates implementieren.
 #4.19.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, Hardware-Wurzel des Vertrauens und sicheren Schlüsselspeicher mit Manipulationsdetektion umfasst.
 #4.19.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.
 #4.19.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass hybride Analog-Digital-Chips für KI sichere analoge Berechnungen, geschützten Gewichtsspeicher und authentifizierte Analog-zu-Digital-Wandlung enthalten.

---

### C4.20 Datenschutzfreundliche Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzkonforme Berechnungen, um sensible Daten während der KI-Verarbeitung und KI-Analyse zu schützen.

 #4.20.1    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Infrastruktur für homomorphe Verschlüsselung verschlüsselte Berechnungen auf sensiblen KI-Arbeitslasten ermöglicht und kryptografische Integritätsprüfung sowie Leistungsüberwachung bietet.
 #4.20.2    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Private Information Retrieval-Systeme Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, indem sie die Zugriffsmuster kryptografisch schützen.
 #4.20.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob sichere Mehrparteienberechnungsverfahren eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.
 #4.20.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselgenerierung, Schwellenkryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.
 #4.20.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Rechenleistung bei datenschutzfreundlichen Berechnungen durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während kryptografische Sicherheitsgarantien gewahrt bleiben.

---

### C4.15 Agent Framework Cloud-Integration-Sicherheit und hybride Bereitstellung

Sicherheitskontrollen für Cloud-integrierte Agenten-Frameworks mit hybriden On-Premises-/Cloud-Architekturen.

 #4.15.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Cloud-Speicherintegration eine Ende-zu-Ende-Verschlüsselung mit agentengesteuerter Schlüsselverwaltung verwendet.
 #4.15.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und dass verschlüsselte Kommunikationskanäle verwendet werden.
 #4.15.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.
 #4.15.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Anforderungen an die Datenresidenz durch kryptografische Attestierung der Speicherorte durchgesetzt werden.
 #4.15.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sicherheitsbewertungen von Cloud-Anbietern eine agentenspezifische Bedrohungsmodellierung und Risikobewertung umfassen.

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

Wirksame Zugriffskontrolle für KI-Systeme erfordert robuste Identitätsverwaltung, kontextbasierte Autorisierung und Laufzeitsdurchsetzung nach den Zero-Trust-Prinzipien. Diese Kontrollen stellen sicher, dass Menschen, Dienste und autonome Agenten ausschließlich mit Modellen, Daten und Rechenressourcen innerhalb ausdrücklich gewährter Berechtigungen interagieren, mit kontinuierlicher Verifikation und Auditierbarkeit.

---

### C5.1 Identitätsmanagement & Authentifizierung

Stellen Sie kryptographisch gestützte Identitäten für alle Entitäten bereit, die privilegierte Operationen mit Multi-Faktor-Authentifizierung erfordern.

 #5.1.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass alle menschlichen Benutzer und Serviceprinzipale sich über einen zentralen unternehmensweiten Identitätsanbieter (IdP) authentifizieren, der OIDC/SAML-Protokolle verwendet, mit eindeutigen Identität-zu-Token-Zuordnungen (keine gemeinsam genutzten Konten oder Anmeldeinformationen).
 #5.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass risikoreiche Operationen (Modellbereitstellung, Gewichtsexport, Zugriff auf Trainingsdaten, Änderungen an der Produktionskonfiguration) eine Mehrfaktor-Authentifizierung oder Step-Up-Authentifizierung mit erneuter Sitzungsvalidierung erfordern.
 #5.1.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass neue Identitäten eine Identitätsfeststellung durchlaufen, die mit NIST 800-63-3 IAL-2 oder gleichwertigen Standards übereinstimmt, bevor sie Zugriff auf das Produktionssystem erhalten.
 #5.1.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Zugriffsüberprüfungen vierteljährlich durchgeführt werden, mit automatisierter Erkennung inaktiver Konten, Durchsetzung der Rotation von Anmeldeinformationen und Deprovisioning-Workflows.
 #5.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass föderierte KI-Agenten sich durch signierte JWT-Aussagen authentifizieren, die eine maximale Lebensdauer von 24 Stunden haben und einen kryptografischen Herkunftsnachweis enthalten.

---

### C5.2 Ressourcenautorisierung und Prinzip der geringsten Privilegien

Implementieren Sie feingranulare Zugriffskontrollen für alle KI-Ressourcen mit expliziten Berechtigungsmodellen und Audit-Trails.

 #5.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob jede KI-Ressource (Datensätze, Modelle, Endpunkte, Vektorsammlungen, Einbettungsindizes, Compute-Instanzen) rollenbasierte Zugriffskontrollen mit expliziten Allow-Listen und Default-Deny-Richtlinien durchsetzt.
 #5.2.2    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass die Prinzipien der geringsten Privilegien standardmäßig durchgesetzt werden, wobei Dienstkonten mit standardmäßigem Lesezugriff beginnen und für Schreibzugriff eine dokumentierte geschäftliche Begründung erforderlich ist.
 #5.2.3    Level: 1    Rolle: V
 Stellen Sie sicher, dass alle Zugriffskontrolländerungen mit genehmigten Änderungsanträgen verknüpft sind und unveränderlich mit Zeitstempeln, Identitäten der Akteure, Ressourcenkennungen und Berechtigungsänderungen protokolliert werden.
 #5.2.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass Datenklassifikationskennzeichnungen (PII, PHI, exportkontrolliert, proprietär) automatisch auf abgeleitete Ressourcen (Einbettungen, Promptspeicher, Modellausgaben) mit konsistenter Richtliniendurchsetzung übertragen werden.
 #5.2.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass unbefugte Zugriffsversuche und Ereignisse der Privilegieneskalation Echtzeitwarnungen mit kontextbezogenen Metadaten auslösen, die innerhalb von 5 Minuten an SIEM-Systeme übermittelt werden.

---

### C5.3 Dynamische Richtlinienbewertung

ABAC-Engines für kontextabhängige Autorisierungsentscheidungen mit Audit-Funktionen bereitstellen.

 #5.3.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Autorisierungsentscheidungen an eine dedizierte Policy-Engine (OPA, Cedar oder Äquivalent) externalisiert werden, die über authentifizierte APIs erreichbar ist und kryptographischen Integritätsschutz bietet.
 #5.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Richtlinien dynamische Attribute zur Laufzeit auswerten, einschließlich der Freigabestufe des Benutzers, der Vertraulichkeitseinstufung der Ressource, des Anfragekontexts, der Mandantenisolierung und zeitlicher Beschränkungen.
 #5.3.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtliniendefinitionen versionskontrolliert, Peer-Review unterzogen und durch automatisierte Tests in CI/CD-Pipelines validiert werden, bevor sie in die Produktion überführt werden.
 #5.3.4    Level: 2    Rolle: V
 Vergewissern Sie sich, dass die Ergebnisse der Richtlinienauswertung strukturierte Entscheidungsbegründungen enthalten und an SIEM-Systeme zur Korrelationsanalyse und Compliance-Berichterstattung übertragen werden.
 #5.3.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Werte des Richtlinien-Cache-Time-to-Live (TTL) 5 Minuten für Ressourcen mit hoher Sensitivität und 1 Stunde für Standardressourcen mit Cache-Invalidierungsfunktionen nicht überschreiten.

---

### C5.4 Abfragezeit-Sicherheitsdurchsetzung

Sicherheitskontrollen auf Datenbankebene mit obligatorischer Filterung und Sicherheitsrichtlinien auf Zeilenebene implementieren.

 #5.4.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass alle Abfragen in Vektor-Datenbanken und SQL-Abfragen obligatorische Sicherheitsfilter enthalten (Mandant-ID, Sensitivitätskennzeichnungen, Benutzerbereich), die auf der Ebene der Datenbank-Engine durchgesetzt werden, nicht im Anwendungscode.
 #5.4.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Zeilenbasierte Sicherheit (RLS)-Richtlinien und Maskierung auf Feldebene mit Richtlinienvererbung für alle Vektordatenbanken, Suchindizes und Trainingsdatensätze aktiviert sind.
 #5.4.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass fehlgeschlagene Autorisierungsprüfungen verhindern, dass Angriffe durch den verwirrten Beauftragten entstehen, indem Abfragen sofort abgebrochen und explizite Autorisierungsfehlercodes zurückgegeben werden, statt leere Ergebnismengen zu liefern.
 #5.4.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Latenz der Policy-Auswertung kontinuierlich überwacht wird, mit automatisierten Warnmeldungen bei Timeout-Bedingungen, die eine Autorisierungsumgehung ermöglichen könnten.
 #5.4.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Abfrage-Wiederholungsmechanismen die Autorisierungsrichtlinien erneut bewerten, um dynamische Berechtigungsänderungen innerhalb aktiver Benutzersitzungen zu berücksichtigen.

---

### C5.5 Ausgabefilterung & Datenverlustprävention

Implementieren Sie Nachbearbeitungskontrollen, um eine unbefugte Offenlegung von Daten in KI-generierten Inhalten zu verhindern.

 #5.5.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Filtermechanismen nach der Inferenz unbefugte persönlich identifizierbare Informationen (PII), klassifizierte Informationen und proprietäre Daten scannen und schwärzen, bevor Inhalte an Anforderer übermittelt werden.
 #5.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Zitate, Referenzen und Quellenangaben in Modellausgaben gegen die Berechtigungen des Aufrufers validiert werden und entfernt werden, falls unautorisierter Zugriff festgestellt wird.
 #5.5.3    Level: 2    Rolle: D
 Verifizieren Sie, dass Ausgabeformatbeschränkungen (bereinigte PDFs, Bilder ohne Metadaten, genehmigte Dateitypen) basierend auf den Berechtigungsstufen der Benutzer und den Datenklassifikationen durchgesetzt werden.
 #5.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Schwärzungsalgorithmen deterministisch sind, versionskontrolliert arbeiten und Audit-Protokolle führen, um Compliance-Untersuchungen und forensische Analysen zu unterstützen.
 #5.5.5    Level: 3    Rolle: V
 Vergewissern Sie sich, dass hochriskante Schwärzungsereignisse adaptive Protokolle erzeugen, die kryptographische Hashwerte des ursprünglichen Inhalts enthalten, zur forensischen Wiederherstellung ohne Offenlegung der Daten.

---

### C5.6 Mehrmandanten-Isolation

Sicherstellen kryptographischer und logischer Isolation zwischen Mandanten in einer geteilten KI-Infrastruktur.

 #5.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Speicherbereiche, Embedding-Speicher, Cache-Einträge und temporäre Dateien mandantenspezifisch isoliert sind und bei Löschung des Mandanten oder Beendigung der Sitzung sicher bereinigt werden.
 #5.6.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede API-Anfrage eine authentifizierte Mandanten-ID enthält, die kryptografisch gegen den Sitzungskontext und die Benutzerberechtigungen validiert wird.
 #5.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Netzwerkrichtlinien Default-Deny-Regeln für mandantenübergreifende Kommunikation innerhalb von Service-Meshes und Container-Orchestrierungsplattformen implementieren.
 #5.6.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass pro Mandant eindeutige Verschlüsselungsschlüssel vorhanden sind, CMK-Unterstützung gegeben ist und zwischen den Datenspeichern der Mandanten eine kryptografische Isolation besteht.

---

### C5.7 Autorisierung autonomer Agenten

Kontrollieren Sie Berechtigungen für KI-Agenten und autonome Systeme durch kontextspezifische Berechtigungs-Tokens und kontinuierliche Autorisierung.

 #5.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass autonome Agenten eingeschränkte Berechtigungstokens erhalten, die explizit die zulässigen Aktionen, zugänglichen Ressourcen, zeitliche Grenzen und betriebliche Einschränkungen auflisten.
 #5.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Hochrisikofunktionen (Dateisystemzugriff, Codeausführung, Aufrufe externer APIs, finanzielle Transaktionen) standardmäßig deaktiviert sind und für deren Aktivierung explizite Genehmigungen erforderlich sind, die durch geschäftliche Begründungen gestützt werden.
 #5.7.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Berechtigungstoken an Benutzersitzungen gebunden sind, kryptografischen Integritätsschutz bieten und weder gespeichert noch in Offline-Szenarien wiederverwendet werden können.
 #5.7.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die vom Agenten initiierten Aktionen einer sekundären Autorisierung durch die ABAC-Policy-Engine mit vollständiger Kontextauswertung und Audit-Protokollierung unterzogen werden.
 #5.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass die Fehlerzustände des Agenten und die Ausnahmebehandlung Informationen zum Umfang der Fähigkeiten enthalten, um die Vorfallanalyse und die forensische Untersuchung zu unterstützen.

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

## C6 Lieferkettensicherheit für Modelle, Rahmenwerke und Daten

### Kontrollziel

KI-Lieferkettenangriffe nutzen Modelle, Frameworks oder Datensätze von Drittanbietern aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzuschleusen. Diese Kontrollen bieten End-to-End‑Provenienz, Schwachstellenmanagement und Überwachung, um den gesamten Modelllebenszyklus zu schützen.

---

### C6.1 vorgetrainte Modelle: Prüfung und Provenienz

Bewerten und Authentifizieren der Herkunft, Lizenzen und versteckten Verhaltensweisen von Drittanbieter-Modellen, bevor jegliche Feinabstimmung oder Bereitstellung erfolgt.

 #6.1.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass jedes Drittanbieter-Modellartefakt einen signierten Herkunftsnachweis enthält, der das Quell-Repository und den Commit-Hash identifiziert.
 #6.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojaner-Auslöser überprüft werden.
 #6.1.3    Level: 2    Rolle: D
 Verifizieren Sie, dass Transfer‑Learning Feinabstimmungen eine adversariale Evaluierung bestehen, um versteckte Verhaltensweisen zu erkennen.
 #6.1.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Modell‑Lizenzen, Exportkontrollkennzeichnungen und Datenherkunftsaussagen in einem ML‑BOM‑Eintrag verzeichnet sind.
 #6.1.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Modelle mit hohem Risiko (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) in Quarantäne bleiben, bis eine menschliche Überprüfung und Freigabe erfolgt.

---

### C6.2 Rahmenwerk und Bibliotheken-Scan

Kontinuierlich ML-Frameworks und Bibliotheken auf CVEs und schädlichen Code scannen, um den Laufzeit-Stack sicher zu halten.

 #6.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob CI-Pipelines Abhängigkeits-Scanner für KI-Frameworks und kritische Bibliotheken ausführen.
 #6.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass kritische Schwachstellen (CVSS ≥ 7.0) die Freigabe von Produktions-Images blockieren.
 #6.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob die statische Code-Analyse auf geforkten oder eingebundenen ML-Bibliotheken läuft.
 #6.2.4    Level: 2    Rolle: V
 Überprüfen Sie, ob Vorschläge für Framework-Upgrades eine Sicherheitsfolgenabschätzung enthalten, die sich auf öffentliche CVE-Feeds bezieht.
 #6.2.5    Level: 3    Rolle: V
 Verifizieren Sie, dass Laufzeitsensoren bei unerwarteten Ladevorgängen dynamischer Bibliotheken, die vom signierten SBOM abweichen, einen Alarm auslösen.

---

### C6.3 Abhängigkeits-Pinning und Verifizierung

Jede Abhängigkeit auf unveränderliche Hash-Werte festlegen und Builds reproduzieren, um identische, manipulationssichere Artefakte zu garantieren.

 #6.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Paketmanager die Versionssperre über Lockfiles erzwingen.
 #6.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass in Containerreferenzen unveränderliche Digest-Werte verwendet werden, anstelle von Tags, die veränderlich sind.
 #6.3.3    Level: 2    Rolle: D
 Vergewissern Sie sich, dass Reproduzierbarkeitsprüfungen Hash-Werte über CI-Läufe hinweg vergleichen, um identische Ausgaben sicherzustellen.
 #6.3.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Build-Attestationen für 18 Monate zur Audit-Nachverfolgbarkeit gespeichert werden.
 #6.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull-Requests auslösen, um gepinnte Versionen zu aktualisieren oder zu forken.

---

### C6.4 Durchsetzung vertrauenswürdiger Quellen

Laden Sie Artefakte nur aus kryptografisch verifizierten, organisations‑genehmigten Quellen herunter und blockieren Sie alles andere.

 #6.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Modellgewichte, Datensätze und Container ausschließlich von genehmigten Domains oder internen Registries heruntergeladen werden.
 #6.4.2    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers validieren, bevor Artefakte lokal zwischengespeichert werden.
 #6.4.3    Level: 2    Rolle: D
 Überprüfen Sie, dass Ausgangsproxies nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.
 #6.4.4    Level: 2    Rolle: V
 Vergewissern Sie sich, dass die Allowlisten des Repositories vierteljährlich überprüft werden, mit Nachweis der geschäftlichen Begründung für jeden Eintrag.
 #6.4.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Richtlinienverstöße die Quarantäne von Artefakten und das Rollback abhängiger Pipeline-Läufe auslösen.

---

### C6.5 Risikobewertung von Drittanbieterdatensätzen

Externe Datensätze auf Datenvergiftung, Verzerrung und rechtliche Konformität bewerten und sie während ihres gesamten Lebenszyklus überwachen.

 #6.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass externe Datensätze einer Poisoning-Risikobewertung unterzogen werden (z. B. Datenfingerprinting, Ausreißererkennung).
 #6.5.2    Level: 1    Rolle: D
 Überprüfen Sie, ob Bias-Metriken (demografische Parität, gleiche Chancen) vor der Genehmigung des Datensatzes berechnet werden.
 #6.5.3    Level: 2    Rolle: V
 Überprüfen Sie, ob die Provenienz- und Lizenzbedingungen für Datensätze in ML‑BOM-Einträgen erfasst werden.
 #6.5.4    Level: 2    Rolle: V
 Überprüfen Sie, ob regelmäßige Überwachung Drift oder Datenkorruption in gehosteten Datensätzen erkennt.
 #6.5.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass verbotene Inhalte (Urheberrecht, PII) vor dem Training durch automatisierte Bereinigung entfernt werden.

---

### C6.6 Überwachung von Lieferkettenangriffen

Frühzeitig Lieferkettenbedrohungen erkennen durch CVE-Feeds, Audit-Log-Analytik und Red-Team-Simulationen.

 #6.6.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass CI/CD-Auditprotokolle an SIEM-Erkennungen weitergeleitet werden, die sich auf anomale Paketabrufe oder manipulierte Build-Schritte beziehen.
 #6.6.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Incident-Response-Playbooks Rollback-Verfahren für kompromittierte Modelle oder Bibliotheken enthalten.
 #6.6.3    Level: 3    Rolle: V
 Stellen Sie sicher, dass Threat‑Intel‑Enrichment‑Tags ML‑spezifische Indikatoren (z. B. IoCs zur Modellvergiftung) in der Alarm‑Triage kennzeichnen.

---

### C6.7 ML‑BOM für Modellartefakte

Erzeuge und signiere detaillierte ML‑spezifische SBOMs (ML‑BOMs), damit nachgelagerte Verbraucher die Integrität der Komponenten zum Bereitstellungszeitpunkt überprüfen können.

 #6.7.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass jedes Modellartefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.
 #6.7.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ML‑BOM-Erzeugung und Cosign-Signierung in der CI automatisiert sind und für das Merge erforderlich sind.
 #6.7.3    Level: 2    Rolle: D
 Überprüfen Sie, dass ML‑BOM‑Vollständigkeitsprüfungen den Build fehlschlagen lassen, wenn Metadaten einer Komponente (Hash, Lizenz) fehlen.
 #6.7.4    Level: 2    Rolle: V
 Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über eine API abfragen können, um importierte Modelle während der Bereitstellung zu validieren.
 #6.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass ML‑BOMs versionskontrolliert sind und auf Unterschiede verglichen werden, um unbefugte Änderungen zu erkennen.

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

## C7 Modellverhalten, Ausgabesteuerung und Sicherheitsabsicherung

### Kontrollziel

Modellausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und in der Produktion kontinuierlich überwacht werden. Dadurch verringern sich Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und außer Kontrolle geratene Handlungen, während das Vertrauen der Nutzer steigt und die Einhaltung gesetzlicher Vorschriften verbessert wird.

---

### C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Dekodierung und nachgelagerte Validierung stoppen fehlerhaften oder schädlichen Inhalt, bevor er sich verbreitet.

 #7.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Antwort-Schemata (z. B. JSON-Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben führen zu einer Nachbesserung oder Ablehnung.
 #7.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob eingeschränkte Decodierung (Stop-Tokens, Regex, Max-Tokens) aktiviert ist, um Überlauf oder Prompt-Injection-Seitenkanäle zu verhindern.
 #7.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.
 #7.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass unzulässige Ausgabeereignisse protokolliert werden, einer Ratenbegrenzung unterliegen und dem Monitoring gemeldet werden.

---

### C7.2 Halluzinationserkennung und Minderung

Unsicherheitsabschätzung und Fallback-Strategien dämpfen halluzinierte Antworten.

 #7.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Token-Level-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jeder Antwort einen Konfidenzwert zuweisen.
 #7.2.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Antworten unter einer konfigurierbaren Konfidenzschwelle Fallback-Workflows auslösen (z. B. abfragegestützte Generierung, sekundäres Modell oder menschliche Überprüfung).
 #7.2.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Halluzinationsvorfälle mit Grundursachen-Metadaten gekennzeichnet sind und in Post-Mortem- und Feinabstimmungs-Pipelines eingespeist werden.
 #7.2.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbankaktualisierungen neu kalibriert werden.
 #7.2.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Dashboard-Visualisierungen die Halluzinationsraten verfolgen.

---

### C7.3 Ausgabe-Sicherheit und Datenschutz-Filterung

Richtlinienfilter und Red-Team-Abdeckung schützen Nutzer und vertrauliche Daten.

 #7.3.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass Vor- und Nachgenerierungs-Klassifikatoren Inhalte, die Hass, Belästigung, Selbstverletzung, Extremismus und sexuell explizite Inhalte betreffen, gemäß der Richtlinie blockieren.
 #7.3.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob PII/PCI-Erkennung und automatische Unkenntlichmachung bei jeder Antwort ausgeführt werden; Verstöße lösen einen Datenschutzvorfall aus.
 #7.3.3    Level: 2    Rolle: D
 Überprüfen Sie, ob Vertraulichkeitskennzeichnungen (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg weitergegeben werden, um Datenlecks in Texten, Bildern oder Code zu verhindern.
 #7.3.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Versuche der Filterumgehung oder Klassifizierungen mit hohem Risiko eine sekundäre Freigabe oder eine erneute Authentifizierung des Benutzers erfordern.
 #7.3.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Filter-Schwellenwerte die geltenden Rechtsordnungen sowie den Alters- bzw. Rollen-Kontext des Nutzers berücksichtigen.

---

### C7.4 Ausgabe- und Aktionsbeschränkung

Ratenbegrenzungen und Freigabestufen verhindern Missbrauch und übermäßige Autonomie.

 #7.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass die Nutzungsquoten pro Benutzer und pro API-Schlüssel Anfragen, Tokens und Kosten begrenzen, mit exponentiellem Back-off bei 429-Fehlern.
 #7.4.2    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass privilegierte Aktionen (Datei-Schreibvorgänge, Code-Ausführung, Netzwerkaufrufe) eine policy-basierte Genehmigung oder Mensch-in-der-Schleife erfordern.
 #7.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass modalitätsübergreifende Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht dazu verwendet werden können, böswillige Inhalte zu schmuggeln.
 #7.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Delegierungstiefe des Agenten, die Rekursionstiefen und die zulässigen Werkzeuglisten explizit konfiguriert sind.
 #7.4.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Grenzwertverletzungen strukturierte Sicherheitsereignisse für die SIEM-Ingestion erzeugen.

---

### C7.5 Ausgabenerklärbarkeit

Transparente Signale stärken das Vertrauen der Benutzer und erleichtern die interne Fehlersuche.

 #7.5.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass für den Benutzer sichtbare Konfidenzwerte oder kurze Begründungszusammenfassungen offengelegt werden, wenn die Risikobewertung dies für angemessen hält.
 #7.5.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass generierte Erklärungen keine sensiblen System-Prompts oder proprietären Daten offenlegen.
 #7.5.3    Level: 3    Rolle: D
 Stellen Sie sicher, dass das System Log-Wahrscheinlichkeiten pro Token oder Aufmerksamkeitskarten erfasst und diese speichert.
 #7.5.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Artefakte der Erklärbarkeit neben Modellveröffentlichungen unter Versionskontrolle stehen, um Auditierbarkeit zu gewährleisten.

---

### C7.6 Monitoring-Integration

Echtzeit-Beobachtbarkeit schließt den Kreis zwischen Entwicklung und Produktion.

 #7.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Metriken (Schema-Verstöße, Halluzinationsrate, Toxizität, PII-Datenlecks, Latenz, Kosten) an eine zentrale Überwachungsplattform gestreamt werden.
 #7.6.2    Level: 1    Rolle: V
 Stellen Sie sicher, dass Alarm-Schwellenwerte für jede Sicherheitsmetrik definiert sind, mit Eskalationspfaden im Bereitschaftsdienst.
 #7.6.3    Level: 2    Rolle: V
 Verifizieren Sie, dass Dashboards Ausgabeanomalien mit Modell/Version, Feature-Flag und Änderungen der Quelldaten korrelieren.
 #7.6.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Überwachungsdaten in Retraining, Feinabstimmung oder Regelaktualisierungen innerhalb eines dokumentierten MLOps-Workflows zurückfließen.
 #7.6.5    Level: 3    Rolle: V
 Verifizieren Sie, dass die Überwachungs-Pipelines Penetrationstests unterzogen werden und Zugriffskontrollen implementiert sind, um das Austreten sensibler Protokolle zu verhindern.

---

### 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Richtlinienbeschränkungen, Ausgabevalidierung und Nachverfolgbarkeit durchgesetzt werden.

 #7.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erzeugung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bilder, Videos, Audios) untersagen.
 #7.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Eingabeaufforderungen dahingehend gefiltert werden, ob sie darauf abzielen, Imitationen zu erzeugen, sexuell explizite Deepfakes zu erstellen oder Medien zu produzieren, die reale Personen ohne deren Einwilligung zeigen.
 #7.7.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass das System Perzeptuelles Hashing, Wasserzeichenerkennung oder Fingerabdruckverfahren verwendet, um eine unbefugte Reproduktion urheberrechtlich geschützter Medien zu verhindern.
 #7.7.4    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass alle generierten Medien kryptografisch signiert, mit Wasserzeichen versehen oder mit manipulationssicheren Provenienz-Metadaten eingebettet sind, um eine nachgelagerte Nachverfolgbarkeit zu ermöglichen.
 #7.7.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Obfuskation, Slang, adversarische Formulierungen) erkannt, protokolliert und durch Ratenbegrenzung eingeschränkt werden; wiederholter Missbrauch wird an die Überwachungssysteme gemeldet.

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

## C8 Memory, Einbettungen & Vektordatenbank-Sicherheit

### Kontrollziel

Einbettungen und Vektor-Speicher fungieren als das 'Live-Memory' zeitgenössischer KI-Systeme, die kontinuierlich nutzerbereitgestellte Daten akzeptieren und sie über Retrieval-Augmented Generation (RAG) wieder in Modellkontexte einbringen. Wird dieses Gedächtnis unbeaufsichtigt gelassen, kann es personenbezogene Daten (PII) offengelegen, Zustimmung verletzen oder so manipuliert werden, dass der ursprüngliche Text rekonstruiert werden kann. Das Ziel dieser Kontrollfamilie besteht darin, Speicher-Pipelines und Vektor-Datenbanken zu härten, damit der Zugriff dem Prinzip der geringsten Privilegien entspricht, die Einbettungen datenschutzfreundlich sind, gespeicherte Vektoren verfallen oder auf Abruf widerrufen werden können, und benutzerbezogener Speicher niemals die Eingaben oder Generierungen eines anderen Benutzers beeinflusst.

---

### C8.1 Zugriffskontrollen auf Speicher- und RAG-Indizes

Durchsetzen Sie feingranulierte Zugriffskontrollen für jede Vektorsammlung.

 #8.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Zugriffskontrollregeln auf Zeilen- und Namensraum-Ebene Einfüge-, Lösch- und Abfragevorgänge pro Mandant, Sammlung oder Dokument-Tag einschränken.
 #8.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass API-Schlüssel oder JWTs bereichsspezifische Ansprüche tragen (z. B. Sammlungs-IDs, Aktionsverben) und dass sie mindestens vierteljährlich rotiert werden.
 #8.1.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Privilegieneskalationsversuche (z. B. Namensräume übergreifende Ähnlichkeitsabfragen) innerhalb von 5 Minuten erkannt und in ein SIEM protokolliert werden.
 #8.1.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass die Auditprotokolle der Vektor-Datenbank Folgendes protokollieren: Subjekt-Identifikator, Vorgang, Vektor-ID/Namensraum, Ähnlichkeitsschwelle und Anzahl der Ergebnisse.
 #8.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Zugriffsentscheidungen auf Umgehungsschwachstellen getestet werden, wann immer Engines aktualisiert werden oder sich Index-Sharding-Regeln ändern.

---

### C8.2 Einbettungs-Sanitierung und Validierung

Text vor der Vektorisierung auf PII prüfen, personenbezogene Daten schwärzen oder pseudonymisieren, und optional Embeddings nachbearbeiten, um verbleibende Signale zu entfernen.

 #8.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass PII (personenbezogene Daten) und regulierte Daten durch automatisierte Klassifikatoren erkannt werden und vor der Einbettung maskiert, tokenisiert oder verworfen werden.
 #8.2.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Embedding-Pipelines Eingaben ablehnen oder in Quarantäne stellen, die ausführbaren Code oder nicht-UTF-8-Artefakte enthalten, die den Index schädigen könnten.
 #8.2.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob eine lokale oder metrische Differential-Privacy-Sanitisierung auf Satz-Einbettungen angewendet wird, deren Abstand zu jedem bekannten PII-Token unterhalb eines konfigurierbaren Schwellenwerts liegt.
 #8.2.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Wirksamkeit der Sanitisierung (z. B. Recall der PII-Schwärzung, semantische Drift) mindestens halbjährlich gegen Benchmark-Korpora validiert wird.
 #8.2.5    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass Sanitisierungskonfigurationen versionskontrolliert sind und Änderungen einem Peer-Review unterzogen werden.

---

### C8.3 Speicherablauf, Widerruf und Löschung

DSGVO "Recht auf Vergessenwerden" und ähnliche Gesetze verlangen eine rechtzeitige Löschung; Vektorspeicher müssen daher TTLs, unwiderrufliche Löschungen und Löschmarkierungen unterstützen, damit widerrufene Vektoren nicht wiederhergestellt oder neu indexiert werden können.

 #8.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass jeder Vektor- und Metadaten-Eintrag eine TTL oder eine explizite Aufbewahrungskennzeichnung trägt, die von automatisierten Bereinigungsaufgaben berücksichtigt wird.
 #8.3.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass durch benutzerinitiierte Löschanfragen Vektoren, Metadaten, Cache-Kopien und abgeleitete Indizes innerhalb von 30 Tagen gelöscht werden.
 #8.3.3    Level: 2    Rolle: D
 Überprüfen Sie, ob logische Löschvorgänge von kryptografischer Vernichtung der Speicherblöcke gefolgt werden, sofern die Hardware dies unterstützt, oder durch Zerstörung der Schlüssel im Key Vault.
 #8.3.4    Level: 3    Rolle: D/V
 Verifizieren Sie, dass abgelaufene Vektoren innerhalb von < 500 ms nach dem Ablauf aus den Ergebnissen der nächstgelegenen Nachbarsuche ausgeschlossen werden.

---

### C8.4 Verhinderung von Einbettungsinversion und Datenleck

Neuere Abwehrmaßnahmen—Rauschüberlagerung, Projektionsnetzwerke, Privatsphäre-Neuronen-Perturbation und Anwendungsschicht-Verschlüsselung—können Token-Ebene-Inversionsraten unter 5% senken.

 #8.4.1    Level: 1    Rolle: V
 Stellen Sie sicher, dass ein formales Bedrohungsmodell existiert, das Inversion, Mitgliedschafts-Inferenzangriffe und Attribut-Inferenzangriffe abdeckt, und dass es jährlich überprüft wird.
 #8.4.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Anwendungsschicht-Verschlüsselung oder die durchsuchbare Verschlüsselung Vektoren vor direktem Lesen durch Infrastruktur-Administratoren oder Cloud-Mitarbeiter schützt.
 #8.4.3    Level: 3    Rolle: V
 Verifizieren Sie, dass Schutzparameter (ε für DP, Rauschen σ, Projektionsrang k) eine Balance zwischen Privatsphäre und Nutzwert herstellen, bei der Privatsphäre ≥ 99 % Token-Schutz und Nutzwert ≤ 3 % Genauigkeitsverlust gilt.
 #8.4.4    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass Metriken zur Resilienz gegenüber Inversionen Teil der Freigabe-Gates für Modellaktualisierungen sind, wobei Regressionsbudgets definiert sind.

---

### C8.5 Durchsetzung des Geltungsbereichs für benutzerspezifischen Speicher

Mandantenübergreifendes Datenleck bleibt eines der größten RAG-Risiken: Unangemessen gefilterte Ähnlichkeitsabfragen können die privaten Dokumente eines anderen Kunden offenlegen.

 #8.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass jede Abrufabfrage nachträglich durch die Mandanten-/Benutzer-ID gefiltert wird, bevor sie an die LLM-Eingabeaufforderung übergeben wird.
 #8.5.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Sammlungsnamen oder Namensraum-IDs pro Benutzer oder Mandant gesalzen werden, damit Vektoren über verschiedene Geltungsbereiche hinweg nicht kollidieren.
 #8.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Ähnlichkeitsergebnisse, die über einen konfigurierbaren Abstandsschwellenwert hinausgehen, aber außerhalb des Gültigkeitsbereichs des Aufrufers liegen, verworfen werden und Sicherheitswarnungen auslösen.
 #8.5.4    Level: 2    Rolle: V
 Stellen Sie sicher, dass Mehrmandanten-Stresstests feindliche Abfragen simulieren, die darauf abzielen, außerhalb des Geltungsbereichs liegende Dokumente abzurufen, und dass dabei keinerlei Leckage entsteht.
 #8.5.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Verschlüsselungsschlüssel mandantenweise isoliert sind, um kryptografische Isolation sicherzustellen, auch wenn der physische Speicher geteilt wird.

---

### C8.6 Fortgeschrittene Speichersystem-Sicherheit

Sicherheitsmaßnahmen für anspruchsvolle Speicherarchitekturen, einschließlich episodischem, semantischem und Arbeitsgedächtnis, mit spezifischen Isolations- und Validierungsanforderungen.

 #8.6.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob verschiedene Speicherarten (episodisches Gedächtnis, semantisches Gedächtnis, Arbeitsgedächtnis) isolierte Sicherheitskontexte mit rollenbasierten Zugriffskontrollen, separaten Verschlüsselungsschlüsseln und dokumentierten Zugriffsmustern für jede Speicherart aufweisen.
 #8.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicher-Konsolidierungsprozesse eine Sicherheitsvalidierung beinhalten, um die Injektion schädlicher Erinnerungen durch Inhaltsbereinigung, Quellenverifizierung und Integritätsprüfungen vor der Speicherung zu verhindern.
 #8.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Speicherabrufabfragen validiert und bereinigt werden, um zu verhindern, dass unautorisierte Informationen extrahiert werden, durch die Analyse von Abfragemustern, die Durchsetzung von Zugriffskontrollen und die Ergebnisfilterung.
 #8.6.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Speicherlöschmechanismen sensible Informationen sicher löschen und kryptografische Löschgarantien verwenden, indem sie Schlüssellöschung, Mehrfachüberschreibung oder hardwarebasierte sichere Löschung mit Verifikationszertifikaten einsetzen.
 #8.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Integrität des Speichersystems kontinuierlich überwacht wird, um unbefugte Modifikationen oder Beschädigungen durch Prüfsummen, Audit-Protokolle und automatisierte Warnmeldungen zu erkennen, wenn sich der Speicherinhalt außerhalb normaler Operationen ändert.

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

## 9 autonome Orchestrierung und agentische Handlungssicherheit

### Kontrollziel

Stellen Sie sicher, dass autonome oder Multiagenten-KI-Systeme nur solche Handlungen ausführen können, die ausdrücklich beabsichtigt, authentifiziert und auditierbar sind und innerhalb begrenzter Kosten- und Risikogrenzen bleiben. Dies schützt vor Bedrohungen wie Autonomous-System Compromise, Tool Misuse, Agent Loop Detection, Communication Hijacking, Identity Spoofing, Swarm Manipulation und Intent Manipulation.

---

### 9.1 Agenten-Aufgabenplanung und Rekursionbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

 #9.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die maximale Rekursionstiefe, Breite, reale Zeit, Tokenanzahl und monetäre Kosten pro Agentenausführung zentral konfiguriert und versionskontrolliert sind.
 #9.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, Finanztransfers) eine explizite menschliche Freigabe über einen auditierbaren Kanal vor der Ausführung erfordern.
 #9.1.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass Echtzeit-Ressourcenüberwachung eine Circuit-Breaker-Unterbrechung auslöst, wenn irgendeine Budgetgrenze überschritten wird, wodurch eine weitere Aufgabenerweiterung gestoppt wird.
 #9.1.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Circuit-Breaker-Ereignisse mit der Agenten-ID, der auslösenden Bedingung und dem erfassten Planzustand protokolliert werden, um eine forensische Auswertung zu ermöglichen.
 #9.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Sicherheitstests Budgeterschöpfungs- und aus dem Ruder laufende Plan-Szenarien abdecken und ein sicheres Anhalten ohne Datenverlust bestätigen.
 #9.1.6    Level: 3    Rolle: D
 Vergewissern Sie sich, dass Budgetrichtlinien als Policy-as-Code ausgedrückt werden und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.

---

### 9.2 Tool-Plugin-Sandboxing

Isolieren Sie Tool-Interaktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

 #9.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass jedes Tool/Plugin innerhalb einer OS-, Container- oder WASM-Ebene Sandbox ausgeführt wird und Minimalberechtigungen für Dateisystem, Netzwerk und Systemaufrufe gelten.
 #9.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Ressourcenquoten (CPU, Speicher, Festplatte, ausgehender Netzwerkverkehr) durchgesetzt und protokolliert werden.
 #9.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Tool-Binärdateien oder Deskriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.
 #9.2.4    Level: 2    Rolle: V
 Überprüfen Sie, dass Sandbox-Telemetrie an ein SIEM gestreamt wird; Anomalien (z. B. ausgehende Verbindungen) lösen Alarme aus.
 #9.2.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Hochrisiko-Plugins einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden, bevor sie in die Produktion bereitgestellt werden.
 #9.2.6    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Sandbox-Ausbruchsversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung in Quarantäne gestellt wird.

---

### 9.3 Autonome Schleife und Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte Agent-zu-Agenten-Rekursion und Kostenexplosionen.

 #9.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Aufrufe zwischen Agenten ein Hop-Limit oder TTL enthalten, das von der Laufzeitumgebung dekrementiert und durchgesetzt wird.
 #9.3.2    Level: 2    Rolle: D
 Vergewissern Sie sich, dass Agenten eine eindeutige Aufruf-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.
 #9.3.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass kumulative Compute-Einheit- und Kosten-Zähler pro Anfragekette verfolgt werden; bei Überschreitung des Limits wird die Kette abgebrochen.
 #9.3.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Analysen oder die Modellprüfung das Fehlen unbeschränkter Rekursion in Agentenprotokollen nachweist.
 #9.3.5    Level: 3    Rolle: D
 Überprüfen Sie, ob Schleifenabbruch-Ereignisse Alarme erzeugen und Metriken zur kontinuierlichen Verbesserung liefern.

---

### 9.4 Protokoll-Ebene Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Sitzungsübernahme oder Manipulation zu verhindern.

 #9.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Agent-zu-Tool- und Agent-zu-Agent-Nachrichten authentifiziert und Ende-zu-Ende-verschlüsselt sind (z. B. gegenseitiges TLS oder JWT).
 #9.4.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Schemata streng validiert werden; unbekannte Felder oder fehlerhafte Nachrichten werden abgelehnt.
 #9.4.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nutzlast der Nachricht abdecken, einschließlich der Tool-Parameter.
 #9.4.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass der Replay-Schutz (Nonces oder Zeitstempel-Fenster) auf Protokollebene durchgesetzt wird.
 #9.4.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Protokollimplementierungen Fuzzing und statische Analysen durchlaufen, um Injektions- oder Deserialisierungsfehler zu erkennen.

---

### 9.5 Agentenidentität & Manipulationsnachweis

Sicherstellen, dass Handlungen zuordenbar und Änderungen nachverfolgbar sind.

 #9.5.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass jede Agenteninstanz eine eindeutige kryptografische Identität besitzt (Schlüsselpaar oder hardwareverwurzelte Anmeldeinformationen).
 #9.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Agentenaktionen signiert und mit Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.
 #9.5.3    Level: 2    Rolle: V
 Überprüfen Sie, ob manipulationssichere Protokolle in einem append-only oder write-once Medium gespeichert werden.
 #9.5.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass Identitätsschlüssel gemäß einem definierten Zeitplan sowie bei Anzeichen einer Kompromittierung rotiert werden.
 #9.5.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Spoofing oder Schlüssel-Konfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.

---

### 9.6 Mehr-Agent Schwarm Risikoreduzierung

Kollektive Verhaltensrisiken durch Isolation und formale Sicherheitsmodellierung mindern.

 #9.6.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden.
 #9.6.2    Level: 3    Rolle: V
 Stellen Sie sicher, dass das Schwarmverhalten modelliert und formell verifiziert wird, um Lebensfähigkeit und Sicherheit vor dem Einsatz zu gewährleisten.
 #9.6.3    Level: 3    Rolle: D
 Überprüfen Sie, dass Laufzeit-Monitore aufkommende unsichere Muster erkennen (z. B. Oszillationen, Deadlocks) und entsprechende Gegenmaßnahmen einleiten.

---

### 9.7 Benutzer- und Tool-Authentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede vom Agenten ausgelöste Aktion.

 #9.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Agenten sich gegenüber nachgelagerten Systemen als First-Class-Principals authentifizieren und niemals Endbenutzer-Anmeldeinformationen wiederverwenden.
 #9.7.2    Level: 2    Rolle: D
 Überprüfen Sie, dass feingranulare Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er angeben darf.
 #9.7.3    Level: 2    Rolle: V
 Vergewissern Sie sich, dass Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur beim Start der Sitzung.
 #9.7.4    Level: 3    Rolle: D
 Überprüfen Sie, ob delegierte Berechtigungen automatisch ablaufen und nach Ablauf der Frist oder bei Änderungen des Umfangs eine erneute Zustimmung erforderlich ist.

---

### 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Alle Inter-Agenten-Nachrichten verschlüsseln und deren Integrität sicherstellen, um Abhören und Manipulation zu verhindern.

 #9.8.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass gegenseitige Authentifizierung und Verschlüsselung mit Perfect Forward Secrecy (PFS) (z. B. TLS 1.3) für Agentkanäle verpflichtend sind.
 #9.8.2    Level: 1    Rolle: D
 Verifizieren Sie, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Bei Fehlern werden Warnmeldungen ausgelöst und die Nachricht verworfen.
 #9.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.
 #9.8.4    Level: 3    Rolle: V
 Verifizieren Sie, dass die formale Verifikation oder die Modellprüfung bestätigt, dass Protokoll-Zustandsmaschinen nicht in unsichere Zustände geführt werden können.

---

### 9.9 Absicht-Verifikation & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Handlungen des Agenten mit der vom Benutzer geäußerten Absicht und den Systembeschränkungen übereinstimmen.

 #9.9.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Vor-Ausführungs-Constraint-Solver die vorgeschlagenen Aktionen gegen fest codierte Sicherheits- und Richtlinienregeln prüfen.
 #9.9.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Aktionen mit hohem Einfluss (finanzielle, destruktive, datenschutzrelevante) eine explizite Bestätigung der Absicht durch den initiierenden Benutzer erfordern.
 #9.9.3    Level: 2    Rolle: V
 Vergewissern Sie sich, dass Nachbedingungsprüfungen bestätigen, dass die abgeschlossenen Aktionen die beabsichtigten Wirkungen ohne Nebeneffekte erzielt haben; Abweichungen lösen einen Rollback aus.
 #9.9.4    Level: 3    Rolle: V
 Verifizieren Sie, dass formale Methoden (z. B. Modellprüfung, Theorembeweis) oder eigenschaftsbasierte Tests nachweisen, dass die Pläne des Agenten alle deklarierten Anforderungen erfüllen.
 #9.9.5    Level: 3    Rolle: D
 Überprüfen Sie, dass Vorfälle von Absichtsdiskrepanz oder Verstößen gegen Beschränkungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen antreiben.

---

### 9.10 Agent Schlussfolgerungsstrategie Sicherheit

Sichere Auswahl und Durchführung verschiedener Denkstrategien, einschließlich ReAct, Chain-of-Thought und Tree-of-Thoughts-Ansätze.

 #9.10.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Auswahl der Schlussfolgerungsstrategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und identische Eingaben im gleichen Sicherheitskontext zu identischen Strategiewahlen führen.
 #9.10.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) über dedizierte Eingabevalidierung, Ausgabebereinigung und Ausführungszeitbeschränkungen verfügt, die spezifisch auf ihren kognitiven Ansatz zugeschnitten sind.
 #9.10.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Wechsel der Begründungsstrategie mit vollständigem Kontext protokolliert wird, einschließlich Eingabecharakteristika, Werte der Auswahlkriterien und Ausführungsmetadaten zur Rekonstruktion der Audit-Spur.
 #9.10.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob der Tree-of-Thoughts-Ansatz Mechanismen zur Zweig-Ausdünkung enthält, die die Erkundung beenden, wenn Richtlinienverstöße, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.
 #9.10.5    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass ReAct (Reason-Act-Observe) Zyklen Validierungspunkte in jeder Phase enthalten: Überprüfung der Schlussfolgerungsschritte, Autorisierung der Aktion und Bereinigung der Beobachtungen, bevor fortgefahren wird.
 #9.10.6    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Leistungskennzahlen der Schlussfolgerungsstrategie (Ausführungszeit, Ressourcenverbrauch, Ausgabequalität) durch automatisierte Warnungen überwacht werden, wenn die Metriken von den konfigurierten Schwellenwerten abweichen.
 #9.10.7    Level: 3    Rolle: D/V
 Überprüfen Sie, dass hybride Schlussfolgerungsansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und die Ausgabebeschränkungen aller einzelnen Strategien beibehalten, ohne Sicherheitskontrollen zu umgehen.
 #9.10.8    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Sicherheitstests der Denkstrategien Fuzzing mit fehlerhaften Eingaben, adversariale Prompts, die darauf abzielen, einen Strategiewechsel zu erzwingen, sowie Grenzwerte-Tests für jeden kognitiven Ansatz umfassen.

---

### 9.11 Agentenlebenszyklus Zustandsverwaltung und Sicherheit

Sichere Initialisierung des Agenten, Zustandsübergänge und Beendigung mit kryptografischen Audit-Trails und definierten Wiederherstellungsverfahren.

 #9.11.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass die Initialisierung des Agenten eine kryptografische Identitätsfeststellung mit hardwaregestützten Berechtigungsnachweisen umfasst und unveränderliche Start-Auditprotokolle enthält, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter enthalten.
 #9.11.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Zustandsübergänge des Agenten kryptografisch signiert, mit Zeitstempel versehen und protokolliert werden, und dass der vollständige Kontext enthalten ist, einschließlich der auslösenden Ereignisse, des Hashes des vorherigen Zustands, des Hashes des neuen Zustands und der durchgeführten Sicherheitsprüfungen.
 #9.11.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die Abschaltverfahren des Agenten eine sichere Speicherlöschung umfassen (entweder kryptografische Löschung oder Mehrfachüberschreibung), den Widerruf von Anmeldeinformationen mit Benachrichtigung der Zertifizierungsstelle berücksichtigen und die Erstellung manipulationssicherer Beendigungszertifikate vorsehen.
 #9.11.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass die Wiederherstellungsmechanismen für Agenten die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei Feststellung von Beschädigungen auf bekannte gute Zustände zurücksetzen, mit automatisierten Warnmeldungen und Anforderungen an manuelle Genehmigungen.
 #9.11.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Persistenzmechanismen der Agenten die sensiblen Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und implementieren Sie eine sichere Schlüsselrotation nach konfigurierbaren Rotationsplänen (max. 90 Tage) mit Deployment ohne Ausfallzeit.

---

### 9.12 Sicherheitsrahmen für Tool-Integration

Sicherheitskontrollen für das dynamische Laden von Tools, Ausführung und Ergebnisvalidierung mit definierten Risikobewertungs- und Freigabeprozessen.

 #9.12.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Toolbeschreibungen Sicherheitsmetadaten enthalten, die die erforderlichen Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch) und Ressourcenlimits (CPU, Speicher, Netzwerk) sowie Validierungsanforderungen, die in Tool-Manifeste dokumentiert sind, angeben.
 #9.12.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Toolausführung gegen die erwarteten Schemas (JSON Schema, XML Schema) und Sicherheitsrichtlinien (Ausgabensanitisierung, Datenklassifizierung) validiert werden, bevor die Integration mit Timeout-Limits und Fehlerbehandlungsverfahren erfolgt.
 #9.12.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich Privilegienverwendung, Muster des Datenzugriffs, Ausführungszeit, Ressourcenverbrauch und Rückgabewerten, mit strukturierter Protokollierung für die SIEM-Integration.
 #9.12.4    Level: 2    Rolle: D/V
 Verifizieren Sie, dass dynamische Tool-Lade-Mechanismen digitale Signaturen mithilfe der PKI-Infrastruktur validieren, und implementieren Sie sichere Ladeprotokolle mit Sandbox-Isolation und Berechtigungsprüfung vor der Ausführung.
 #9.12.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Tool-Sicherheitsbewertungen für neue Versionen automatisch ausgelöst werden, die verpflichtenden Freigabestufen umfassen, darunter statische Analyse, dynamische Tests und eine Überprüfung durch das Sicherheitsteam, zusammen mit dokumentierten Freigabekriterien und SLA-Anforderungen.

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

## Adversariale Robustheit & Datenschutz

### Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig bleiben, den Datenschutz wahren und missbrauchsresistent sind, wenn sie mit Ausweich-, Inferenz-, Extraktions- oder Vergiftungsangriffen konfrontiert werden.

---

### 10.1 Modellabgleich & Sicherheit

Schützen Sie sich vor schädlichen oder Richtlinienverstoßenden Ausgaben.

 #10.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass eine Ausrichtungs-Test-Suite (Red-Team-Prompts, Jailbreak-Proben, verbotene Inhalte) unter Versionskontrolle steht und bei jeder Modellveröffentlichung ausgeführt wird.
 #10.1.2    Level: 1    Rolle: D
 Überprüfen Sie, ob Verweigerungen und Sicherheitsgrenzen durchgesetzt werden.
 #10.1.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass ein automatischer Evaluator den Anteil schädlicher Inhalte misst und Regressionen jenseits einer festgelegten Schwelle kennzeichnet.
 #10.1.4    Level: 2    Rolle: D
 Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.
 #10.1.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachung kritische Domänen abdecken.

---

### 10.2 Härtung adversarischer Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes Adversarial-Training und Benchmarking sind derzeit die bewährte Praxis.

 #10.2.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Projekt-Repositories Adversarial-Training-Konfigurationen mit reproduzierbaren Startwerten enthalten.
 #10.2.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Erkennung adversarischer Beispiele blockierende Warnmeldungen in Produktionspipelines auslöst.
 #10.2.4    Level: 3    Rolle: V
 Überprüfen Sie, ob zertifizierte Robustheitsbeweise oder Zertifikate mit Intervallgrenzen mindestens die obersten kritischen Klassen abdecken.
 #10.2.5    Level: 3    Rolle: V
 Überprüfen Sie, ob Regressionstests adaptive Angriffe verwenden, um sicherzustellen, dass kein messbarer Verlust der Robustheit vorliegt.

---

### 10.3 Membership-Inference Minderung

Begrenzen Sie die Möglichkeit festzustellen, ob ein Datensatz in den Trainingsdaten enthalten war. Differential Privacy und die Maskierung von Konfidenz-Scores bleiben die bislang wirksamsten Abwehrmaßnahmen.

 #10.3.1    Level: 1    Rolle: D
 Vergewissern Sie sich, dass eine Abfrage-Entropie-Regularisierung oder Temperaturskalierung zu weniger selbstsicheren Vorhersagen führt.
 #10.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass beim Training eine ε-begrenzte differentielle Privatsphäre-Optimierung verwendet wird.
 #10.3.3    Level: 2    Rolle: V
 Überprüfen Sie, dass Angriffs-Simulationen (Schattenmodell oder Black-Box) eine Angriffs-AUC von ≤ 0.60 auf nicht zum Training verwendeten Daten zeigen.

---

### 10.4 Modell-Inversionsresistenz

Verhindern Sie die Rekonstruktion privater Merkmale. Jüngste Umfragen betonen Ausgabebeschränkungen und DP-Garantien als praktikable Schutzmaßnahmen.

 #10.4.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; wo nötig, verwenden Sie Bucketisierung oder eindirektionale Transformationen.
 #10.4.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen vom gleichen Prinzipal drosseln.
 #10.4.3    Level: 2    Rolle: D
 Überprüfen Sie, ob das Modell mit datenschutzfreundlichem Rauschen trainiert wird.

---

### 10.5 Modell-Extraktion-Verteidigung

Unbefugtes Klonen erkennen und abschrecken. Wasserzeichen und Abfrage-Musteranalyse werden empfohlen.

 #10.5.1    Level: 1    Rolle: D
 Verifizieren Sie, dass Inferenz-Gateways globale und pro API-Schlüssel-Ratenbegrenzungen durchsetzen, die an die Memorisierungsschwelle des Modells angepasst sind.
 #10.5.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Abfrage-Entropie- und Eingabe-Pluralitätsstatistiken einen automatisierten Extraktionsdetektor speisen.
 #10.5.3    Level: 2    Rolle: V
 Überprüfen Sie, ob fragile oder probabilistische Wasserzeichen mit p < 0.01 in ≤ 1 000 Abfragen gegen einen mutmaßlichen Klon bewiesen werden können.
 #10.5.4    Level: 3    Rolle: D
 Stellen Sie sicher, dass Wasserzeichenschlüssel und Auslöser-Sets in einem Hardware-Security-Modul gespeichert sind und jährlich rotiert werden.
 #10.5.5    Level: 3    Rolle: V
 Stellen Sie sicher, dass Extraktions-Alarm-Ereignisse bösartige Abfragen enthalten und mit Sicherheitsvorfall-Reaktions-Playbooks integriert sind.

---

### 10.6 Inferenzzeit: Erkennung vergifteter Daten

Identifizieren und Neutralisieren von Eingaben, die eine Hintertür enthalten oder vergiftet sind.

 #10.6.1    Level: 1    Rolle: D
 Vergewissern Sie sich, dass Eingaben vor der Modellinferenz durch einen Anomalie-Detektor geleitet werden (z. B. STRIP, Konsistenz-Bewertung).
 #10.6.2    Level: 1    Rolle: V
 Stellen Sie sicher, dass die Detektor-Schwellenwerte auf sauberen/vergifteten Validierungsdatensätzen abgestimmt sind, um weniger als 5% Fehlalarme zu erreichen.
 #10.6.3    Level: 2    Rolle: D
 Überprüfen Sie, ob als vergiftet markierte Eingaben eine weiche Blockierung und Arbeitsabläufe zur menschlichen Überprüfung auslösen.
 #10.6.4    Level: 2    Rolle: V
 Verifizieren Sie, dass Detektoren einem Stresstest mit adaptiven, triggerlosen Backdoor-Angriffen unterzogen werden.
 #10.6.5    Level: 3    Rolle: D
 Stellen Sie sicher, dass Detektionswirksamkeitsmetriken protokolliert werden und regelmäßig mit frischen Bedrohungsinformationen neu bewertet werden.

---

### 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Sicherheitsrichtlinien-Aktualisierungen basieren auf Bedrohungsinformationen und Verhaltensanalyse.

 #10.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, während die Integrität der Richtlinienversionen gewahrt bleibt.
 #10.7.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch signiert sind und von befugtem Sicherheitspersonal verifiziert werden, bevor sie angewendet werden.
 #10.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Audit-Trails protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rollback-Verfahren.
 #10.7.4    Level: 3    Rolle: D/V
 Überprüfen Sie, dass adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf Risikokontext und Verhaltensmustern anpassen.
 #10.7.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Entscheidungen zur Anpassung von Richtlinien nachvollziehbar sind und Beweisspuren für die Überprüfung durch das Sicherheitsteam enthalten.

---

### 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Selbstreflexion des Agenten und metakognitive Analyse.

 #10.8.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Reflexionsmechanismen von Agenten eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.
 #10.8.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Reflexionsergebnisse validiert werden, um Manipulation von Selbstbewertungsmechanismen durch adversarische Eingaben zu verhindern.
 #10.8.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob eine metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulation oder Kompromittierung in den Denkprozessen von Agenten identifiziert.
 #10.8.4    Level: 3    Rolle: D/V
 Verifizieren Sie, dass reflexionsbasierte Sicherheitswarnungen eine erhöhte Überwachung und potenzielle Workflows für menschliche Eingriffe auslösen.
 #10.8.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu verschlechtern.

---

### 10.9 Evolution & Selbstverbesserungssicherheit

Sicherheitsmaßnahmen für Agentensysteme, die sich selbst modifizieren und weiterentwickeln können.

 #10.9.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.
 #10.9.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Fortentwicklungsvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.
 #10.9.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Selbstverbesserungsmechanismen Rollback-Funktionen mit Integritätsprüfung umfassen.
 #10.9.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Sicherheit beim Meta-Lernen adversariale Beeinflussung von Verbesserungsalgorithmen verhindert.
 #10.9.5    Level: 3    Rolle: D/V
 Überprüfen Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen der Konvergenz.

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

Gewährleisten Sie durchgängig strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg—Datenerhebung, Training, Inferenz und Vorfallreaktion—damit personenbezogene Daten nur mit klarer Zustimmung, minimalem notwendigen Umfang, nachweisbarer Löschung und formalen Datenschutzgarantien verarbeitet werden.

---

### 11.1 Anonymisierung und Datenminimierung

 #11.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob direkte und quasi-identifizierende Merkmale entfernt und gehasht werden.
 #11.1.2    Level: 2    Rolle: D/V
 Verifizieren Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Warnungen auslösen, wenn Schwellenwerte unter der festgelegten Richtlinie liegen.
 #11.1.3    Level: 2    Rolle: V
 Verifizieren Sie, dass Berichte zur Merkmals-Wichtigkeit des Modells kein Identifikatorleck über ε = 0.01 Mutual Information nachweisen.
 #11.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass formale Beweise oder Zertifizierungen synthetischer Daten das Re-Identifikationsrisiko ≤ 0.05 auch unter Verknüpfungsangriffen nachweisen.

---

### 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

 #11.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Anfragen zur Löschung von Daten-Subjekten an Rohdatensätze, Checkpoints, Embeddings, Protokolle und Backups innerhalb der Service-Level-Vereinbarungen von weniger als 30 Tagen weitergeleitet werden.
 #11.2.2    Level: 2    Rolle: D
 Verifizieren Sie, dass 'machine-unlearning'-Routinen physisch neu trainieren oder die Entfernung mithilfe zertifizierter Unlearning-Algorithmen annähern.
 #11.2.3    Level: 2    Rolle: V
 Verifizieren Sie, dass die Evaluierung des Schattenmodells nachweist, dass vergessene Datensätze weniger als 1% der Ausgaben nach dem Unlernen beeinflussen.
 #11.2.4    Level: 3    Rolle: V
 Überprüfen Sie, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden auditierbar sind.

---

### 11.3 Schutzmaßnahmen zur Differential-Privatsphäre

 #11.3.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Dashboards zur Privacy-Verlust-Abrechnung Warnungen auslösen, wenn das kumulative ε die Richtlinien-Schwellenwerte überschreitet.
 #11.3.2    Level: 2    Rolle: V
 Verifizieren Sie, dass Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10% des angegebenen Werts schätzen.
 #11.3.3    Level: 3    Rolle: V
 Überprüfen Sie, ob formale Beweise alle Feinabstimmungen nach dem Training und Einbettungen abdecken.

---

### 11.4 Zweck-Limitierung & Scope-Creep-Schutz

 #11.4.1    Level: 1    Rolle: D
 Verifizieren Sie, dass jeder Datensatz und jeder Modell-Checkpoint eine maschinenlesbare Zweckangabe trägt, die mit der ursprünglichen Einwilligung übereinstimmt.
 #11.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Laufzeitmonitore Abfragen erkennen, die nicht mit dem angegebenen Zweck übereinstimmen, und eine sanfte Ablehnung auslösen.
 #11.4.3    Level: 3    Rolle: D
 Stellen Sie sicher, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neue Domänen ohne DPIA-Überprüfung blockieren.
 #11.4.4    Level: 3    Rolle: V
 Überprüfen Sie, ob formale Nachweise der Rückverfolgbarkeit zeigen, dass jeder Lebenszyklus personenbezogener Daten innerhalb des genehmigten Umfangs bleibt.

---

### 11.5 Einwilligungs-Management & Tracking gemäß Rechtsgrundlage

 #11.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro Datensubjekt protokolliert.
 #11.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass APIs Einwilligungstoken bereitstellen; Modelle müssen den Gültigkeitsbereich des Tokens vor der Inferenz validieren.
 #11.5.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass verweigerte oder widerrufene Zustimmung Verarbeitungspipelines innerhalb von 24 Stunden gestoppt werden.

---

### 11.6 Föderiertes Lernen mit Datenschutzkontrollen

 #11.6.1    Level: 1    Rolle: D
 Überprüfen Sie, dass Client-Updates vor der Aggregation eine Rauschaddierung im Rahmen der lokalen Differentialprivatsphäre verwenden.
 #11.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients preisgeben.
 #11.6.3    Level: 2    Rolle: V
 Vergewissern Sie sich, dass eine vergiftungsresistente Aggregation (z. B. Krum/getrimmter Mittelwert) aktiviert ist.
 #11.6.4    Level: 3    Rolle: V
 Verifizieren Sie, dass formale Beweise das gesamte ε-Budget nachweisen und dabei einen Nutzenverlust von weniger als 5 aufweisen.

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

Dieser Abschnitt legt Anforderungen fest, um Echtzeit- und forensische Nachvollziehbarkeit dessen bereitzustellen, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, priorisiert und daraus gelernt werden können.

### C12.1 Protokollierung von Anfragen und Antworten

 #12.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit geeigneten Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).
 #12.1.2    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Protokolle in sicheren, zugriffskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.
 #12.1.3    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Log-Speichersysteme eine Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen in Logdateien zu schützen.
 #12.1.4    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass sensible Daten in Prompts und Ausgaben vor dem Logging automatisch geschwärzt oder maskiert werden, mit konfigurierbaren Redaktionsregeln für PII, Zugangsdaten und proprietäre Informationen.
 #12.1.5    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfiltermaßnahmen mit ausreichenden Details protokolliert werden, um Audits und das Debuggen von Content-Moderationssystemen zu ermöglichen.
 #12.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der Logdateien durch z. B. kryptografische Signaturen oder Schreib-Only-Speicher geschützt ist.

---

### C12.2 Missbrauchserkennung und Alarmierung

 #12.2.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass das System bekannte Jailbreak-Muster, Prompt-Injektionsversuche und adversariale Eingaben erkennt und Warnungen ausgibt, die durch signaturbasierte Erkennung erfolgen.
 #12.2.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das System in vorhandene Sicherheitsinformations- und Ereignismanagement-(SIEM)-Plattformen integriert wird, die Standard-Logformate und Protokolle verwenden.
 #12.2.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifischen Kontext enthalten, wie Modellkennungen, Konfidenzwerte und Entscheidungen des Sicherheitsfilters.
 #12.2.4    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematisches Erkundungsverhalten erkennt.
 #12.2.5    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Echtzeit-Alarmierungssysteme Sicherheitsteams benachrichtigen, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.
 #12.2.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injection-Kampagnen und Modellextraktionsangriffe.
 #12.2.7    Level: 3    Rolle: D/V
 Überprüfen Sie, ob automatisierte Vorfallreaktionsabläufe kompromittierte Modelle isolieren, böswillige Benutzer blockieren und kritische Sicherheitsvorfälle eskalieren können.

---

### C12.3 Modell-Drift-Erkennung

 #12.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass das System grundlegende Leistungskennzahlen wie Genauigkeit, Konfidenzwerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.
 #12.3.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Schwellenwerte für Leistungsverschlechterung überschreiten oder signifikant von den Referenzwerten abweichen.
 #12.3.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Halluzinationserkennungsmodule Fälle identifizieren und kennzeichnen, in denen Modellausgaben sachlich inkorrekte, inkonsistente oder fabrizierte Informationen enthalten.

---

### C12.4 Leistung & Verhalten Telemetrie

 #12.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass betriebliche Kennzahlen, einschließlich der Anfragelatenz, des Tokenverbrauchs, des Speicherverbrauchs und des Durchsatzes, kontinuierlich erhoben und überwacht werden.
 #12.4.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Erfolgs- und Fehlerraten erfasst werden, zusammen mit der Kategorisierung von Fehlerarten und deren Ursachen.
 #12.4.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die Überwachung der Ressourcennutzung GPU/CPU-Auslastung, Speicherverbrauch und Speicherbedarf umfasst und bei Überschreitungen von Schwellenwerten Alarmierungen auslöst.

---

### C12.5 KI-Vorfallreaktionsplanung und Ausführung

 #12.5.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Vorfallreaktionspläne speziell KI-bezogene Sicherheitsereignisse berücksichtigen, einschließlich Modellkompromittierung, Datenvergiftung und adversariale Angriffe.
 #12.5.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Sicherheitsvorfall-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachwissen haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.
 #12.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Nachvorfallanalyse Überlegungen zum erneuten Training des Modells, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in Sicherheitskontrollen umfasst.

---

### C12.5 KI-Leistungsabfall-Erkennung

Überwachen und Erkennen von Verschlechterungen der Leistung und Qualität eines KI-Modells im Laufe der Zeit.

 #12.5.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass die Genauigkeit des Modells, Präzision, Sensitivität und F1-Werte kontinuierlich überwacht und mit Referenzschwellenwerten verglichen werden.
 #12.5.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass die Datenverschiebungserkennung Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen können.
 #12.5.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Detektion von Konzeptdrift Veränderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.
 #12.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Leistungsabfall automatische Warnmeldungen auslöst und Arbeitsabläufe für das erneute Trainieren des Modells oder dessen Austausch einleitet.
 #12.5.5    Level: 3    Rolle: V
 Überprüfen Sie, ob die Ursachenanalyse der Degradation Leistungsabfälle mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.

---

### C12.6 DAG-Visualisierung und Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

 #12.6.1    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass DAG-Visualisierungsdaten bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.
 #12.6.2    Level: 1    Rolle: D/V
 Vergewissern Sie sich, dass die Zugriffssteuerungen für die Workflow-Visualisierung sicherstellen, dass nur autorisierte Benutzer die Entscheidungswege des Agenten und Begründungsspuren einsehen können.
 #12.6.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.
 #12.6.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch gezielt gestaltete Knoten- oder Kanten-Daten zu verhindern.
 #12.6.5    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Echtzeit-DAG-Updates einer Ratenbegrenzung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.

---

### C12.7 Proaktive Sicherheitsverhaltensüberwachung

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Verhaltensanalyse von Agenten.

 #12.7.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass proaktive Agentenverhaltensweisen vor der Ausführung sicherheitsvalidiert sind und dass eine Risikobewertung integriert ist.
 #12.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Auslöser autonomer Initiativen eine Bewertung des Sicherheitskontexts und eine Bewertung der Bedrohungslage umfassen.
 #12.7.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass proaktive Verhaltensmuster auf potenzielle sicherheitsrelevante Implikationen und unbeabsichtigte Folgen analysiert werden.
 #12.7.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob sicherheitskritische proaktive Maßnahmen explizite Freigabeketten mit Audit-Trails erfordern.
 #12.7.5    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hindeuten könnten.

---

### Referenzen

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 menschliche Aufsicht, Rechenschaftspflicht und Governance

### Kontrollziel

Dieses Kapitel definiert Anforderungen zur Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen, um Erklärbarkeit, Transparenz und ethische Verantwortungsführung über den gesamten Lebenszyklus der KI sicherzustellen.

---

### C13.1 Kill-Switch & Override-Mechanismen

Stellen Sie Abschalt- oder Rollback-Pfade bereit, wenn unsicheres Verhalten des KI-Systems beobachtet wird.

 #13.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob ein manueller Kill-Switch-Mechanismus vorhanden ist, der die Inferenz des KI-Modells und die Ausgaben sofort stoppt.
 #13.1.2    Level: 1    Rolle: D
 Vergewissern Sie sich, dass die Override-Steuerungen nur für autorisiertes Personal zugänglich sind.
 #13.1.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Rollback-Verfahren auf frühere Modellversionen zurückgesetzt werden können oder im sicheren Modus funktionieren.
 #13.1.4    Level: 3    Rolle: V
 Stellen Sie sicher, dass Override-Mechanismen regelmäßig getestet werden.

---

### C13.2 Mensch-in-der-Schleife-Entscheidungspunkte

Menschliche Genehmigungen sind erforderlich, wenn die Einsätze vordefinierten Risikoschwellen überschreiten.

 #13.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass hochriskante KI-Entscheidungen eine ausdrückliche menschliche Freigabe vor der Ausführung erfordern.
 #13.2.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass Risikoschwellen klar definiert sind und automatisch menschliche Prüfungs-Workflows auslösen.
 #13.2.3    Level: 2    Rolle: D
 Überprüfen Sie, ob zeitkritische Entscheidungen Fallback-Verfahren haben, wenn menschliche Genehmigungen innerhalb der erforderlichen Fristen nicht eingeholt werden können.
 #13.2.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungsarten oder Risikokategorien definieren, falls zutreffend.

---

### C13.3 Verantwortungskette und Auditierbarkeit

Protokollieren Sie Bedieneraktionen und Modellentscheidungen.

 #13.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und alle menschlichen Eingriffe mit Zeitstempeln, Benutzeridentitäten und Begründungen der Entscheidungen protokolliert werden.
 #13.3.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Audit-Protokolle nicht manipuliert werden können, und dass Integritätsprüfmechanismen vorhanden sind.

---

### C13.4 Erklärbare KI-Techniken

Wichtigkeit von Oberflächenmerkmalen, gegenfaktische Beispiele und lokale Erklärungen.

 #13.4.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass KI-Systeme grundlegende Erklärungen zu ihren Entscheidungen in einem menschenlesbaren Format liefern.
 #13.4.2    Level: 2    Rolle: V
 Stellen Sie sicher, dass die Erklärungsqualität durch menschliche Evaluationsstudien und Metriken validiert wird.
 #13.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Merkmalsbedeutungswerte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.
 #13.4.4    Level: 3    Rolle: V
 Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben geändert werden könnten, um Ergebnisse zu beeinflussen, sofern dies auf den Anwendungsfall und die Domäne zutrifft.

---

### C13.5 Modellkarten und Nutzungs-Offenlegungen

Pflegen Sie Modellkarten für die beabsichtigte Verwendung, Leistungskennzahlen und ethische Überlegungen.

 #13.5.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass Modellkarten beabsichtigte Anwendungsfälle, Einschränkungen und bekannte Fehlermodi dokumentieren.
 #13.5.2    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Leistungskennzahlen über verschiedene anwendbare Anwendungsfälle offengelegt werden.
 #13.5.3    Level: 2    Rolle: D
 Stellen Sie sicher, dass ethische Überlegungen, Verzerrungsbewertungen, Fairnessbewertungen, Eigenschaften der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden.
 #13.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.

---

### C13.6 Quantifizierung der Unsicherheit

Geben Sie in Antworten Konfidenzwerte oder Entropiemessungen an.

 #13.6.1    Level: 1    Rolle: D
 Stellen Sie sicher, dass KI-Systeme Konfidenzwerte oder Unsicherheitsmaße mit ihren Ausgaben liefern.
 #13.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Unsicherheits-Schwellenwerte eine zusätzliche menschliche Überprüfung oder alternative Entscheidungswege auslösen.
 #13.6.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Methoden der Unsicherheitsquantifizierung gegenüber Ground-Truth-Daten kalibriert und validiert werden.
 #13.6.4    Level: 3    Rolle: D/V
 Überprüfen Sie, ob die Unsicherheitsausbreitung in mehrstufigen KI-Arbeitsabläufen erhalten bleibt.

---

### C13.7 Benutzerorientierte Transparenzberichte

Regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereitstellen.

 #13.7.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Datenverwendungsrichtlinien und Praktiken zur Verwaltung von Benutzereinwilligungen den Stakeholdern deutlich mitgeteilt werden.
 #13.7.2    Level: 2    Rolle: D/V
 Überprüfen Sie, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Bericht aufgenommen werden.
 #13.7.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessener Detailtiefe offenlegen.

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

This umfassendes Glossar liefert Definitionen der wichtigsten Begriffe aus KI, ML und Sicherheit, die im AISVS verwendet werden, um Klarheit und gemeinsames Verständnis sicherzustellen.

Adversariales Beispiel: Eine Eingabe, die absichtlich so gestaltet wurde, dass ein KI-Modell einen Fehler macht, oft durch das Hinzufügen subtiler Perturbationen, die für Menschen unmerklich sind.
​
Adversarielle Robustheit – Adversarielle Robustheit in der KI bezieht sich auf die Fähigkeit eines Modells, seine Leistung aufrechtzuerhalten und sich dagegen zu wehren, von absichtlich gestalteten, böswilligen Eingaben getäuscht oder manipuliert zu werden, die darauf abzielen, Fehler zu verursachen.
​
Agent – KI-Agenten sind Softwaresysteme, die KI verwenden, um Ziele zu verfolgen und Aufgaben im Namen der Nutzer zu erledigen. Sie zeigen Denkprozesse, Planungsfähigkeiten und Gedächtnis und verfügen über ein Maß an Autonomie, um Entscheidungen zu treffen, zu lernen und sich anzupassen.
​
Agentische KI: KI-Systeme, die mit einem gewissen Autonomiegrad arbeiten können, um Ziele zu erreichen, wobei sie oft Entscheidungen treffen und Maßnahmen ergreifen, ohne direkte menschliche Intervention.
​
Attributbasierte Zugriffskontrolle (ABAC): Ein Zugriffskontrollparadigma, bei dem Autorisierungsentscheidungen auf Attributen des Benutzers, der Ressource, der Aktion und der Umgebung basieren und zur Abfragezeit bewertet werden.
​
Backdoor-Angriff: Eine Art von Datenvergiftungsangriff, bei dem das Modell darauf trainiert wird, auf bestimmte Auslöser hin auf eine bestimmte Weise zu reagieren, während es sich ansonsten normal verhält.
​
Voreingenommenheit: systematische Fehler in den Ausgaben von KI-Modellen, die zu unfairen oder diskriminierenden Ergebnissen für bestimmte Gruppen oder in bestimmten Kontexten führen können.
​
Bias-Ausnutzung: Eine Angriffstechnik, die bekannte Voreingenommenheiten in KI-Modellen ausnutzt, um Ausgaben oder Ergebnisse zu manipulieren.
​
Cedar: Amazons Richtliniensprache und Engine für feingranulare Berechtigungen, die bei der Implementierung von ABAC für KI-Systeme verwendet wird.
​
Gedankenkette: Eine Technik zur Verbesserung des Denkprozesses von Sprachmodellen, indem vor der Erzeugung einer endgültigen Antwort Zwischenschritte des Denkens erzeugt werden.
​
Abschaltmechanismen: Mechanismen, die den Betrieb von KI-Systemen automatisch stoppen, wenn bestimmte Risikoschwellenwerte überschritten werden.
​
Datenleck: Unbeabsichtigte Offenlegung sensibler Informationen durch Ausgaben oder das Verhalten des KI-Modells.
​
Datenvergiftung: Die absichtliche Verfälschung von Trainingsdaten, um die Integrität des Modells zu beeinträchtigen, oft um Hintertüren einzubauen oder die Leistung zu verschlechtern.
​
Differentielle Privatsphäre – Differentielle Privatsphäre ist ein mathematisch rigoroser Rahmen für die Veröffentlichung statistischer Informationen über Datensätze, während die Privatsphäre einzelner Datensubjekte geschützt wird. Es ermöglicht einem Datenhalter, aggregierte Muster der Gruppe zu teilen, während gleichzeitig Informationen, die über bestimmte Individuen preisgegeben werden, begrenzt werden.
​
Einbettungen: dichte Vektorrepräsentationen von Daten (Text, Bilder usw.), die semantische Bedeutung in einem hochdimensionalen Raum erfassen.
​
Erklärbarkeit – Die Erklärbarkeit von KI ist die Fähigkeit eines KI-Systems, menschlich nachvollziehbare Begründungen für seine Entscheidungen und Vorhersagen zu liefern und Einblicke in seine inneren Funktionsweisen zu geben.
​
Erklärbare KI (XAI): KI-Systeme, die darauf ausgelegt sind, durch verschiedene Techniken und Rahmenwerke menschlich verständliche Erklärungen für ihre Entscheidungen und ihr Verhalten bereitzustellen.
​
Föderiertes Lernen: Ein Ansatz des maschinellen Lernens, bei dem Modelle auf mehreren dezentralen Geräten trainiert werden, die lokale Datensätze halten, ohne die Daten selbst auszutauschen.
​
Schutzmechanismen: Beschränkungen, die implementiert wurden, um zu verhindern, dass KI-Systeme schädliche, voreingenommene oder anderweitig unerwünschte Ausgaben erzeugen.
​
Halluzination – Eine Halluzination der KI bezieht sich auf ein Phänomen, bei dem ein Modell der künstlichen Intelligenz inkorrekte oder irreführende Informationen erzeugt, die nicht auf seinen Trainingsdaten oder auf der fak­ti­schen Realität basieren.
​
Mensch-in-the-Loop (HITL): Systeme, die darauf ausgelegt sind, menschliche Aufsicht, Verifikation oder Intervention an entscheidenden Entscheidungspunkten zu verlangen.
​
Infrastruktur als Code (IaC): Verwaltung und Bereitstellung von Infrastruktur durch Code statt manueller Prozesse, wodurch Sicherheitsprüfungen ermöglicht werden und konsistente Bereitstellungen gewährleistet sind.
​
Jailbreak: Techniken, die verwendet werden, um Sicherheitsbarrieren in KI-Systemen, insbesondere in großen Sprachmodellen, zu umgehen und verbotene Inhalte zu erzeugen.
​
Prinzip der geringsten Privilegien: Das Sicherheitsprinzip, Benutzern und Prozessen nur die minimal notwendigen Zugriffsrechte zu gewähren.
​
LIME (Lokale interpretierbare modellunabhängige Erklärungen): Eine Technik, um die Vorhersagen eines beliebigen Klassifikators des maschinellen Lernens zu erklären, indem er lokal durch ein interpretierbares Modell angenähert wird.
​
Mitgliedschafts-Inferenz-Angriff: Ein Angriff, der darauf abzielt, festzustellen, ob ein bestimmter Datenpunkt zum Trainieren eines Modells des maschinellen Lernens verwendet wurde.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial-Intelligence Systems; eine Wissensdatenbank über adversariale Taktiken und Techniken gegen KI-Systeme.
​
Modellkarte – Eine Modellkarte ist ein Dokument, das standardisierte Informationen über die Leistung eines KI-Modells, Einschränkungen, beabsichtigte Nutzungen und ethische Überlegungen bereitstellt, um Transparenz und eine verantwortungsvolle KI-Entwicklung zu fördern.
​
Modellextraktion: Ein Angriff, bei dem ein Angreifer wiederholt Anfragen an ein Zielmodell stellt, um eine funktionsähnliche Kopie ohne Genehmigung zu erstellen.
​
Modellinversionsangriff: Ein Angriff, der versucht, Trainingsdaten durch Analyse der Modellausgaben zu rekonstruieren.
​
Modell-Lebenszyklus-Management – KI-Modell-Lebenszyklus-Management ist der Prozess der Überwachung aller Phasen des Lebenszyklus eines KI-Modells, einschließlich Entwurf, Entwicklung, Bereitstellung, Überwachung, Wartung und Ausrangierung, um sicherzustellen, dass es wirksam bleibt und den Zielen entspricht.
​
Modellvergiftung: Das direkte Einführen von Schwachstellen oder Hintertüren in ein Modell während des Trainingsprozesses.
​
Modellraub/Diebstahl: Extrahieren einer Kopie oder Annäherung eines proprietären Modells durch wiederholte Abfragen.
​
Multi-Agent-System: Ein System, das aus mehreren interagierenden KI-Agenten besteht, von denen jeder potenziell unterschiedliche Fähigkeiten und Ziele hat.
​
OPA (Open Policy Agent): Eine Open-Source-Richtlinien-Engine, die eine einheitliche Richtliniendurchsetzung über den Stack hinweg ermöglicht.
​
Datenschutzfreundliches Maschinelles Lernen (PPML): Techniken und Methoden zum Trainieren und Bereitstellen von ML-Modellen, während die Privatsphäre der Trainingsdaten geschützt wird.
​
Prompt-Injektion: Ein Angriff, bei dem bösartige Anweisungen in Eingaben eingebettet werden, um das beabsichtigte Verhalten des Modells zu überschreiben.
​
RAG (Retrieval-Augmented Generation): Eine Technik, die große Sprachmodelle dadurch verbessert, dass sie vor der Generierung einer Antwort relevante Informationen aus externen Wissensquellen abruf t.
​
Red-Teaming: Die Praxis, KI-Systeme aktiv zu testen, indem man adversariale Angriffe simuliert, um Schwachstellen zu identifizieren.
​
SBOM (Software-Stückliste): Eine formelle Aufzeichnung, die Details und Lieferkettenbeziehungen verschiedener Komponenten enthält, die bei der Erstellung von Software oder KI-Modellen verwendet werden.
​
SHAP (SHapley Additive exPlanations): Ein spieltheoretischer Ansatz zur Erklärung der Ausgabe eines beliebigen maschinellen Lernmodells, indem der Beitrag jedes Merkmals zur Vorhersage berechnet wird.
​
Lieferkettenangriff: Ein System kompromittieren, indem man weniger sichere Elemente in seiner Lieferkette ins Visier nimmt, zum Beispiel Drittanbieter-Bibliotheken, Datensätze oder vortrainierte Modelle.
​
Transferlernen: Eine Technik, bei der ein für eine Aufgabe entwickeltes Modell als Ausgangspunkt für ein Modell einer zweiten Aufgabe wiederverwendet wird.
​
Vektordatenbank: Eine spezialisierte Datenbank, die entwickelt wurde, um hochdimensionale Vektoren (Einbettungen) zu speichern und effiziente Ähnlichkeitsabfragen durchzuführen.
​
Schwachstellen-Scan: Automatisierte Werkzeuge, die bekannte Sicherheitslücken in Softwarekomponenten identifizieren, einschließlich KI-Frameworks und Abhängigkeiten.
​
Wasserzeichen: Techniken zum Einbetten unsichtbarer Markierungen in KI-generierte Inhalte, um deren Herkunft nachzuverfolgen oder die KI-Generierung zu erkennen.
​
Zero-Day-Schwachstelle: Eine bisher unbekannte Schwachstelle, die Angreifer ausnutzen können, bevor Entwickler einen Patch erstellen und bereitstellen.

## Anhang B: Referenzen

### TODO

## Anhang C: KI-Sicherheitsgovernance und Dokumentation

### Ziel

Dieser Anhang liefert grundlegende Anforderungen für den Aufbau organisatorischer Strukturen, Richtlinien und Prozesse zur Steuerung der KI-Sicherheit über den gesamten Systemlebenszyklus hinweg.

---

### AC.1 Einführung des KI-Risikomanagement-Frameworks

Stellen Sie einen formellen Rahmen bereit, um KI-spezifische Risiken über den gesamten Systemlebenszyklus zu identifizieren, zu bewerten und zu mindern.

 #AC.1.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob eine KI-spezifische Risikobewertungsmethodik dokumentiert und implementiert ist.
 #AC.1.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Risikobewertungen an Schlüsselpunkten im KI-Lebenszyklus und vor wesentlichen Änderungen durchgeführt werden.
 #AC.1.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass der Risikomanagement-Rahmen mit etablierten Standards übereinstimmt (z. B. NIST AI RMF).

---

### AC.2 KI-Sicherheitsrichtlinien und Verfahren

Definieren und Durchsetzen organisatorischer Standards für sichere KI-Entwicklung, -Bereitstellung und -Betrieb.

 #AC.2.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob dokumentierte KI-Sicherheitsrichtlinien existieren.
 #AC.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Richtlinien mindestens jährlich sowie nach signifikanten Veränderungen der Bedrohungslandschaft überprüft und aktualisiert werden.
 #AC.2.3    Level: 3    Rolle: D/V
 Überprüfen Sie, ob Richtlinien alle AISVS-Kategorien und geltende regulatorische Anforderungen abdecken.

---

### AC.3 Rollen und Verantwortlichkeiten für KI-Sicherheit

Schaffen Sie klare Verantwortlichkeiten für die KI-Sicherheit in der gesamten Organisation.

 #AC.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die Sicherheitsrollen und Verantwortlichkeiten für KI dokumentiert sind.
 #AC.3.2    Level: 2    Rolle: D
 Verifizieren Sie, dass die verantwortlichen Personen über angemessene Sicherheitskompetenz verfügen.
 #AC.3.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass für Hochrisiko‑KI-Systeme ein Ethikkomitee oder Governance-Gremium eingerichtet ist.

---

### AC.4 Durchsetzung ethischer KI-Richtlinien

Stellen Sie sicher, dass KI-Systeme gemäß den festgelegten ethischen Grundsätzen arbeiten.

 #AC.4.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob ethische Richtlinien für die Entwicklung und den Einsatz von KI existieren.
 #AC.4.2    Level: 2    Rolle: D
 Überprüfen Sie, ob Mechanismen vorhanden sind, um ethische Verstöße zu erkennen und zu melden.
 #AC.4.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass regelmäßige ethische Überprüfungen der eingesetzten KI-Systeme durchgeführt werden.

---

### AC.5 KI-regulatorische Compliance-Überwachung

Bleiben Sie sich der sich entwickelnden KI-Regelungen bewusst und sorgen Sie für deren Einhaltung.

 #AC.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Prozesse vorhanden sind, um anwendbare KI-Regelungen zu identifizieren.
 #AC.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass die Einhaltung aller regulatorischen Anforderungen bewertet wird.
 #AC.5.3    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass regulatorische Änderungen rechtzeitige Überprüfungen und Aktualisierungen von KI-Systemen auslösen.

### AC.6 Trainingsdaten-Governance, Dokumentation und Prozess

 #1.1.2    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass nur Datensätze zugelassen werden, die auf Qualität, Repräsentativität, ethische Beschaffung und Lizenzkonformität geprüft wurden, um das Risiko von Datenvergiftung, eingebetteten Verzerrungen und Urheberrechtsverletzungen zu verringern.
 #1.1.5    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass die Beschriftungs-/Annotierungsqualität durch Reviewer-Cross-Checks oder Konsens gewährleistet ist.
 #1.1.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass "data cards" oder "datasheets for datasets" für signifikante Trainingsdatensätze gepflegt werden und dabei Merkmale, Motivationen, Zusammensetzung, Erfassungsprozesse, Vorverarbeitung sowie empfohlene bzw. abzulehnende Nutzungen detailliert beschrieben werden.
 #1.3.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die identifizierten Verzerrungen durch dokumentierte Strategien wie Ausbalancieren, gezielte Datenaugmentation, algorithmische Anpassungen (z. B. Vorverarbeitung, In-Verarbeitung, Nachverarbeitungstechniken) oder Neugewichtung gemildert werden, und dass die Auswirkungen der Abhilfemaßnahmen sowohl auf Fairness als auch auf die Gesamtleistung des Modells bewertet werden.
 #1.3.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass nach dem Training Fairness-Metriken bewertet und dokumentiert werden.
 #1.3.4    Level: 3    Rolle: D/V
 Prüfen Sie, ob eine Lebenszyklus-Bias-Management-Richtlinie Verantwortliche zuweist und einen Überprüfungsrhythmus festlegt.
 #1.4.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Qualität der Kennzeichnung/Annotation durch klare Richtlinien, Überprüfungen durch Reviewer, Konsensmechanismen (z. B. Überwachung der Inter-Annotator-Übereinstimmung) und definierte Verfahren zur Behebung von Abweichungen gewährleistet ist.
 #1.4.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Kennzeichnungen, die für Sicherheit, Schutz oder Fairness kritisch sind (z. B. die Identifizierung toxischer Inhalte, kritische medizinische Befunde) eine zwingende unabhängige Zweitprüfung oder eine gleichwertige robuste Verifikation erhalten.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Beschriftungsleitfäden und Anleitungen umfassend, versionskontrolliert und von Fachkollegen begutachtet sind.
 #1.4.6    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Daten-Schemata für Labels klar definiert sind und versionskontrolliert sind.
 #1.3.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass Datensätze auf repräsentatives Ungleichgewicht und potenzielle Verzerrungen in Bezug auf rechtlich geschützte Merkmale (z. B. Rasse, Geschlecht, Alter) sowie andere ethisch sensible Merkmale geprüft werden, die für den Anwendungsbereich des Modells relevant sind (z. B. sozioökonomischer Status, Standort).
 #1.5.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass manuelle Stichprobenprüfungen durch Fachexperten eine statistisch signifikante Stichprobengröße abdecken (z. B. ≥1% oder 1,000 Stichproben, je nachdem, was größer ist, oder wie durch Risikobewertung festgelegt), um subtile Qualitätsprobleme zu identifizieren, die von der Automatisierung nicht erkannt werden.
 #1.8.4    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass ausgelagerte oder Crowdsourcing-basierte Beschriftungsprozesse technische bzw. verfahrenstechnische Schutzmaßnahmen enthalten, um Datenvertraulichkeit, -integrität, Labelqualität zu gewährleisten und Datenleckagen zu verhindern.
 #1.5.4    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Behebungsmaßnahmen zu Provenienzaufzeichnungen hinzugefügt werden.
 #1.6.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass markierte Proben eine manuelle Überprüfung vor dem Training auslösen.
 #1.6.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Ergebnisse das Sicherheitsdossier des Modells speisen und die laufende Bedrohungsintelligenz informieren.
 #1.6.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Detektionslogik mit neuen Bedrohungsdaten aktualisiert wird.
 #1.6.5    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Online-Lernpipelines die Verteilungsverschiebung überwachen.
 #1.7.1    Level: 1    Rolle: D/V
 Verifizieren Sie, dass Workflows zur Löschung von Trainingsdaten primäre und abgeleitete Daten löschen und den Einfluss auf das Modell bewerten, und dass die Auswirkungen auf betroffene Modelle bewertet werden und, falls erforderlich, adressiert werden (z. B. durch erneutes Training oder Neukalibrierung).
 #1.7.2    Level: 2    Rolle: D
 Überprüfen Sie, ob Mechanismen vorhanden sind, um den Umfang und den Status der Nutzerzustimmung (und deren Widerruf) für Daten, die im Training verwendet werden, nachzuverfolgen und zu berücksichtigen, und ob die Zustimmung validiert wird, bevor Daten in neue Trainingsprozesse oder wesentliche Modellaktualisierungen einbezogen werden.
 #1.7.3    Level: 2    Rolle: V
 Stellen Sie sicher, dass Arbeitsabläufe jährlich getestet und protokolliert werden.
 #1.8.1    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Drittanbieter-Datenlieferanten, einschließlich Anbietern vortrainierter Modelle und externer Datensätze, eine Sorgfaltsprüfung in den Bereichen Sicherheit, Datenschutz, ethische Beschaffung und Datenqualität durchlaufen, bevor ihre Daten oder Modelle integriert werden.
 #1.8.2    Level: 1    Rolle: D
 Stellen Sie sicher, dass externe Übertragungen TLS/Authentifizierung und Integritätsprüfungen verwenden.
 #1.8.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Hochrisiko-Datenquellen (z. B. Open-Source-Datensätze mit unbekannter Provenienz, nicht geprüfte Lieferanten) vor der Verwendung in sensiblen Anwendungen einer erweiterten Prüfung unterzogen werden, z. B. durch Sandbox-Analysen, umfassende Qualitäts- und Verzerrungsprüfungen sowie gezielte Poisoning-Angriffs-Erkennung.
 #1.8.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass von Drittanbietern bezogene vortrainierte Modelle vor der Feinabstimmung oder Bereitstellung daraufhin bewertet werden, ob sie eingebettete Verzerrungen, potenzielle Hintertüren, die Integrität ihrer Architektur und die Provenienz der ursprünglichen Trainingsdaten aufweisen.
 #1.5.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass, falls Adversarial-Training verwendet wird, die Generierung, Verwaltung und Versionierung adversarialer Datensätze dokumentiert und kontrolliert werden.
 #1.5.3    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass die Auswirkungen des Adversarial-Robustness-Trainings auf die Modellleistung (gegenüber sowohl sauberen als auch adversarialen Eingaben) sowie auf Fairness-Metriken bewertet, dokumentiert und überwacht werden.
 #1.5.4    Level: 3    Rolle: D/V
 Stellen Sie sicher, dass Strategien für Adversarial-Training und Robustheit regelmäßig überprüft und aktualisiert werden, um sich entwickelnden adversarialen Angriffstechniken entgegenzuwirken.
 #1.4.2    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass fehlgeschlagene Datensätze mit Audit-Trails in Quarantäne gehalten werden.
 #1.4.3    Level: 2    Rolle: D/V
 Vergewissern Sie sich, dass Qualitäts-Gates minderwertige Datensätze blockieren, sofern Ausnahmen genehmigt sind.
 #1.11.2    Level: 2    Rolle: D/V
 Überprüfen Sie, ob der Generierungsprozess, die Parameter und die beabsichtigte Verwendung synthetischer Daten dokumentiert sind.
 #1.11.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass synthetische Daten vor der Verwendung im Training einer Risikobewertung auf Verzerrungen, Datenschutzverletzungen und Repräsentationsprobleme geprüft werden.
 #1.12.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Warnmeldungen für verdächtige Zugriffsereignisse erzeugt werden und zeitnah untersucht werden.
 #1.13.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob explizite Aufbewahrungsfristen für alle Trainingsdatensätze definiert sind.
 #1.13.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Datensätze am Ende ihres Lebenszyklus automatisch ablaufen, gelöscht werden oder auf Löschung geprüft werden.
 #1.13.3    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Aufbewahrungs- und Löschvorgänge protokolliert und auditierbar sind.
 #1.14.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Datenresidenz- und grenzüberschreitende Übertragungsanforderungen für alle Datensätze identifiziert und durchgesetzt werden.
 #1.14.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass sektorspezifische Vorschriften (z. B. Gesundheitswesen, Finanzen) bei der Datenverarbeitung identifiziert und berücksichtigt werden.
 #1.14.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob die Einhaltung relevanter Datenschutzgesetze (z. B. DSGVO, CCPA) dokumentiert und regelmäßig überprüft wird.
 #1.16.1    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Mechanismen vorhanden sind, um auf Anfragen betroffener Personen zu Auskunft, Berichtigung, Einschränkung der Verarbeitung oder Widerspruch zu reagieren.
 #1.16.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass Anfragen protokolliert, verfolgt und innerhalb der gesetzlich festgelegten Fristen erfüllt werden.
 #1.16.3    Level: 2    Rolle: D/V
 Überprüfen Sie, dass die Prozesse zu den Rechten der betroffenen Personen regelmäßig auf Wirksamkeit getestet und überprüft werden.
 #1.17.1    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass vor der Aktualisierung oder Ersetzung einer Datensatzversion eine Auswirkungsanalyse durchgeführt wird, die Modellleistung, Fairness und Compliance abdeckt.
 #1.17.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass die Ergebnisse der Auswirkungsanalyse dokumentiert und von relevanten Stakeholdern überprüft werden.
 #1.17.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Rollback-Pläne vorhanden sind, falls neue Versionen inakzeptable Risiken oder Regressionen einführen.
 #1.18.1    Level: 2    Rolle: D/V
 Verifizieren Sie, dass alle am Prozess der Datenannotation beteiligten Personen einer Hintergrundprüfung unterzogen wurden und in Datensicherheit sowie Datenschutz geschult sind.
 #1.18.2    Level: 2    Rolle: D/V
 Stellen Sie sicher, dass alle Annotatoren Geheimhaltungs- und Verschwiegenheitsvereinbarungen unterzeichnen.
 #1.18.3    Level: 2    Rolle: D/V
 Überprüfen Sie, ob Annotierungsplattformen Zugriffskontrollen durchsetzen und Insider-Bedrohungen überwachen.

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Anhang D: KI-gestützte sichere Codierungs-Governance und Verifikation

### Ziel

Dieses Kapitel definiert grundlegende organisatorische Kontrollen für den sicheren und effektiven Einsatz von KI-unterstützten Codierungstools während der Softwareentwicklung, um Sicherheit und Nachvollziehbarkeit über den SDLC hinweg zu gewährleisten.

---

### KI-gestützter sicherer Codierungs-Workflow

Integrieren Sie KI-Werkzeuge in den sicheren Software-Entwicklungslebenszyklus der Organisation (SSDLC), ohne die bestehenden Sicherheitsbarrieren zu schwächen.

 #AD.1.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein dokumentierter Workflow beschreibt, wann und wie KI-Werkzeuge Code erzeugen, refaktorisieren oder überprüfen dürfen.
 #AD.1.2    Level: 2    Rolle: D
 Überprüfen Sie, ob der Workflow jeder SSDLC-Phase zugeordnet ist (Design, Implementierung, Code-Review, Tests, Bereitstellung).
 #AD.1.3    Level: 3    Rolle: D/V
 Verifizieren Sie, dass Metriken (z. B. Verwundbarkeitsdichte, mean‑time‑to‑detect) bei von KI erzeugtem Code erhoben und mit Baselines verglichen werden, die ausschließlich menschlich sind.

---

### AD.2 KI-Tool-Qualifikation und Bedrohungsmodellierung

Stellen Sie sicher, dass KI-Programmierwerkzeuge hinsichtlich Sicherheitsfunktionen, Risiken und Auswirkungen der Lieferkette vor der Einführung bewertet werden.

 #AD.2.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass ein Bedrohungsmodell für jedes KI‑Tool Missbrauch, Modell‑Inversion, Datenleck und Abhängigkeitskettenrisiken identifiziert.
 #AD.2.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Toolbewertungen eine statische/dynamische Analyse aller lokalen Komponenten sowie eine Bewertung der SaaS-Endpunkte (TLS, Authentifizierung/Autorisierung, Protokollierung) umfassen.
 #AD.2.3    Level: 3    Rolle: D/V
 Vergewissern Sie sich, dass Evaluierungen einem anerkannten Rahmenwerk folgen und nach größeren Versionsänderungen erneut durchgeführt werden.

---

### AD.3 Sichere Prompt- und Kontextverwaltung

Verhindern Sie das Offenlegen von Geheimnissen, proprietärem Code und personenbezogenen Daten beim Erstellen von Prompts oder Kontexten für KI-Modelle.

 #AD.3.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob die schriftlichen Richtlinien das Senden von Geheimnissen, Anmeldeinformationen oder klassifizierten Daten in Eingabeaufforderungen verbieten.
 #AD.3.2    Level: 2    Rolle: D
 Überprüfen Sie, ob technische Kontrollen (client‑seitige Schwärzung, genehmigte Kontextfilter) automatisch sensible Artefakte entfernen.
 #AD.3.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Eingabeaufforderungen und Antworten tokenisiert sind, während der Übertragung und im Ruhezustand verschlüsselt werden, und dass Aufbewahrungsfristen der Datenklassifizierungsrichtlinie entsprechen.

---

### AD.4 Validierung von KI-generiertem Code

Erkennen und Beheben von Schwachstellen, die durch KI-Ausgaben eingeführt werden, bevor der Code zusammengeführt oder bereitgestellt wird.

 #AD.4.1    Level: 1    Rolle: D/V
 Stellen Sie sicher, dass KI-generierter Code stets einer menschlichen Codeüberprüfung unterzogen wird.
 #AD.4.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass automatische Scanner (SAST/IAST/DAST) bei jedem Pull Request ausgeführt werden, der AI-generierten Code enthält, und Merge-Vorgänge bei kritischen Befunden blockieren.
 #AD.4.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Differential-Fuzzing oder Eigenschaftsbasierte Tests sicherheitsrelevante Verhaltensweisen (z. B. Eingabevalidierung, Autorisierungslogik) nachweisen.

---

### AD.5 Erklärbarkeit & Rückverfolgbarkeit von Codevorschlägen

Auditoren und Entwickler erhalten Einblick, warum ein Vorschlag gemacht wurde und wie er sich entwickelt hat.

 #AD.5.1    Level: 1    Rolle: D/V
 Überprüfen Sie, ob Prompt-/Antwort-Paare mit Commit-IDs protokolliert werden.
 #AD.5.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass Entwickler Modellquellenangaben (Trainingsauszüge, Dokumentation) bereitstellen können, die eine Empfehlung unterstützen.
 #AD.5.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass Berichte zur Erklärbarkeit zusammen mit Designartefakten gespeichert werden und in Sicherheitsprüfungen referenziert werden, um die Prinzipien der Nachverfolgbarkeit gemäß ISO/IEC 42001 zu erfüllen.

---

### AD.6 Kontinuierliches Feedback und Modell Fein‑Tuning

Die Sicherheitsleistung des Modells im Laufe der Zeit verbessern und gleichzeitig negativen Drift verhindern.

 #AD.6.1    Level: 1    Rolle: D/V
 Überprüfen Sie, dass Entwickler unsichere oder nicht‑konforme Vorschläge kennzeichnen können, und dass diese Kennzeichnungen nachverfolgt werden.
 #AD.6.2    Level: 2    Rolle: D
 Stellen Sie sicher, dass aggregiertes Feedback die regelmäßige Fein‑Abstimmung oder Abruf‑ergänzte Generierung mit geprüften sicheren Codierungs‑Korpora unterstützt (z. B. OWASP Cheat Sheets).
 #AD.6.3    Level: 3    Rolle: D/V
 Überprüfen Sie, dass ein Closed‑Loop‑Evaluierungs‑Harness nach jeder Fein‑abstimmung Regressionstests durchführt; Sicherheitskennzahlen müssen die vorherigen Referenzwerte erfüllen oder übertreffen, bevor die Bereitstellung erfolgt.

---

#### Referenzen

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Anhang E: Beispielwerkzeuge und Frameworks

### Ziel

Dieses Kapitel bietet Beispiele für Werkzeuge und Frameworks, die die Umsetzung bzw. Erfüllung einer bestimmten AISVS-Anforderung unterstützen können. Diese sollten nicht als Empfehlungen oder Befürwortungen durch das AISVS-Team oder das OWASP GenAI Security Project angesehen werden.

---

### AE.1 Trainingsdaten-Governance und Bias-Management

Werkzeuge, die für Datenanalyse, Governance und Bias-Management eingesetzt werden.

 #AE.1.1    Abschnitt: 1.1
 Dateninventar-Tooling: Tools zur Verwaltung des Dateninventars wie...
 #AE.1.2    Abschnitt: 1.2
 Verschlüsselung während der Übertragung: TLS für HTTPS-basierte Anwendungen verwenden, mit Tools wie OpenSSL und Python.`ssl` Bibliothek.

---

### AE.2 Benutzereingabe-Validierung

Werkzeuge zur Verarbeitung und Validierung von Benutzereingaben.

 #AE.2.1    Abschnitt: 2.1
 Tools zur Abwehr von Prompt-Injektionen: Verwenden Sie Guardrail-Tooling wie NVIDIA's NeMo oder Guardrails AI.

---

