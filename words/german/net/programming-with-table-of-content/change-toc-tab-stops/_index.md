---
"description": "Erfahren Sie, wie Sie Tabstopps im Inhaltsverzeichnis in Word-Dokumenten mit Aspose.Words für .NET ändern. Diese Schritt-für-Schritt-Anleitung hilft Ihnen beim Erstellen eines professionell aussehenden Inhaltsverzeichnisses."
"linktitle": "Toc-Tabstopps im Word-Dokument ändern"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Toc-Tabstopps im Word-Dokument ändern"
"url": "/de/net/programming-with-table-of-content/change-toc-tab-stops/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Toc-Tabstopps im Word-Dokument ändern

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie das Inhaltsverzeichnis (TOC) in Ihren Word-Dokumenten aufpeppen können? Vielleicht möchten Sie die Tabstopps perfekt ausrichten, um Ihrem Dokument einen professionellen Touch zu verleihen. Hier sind Sie richtig! Heute zeigen wir Ihnen ausführlich, wie Sie die Tabstopps im Inhaltsverzeichnis mit Aspose.Words für .NET ändern können. Bleiben Sie dran – ich verspreche Ihnen, dass Sie mit dem nötigen Know-how Ihr Inhaltsverzeichnis elegant und ordentlich gestalten können.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Sie können [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede C#-kompatible IDE.
3. Ein Word-Dokument: Insbesondere eines, das ein Inhaltsverzeichnis enthält.

Alles klar? Super! Los geht's.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren. Das ist so, als würden Sie Ihre Werkzeuge packen, bevor Sie ein Projekt starten.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Lassen Sie uns diesen Vorgang in einfache, verständliche Schritte unterteilen. Wir gehen das Laden des Dokuments durch, ändern die Tabstopps im Inhaltsverzeichnis und speichern das aktualisierte Dokument.

## Schritt 1: Laden Sie das Dokument

Warum? Wir müssen auf das Word-Dokument zugreifen, das das zu ändernde Inhaltsverzeichnis enthält.

Wie? Hier ist ein einfacher Codeausschnitt für den Einstieg:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Laden Sie das Dokument mit dem Inhaltsverzeichnis
Document doc = new Document(dataDir + "Table of contents.docx");
```

Stellen Sie sich vor, Ihr Dokument ist wie ein Kuchen, dem wir nun etwas Zuckerguss hinzufügen. Der erste Schritt besteht darin, den Kuchen aus der Schachtel zu holen.

## Schritt 2: Identifizieren Sie die Inhaltsverzeichnisabsätze

Warum? Wir müssen die Absätze genau bestimmen, aus denen das Inhaltsverzeichnis besteht. 

Wie? Gehen Sie die Absätze durch und überprüfen Sie deren Stil:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Inhaltsverzeichnisabsatz gefunden
    }
}
```

Stellen Sie sich vor, Sie durchsuchen eine Menschenmenge nach Ihren Freunden. Hier suchen wir nach Absätzen, die als Inhaltsverzeichniseinträge formatiert sind.

## Schritt 3: Ändern Sie die Tabstopps

Warum? Hier geschieht die Magie. Durch das Ändern von Tabstopps wird Ihr Inhaltsverzeichnis übersichtlicher.

Wie? Entfernen Sie den vorhandenen Tabstopp und fügen Sie an einer geänderten Position einen neuen hinzu:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Es ist, als würden Sie die Möbel in Ihrem Wohnzimmer so lange verstellen, bis sie sich perfekt anfühlen. Wir optimieren diese Tabstopps für die perfekte Passform.

## Schritt 4: Speichern des geänderten Dokuments

Warum? Um sicherzustellen, dass Ihre gesamte harte Arbeit gespeichert und angezeigt oder geteilt werden kann.

Wie? Speichern Sie das Dokument unter einem neuen Namen, um das Original zu erhalten:

```csharp
// Speichern des geänderten Dokuments
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

Und voilà! Ihr Inhaltsverzeichnis hat jetzt die Tabstopps genau dort, wo Sie sie haben möchten.

## Abschluss

Das Ändern von Inhaltsverzeichnis-Tabstopps in einem Word-Dokument mit Aspose.Words für .NET ist einfach, sobald Sie es aufschlüsseln. Laden Sie Ihr Dokument, identifizieren Sie die Inhaltsverzeichnis-Absätze, ändern Sie die Tabstopps und speichern Sie das Dokument, um ein ansprechendes und professionelles Erscheinungsbild zu erzielen. Übung macht den Meister. Experimentieren Sie also mit verschiedenen Tabstopp-Positionen, um genau das gewünschte Layout zu erhalten.

## Häufig gestellte Fragen

### Kann ich Tabstopps für verschiedene Inhaltsverzeichnisebenen separat ändern?
Ja, das ist möglich! Überprüfen Sie einfach die einzelnen TOC-Ebenen (Toc1, Toc2 usw.) und passen Sie sie entsprechend an.

### Was ist, wenn mein Dokument mehrere Inhaltsverzeichnisse hat?
Der Code sucht nach allen Absätzen im Inhaltsverzeichnisstil und ändert daher alle im Dokument vorhandenen Inhaltsverzeichnisse.

### Ist es möglich, in einem Inhaltsverzeichniseintrag mehrere Tabstopps hinzuzufügen?
Absolut! Sie können so viele Tabstopps wie nötig hinzufügen, indem Sie die `para.ParagraphFormat.TabStops` Sammlung.

### Kann ich die Tabulatorausrichtung und den Füllstil ändern?
Ja, Sie können beim Hinzufügen eines neuen Tabstopps unterschiedliche Ausrichtungen und Füllzeichenstile angeben.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
Ja, Sie benötigen eine gültige Lizenz, um Aspose.Words für .NET über den Testzeitraum hinaus zu nutzen. Sie erhalten eine [vorläufige Lizenz](https://purchase.aspose.com/tempoderary-license/) or [kauf eins](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}