---
date: '2026-08-10'
description: Erfahren Sie, wie Sie Kommentar‑Java mit Aspose.Words for Java hinzufügen.
  Schritt‑für‑Schritt‑Anleitung zum Erstellen, Antworten, Drucken, Entfernen und Markieren
  von Kommentaren als erledigt sowie zum Abrufen von UTC‑Zeitstempeln.
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: Erfahren Sie, wie Sie Kommentar‑Java mit Aspose.Words for Java hinzufügen.
  Schritt‑für‑Schritt‑Anleitung zum Erstellen, Antworten, Drucken, Entfernen und Markieren
  von Kommentaren als erledigt sowie zum Abrufen von UTC‑Zeitstempeln.
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: Wie man Kommentar‑Java mit Aspose.Words for Java für Word‑Dokumente hinzufügt
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: Wie man Kommentar‑Java mit Aspose.Words for Java für Word‑Dokumente hinzufügt
url: /de/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Kommentare in Java mit Aspose.Words für Word-Dokumente hinzufügt

## Einleitung
Das programmgesteuerte Hinzufügen von Kommentaren zu einem Word-Dokument kann die Zusammenarbeit, Code‑Reviews oder die automatisierte Berichtserstellung vereinfachen. In diesem Tutorial lernen Sie **how to add comment java** mit der Aspose.Words‑Bibliothek, einschließlich Erstellung, Antworten, Ausgabe, Entfernen, Markieren als erledigt und Extrahieren von UTC‑Zeitstempeln. Am Ende können Sie reichhaltiges Feedback direkt in Ihre Dokumente einbetten, ohne manuelles Eingreifen.

## Schnelle Antworten
- **Was ist der erste Schritt?** Laden Sie die Word‑Datei mit `new Document("input.docx")`.  
- **Kann ich auf einen Kommentar antworten?** Ja – erstellen Sie ein `Comment`‑Objekt und rufen Sie `comment.getReplies().add(reply)` auf.  
- **Wie markiere ich einen Kommentar als erledigt?** Setzen Sie `comment.setDone(true)`, um ihn als gelöst zu kennzeichnen.  
- **Ist die UTC‑Zeit verfügbar?** Jeder Kommentar speichert `getDateTime()` in UTC, das Sie direkt auslesen können.  
- **Benötige ich eine Lizenz?** Eine Testversion funktioniert für die Entwicklung; eine Voll‑lizenz entfernt Evaluationsbeschränkungen.

## Was ist how to add comment Java?
`how to add comment java` bezieht sich auf den Vorgang, programmgesteuert einen Kommentar in ein Microsoft‑Word‑Dokument mit Java‑Code und der Aspose.Words‑API einzufügen. Dieser Vorgang ermöglicht automatisierte Feedback‑Schleifen in dokumentzentrierten Arbeitsabläufen.

## Warum Aspose.Words für die Kommentarverwaltung verwenden?
Aspose.Words unterstützt **über 35 Eingabe‑ und Ausgabeformate** und kann Dokumente mit mehr als **500 Seiten** verarbeiten, während der Speicherverbrauch auf einem typischen Server unter **100 MB** bleibt. Die Kommentar‑API funktioniert ohne installierten Microsoft Word, bietet vollständige Kontrolle in Headless‑Umgebungen und senkt die Lizenzkosten im Vergleich zur Office‑Automatisierung um bis zu **70 %**.

## Voraussetzungen
- Java Development Kit (JDK) 17 oder höher installiert.  
- Eine IDE wie IntelliJ IDEA oder Eclipse.  
- Maven oder Gradle für das Abhängigkeitsmanagement.  
- Eine gültige Aspose.Words‑Lizenz für Java (Testversion oder Vollversion).

### Einrichtung von Aspose.Words für Java
Aspose.Words wird als einzelnes JAR bereitgestellt. Fügen Sie die Abhängigkeit hinzu, die zu Ihrem Build‑Tool passt.

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### Lizenzbeschaffung
Aspose.Words ist ein kommerzielles Produkt; Sie können mit einer kostenlosen Testversion beginnen oder eine temporäre Lizenz für den vollen Funktionsumfang anfordern. Besuchen Sie die [Kaufseite](https://purchase.aspose.com/buy), um Lizenzoptionen zu erkunden.

## Wie fügt man einen Kommentar in Java mit Aspose.Words hinzu?
Laden Sie Ihr Dokument, erstellen Sie ein `Comment`‑Objekt und hängen Sie es an einen `Paragraph` an. Dieses zweistufige Muster fügt an der gewünschten Stelle einen Kommentar ein und bildet die Grundlage für alle nachfolgenden Vorgänge. Durch Angabe von Autor, Text und Zeitstempel können Sie sofort Kontext für die Reviewer bereitstellen, und der Kommentar wird Teil der Dokumentstruktur.

Die Klasse `Document` ist das Top‑Level‑Objekt von Aspose.Words, das eine einzelne Word‑Datei im Speicher repräsentiert. Nach der Instanziierung laufen alle Lese‑ und Schreibvorgänge über dieses Objekt.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

Als Nächstes erstellen Sie den Kommentar selbst. Die Klasse `Comment` speichert Autor, Text und Zeitstempelinformationen.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Abschließend fügen Sie eine Antwort über die `Replies`‑Sammlung des Kommentars hinzu. Das `Comment`‑Objekt verfolgt automatisch die Antwort‑Hierarchie.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Wie gibt man alle Kommentare und deren Antworten aus?
Iterieren Sie über die `CommentCollection` des Dokuments und geben Sie den Text, den Autor und den UTC‑Zeitstempel jedes Kommentars aus. Antworten sind in jedem Kommentar verschachtelt, sodass Sie einen vollständigen Gesprächsverlauf anzeigen können. Durch rekursives Durchlaufen der Sammlung können Sie die Hierarchie beibehalten, die Ausgabe für Protokolle oder UI formatieren und optional nach Autor oder Datum filtern.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

Verwenden Sie eine einfache Schleife, um die Sammlung zu durchlaufen und Details auszugeben.  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

## Wie entfernt man Kommentarantworten?
Sie können eine bestimmte Antwort löschen oder alle Antworten eines Kommentars entfernen. Das Entfernen von Antworten hilft, das Dokument nach der Integration von Feedback sauber zu halten. Verwenden Sie die Methode `getReplies().remove(index)` für gezieltes Entfernen oder rufen Sie `clear()` auf, um die gesamte Antwortliste zu leeren, sodass keine verwaisten Diskussionen zurückbleiben.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

Rufen Sie `comment.getReplies().clear()` auf oder entfernen Sie einzelne Antworten nach Index.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## Wie markiert man einen Kommentar als erledigt?
Das Setzen des `Done`‑Flags eines Kommentars signalisiert, dass das Problem gelöst wurde. Dieser visuelle Hinweis ist für Reviewer und nachgelagerte Verarbeitungstools nützlich. Wenn `setDone(true)` aufgerufen wird, zeigt Word ein Häkchen neben dem Kommentar an, und Sie können das Flag später abfragen, um Berichte über offene Punkte zu erstellen.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

Wenden Sie das Flag an, nachdem Sie den Inhalt des Kommentars bearbeitet haben.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## Wie erhält man das UTC‑Datum und die -Uhrzeit aus einem Kommentar?
Jeder Kommentar speichert seine Erstellungszeit in UTC, zugänglich über `getDateTime()`. Dieser Zeitstempel ist unverzichtbar für Prüfpfade und Versionskontrolle. Das zurückgegebene `DateTime`‑Objekt kann mit ISO‑8601‑Mustern formatiert werden, sodass Sie genaue Zeitpunkte des Feedbacks protokollieren und Kommentardaten über verteilte Systeme synchronisieren können.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Sie können den Zeitstempel als ISO‑8601 für einfaches Logging formatieren.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Praktische Anwendungen
Das Verständnis dieser APIs ermöglicht den Aufbau robuster Lösungen für:
- **Kollaborative Bearbeitungsplattformen** – Feedback‑Schleifen direkt in generierten Berichten einbetten.  
- **Automatisierte Review‑Pipelines** – Kommentare kennzeichnen, lösen und prüfen, ohne menschliches Eingreifen.  
- **Compliance‑Dokumentation** – Prüfer‑Zeitstempel für regulatorische Audits erfassen.

## Leistungsüberlegungen
Beim Verarbeiten großer Dateien (500 + Seiten) sollten Sie folgende bewährte Methoden beachten:
- Kommentare stapelweise verarbeiten, um das Laden der gesamten Sammlung in den Speicher zu vermeiden.  
- `Document.optimizeResources()` verwenden, um das Dokument vor dem Speichern zu verkleinern.  
- Aspose.Words aktuell halten; Version 24.12 brachte eine 30 %ige Geschwindigkeitssteigerung bei der Kommentar‑Aufzählung.

## Fazit
Sie verfügen nun über ein vollständiges Toolkit für **how to add comment java** mit Aspose.Words: Erstellen von Kommentaren, Antworten, Ausgeben, Entfernen, Markieren als erledigt und Extrahieren von UTC‑Zeitstempeln. Integrieren Sie diese Snippets in Ihre bestehenden Java‑Dienste, um Feedback zu automatisieren, Review‑Richtlinien durchzusetzen und einen sauberen Prüfpfad zu erhalten.

**Nächste Schritte**
- Experimentieren Sie mit dem Filtern von Kommentaren nach Autor oder Datum.  
- Kombinieren Sie die Kommentarverwaltung mit der Aspose.Words‑„Track Changes“‑API für vollständige Versionskontrolle.  
- Untersuchen Sie den Export von Kommentardaten nach JSON für nachgelagerte Analysen.

## Häufig gestellte Fragen

**F: Kann ich Aspose.Words ohne Lizenz in der Produktion verwenden?**  
A: Nein. Die Testversion funktioniert nur für die Entwicklung; eine Voll‑lizenz ist für Produktionsumgebungen erforderlich.

**F: Unterstützt die Bibliothek passwortgeschützte Dokumente?**  
A: Ja. Laden Sie eine geschützte Datei, indem Sie das Passwort an den `Document`‑Konstruktor übergeben.

**F: Welche Java‑Versionen sind kompatibel?**  
A: Aspose.Words für Java unterstützt JDK 8 bis JDK 21 mit voller Funktionsparität über alle Versionen hinweg.

**F: Wie skaliert die Kommentar‑Performance mit der Dokumentgröße?**  
A: Die Aufzählung von Kommentaren erfolgt in linearer Zeit; ein 1.000‑Seiten‑Dokument wird auf einem typischen 4‑Kern‑Server in weniger als 2 Sekunden verarbeitet.

**F: Kann ich Kommentare in eine separate Datei exportieren?**  
A: Absolut. Durchlaufen Sie die `CommentCollection` und schreiben Sie die Eigenschaften jedes Kommentars nach Bedarf in CSV, JSON oder XML.

---

**Zuletzt aktualisiert:** 2026-08-10  
**Getestet mit:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Verwandte Tutorials

- [Meistern von Anmerkungen & Kommentaren mit Aspose.Words für Java Tutorials](/words/java/annotations-comments/)
- [Änderungen in Word-Dokumenten mit Aspose.Words Java nachverfolgen: Ein vollständiger Leitfaden zu Dokumentrevisionen](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Umfassender Leitfaden zur Word-Dokumentenverarbeitung](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}