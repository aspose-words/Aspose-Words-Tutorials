---
title: Anpassen eines einzelnen Diagrammdatenpunkts in einem Diagramm
linktitle: Anpassen eines einzelnen Diagrammdatenpunkts in einem Diagramm
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in einer detaillierten Schritt-für-Schritt-Anleitung, wie Sie einzelne Diagrammdatenpunkte mit Aspose.Words für .NET anpassen. Verbessern Sie Ihre Diagramme mit einzigartigen Markierungen und Größen.
weight: 10
url: /de/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anpassen eines einzelnen Diagrammdatenpunkts in einem Diagramm

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie Ihre Diagramme mit einzigartigen Datenpunkten hervorheben können? Dann ist heute Ihr Glückstag! Wir tauchen ein in die Anpassung eines einzelnen Diagrammdatenpunkts mit Aspose.Words für .NET. Schnall dich an für eine Fahrt durch ein Schritt-für-Schritt-Tutorial, das nicht nur informativ, sondern auch unterhaltsam und leicht verständlich ist.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alle wichtigen Voraussetzungen erfüllt haben:

-  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version haben.[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
- Grundlegende Kenntnisse in C#: Grundkenntnisse in der C#-Programmierung sind hilfreich.
- Integrierte Entwicklungsumgebung (IDE): Visual Studio wird empfohlen.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces, um den Ball ins Rollen zu bringen:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Okay, legen wir los, indem wir ein neues Dokument und einen DocumentBuilder initialisieren. Dies wird die Leinwand für unser Diagramm sein.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier,`dataDir` ist der Verzeichnispfad, in dem Sie Ihr Dokument speichern. Der`DocumentBuilder` Klasse hilft beim Erstellen des Dokuments.

## Schritt 2: Einfügen eines Diagramms

Als Nächstes fügen wir ein Liniendiagramm in das Dokument ein. Dies wird unser Spielplatz zum Anpassen von Datenpunkten.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 Der`InsertChart` Die Methode verwendet den Diagrammtyp, die Breite und die Höhe als Parameter. In diesem Fall fügen wir ein Liniendiagramm mit einer Breite von 432 und einer Höhe von 252 ein.

## Schritt 3: Auf Diagrammserien zugreifen

Jetzt ist es an der Zeit, auf die Reihen in unserem Diagramm zuzugreifen. Ein Diagramm kann mehrere Reihen enthalten und jede Reihe enthält Datenpunkte.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Hier greifen wir auf die ersten beiden Reihen in unserem Diagramm zu. 

## Schritt 4: Datenpunkte anpassen

Und hier geschieht die Magie! Lassen Sie uns bestimmte Datenpunkte innerhalb unserer Serie anpassen.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Wir holen die Datenpunkte aus der ersten Reihe. Jetzt passen wir diese Punkte an.

### Datenpunkt 00 anpassen

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Für`dataPoint00`, wir legen eine Explosion fest (nützlich für Kreisdiagramme), ändern das Markierungssymbol in einen Kreis und legen die Markierungsgröße auf 15 fest.

### Datenpunkt 01 anpassen

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Für`dataPoint01`ändern wir das Markierungssymbol in eine Raute und setzen die Markierungsgröße auf 20.

### Datenpunkt in Serie 1 anpassen

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 Für den dritten Datenpunkt in`series1`, wir stellen es so ein, dass es invertiert wird, wenn der Wert negativ ist, ändern das Markierungssymbol in einen Stern und setzen die Markierungsgröße auf 20.

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument mit allen Anpassungen.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Diese Zeile speichert das Dokument in Ihrem angegebenen Verzeichnis unter dem Namen`WorkingWithCharts.SingleChartDataPoint.docx`.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich einzelne Datenpunkte in einem Diagramm mit Aspose.Words für .NET angepasst. Durch die Anpassung einiger Eigenschaften können Sie Ihre Diagramme viel informativer und optisch ansprechender gestalten. Experimentieren Sie also mit verschiedenen Markierungen und Größen, um herauszufinden, was für Ihre Daten am besten funktioniert.

## Häufig gestellte Fragen

### Kann ich Datenpunkte in anderen Diagrammtypen anpassen?

Auf jeden Fall! Sie können Datenpunkte in verschiedenen Diagrammtypen anpassen, darunter Balkendiagramme, Kreisdiagramme und mehr. Der Vorgang ist bei verschiedenen Diagrammtypen ähnlich.

### Ist es möglich, Datenpunkten benutzerdefinierte Beschriftungen hinzuzufügen?

 Ja, Sie können Datenpunkten benutzerdefinierte Beschriftungen hinzufügen, indem Sie`ChartDataPoint.Label` Eigenschaft. Dadurch können Sie für jeden Datenpunkt mehr Kontext bereitstellen.

### Wie kann ich einen Datenpunkt aus einer Reihe entfernen?

 Sie können einen Datenpunkt entfernen, indem Sie seine Sichtbarkeit auf „false“ setzen.`dataPoint.IsVisible = false`.

### Kann ich Bilder als Markierungen für Datenpunkte verwenden?

Während Aspose.Words die direkte Verwendung von Bildern als Markierungen nicht unterstützt, können Sie benutzerdefinierte Formen erstellen und diese als Markierungen verwenden.

### Ist es möglich, Datenpunkte im Diagramm zu animieren?

Aspose.Words für .NET unterstützt keine Animation für Diagrammdatenpunkte. Sie können jedoch mit anderen Tools animierte Diagramme erstellen und diese in Ihre Word-Dokumente einbetten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
