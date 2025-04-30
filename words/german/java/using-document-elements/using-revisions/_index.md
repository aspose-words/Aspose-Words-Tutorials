---
"description": "Lernen Sie, Aspose.Words für die Java-Revision effizient zu nutzen. Schritt-für-Schritt-Anleitung für Entwickler. Optimieren Sie Ihr Dokumentenmanagement."
"linktitle": "Verwenden von Revisionen"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Verwenden von Revisionen in Aspose.Words für Java"
"url": "/de/java/using-document-elements/using-revisions/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Revisionen in Aspose.Words für Java


Wenn Sie als Java-Entwickler mit Dokumenten arbeiten und Revisionskontrollen implementieren möchten, bietet Aspose.Words für Java leistungsstarke Tools zur effektiven Verwaltung von Revisionen. In diesem Tutorial führen wir Sie Schritt für Schritt durch die Verwendung der Revision in Aspose.Words für Java. 

## 1. Einführung in Aspose.Words für Java

Aspose.Words für Java ist eine robuste Java-API, mit der Sie Word-Dokumente erstellen, ändern und bearbeiten können, ohne Microsoft Word zu benötigen. Dies ist besonders nützlich, wenn Sie Ihre Dokumente überarbeiten müssen.

## 2. Einrichten Ihrer Entwicklungsumgebung

Bevor wir uns mit Aspose.Words für Java befassen, müssen Sie Ihre Entwicklungsumgebung einrichten. Stellen Sie sicher, dass Sie die erforderlichen Java-Entwicklungstools und die Aspose.Words für Java-Bibliothek installiert haben.

## 3. Erstellen eines neuen Dokuments

Beginnen wir mit der Erstellung eines neuen Word-Dokuments mit Aspose.Words für Java. So geht's:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. Hinzufügen von Inhalten zum Dokument

Da Sie nun ein leeres Dokument haben, können Sie Inhalt hinzufügen. In diesem Beispiel fügen wir drei Absätze hinzu:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. Starten der Revisionsverfolgung

Um Revisionen in Ihrem Dokument zu verfolgen, können Sie den folgenden Code verwenden:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. Überarbeitungen vornehmen

Nehmen wir eine Überarbeitung vor, indem wir einen weiteren Absatz hinzufügen:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. Akzeptieren und Ablehnen von Überarbeitungen

Mit Aspose.Words für Java können Sie Änderungen an Ihrem Dokument akzeptieren oder ablehnen. Änderungen können nach der Dokumenterstellung einfach in Microsoft Word verwaltet werden.

## 8. Beenden der Revisionsverfolgung

Um die Revisionsverfolgung zu beenden, verwenden Sie den folgenden Code:

```java
doc.stopTrackRevisions();
```

## 9. Speichern des Dokuments

Speichern Sie abschließend Ihr Dokument:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. Fazit

In diesem Tutorial haben wir die Grundlagen der Revisionsfunktion in Aspose.Words für Java behandelt. Sie haben gelernt, wie Sie ein Dokument erstellen, Inhalte hinzufügen, die Revisionsverfolgung starten und stoppen und Ihr Dokument speichern.

Jetzt verfügen Sie über die Tools, die Sie benötigen, um Revisionen in Ihren Java-Anwendungen mit Aspose.Words für Java effektiv zu verwalten.

## Vollständiger Quellcode
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// Fügen Sie dem ersten Absatz Text hinzu und fügen Sie dann zwei weitere Absätze hinzu.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// Wir haben drei Absätze, von denen keiner als irgendeine Art von Überarbeitung registriert ist
// Wenn wir beim Verfolgen von Revisionen Inhalte im Dokument hinzufügen/entfernen,
// Sie werden als solche im Dokument angezeigt und können akzeptiert/abgelehnt werden.
doc.startTrackRevisions("John Doe", new Date());
// Dieser Absatz ist eine Revision und das entsprechende Flag „IsInsertRevision“ ist gesetzt.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// Holen Sie sich die Absatzsammlung des Dokuments und entfernen Sie einen Absatz.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// Da wir Revisionen verfolgen, ist der Absatz noch im Dokument vorhanden und hat den Wert "IsDeleteRevision"
// und wird als Revision in Microsoft Word angezeigt, bis wir alle Revisionen akzeptieren oder ablehnen.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// Der Absatz zum Löschen der Revision wird entfernt, sobald wir die Änderungen akzeptieren.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //war Is.Empty
// Wenn Sie die Revisionsverfolgung stoppen, wird dieser Text als normaler Text angezeigt.
// Revisionen werden nicht gezählt, wenn das Dokument geändert wird.
doc.stopTrackRevisions();
// Speichern Sie das Dokument.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## FAQs

### 1. Kann ich Aspose.Words für Java mit anderen Programmiersprachen verwenden?

Nein, Aspose.Words für Java ist speziell für die Java-Entwicklung konzipiert.

### 2. Ist Aspose.Words für Java mit allen Versionen von Microsoft Word kompatibel?

Ja, Aspose.Words für Java ist so konzipiert, dass es mit verschiedenen Versionen von Microsoft Word kompatibel ist.

### 3. Kann ich Überarbeitungen in vorhandenen Word-Dokumenten verfolgen?

Ja, Sie können Aspose.Words für Java verwenden, um Revisionen in vorhandenen Word-Dokumenten zu verfolgen.

### 4. Gibt es Lizenzanforderungen für die Verwendung von Aspose.Words für Java?

Ja, Sie benötigen eine Lizenz, um Aspose.Words für Java in Ihren Projekten zu verwenden. Sie können [Erhalten Sie hier Zugriff auf eine Lizenz](https://purchase.aspose.com/buy).

### 5. Wo finde ich Unterstützung für Aspose.Words für Java?

Bei Fragen oder Problemen können Sie die [Aspose.Words für Java-Supportforum](https://forum.aspose.com/).

Beginnen Sie noch heute mit Aspose.Words für Java und optimieren Sie Ihre Dokumentenverwaltungsprozesse.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}