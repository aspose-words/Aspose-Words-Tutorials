---
title: Tabelle und Zelle mit unterschiedlichen Rändern formatieren
linktitle: Tabelle und Zelle mit unterschiedlichen Rändern formatieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Tabellen und Zellen mit unterschiedlichen Rändern formatieren. Verbessern Sie Ihre Word-Dokumente mit benutzerdefinierten Tabellenstilen und Zellenschattierung.
weight: 10
url: /de/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabelle und Zelle mit unterschiedlichen Rändern formatieren

## Einführung

Haben Sie schon einmal versucht, Ihren Word-Dokumenten durch Anpassen der Ränder von Tabellen und Zellen ein professionelleres Aussehen zu verleihen? Falls nicht, erwartet Sie ein Leckerbissen! Dieses Tutorial führt Sie durch den Prozess der Formatierung von Tabellen und Zellen mit unterschiedlichen Rändern mithilfe von Aspose.Words für .NET. Stellen Sie sich vor, Sie könnten das Erscheinungsbild Ihrer Tabellen mit nur wenigen Codezeilen ändern. Neugierig? Lassen Sie uns eintauchen und erkunden, wie Sie dies ganz einfach erreichen können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
- Grundlegende Kenntnisse der C#-Programmierung.
- Visual Studio ist auf Ihrem Computer installiert.
-  Aspose.Words für .NET-Bibliothek. Wenn Sie es noch nicht installiert haben, können Sie es herunterladen[Hier](https://releases.aspose.com/words/net/).
-  Eine gültige Aspose-Lizenz. Sie erhalten eine kostenlose Testversion oder eine temporäre Lizenz von[Hier](https://purchase.aspose.com/temporary-license/).

## Namespaces importieren

Um mit Aspose.Words für .NET zu arbeiten, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Fügen Sie oben in Ihrer Codedatei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Schritt 1: Dokument und DocumentBuilder initialisieren

Zuerst müssen Sie ein neues Dokument erstellen und den DocumentBuilder initialisieren, der beim Erstellen des Dokumentinhalts hilft. 

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Beginnen Sie mit der Erstellung einer Tabelle

Beginnen Sie als Nächstes mit dem DocumentBuilder mit der Erstellung einer Tabelle und fügen Sie die erste Zelle ein.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Schritt 3: Tabellenränder festlegen

Legen Sie die Rahmen für die gesamte Tabelle fest. Dieser Schritt stellt sicher, dass alle Zellen in der Tabelle einen einheitlichen Rahmenstil haben, sofern nicht anders angegeben.

```csharp
// Legen Sie die Grenzen für die gesamte Tabelle fest.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Schritt 4: Zellenschattierung anwenden

Wenden Sie Schattierungen auf die Zellen an, um sie optisch voneinander abzugrenzen. In diesem Beispiel legen wir die Hintergrundfarbe der ersten Zelle auf Rot fest.


```csharp
// Legen Sie die Zellenschattierung für diese Zelle fest.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Schritt 5: Einfügen einer weiteren Zelle mit anderer Schattierung

Fügen Sie die zweite Zelle ein und wenden Sie eine andere Schattierungsfarbe an. Dadurch wird die Tabelle bunter und leichter lesbar.

```csharp
builder.InsertCell();
// Geben Sie für die zweite Zelle eine andere Zellenschattierung an.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Schritt 6: Zellenformatierung löschen

Löschen Sie die Zellenformatierung aus vorherigen Vorgängen, um sicherzustellen, dass die nächsten Zellen nicht dieselben Stile erben.


```csharp
// Löschen Sie die Zellenformatierung aus vorherigen Vorgängen.
builder.CellFormat.ClearFormatting();
```

## Schritt 7: Ränder für bestimmte Zellen anpassen

Passen Sie die Ränder bestimmter Zellen an, damit sie hervorstechen. Hier legen wir größere Ränder für die erste Zelle der neuen Zeile fest.

```csharp
builder.InsertCell();
// Erstellen Sie größere Ränder für die erste Zelle dieser Zeile. Das wird anders sein
// im Vergleich zu den für die Tabelle festgelegten Grenzen.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Schritt 8: Letzte Zelle einfügen

Fügen Sie die letzte Zelle ein und stellen Sie sicher, dass ihre Formatierung gelöscht wird, sodass die Standardstile der Tabelle verwendet werden.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Schritt 9: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie Tabellen und Zellen mit verschiedenen Rändern mithilfe von Aspose.Words für .NET formatieren. Durch Anpassen von Tabellenrändern und Zellenschattierungen können Sie die visuelle Attraktivität Ihrer Dokumente deutlich verbessern. Also los, experimentieren Sie mit verschiedenen Stilen und lassen Sie Ihre Dokumente hervorstechen!

## Häufig gestellte Fragen

### Kann ich für jede Zelle einen anderen Rahmenstil verwenden?
 Ja, Sie können für jede Zelle einen anderen Rahmenstil festlegen, indem Sie die`CellFormat.Borders` Eigentum.

### Wie kann ich alle Ränder aus einer Tabelle entfernen?
 Sie können alle Ränder entfernen, indem Sie den Randstil auf`LineStyle.None`.

### Ist es möglich, für jede Zelle eine andere Rahmenfarbe festzulegen?
 Absolut! Sie können die Rahmenfarbe für jede Zelle anpassen, indem Sie`CellFormat.Borders.Color` Eigentum.

### Kann ich Bilder als Zellenhintergründe verwenden?
Obwohl Aspose.Words Bilder nicht direkt als Zellenhintergründe unterstützt, können Sie ein Bild in eine Zelle einfügen und seine Größe so anpassen, dass es den Zellenbereich abdeckt.

### Wie füge ich Zellen in einer Tabelle zusammen?
 Sie können Zellen verbinden, indem Sie`CellFormat.HorizontalMerge` Und`CellFormat.VerticalMerge` Eigenschaften.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
