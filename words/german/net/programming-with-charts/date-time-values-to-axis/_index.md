---
title: Hinzufügen von Datums- und Uhrzeitwerten zu den Achsen eines Diagramms
linktitle: Hinzufügen von Datums- und Uhrzeitwerten zu den Achsen eines Diagramms
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Datums- und Uhrzeitwerte zur Achse eines Diagramms hinzufügen.
weight: 10
url: /de/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hinzufügen von Datums- und Uhrzeitwerten zu den Achsen eines Diagramms

## Einführung

Das Erstellen von Diagrammen in Dokumenten kann eine leistungsstarke Möglichkeit zur Visualisierung von Daten sein. Beim Umgang mit Zeitreihendaten ist das Hinzufügen von Datums- und Zeitwerten zur Achse eines Diagramms für die Übersichtlichkeit entscheidend. In diesem Tutorial führen wir Sie durch den Prozess des Hinzufügens von Datums- und Zeitwerten zur Achse eines Diagramms mithilfe von Aspose.Words für .NET. Diese Schritt-für-Schritt-Anleitung hilft Ihnen beim Einrichten Ihrer Umgebung, beim Schreiben des Codes und beim Verstehen jedes Teils des Prozesses. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Visual Studio oder eine beliebige .NET IDE: Sie benötigen eine Entwicklungsumgebung zum Schreiben und Ausführen Ihres .NET-Codes.
2.  Aspose.Words für .NET: Sie sollten die Bibliothek Aspose.Words für .NET installiert haben. Sie können sie herunterladen von[Hier](https://releases.aspose.com/words/net/).
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.
4.  Eine gültige Aspose-Lizenz: Sie erhalten eine temporäre Lizenz von[Hier](https://purchase.aspose.com/temporary-license/).

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Dieser Schritt ist für den Zugriff auf die Aspose.Words-Klassen und -Methoden von entscheidender Bedeutung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zuerst müssen Sie das Verzeichnis definieren, in dem Ihr Dokument gespeichert wird. Dies ist wichtig für die Organisation Ihrer Dateien und stellt sicher, dass Ihr Code korrekt ausgeführt wird.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Neues Dokument und DocumentBuilder erstellen

 Erstellen Sie als nächstes eine neue Instanz des`Document` Klasse und eine`DocumentBuilder` Objekt. Diese Objekte helfen Ihnen beim Erstellen und Bearbeiten Ihres Dokuments.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Einfügen eines Diagramms in das Dokument

 Fügen Sie nun ein Diagramm in Ihr Dokument ein, indem Sie das`DocumentBuilder` Objekt. In diesem Beispiel verwenden wir ein Säulendiagramm, Sie können aber auch andere Typen auswählen.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Schritt 4: Vorhandene Serien löschen

Löschen Sie alle vorhandenen Reihen im Diagramm, um sicherzustellen, dass Sie mit einer leeren Tafel beginnen. Dieser Schritt ist für benutzerdefinierte Daten unerlässlich.

```csharp
chart.Series.Clear();
```

## Schritt 5: Datums- und Zeitwerte zur Serie hinzufügen

Fügen Sie der Diagrammreihe Ihre Datums- und Zeitwerte hinzu. In diesem Schritt werden Arrays für Daten und entsprechende Werte erstellt.

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

Legen Sie die Skalierung und die Markierungen für die X-Achse fest. So stellen Sie sicher, dass Ihre Daten korrekt und in den richtigen Abständen angezeigt werden.

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

Speichern Sie abschließend Ihr Dokument im angegebenen Verzeichnis. Mit diesem Schritt ist der Vorgang abgeschlossen und Ihr Dokument sollte nun ein Diagramm mit Datums- und Zeitwerten auf der X-Achse enthalten.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Abschluss

Das Hinzufügen von Datums- und Zeitwerten zur Achse eines Diagramms in einem Dokument ist mit Aspose.Words für .NET ein unkomplizierter Vorgang. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie klare und informative Diagramme erstellen, die Zeitreihendaten effektiv visualisieren. Egal, ob Sie Berichte, Präsentationen oder ein anderes Dokument erstellen, das eine detaillierte Datendarstellung erfordert, Aspose.Words bietet die Tools, die Sie zum Erfolg benötigen.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET andere Diagrammtypen verwenden?

Ja, Aspose.Words unterstützt verschiedene Diagrammtypen, darunter Linien-, Balken-, Kreisdiagramme und mehr.

### Wie kann ich das Erscheinungsbild meines Diagramms anpassen?

Sie können das Erscheinungsbild anpassen, indem Sie auf die Eigenschaften des Diagramms zugreifen und Stile, Farben und mehr festlegen.

### Ist es möglich, einem Diagramm mehrere Reihen hinzuzufügen?

 Auf jeden Fall! Sie können Ihrem Diagramm mehrere Serien hinzufügen, indem Sie den`Series.Add` Methode mehrmals mit unterschiedlichen Daten.

### Was ist, wenn ich die Diagrammdaten dynamisch aktualisieren muss?

Sie können die Diagrammdaten dynamisch aktualisieren, indem Sie die Serien- und Achseneigenschaften programmgesteuert entsprechend Ihren Anforderungen bearbeiten.

### Wo finde ich ausführlichere Dokumentation für Aspose.Words für .NET?

 Eine ausführlicHier Dokumentation finden Sie[here](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
