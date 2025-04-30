---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für Java Inhaltsverzeichnisse erstellen und anpassen. Erstellen Sie mühelos organisierte und professionelle Dokumente."
"linktitle": "Inhaltsverzeichnis erstellen"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Generieren eines Inhaltsverzeichnisses in Aspose.Words für Java"
"url": "/de/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generieren eines Inhaltsverzeichnisses in Aspose.Words für Java


## Einführung in die Generierung eines Inhaltsverzeichnisses in Aspose.Words für Java

In diesem Tutorial führen wir Sie durch die Erstellung eines Inhaltsverzeichnisses (TOC) mit Aspose.Words für Java. Das TOC ist ein wichtiges Feature für die Erstellung strukturierter Dokumente. Wir zeigen Ihnen, wie Sie das Erscheinungsbild und Layout des TOC anpassen.

## Voraussetzungen

Stellen Sie vor dem Beginn sicher, dass Aspose.Words für Java in Ihrem Java-Projekt installiert und eingerichtet ist.

## Schritt 1: Erstellen Sie ein neues Dokument

Lassen Sie uns zunächst ein neues Dokument zum Arbeiten erstellen.

```java
Document doc = new Document();
```

## Schritt 2: Inhaltsverzeichnisse anpassen

Um das Erscheinungsbild Ihres Inhaltsverzeichnisses anzupassen, können Sie die zugehörigen Stile ändern. In diesem Beispiel werden die Inhaltsverzeichniseinträge der ersten Ebene fett dargestellt.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Schritt 3: Fügen Sie Ihrem Dokument Inhalt hinzu

Sie können dem Dokument Ihren Inhalt hinzufügen. Dieser Inhalt wird zur Generierung des Inhaltsverzeichnisses verwendet.

## Schritt 4: Generieren Sie das Inhaltsverzeichnis

Um das Inhaltsverzeichnis zu erstellen, fügen Sie an der gewünschten Stelle in Ihrem Dokument ein Inhaltsverzeichnisfeld ein. Dieses Feld wird automatisch anhand der Überschriften und Formatvorlagen Ihres Dokuments ausgefüllt.

```java
// Fügen Sie an der gewünschten Stelle in Ihrem Dokument ein Inhaltsverzeichnisfeld ein.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie abschließend das Dokument mit dem Inhaltsverzeichnis.

```java
doc.save("your_output_path_here");
```

## Anpassen von Tabstopps im Inhaltsverzeichnis

Sie können die Tabulatoren im Inhaltsverzeichnis anpassen, um das Layout der Seitenzahlen zu steuern. So ändern Sie Tabulatoren:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Holen Sie sich den ersten in diesem Absatz verwendeten Tabulator, der die Seitenzahlen ausrichtet.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Entfernen Sie die alte Lasche.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Fügen Sie einen neuen Tabulator an einer geänderten Position ein (z. B. 50 Einheiten nach links).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Jetzt haben Sie in Ihrem Dokument ein benutzerdefiniertes Inhaltsverzeichnis mit angepassten Tabstopps zur Seitenzahlausrichtung.


## Abschluss

In diesem Tutorial haben wir gezeigt, wie man mit Aspose.Words für Java, einer leistungsstarken Bibliothek für die Arbeit mit Word-Dokumenten, ein Inhaltsverzeichnis (TOC) erstellt. Ein gut strukturiertes Inhaltsverzeichnis ist für die Organisation und Navigation umfangreicher Dokumente unerlässlich. Aspose.Words bietet die Tools zum mühelosen Erstellen und Anpassen von Inhaltsverzeichnissen.

## Häufig gestellte Fragen

### Wie ändere ich die Formatierung von Inhaltsverzeichniseinträgen?

Sie können die Stile, die den Inhaltsverzeichnisebenen zugeordnet sind, ändern, indem Sie `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, wobei X der TOC-Level ist.

### Wie kann ich meinem Inhaltsverzeichnis weitere Ebenen hinzufügen?

Um mehr Ebenen in Ihr Inhaltsverzeichnis aufzunehmen, können Sie das Inhaltsverzeichnisfeld ändern und die gewünschte Anzahl von Ebenen angeben.

### Kann ich die Tabstopppositionen für bestimmte Inhaltsverzeichniseinträge ändern?

Ja, wie im obigen Codebeispiel gezeigt, können Sie die Tabstopppositionen für bestimmte Inhaltsverzeichniseinträge ändern, indem Sie die Absätze durchlaufen und die Tabstopps entsprechend ändern.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}