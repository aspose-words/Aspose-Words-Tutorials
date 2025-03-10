---
title: Anzahl der Datenbeschriftungen in einem Diagramm formatieren
linktitle: Anzahl der Datenbeschriftungen in einem Diagramm formatieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Datenbeschriftungen in Diagrammen formatieren. Verbessern Sie Ihre Word-Dokumente mühelos.
weight: 10
url: /de/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anzahl der Datenbeschriftungen in einem Diagramm formatieren

## Einführung

Zum Erstellen ansprechender und informativer Dokumente gehört häufig das Einfügen von Diagrammen mit gut formatierten Datenbeschriftungen. Wenn Sie ein .NET-Entwickler sind und Ihre Word-Dokumente mit anspruchsvollen Diagrammen erweitern möchten, ist Aspose.Words für .NET eine fantastische Bibliothek, die Ihnen dabei hilft. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess der Formatierung von Zahlenbeschriftungen in einem Diagramm mit Aspose.Words für .NET.

## Voraussetzungen

Bevor Sie sich in den Code vertiefen, müssen einige Voraussetzungen erfüllt sein:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Wenn Sie sie noch nicht installiert haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Sie sollten eine .NET-Entwicklungsumgebung eingerichtet haben. Visual Studio wird dringend empfohlen.
- Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind unbedingt erforderlich, da es in diesem Tutorial um das Schreiben und Verstehen von C#-Code geht.
-  Temporäre Lizenz: Um Aspose.Words ohne Einschränkungen nutzen zu können, erhalten Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).

Lassen Sie uns nun Schritt für Schritt in die Formatierung von Zahlenbeschriftungen in einem Diagramm eintauchen.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren, um mit Aspose.Words für .NET zu arbeiten. Fügen Sie oben in Ihrer C#-Datei die folgenden Zeilen hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Bevor Sie mit der Bearbeitung Ihres Word-Dokuments beginnen können, müssen Sie das Verzeichnis angeben, in dem Ihr Dokument gespeichert werden soll. Dies ist für den späteren Speichervorgang unbedingt erforderlich.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis.

## Schritt 2: Initialisieren Sie das Dokument und den DocumentBuilder

 Der nächste Schritt ist die Initialisierung eines neuen`Document` und ein`DocumentBuilder` . Der`DocumentBuilder` ist eine Hilfsklasse, die es uns ermöglicht, den Dokumentinhalt zu erstellen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Einfügen eines Diagramms in das Dokument

 Fügen wir nun ein Diagramm in das Dokument ein, und zwar mit dem`DocumentBuilder`In diesem Tutorial verwenden wir als Beispiel ein Liniendiagramm.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Hier fügen wir ein Liniendiagramm mit einer bestimmten Breite und Höhe ein und legen den Diagrammtitel fest.

## Schritt 4: Standardserie löschen und neue Serie hinzufügen

Standardmäßig enthält das Diagramm einige vorgenerierte Reihen. Wir müssen diese löschen und unsere eigenen Reihen mit bestimmten Datenpunkten hinzufügen.

```csharp
// Standardmäßig generierte Serien löschen.
chart.Series.Clear();

// Fügen Sie neue Reihen mit benutzerdefinierten Datenpunkten hinzu.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Schritt 5: Datenbeschriftungen aktivieren

Um die Datenbeschriftungen im Diagramm anzuzeigen, müssen wir sie für unsere Reihe aktivieren.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Schritt 6: Datenbeschriftungen formatieren

Der Kern dieses Tutorials ist das Formatieren der Datenbeschriftungen. Wir können auf jede Datenbeschriftung einzeln unterschiedliche Zahlenformate anwenden.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Währungsformat
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Datumsformat
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Prozentformat
```

 Darüber hinaus können Sie das Format einer Datenbeschriftung mit einer Quellzelle verknüpfen. Wenn die Verknüpfung erfolgt,`NumberFormat` wird auf allgemein zurückgesetzt und von der Quellzelle übernommen.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Schritt 7: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Dadurch wird Ihr Dokument unter dem angegebenen Namen gespeichert und sichergestellt, dass Ihr Diagramm mit formatierten Datenbeschriftungen erhalten bleibt.

## Abschluss

Das Formatieren von Datenbeschriftungen in einem Diagramm mit Aspose.Words für .NET kann die Lesbarkeit und Professionalität Ihrer Word-Dokumente erheblich verbessern. Wenn Sie dieser Schritt-für-Schritt-Anleitung folgen, sollten Sie nun in der Lage sein, ein Diagramm zu erstellen, Datenreihen hinzuzufügen und die Datenbeschriftungen nach Ihren Wünschen zu formatieren. Aspose.Words für .NET ist ein leistungsstarkes Tool, das eine umfassende Anpassung und Automatisierung von Word-Dokumenten ermöglicht und somit für .NET-Entwickler von unschätzbarem Wert ist.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zum programmgesteuerten Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten mit C#.

### Kann ich mit Aspose.Words für .NET andere Diagrammtypen formatieren?
Ja, Aspose.Words für .NET unterstützt eine Vielzahl von Diagrammtypen, darunter Balken-, Säulen-, Kreisdiagramme und mehr.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words für .NET?
Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).

### Ist es möglich, Datenbeschriftungen mit Quellzellen in Excel zu verknüpfen?
Ja, Sie können Datenbeschriftungen mit Quellzellen verknüpfen, sodass das Zahlenformat von der Quellzelle übernommen wird.

### Wo finde ich ausführlichere Dokumentation für Aspose.Words für .NET?
 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
