---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET ein Streudiagramm in Word einfügen. Einfache Schritte zum Integrieren visueller Datendarstellungen in Ihre Dokumente."
"linktitle": "Streudiagramm in Word-Dokument einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Streudiagramm in Word-Dokument einfügen"
"url": "/de/net/programming-with-charts/insert-scatter-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Streudiagramm in Word-Dokument einfügen

## Einführung

In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET ein Streudiagramm in Ihr Word-Dokument einfügen. Streudiagramme sind leistungsstarke visuelle Tools, die Datenpunkte basierend auf zwei Variablen effektiv darstellen und Ihre Dokumente ansprechender und informativer gestalten.

## Voraussetzungen

Bevor wir mit der Erstellung von Streudiagrammen mit Aspose.Words für .NET beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1. Installation von Aspose.Words für .NET: Laden Sie Aspose.Words für .NET herunter und installieren Sie es von [Hier](https://releases.aspose.com/words/net/).
   
2. Grundkenntnisse in C#: Kenntnisse der Programmiersprache C# und des .NET-Frameworks sind von Vorteil.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Lassen Sie uns nun den Vorgang zum Einfügen eines Streudiagramms in Ihr Word-Dokument mit Aspose.Words für .NET aufschlüsseln:

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Initialisieren Sie zunächst eine neue Instanz des `Document` Klasse und `DocumentBuilder` Klasse, um mit dem Erstellen Ihres Dokuments zu beginnen.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Einfügen des Streudiagramms

Verwenden Sie die `InsertChart` Methode der `DocumentBuilder` Klasse, um ein Streudiagramm in das Dokument einzufügen.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Schritt 3: Datenreihen zum Diagramm hinzufügen

Fügen Sie nun Datenreihen zu Ihrem Streudiagramm hinzu. Dieses Beispiel zeigt das Hinzufügen einer Reihe mit bestimmten Datenpunkten.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das geänderte Dokument abschließend am gewünschten Speicherort mit dem `Save` Methode der `Document` Klasse.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für .NET ein Streudiagramm in Ihr Word-Dokument einfügen. Streudiagramme eignen sich hervorragend zur Visualisierung von Datenbeziehungen. Mit Aspose.Words können Sie sie mühelos in Ihre Dokumente integrieren, um die Übersichtlichkeit und das Verständnis zu verbessern.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild des Streudiagramms mit Aspose.Words anpassen?
Ja, Aspose.Words ermöglicht eine umfassende Anpassung von Diagrammeigenschaften wie Farben, Achsen und Beschriftungen.

### Ist Aspose.Words mit verschiedenen Versionen von Microsoft Word kompatibel?
Aspose.Words unterstützt verschiedene Versionen von Microsoft Word und gewährleistet so plattformübergreifende Kompatibilität.

### Bietet Aspose.Words Unterstützung für andere Diagrammtypen?
Ja, Aspose.Words unterstützt eine breite Palette von Diagrammtypen, darunter Balkendiagramme, Liniendiagramme und Kreisdiagramme.

### Kann ich Daten im Streudiagramm programmgesteuert dynamisch aktualisieren?
Natürlich können Sie Diagrammdaten mithilfe von Aspose.Words-API-Aufrufen dynamisch aktualisieren.

### Wo kann ich weitere Hilfe oder Unterstützung für Aspose.Words erhalten?
Weitere Hilfe erhalten Sie auf der [Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}