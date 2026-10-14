---
title: Sekundäre X‑Achse formatieren und Anzeigeeinheiten auf Tausend setzen in Word‑Liniendiagrammen mit Aspose.Words für .NET
weight: 710
limit:
description: Erstellen Sie ein Word‑Liniendiagramm, fügen Sie eine sekundäre X‑Achse hinzu, setzen Sie deren Anzeigeeinheit auf Tausend und wenden Sie ein benutzerdefiniertes Zahlenformat mit Aspose.Words für .NET an.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Erstellen Sie ein Word‑Liniendiagramm, fügen Sie eine sekundäre X‑Achse
    hinzu, setzen Sie deren Anzeigeeinheit auf Tausend und wenden Sie ein benutzerdefiniertes
    Zahlenformat mit Aspose.Words für .NET an.
  headline: Sekundäre X‑Achse formatieren und Anzeigeeinheiten auf Tausend setzen
    in Word‑Liniendiagrammen mit Aspose.Words für .NET
  type: TechArticle
- description: Erstellen Sie ein Word‑Liniendiagramm, fügen Sie eine sekundäre X‑Achse
    hinzu, setzen Sie deren Anzeigeeinheit auf Tausend und wenden Sie ein benutzerdefiniertes
    Zahlenformat mit Aspose.Words für .NET an.
  name: Sekundäre X‑Achse formatieren und Anzeigeeinheiten auf Tausend setzen in Word‑Liniendiagrammen
    mit Aspose.Words für .NET
  steps:
  - name: Erstellen Sie ein neues Document und einen DocumentBuilder, um mit dem Aufbau
      der Word‑Datei zu beginnen.
    text: Erstellen Sie ein neues Document und einen DocumentBuilder, um mit dem Aufbau
      der Word‑Datei zu beginnen.
  - name: Fügen Sie ein Liniendiagramm mit der Größe 500×300 in das Dokument ein und
      erhalten Sie das Chart‑Objekt.
    text: Fügen Sie ein Liniendiagramm mit der Größe 500×300 in das Dokument ein und
      erhalten Sie das Chart‑Objekt.
  - name: Entfernen Sie die standardmäßige Demo‑Serie, die Aspose.Words automatisch
      hinzufügt.
    text: Entfernen Sie die standardmäßige Demo‑Serie, die Aspose.Words automatisch
      hinzufügt.
  - name: Definieren Sie ein Array von Kategorienbeschriftungen, das für die X‑Achse
      verwendet wird.
    text: Definieren Sie ein Array von Kategorienbeschriftungen, das für die X‑Achse
      verwendet wird.
  - name: Fügen Sie die primäre Datenreihe mit dem Namen "Main Data" unter Verwendung
      der Beschriftungen und Werte hinzu.
    text: Fügen Sie die primäre Datenreihe mit dem Namen "Main Data" unter Verwendung
      der Beschriftungen und Werte hinzu.
  - name: Erstellen Sie eine sekundäre Series‑Group vom Typ Line und weisen Sie sie
      der sekundären Achsen‑Group zu.
    text: Erstellen Sie eine sekundäre Series‑Group vom Typ Line und weisen Sie sie
      der sekundären Achsen‑Group zu.
  - name: Setzen Sie die Anzeigeeinheit der sekundären X‑Achse auf Tausend, sodass
      Werte in K angezeigt werden.
    text: Setzen Sie die Anzeigeeinheit der sekundären X‑Achse auf Tausend, sodass
      Werte in K angezeigt werden.
  - name: Wenden Sie das benutzerdefinierte Zahlenformat "#,##0.0" auf die Tick‑Beschriftungen
      der sekundären X‑Achse an.
    text: Wenden Sie das benutzerdefinierte Zahlenformat "#,##0.0" auf die Tick‑Beschriftungen
      der sekundären X‑Achse an.
  - name: Fügen Sie optional eine Hilfsdatenreihe zur sekundären Gruppe hinzu.
    text: Fügen Sie optional eine Hilfsdatenreihe zur sekundären Gruppe hinzu.
  - name: Speichern Sie das Dokument als .docx‑Datei.
    text: Speichern Sie das Dokument als .docx‑Datei.
  type: HowTo
- questions:
  - answer: Nein – die `AxisX`‑Einstellungen gehören zur `ChartSeriesGroup`, sodass
      Sie `secondaryGroup.AxisX.DisplayUnit.Unit` und `secondaryGroup.AxisX.NumberFormat.FormatCode`
      vor oder nach dem Hinzufügen von Serien festlegen können; die Konfiguration
      wird in beiden Fällen auf die Achse der Gruppe angewendet.
    question: Muss ich die sekundäre Serie hinzufügen, bevor ich die Anzeigeeinheit
      und das Zahlenformat für die sekundäre X‑Achse festlege?
  - answer: Ja – weisen Sie einen beliebigen `AxisBuiltInUnit`‑Wert zu, z. B. `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`, um die Achsenwerte in Millionen anstelle von Tausend
      anzuzeigen.
    question: Kann ich für die sekundäre X‑Achse eine andere vordefinierte Einheit,
      z. B. Millionen, verwenden?
  - answer: Nein – der Formatcode wird nur auf die von Ihnen modifizierte Achse (`secondaryGroup.AxisX.NumberFormat.FormatCode`)
      angewendet, sodass die primäre X‑Achse ihre Standardformatierung beibehält.
    question: Wird das benutzerdefinierte Format `"#,##0.0"` die Beschriftungen der
      primären X‑Achse beeinflussen?
  - answer: Das Diagramm enthält dann zusätzlich zur von Ihnen hinzugefügten die standardmäßige
      Demo‑Serie, was zu zusätzlichen Linien und nicht übereinstimmenden Kategorien
      führen kann; das Leeren der Sammlung stellt sicher, dass nur die beabsichtigten
      Daten angezeigt werden.
    question: Was passiert, wenn ich vergesse, die Demo‑Serie mit `lineChart.Series.Clear();`
      zu löschen?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Sekundäre X‑Achse formatieren und Einheiten auf Tausend setzen
og_description: Fügen Sie einem Word‑Liniendiagramm eine sekundäre X‑Achse hinzu und formatieren Sie deren Beschriftungen in Tausend mit einem benutzerdefinierten Muster.
og_image_alt: Anleitung, wie man einem Word‑Liniendiagramm eine sekundäre X‑Achse hinzufügt und deren Beschriftungen mit Aspose.Words für .NET so formatiert, dass die Anzeigeeinheiten in Tausend dargestellt werden.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sekundäre X‑Achse formatieren und Anzeigeeinheiten auf Tausend setzen in Word‑Liniendiagrammen mit Aspose.Words für .NET
Dieses Tutorial führt Sie Schritt für Schritt durch das Erstellen eines Word‑Dokuments mit einem Liniendiagramm, das Hinzufügen einer sekundären X‑Achse und die Konfiguration dieser Achse, sodass Werte in Tausend angezeigt werden. Sie lernen außerdem, wie Sie ein benutzerdefiniertes Zahlenformat auf die Beschriftungen der sekundären Achse anwenden, um die Darstellung der Daten präzise zu steuern. Befolgen Sie die Schritte, um die Lesbarkeit von Diagrammen mit mehreren Achsen in Ihren Word‑Berichten zu verbessern.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Muss ich die sekundäre Serie hinzufügen, bevor ich die Anzeigeeinheit und das Zahlenformat für die sekundäre X‑Achse festlege?**  
A: Nein – die `AxisX`‑Einstellungen gehören zur `ChartSeriesGroup`, sodass Sie `secondaryGroup.AxisX.DisplayUnit.Unit` und `secondaryGroup.AxisX.NumberFormat.FormatCode` vor oder nach dem Hinzufügen von Serien festlegen können; die Konfiguration wird in beiden Fällen auf die Achse der Gruppe angewendet.

**Q: Kann ich für die sekundäre X‑Achse eine andere vordefinierte Einheit, z. B. Millionen, verwenden?**  
A: Ja – weisen Sie einen beliebigen `AxisBuiltInUnit`‑Wert zu, z. B. `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`, um die Achsenwerte in Millionen anstelle von Tausend anzuzeigen.

**Q: Wird das benutzerdefinierte Format `"#,##0.0"` die Beschriftungen der primären X‑Achse beeinflussen?**  
A: Nein – der Formatcode wird nur auf die von Ihnen modifizierte Achse (`secondaryGroup.AxisX.NumberFormat.FormatCode`) angewendet, sodass die primäre X‑Achse ihre Standardformatierung beibehält.

**Q: Was passiert, wenn ich vergesse, die Demo‑Serie mit `lineChart.Series.Clear();` zu löschen?**  
A: Das Diagramm enthält dann zusätzlich zur von Ihnen hinzugefügten die standardmäßige Demo‑Serie, was zu zusätzlichen Linien und nicht übereinstimmenden Kategorien führen kann; das Leeren der Sammlung stellt sicher, dass nur die beabsichtigten Daten angezeigt werden.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}