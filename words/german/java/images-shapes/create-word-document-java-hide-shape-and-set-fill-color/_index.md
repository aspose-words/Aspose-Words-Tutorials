---
category: general
date: 2026-08-07
description: 'Word-Dokument in Java mit Aspose.Words erstellen: eine Ellipse einfügen,
  die Füllfarbe der Form festlegen und die Form in Word ausblenden – anhand eines
  kurzen Beispiels.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: de
lastmod: 2026-08-07
og_description: Erstellen Sie ein Word-Dokument in Java mit Aspose.Words. Lernen Sie,
  eine Form einzufügen, ihre Füllfarbe festzulegen und die Form in Word auszublenden
  – alles in einem einzigen, ausführbaren Beispiel.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Word-Dokument in Java erstellen – Form ausblenden und Füllfarbe festlegen
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Word-Dokument mit Java erstellen – Form ausblenden und Füllfarbe festlegen
url: /de/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument mit Java erstellen – Form ausblenden und Füllfarbe setzen

Wenn Sie ein **Word‑Dokument mit Java** programmatisch erstellen und Formen verwalten möchten, zeigt Ihnen dieses Tutorial, wie das geht. Sie lernen, wie Sie eine Form einfügen, deren Füllfarbe setzen und die Form in Word ausblenden – mit Aspose.Words für Java.

Der Leitfaden führt Sie durch jeden Schritt, vom Initialisieren eines `Document`‑Objekts bis zum Überprüfen, dass die Form beim Öffnen der Datei unsichtbar ist. Keine externen Ressourcen sind nötig, außer der Aspose.Words‑Bibliothek, und der komplette Quellcode wird bereitgestellt, sodass Sie ihn sofort ausführen können.

**Voraussetzungen**

- Java 8 oder neuer
- Maven oder Gradle zur Verwaltung der Abhängigkeiten (oder das Aspose.Words‑JAR im Klassenpfad)
- Grundlegende Kenntnisse der Java‑Syntax
- Eine IDE oder ein Texteditor für die Java‑Entwicklung

Das Tutorial erklärt außerdem **wie man eine Form ausblendet** in einer Word‑Datei, **wie man eine Form einfügt** mit genauen Abmessungen und **wie man die Füllfarbe einer Form setzt** für die visuelle Gestaltung.

---

![Create word document java – hidden shape preview](image-placeholder.png){.align-center width=600 alt="Word‑Dokument mit Java erstellen – versteckte Form Vorschau"}

## Word‑Dokument mit Java erstellen – Dokument und Builder initialisieren

Der erste Schritt besteht darin, ein leeres Word‑Dokument und einen `DocumentBuilder` zu erstellen, mit dem Sie Inhalte hinzufügen können. Das Initialisieren dieser Objekte reserviert die internen Strukturen, die Aspose.Words benötigt, um Seiten, Absätze und Formen zu verwalten.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist:* Ohne einen `DocumentBuilder` können Sie keine Formen, Texte oder andere Objekte einfügen. Der Builder arbeitet auf der im Speicher befindlichen `Document`‑Instanz und stellt sicher, dass alle Änderungen erfasst werden, bevor Sie speichern.

## Wie man mit Aspose.Words eine Form einfügt

Aspose.Words unterstützt viele geometrische Formen. Hier fügen wir eine Ellipse mit einer Breite von 150 pt und einer Höhe von 100 pt ein. Die Methode `insertShape` liefert ein `Shape`‑Objekt, das Sie weiter konfigurieren können.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Warum das wichtig ist:* Die Verwendung von `insertShape` garantiert, dass die Form korrekt im Dokumenten‑Fluss verankert wird. Das zurückgegebene `Shape` ermöglicht das Ändern von Eigenschaften wie Füllfarbe, Linienstil und Sichtbarkeit.

## Füllfarbe einer Form in Word setzen

Eine Form ohne Füllung wirkt transparent. Das Setzen einer Füllfarbe lässt die Form hervortreten, wenn sie sichtbar ist. Das Beispiel verwendet `java.awt.Color.GREEN`, um **set shape fill color** zu demonstrieren.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Warum das wichtig ist:* Die Füllfarbe wird in der XML‑Definition der Form gespeichert. Durch das Ändern zur Laufzeit können Sie Dokumente mit markenspezifischen Farben erzeugen oder wichtige Bereiche hervorheben.

## Wie man eine Form in Word ausblendet

Manchmal benötigen Sie eine Form, die das Layout steuert oder als Platzhalter dient, aber nicht für den Endbenutzer sichtbar sein soll. Der Aufruf `setHidden(true)` implementiert **how to hide shape** und erfüllt die Anforderung **hide shape in word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Warum das wichtig ist:* Ausgeblendete Formen bleiben Teil des Objektmodells des Dokuments, das heißt, sie können später referenziert werden (z. B. für Lesezeichen oder programmgesteuerte Manipulation), ohne das visuelle Layout zu überladen.

## Dokument speichern und Ergebnis überprüfen

Nachdem die Form konfiguriert wurde, speichern Sie die Datei auf dem Datenträger. Die gespeicherte `.docx`‑Datei kann in Microsoft Word geöffnet werden; die Ellipse ist unsichtbar, ihre Existenz lässt sich jedoch durch Inspektion des Dokument‑XML oder mittels Aspose.Words zur Auflistung von Formen bestätigen.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Erwartetes Ergebnis:* Beim Öffnen von `ShapeVisibilityDemo.docx` wird eine normale Seite ohne sichtbare Grafiken angezeigt. Wenn Sie das Dokument mit einem ZIP‑Viewer untersuchen und `word/document.xml` öffnen, finden Sie ein `<w:shape>`‑Element mit `hidden="true"` und ein `<v:fillcolor>` von `#00FF00`.

---

## Häufige Varianten und Sonderfälle

- **Verschiedene Formtypen:** Ersetzen Sie `ShapeType.ELLIPSE` durch `ShapeType.RECTANGLE`, `ShapeType.CLOUD` oder einen anderen unterstützten Enum‑Wert, um die gewünschte Geometrie zu erhalten.
- **Bedingte Sichtbarkeit:** Sie können `ellipse.setHidden(false)` basierend auf Laufzeit‑Logik umschalten, um dynamische Dokumente zu erzeugen.
- **Komplexe Füllungen:** Statt einer einfarbigen Füllung verwenden Sie `ellipse.getFill().setTextureImage(...)` für Musterfüllungen. Die Methode `setHidden` steuert weiterhin die Sichtbarkeit.
- **Mehrere Formen:** Erstellen Sie ein Array oder eine Liste von `Shape`‑Objekten, konfigurieren Sie jedes unabhängig und blenden Sie nur jene aus, die bestimmte Kriterien erfüllen.

*Pro‑Tipp:* Beim Erzeugen großer Dokumente sollten Sie eine einzelne `DocumentBuilder`‑Instanz wiederverwenden, anstatt für jede Form eine neue zu erstellen. Das reduziert den Speicherverbrauch und verbessert die Performance.

---

## Fazit

Sie wissen jetzt, wie Sie **Word‑Dokument mit Java** erstellen, das eine Ellipse einfügt, **die Füllfarbe einer Form setzt** und **eine Form in Word ausblendet** – alles mit Aspose.Words. Das vollständige, ausführbare Beispiel demonstriert jeden API‑Aufruf, erklärt, warum jeder Schritt nötig ist, und zeigt das erwartete Ergebnis.

Als Nächstes können Sie verwandte Themen erkunden, etwa **wie man eine Form einfügt** mit Textumbruch, Hyperlinks zu Formen hinzufügt und das Dokument als PDF exportiert, wobei ausgeblendete Elemente erhalten bleiben. Experimentieren Sie mit verschiedenen Farben, Größen und Sichtbarkeits‑Flags, um die Word‑Automatisierung an die Bedürfnisse Ihres Projekts anzupassen.

Bereit, weitere Word‑Funktionen zu automatisieren? Werfen Sie einen Blick in die Aspose.Words für Java‑Dokumentation zu [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) und beginnen Sie noch heute mit dem Erstellen umfangreicher, programmgesteuerter Dokumente.


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}