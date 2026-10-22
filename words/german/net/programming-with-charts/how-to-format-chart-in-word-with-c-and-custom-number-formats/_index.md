---
category: general
date: 2026-10-13
description: Wie man ein Diagramm in Word mit C# formatiert, indem man ein benutzerdefiniertes
  Zahlenformat, z. B. Währung, auf die Diagrammachsen anwendet. Schritt‑für‑Schritt‑Codebeispiel
  enthalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: de
lastmod: 2026-10-13
og_description: Wie man Diagramme in Word mit C# formatiert, ermöglicht das Anwenden
  eines benutzerdefinierten Zahlenformats auf Diagrammachsen, sodass Werte als Währung,
  Prozentsätze oder jedes gewünschte Muster angezeigt werden. Folgen Sie der Schritt‑für‑Schritt‑Anleitung.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Diagramm in Word mit C# formatieren – benutzerdefinierte Zahlenformate
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Wie man ein Diagramm in Word mit C# und benutzerdefinierten Zahlenformaten
  formatiert
url: /de/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Diagramme in Word mit C# und benutzerdefinierten Zahlenformaten formatiert

Diagramme in Word mit C# zu formatieren ist ein häufiges Bedürfnis, wenn Sie Daten professionell präsentieren müssen. Dieser Leitfaden zeigt Ihnen, wie Sie ein benutzerdefiniertes Zahlenformat auf die Achse eines Diagramms anwenden, indem Sie **Aspose.Words for .NET** verwenden, sodass die Werte genau so erscheinen, wie Sie es erwarten.

Sie lernen, wie Sie eine DOCX‑Datei laden, das erste Diagramm finden, das aktuelle Format auslesen und dann ein neues Muster wie Währung mit zwei Dezimalstellen festlegen. Das Tutorial behandelt außerdem, wie Sie das Achsenformat für weitere Reihen ändern und das Format bei Bedarf zurücksetzen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher installiert  
* Ein Visual Studio 2022‑Projekt (oder ein beliebiges IDE, das .NET unterstützt)  
* Das **Aspose.Words for .NET** NuGet‑Paket (`Aspose.Words`)  
* Ein Word‑Dokument (`input.docx`), das mindestens ein Diagramm enthält

Sie können das Paket mit dem folgenden Befehl hinzufügen:

```bash
dotnet add package Aspose.Words
```

## Diagramm in Word mit Aspose.Words formatieren

Das folgende vollständige Programm demonstriert jeden Schritt, der erforderlich ist, um **Diagramm**‑Achsenwerte zu **formatieren**. Speichern Sie die Datei als `Program.cs` und führen Sie sie über die Befehlszeile oder Ihre IDE aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Erklärung jedes Schrittes

| Schritt | Warum es wichtig ist | Schlüsscode |
|------|-------------------|----------|
| **Dokument laden** | Sie benötigen ein `Document`‑Objekt, um mit der Word‑Datei zu arbeiten. | `new Document("input.docx")` |
| **Diagramm abrufen** | `Chart`‑Objekte werden als `Shape`‑Knoten gespeichert; das Casting ermöglicht die Verwendung diagrammspezifischer APIs. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Auf X‑Werte zugreifen** | Die Achsenformatierung wird auf die Wertsammlung einer Datenreihe angewendet. | `chart.ChartData.Series[0].XValues` |
| **Aktuelles Format lesen** | Das Wissen um den vorhandenen `FormatCode` hilft zu entscheiden, ob er ersetzt oder erweitert werden soll. | `xValues.FormatCode` |
| **Benutzerdefiniertes Format festlegen** | Die Eigenschaft `FormatCode` akzeptiert jedes Excel‑kompatible Muster und ermöglicht Währungen, Prozentsätze, Datumsangaben usw. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Dokument speichern** | Das Persistieren der Änderungen schreibt das neue Achsenformat zurück in die DOCX‑Datei. | `doc.Save("output_formatted.docx")` |

Das Ausführen des Programms erzeugt `output_formatted.docx`. Öffnen Sie die Datei in Word und Sie sehen, dass die X‑Achsenwerte des Diagramms als **$1,234.00**, **$2,345.00**, … angezeigt werden, anstatt als reine Zahlen.

## Benutzerdefiniertes Zahlenformat auf Diagrammachse anwenden

Wenn Sie ein **benutzerdefiniertes Zahlenformat** auf die Y‑Achse oder auf zusätzliche Reihen anwenden müssen, ist der Vorgang identisch – Sie richten sich nur an eine andere Sammlung:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro‑Tipp:** Verwenden Sie doppelte Anführungszeichen innerhalb des Format‑Strings, um Literalzeichen einzubetten (z. B. `"$"` für Währung). Escapen Sie die Anführungszeichen wie oben gezeigt.

## Benutzerdefiniertes Zahlenformat in Word – Umgang mit der Word‑Locale

Word respektiert die Locale des Dokuments beim Interpretieren von Zahlenformaten. Wenn das Dokument eine nicht‑US‑Locale verwendet, müssen Sie den Format‑String möglicherweise anpassen:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Das Testen des Formats in einem Dokument mit deutschen Spracheinstellungen bestätigt, dass die Werte als **€ 1.234,00** erscheinen.

## Diagrammeigenschaften programmgesteuert festlegen

Über die Achsenformatierung hinaus möchten Sie häufig **Diagramm**‑Titel, Legenden oder Datenbeschriftungen setzen. Hier ein kurzer Ausschnitt, der zeigt, wie ein Diagrammtitel gesetzt wird, nachdem die Achse formatiert wurde:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Die Kombination mit dem benutzerdefinierten Zahlenformat liefert Ihnen ein vollständig poliertes Diagramm, das bereit für Berichte ist.

## Diagrammachsenformat dynamisch basierend auf Benutzereingaben ändern

In realen Anwendungen können Sie Benutzern erlauben, zur Laufzeit ein Format auszuwählen. Die folgende Methode kapselt die Formatierungslogik:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Sie können `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` für Währung oder `SetAxisFormat(chart, 0, "0%")` für Prozentsätze aufrufen. Dieser Ansatz hält Ihren Hauptcode sauber und unterstützt zukünftige Erweiterungen.

## Randfälle und häufige Stolperfallen

| Situation | Worauf zu achten ist | Empfohlene Lösung |
|-----------|----------------------|-------------------|
| Dokument enthält **kein Diagramm** | `GetChild` gibt `null` zurück, was zu einer Cast‑Ausnahme führt. | Prüfen Sie vor dem Casten auf `null` (siehe Beispiel). |
| Mehrere Diagramme im selben Dokument | Der Code greift immer auf das erste Diagramm (`Index 0`) zu. | Durchlaufen Sie `doc.GetChildNodes(NodeType.Shape, true)` und filtern Sie nach `ShapeType.Chart`. |
| Reihen **ohne X‑Werte** (z. B. Kreisdiagramme) | Der Zugriff auf `XValues` kann eine `ArgumentOutOfRangeException` auslösen. | Stellen Sie sicher, dass `Series[i].XValues` nicht leer ist, bevor Sie formatieren. |
| Locale‑Mismatch | Das Währungssymbol kann falsch angezeigt werden. | Setzen Sie `xValues.FormatCode` explizit mit den passenden Locale‑Symbolen. |

## Erwartete Ausgabe

Nach dem Ausführen des Beispielprogramms öffnen Sie **output_formatted.docx**. Die X‑Achse des Diagramms sollte die Zahlen im gewählten benutzerdefinierten Format anzeigen. Für das Währungsbeispiel sehen die Achsenbeschriftungen folgendermaßen aus:

```
$1,000.00
$2,000.00
$3,000.00
```

Wenn Sie das Prozentformat auf Y‑Werte angewendet haben, erscheinen die Y‑Achsenbeschriftungen so:

```
10%
20%
30%
```

## Fazit

Dieses Tutorial hat Ihnen gezeigt, **wie man Diagramme** in Word mit C# **durch Anwenden eines benutzerdefinierten Zahlenformats** auf Achsenwerte formatiert. Sie verfügen nun über ein wiederverwendbares Muster zum Setzen von Währungen, Prozentsätzen oder anderen numerischen Mustern sowie über Anleitungen zum Umgang mit Locales, mehreren Reihen und dynamischen Benutzereingaben.

Als Nächstes könnten Sie **wie man Diagramm**‑Titel, Datenbeschriftungen oder sogar das Exportieren des Diagramms als Bild mit `ChartRenderer` erkunden. Diese Themen bauen direkt auf den hier behandelten Konzepten auf und helfen Ihnen, vollständig automatisierte Reporting‑Lösungen zu erstellen.

---

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden demonstrierten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Zahlenformat für Achsen in einem Diagramm](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Zahlformat von Datenbeschriftungen in einem Diagramm](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Sekundäre X‑Achse formatieren und Anzeigeeinheiten auf Tausend setzen in Word-Liniendiagrammen mit Aspose.Words für .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}