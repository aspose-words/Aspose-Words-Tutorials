---
category: general
date: 2026-10-07
description: Erfahren Sie, wie Sie eine OLE‑Schaltfläche in ein Word‑Dokument mit
  Aspose.Words C# einfügen. Schritt‑für‑Schritt‑Anleitung, die DocumentBuilder, Eigenschaften
  und das Speichern der Datei abdeckt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: de
lastmod: 2026-10-07
og_description: Fügen Sie in einem Word-Dokument über C# einen OLE-Befehlsschalter
  ein. Folgen Sie diesem kurzen Tutorial, um einen funktionalen CommandButton mit
  Aspose.Words hinzuzufügen, zu konfigurieren und zu speichern.
og_image_alt: Insert OLE command button example in Word document
og_title: OLE‑Befehlsschaltfläche in Word mit C# einfügen – vollständige Aspose.Words‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Wie man eine OLE‑Befehlsschaltfläche in ein Word‑Dokument mit C# einfügt
url: /de/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man einen OLE‑Befehlsschaltfläche in ein Word‑Dokument mit C# einfügt

Wenn Sie **eine OLE‑Befehlsschaltfläche** programmgesteuert in eine Word‑Datei einfügen müssen, zeigt Ihnen diese Anleitung genau, wie das mit Aspose.Words für .NET funktioniert. Egal, ob Sie einen formularbasierten Bericht erstellen oder eine Vorlage automatisieren, die Benutzerinteraktion erfordert – die nachfolgenden Schritte liefern eine vollständige, ausführbare Lösung.

Sie lernen, wie Sie ein leeres Dokument erstellen, den `DocumentBuilder` verwenden, um ein `Forms2OleControl` zu platzieren, die Beschriftung und den Namen der Schaltfläche festzulegen und schließlich das `.docx` zu speichern. Es werden keine externen Werkzeuge außer der Aspose.Words‑Bibliothek benötigt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz oder einen kostenlosen Evaluierungsschlüssel
* Visual Studio 2022 (oder eine andere C#‑IDE Ihrer Wahl)
* Grundlegende Kenntnisse der C#‑Syntax und von Word‑OLE‑Konzepten

> **Pro‑Tipp:** Wenn Sie die kostenlose Evaluation verwenden, enthält das erzeugte Dokument ein kleines Wasserzeichen. Eine lizenzierte Version entfernt es automatisch.

## Schritt 1: Aspose.Words installieren

Fügen Sie das Aspose.Words‑Paket Ihrem Projekt über NuGet hinzu:

```bash
dotnet add package Aspose.Words
```

Das Paket enthält die Namespaces `Aspose.Words.Drawing` und `Aspose.Words.Drawing.Ole`, die für OLE‑Steuerelemente erforderlich sind.

## Schritt 2: OLE‑Befehlsschaltfläche mit DocumentBuilder einfügen

Der Kern des Tutorials ist die Methode `InsertForms2OleControl`. Sie erstellt eine **Forms2 OLE CommandButton** an einer bestimmten Position und Größe.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Warum das funktioniert

* `DocumentBuilder` ist die primäre API zum programmatischen Erstellen von Word‑Dokumenten.  
* `InsertForms2OleControl` weist Aspose.Words an, ein **Forms2 OLE‑Steuerelement** einzubetten, die veraltete Word‑Formtechnologie, die Befehlsschaltflächen, Kontrollkästchen usw. unterstützt.  
* Der Enum‑Wert `OleControlType.CommandButton` gibt an, dass das eingefügte Steuerelement eine **Befehlsschaltfläche** ist – exakt der Typ, den Sie beim **Einfügen einer OLE‑Befehlsschaltfläche** angefordert haben.  
* Das `Rectangle` bestimmt die visuelle Platzierung. Passen Sie die X/Y‑Koordinaten oder Breite/Höhe an Ihr Layout an.

## Schritt 3: Das Dokument speichern

Nachdem die Schaltfläche konfiguriert wurde, schreiben Sie das Dokument auf die Festplatte. Sie können jedes von Aspose.Words unterstützte Format wählen (`.docx`, `.pdf`, `.odt`, …). Für dieses Tutorial speichern wir als Word‑Dokument.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie `CommandButton.docx` in Microsoft Word öffnen, sehen Sie eine anklickbare Schaltfläche mit der Beschriftung **Click Me**. Das Drücken der Schaltfläche löst in Word den Standard‑Dialog „Makro ausführen“ aus, weil es sich um ein OLE‑Formularsteuerelement handelt; Sie können später ein Makro oder VBA‑Code anhängen, falls gewünscht.

## Schritt 4: Ergebnis überprüfen (erwartete Ausgabe)

Öffnen Sie die erzeugte Datei:

1. Die Schaltfläche erscheint an den von Ihnen angegebenen Koordinaten (ungefähr 1,4 in von links und oben der Seite).  
2. Die Beschriftung lautet **Click Me**.  
3. Die Eigenschaft `Name` (`cmdSubmit`) ist im Word‑Fenster **Entwicklertools → Eigenschaften** sichtbar, was nützlich ist, wenn Sie das Steuerelement aus VBA referenzieren müssen.

![Beispiel für das Einfügen einer OLE‑Befehlsschaltfläche in ein Word‑Dokument](insert-ole-button.png)

*Bild‑Alt‑Text*: **Beispiel für das Einfügen einer OLE‑Befehlsschaltfläche in ein Word‑Dokument** (enthält das Haupt‑Keyword für Barrierefreiheit und SEO).

## Sonderfälle & häufige Fragen

### 1. Was tun, wenn die Schaltfläche nicht an der erwarteten Stelle erscheint?

* Word verwendet Punkte, nicht Pixel. Konvertieren Sie Bildschirm‑Pixel in Punkte (`points = pixels * 72 / DPI`).  
* Stellen Sie sicher, dass das Rechteck nicht mit den Seitenrändern überschneidet; andernfalls kann Word das Steuerelement verschieben.

### 2. Kann ich die Schaltfläche in ein bestehendes Dokument einfügen?

Ja. Laden Sie das Dokument mit `new Document("Existing.docx")` und verwenden Sie denselben `DocumentBuilder`‑Ablauf. Denken Sie nur daran, den Cursor des Builders zu verschieben (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` usw.), bevor Sie `InsertForms2OleControl` aufrufen.

### 3. Wie hänge ich ein Makro an die Schaltfläche an?

Aspose.Words erzeugt keinen VBA‑Code, aber Sie können nach der Dokumenterstellung ein Makro einbetten:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Funktioniert das mit .NET Core unter Linux?

Das OLE‑Steuerelement ist eine Windows‑spezifische Funktion, weil es auf COM basiert. Unter Linux wird die Schaltfläche zwar eingefügt, erscheint jedoch als statisches Bild ohne interaktives Verhalten. Für plattformübergreifende interaktive Formulare sollten Sie stattdessen Inhaltssteuerelemente (`StructuredDocumentTag`) verwenden.

### 5. Was, wenn ich eine andere Größe oder mehrere Schaltflächen benötige?

Erstellen Sie zusätzliche `Rectangle`‑Objekte mit eindeutigen Koordinaten und wiederholen Sie den Aufruf von `InsertForms2OleControl`. Jede Schaltfläche kann ihre eigene `Caption` und `Name` besitzen.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es enthält alle notwendigen `using`‑Direktiven, Fehlerbehandlung und Kommentare.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Führen Sie das Programm aus, öffnen Sie das erzeugte `CommandButton.docx` und Sie sehen die **Click Me**‑Schaltfläche, bereit für weitere Anpassungen.

## Fazit

Sie wissen jetzt, wie man **eine OLE‑Befehlsschaltfläche** in ein Word‑Dokument mit C# und Aspose.Words einfügt. Das Tutorial behandelte:

* Installation des Aspose.Words‑Pakets  
* Verwendung von `DocumentBuilder.InsertForms2OleControl` mit `OleControlType.CommandButton`  
* Einstellung der Schaltflächeneigenschaften (`Caption`, `Name`)  
* Speichern und Überprüfen der Ausgabe  

Ab hier können Sie verwandte Themen erkunden, etwa **Aspose.Words OLE‑Steuerelement** für Kontrollkästchen, Kombinationsfelder oder das Einbetten ganzer Excel‑Arbeitsblätter. Sie können außerdem die **Word OLE‑Befehlsschaltfläche**‑Automatisierung in größeren Vorlagen testen oder OLE‑Steuerelemente durch moderne **Inhaltssteuerelemente** ersetzen, um bessere plattformübergreifende Unterstützung zu erhalten.

Passen Sie die Rechteckwerte an, fügen Sie mehrere Schaltflächen hinzu oder binden Sie VBA‑Makros ein, um den Anforderungen Ihrer Anwendung gerecht zu werden. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}