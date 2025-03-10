---
title: Tabelle im Word-Dokument erstellen
linktitle: Tabelle im Word-Dokument erstellen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem ausführlichen Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET eine Tabelle in einem Word-Dokument erstellen. Perfekt für Anfänger und Profis gleichermaßen.
weight: 10
url: /de/net/add-content-using-documentbuilder/build-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabelle im Word-Dokument erstellen

## Einführung

Hallo! Möchten Sie Tabellen programmgesteuert in Ihren Word-Dokumenten erstellen? Dann sind Sie hier genau richtig! Heute tauchen wir in die magische Welt von Aspose.Words für .NET ein. Mit dieser leistungsstarken Bibliothek können Sie Word-Dokumente wie ein Profi bearbeiten. Stellen Sie sich vor, Sie sind ein Zauberer und Aspose.Words ist Ihr Zauberstab, mit dem Sie Dokumente mit einer Handbewegung (oder besser gesagt einer Codezeile) erstellen, bearbeiten und formatieren können. In diesem Tutorial konzentrieren wir uns auf das Erstellen einer Tabelle in einem Word-Dokument. Also schnappen Sie sich Ihren Programmierhut und legen Sie los!

## Voraussetzungen

Bevor wir uns auf unser Tischbau-Abenteuer stürzen, sollten wir sicherstellen, dass alles in Ordnung ist. Folgendes brauchen Sie:

- Visual Studio (oder eine andere C#-IDE)
- .NET Framework (4.0 oder höher)
- Aspose.Words für .NET-Bibliothek

 Wenn Sie Aspose.Words noch nicht haben, können Sie ganz einfach[Laden Sie es hier herunter](https://releases.aspose.com/words/net/) Sie können auch mit einem[Kostenlose Testversion](https://releases.aspose.com/) wenn Sie das Wasser testen möchten. Für diejenigen, die bereit sind, den Sprung zu wagen, können Sie[eine Lizenz kaufen](https://purchase.aspose.com/buy)oder wenn Sie mehr Zeit zur Auswertung benötigen, holen Sie sich ein[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

## Namespaces importieren

Das Wichtigste zuerst: Bringen wir unsere Namespaces in Ordnung. Dieser Schritt ist wie das Bereiten der Bühne vor der großen Aufführung. Fügen Sie Ihrer C#-Datei die folgenden Namespaces hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

Okay, lassen Sie uns den Vorgang zum Erstellen einer Tabelle in einem Word-Dokument in überschaubare Schritte unterteilen. Stellen Sie es sich wie das Zusammenbauen eines Möbelstücks vor – wir nehmen uns eine Schraube und einen Bolzen nach dem anderen vor.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

 Zuerst müssen wir unser Dokument und den Dokument-Builder einrichten.`Document` Klasse repräsentiert das Word-Dokument und`DocumentBuilder` ist unser praktisches Tool zum Hinzufügen von Inhalten.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Stellen Sie sich das so vor, als ob Sie die Leinwand auslegen, bevor Sie mit dem Malen beginnen.`DocumentBuilder` ist unser Pinsel, bereit, ein Meisterwerk zu schaffen.

## Schritt 2: Starten Sie die Tabelle

 Nun beginnen wir mit unserem Tisch. Wir nennen die`StartTable` Methode der`DocumentBuilder` um zu beginnen.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

 Durch die Verwendung`StartTable` sagen wir Aspose.Words, dass wir dabei sind, eine Tabelle zu erstellen.`InsertCell` Methode fügt die erste Zelle hinzu und`AutoFit` stellt sicher, dass unsere Spalten eine feste Breite haben.

## Schritt 3: Formatieren Sie die erste Zeile

Lassen Sie uns die erste Zeile aufpeppen, indem Sie etwas Text hinzufügen und ihn vertikal zur Mitte ausrichten.

```csharp
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.Write("This is row 1 cell 1");

builder.InsertCell();
builder.Write("This is row 1 cell 2");

builder.EndRow();
```

Stellen Sie sich das so vor, als würden Sie die Tischdecke aufstellen und das erste Geschirr aufstellen. Wir sorgen dafür, dass alles ordentlich und sauber aussieht.

## Schritt 4: Erstellen Sie die zweite Zeile mit benutzerdefinierter Formatierung

Lassen Sie uns nun mit der zweiten Zeile kreativ werden. Wir legen die Zeilenhöhe fest, richten den Text anders aus und fügen etwas Flair hinzu, indem wir die Textausrichtung ändern.

```csharp
builder.InsertCell();

builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
builder.CellFormat.Orientation = TextOrientation.Upward;
builder.Writeln("This is row 2 cell 1");

builder.InsertCell();
builder.CellFormat.Orientation = TextOrientation.Downward;
builder.Writeln("This is row 2 cell 2");

builder.EndRow();
```

 Hier legen wir die Höhe der Reihe fest und stellen sicher, dass sie fixiert bleibt mit`HeightRule.Exactly`. Durch die Änderungen der Textausrichtung fällt unsere Tabelle auf und erhält einen Hauch von Einzigartigkeit.

## Schritt 5: Beenden Sie die Tabelle

Nachdem alle unsere Zeilen festgelegt sind, ist es Zeit, den Tabellenerstellungsprozess abzuschließen.

```csharp
builder.EndTable();
```

Mit diesem Schritt geben wir unserem Kunstwerk den letzten Schliff. Die Tischkonstruktion ist fertig und einsatzbereit.

## Schritt 6: Speichern Sie das Dokument

 Zum Schluss speichern wir unser Dokument. Wählen Sie einen Speicherort und einen Namen für Ihre Datei und speichern Sie sie mit dem`.docx` Verlängerung.

```csharp
doc.Save("YourDirectoryPath/AddContentUsingDocumentBuilder.BuildTable.docx");
```

Stellen Sie sich das so vor, als würden Sie Ihr Meisterwerk einrahmen und zur Schau stellen. Ihre Tabelle ist jetzt Teil eines Word-Dokuments und kann geteilt und bewundert werden.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine Tabelle in einem Word-Dokument mit Aspose.Words für .NET erstellt. Dieses Tutorial hat Sie durch jeden Schritt geführt, vom Initialisieren des Dokuments bis zum Speichern des Endprodukts. Mit Aspose.Words sind die Möglichkeiten endlos. Egal, ob Sie Berichte, Rechnungen oder andere Dokumente erstellen, Sie haben jetzt die Möglichkeit, Tabellen nach Herzenslust zu formatieren und anzupassen.

Denken Sie daran: Übung macht den Meister. Scheuen Sie sich also nicht, mit verschiedenen Tabellenformaten und -stilen zu experimentieren. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten. Sie können damit Dokumente erstellen, bearbeiten und manipulieren, ohne Microsoft Word zu benötigen.

### Wie installiere ich Aspose.Words für .NET?
 Du kannst[Laden Sie Aspose.Words für .NET hier herunter](https://releases.aspose.com/words/net/)Befolgen Sie die bereitgestellten Installationsanweisungen, um es in Ihrer Entwicklungsumgebung einzurichten.

### Kann ich Aspose.Words kostenlos nutzen?
 Aspose.Words bietet eine[Kostenlose Testversion](https://releases.aspose.com/) damit Sie die Funktionen testen können. Für eine erweiterte Nutzung können Sie eine Lizenz erwerben oder eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

### Was sind weitere Funktionen von Aspose.Words für .NET?
Neben dem Erstellen von Tabellen können Sie mit Aspose.Words auch mit Text, Bildern, Stilen und vielen anderen Dokumentelementen arbeiten. Es unterstützt eine breite Palette von Dokumentformaten, darunter DOCX, PDF und HTML.

### Wo bekomme ich Hilfe, wenn ich auf Probleme stoße?
 Wenn Sie Unterstützung benötigen, besuchen Sie die[Aspose.Words-Forum](https://forum.aspose.com/c/words/8) wo Sie Fragen stellen und Hilfe von der Community und den Aspose-Entwicklern erhalten können.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
