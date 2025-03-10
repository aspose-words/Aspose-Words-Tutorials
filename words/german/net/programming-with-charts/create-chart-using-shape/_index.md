---
title: Erstellen und Anpassen von Diagrammen mithilfe von Formen
linktitle: Erstellen und Anpassen von Diagrammen mithilfe von Formen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Diagramme in Word-Dokumenten erstellen und anpassen. Perfekt für die Datenvisualisierung.
weight: 10
url: /de/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen und Anpassen von Diagrammen mithilfe von Formen

## Einführung

Das Erstellen und Anpassen von Diagrammen in Ihren Dokumenten ist in der heutigen datengesteuerten Welt eine entscheidende Fähigkeit. Diagramme können dabei helfen, Daten zu visualisieren und komplexe Informationen leichter verdaulich zu machen. Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente programmgesteuert erstellen und bearbeiten können. In diesem Tutorial führen wir Sie durch den Prozess des Erstellens und Anpassens eines Liniendiagramms mit Aspose.Words für .NET. Am Ende dieses Handbuchs können Sie mühelos professionell aussehende Diagramme erstellen.

## Voraussetzungen

Bevor Sie sich in den Code vertiefen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Words für .NET-Bibliothek: Sie können sie herunterladen[Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Jede Version, die .NET unterstützt.
- Grundkenntnisse in C#: Das Verständnis der Grundlagen von C# wird Ihnen helfen, dem Tutorial zu folgen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Dieser Schritt ist wichtig, da Sie damit die von Aspose.Words für .NET bereitgestellten Klassen und Methoden verwenden können.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Schritt 1: Neues Dokument erstellen

Zuerst müssen Sie ein neues Word-Dokument erstellen. Dieses Dokument dient als Leinwand für Ihr Diagramm.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Einfügen eines Diagramms

 Als nächstes fügen Sie ein Liniendiagramm in das Dokument ein. Das`DocumentBuilder.InsertChart` Zu diesem Zweck wird die Methode verwendet.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Schritt 3: Den Diagrammtitel anpassen

Durch Anpassen des Diagrammtitels können Sie den Kontext für die angezeigten Daten verbessern. Mit dem folgenden Code können Sie den Titel anzeigen und seinen Text festlegen:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Bitte beachten Sie, dass, wenn als Titeltext ein Null- oder leerer Wert angegeben wird, ein automatisch generierter Titel angezeigt wird.
```

## Schritt 4: Passen Sie die Legendenposition an

Die Legende hilft dabei, verschiedene Datenreihen in Ihrem Diagramm zu identifizieren. Sie können ihre Position und Overlay-Einstellungen wie folgt anpassen:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Schritt 5: Speichern Sie das Dokument

Zum Schluss müssen Sie das Dokument noch speichern. Mit diesem Schritt stellen Sie sicher, dass alle Ihre Änderungen in die Datei geschrieben werden.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Abschluss

In diesem Tutorial haben wir erläutert, wie Sie mit Aspose.Words für .NET ein Liniendiagramm in einem Word-Dokument erstellen und anpassen. Indem Sie der Schritt-für-Schritt-Anleitung folgen, können Sie jetzt optisch ansprechende Diagramme erstellen, die Ihre Daten effektiv kommunizieren. Aspose.Words für .NET bietet eine breite Palette an Anpassungsoptionen, mit denen Sie Diagramme an Ihre spezifischen Anforderungen anpassen können.

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET verwenden, um andere Diagrammtypen zu erstellen?

 Ja, Aspose.Words für .NET unterstützt verschiedene Diagrammtypen, darunter Balkendiagramme, Kreisdiagramme und mehr. Sie können die Dokumentation erkunden[Hier](https://reference.aspose.com/words/net/) für weitere Details.

### Wie kann ich Aspose.Words für .NET vor dem Kauf ausprobieren?

 Sie können eine kostenlose Testversion herunterladen unter[Hier](https://releases.aspose.com/). So können Sie die Bibliothek und ihre Funktionen testen, bevor Sie einen Kauf tätigen.

### Gibt es eine Möglichkeit, Support zu erhalten, wenn ich auf Probleme stoße?

 Absolut. Sie können über die Aspose-Community-Foren auf Support zugreifen[Hier](https://forum.aspose.com/c/words/8)Die Community und die Mitarbeiter von Aspose reagieren sehr schnell.

### Wie kaufe ich eine Lizenz für Aspose.Words für .NET?

 Sie können eine Lizenz direkt von der Aspose-Website erwerben[Hier](https://purchase.aspose.com/buy). Es gibt verschiedene Lizenzierungsoptionen für unterschiedliche Anforderungen.

### Was ist, wenn ich für ein kurzfristiges Projekt eine vorübergehende Lizenz benötige?

 Aspose bietet temporäre Lizenzen an, die Sie anfordern können[Hier](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
