---
category: general
date: 2026-06-02
description: Diagrammlegende in einem Word-Dokument mit C# anzeigen. Erfahren Sie,
  wie Sie eine Legende hinzufügen, vordefinierte Diagramm‑Stile anwenden und die Diagramm‑Visualisierung
  in Word in wenigen Minuten anpassen.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: de
og_description: Diagrammlegende sofort in einem Word-Dokument anzeigen. Diese Anleitung
  führt Sie durch das Hinzufügen einer Legende, das Anwenden eines vordefinierten
  Diagramm‑Stils und den Umgang mit Sonderfällen.
og_title: Diagrammlegende in Word anzeigen – Vollständiges C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Diagrammlegende in Word mit C# anzeigen – Vollständige Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagrammlegende in Word mit C# anzeigen – Vollständige Schritt‑für‑Schritt‑Anleitung

Haben Sie sich jemals gefragt, **wie man einer Grafik**, die in einem Word‑Dokument eingebettet ist, **eine Legende hinzufügt**? Sie sind nicht allein. In vielen Berichten lässt eine fehlende Legende die Daten kryptisch wirken, und das Beheben sollte kein Kopfzerbrechen sein.  

In diesem Tutorial zeigen wir, wie man **die Diagrammlegende** in einer Word‑Datei mit Aspose.Words für .NET anzeigt, einen vordefinierten Diagrammstil anwendet und sicherstellt, dass die Legende genau dort erscheint, wo Sie sie benötigen. Am Ende haben Sie ein einsatzbereites Beispiel, das Sie in jedes C#‑Projekt einbinden können.

## Was dieser Leitfaden abdeckt

Wir gehen den gesamten Workflow durch:

1. Laden einer bestehenden *.docx*‑Datei, die bereits ein Diagramm enthält.  
2. Das erste Diagramm (oder ein beliebiges Ziel‑Diagramm) abrufen.  
3. **Vordefinierten Diagrammstil anwenden**, um dem Diagramm ein professionelles Aussehen zu verleihen.  
4. **Diagrammlegende anzeigen**, sie rechts positionieren und Sonderfälle wie Wasserfalldiagramme behandeln.  
5. Das geänderte Dokument speichern.

Keine externen Werkzeuge, kein manuelles Herumbasteln an der UI – nur reiner Code. Die einzige Voraussetzung ist ein Verweis auf das Aspose.Words‑NuGet‑Paket (Version 23.10 oder höher) und ein Grundverständnis von C#.

---

## Voraussetzungen

- .NET 6.0 oder höher (das Beispiel funktioniert auch mit .NET Framework 4.7.2).  
- Aspose.Words für .NET Bibliothek installiert (`Install-Package Aspose.Words`).  
- Eine Word‑Datei (`input.docx`), die bereits mindestens ein Diagramm enthält.  
- Visual Studio, Rider oder eine beliebige IDE Ihrer Wahl.

---

## Schritt 1: Projekt einrichten und Dokument laden

Zuerst erstellen Sie eine Konsolen‑App (oder integrieren den Code in ein bestehendes Projekt). Fügen Sie die `using`‑Direktiven hinzu und laden Sie die `.docx`‑Datei.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Warum das wichtig ist:** Das Laden des Dokuments ist die Grundlage. Ohne eine `Document`‑Instanz können Sie nicht auf die Diagramm‑Objekte zugreifen, die Aspose.Words bereitstellt.

---

## Schritt 2: Ziel‑Diagramm abrufen

Diagramme werden als Knoten im Dokumenten‑Baum gespeichert. Die Methode `GetChild` führt eine Tiefensuche durch, sodass wir das erste Diagramm unabhängig davon finden, wo es sich befindet (Kopfzeile, Hauptteil, Fußzeile usw.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tipp:** Wenn Sie mehrere Diagramme haben, ändern Sie den Index `0` zu `1`, `2`, … oder iterieren Sie über `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Schritt 3: Vordefinierten visuellen Stil anwenden

Ein gut aussehendes Diagramm beginnt häufig mit einem Stil. Aspose.Words liefert Dutzende integrierter Stile; `ChartStyle.Style12` ist eine saubere, moderne Option.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Wie es funktioniert:** Die Eigenschaft `Style` verweist auf die integrierten Word‑Diagramm‑Stile, die Sie in der Benutzeroberfläche sehen. Die Auswahl eines Voreinstellungs‑Stils erspart Ihnen das manuelle Setzen von Farben, Schriftarten und Markern.

---

## Schritt 4: Legende aktivieren und positionieren

Jetzt zum Star des Show‑Falls – **Diagrammlegende anzeigen**. Wir schalten die Legende ein und docken sie an die rechte Seite des Diagramms.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Warum rechts?** Das Platzieren der Legende rechts lässt den Datenbereich breit, was besonders bei Balken‑ oder Säulendiagrammen hilfreich ist.

---

## Schritt 5: Wasserfalldiagramme behandeln (Sonderfall)

Wasserfalldiagramme verhalten sich etwas anders; die Legende kann standardmäßig ausgeblendet sein. Die folgende Guard‑Clause stellt sicher, dass die Legende sichtbar ist, wenn der Diagrammtyp Wasserfall ist.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Hinweis zum Randfall:** Einige ältere Word‑Versionen ignorieren `HasLegend` bei Wasserfalldiagrammen, sodass das explizite Setzen von `Legend.Show` die Sichtbarkeit garantiert.

---

## Schritt 6: Das geänderte Dokument speichern

Zum Schluss schreiben Sie die Änderungen zurück auf die Festplatte. Sie können die Originaldatei überschreiben oder eine neue Datei erstellen.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Das Ausführen des Programms erzeugt `output.docx` mit einer sichtbaren Legende rechts, formatiert mit `Style12`. Öffnen Sie die Datei in Word, um das Ergebnis zu prüfen.

---

## Vollständiges funktionierendes Beispiel (Alle Schritte kombiniert)

Unten finden Sie den kompletten, sofort ausführbaren Code. Kopieren Sie ihn nach `Program.cs` (oder in eine beliebige C#‑Datei) und passen Sie die Dateipfade an.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Erwartete Ausgabe:** Beim Öffnen von `output.docx` wird das ursprüngliche Diagramm mit einer rechtsbündigen Legende, formatiert mit dem modernen `Style12`, angezeigt. Alle Datenreihen sind klar beschriftet, sodass das Diagramm sofort verständlich ist.

---

## Häufig gestellte Fragen (FAQ)

### Wie füge ich einer bestimmten Grafik (nicht der ersten) eine Legende hinzu?

Ersetzen Sie den Index `0` in `GetChild(NodeType.Chart, 0, true)` durch die nullbasierte Position Ihrer Ziel‑Grafik oder durchlaufen Sie alle Diagrammknoten:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Kann ich die Legende unten statt rechts platzieren?

Natürlich. Ändern Sie einfach das `LegendPosition`‑Enum:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Was tun, wenn das Diagramm bereits eine Legende hat, ich sie aber ausblenden möchte?

Setzen Sie `HasLegend` auf `false`:

```csharp
chart.HasLegend = false;
```

### Funktioniert das mit Word 2010, 2016 und neueren Versionen?

Ja. Aspose.Words abstrahiert die zugrunde liegende Word‑Version, sodass derselbe Code mit allen modernen .docx‑Dateien funktioniert.

---

## Pro‑Tipps & häufige Stolperfallen

- **Pro‑Tipp:** Nach dem Anwenden eines Stils können Sie einzelne Elemente (Farben, Datenbeschriftungen) über die `Chart.Series`‑Sammlung weiter anpassen. Der Stil liefert Ihnen eine solide Basis.  
- **Achten Sie auf:** Befindet sich das Diagramm in einer Tabellenzelle, kann die Legende beengt wirken. Erwägen Sie, die Diagrammgröße (`chart.Width`, `chart.Height`) zu erhöhen, bevor Sie die Legende positionieren.  
- **Leistungshinweis:** Das Laden großer Dokumente (Hunderte MB) kann speicherintensiv sein. Verwenden Sie `LoadOptions` mit `LoadFormat.Docx`, um den Aufwand zu reduzieren, wenn Sie nur Diagramme bearbeiten müssen.

---

## Nächste Schritte

Jetzt, wo Sie **wissen, wie man eine Legende hinzufügt** und **einen vordefinierten Diagrammstil anwendet** in Word, können Sie Folgendes erkunden:

- **Benutzerdefinierte Diagramm‑Farben** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formatierung von Datenbeschriftungen** (`chart.Series[i].HasDataLabel = true`).  
- **Export des Diagramms als Bild** (`chart.ToImage()`), nützlich für die Einbettung an anderer Stelle.  

All diese Themen bauen auf demselben Objektmodell auf, sodass die Lernkurve sanft verläuft.

---

## Fazit

Wir haben gerade eine saubere End‑zu‑End‑Lösung für **Diagrammlegende in einem Word‑Dokument** mit C# demonstriert. Durch das Laden des Dokuments, das Abrufen des Diagramms, das Anwenden eines vordefinierten Stils, das Aktivieren der Legende und das Behandeln von Wasserfall‑Sonderfällen erhalten Sie ein professionell aussehendes Diagramm, das in jedem Business‑Report eingesetzt werden kann.  

Experimentieren Sie gern mit anderen `ChartStyle`‑Werten oder Legenden‑Positionen – Ihre Datenvisualisierungen verdienen die beste Präsentation. Wenn Sie auf Probleme stoßen, hinterlassen Sie einen Kommentar unten; happy coding!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Spalten‑Diagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-column-chart/)
- [Diagramm‑Achse in einem Word‑Dokument ausblenden](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Verwendung der Word‑Diagramm‑API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}