---
category: general
date: 2026-09-11
description: Tutorial zum Bearbeiten von Diagrammbeschriftungen, das zeigt, wie man
  die Position der Diagrammbeschriftung ändert, Diagrammdatenbeschriftungen anpasst,
  den Diagrammkategorienamen ausblendet und den Diagrammbeschriftungswert mit Aspose.Words
  anzeigt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: de
lastmod: 2026-09-11
og_description: Das Tutorial zum Bearbeiten von Diagrammbeschriftungen führt Sie durch
  das Ändern der Position von Diagrammbeschriftungen, das Anpassen von Diagrammdatenbeschriftungen,
  das Ausblenden des Diagrammkategorienamens und das Anzeigen des Diagrammbeschriftungswerts
  mit Aspose.Words für .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Tutorial zum Bearbeiten von Diagrammbeschriftungen – Word‑Diagrammbeschriftungen
  in C# anpassen
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Tutorial zum Bearbeiten von Diagrammbeschriftungen – Word‑Diagrammbeschriftungen
  in C# ändern
url: /de/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Edit chart label tutorial – modify Word chart labels in C#

Wenn Sie ein **Edit Chart Label Tutorial** für ein Word‑Dokument benötigen, zeigt Ihnen dieser Leitfaden genau, wie Sie die Position von Diagrammbeschriftungen ändern, Diagrammdatenbeschriftungen anpassen, den Diagrammkategorienamen ausblenden und den Diagrammbeschriftungswert anzeigen können – und das mit Aspose.Words für .NET. Sie erhalten ein vollständiges, ausführbares Beispiel, das Sie in jedes C#‑Projekt übernehmen können.

Die Arbeit mit Diagrammbeschriftungen ist ein häufiges Anliegen beim programmgesteuerten Erstellen von Berichten, Rechnungen oder Dashboards. Dieses Tutorial behandelt jeden Schritt – vom Laden des Dokuments bis zum Persistieren der Änderungen – sodass Sie gepflegte Diagramme ohne manuelle Nachbearbeitung erzeugen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher installiert  
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder einen temporären Evaluierungsschlüssel)  
* Visual Studio 2022 oder eine beliebige C#‑kompatible IDE  
* Eine Word‑Datei (`Chart.docx`), die mindestens ein Diagramm enthält  

Weitere NuGet‑Pakete sind über `Aspose.Words` hinaus nicht erforderlich.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie eine neue Konsolenanwendung und fügen Sie das Aspose.Words‑NuGet‑Paket hinzu:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Öffnen Sie `Program.cs` und importieren Sie die erforderlichen Namespaces:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Diese Namespaces geben Ihnen Zugriff auf die Klasse `Document` zum Umgang mit Word‑Dateien und die `Chart`‑Klassen zum Manipulieren von Diagrammelementen.

## Schritt 2: Das Word‑Dokument laden, das ein Diagramm enthält

Die erste ausführbare Zeile lädt das Quelldokument. Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Pfad, in dem sich `Chart.docx` befindet.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Das Laden des Dokuments erzeugt eine In‑Memory‑Repräsentation, die Sie traversieren und ändern können.

## Schritt 3: Das erste Diagramm im Dokument abrufen

Diagramme werden als Kindknoten des Typs `NodeType.Chart` gespeichert. Die Methode `GetChild` durchsucht den Dokumentbaum und gibt das Diagramm zurück, das Sie bearbeiten möchten.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Enthält das Dokument mehrere Diagramme, können Sie den Index ändern, um ein anderes Ziel auszuwählen.

## Schritt 4: Auf die Datenbeschriftung der ersten Serie zugreifen und sie anpassen

Jede Diagrammserie besitzt ein `DataLabel`‑Objekt, das steuert, wie die Beschriftung erscheint. Der nachfolgende Code demonstriert die vier wichtigsten Anpassungen, die im Tutorial gefordert werden.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Warum diese Einstellungen wichtig sind**

* `DataLabelPosition.Center` verschiebt die Beschriftung vom standardmäßigen Außen‑des‑Punkt‑Ort in die Mitte des Datenpunkts, wodurch das Diagramm leichter lesbar wird, wenn Punkte dicht beieinander liegen.  
* Das Festlegen eines benutzerdefinierten `Separator` ermöglicht die Kontrolle darüber, wie Serienname, Wert und weitere Teile verkettet werden.  
* Das Ausblenden des Kategorienamens (`ShowCategoryName = false`) reduziert visuelle Unordnung, wenn die Kategorie bereits aus der Achse ersichtlich ist.  
* Das Aktivieren von `ShowValue` stellt sicher, dass der tatsächliche Datenwert sichtbar ist – häufig erforderlich für Finanz‑ oder Statistikberichte.

## Schritt 5: Das geänderte Dokument speichern

Nachdem Sie die Beschriftungseigenschaften angepasst haben, speichern Sie die Änderungen in einer neuen Datei:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Die neue Datei (`CustomLabelChart.docx`) enthält dasselbe Diagrammlayout, jedoch mit der von Ihnen definierten Beschriftungsdarstellung.

## Vollständiger Quellcode

Im Folgenden finden Sie das komplette, sofort ausführbare Programm. Kopieren Sie es in `Program.cs`, passen Sie die Dateipfade an und führen Sie das Projekt aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Erwartetes Ergebnis

Öffnen Sie `CustomLabelChart.docx` in Microsoft Word. Sie sollten die Beschriftung der ersten Serie zentriert auf jedem Datenpunkt sehen, die nur den numerischen Wert anzeigt und “; ” als Trennzeichen verwendet. Die Kategorienamen werden nicht mehr neben den Werten angezeigt.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Was ist, wenn das Dokument kein Diagramm enthält?** | Das Beispiel prüft, ob das Diagramm `null` ist, und beendet das Programm mit einer aussagekräftigen Konsolennachricht. |
| **Kann ich Beschriftungen für mehrere Serien bearbeiten?** | Ja. Durchlaufen Sie `chart.Series` und wenden Sie dieselben `DataLabel`‑Einstellungen auf jede `Series[i].DataLabel` an. |
| **Wie ändere ich den Schriftstil der Beschriftung?** | Verwenden Sie `label.Font` (z. B. `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Wird `DataLabelPosition.Center` für alle Diagrammtypen unterstützt?** | Die meisten 2‑D‑Diagrammtypen unterstützen es. Bei 3‑D‑Diagrammen können einige Positionen von Word ignoriert werden. |
| **Benötige ich eine Lizenz für Aspose.Words?** | Der Evaluierungsmodus funktioniert, fügt jedoch ein Wasserzeichen hinzu. Eine Lizenz entfernt das Wasserzeichen und schaltet die volle Funktionalität frei. |

## Pro‑Tipps

* **Batch‑Verarbeitung:** Kapseln Sie die Lade‑ und Speicherlogik in einer Methode, die Eingabe‑ und Ausgabepfade entgegennimmt. So können Sie Dutzende Dokumente in einer Schleife verarbeiten.  
* **Performance:** Verwenden Sie eine einzige `Document`‑Instanz, wenn Sie mehrere Diagramme in derselben Datei ändern, um wiederholte I/O‑Operationen zu vermeiden.  
* **Testing:** Verifizieren Sie Beschriftungsänderungen, indem Sie einen visuellen Diff automatisieren (z. B. mit einem headless Word‑Viewer), falls Sie das Ergebnis in CI‑Pipelines prüfen müssen.

## Nächste Schritte

Jetzt, da Sie die Grundlagen des **Edit Chart Label Tutorials** beherrschen, können Sie Folgendes erkunden:

* **Diagrammbeschriftungsposition ändern** für andere Serien oder Diagrammtypen  
* **Diagrammdatenbeschriftung** formatieren, z. B. Zahlenformate, Schriftfarben oder Hintergrundfüllungen anpassen  
* **Diagrammkategorienamen ausblenden**, während der Serienname bei Mehrfachserien‑Diagrammen erhalten bleibt  
* **Diagrammbeschriftungswert anzeigen** zusammen mit Prozentwerten bei Kreisdiagrammen  

Diese Themen vertiefen Ihre Kontrolle über die Ästhetik von Word‑Diagrammen und bereiten Sie auf fortgeschrittene Reporting‑Szenarien vor.

---

*Viel Spaß beim Programmieren! Wenn Ihnen dieses Tutorial geholfen hat, teilen Sie es mit Kolleg*innen oder tragen Sie Verbesserungen auf GitHub bei.*

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Diagrammdatenbeschriftung anpassen](/words/english/net/programming-with-charts/chart-data-label/)
- [Diagrammdatenbeschriftung](/words/german/net/programming-with-charts/chart-data-label/)
- [Diagrammdatenbeschriftung](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}