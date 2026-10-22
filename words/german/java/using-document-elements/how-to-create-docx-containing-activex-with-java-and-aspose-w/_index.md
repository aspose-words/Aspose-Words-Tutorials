---
category: general
date: 2026-09-27
description: Erstellen Sie ein DOCX mit ActiveX in Java mithilfe von Aspose.Words.
  Lernen Sie, wie Sie Schritt für Schritt eine ActiveX‑Befehlsschaltfläche einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: de
lastmod: 2026-09-27
og_description: Erstellen Sie ein DOCX mit ActiveX in Java mithilfe von Aspose.Words.
  Folgen Sie dieser Anleitung, um eine ActiveX‑Befehlsschaltfläche einzufügen und
  das Dokument zu speichern.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: docx mit ActiveX in Java erstellen – vollständige Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Wie man ein docx mit ActiveX in Java und Aspose.Words erstellt
url: /de/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man docx mit ActiveX mit Java und Aspose.Words erstellt

Wenn Sie **docx mit ActiveX erstellen** müssen, zeigt Ihnen dieser Leitfaden eine vollständige Lösung. Sie lernen, wie Sie **ActiveX‑Befehlsschaltfläche** in eine Word‑Datei mit Aspose.Words für Java einfügen und das Ergebnis als .docx speichern, das in Microsoft Word geöffnet werden kann.

Das programmgesteuerte Erzeugen eines Word‑Dokuments erspart Ihnen manuelle Bearbeitung und gewährleistet Konsistenz bei Berichten, Verträgen oder Formularvorlagen. Die nachstehenden Schritte decken alles ab, von der Projektkonfiguration bis zum Umgang mit typischen Fallstricken, sodass Sie die Technik in jede Java‑Anwendung integrieren können.

## Voraussetzungen

* Java Development Kit (JDK) 8 oder neuer installiert.
* Maven 3.6+ (oder ein anderes bevorzugtes Build‑Tool).
* Eine Aspose.Words für Java Lizenzdatei (die kostenlose Testversion funktioniert zum Testen).
* Microsoft Word auf dem Zielrechner installiert, falls Sie die ActiveX‑Steuerung visuell überprüfen möchten.

Diese Elemente sind erforderlich, weil Aspose.Words die API bereitstellt, die das Dokument erstellt, während Word zum Rendern der ActiveX‑Steuerung benötigt wird.

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt oder fügen Sie die Aspose.Words‑Abhängigkeit zu einer bestehenden `pom.xml` hinzu:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Profi‑Tipp:** Halten Sie die Aspose.Words‑Version synchron mit den offiziellen Release‑Notes, um von Fehlerbehebungen und neuen ActiveX‑Funktionen zu profitieren.

## Schritt 2: Java‑Code schreiben, der das Dokument erstellt

Erstellen Sie eine Klasse mit dem Namen `ActiveXDocxCreator`. Der untenstehende Code enthält alle erforderlichen Importe, eine `main`‑Methode und ausführliche Kommentare, die jede Operation erklären.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Warum jede Zeile wichtig ist

* `Document` ist der Container für allen Word‑Inhalt. Das Erzeugen einer neuen Instanz gibt Ihnen eine leere Leinwand.
* `DocumentBuilder` bietet eine fluente API zum Einfügen von Elementen; sie verfolgt automatisch den Einfügepunkt.
* `insertForms2OleControl()` erstellt einen generischen OLE‑Steuerungs‑Platzhalter. Aspose.Words behandelt ihn als ActiveX‑Container.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` weist Word an, den Platzhalter als CommandButton darzustellen.
* `setCaption("Click Me")` definiert den auf der Schaltfläche angezeigten Text.
* `setLeft` und `setTop` positionieren die Schaltfläche relativ zu den Seitenrändern. Passen Sie diese Werte an Ihr Layout an.
* `setWidth` und `setHeight` sind optional, verbessern jedoch das Aussehen der Schaltfläche, insbesondere wenn die Standardgröße zu klein ist.
* `doc.save` schreibt die In‑Memory‑Struktur in eine physische .docx‑Datei, die Word öffnen kann.

## Schritt 3: Das erzeugte Dokument überprüfen

Öffnen Sie `output/ActiveXCommandButton.docx` in Microsoft Word:

1. Das Dokument sollte eine einzelne Seite mit einer Schaltfläche anzeigen, die **Click Me** beschriftet ist und sich in der Nähe der oberen linken Ecke befindet.
2. Wenn die Schaltfläche nicht erscheint, prüfen Sie, ob **ActiveX‑Steuerelemente aktiviert** sind im Trust Center von Word (Datei → Optionen → Trust Center → Trust Center‑Einstellungen → ActiveX‑Einstellungen).
3. Die Schaltfläche funktioniert nur in Windows‑Versionen von Word, die ActiveX unterstützen. Auf macOS oder webbasiertem Word wird die Steuerung als statisches Bild angezeigt.

## Schritt 4: Umgang mit häufigen Randfällen

| Situation | Grund | Empfohlene Aktion |
|-----------|-------|--------------------|
| Die Schaltfläche fehlt nach dem Öffnen der Datei | Word‑Sicherheitseinstellungen blockieren ActiveX | „Alle Steuerelemente ohne Einschränkungen ausführen“ für vertrauenswürdige Speicherorte aktivieren. |
| Das erzeugte .docx lässt sich nicht öffnen | Inkompatible Aspose.Words‑Version | Auf die neueste Aspose.Words‑Version aktualisieren; ältere Versionen betten die erforderlichen OLE‑Teile möglicherweise nicht korrekt ein. |
| Sie benötigen, dass die Schaltfläche ein Makro ausführt | ActiveX allein enthält keinen Makro‑Code | Das ActiveX‑Steuerelement mit einem VBA‑Makro kombinieren, das das `Click`‑Ereignis verarbeitet. Verwenden Sie die Methode `DocumentBuilder.insertOleObject`, um eine makrofähige Vorlage einzubetten. |
| Das Layout ist bei unterschiedlichen Seitengrößen verschoben | Koordinaten sind absolute Punkte | Verwenden Sie `builder.getPageSetup().setPageWidth` und `setPageHeight`, um die Seitengröße vor der Positionierung des Steuerelements zu standardisieren. |

## Schritt 5: Lösung erweitern

Sie können andere ActiveX‑Steuerelemente einfügen, indem Sie das `ControlType`‑Enum ändern:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words unterstützt außerdem das Einfügen von **ActiveX‑Textfeldern**, **Listboxen** und **Combo‑Boxen**. Die gleichen Positionierungsmethoden (`setLeft`, `setTop`, `setWidth`, `setHeight`) gelten.

Wenn Sie mehrere Steuerelemente platzieren müssen, rufen Sie `builder.insertForms2OleControl()` wiederholt auf und passen die Koordinaten jedes Steuerelements entsprechend an.

## Vollständige Quelldatei

Unten finden Sie die komplette Datei `ActiveXDocxCreator.java`, bereit zum Kopieren und Einfügen:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

## Fazit

Sie wissen jetzt, wie man **docx mit ActiveX** mit Java und Aspose.Words erstellt und wie man **ActiveX‑Befehlsschaltfläche** programmgesteuert einfügt. Das Tutorial behandelte die Projektkonfiguration, den vollständigen Quellcode, Verifizierungsschritte und Strategien zum Umgang mit typischen Problemen.

Von hier aus können Sie folgendes erkunden:

* Hinzufügen von VBA‑Makros, die auf das Klicken der Schaltfläche reagieren.
* Einbetten anderer ActiveX‑Steuerelemente wie Kontrollkästchen oder Kombinationsfelder.
* Automatisieren der Erstellung mehrseitiger Formulare mit dynamischen Daten.

Experimentieren Sie mit verschiedenen Koordinaten, Größen und Steuerelementtypen, um Ihr spezifisches Dokumentlayout anzupassen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}