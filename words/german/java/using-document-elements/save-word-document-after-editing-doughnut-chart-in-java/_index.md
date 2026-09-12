---
category: general
date: 2026-09-11
description: Speichern Sie das Word-Dokument nach dem Bearbeiten eines Donut-Diagramms
  mit Aspose.Words für Java. Erfahren Sie, wie Sie die Größe des Donut‑Lochs ändern,
  das Donut-Diagramm drehen und die Eigenschaften des Donut-Diagramms bearbeiten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: de
lastmod: 2026-09-11
og_description: Speichern Sie das Word-Dokument nach dem Bearbeiten eines Donut-Diagramms
  mit Aspose.Words für Java. Dieses Tutorial zeigt, wie Sie die Größe des Donut-Lochs
  ändern, das Donut-Diagramm drehen und das Erscheinungsbild des Diagramms anpassen.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Word-Dokument nach dem Bearbeiten eines Donut-Diagramms speichern – Java-Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Word‑Dokument nach dem Bearbeiten des Donut‑Diagramms in Java speichern
url: /de/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument nach dem Bearbeiten eines Donut‑Diagramms in Java speichern

Wenn Sie ein **Word‑Dokument** speichern müssen, das ein angepasstes Donut‑Diagramm enthält, zeigt Ihnen diese Anleitung genau, wie das geht. Mit nur wenigen Zeilen Java können Sie das Donut‑Loch ändern, das Donut‑Diagramm drehen und das Ergebnis anschließend wieder auf die Festplatte schreiben.

Sie sehen ein vollständiges, ausführbares Beispiel, das Aspose.Words für Java verwendet, sowie Tipps zum Umgang mit mehreren Diagrammen, zur Überprüfung von Knotentypen und zur Vermeidung häufiger Fallstricke. Es werden keine externen Referenzen benötigt – alles, was Sie brauchen, ist enthalten.

## Voraussetzungen

- Java 17 oder neuer installiert
- Maven oder Gradle zur Verwaltung von Abhängigkeiten
- Aspose.Words für Java (Version 23.9 oder später) zu Ihrem Projekt hinzugefügt  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Eine Word‑Datei (`input.docx`), die ein einzelnes Donut‑Diagramm enthält

## Schritt 1: Word‑Dokument laden

Der erste Schritt besteht darin, die Quelldatei zu öffnen. Dieser Schritt ist entscheidend, weil jede nachfolgende Operation auf dem im Speicher befindlichen `Document`‑Objekt arbeitet.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Warum?** Das Laden des Dokuments erzeugt eine DOM‑Repräsentation, die es Ihnen ermöglicht, Formen, Tabellen und Diagramme zu durchlaufen. Wenn die Datei nicht geöffnet werden kann, wirft Aspose.Words eine Ausnahme, sodass Sie sofort wissen, dass der Pfad falsch ist.

## Schritt 2: Donut‑Diagramm‑Shape finden

Ein Diagramm wird in einem `Shape`‑Knoten gespeichert. Wir holen das erste Shape, das ein Diagramm enthält, und casten dessen Renderer zu `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Warum?** Das Prüfen von `isChart()` verhindert eine `ClassCastException`, wenn das Dokument Bilder oder andere Shapes vor dem Diagramm enthält. Dadurch wird der Code robust für Dokumente mit gemischtem Inhalt.

## Schritt 3: Donut‑Lochgröße ändern  

Jetzt bearbeiten wir das Donut‑Loch. Die Methode `setHoleSize` erwartet einen Prozentsatz des Diagrammradius (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Warum?** Das Ändern des Donut‑Lochs (`change doughnut hole` / `change chart hole size`) ermöglicht es, den zentralen Bereich zu betonen oder zu entbetonen. Werte außerhalb von 10‑90 % werden von der API ignoriert.

## Schritt 4: Donut‑Diagramm drehen  

Um zu steuern, wo das erste Segment beginnt, setzen Sie den Winkel des ersten Segments. Damit wird das Donut‑Diagramm effektiv **rotiert**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Warum?** Das Drehen des Diagramms ist nützlich, wenn ein bestimmtes Segment oben angezeigt werden soll oder um einer Designspezifikation zu entsprechen.

## Schritt 5: Aktualisiertes Dokument speichern  

Abschließend schreiben Sie die Änderungen in eine neue Datei. Dies ist der Moment, in dem Sie das **Word‑Dokument** mit dem bearbeiteten Diagramm **speichern**.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Erwartetes Ergebnis:** `output.docx` enthält den ursprünglichen Inhalt, aber das Donut‑Diagramm hat jetzt ein 30 %‑Loch und sein erstes Segment beginnt bei 45 °. Das Öffnen der Datei in Microsoft Word zeigt das transformierte Diagramm.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie in Ihre IDE kopieren können. Es enthält alle Importe und die Fehlerbehandlung, die zum sicheren **Bearbeiten des Donut‑Diagramms** und **Speichern des Word‑Dokuments** erforderlich sind.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Erwartete Ausgabe

Wenn Sie `output.docx` öffnen:

- Das zentrale Loch des Donut‑Diagramms nimmt etwa ein Drittel des Diagrammradius ein.  
- Das erste Segment beginnt bei 45 Grad, wodurch das gesamte Diagramm im Uhrzeigersinn verschoben wird.  

Beide visuellen Änderungen werden sofort in Word angezeigt.

## Häufige Varianten und Randfälle

| Situation | Vorgehensweise |
|-----------|----------------|
| **Mehrere Diagramme** | Durchlaufen Sie `doc.getChildNodes(NodeType.SHAPE, true)` und filtern Sie `shape.isChart()`; wenden Sie `setHoleSize` / `setFirstSliceAngle` auf jedes `Chart` an. |
| **Diagramm ist kein Donut** | Prüfen Sie `chart.getType()`; rufen Sie `setHoleSize` nur auf, wenn `chart.getType() == ChartType.DOUGHNUT`. |
| **Notwendig, die Lochgröße dynamisch zu ändern** | Berechnen Sie den gewünschten Prozentsatz basierend auf den Datenwerten und rufen Sie anschließend `setHoleSize(computedValue)` auf. |
| **In einen Stream speichern** | Use |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Wie man ein Dokument mit Aspose.Words für Java als PDF speichert](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word mit Passwort speichern mit Aspose.Words für Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}