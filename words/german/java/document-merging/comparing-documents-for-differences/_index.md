---
"description": "Erfahren Sie, wie Sie Dokumente mit Aspose.Words in Java auf Unterschiede prüfen. Unsere Schritt-für-Schritt-Anleitung sorgt für präzises Dokumentenmanagement."
"linktitle": "Vergleichen von Dokumenten auf Unterschiede"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Vergleichen von Dokumenten auf Unterschiede"
"url": "/de/java/document-merging/comparing-documents-for-differences/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vergleichen von Dokumenten auf Unterschiede

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie jeden einzelnen Unterschied zwischen zwei Word-Dokumenten erkennen? Vielleicht überarbeiten Sie gerade ein Dokument oder versuchen, Änderungen eines Kollegen zu finden. Manuelle Vergleiche können mühsam und fehleranfällig sein, aber mit Aspose.Words für Java ist das ein Kinderspiel! Diese Bibliothek ermöglicht Ihnen, den Dokumentvergleich zu automatisieren, Revisionen hervorzuheben und Änderungen mühelos zusammenzuführen.

## Voraussetzungen

Bevor Sie mit dem Code beginnen, stellen Sie sicher, dass Sie Folgendes bereit haben:  
1. Auf Ihrem System ist das Java Development Kit (JDK) installiert.  
2. Aspose.Words für Java-Bibliothek. Sie können [Laden Sie es hier herunter](https://releases.aspose.com/words/java/).  
3. Eine Entwicklungsumgebung wie IntelliJ IDEA oder Eclipse.  
4. Grundlegende Kenntnisse der Java-Programmierung.  
5. Eine gültige Aspose-Lizenz. Falls Sie keine haben, besorgen Sie sich eine [vorläufige Lizenz hier](https://purchase.aspose.com/temporary-license/).

## Pakete importieren

Um Aspose.Words verwenden zu können, müssen Sie die erforderlichen Klassen importieren. Nachfolgend sind die erforderlichen Importe aufgeführt:

```java
import com.aspose.words.*;
import java.util.Date;
```

Stellen Sie sicher, dass diese Pakete korrekt zu Ihren Projektabhängigkeiten hinzugefügt werden.


In diesem Abschnitt unterteilen wir den Vorgang in einfache Schritte.


## Schritt 1: Richten Sie Ihre Dokumente ein

Zunächst benötigen Sie zwei Dokumente: eines mit dem Original und eines mit der bearbeiteten Version. So erstellen Sie sie:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

Dadurch werden zwei Dokumente mit grundlegendem Inhalt im Speicher erstellt. Sie können auch vorhandene Word-Dokumente laden mit `new Document("path/to/document.docx")`.


## Schritt 2: Auf vorhandene Revisionen prüfen

Revisionen in Word-Dokumenten stellen nachverfolgte Änderungen dar. Stellen Sie vor dem Vergleich sicher, dass keines der Dokumente bereits vorhandene Revisionen enthält:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Wenn Überarbeitungen vorhanden sind, möchten Sie diese möglicherweise akzeptieren oder ablehnen, bevor Sie fortfahren.


## Schritt 3: Vergleichen Sie die Dokumente

Verwenden Sie die `compare` Methode, um Unterschiede zu finden. Diese Methode vergleicht das Zieldokument (`doc2`) mit dem Quelldokument (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Hier:
- AuthorName ist der Name der Person, die die Änderungen vornimmt.
- Das Datum ist der Vergleichszeitstempel.


## Schritt 4: Prozessrevisionen

Nach dem Vergleich generiert Aspose.Words Revisionen im Quelldokument (`doc1`). Lassen Sie uns diese Revisionen analysieren:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Diese Schleife liefert detaillierte Informationen zu jeder Revision, beispielsweise die Art der Änderung und den betroffenen Text.


## Schritt 5: Alle Revisionen akzeptieren

Wenn Sie das Quelldokument (`doc1`), um dem Zieldokument zu entsprechen (`doc2`), alle Revisionen akzeptieren:

```java
doc1.getRevisions().acceptAll();
```

Dieses Update `doc1` um alle Änderungen widerzuspiegeln, die in `doc2`.


## Schritt 6: Speichern Sie das aktualisierte Dokument

Speichern Sie abschließend das aktualisierte Dokument auf der Festplatte:

```java
doc1.save("Document.Compare.docx");
```

Um die Änderungen zu bestätigen, laden Sie das Dokument neu und stellen Sie sicher, dass keine Revisionen mehr vorhanden sind:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Schritt 7: Überprüfen der Dokumentgleichheit

Um sicherzustellen, dass die Dokumente identisch sind, vergleichen Sie deren Text:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Wenn die Texte übereinstimmen, herzlichen Glückwunsch – Sie haben die Dokumente erfolgreich verglichen und synchronisiert!


## Abschluss

Dank Aspose.Words für Java ist Dokumentenvergleich kein lästiges Unterfangen mehr. Mit nur wenigen Codezeilen können Sie Unterschiede identifizieren, Revisionen bearbeiten und die Dokumentenkonsistenz sicherstellen. Ob Sie ein kollaboratives Schreibprojekt verwalten oder juristische Dokumente prüfen – diese Funktion ist bahnbrechend.

## Häufig gestellte Fragen

### Kann ich Dokumente mit Bildern und Tabellen vergleichen?  
Ja, Aspose.Words unterstützt den Vergleich komplexer Dokumente, einschließlich solcher mit Bildern, Tabellen und Formatierungen.

### Benötige ich eine Lizenz, um diese Funktion zu nutzen?  
Ja, für die volle Funktionalität ist eine Lizenz erforderlich. Holen Sie sich eine [vorläufige Lizenz hier](https://purchase.aspose.com/temporary-license/).

### Was passiert, wenn bereits Revisionen vorhanden sind?  
Um Konflikte zu vermeiden, müssen Sie sie vor dem Vergleichen von Dokumenten akzeptieren oder ablehnen.

### Kann ich die Überarbeitungen im Dokument hervorheben?  
Ja, mit Aspose.Words können Sie die Anzeige von Revisionen anpassen, z. B. durch Hervorheben von Änderungen.

### Ist diese Funktion in anderen Programmiersprachen verfügbar?  
Ja, Aspose.Words unterstützt mehrere Sprachen, darunter .NET und Python.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}