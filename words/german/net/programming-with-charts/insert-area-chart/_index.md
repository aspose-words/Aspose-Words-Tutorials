---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET ein Flächendiagramm in ein Dokument einfügen. Fügen Sie Seriendaten hinzu und speichern Sie das Dokument mit dem Diagramm."
"linktitle": "Flächendiagramm in ein Word-Dokument einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Flächendiagramm in ein Word-Dokument einfügen"
"url": "/de/net/programming-with-charts/insert-area-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Flächendiagramm in ein Word-Dokument einfügen

## Einführung

Willkommen zu dieser Schritt-für-Schritt-Anleitung zum Einfügen eines Flächendiagramms in ein Word-Dokument mit Aspose.Words für .NET. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen – dieses Tutorial führt Sie durch alles, was Sie wissen müssen, um beeindruckende und informative Flächendiagramme in Ihren Word-Dokumenten zu erstellen. Wir erklären die Voraussetzungen, zeigen Ihnen, wie Sie die erforderlichen Namespaces importieren, und führen Sie mit klaren, leicht verständlichen Anweisungen durch jeden Schritt des Prozesses.

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass Sie alles haben, was Sie für den Einstieg benötigen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
2. .NET Framework: Stellen Sie sicher, dass das .NET Framework auf Ihrem Computer installiert ist.
3. IDE: Eine integrierte Entwicklungsumgebung (IDE) wie Visual Studio zum Schreiben und Ausführen Ihres Codes.
4. Grundlegende C#-Kenntnisse: Ein grundlegendes Verständnis der C#-Programmierung ist hilfreich.

Sobald diese Voraussetzungen erfüllt sind, können Sie mit der Erstellung ansprechender Flächendiagramme in Ihren Word-Dokumenten beginnen.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Diese Namespaces stellen die Klassen und Methoden bereit, die für die Arbeit mit Word-Dokumenten und Diagrammen in Aspose.Words für .NET erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Nachdem wir nun die wesentlichen Namespaces importiert haben, können wir mit der Erstellung unseres Dokuments und dem schrittweisen Einfügen eines Flächendiagramms fortfahren.

## Schritt 1: Erstellen Sie ein neues Word-Dokument

Beginnen wir mit der Erstellung eines neuen Word-Dokuments. Dies dient als Grundlage für unser Flächendiagramm.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

In diesem Schritt initialisieren wir ein neues `Document` Objekt, das unser Word-Dokument darstellt.

## Schritt 2: Verwenden Sie DocumentBuilder zum Einfügen eines Diagramms

Als nächstes verwenden wir die `DocumentBuilder` Klasse, um ein Flächendiagramm in unser Dokument einzufügen.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

Hier erstellen wir eine `DocumentBuilder` Objekt und verwenden Sie es, um ein Flächendiagramm mit bestimmten Abmessungen (432 x 252) in unser Dokument einzufügen.

## Schritt 3: Zugriff auf das Diagrammobjekt

Nach dem Einfügen des Diagramms müssen wir auf die `Chart` Objekt, um unser Flächendiagramm anzupassen.

```csharp
Chart chart = shape.Chart;
```

Diese Codezeile ruft die `Chart` Objekt aus der Form, die wir gerade eingefügt haben.

## Schritt 4: Seriendaten zum Diagramm hinzufügen

Jetzt ist es an der Zeit, unserem Diagramm einige Daten hinzuzufügen. Wir fügen eine Reihe mit Datumsangaben und entsprechenden Werten hinzu.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

In diesem Schritt fügen wir eine Reihe mit dem Namen „Aspose Series 1“ mit einer Reihe von Daten und entsprechenden Werten hinzu.

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument mit dem eingefügten Flächendiagramm.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Diese Codezeile speichert das Dokument unter dem angegebenen Dateinamen im angegebenen Verzeichnis.

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Words für .NET erfolgreich ein Flächendiagramm in ein Word-Dokument eingefügt. Diese Anleitung hat Sie Schritt für Schritt durch die Einrichtung Ihrer Umgebung bis zum Speichern des fertigen Dokuments geführt. Mit Aspose.Words für .NET können Sie eine Vielzahl von Diagrammen und anderen komplexen Elementen in Ihren Word-Dokumenten erstellen und so Ihre Berichte und Präsentationen dynamischer und informativer gestalten.

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen verwenden?
Ja, Aspose.Words für .NET unterstützt andere .NET-Sprachen wie VB.NET.

### Ist es möglich, das Erscheinungsbild des Diagramms anzupassen?
Absolut! Aspose.Words für .NET bietet umfangreiche Optionen zur individuellen Gestaltung Ihrer Diagramme.

### Kann ich einem einzelnen Word-Dokument mehrere Diagramme hinzufügen?
Ja, Sie können so viele Diagramme wie nötig in ein einzelnes Word-Dokument einfügen.

### Unterstützt Aspose.Words für .NET andere Diagrammtypen?
Ja, Aspose.Words für .NET unterstützt verschiedene Diagrammtypen, darunter Balken-, Linien-, Kreisdiagramme und mehr.

### Wo kann ich eine temporäre Lizenz für Aspose.Words für .NET erhalten?
Eine vorläufige Lizenz erhalten Sie bei [Hier](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}