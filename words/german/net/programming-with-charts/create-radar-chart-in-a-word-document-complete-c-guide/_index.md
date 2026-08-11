---
category: general
date: 2026-08-10
description: Erstellen Sie schnell ein Radar‑Diagramm und lernen Sie, wie Sie das
  Diagramm mit Aspose.Words in ein Word‑Dokument einfügen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung
  für zuverlässige Ergebnisse.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- insert chart into word document
- how to insert radar chart
language: de
lastmod: 2026-08-10
og_description: Erstellen Sie ein Radar‑Diagramm in einer Word‑Datei mit Aspose.Words.
  Dieser Leitfaden zeigt, wie man ein Diagramm in ein Word‑Dokument einfügt und es
  für eine klare Darstellung anpasst.
og_image_alt: Radar chart created in a Word document using Aspose.Words
og_title: Radar-Diagramm in Word erstellen – vollständige C#‑Implementierung
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  headline: create radar chart in a Word document – complete C# guide
  type: TechArticle
- description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  name: create radar chart in a Word document – complete C# guide
  steps:
  - name: Set up the project and add Aspose.Words
    text: '1. Open a new Console App project in Visual Studio. 2. Add the Aspose.Words
      package via NuGet:'
  - name: Create a blank document and a builder
    text: A `Document` represents the .docx file, while `DocumentBuilder` provides
      methods to add content.
  - name: Insert radar chart and obtain the Chart object
    text: The `InsertChart` method inserts a chart placeholder and returns a `Shape`.
      Access the underlying `Chart` to modify its settings.
  - name: Enable graduations on both axes for better readability
    text: Graduations (tick marks) improve data interpretation, especially on radar
      charts where radial spacing matters.
  - name: Define the data series for the radar chart
    text: A radar chart requires a category axis (labels) and one or more data series.
      The example adds a single series named *Series 1*.
  - name: Save the document containing the radar chart
    text: Choose a folder where the output should reside. The file extension `.docx`
      ensures compatibility with Microsoft Word, Google Docs, and LibreOffice.
  type: HowTo
tags:
- Aspose.Words
- C#
- Radar chart
- Word automation
title: Radar-Diagramm in einem Word‑Dokument erstellen – vollständige C#‑Anleitung
url: /de/net/programming-with-charts/create-radar-chart-in-a-word-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radar‑Diagramm in einem Word‑Dokument erstellen – vollständige C#‑Anleitung

Wenn Sie ein **Radar‑Diagramm** in einer Word‑Datei erstellen müssen, zeigt Ihnen dieses Tutorial die genauen Schritte. Sie sehen, wie Sie **ein Diagramm in ein Word‑Dokument einfügen** mit Aspose.Words, Achsenbeschriftungen konfigurieren und Datenreihen hinzufügen, sodass das Diagramm fertig für die Präsentation ist.

Das programmgesteuerte Erzeugen eines Radar‑Diagramms eliminiert den manuellen Aufwand für das Zeichnen von Formen und das Ausrichten von Daten. Am Ende dieses Leitfadens können Sie **wie man ein Radar‑Diagramm einfügt** in jede .docx‑Datei, sein Aussehen anpassen und das Ergebnis mit einer einzigen Codezeile speichern.

## Voraussetzungen

* .NET 6.0 oder höher installiert  
* Visual Studio 2022 (oder ein beliebiger C#‑Editor)  
* Eine Aspose.Words‑für‑.NET‑Lizenz (die kostenlose Testversion funktioniert für Evaluierungen)  

Es sind keine zusätzlichen NuGet‑Pakete über `Aspose.Words` hinaus erforderlich. Der Code läuft unter Windows, macOS und Linux, da Aspose.Words plattformübergreifend ist.

## Wie man ein Radar‑Diagramm in einem Word‑Dokument erstellt

Dieser Abschnitt führt jede für das **Erstellen eines Radar‑Diagramms** von Grund auf erforderliche Operation aus. Der Ansatz folgt dem typischen Workflow, den Aspose.Words empfiehlt: ein `Document` erstellen, ein `DocumentBuilder` erhalten, das Diagramm einfügen, seine Eigenschaften konfigurieren und schließlich die Datei speichern.

### Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

1. Öffnen Sie ein neues Konsolen‑App‑Projekt in Visual Studio.  
2. Fügen Sie das Aspose.Words‑Paket über NuGet hinzu:

```bash
dotnet add package Aspose.Words
```

3. Wenn Sie eine Lizenzdatei besitzen, laden Sie sie zu Beginn von `Main`, um Evaluations‑Wasserzeichen zu vermeiden:

```csharp
// Load license (optional)
Aspose.Words.License license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

**Warum das wichtig ist:** Das Laden der Lizenz deaktiviert das Evaluationsbanner und schaltet die vollständigen Diagramm‑Render‑Funktionen frei.

### Schritt 2: Ein leeres Dokument und einen Builder erstellen

Ein `Document` repräsentiert die .docx‑Datei, während `DocumentBuilder` Methoden zum Hinzufügen von Inhalten bereitstellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new empty document
Document document = new Document();

// Obtain a builder linked to the document
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

**Erklärung:** Der Builder funktioniert wie ein Cursor; jeder Einfügebefehl schreibt an der aktuellen Position. Der Start mit einem leeren Dokument stellt sicher, dass das Radar‑Diagramm das erste visuelle Element ist.

### Schritt 3: Radar‑Diagramm einfügen und das Chart‑Objekt erhalten

Die Methode `InsertChart` fügt einen Diagramm‑Platzhalter ein und gibt ein `Shape` zurück. Greifen Sie auf das zugrunde liegende `Chart` zu, um dessen Einstellungen zu ändern.

```csharp
// Insert a radar chart of 400x300 points
Chart radarChart = docBuilder.InsertChart(ChartType.Radar, 400, 300).Chart;
```

**Warum das funktioniert:** `ChartType.Radar` weist Aspose.Words an, ein Radar‑(Spinnennetz‑)Diagramm zu erzeugen. Die Größenparameter bestimmen den visuellen Fußabdruck auf der Seite.

### Schritt 4: Graduierungen auf beiden Achsen aktivieren für bessere Lesbarkeit

Graduierungen (Tick‑Marks) verbessern die Dateninterpretation, besonders bei Radar‑Diagrammen, bei denen der radiale Abstand entscheidend ist.

```csharp
// Enable graduations on the radial (X) axis
radarChart.AxisX.HasGraduations = true;
radarChart.AxisX.GraduationLineStyle = LineStyle.Thick;

// Enable graduations on the value (Y) axis
radarChart.AxisY.HasGraduations = true;
radarChart.AxisY.GraduationLineStyle = LineStyle.Thick;
```

**Pro‑Tipp:** Die Verwendung von `LineStyle.Thick` lässt die Tick‑Marks hervorstechen, wenn das Dokument gedruckt oder auf hochauflösenden Bildschirmen angezeigt wird.

### Schritt 5: Datenreihen für das Radar‑Diagramm definieren

Ein Radar‑Diagramm benötigt eine Kategorien‑Achse (Beschriftungen) und eine oder mehrere Datenreihen. Das Beispiel fügt eine einzelne Reihe mit dem Namen *Series 1* hinzu.

```csharp
// Remove any default series
radarChart.Series.Clear();

// Add a new series with three categories
radarChart.Series.Add(
    "Series 1",                     // Series name
    new[] { "A", "B", "C" },        // Category labels
    new[] { 10, 20, 15 }            // Corresponding values
);
```

**Erklärung:** `Series.Add` ordnet jeder Beschriftung einen numerischen Wert zu. Das Diagramm verbindet die Punkte automatisch und bildet die charakteristische Spinnennetz‑Form.

### Schritt 6: Das Dokument mit dem Radar‑Diagramm speichern

Wählen Sie einen Ordner, in dem die Ausgabe abgelegt werden soll. Die Dateierweiterung `.docx` gewährleistet die Kompatibilität mit Microsoft Word, Google Docs und LibreOffice.

```csharp
// Save the document with the radar chart
document.Save("RadialChartGraduations.docx");
```

Nach dem Ausführen des Programms öffnen Sie `RadialChartGraduations.docx`. Sie sehen ein Radar‑Diagramm mit dicken Graduierungen auf beiden Achsen und die Datenreihe als geschlossenen Polygon.

![Radar-Diagramm mit Graduierungen](/images/radar-chart.png){: .align-center alt="Radar-Diagramm, erstellt in einem Word-Dokument mit Aspose.Words" }

**Erwartete Ausgabe:**  

* Ein einseitiges Word‑Dokument.  
* Ein 400 × 300 Punkt Radar‑Diagramm, zentriert auf der Seite.  
* Dicke Tick‑Marks auf der radialen und Wert‑Achse.  
* Eine Datenreihe mit der Bezeichnung „Series 1“ und den Werten 10, 20, 15.

## Wie man ein Diagramm in ein Word‑Dokument einfügt – zusätzliche Anpassungen

Während die Kernschritte oben **wie man ein Radar‑Diagramm einfügt** beantworten, benötigen Sie häufig weitere Feinjustierungen:

| Anpassung | Code‑Snippet | Wann verwenden |
|---|---|---|
| Diagrammtitel ändern | `radarChart.Title.Text = "Performance Overview";` | Um den Lesern Kontext zu geben |
| Hintergrundfarbe festlegen | `radarChart.ChartArea.FillFormat.Color = Color.LightYellow;` | Für Branding oder visuellen Kontrast |
| Eine zweite Datenreihe hinzufügen | `radarChart.Series.Add("Series 2", new[] {"A","B","C"}, new[] {12,18,22});` | Beim Vergleich mehrerer Datensätze |
| Achsenbegrenzungen anpassen | `radarChart.AxisY.Minimum = 0; radarChart.AxisY.Maximum = 30;` | Um das Diagramm innerhalb eines bekannten Bereichs zu halten |

Diese Snippets können nach **Schritt 5** und vor dem Speichern des Dokuments eingefügt werden. Sie illustrieren gängige Variationen, nach denen Entwickler suchen, wenn sie nach **ein Diagramm in ein Word‑Dokument einfügen** suchen.

## Häufige Fallstricke und wie man sie vermeidet

* **Fehlende Lizenz** – Das Diagramm wird gerendert, aber ein Evaluations‑Wasserzeichen erscheint. Laden Sie früh im `Main` eine gültige Lizenz.  
* **Falsche Diagrammgröße** – Die Verwendung von Pixelwerten statt Punkten führt zu verzerrter Ausgabe. Aspose.Words erwartet Punkte (1 pt ≈ 1/72 in).  
* **Leere Datenreihe** – Das Vergessen von `Series.Clear()` kann Platzhalterdaten hinterlassen, die Ihre benutzerdefinierte Reihe überschreiben.  

Die Behebung dieser Punkte stellt sicher, dass das Radar‑Diagramm exakt wie gewünscht erscheint.

## Fazit

Sie wissen jetzt, wie Sie **ein Radar‑Diagramm** in einer Word‑Datei mit Aspose.Words für .NET **erstellen**. Das Tutorial hat jeden Schritt von der Projekt‑Einrichtung bis zum Speichern des finalen Dokuments behandelt, gezeigt **wie man ein Radar‑Diagramm einfügt** und demonstriert **wie man ein Diagramm in ein Word‑Dokument einfügt** mit Achsen‑Graduierungen und benutzerdefinierten Daten. Experimentieren Sie mit zusätzlichen Reihen, Titeln und Stiloptionen, um das Diagramm an Ihre Reporting‑Bedürfnisse anzupassen.

**Nächste Schritte**

* Erkunden Sie weitere Diagrammtypen (`ChartType.Pie`, `ChartType.Column`), um Ihr Automatisierungs‑Toolkit zu erweitern.  
* Kombinieren Sie die Diagrammerstellung mit Seriendruck für personalisierte Berichte.  
* Lesen Sie die Aspose.Words‑Dokumentation zur Diagrammformatierung für erweiterte Stiloptionen.  

Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Flächendiagramm in Word‑Dokument einfügen | Aspose.Words für .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Säulendiagramm in Word einfügen mit Aspose.Words für .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Scatter‑Diagramm in Word erstellen mit Aspose.Words für .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}