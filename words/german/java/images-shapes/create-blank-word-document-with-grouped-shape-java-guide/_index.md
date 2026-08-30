---
category: general
date: 2026-07-20
description: Erstellen Sie ein leeres Word‑Dokument in Java mit Aspose.Words. Erfahren
  Sie, wie Sie eine Gruppe erstellen, ein Rechteck‑Shape einfügen und ein Bild in
  das Shape einbetten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: de
lastmod: 2026-07-20
og_description: Erstellen Sie ein leeres Word-Dokument in Java mit Aspose.Words. Diese
  Anleitung zeigt, wie man eine Gruppe erstellt, ein Rechteck‑Shape einfügt und ein
  Bild in das Shape einbettet, um dynamische Word‑Dateien zu erzeugen.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Erstelle ein leeres Word-Dokument mit gruppierter Form – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Leeres Word-Dokument mit gruppierter Form erstellen – Java‑Leitfaden
url: /de/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Word-Dokuments mit gruppierter Form – Java‑Leitfaden

Haben Sie sich jemals gefragt, wie man ein **leeres Word-Dokument** erstellt, das bereits eine schön gruppierte Form enthält? Vielleicht erstellen Sie eine Berichtsvorlage oder benötigen einen Platzhalter für ein Logo und eine Beschriftung. So oder so ist das Problem häufig: Sie beginnen mit einer leeren Datei, dann müssen Sie eine Gruppe hinzufügen, ein Rechteck darin platzieren und schließlich ein Bild einbetten – alles programmgesteuert.

In diesem Tutorial führen wir Sie durch ein komplettes, sofort ausführbares Java-Beispiel, das genau das tut. Sie lernen **wie man eine Gruppe erstellt**, **ein Rechteck-Shape einfügt** und **ein Bild in ein Word-Dokument** innerhalb derselben Gruppe hinzufügt. Am Ende haben Sie eine Word-Datei, die wie eine ausgefeilte Vorlage aussieht und bereit für weitere Anpassungen ist.

> **Was Sie erhalten:** eine voll funktionsfähige Java‑Klasse, Schritt‑für‑Schritt‑Erklärungen, Tipps zum Umgang mit Dateipfaden und eine Vorschau des erwarteten Outputs. Keine externe Dokumentation nötig – alles, was Sie brauchen, finden Sie hier.

---

## Erstellen eines leeren Word-Dokuments – Schritt‑für‑Schritt‑Übersicht

Das Erste, was wir benötigen, ist eine wirklich leere Word-Datei. Aspose.Words macht das trivial: Instanziieren Sie einfach die Klasse `Document` mit ihrem Standard‑Konstruktor. Das liefert Ihnen eine leere Leinwand, gleichbedeutend mit dem Öffnen von Word und dem Klick auf **Neu → Leeres Dokument**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Warum mit einem leeren Dokument beginnen?**  
> Ein leeres Dokument stellt sicher, dass keine versteckten Stile oder Abschnitte die später hinzuzufügenden Formen beeinträchtigen. Es hält außerdem die Dateigröße minimal, was praktisch ist, wenn Sie Dutzende von Dateien in einem Batch‑Job erzeugen.

## Wie man eine Gruppe erstellt und Formen hinzufügt

Eine **Gruppen-Form** ist im Wesentlichen ein Container, der mehrere untergeordnete Formen aufnehmen kann – denken Sie an einen Ordner für Zeichenobjekte. Durch das Gruppieren können Sie das gesamte Set mit einem einzigen Befehl verschieben, skalieren oder drehen.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Die Methode `insertGroupShape` gibt ein `GroupShape`‑Objekt zurück, das wir als übergeordnetes Element für das Rechteck und das Bild verwenden. Die Größe wird in Punkten angegeben (1 Punkt = 1/72 Zoll), sodass 200 Punkte etwa ein 2,78 × 2,78‑Zoll‑Feld ergeben.

> **Pro‑Tipp:** Wenn Sie die Gruppe transparent benötigen, setzen Sie nach der Erstellung `group.setFillColor(Color.getWhite());`.

Jetzt, da die Gruppe existiert, müssen wir dem Builder mitteilen, wo die nächsten Formen platziert werden sollen. Der Cursor des Builders muss sich innerhalb des ersten Absatzes der Gruppe befinden.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

## Rechteck-Form innerhalb der Gruppe einfügen

Ein Rechteck wird häufig als Platzhalter für Text oder als visueller Hinweis verwendet. Wenn es als **erstes Kind** der Gruppe hinzugefügt wird, befindet es sich hinter allen nachfolgenden Bildern.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Das Rechteck erbt das Koordinatensystem der Gruppe, sodass seine Größe von 100 × 50 Punkten standardmäßig zentriert ist. Sie können es weiter gestalten – einen Rahmen hinzufügen, die Füllfarbe ändern oder einen Schatten anwenden – indem Sie auf das zurückgegebene `Shape`‑Objekt zugreifen.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

## Bild zum Word-Dokument hinzufügen – Bild in Form einbetten

Jetzt zum spaßigen Teil: **Bild in Form einbetten**. Wir fügen ein JPEG-Bild als zweites Kind derselben Gruppe ein. Da sich der Cursor noch innerhalb der Gruppe befindet, wird das Bild automatisch ein Kind‑Knoten.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Wenn die Bilddatei nicht gefunden wird, wirft Aspose.Words eine `FileNotFoundException`. Um das zu vermeiden, legen Sie `sample.jpg` entweder im Arbeitsverzeichnis des Projekts ab oder verwenden Sie einen absoluten Pfad.

> **Was, wenn Sie ein anderes Bildformat benötigen?**  
> Aspose.Words unterstützt PNG, BMP, GIF, TIFF und sogar SVG. Ändern Sie einfach die Dateierweiterung und die Bibliothek übernimmt die Konvertierung.

## Dokument speichern und Ergebnis ansehen

Abschließend speichern wir das im Speicher befindliche Dokument auf die Festplatte. Das resultierende `.docx` enthält eine einzelne Seite mit einer gruppierten Form, die sowohl das Rechteck als auch das Bild enthält.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Wenn Sie `output.docx` in Microsoft Word öffnen, sollten Sie eine 200 × 200‑Punkte‑Gruppe in der oberen linken Ecke sehen. Innerhalb der Gruppe befindet sich ein hellgraues Rechteck oben, und direkt darunter erscheint das von Ihnen angegebene Bild, perfekt ausgerichtet.

![Grouped shape example](grouped-shape.png){:alt="Screenshot eines leeren Word-Dokuments mit einer gruppierten Form, die ein Rechteck und ein eingebettetes Bild enthält"}

## Häufige Variationen und Edge‑Case‑Behandlung

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Andere Gruppengröße** | Passen Sie die Parameter von `insertGroupShape(width, height)` an | Größere Gruppen können komplexere Layouts aufnehmen. |
| **Mehrere Bilder** | Rufen Sie `builder.insertImage()` wiederholt auf, nachdem Sie jedes Mal zum Absatz der Gruppe gewechselt haben | Jeder Aufruf fügt ein neues Kind hinzu; Sie können sie auch mit `Shape.setLeft()` / `setTop()` positionieren. |
| **Dynamische Bildpfade** | Verwenden Sie `String.format("images/%s.jpg", imageName)` | Macht den Code wiederverwendbar für die Batch‑Verarbeitung. |
| **Als PDF speichern** | Ersetzen Sie `doc.save("output.pdf")` | Aspose.Words kann on‑the‑fly konvertieren, sodass Sie PDFs direkt erzeugen können. |
| **Gruppe rotieren** | `group.setRotation(45);` | Nützlich für dekorative Wasserzeichen oder stilisierte Kopfzeilen. |

## Erwartetes Ergebnis und Verifizierung

Nach dem Ausführen der Klasse:

1. `output.docx` erscheint im Projektordner.  
2. Beim Öffnen der Datei wird eine einzelne Seite mit einer gruppierten Form angezeigt.  
3. Innerhalb der Gruppe ist das Rechteck oben links positioniert, und das Bild befindet sich direkt darunter.  
4. Wenn Sie die Gruppe in Word auswählen, werden beide Kindobjekte hervorgehoben, was bestätigt, dass sie wirklich gruppiert sind.

Falls einer dieser Schritte fehlschlägt, überprüfen Sie den Bildpfad erneut und stellen Sie sicher, dass das Aspose.Words‑JAR in Ihrem Klassenpfad liegt.

## Fazit

Sie wissen jetzt, **wie man ein leeres Word-Dokument erstellt** und es mit einer gruppierten Form, die ein Rechteck und ein eingebettetes Bild enthält, anreichert. Indem Sie **wie man eine Gruppe erstellt**, **ein Rechteck-Shape einfügt** und **ein Bild in ein Word-Dokument hinzufügt** beherrschen, können Sie vollständig in Code anspruchsvolle Word-Vorlagen erstellen – ohne manuelles Nachbearbeiten.

Bereit für die nächste Herausforderung? Versuchen Sie, Textfelder innerhalb derselben Gruppe hinzuzufügen, oder experimentieren Sie mit verschiedenen Form‑Stilen, um Ihr Corporate Branding anzupassen. Sie könnten sogar eine komplette Berichtsbibliothek generieren, bei der jedes Dokument mit diesem genauen Layout beginnt.

Viel Spaß beim Coden und teilen Sie gerne Ihre eigenen Variationen in den Kommentaren unten!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code-Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument mit Java erstellen – Rechteck-Shape mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wie man PDF-Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}