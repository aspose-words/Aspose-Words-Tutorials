---
category: general
date: 2026-10-26
description: Erstelle ein Donut‑Diagramm und füge ein Kreisdiagramm in Java mit Schritt‑für‑Schritt‑Code
  ein. Lerne den vollständigen Arbeitsablauf für flexible Diagrammvisualisierungen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: de
lastmod: 2026-10-26
og_description: Erstellen Sie ein Donut‑Diagramm in Java mit diesem Leitfaden, der
  auch zeigt, wie man ein Kreisdiagramm für flexible Visualisierungen einfügt.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Erstelle ein Donut‑Diagramm und füge ein Kreisdiagramm ein – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Wie man ein Donut‑Diagramm erstellt und ein Kreisdiagramm einfügt
url: /de/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Donut-Diagramm erstellt und ein Kreisdiagramm einfügt

Wenn Sie in Java **ein Donut-Diagramm erstellen** müssen, führt Sie dieses Tutorial durch die genauen Schritte. Wir zeigen außerdem, wie man **ein Kreisdiagramm einfügt** mit derselben Builder‑API, sodass Sie mühelos zwischen den visuellen Stilen wechseln können. Am Ende des Leitfadens haben Sie ein vollständiges, ausführbares Programm, das beide Diagrammtypen erzeugt und gängige Anpassungen demonstriert.

Das Tutorial behandelt:

* Initialisierung des Chart‑Builders, der von der gewählten Bibliothek bereitgestellt wird.  
* Erstellung eines Donut-Diagramms und Konfiguration der Lochgröße.  
* Einfügen eines Kreisdiagramms und Hervorheben einer Scheibe durch Explodieren.  
* Tipps zum Umgang mit Randfällen wie fehlenden Serien oder nicht unterstützten Diagrammtypen.

Sie benötigen lediglich ein aktuelles JDK (8 oder neuer) und die Chart‑Bibliothek‑JAR in Ihrem Klassenpfad. Keine externen Dienste sind erforderlich.

---

## Voraussetzungen

| Element | Grund |
|------|--------|
| Java Development Kit (JDK) 8+ | Erforderlich zum Kompilieren und Ausführen des Beispiels. |
| Chart library (z. B. **Aspose.Cells for Java** oder **JFreeChart**) | Stellt `ChartBuilder`, `ChartType` und Methoden zur Serienmanipulation bereit, die im Code verwendet werden. |
| Eine IDE oder ein Texteditor | Zum Schreiben und Ausführen der Java‑Quelldatei. |

Stellen Sie sicher, dass die Bibliotheks‑JAR zu Ihrem Build‑Pfad hinzugefügt wird. Wenn Sie Maven verwenden, fügen Sie die entsprechende Abhängigkeit hinzu; andernfalls legen Sie die JAR in den `libs`‑Ordner und referenzieren sie beim Kompilieren.

---

## Schritt 1: Chart‑Builder einrichten

Der erste Schritt besteht darin, eine Instanz von `ChartBuilder` (oder einer äquivalenten Klasse) zu erstellen, die die Diagrammobjekte erzeugt. Dieses Objekt fungiert als Fabrik und hält das Arbeitsblatt oder die Leinwand, auf der das Diagramm platziert wird.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Warum das wichtig ist:**  
Der Builder bindet das Diagramm an ein bestimmtes Arbeitsblatt, sodass alle nachfolgenden Diagrammobjekte dieselbe Zeichenfläche teilen. Das Überspringen dieses Schrittes würde dazu führen, dass Sie keinen Zielort für die visuellen Elemente haben.

---

## Schritt 2: **Donut-Diagramm erstellen**

Jetzt erzeugen wir ein Donut-Diagramm mit einer definierten Größe. Die Lochgröße bestimmt, wie viel vom Zentrum des Diagramms leer bleibt und verwandelt ein normales Kreisdiagramm in ein Donut-Diagramm.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Erklärung:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` erstellt das Diagrammobjekt und reserviert Platz im Arbeitsblatt.  
* `setHoleSize(30)` wandelt das Kreisdiagramm in ein Donut-Diagramm mit einem 30 % leeren Zentrum um.  
* `add("{10, 20, 30, 40}", true)` liefert vier Datenpunkte; das `true`‑Flag weist die Bibliothek an, die Werte als eine einzelne Serie zu behandeln.

**Randfall:** Wenn der ausgewählte Diagrammtyp kein Loch unterstützt (z. B. ein Balkendiagramm), wirft der Aufruf von `getDoughnutChart()` eine Ausnahme. Überprüfen Sie stets den Diagrammtyp, bevor Sie die Lochgröße anpassen.

---

## Schritt 3: **Kreisdiagramm einfügen**

Nachdem das Donut‑Diagramm fertig ist, zeigen wir, wie man **ein Kreisdiagramm einfügt** mit demselben Builder. Dieser Schritt verdeutlicht die Ähnlichkeit beider Diagrammtypen und zeigt, wie man eine Scheibe hervorhebt.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Erklärung:**  

* `ChartType.PIE` weist den Builder an, ein klassisches Kreisdiagramm zu erstellen.  
* `setExplode(10)` verschiebt die erste Scheibe um 10 % des Radius, eine gängige Technik, um einen wichtigen Datenpunkt hervorzuheben.  

**Tipp:** Die Methode `setExplode` wirkt nur auf die erste Serie eines Kreisdiagramms. Haben Sie mehrere Serien, müssen Sie den entsprechenden Index ansteuern.

---

## Schritt 4: Arbeitsmappe speichern

Zum Schluss schreiben wir die Arbeitsmappe in eine Datei, damit Sie die Diagramme in Excel oder einem kompatiblen Viewer ansehen können.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Warum jetzt speichern:** Das Persistieren der Arbeitsmappe finalisiert alle Zeichenoperationen. Der Versuch, die Datei vor dem Speichern zu öffnen, führt zu einem leeren oder unvollständigen Dokument.

**Ergebnis:** Das Öffnen von *DoughnutAndPieChart.xlsx* zeigt ein Donut‑Diagramm mit 30 % Loch auf der linken Seite und ein Kreisdiagramm mit einer explodierten ersten Scheibe rechts.

---

## Schritt 5: Häufige Variationen und Fehlersuche

| Situation | Anpassung |
|-----------|------------|
| **Andere Diagrammabmessungen** | Ändern Sie die Breiten‑ und Höhen‑Argumente in `insertChart`. |
| **Mehrere Datenserien** | Rufen Sie `add` mehrfach auf oder übergeben Sie einen 2‑D‑Array‑String. |
| **Dynamische Lochgröße** | Berechnen Sie die Lochgröße basierend auf dem Datenbereich und rufen Sie dann `setHoleSize` auf. |
| **Mehrere Scheiben explodieren** | Durchlaufen Sie `chart.getSeries().get(i).setExplode(percent)` für jede Scheibe, die Sie versetzen möchten. |
| **Bibliothek unterstützt kein Donut** | Verwenden Sie ein Kreisdiagramm und zeichnen Sie manuell einen weißen Kreis darüber, obwohl dies weniger präzise ist. |

**Pro‑Tipp:** Rufen Sie stets `builder.flush()` (falls verfügbar) nach dem Einfügen von Diagrammen bei großen Arbeitsmappen auf. Dadurch werden interne Puffer freigegeben und Speicherlecks vermieden.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "Beispiel für das Erstellen eines Donut‑Diagramms in Java")

*Das Bild illustriert das endgültige Layout der Arbeitsmappe mit beiden Diagrammen nebeneinander.*

---

## Fazit

Sie wissen jetzt, wie man **ein Donut-Diagramm erstellt** und **ein Kreisdiagramm einfügt** in Java mithilfe einer flüssigen Builder‑API. Das vollständige Beispiel deckt Initialisierung, Größenkonfiguration, Lochgröße, Scheibenexplosion und Dateiausgabe ab. Von hier aus können Sie weitere Anpassungen wie Farben, Legenden und Datenbeschriftungen erkunden, um Ihre Berichtserfordernisse zu erfüllen.

**Nächste Schritte**

* Experimentieren Sie mit **chart customization Java**‑Funktionen wie Farbverläufen und Datenbeschriftungen.  
* Integrieren Sie die Diagrammerstellung in einen Webservice, der die Arbeitsmappe bei Bedarf zurückgibt.  
* Vergleichen Sie den Builder‑Ansatz mit anderen Bibliotheken (z. B. JFreeChart), um die beste Lösung für Ihr Projekt zu finden.

Viel Spaß beim Diagramm‑Erstellen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Donut‑Diagramm in einem Word‑Dokument mit Java erstellt](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Word‑Dokument nach dem Bearbeiten eines Donut‑Diagramms in Java speichern](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Kreisdiagramm in Java einfügen – Explodieren, Drehen & Scheiben hervorheben](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}