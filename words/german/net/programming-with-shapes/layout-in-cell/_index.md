---
"description": "Erfahren Sie in dieser umfassenden Anleitung, wie Sie das Layout in Zellen mit Aspose.Words für .NET festlegen. Ideal für Entwickler, die Word-Dokumente anpassen möchten."
"linktitle": "Layout in Zelle"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Layout in Zelle"
"url": "/de/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Layout in Zelle

## Einführung

Wenn Sie schon immer das Layout Ihrer Tabellenzellen in Word-Dokumenten programmgesteuert optimieren wollten, sind Sie hier genau richtig. Heute zeigen wir Ihnen, wie Sie das Zellenlayout mit Aspose.Words für .NET festlegen. Wir erklären es anhand eines praktischen Beispiels Schritt für Schritt, damit Sie es problemlos nachvollziehen können.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass die Bibliothek Aspose.Words für .NET installiert ist. Falls nicht, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Sie benötigen eine Entwicklungsumgebung mit .NET. Visual Studio ist eine gute Wahl, wenn Sie Empfehlungen suchen.
3. Grundkenntnisse in C#: Ich werde zwar jeden Schritt erklären, aber ein grundlegendes Verständnis von C# wird Ihnen dabei helfen, den Anweisungen leichter zu folgen.
4. Dokumentverzeichnis: Bereiten Sie einen Verzeichnispfad vor, in dem Sie Ihre Dokumente speichern. Wir nennen dies `YOUR DOCUMENT DIRECTORY`.

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

## Schritt 1: Erstellen Sie ein neues Dokument

Zuerst erstellen wir ein neues Word-Dokument und initialisieren ein `DocumentBuilder` Objekt, das uns beim Erstellen unserer Inhalte hilft.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Erstellen Sie eine Tabelle und legen Sie das Zeilenformat fest

Wir beginnen mit der Erstellung einer Tabelle und legen die Höhe und Höhenregel für die Zeilen fest.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Schritt 3: Zellen einfügen und mit Inhalt füllen

Als Nächstes fügen wir Zellen in die Tabelle ein. Nach jeweils 7 Zellen beenden wir die Zeile, um eine neue zu erstellen.

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

Fügen wir nun ein Wasserzeichen zu unserem Dokument hinzu. Wir erstellen ein `Shape` Objekt und legen Sie seine Eigenschaften fest.

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

Wir werden das Erscheinungsbild des Wasserzeichens weiter anpassen, indem wir seine Farb- und Texteigenschaften festlegen.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Schritt 6: Wasserzeichen in Dokument einfügen

Wir suchen den letzten Lauf im Dokument und fügen an dieser Stelle das Wasserzeichen ein.

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

Und da haben Sie es! Sie haben erfolgreich ein Word-Dokument mit einem benutzerdefinierten Tabellenlayout erstellt und mithilfe von Aspose.Words für .NET ein Wasserzeichen hinzugefügt. Dieses Tutorial bietet Ihnen eine klare Schritt-für-Schritt-Anleitung, die Ihnen hilft, jeden Teil des Prozesses zu verstehen. Mit diesen Kenntnissen können Sie nun programmgesteuert anspruchsvollere und individuellere Word-Dokumente erstellen.

## Häufig gestellte Fragen

### Kann ich für den Wasserzeichentext eine andere Schriftart verwenden?
Ja, Sie können die Schriftart ändern, indem Sie die `watermark.TextPath.FontFamily` Eigenschaft auf die gewünschte Schriftart.

### Wie passe ich die Position des Wasserzeichens an?
Sie können die `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, Und `VerticalAlignment` Eigenschaften, um die Position des Wasserzeichens anzupassen.

### Ist es möglich, für das Wasserzeichen ein Bild statt Text zu verwenden?
Absolut! Sie können eine `Shape` mit dem Typ `ShapeType.Image` und legen Sie das Bild mit dem `ImageData.SetImage` Verfahren.

### Kann ich Tabellen mit unterschiedlichen Zeilenhöhen erstellen?
Ja, Sie können für jede Reihe eine andere Höhe einstellen, indem Sie die `RowFormat.Height` -Eigenschaft, bevor Sie Zellen in diese Zeile einfügen.

### Wie entferne ich ein Wasserzeichen aus dem Dokument?
Sie können das Wasserzeichen entfernen, indem Sie es in der Formensammlung des Dokuments suchen und den `Remove` Verfahren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}