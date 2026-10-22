---
category: general
date: 2026-09-24
description: Fügen Sie ein Kreisdiagramm in ein DOCX mit Aspose.Words für Java ein.
  Erfahren Sie, wie Sie die Lochgröße einstellen, ein Segment des Kreisdiagramms explodieren,
  ein Segment hervorheben und mühelos ein DOCX‑Diagramm erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: de
lastmod: 2026-09-24
og_description: Fügen Sie ein Kreisdiagramm in ein DOCX mit Aspose.Words für Java
  ein. Beherrschen Sie das Einstellen der Lochgröße, das Explodieren von Kuchenscheiben,
  das Hervorheben von Diagrammscheiben und das Erstellen von DOCX‑Diagrammen in Minuten.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Pie‑Chart‑Wort in Java einfügen – Schritt‑für‑Schritt‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Kreisdiagramm‑Wort in Java einfügen – vollständige Anleitung
url: /de/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kuchendiagramm‑Wort in Java einfügen – vollständige Anleitung

Wenn Sie **pie chart word einfügen** in einer DOCX‑Datei benötigen, zeigt Ihnen dieses Tutorial genau, wie Sie das mit Aspose.Words für Java erledigen. Sie sehen den kompletten Workflow vom Erstellen des Dokuments bis zur Anpassung des Diagramms, sodass das Segment explodiert, die Lochgröße auf Null gesetzt und das Segment hervorgehoben wird.

Die Arbeit mit Diagrammen in Word‑Dokumenten fühlt sich oft wie ein separates Thema zur regulären Textverarbeitung an, aber Aspose.Words vereint beides. In den nachfolgenden Schritten lernen Sie außerdem, wie Sie **docx chart erstellen** können, die in Microsoft Word, Google Docs oder jedem anderen DOCX‑kompatiblen Viewer geöffnet werden können.

## Was Sie erreichen werden

* **pie chart word einfügen** in ein leeres Dokument  
* **hole size setzen**, um das Diagramm zu einem vollen Kuchen (kein Donut) zu machen  
* **pie slice explodieren**, um die Aufmerksamkeit auf ein bestimmtes Segment zu lenken  
* **pie chart slice hervorheben** mit benutzerdefiniertem Format  
* **docx chart erstellen**, das weitergegeben oder bearbeitet werden kann  

### Voraussetzungen

* Java 17 oder höher (der Code kompiliert auch mit Java 8)  
* Aspose.Words für Java Bibliothek (Version 23.9 oder neuer)  
* Eine IDE oder ein Build‑Tool (Maven/Gradle), das die Aspose.Words‑Abhängigkeit auflösen kann  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Wie man **pie chart word** in einer DOCX mit Aspose.Words einfügt

Der erste Schritt besteht darin, ein neues leeres Dokument zu erstellen und einen `DocumentBuilder` zu erhalten. Der Builder gibt Ihnen direkten Zugriff auf den Inhaltsstrom des Dokuments und macht das **pie chart word einfügen** trivial.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Warum das wichtig ist
`Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` die High‑Level‑API ist, mit der Sie Absätze, Tabellen und Diagramme einfügen können, ohne sich mit Low‑Level‑XML auseinandersetzen zu müssen. Das Beginnen mit einem leeren Dokument stellt sicher, dass das von Ihnen hinzugefügte Diagramm das einzige Element ist – ideal zum Lernen oder zum Generieren von vorlagenbasierten Berichten.

## **hole size** setzen, um einen vollen Kuchen zu erhalten

Standardmäßig erstellt Aspose.Words ein Donut‑Diagramm, wenn Sie ein Kuchendiagramm anfordern. Um das Diagramm zu einem echten Kreis zu machen, müssen Sie **hole size** auf `0` setzen. Dadurch wird das innere Loch entfernt und ein klassisches Kuchendiagramm entsteht.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktischer Tipp
Wenn Sie später zu einem Donut‑Diagramm wechseln möchten, ändern Sie einfach den Wert von `holeSize` auf einen Prozentsatz (z. B. `30`). dieselbe API funktioniert für beide Diagrammtypen.

## **pie slice** explodieren, um ein Segment hervorzuheben

Das Explodieren eines Segments lässt es visuell hervorstechen. Der **explode pie slice** Vorgang verschiebt das ausgewählte Segment nach außen um einen Prozentsatz des Diagrammradius.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Warum explodieren?
Ein explodiertes Segment zieht das Auge des Lesers auf den wichtigsten Datenpunkt – perfekt für Dashboards oder Management‑Zusammenfassungen. Der Wert `20` bedeutet 20 % des Radius; Sie können ihn zwischen `0` (kein Explodieren) und `100` (vollständig losgelöst) anpassen.

## **pie chart slice** mit benutzerdefiniertem Format hervorheben

Neben dem Explodieren möchten Sie möglicherweise **pie chart slice hervorheben**, indem Sie die Füllfarbe oder den Rand ändern. Während sich der Demo‑Code auf das Explodieren konzentriert, können Sie ihn wie folgt erweitern:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Hinweis für Experten
Das Ändern der Füllfarbe eines bestimmten Segments erfordert den Zugriff auf das `DataPoint`‑Objekt. Haben Sie mehrere Serien, iterieren Sie über `series.getDataPoints()` und wenden Sie die Stile bedingt an.

## Speichern und Überprüfen des erstellten **docx chart**

Abschließend **create docx chart** Sie, indem Sie das `Document` speichern. Die resultierende Datei kann in Microsoft Word geöffnet werden, um das formatierte Kuchendiagramm zu sehen.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Erwartete Ausgabe
Das Öffnen von `PieChartFormatted.docx` zeigt ein einzelnes Kuchendiagramm:

* Das Diagramm belegt einen Bereich von 400 × 300 pt.  
* Die **hole size** ist `0`, sodass das Diagramm ein voller Kuchen ist.  
* Das erste Segment ist um 20 % explodiert und rot gefärbt (falls Sie die optionale Formatierung hinzugefügt haben).  

Sie haben nun ein **docx chart erstellt**, das verteilt, in E‑Mails eingebettet oder programmgesteuert weiter bearbeitet werden kann.

---

## Häufige Variationen und Sonderfälle

| Szenario | Wie der Code anzupassen ist |
|----------|-----------------------------|
| **Mehrere Serien** | Durchlaufen Sie `pieChart.getChart().getSeries()` und setzen Sie `Explosion` bzw. `FillColor` pro Serie. |
| **Dynamische Daten** | Befüllen Sie die Serien mit Werten aus einer Datenbank oder CSV, bevor Sie `setExplosion` aufrufen. |
| **Andere Diagrammgröße** | Ändern Sie die Breiten‑/Höhen‑Argumente in `insertChart(ChartType.PIE, width, height)`. |
| **Export nach PDF** | Nach dem Speichern der DOCX rufen Sie `doc.save("output.pdf")` auf, um eine PDF‑Version desselben Diagramms zu erzeugen. |
| **Lokalisierung** | Verwenden Sie `DocumentBuilder.insertChart` mit einem lokalspezifischen Zahlenformat für Beschriftungen. |

### Pro‑Tipp
Rufen Sie `setHoleSize(0)` **nach** `insertChart` auf. Wenn Sie es vor dem Einfügen setzen, setzt Aspose.Words die Größe wieder auf den Standard‑Donut zurück, sobald das Diagramm erstellt wird.

---

## Zusammenfassung

Sie wissen jetzt, wie Sie **pie chart word** in ein Word‑Dokument mit Java einfügen, wie Sie **hole size** für ein Voll‑Kuchen‑Aussehen setzen, wie Sie **pie slice** explodieren, um Aufmerksamkeit zu erzeugen, und wie Sie **pie chart slice** mit eigenen Farben hervorheben. Das vollständige Beispiel demonstriert zudem, wie Sie **docx chart**‑Dateien erstellen, die bereit zur Verteilung sind.

---

## Nächste Schritte

* Erkunden Sie weitere Diagrammtypen (`BAR`, `LINE`, `SCATTER`) mit `ChartType`.  
* Kombinieren Sie die Diagrammerstellung mit Mail‑Merge, um personalisierte Berichte zu erzeugen.  
* Integrieren Sie das erzeugte DOCX in einen Web‑Service, der die Datei auf Abruf zurückgibt.  

Wenn Sie auf Probleme stoßen, prüfen Sie, ob Sie eine kompatible Version von Aspose.Words verwenden und ob das Ausgabeverzeichnis existiert und beschreibbar ist.

Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}