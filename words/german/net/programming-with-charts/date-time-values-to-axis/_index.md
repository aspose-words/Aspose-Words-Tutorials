---
"description": "Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Datums- und Zeitwerte zur Achse eines Diagramms hinzufügen."
"linktitle": "Hinzufügen von Datums- und Zeitwerten zur Achse eines Diagramms"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Hinzufügen von Datums- und Zeitwerten zur Achse eines Diagramms"
"url": "/de/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hinzufügen von Datums- und Zeitwerten zur Achse eines Diagramms

## Einführung

Das Erstellen von Diagrammen in Dokumenten kann eine leistungsstarke Möglichkeit zur Datenvisualisierung sein. Bei Zeitreihendaten ist das Hinzufügen von Datums- und Zeitwerten zu den Achsen eines Diagramms entscheidend für die Übersichtlichkeit. In diesem Tutorial führen wir Sie durch das Hinzufügen von Datums- und Zeitwerten zu den Achsen eines Diagramms mit Aspose.Words für .NET. Diese Schritt-für-Schritt-Anleitung hilft Ihnen, Ihre Umgebung einzurichten, den Code zu schreiben und jeden Teil des Prozesses zu verstehen. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Visual Studio oder eine beliebige .NET-IDE: Sie benötigen eine Entwicklungsumgebung zum Schreiben und Ausführen Ihres .NET-Codes.
2. Aspose.Words für .NET: Sie sollten die Bibliothek Aspose.Words für .NET installiert haben. Sie können sie herunterladen von [Hier](https://releases.aspose.com/words/net/).
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.
4. Eine gültige Aspose-Lizenz: Sie können eine temporäre Lizenz erhalten von [Hier](https://purchase.aspose.com/temporary-license/).

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Dieser Schritt ist entscheidend für den Zugriff auf die Aspose.Words-Klassen und -Methoden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zuerst müssen Sie das Verzeichnis definieren, in dem Ihr Dokument gespeichert wird. Dies ist wichtig für die Organisation Ihrer Dateien und die korrekte Ausführung Ihres Codes.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Erstellen Sie ein neues Dokument und einen neuen DocumentBuilder

Als nächstes erstellen Sie eine neue Instanz des `Document` Klasse und eine `DocumentBuilder` Objekt. Diese Objekte helfen Ihnen beim Erstellen und Bearbeiten Ihres Dokuments.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Einfügen eines Diagramms in das Dokument

Fügen Sie nun ein Diagramm in Ihr Dokument ein, indem Sie das `DocumentBuilder` Objekt. In diesem Beispiel verwenden wir ein Säulendiagramm, Sie können aber auch andere Typen auswählen.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Schritt 4: Vorhandene Serien löschen

Löschen Sie alle vorhandenen Reihen im Diagramm, um sicherzustellen, dass Sie mit einer leeren Tafel beginnen. Dieser Schritt ist für benutzerdefinierte Daten unerlässlich.

```csharp
chart.Series.Clear();
```

## Schritt 5: Datums- und Zeitwerte zur Reihe hinzufügen

Fügen Sie Ihre Datums- und Zeitwerte zur Diagrammreihe hinzu. In diesem Schritt erstellen Sie Arrays für Datumsangaben und entsprechende Werte.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Schritt 6: Konfigurieren Sie die X-Achse

Legen Sie die Skalierung und die Markierungen für die X-Achse fest. So stellen Sie sicher, dass Ihre Daten korrekt und in den richtigen Intervallen angezeigt werden.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Schritt 7: Speichern Sie das Dokument

Speichern Sie Ihr Dokument abschließend im angegebenen Verzeichnis. Damit ist der Vorgang abgeschlossen. Ihr Dokument sollte nun ein Diagramm mit Datums- und Zeitwerten auf der X-Achse enthalten.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Abschluss

Das Hinzufügen von Datums- und Zeitwerten zu den Achsen eines Diagramms in einem Dokument ist mit Aspose.Words für .NET ein unkomplizierter Vorgang. Mit den in diesem Tutorial beschriebenen Schritten erstellen Sie übersichtliche und informative Diagramme, die Zeitreihendaten effektiv visualisieren. Ob Sie Berichte, Präsentationen oder andere Dokumente erstellen, die eine detaillierte Datendarstellung erfordern – Aspose.Words bietet Ihnen die Werkzeuge, die Sie für Ihren Erfolg benötigen.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET andere Diagrammtypen verwenden?

Ja, Aspose.Words unterstützt verschiedene Diagrammtypen, darunter Linien-, Balken-, Kreisdiagramme und mehr.

### Wie kann ich das Erscheinungsbild meines Diagramms anpassen?

Sie können das Erscheinungsbild anpassen, indem Sie auf die Eigenschaften des Diagramms zugreifen und Stile, Farben und mehr festlegen.

### Ist es möglich, einem Diagramm mehrere Reihen hinzuzufügen?

Absolut! Sie können Ihrem Diagramm mehrere Serien hinzufügen, indem Sie die `Series.Add` Methode mehrmals mit unterschiedlichen Daten.

### Was ist, wenn ich die Diagrammdaten dynamisch aktualisieren muss?

Sie können die Diagrammdaten dynamisch aktualisieren, indem Sie die Reihen- und Achseneigenschaften programmgesteuert entsprechend Ihren Anforderungen bearbeiten.

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?

Eine ausführlichere Dokumentation finden Sie [Hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}