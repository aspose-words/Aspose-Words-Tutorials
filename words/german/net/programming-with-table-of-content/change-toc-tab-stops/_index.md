---
title: Inhaltsverzeichnis-Tabstopps im Word-Dokument ändern
linktitle: Inhaltsverzeichnis-Tabstopps im Word-Dokument ändern
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Inhaltsverzeichnis-Tabstopps in Word-Dokumenten ändern. Diese Schritt-für-Schritt-Anleitung hilft Ihnen beim Erstellen eines professionell aussehenden Inhaltsverzeichnisses.
weight: 10
url: /de/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhaltsverzeichnis-Tabstopps im Word-Dokument ändern

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie das Inhaltsverzeichnis (TOC) in Ihren Word-Dokumenten aufpeppen können? Vielleicht möchten Sie, dass die Tabstopps perfekt ausgerichtet sind, um dem Dokument einen professionellen Touch zu verleihen. Dann sind Sie hier richtig! Heute tauchen wir tief in die Frage ein, wie Sie die Tabstopps im Inhaltsverzeichnis mit Aspose.Words für .NET ändern können. Bleiben Sie dran, und ich verspreche Ihnen, dass Sie mit dem gesamten Know-how, das Sie brauchen, um Ihr Inhaltsverzeichnis schick und ordentlich aussehen zu lassen, abschließen können.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede C#-kompatible IDE.
3. Ein Word-Dokument: Insbesondere eines, das ein Inhaltsverzeichnis enthält.

Alles klar? Super! Los geht‘s.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Das ist so, als würden Sie Ihre Werkzeuge packen, bevor Sie ein Projekt starten.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Lassen Sie uns diesen Vorgang in einfache, leicht verständliche Schritte unterteilen. Wir gehen das Laden des Dokuments durch, ändern die Tabulatorstopps im Inhaltsverzeichnis und speichern das aktualisierte Dokument.

## Schritt 1: Dokument laden

Warum? Wir müssen auf das Word-Dokument zugreifen, das das Inhaltsverzeichnis enthält, das wir ändern möchten.

Wie? Hier ist ein einfacher Codeausschnitt, der Ihnen den Einstieg erleichtert:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Laden Sie das Dokument mit dem Inhaltsverzeichnis
Document doc = new Document(dataDir + "Table of contents.docx");
```

Stellen Sie sich vor, Ihr Dokument ist wie ein Kuchen und wir wollen ihn mit etwas Zuckerguss verzieren. Der erste Schritt besteht darin, den Kuchen aus der Schachtel zu holen.

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

Stellen Sie es sich so vor, als würden Sie eine Menschenmenge absuchen, um Ihre Freunde zu finden. Hier suchen wir nach Absätzen, die als Inhaltsverzeichniseinträge formatiert sind.

## Schritt 3: Ändern Sie die Tabulatoren

Warum? Hier geschieht die Magie. Durch das Ändern von Tabulatoren sieht Ihr Inhaltsverzeichnis übersichtlicher aus.

Wie? Den vorhandenen Tabstopp entfernen und an geänderter Position einen neuen hinzufügen:

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

Es ist, als würden Sie die Möbel in Ihrem Wohnzimmer so lange verschieben, bis sie sich richtig anfühlen. Wir optimieren diese Tabstopps, bis sie perfekt sind.

## Schritt 4: Speichern Sie das geänderte Dokument

Warum? Um sicherzustellen, dass Ihre gesamte harte Arbeit gespeichert und angezeigt oder freigegeben werden kann.

Wie? Speichern Sie das Dokument unter einem neuen Namen, damit das Original erhalten bleibt:

```csharp
// Speichern des geänderten Dokuments
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

Und voilà! Ihr Inhaltsverzeichnis hat jetzt die Tabstopps genau dort, wo Sie sie haben möchten.

## Abschluss

Das Ändern von Inhaltsverzeichnis-Tabstopps in einem Word-Dokument mit Aspose.Words für .NET ist unkompliziert, wenn man es einmal aufschlüsselt. Indem Sie Ihr Dokument laden, die Inhaltsverzeichnis-Absätze identifizieren, die Tabstopps ändern und das Dokument speichern, können Sie ein elegantes und professionelles Erscheinungsbild erzielen. Denken Sie daran: Übung macht den Meister. Experimentieren Sie also weiter mit verschiedenen Tabstopppositionen, um genau das gewünschte Layout zu erhalten.

## Häufig gestellte Fragen

### Kann ich Tabstopps für verschiedene Inhaltsverzeichnisebenen separat ändern?
Ja, das können Sie! Überprüfen Sie einfach die einzelnen TOC-Ebenen (TOC1, TOC2 usw.) und passen Sie sie entsprechend an.

### Was ist, wenn mein Dokument mehrere Inhaltsverzeichnisse hat?
Der Code sucht nach allen Absätzen im Inhaltsverzeichnisstil und ändert daher alle im Dokument vorhandenen Inhaltsverzeichnisse.

### Ist es möglich, in einen Inhaltsverzeichniseintrag mehrere Tabstopps einzufügen?
 Auf jeden Fall! Sie können so viele Tabstopps hinzufügen wie nötig, indem Sie die`para.ParagraphFormat.TabStops` Sammlung.

### Kann ich die Tabulatorausrichtung und den Füllstil ändern?
Ja, Sie können beim Hinzufügen eines neuen Tabulatorstopps unterschiedliche Ausrichtungen und Füllzeichenstile angeben.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, Sie benötigen eine gültige Lizenz, um Aspose.Words für .NET über den Testzeitraum hinaus zu verwenden. Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) oder[kauf eins](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
