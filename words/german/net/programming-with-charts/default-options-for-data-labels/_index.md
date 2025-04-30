---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Standardoptionen für Datenbeschriftungen in einem Diagramm festlegen. Folgen Sie unserer Schritt-für-Schritt-Anleitung, um mühelos Diagramme zu erstellen und anzupassen."
"linktitle": "Festlegen von Standardoptionen für Datenbeschriftungen in einem Diagramm"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Festlegen von Standardoptionen für Datenbeschriftungen in einem Diagramm"
"url": "/de/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Festlegen von Standardoptionen für Datenbeschriftungen in einem Diagramm

## Einführung

Hallo! Tauchen Sie ein in die Welt der Dokumentenautomatisierung? Heute zeigen wir Ihnen, wie Sie mit Aspose.Words für .NET programmgesteuert beeindruckende Dokumente erstellen. Aspose.Words ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente mühelos bearbeiten können. In diesem Tutorial konzentrieren wir uns auf das Festlegen von Standardoptionen für Datenbeschriftungen in einem Diagramm. Egal, ob Sie erfahrener Entwickler oder Neuling sind – diese Anleitung führt Sie Schritt für Schritt durch die Arbeit, damit Sie im Handumdrehen einsatzbereit sind.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie für dieses Tutorial benötigen. Hier ist eine kurze Checkliste:

- Visual Studio oder eine andere .NET-kompatible IDE: Hier schreiben und führen Sie Ihren Code aus.
- Aspose.Words für .NET: Sie können [Laden Sie die neueste Version herunter](https://releases.aspose.com/words/net/) und installieren Sie es in Ihrem Projekt.
- Grundkenntnisse der C#-Programmierung: Obwohl dieses Handbuch anfängerfreundlich ist, sind einige Kenntnisse in C# hilfreich.
- .NET Framework installiert: Stellen Sie sicher, dass Sie das .NET Framework auf Ihrem Computer eingerichtet haben.
- Eine temporäre Lizenz für Aspose.Words: Holen Sie sich eine [Hier](https://purchase.aspose.com/temporary-license/) um die volle Funktionalität freizuschalten.

Sobald Sie diese Voraussetzungen erfüllt haben, können wir loslegen!

## Namespaces importieren

Zunächst richten wir unser Projekt ein und importieren die erforderlichen Namespaces. Diese Namespaces sind für den Zugriff auf die Aspose.Words-Funktionalität von entscheidender Bedeutung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Schritt 1: Erstellen Sie ein neues Dokument


Die Reise beginnt mit der Erstellung eines neuen Dokuments und der Initialisierung eines `DocumentBuilder`. Der `DocumentBuilder` Die Klasse bietet eine Reihe von Methoden zur einfachen Bearbeitung des Dokumentinhalts.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Erstellen eines neuen Dokuments
Document doc = new Document();

// DocumentBuilder initialisieren
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Erläuterung

In diesem Schritt haben wir das Dokument und den Builder eingerichtet, mit dem wir unseren Inhalt einfügen und formatieren. Die `dataDir` Die Variable enthält den Pfad, unter dem wir unser endgültiges Dokument speichern.

## Schritt 2: Einfügen eines Diagramms

Als nächstes fügen wir unserem Dokument ein Kreisdiagramm hinzu. Das `InsertChart` Methode der `DocumentBuilder` Klasse macht das super einfach.

```csharp
// Einfügen eines Kreisdiagramms
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Greifen Sie auf das Diagrammobjekt zu
Chart chart = shape.Chart;
```

### Erläuterung

Hier fügen wir ein Kreisdiagramm in unser Dokument ein. Das `InsertChart` Die Methode benötigt den Diagrammtyp, die Breite und die Höhe als Parameter. Nach dem Einfügen des Diagramms greifen wir auf das Diagrammobjekt zu, um es weiter zu bearbeiten.

## Schritt 3: Anpassen der Diagrammserie

Jetzt löschen wir alle vorhandenen Reihen im Diagramm und fügen unsere benutzerdefinierten Reihen hinzu. Diese Reihen repräsentieren unsere Datenpunkte.

```csharp
// Vorhandene Diagrammreihen löschen
chart.Series.Clear();

// Neue Reihen zum Diagramm hinzufügen
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Erläuterung

In diesem Schritt stellen wir sicher, dass unser Diagramm leer ist, indem wir alle vorhandenen Reihen löschen. Anschließend fügen wir eine neue Reihe mit benutzerdefinierten Kategorien und Werten hinzu, die in unserem Kreisdiagramm angezeigt wird.

## Schritt 4: Standardoptionen für Datenbeschriftungen festlegen

Datenbeschriftungen sind entscheidend für die Aussagekraft Ihres Diagramms. Wir legen Optionen für die Anzeige von Prozentwerten und Werten fest und passen das Trennzeichen an.

```csharp
// Zugriff auf die Sammlung von Datenbeschriftungen
ChartDataLabelCollection labels = series.DataLabels;

// Festlegen von Datenbeschriftungsoptionen
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Erläuterung

Hier greifen wir auf die `DataLabels` Eigenschaft unserer Serie, um das Erscheinungsbild und die auf jedem Datenetikett angezeigten Informationen anzupassen. Wir haben uns entschieden, sowohl den Prozentsatz als auch den Wert anzuzeigen, Führungslinien auszublenden und ein benutzerdefiniertes Trennzeichen festzulegen.

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir unser Dokument im angegebenen Verzeichnis. Dadurch stellen wir sicher, dass alle Änderungen in eine Datei geschrieben werden.

```csharp
// Speichern des Dokuments
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Erläuterung

Im letzten Schritt speichern wir unser Dokument mit dem `Save` Das Dokument wird in dem durch `dataDir`, mit dem Namen „WorkingWithCharts.DefaultOptionsForDataLabels.docx“.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein Word-Dokument mit einem benutzerdefinierten Kreisdiagramm mit Aspose.Words für .NET erstellt. Diese leistungsstarke Bibliothek vereinfacht die Automatisierung der Dokumenterstellung und -bearbeitung und spart Ihnen Zeit und Mühe. Egal, ob Sie Berichte, Rechnungen oder andere Dokumente erstellen – Aspose.Words unterstützt Sie dabei.

Erkunden Sie die [Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) für weitere Funktionen und Beispiele. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich Aspose.Words kostenlos nutzen?
Sie können Aspose.Words kostenlos nutzen mit einem [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) oder erkunden Sie die Funktionen mithilfe des [kostenlose Testversion](https://releases.aspose.com/).

### Wie erhalte ich Support für Aspose.Words?
Unterstützung erhalten Sie durch die [Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).

### Kann ich andere Diagrammtypen hinzufügen?
Ja, Aspose.Words unterstützt verschiedene Diagrammtypen wie Balken-, Linien- und Säulendiagramme. Überprüfen Sie die [Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words ist mit .NET Core kompatibel. Weitere Informationen finden Sie im [Dokumentation](https://reference.aspose.com/words/net/).

### Wie kann ich eine Lizenz für Aspose.Words erwerben?
Sie können eine Lizenz erwerben bei der [Aspose-Laden](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}