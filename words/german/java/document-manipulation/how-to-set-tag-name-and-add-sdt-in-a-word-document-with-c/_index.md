---
category: general
date: 2026-09-08
description: Tag‑Namen festlegen und ein Inhaltssteuerelement (SDT) in einem Word‑Dokument
  mit C# erstellen. Erfahren Sie, wie man ein SDT hinzufügt, Text zum Tag schreibt
  und das Dokument bearbeitet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: de
lastmod: 2026-09-08
og_description: Setze den Tag-Namen und erstelle ein Inhaltssteuerelement (SDT) in
  einem Word-Dokument mit C#. Befolge diese Schritt‑für‑Schritt‑Anleitung, um ein
  SDT hinzuzufügen, Text zum Tag zu schreiben und das Dokument zu bearbeiten.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Tag‑Name festlegen und SDT in ein Word‑Dokument hinzufügen – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man den Tag‑Namen festlegt und ein SDT in ein Word‑Dokument mit C# hinzufügt
url: /de/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man den Tag-Namen festlegt und ein SDT in einem Word‑Dokument mit C# hinzufügt

Wenn Sie **den Tag‑Namen** für ein StructuredDocumentTag (SDT) in Word‑Dateien festlegen müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen ein vollständiges, ausführbares Beispiel, das **ein Inhaltssteuerelement erstellt**, Text in den Tag schreibt und **das Word‑Dokument** von Anfang bis Ende **modifiziert**.

Entwickler fragen häufig: *„Wie füge ich ein sdt* zu einer bestehenden .docx‑Datei hinzu und *schreibe Text in den Tag*?“ – Die Antwort liegt in der Verwendung der Aspose.Words for .NET API. Am Ende dieses Tutorials können Sie eine Word‑Datei öffnen, ein Plain‑Text‑SDT einfügen, dessen Tag‑Name festlegen, es mit Inhalt füllen und die Änderungen speichern, ohne dass Ressourcen hängen bleiben.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher installiert.
* Eine gültige Aspose.Words for .NET Lizenz (oder Sie arbeiten mit der Evaluierungs‑Version).
* Visual Studio 2022 (oder eine IDE, die C# unterstützt).
* Ein Eingabe‑Word‑Dokument (`input.docx`) in einem Ordner, den Sie im Code referenzieren können.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolen‑App‑Projekt und fügen Sie das Aspose.Words‑NuGet‑Paket hinzu:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Fügen Sie dann die erforderlichen `using`‑Direktiven oben in `Program.cs` ein:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Diese Namespaces geben Ihnen Zugriff auf `Document`, `DocumentBuilder` und die Klasse `StructuredDocumentTag`, die für das **Modifizieren eines Word‑Dokuments** unerlässlich sind.

## Schritt 2: Das vorhandene Word‑Dokument laden

Der erste Vorgang besteht darin, die Datei zu laden, die Sie bearbeiten möchten. Dieser Schritt ist für jedes Szenario erforderlich, in dem Sie **Word‑Dokument‑Inhalte** ändern.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Warum wir das Dokument zuerst laden** – Das `Document`‑Objekt repräsentiert das gesamte .docx‑Paket im Speicher. Nur nach dem Laden können Sie sicher neue Knoten wie ein SDT einfügen.

## Schritt 3: Ein StructuredDocumentTag (SDT) einfügen und dessen Tag‑Name festlegen

Jetzt beantworten wir die Kernfrage: **wie füge ich sdt** hinzu und **den Tag‑Namen setze**. Wir verwenden `DocumentBuilder.InsertStructuredDocumentTag` mit `SdtType.PlainText`. Das zweite Argument ist der Tag‑Name, den Sie später programmgesteuert oder über die Word‑Benutzeroberfläche referenzieren können.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Erklärung** – `InsertStructuredDocumentTag` gibt eine Instanz von `StructuredDocumentTag` zurück. Durch die Übergabe von `"MyTag"` **setzen wir den Tag‑Namen** direkt beim Erstellen. Wenn Sie ihn später ändern müssen, können Sie `sdt.Tag` einen neuen Wert zuweisen.

## Schritt 4: Text in den neu erstellten Tag schreiben

Nachdem das SDT existiert, möchten Sie typischerweise **Text in den Tag schreiben**, damit Endbenutzer Platzhalter‑ oder Standardinhalt sehen. Die Methode `SetText` erledigt genau das.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Warum SetText verwenden** – Das direkte Zuweisen zur Eigenschaft `Text` würde die gesamte Knoten‑Hierarchie ersetzen. `SetText` aktualisiert sicher den inneren Text des Inhaltssteuerelements, während die Struktur erhalten bleibt.

## Schritt 5: Das modifizierte Dokument speichern

Abschließend persistieren Sie die Änderungen in einer neuen Datei. Damit ist der **modify word document**‑Workflow abgeschlossen.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wenn Sie `output.docx` in Microsoft Word öffnen, sehen Sie ein Plain‑Text‑Inhaltssteuerelement mit der Beschriftung **MyTag**, das den Text „Sample content“ enthält. Das Steuerelement kann manuell bearbeitet werden, und der Tag‑Name bleibt über die Entwickler‑Tools von Word zugänglich.

## Vollständiger Quellcode

Unten finden Sie das komplette, eigenständige Programm. Kopieren Sie es in `Program.cs` und führen Sie es aus; weitere Snippets sind nicht nötig.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Erwartete Ausgabe in der Konsole

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Wie das resultierende Word‑Dokument aussieht

![Word document showing a content control named MyTag with the text “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Beispiel für das Festlegen des Tag‑Namens in einem Word‑Dokument"}

*Der Screenshot illustriert das SDT mit dem **Tag‑Namen** *MyTag* und dem eingebetteten Text, der sichtbar ist.*

## Häufige Varianten und Sonderfälle

| Situation | Vorgehensweise |
|-----------|----------------|
| **Ein Rich‑Text‑SDT erstellen** | Verwenden Sie `SdtType.RichText` anstelle von `PlainText`. |
| **Einen anderen Tag‑Namen nach dem Einfügen setzen** | `sdt.Tag = "NewTag";` – Sie können den Tag‑Namen jederzeit neu zuweisen. |
| **Das SDT in einem bestimmten Absatz einfügen** | Bewegen Sie den Cursor des Builders (`builder.MoveToParagraph(index)`) bevor Sie `InsertStructuredDocumentTag` aufrufen. |
| **Mehrere SDTs im selben Dokument** | Wiederholen Sie die Schritte 3‑4 für jedes Steuerelement; jedes kann einen eindeutigen Tag‑Namen besitzen. |
| **Arbeiten mit geschützten Dokumenten** | Stellen Sie sicher, dass das Dokument ungeschützt ist (`doc.Unprotect()`), bevor Sie ein SDT einfügen. |

## Pro‑Tipps für robuste Word‑Automatisierung

* **Lizenz früh setzen** – Rufen Sie `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` zu Beginn von `Main` auf, um Evaluierungs‑Wasserzeichen zu vermeiden.
* **Objekte freigeben** – Verpacken Sie `Document` in einen `using`‑Block, wenn Sie .NET Framework anvisieren, um Dateihandles zuverlässig zu schließen.
* **Tag‑Existenz prüfen** – Beim späteren Lesen eines Dokuments verwenden Sie `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`, um Tags über die Eigenschaft `Tag` zu finden.
* **Performance** – Laden Sie bei großen Dokumenten nur benötigte Abschnitte mit `LoadOptions` und `LoadFormat.Docx` bzw. `LoadFormat.Auto`.  

## Fazit

Sie wissen jetzt, wie man **den Tag‑Namen setzt**, **ein Inhaltssteuerelement erstellt**, **Text in den Tag schreibt** und **ein Word‑Dokument** mit C# **modifiziert**. Das vollständige Beispiel demonstriert das Standard‑Muster für **wie man sdt hinzufügt** und Änderungen sicher persistiert.  

Von hier aus


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Inhalte mit Document Builder in Aspose.Words für .NET hinzufügen](/words/english/net/add-content-using-document-builder/)
- [Word‑Dokument – Wie man Inhalte entfernt](/words/english/net/remove-content/)
- [Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}