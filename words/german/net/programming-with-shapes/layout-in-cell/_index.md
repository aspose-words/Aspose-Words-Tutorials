---
title: Layout in Zelle
linktitle: Layout in Zelle
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem umfassenden Handbuch, wie Sie mit Aspose.Words für .NET das Layout in Zellen festlegen. Perfekt für Entwickler, die Word-Dokumente anpassen möchten.
weight: 10
url: /de/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Layout in Zelle

## Einführung

Wenn Sie schon immer das Layout Ihrer Tabellenzellen in Word-Dokumenten programmgesteuert optimieren wollten, sind Sie hier richtig. Heute werden wir uns damit befassen, wie Sie das Layout in Zellen mit Aspose.Words für .NET festlegen. Wir werden ein praktisches Beispiel durchgehen und es Schritt für Schritt aufschlüsseln, damit Sie es problemlos nachvollziehen können.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Wenn nicht, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Sie benötigen eine mit .NET eingerichtete Entwicklungsumgebung. Visual Studio ist eine gute Wahl, wenn Sie nach Empfehlungen suchen.
3. Grundkenntnisse in C#: Ich werde zwar jeden Schritt erklären, aber Grundkenntnisse in C# helfen Ihnen dabei, den Anweisungen leichter zu folgen.
4.  Dokumentverzeichnis: Bereiten Sie einen Verzeichnispfad vor, in dem Sie Ihre Dokumente speichern. Wir nennen dies`YOUR DOCUMENT DIRECTORY`.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Lassen Sie uns den Prozess in überschaubare Schritte unterteilen.

## Schritt 1: Neues Dokument erstellen

 Zuerst erstellen wir ein neues Word-Dokument und initialisieren ein`DocumentBuilder` Objekt, das uns beim Erstellen unserer Inhalte hilft.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Eine Tabelle starten und Zeilenformat festlegen

Wir beginnen mit der Erstellung einer Tabelle und geben die Höhe und Höhenregel für die Zeilen an.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Schritt 3: Zellen einfügen und mit Inhalt füllen

Als nächstes fügen wir in einer Schleife Zellen in die Tabelle ein. Nach jeweils 7 Zellen beenden wir die Zeile, um eine neue zu erstellen.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Schritt 4: Fügen Sie eine Wasserzeichenform hinzu

 Fügen wir nun unserem Dokument ein Wasserzeichen hinzu. Wir erstellen ein`Shape` -Objekt und legen Sie seine Eigenschaften fest.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Zeigen Sie die Form außerhalb der Tabellenzelle an, wenn sie in einer Zelle platziert wird.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Schritt 5: Wasserzeichen-Erscheinungsbild anpassen

Wir werden das Erscheinungsbild des Wasserzeichens weiter anpassen, indem wir seine Farbe und Texteigenschaften festlegen.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Schritt 6: Wasserzeichen in Dokument einfügen

Wir suchen den letzten Durchlauf im Dokument und fügen an dieser Stelle das Wasserzeichen ein.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Schritt 7: Dokument für Word 2010 optimieren

Um die Kompatibilität zu gewährleisten, optimieren wir das Dokument für Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Schritt 8: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein Word-Dokument mit einem angepassten Tabellenlayout erstellt und mithilfe von Aspose.Words für .NET ein Wasserzeichen hinzugefügt. Dieses Tutorial soll Ihnen eine klare Schritt-für-Schritt-Anleitung bieten, die Ihnen hilft, jeden Teil des Prozesses zu verstehen. Mit diesen Fähigkeiten können Sie nun programmgesteuert anspruchsvollere und angepasstere Word-Dokumente erstellen.

## Häufig gestellte Fragen

### Kann ich für den Wasserzeichentext eine andere Schriftart verwenden?
 Ja, Sie können die Schriftart ändern, indem Sie die`watermark.TextPath.FontFamily` -Eigenschaft auf die gewünschte Schriftart.

### Wie passe ich die Position des Wasserzeichens an?
 Sie können die`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , Und`VerticalAlignment` Eigenschaften, um die Position des Wasserzeichens anzupassen.

### Ist es möglich, für das Wasserzeichen ein Bild statt Text zu verwenden?
 Auf jeden Fall! Sie können eine`Shape` mit dem Typ`ShapeType.Image` und legen Sie das Bild mit dem`ImageData.SetImage` Verfahren.

### Kann ich Tabellen mit unterschiedlichen Zeilenhöhen erstellen?
Ja, Sie können für jede Reihe eine andere Höhe einstellen, indem Sie die`RowFormat.Height` -Eigenschaft, bevor Zellen in diese Zeile eingefügt werden.

### Wie entferne ich ein Wasserzeichen aus dem Dokument?
 Sie können das Wasserzeichen entfernen, indem Sie es in der Formensammlung des Dokuments suchen und den`Remove` Verfahren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
