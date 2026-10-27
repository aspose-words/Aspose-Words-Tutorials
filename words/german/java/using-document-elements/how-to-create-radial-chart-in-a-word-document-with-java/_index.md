---
category: general
date: 2026-09-18
description: Erfahren Sie, wie Sie ein Radialdiagramm in einem Word‑Dokument mit Java
  erstellen, Diagrammdatenbeschriftungen hinzufügen und Seriendaten mit einem vollständigen
  Codebeispiel einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: de
lastmod: 2026-09-18
og_description: Erstelle ein Radialdiagramm in einem Word‑Dokument mit Java, füge
  Diagrammbeschriftungen hinzu und füge Seriendaten in einer einzigen Anleitung ein.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Radialdiagramm in Word mit Java erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Wie man ein Radialdiagramm in einem Word-Dokument mit Java erstellt
url: /de/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Radialdiagramm in einem Word‑Dokument mit Java erstellt

Wenn Sie ein Radialdiagramm in einem Word‑Dokument erstellen müssen, zeigt Ihnen diese Anleitung die genauen Schritte. Sie erfahren außerdem, wie Sie Diagrammdatenbeschriftungen hinzufügen und Serien‑Daten einfügen, sodass das Diagramm fertig für die Präsentation ist.

Das programmgesteuerte Erzeugen eines Diagramms eliminiert manuelle Formatierungsarbeit und garantiert Konsistenz über alle Berichte hinweg. Das Tutorial setzt Grundkenntnisse in Java und eine aktuelle Version der Aspose.Words for Java‑Bibliothek voraus.

## Was Sie benötigen

* Java 17 oder neuer  
* Aspose.Words for Java (Version 23.12 oder später)  
* Eine IDE oder ein Build‑Tool, das Maven/Gradle‑Abhängigkeiten auflösen kann  

Wenn diese Voraussetzungen installiert sind, können Sie das Beispiel ohne weitere Konfiguration ausführen.

## Wie man ein Radialdiagramm in einem Word‑Dokument erstellt

Der erste Schritt besteht darin, eine leere Word‑Datei zu erzeugen, die das Diagramm aufnehmen wird. Ein leeres Dokument bietet eine saubere Arbeitsfläche und verhindert unbeabsichtigte Formatierungen.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` Methoden zum Einfügen von Elementen wie Absätzen, Tabellen und Diagrammen bereitstellt.

## Wie man das Diagramm einfügt

Als Nächstes fügen Sie das eigentliche Diagramm ein. Die Methode `insertChart` erzeugt ein Diagramm‑Objekt und platziert es an der aktuellen Cursor‑Position des Builders.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Ein Polardiagramm stellt Datenpunkte um eine zentrale Achse dar, was ideal für die Darstellung zyklischer Informationen ist. Die Abmessungen werden in Punkten angegeben (1 pt ≈ 1/72 Zoll).

## Serien‑Daten zum Diagramm hinzufügen

Ein Diagramm ohne Serien‑Daten ist leer. Sie können eine Serie manuell hinzufügen oder an eine Datenquelle binden. Das nachfolgende Beispiel fügt eine einzelne Serie mit drei Datenpunkten hinzu.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` erhält einen Seriennamen, eine Liste von Kategorien‑Beschriftungen und eine Liste der entsprechenden numerischen Werte. Sie können diesen Block wiederholen, um weitere Serien hinzuzufügen (`addSeriesData`).

## Diagrammdatenbeschriftungen zur ersten Serie hinzufügen

Datenbeschriftungen machen das Diagramm lesbar, ohne dass man über die Punkte fahren muss. Die folgende Zeile aktiviert Wert‑Beschriftungen für die erste Serie.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Durch Setzen von `showValue` auf `true` wird der Wert jedes Punktes direkt im Diagramm angezeigt. Sie können ebenfalls Kategorienamen, Prozentsätze oder Führungslinien über dasselbe `DataLabelFormat`‑Objekt aktivieren.

## Das Word‑Dokument speichern

Nachdem das Diagramm konfiguriert ist, schreiben Sie das Dokument auf die Festplatte. Wählen Sie einen Speicherort, auf den Ihre Anwendung Zugriff hat.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Die Datei `RadialChart.docx` enthält nun ein voll funktionsfähiges Radialdiagramm mit Datenbeschriftungen.

## Vollständiges funktionierendes Beispiel

Unten finden Sie ein eigenständiges Programm, das Sie kopieren, kompilieren und ausführen können. Es demonstriert den kompletten Workflow vom Erzeugen eines leeren Word‑Dokuments bis zum Speichern eines Radialdiagramms mit Datenbeschriftungen.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Erwartetes Ergebnis**

Wenn Sie `output/RadialChart.docx` in Microsoft Word öffnen, sehen Sie ein Radialdiagramm mit dem Titel *Quarterly Sales*. Jeder Punkt zeigt seinen numerischen Wert (z. B. „15000“) neben dem Markierungssymbol an.

## Häufige Variationen und Sonderfälle

| Situation | Empfohlene Änderung |
|-----------|---------------------|
| Sie benötigen einen anderen Diagrammtyp | Ersetzen Sie `ChartType.POLAR` durch einen anderen `ChartType`‑Enum‑Wert (z. B. `ChartType.COLUMN`). |
| Das Diagramm muss einen externen Excel‑Bereich verwenden | Verwenden Sie `chart.setDataRange("Sheet1!A1:B5")` nach der Diagrammerstellung und dem Laden der Arbeitsmappe. |
| Sie möchten die Legende ausblenden | `chart.getLegend().setVisible(false);` |
| Das Dokument muss als PDF gespeichert werden | Rufen Sie `doc.save("RadialChart.pdf");` auf – Aspose.Words konvertiert das Diagramm automatisch. |

Diese Anpassungen erhalten die Kernlogik, passen jedoch die Ausgabe an spezifische Anforderungen an.

## Pro‑Tipps

* **Builder wiederverwenden** – Sie können mehrere Diagramme im selben Dokument einfügen, indem Sie `builder.insertChart` wiederholt aufrufen.
* **Performance** – Beim Erzeugen vieler Diagramme erstellen Sie eine einzige `DocumentBuilder`‑Instanz und verwenden sie erneut, um den Overhead bei Objektallokationen zu reduzieren.
* **Styling** – Das Aussehen des Diagramms (Farben, Linienstärke) wird über die Methoden des `Chart`‑Objekts `getSeries().get(i).getFormat()` gesteuert. Experimentieren Sie mit diesen Einstellungen, um das Corporate Branding zu treffen.

## Fazit

Sie wissen jetzt, wie man ein Radialdiagramm in einem Word‑Dokument mit Java erstellt, Serien‑Daten hinzufügt und Diagrammdatenbeschriftungen einbindet, bevor die Datei gespeichert wird. Das vollständige Beispiel lässt sich erweitern, um weitere Serien, benutzerdefinierte Stile oder alternative Ausgabeformate zu unterstützen.

Entdecken Sie verwandte Themen wie **wie man ein Diagramm aus externen Datenquellen einfügt**, **wie man leere Word‑Dokumente mit vordefinierten Vorlagen erstellt** und **wie man Serien‑Daten dynamisch aus Datenbanken hinzufügt**. Experimentieren Sie mit verschiedenen Diagrammtypen, um herauszufinden, welche Visualisierung Ihre Daten am besten kommuniziert.


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Word‑Dokument Java – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Standardoptionen für Datenbeschriftungen in einem Diagramm festlegen](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}