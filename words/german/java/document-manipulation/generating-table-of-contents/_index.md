---
title: Generieren eines Inhaltsverzeichnisses in Aspose.Words für Java
linktitle: Inhaltsverzeichnis erstellen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Inhaltsverzeichnisse (TOC) erstellen und anpassen. Erstellen Sie mühelos organisierte und professionelle Dokumente.
weight: 21
url: /de/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generieren eines Inhaltsverzeichnisses in Aspose.Words für Java


## Einführung in die Generierung eines Inhaltsverzeichnisses in Aspose.Words für Java

In diesem Tutorial führen wir Sie durch den Prozess der Generierung eines Inhaltsverzeichnisses (TOC) mit Aspose.Words für Java. Das Inhaltsverzeichnis ist eine wichtige Funktion zum Erstellen organisierter Dokumente. Wir zeigen Ihnen, wie Sie das Erscheinungsbild und Layout des Inhaltsverzeichnisses anpassen können.

## Voraussetzungen

Stellen Sie vor dem Beginn sicher, dass Aspose.Words für Java in Ihrem Java-Projekt installiert und eingerichtet ist.

## Schritt 1: Neues Dokument erstellen

Lassen Sie uns zunächst ein neues Dokument zum Arbeiten erstellen.

```java
Document doc = new Document();
```

## Schritt 2: Inhaltsverzeichnisse anpassen

Um das Erscheinungsbild Ihres Inhaltsverzeichnisses anzupassen, können Sie die damit verbundenen Stile ändern. In diesem Beispiel werden die Inhaltsverzeichniseinträge der ersten Ebene fett dargestellt.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Schritt 3: Fügen Sie Ihrem Dokument Inhalt hinzu

Sie können dem Dokument Ihren Inhalt hinzufügen. Dieser Inhalt wird zum Generieren des Inhaltsverzeichnisses verwendet.

## Schritt 4: Inhaltsverzeichnis generieren

Um das Inhaltsverzeichnis zu generieren, fügen Sie an der gewünschten Stelle in Ihrem Dokument ein Inhaltsverzeichnisfeld ein. Dieses Feld wird automatisch basierend auf den Überschriften und Formatvorlagen in Ihrem Dokument ausgefüllt.

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

Sie können auch die Tabstopps in Ihrem Inhaltsverzeichnis anpassen, um das Layout der Seitenzahlen zu steuern. So können Sie Tabstopps ändern:

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
        
        //Fügt einen neuen Tabulator an geänderter Position ein (z. B. 50 Einheiten weiter links).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Jetzt haben Sie in Ihrem Dokument ein individuelles Inhaltsverzeichnis mit angepassten Tabstopps zur Seitenzahlausrichtung.


## Abschluss

In diesem Tutorial haben wir untersucht, wie man mit Aspose.Words für Java, einer leistungsstarken Bibliothek für die Arbeit mit Word-Dokumenten, ein Inhaltsverzeichnis (TOC) erstellt. Ein gut strukturiertes Inhaltsverzeichnis ist für die Organisation und Navigation langer Dokumente unerlässlich, und Aspose.Words bietet die Tools zum mühelosen Erstellen und Anpassen von Inhaltsverzeichnissen.

## Häufig gestellte Fragen

### Wie ändere ich die Formatierung von Inhaltsverzeichniseinträgen?

 Sie können die den Inhaltsverzeichnisebenen zugeordneten Stile ändern mit`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, wobei X der TOC-Level ist.

### Wie kann ich meinem Inhaltsverzeichnis weitere Ebenen hinzufügen?

Um weitere Ebenen in Ihr Inhaltsverzeichnis aufzunehmen, können Sie das Inhaltsverzeichnisfeld ändern und die gewünschte Anzahl Ebenen angeben.

### Kann ich die Tabstopppositionen für bestimmte Inhaltsverzeichniseinträge ändern?

Ja, wie im obigen Codebeispiel gezeigt, können Sie die Tabstopppositionen für bestimmte Inhaltsverzeichniseinträge ändern, indem Sie die Absätze durchlaufen und die Tabstopps entsprechend ändern.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
