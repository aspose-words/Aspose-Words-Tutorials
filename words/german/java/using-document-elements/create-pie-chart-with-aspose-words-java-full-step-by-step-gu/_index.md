---
category: general
date: 2026-07-16
description: Erstellen Sie ein Kreisdiagramm in Java mit Aspose.Words. Erfahren Sie,
  wie Sie Leitlinien hinzufügen, die Diagrammlegende anzeigen und ein Segment herauslösen
  – alles in einem einzigen Tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: de
lastmod: 2026-07-16
og_description: Erstellen Sie ein Kreisdiagramm in Java mit Aspose.Words. Dieser Leitfaden
  zeigt, wie Sie Führungslinien hinzufügen, die Diagrammlegende anzeigen und ein Segment
  hervorheben, um Ihnen in wenigen Minuten ein professionelles Bild zu liefern.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Kreisdiagramm mit Aspose.Words Java erstellen – Komplettes Formatierungs‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Erstellen Sie ein Kreisdiagramm mit Aspose.Words Java – Vollständige Schritt‑für‑Schritt‑Anleitung
url: /de/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm mit Aspose.Words Java – Vollständige Schritt‑für‑Schritt‑Anleitung

Haben Sie sich jemals gefragt, wie man **Kreisdiagramme** programmgesteuert in Java erstellt, ohne sich mit Low‑Level‑Zeichnungs‑APIs herumzuschlagen? Sie sind nicht allein. Viele Entwickler benötigen eine schnelle Visualisierung für Berichte, Dashboards oder automatisierte Dokumente und greifen zu Aspose.Words, weil es die schwere Arbeit übernimmt.  

In diesem Tutorial führen wir Sie durch ein vollständiges, sofort ausführbares Beispiel, das nicht nur **ein Kreisdiagramm erstellt**, sondern Ihnen auch zeigt, wie man **Führungs‑Linien hinzufügt**, **die Diagrammlegende anzeigt** und sogar **ein Segment hervorhebt**. Am Ende haben Sie eine `.docx`‑Datei, die so professionell aussieht, dass sie einen Kunden beeindruckt.

> **Schneller Erfolg:** Der untenstehende Codeausschnitt funktioniert sofort mit Aspose.Words for Java 23.9 (oder jeder neueren Version). Keine zusätzlichen Abhängigkeiten, nur das JAR.

## Was Sie lernen werden

- Ein leeres Word‑Dokument mit `DocumentBuilder` einrichten.
- Ein **Kreisdiagramm** in benutzerdefinierter Größe einfügen.
- Die **explode slice**‑Funktion verwenden, um einen Datenpunkt hervorzuheben.
- **Führungs‑Linien** aktivieren, damit das ausgeklügelte Segment mit dem Beschriftungsfeld verbunden bleibt.
- Die **Diagrammlegende** aktivieren, damit Leser jedes Segment sofort erkennen können.
- Das Ergebnis in einer `.docx`‑Datei speichern, die Sie in Microsoft Word oder LibreOffice öffnen können.

**Voraussetzungen** – Sie benötigen:

1. Java 17 (oder neuer) installiert.
2. Aspose.Words for Java JAR in Ihrem Klassenpfad.
3. Eine grundlegende IDE oder einen Texteditor – IntelliJ IDEA, Eclipse, VS Code, oder was Sie bevorzugen.

Jetzt tauchen wir ein.

## Schritt 1: Dokument und Builder initialisieren – Vorbereitung zum **Erstellen eines Kreisdiagramms**

Zuerst benötigen wir eine leere Dokumentenfläche. `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` das Hilfsmittel ist, das uns das Hinzufügen von Inhalten ermöglicht.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Warum das wichtig ist:** Das Starten mit einem frischen `Document` stellt sicher, dass keine versteckten Stile oder übrig gebliebenen Objekte vorhanden sind, die die Diagrammdarstellung beeinträchtigen könnten.

## Schritt 2: Das **Kreisdiagramm** einfügen – Größe ist wichtig

Aspose.Words ermöglicht das Einfügen von Diagrammen mit einer einzigen Zeile Code. Hier fordern wir ein Kreisdiagramm mit 400 × 300 Punkten an – etwa 5,5 × 4,2 Zoll auf einem typischen Bildschirm.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Profi‑Tipp:** Wenn Sie eine andere Größe benötigen, ändern Sie einfach die beiden numerischen Argumente. Die API arbeitet mit Punkten, wobei 72 Punkte = 1 Zoll.

## Schritt 3: **Wie man ein Segment hervorhebt** – Einen wichtigen Datenpunkt betonen

Das Hervorheben eines Segments zieht es aus dem Rest des Kreisdiagramms heraus und lenkt die Aufmerksamkeit des Lesers. Die Methode `setExplosion` nimmt einen Integer entgegen, der den Abstand in Punkten angibt.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Was, wenn Sie mehrere Serien haben?** Sie können `setExplosion` für jeden Serien‑Index (`get(1)`, `get(2)`, …) aufrufen, um verschiedene Segmente hervorzuheben.

## Schritt 4: **Führungs‑Linien hinzufügen** und **Diagrammlegende anzeigen** – Die Punkte verbinden

Wenn ein Segment hervorgehoben wird, kann die Beschriftung davon abdriften. Führungs‑Linien halten die Beschriftung befestigt und erhalten die Lesbarkeit. Gleichzeitig bietet eine Legende eine schnelle Legende für alle Segmente.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Warum Führungs‑Linien aktivieren?** Ohne sie könnte die Beschriftung schwebend erscheinen und die Benutzer verwirren, welchem Segment sie zugeordnet ist.  
> **Benötigen Sie eine benutzerdefinierte Legendenposition?** Verwenden Sie `chart.getLegend().setPosition(LegendPosition.TOP)` oder einen anderen Enum‑Wert.

## Schritt 5: Dokument speichern – Der letzte **Erstellen‑Kreisdiagramm**‑Schritt

Abschließend speichern wir das Dokument auf dem Datenträger. Passen Sie den Pfad zu einem Ordner an, in den Sie Schreibzugriff haben.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Führen Sie das Programm aus, öffnen Sie die erzeugte `PieChartDemo.docx`, und Sie sollten ein schön formatiertes Kreisdiagramm mit einem hervorgehobenen ersten Segment, Führungs‑Linien und einer sichtbaren Legende sehen.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Beispiel für ein Kreisdiagramm mit hervorgehobenen Segment, Führungs‑Linien und Legende"}

### Erwartete Ausgabe

Wenn Sie die Word‑Datei öffnen, sieht das Diagramm ungefähr so aus:

- Ein 400 × 300 pt Kreisdiagramm.
- Das erste Segment ist um 10 pt versetzt.
- Eine dünne Führungs‑Linie verbindet das hervorgehobene Segment mit seiner Beschriftung.
- Eine Legende unter dem Diagramm listet jeden Seriennamen auf.

Wenn Sie die Führungs‑Linie nicht sehen, prüfen Sie, ob `setLeaderLines(true)` *nach* der Explosions‑Einstellung aufgerufen wird – die Reihenfolge ist wichtig.

## Häufige Fallstricke und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| **Keine Legende sichtbar** | `setShowLegend(true)` wurde weggelassen oder am falschen Diagrammobjekt aufgerufen. | Stellen Sie sicher, dass Sie `chart.setShowLegend(true)` **nach** dem Abrufen des `Chart` aus der Form aufrufen. |
| **Führungs‑Linie fehlt** | Das Segment wurde nicht hervorgehoben, oder der Diagrammtyp unterstützt keine Führungs‑Linien. | Nur `ChartType.PIE` (oder `PIE_3D`) unterstützt Führungs‑Linien. Rufen Sie zuerst `setExplosion` auf, dann `setLeaderLines(true)`. |
| **Segment bewegt sich nicht** | Explosionswert zu niedrig (0‑2 pt). | Erhöhen Sie den Integer, z. B. `setExplosion(10)` oder höher für einen dramatischeren Effekt. |
| **Diagramm wirkt verzerrt** | Die Verwendung einer nicht‑quadratischen Größe (Breite ≠ Höhe) kann das Kreisdiagramm verformen. | Halten Sie Breite und Höhe gleich oder nah beieinander; 400 × 300 funktioniert, aber 400 × 400 ergibt einen perfekten Kreis. |

## Erweiterte Anpassungen (Optional)

Wenn Sie über die Grundlagen hinausgehen möchten, denken Sie an:

- **Benutzerdefinierte Farben**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Datenbeschriftungen**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D‑Effekt**: Ersetzen Sie `ChartType.PIE` durch `ChartType.PIE_3D`.

Diese Optionen ermöglichen es Ihnen, die Darstellung fein abzustimmen, um den Corporate‑Branding‑Richtlinien zu entsprechen.

## Zusammenfassung – Was wir erreicht haben

Wir begannen mit einem leeren Word‑Dokument, **erstellten ein Kreisdiagramm**, **hoben das erste Segment hervor**, **fügten Führungs‑Linien hinzu** und **zeigten die Diagrammlegende**. Der gesamte Ablauf passt in eine kompakte `main`‑Methode, sodass er sich leicht in größere Reporting‑Pipelines einbinden lässt.

## Nächste Schritte

- **Weitere Serien hinzufügen**: Das Diagramm mit echten Daten aus einer Datenbank oder CSV füllen.
- **Export nach PDF**: Verwenden Sie `doc.save("output.pdf", SaveFormat.PDF);`, um eine PDF‑Version zu erzeugen.
- **Mit anderen Formen kombinieren**: Tabellen, Bilder oder zusätzliche Diagramme einfügen, um einen vollständigen Bericht zu erstellen.

Wenn Sie neugierig auf andere Diagrammtypen sind – Säulen, Balken, Linie – ersetzen Sie einfach `ChartType.PIE` durch das passende Enum und folgen Sie denselben Formatierungsschritten.

---

*Viel Spaß beim Diagramm‑Erstellen!* Hinterlassen Sie gerne einen Kommentar, wenn etwas nicht wie erwartet funktioniert hat, oder teilen Sie mit, wie Sie die Legendenposition angepasst haben. Ihr Feedback hilft uns allen, bessere automatisierte Dokumente zu erstellen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Wie man PDF‑Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)
- [Wie man Wasserzeichen zu Dokumenten mit Aspose.Words für Java hinzufügt](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}