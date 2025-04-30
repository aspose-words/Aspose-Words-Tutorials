---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET XY-Achseneigenschaften in einem Diagramm definieren. Perfekt für .NET-Entwickler."
"linktitle": "Definieren der XY-Achseneigenschaften in einem Diagramm"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Definieren der XY-Achseneigenschaften in einem Diagramm"
"url": "/de/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definieren der XY-Achseneigenschaften in einem Diagramm

## Einführung

Diagramme sind ein leistungsstarkes Werkzeug zur Datenvisualisierung. Wenn Sie professionelle Dokumente mit dynamischen Diagrammen erstellen müssen, ist Aspose.Words für .NET eine unverzichtbare Bibliothek. Dieser Artikel führt Sie durch die Definition der XY-Achseneigenschaften in einem Diagramm mit Aspose.Words für .NET und erläutert jeden Schritt, um Klarheit und Verständlichkeit zu gewährleisten.

## Voraussetzungen

Bevor Sie mit der Codierung beginnen, müssen einige Voraussetzungen erfüllt sein:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET haben. Sie können [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Sie benötigen eine integrierte Entwicklungsumgebung (IDE) wie Visual Studio.
3. .NET Framework: Stellen Sie sicher, dass Ihre Entwicklungsumgebung für die .NET-Entwicklung eingerichtet ist.
4. Grundkenntnisse in C#: Diese Anleitung setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Dadurch stellen Sie sicher, dass Sie Zugriff auf alle Klassen und Methoden haben, die Sie zum Erstellen und Bearbeiten von Dokumenten und Diagrammen benötigen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Wir unterteilen den Prozess in einfache Schritte, von denen sich jeder auf einen bestimmten Teil der Definition der XY-Achseneigenschaften in einem Diagramm konzentriert.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Zuerst müssen Sie ein neues Dokument initialisieren und ein `DocumentBuilder` Objekt. Das `DocumentBuilder` hilft beim Einfügen von Inhalten in das Dokument.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Einfügen eines Diagramms

Als Nächstes fügen Sie ein Diagramm in das Dokument ein. In diesem Beispiel verwenden wir ein Flächendiagramm. Sie können die Abmessungen des Diagramms nach Bedarf anpassen.

```csharp
// Diagramm einfügen
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Schritt 3: Standardreihen löschen und benutzerdefinierte Daten hinzufügen

Standardmäßig enthält das Diagramm einige vordefinierte Reihen. Wir löschen diese und fügen unsere benutzerdefinierten Datenreihen hinzu.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Schritt 4: Definieren Sie die Eigenschaften der X-Achse

Nun legen wir die Eigenschaften der X-Achse fest. Dazu gehören das Festlegen des Kategorietyps, das Anpassen der Achsenkreuzung sowie das Anpassen von Teilstrichen und Beschriftungen.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Gemessen in Anzeigeeinheiten der Y-Achse (Hunderter).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Schritt 5: Definieren Sie die Eigenschaften der Y-Achse

Auf ähnliche Weise legen Sie die Eigenschaften für die Y-Achse fest. Dazu gehören die Festlegung der Position der Teilstrichbeschriftung, der Haupt- und Nebeneinheiten, der Anzeigeeinheit und der Skalierung.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis. Dadurch wird das Word-Dokument mit dem angepassten Diagramm erstellt.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Abschluss

Das Erstellen und Anpassen von Diagrammen in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert, sobald Sie die erforderlichen Schritte verstanden haben. Diese Anleitung führt Sie durch den Prozess der Definition der XY-Achseneigenschaften in einem Diagramm, von der Initialisierung des Dokuments bis zum Speichern des Endprodukts. Mit diesen Kenntnissen können Sie detaillierte, professionell aussehende Diagramme erstellen, die Ihre Dokumente aufwerten.

## Häufig gestellte Fragen

### Welche Arten von Diagrammen kann ich mit Aspose.Words für .NET erstellen?
Sie können verschiedene Diagrammtypen erstellen, darunter Flächen-, Balken-, Linien-, Kreisdiagramme und mehr.

### Wie installiere ich Aspose.Words für .NET?
Sie können Aspose.Words für .NET herunterladen von [Hier](https://releases.aspose.com/words/net/) und befolgen Sie die bereitgestellten Installationsanweisungen.

### Kann ich das Erscheinungsbild meiner Diagramme anpassen?
Ja, Aspose.Words für .NET ermöglicht eine umfassende Anpassung von Diagrammen, einschließlich Farben, Schriftarten und Achseneigenschaften.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
Ja, Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/).

### Wo finde ich weitere Tutorials und Dokumentationen?
Weitere Tutorials und ausführliche Dokumentation finden Sie auf der [Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}