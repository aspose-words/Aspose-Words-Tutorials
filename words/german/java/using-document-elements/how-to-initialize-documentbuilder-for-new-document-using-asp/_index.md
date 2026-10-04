---
category: general
date: 2026-10-04
description: Erfahren Sie, wie Sie DocumentBuilder für ein neues Dokument initialisieren
  und mit Aspose.Words in Java eine ActiveX-Schaltfläche hinzufügen. Schritt‑für‑Schritt-Anleitung
  mit vollständigem Code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: de
lastmod: 2026-10-04
og_description: Initialisieren Sie DocumentBuilder für ein neues Dokument und betten
  Sie mithilfe der Aspose.Words Java API einen ActiveX-Befehlsschalter ein. Folgen
  Sie diesem kurzen Tutorial.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: DocumentBuilder für ein neues Dokument initialisieren – vollständiger Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Wie man DocumentBuilder für ein neues Dokument mit Aspose.Words initialisiert
url: /de/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man DocumentBuilder für ein neues Dokument mit Aspose.Words initialisiert

Wenn Sie **DocumentBuilder für ein neues Dokument** in einem Java‑Projekt initialisieren müssen, zeigt Ihnen dieses Tutorial die genauen Schritte. Sie sehen, wie man eine leere Word‑Datei erstellt, einen ActiveX‑Befehlsschalter anhängt und das Ergebnis speichert – alles mit einem einzigen, eigenständigen Code‑Beispiel.

Das programmatische Arbeiten mit Word‑Dokumenten bedeutet häufig, Low‑Level‑Details wie Formularsteuerelemente zu handhaben. Am Ende dieses Leitfadens können Sie einen ActiveX‑Button einbetten, ohne Ihre IDE zu verlassen – praktisch für die Generierung von Vorlagen, automatisierten Berichten oder interaktiven Formularen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert  
* Maven 3.8+ (oder Gradle, falls Sie das bevorzugen)  
* Eine Aspose.Words for Java‑Lizenz (die kostenlose Testversion funktioniert zum Testen)  
* Grundlegende Kenntnisse der Java‑Syntax  

Wenn Sie neu bei Aspose.Words sind, bietet die Bibliothek eine High‑Level‑API zum Erstellen, Bearbeiten und Speichern von Word‑Dokumenten. Die Klasse `DocumentBuilder` ist der primäre Einstiegspunkt zum Aufbau von Dokumenteninhalten.

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt (oder fügen Sie es einem bestehenden hinzu) und binden Sie die Aspose.Words‑Abhängigkeit ein:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Profi‑Tipp:** Halten Sie die Bibliotheksversion aktuell; neuere Releases unterstützen zusätzliche Formularsteuerelemente und verbessern die Leistung.

## Schritt 2: `DocumentBuilder` für ein neues Dokument initialisieren

Der Kern des Tutorials ist die **initialize DocumentBuilder for new document**‑Operation. Sie erstellen zunächst eine leere `Document`‑Instanz und übergeben sie dann dem Konstruktor von `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist:* Durch das Initialisieren von `DocumentBuilder` wird der Builder an ein bestimmtes `Document`‑Objekt gebunden, sodass Sie Absätze, Tabellen oder Formularsteuerelemente direkt zu diesem Dokument hinzufügen können. Ohne diesen Schritt hätte der Builder kein Ziel, auf dem er arbeiten könnte.

## Schritt 3: Ein ActiveX‑Befehlsschalter‑Steuerelement einfügen

Aspose.Words stellt die Klasse `Forms2OleControl` bereit, um legacy ActiveX‑Steuerelemente einzubetten. Der folgende Code fügt einen **Forms2OleControl‑Befehlsschalter** an der aktuellen Cursor‑Position ein.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Was ist ein ActiveX‑Befehlsschalter?

Ein ActiveX‑Befehlsschalter ist ein veraltetes UI‑Element, das Makros ausführen oder Ereignisse auslösen kann, wenn ein Benutzer ihn innerhalb eines Word‑Dokuments anklickt. Obwohl moderne Office‑Versionen Content Controls bevorzugen, setzen viele Unternehmensvorlagen weiterhin auf ActiveX für Abwärtskompatibilität.

## Schritt 4: Dokument speichern

Nach dem Einfügen des Steuerelements rufen Sie einfach `save` auf. Die Datei enthält den ActiveX‑Button und kann in Microsoft Word geöffnet werden.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Wenn Sie `ActiveXButton.docx` in Word öffnen, sehen Sie einen Button mit der Aufschrift **Click Me**. Das Anklicken des Buttons bewirkt nichts, solange Sie kein Makro anhängen, aber das Steuerelement selbst ist voll funktionsfähig.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in `src/main/java/com/example/ActiveXButtonDemo.java` kopieren‑und‑einfügen können. Es enthält alle Importe und die Fehlerbehandlung, die für einen schnellen Test nötig sind.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Erwartete Ausgabe**

```
Document saved to output/ActiveXButton.docx
```

Öffnen Sie die erzeugte Datei in Microsoft Word 2016 oder neuer; Sie sollten einen Button mit der Aufschrift *Click Me* oben auf der ersten Seite sehen.

## Häufige Variationen und Randfälle

| Szenario | Anpassung |
|----------|------------|
| **Den Button zu einem bestimmten Absatz hinzufügen** | Bewegen Sie den Cursor des Builders mit `builder.moveToParagraph(index, NodeType.PARAGRAPH);` bevor Sie `insertForms2OleControl` aufrufen. |
| **Button‑Größe festlegen** | Verwenden Sie `commandButton.setWidth(100);` und `commandButton.setHeight(30);`, um die Abmessungen in Punkten zu definieren. |
| **Ein Makro zum Button hinzufügen** | Nach dem Speichern des Dokuments öffnen Sie es in Word, aktivieren Sie die Registerkarte Entwickler und hängen Sie manuell ein VBA‑Makro an den Button an (ActiveX‑Steuerelemente können nicht direkt über Aspose.Words gescriptet werden). |
| **Ziel‑Format .doc (binär)** | Ändern Sie `doc.save(outputPath, SaveFormat.DOC);`, um eine Legacy‑Word‑97‑2003‑Datei zu erzeugen. |
| **Ausführen auf Android** | Nutzen Sie Aspose.Words für Android über dessen Java‑API; derselbe Code funktioniert, solange die Bibliothek im APK enthalten ist. |

## Tipps zur Fehlerbehebung

* **`java.lang.NoClassDefFoundError`** – Stellen Sie sicher, dass das Aspose.Words‑JAR im Klassenpfad liegt. Maven fügt es automatisch hinzu; bei manuellen Builds legen Sie das JAR in `libs/` ab und binden es in die Bibliotheken Ihrer IDE ein.  
* **Button erscheint nicht in Word** – Prüfen Sie, ob die Option *Show legacy forms* im Trust Center von Word aktiviert ist (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Lizenz‑Ausnahme** – Wenn Sie den Code ohne gültige Lizenz ausführen, fügt Aspose.Words ein Wasserzeichen ein. Registrieren Sie eine kostenlose Testversion oder erwerben Sie eine Lizenz, um das Wasserzeichen zu entfernen.

## Fazit

Sie wissen jetzt, wie man **DocumentBuilder für ein neues Dokument** initialisiert, einen ActiveX‑Befehlsschalter einfügt und das Ergebnis mit Aspose.Words für Java speichert. Dieses Muster ermöglicht die programmgesteuerte Erstellung interaktiver Word‑Vorlagen, was besonders praktisch für automatisierte Berichte oder formulargesteuerte Workflows ist.

Ab hier können Sie weitere Formularsteuerelemente erkunden (`Forms2OleControlType.CHECKBOX`, `COMBOBOX` usw.), den Button mit benutzerdefinierten VBA‑Makros kombinieren oder vollwertige Dokumente erzeugen, die Tabellen, Bilder und Formatierungen enthalten – alles mit demselben `DocumentBuilder`‑Workflow.

---

*Bereit, komplexere Word‑Automatisierungen zu bauen? Schauen Sie sich unsere Anleitungen zu **Tabelle einfügen mit DocumentBuilder**, **Stile programmgesteuert anwenden** und **Export nach PDF mit Aspose.Words** an.*

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wie man ein Dokument als PDF mit Aspose.Words für Java speichert](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Wie man einem Dokument ein Wasserzeichen mit Aspose.Words für Java hinzufügt](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}