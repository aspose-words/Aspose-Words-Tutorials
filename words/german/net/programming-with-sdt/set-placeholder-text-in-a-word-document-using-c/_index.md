---
category: general
date: 2026-10-20
description: Platzhaltertext in einem Word-Dokument mit C# festlegen. Erfahren Sie,
  wie Sie ein Steuerelement hinzufügen und den Platzhalter schnell mit Aspose.Words
  für .NET setzen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: de
lastmod: 2026-10-20
og_description: Platzhaltertext in einem Word‑Dokument mit C# festlegen. Dieses Tutorial
  zeigt, wie man Steuerelemente hinzufügt, Platzhalter setzt und Word‑Dateien programmgesteuert
  erzeugt.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Platzhaltertext in einem Word‑Dokument mit C# festlegen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Platzhaltertext in einem Word‑Dokument mit C# setzen
url: /de/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Platzhaltertext in einem Word-Dokument mit C# festlegen

Wenn Sie **Platzhaltertext** in einer Microsoft Word‑Datei festlegen müssen, während Sie sie mit C# erzeugen, zeigt Ihnen dieser Leitfaden genau, wie das geht. Sie sehen eine prägnante, durchgängige Lösung, die ein Content‑Control hinzufügt, dessen Platzhalter definiert und das Dokument speichert – alles mit Aspose.Words für .NET.

Viele Entwickler fragen sich, **wie man ein Control** zu einem Word‑Dokument hinzufügt oder **wie man einen Platzhalter** setzt, ohne Word manuell zu öffnen. Dieses Tutorial beantwortet diese Fragen und zeigt zudem eine saubere Methode, **Word‑C#‑Dateien** zu **generieren**, die bereit für Benutzereingaben sind.

## Was Sie erreichen werden

* Ein leeres Word‑Dokument programmgesteuert erstellen.
* Ein Plain‑Text Structured Document Tag (SDT) einfügen, das der technische Name für ein Content‑Control ist.
* Dem SDT einen aussagekräftigen Titel und Platzhaltertext zuweisen.
* Die resultierende `.docx`‑Datei auf die Festplatte speichern.

Keine zusätzlichen Werkzeuge sind erforderlich, außer der Aspose.Words‑Bibliothek und einer .NET 6‑ (oder höher) Entwicklungsumgebung.

## Voraussetzungen

* .NET 6 SDK oder neuer installiert.  
* Visual Studio 2022 (oder jede IDE, die .NET unterstützt).  
* Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`).  

> **Pro‑Tipp:** Verwenden Sie die kostenlose Evaluierungsversion von Aspose.Words, wenn Sie nur testen; sie fügt ein Wasserzeichen hinzu, funktioniert aber ansonsten genauso wie die lizenzierte Version.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt und fügen Sie die erforderlichen `using`‑Direktiven hinzu. Diese bringen die Kernklassen von Aspose.Words und den Markup‑Namespace in den Gültigkeitsbereich.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Warum dieser Schritt wichtig ist:* Das Importieren von `Aspose.Words.Markup` verschafft Ihnen Zugriff auf `StructuredDocumentTag`, `SdtType` und `MarkupLevel` – die Objekte, die zum **Hinzufügen von Controls** und **Setzen von Platzhaltern** benötigt werden.

## Schritt 2: Ein leeres Dokument und einen DocumentBuilder erstellen

Ein `Document` repräsentiert die gesamte Word‑Datei, während ein `DocumentBuilder` einen praktischen Cursor zum Einfügen von Elementen bereitstellt.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum dieser Schritt wichtig ist:* Das Beginnen mit einem leeren Dokument stellt sicher, dass der von Ihnen gesetzte Platzhalter genau dort erscheint, wo Sie ihn möchten, ohne von vorhandenem Inhalt gestört zu werden.

## Schritt 3: Das Content‑Control (Structured Document Tag) erstellen

Hier erstellen wir ein Plain‑Text‑SDT, geben ihm einen Titel und setzen den Platzhaltertext, den der Benutzer sieht, wenn das Control leer ist.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Warum dieser Schritt wichtig ist:* Die `Title`‑Eigenschaft ermöglicht es Ihnen, das Control später zu referenzieren (z. B. für Data‑Binding). `PlaceholderName` ist genau der **Platzhaltertext**, den Sie anzeigen lassen möchten, um den Endbenutzer zu führen.

## Schritt 4: Das Control an der aktuellen Cursor‑Position einfügen

Verwenden Sie den `DocumentBuilder`, um das SDT in das Dokument einzufügen, wo der Builder gerade positioniert ist.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Warum dieser Schritt wichtig ist:* Das Einfügen des Knotens verbindet das Control mit dem DOM des Dokuments. Wenn Sie mehrere Platzhalter hinzufügen müssen, können Sie den Cursor des Builders verschieben und diesen Schritt wiederholen.

## Schritt 5: Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Ersetzen Sie `YOUR_DIRECTORY` durch einen tatsächlichen Pfad auf Ihrem Rechner.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie `SDT.docx` in Microsoft Word öffnen, sehen Sie ein grau schattiertes Inline‑Textfeld, das **Enter name here** anzeigt. Ein Klick in das Feld entfernt den Platzhalter, sodass der Benutzer einen Kundennamen eingeben kann.

### Erwartete Ausgabe

| Dateipfad | Inhaltsvorschau |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | Inline‑Platzhalter **Enter name here** in einem Plain‑Text‑Content‑Control mit dem Titel *CustomerName*. |

## Sonderfälle und Variationen

| Situation | Empfohlene Anpassung |
|-----------|------------------------|
| **Mehrere Platzhalter** | Erstellen Sie zusätzliche `StructuredDocumentTag`‑Objekte mit unterschiedlichen `Title`‑ und `PlaceholderName`‑Werten und fügen Sie jedes dort ein, wo es benötigt wird. |
| **Rich‑Text‑Platzhalter** | Verwenden Sie `SdtType.RichText` anstelle von `PlainText`, um Formatierungen im Platzhalter zu ermöglichen. |
| **Block‑Level‑Control** | Ändern Sie `MarkupLevel.Inline` zu `MarkupLevel.Block`, damit das Control sich wie ein voller Absatz verhält. |
| **Platzhalter nicht sichtbar** | Stellen Sie sicher, dass die Ansichtseinstellungen des Dokuments in Word nicht so konfiguriert sind, dass Content‑Controls ausgeblendet werden (`Datei → Optionen → Erweitert → Content‑Controls anzeigen`). |
| **Speichern in einen Stream** | Rufen Sie `doc.Save(stream, SaveFormat.Docx)` auf, wenn Sie die Datei über HTTP senden statt auf die Festplatte zu schreiben. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle oben genannten Schritte in einer einzigen `Main`‑Methode.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Führen Sie das Programm aus, öffnen Sie die erzeugte Datei, und Sie sehen den Platzhaltertext, bereit für Benutzereingaben.

## Häufig gestellte Fragen beantwortet

**F: Funktioniert das mit .NET Core?**  
A: Ja. Aspose.Words für .NET ist kompatibel mit .NET Core, .NET 5 und .NET 6+. Der gleiche Code läuft unverändert.

**F: Kann ich zusätzlich zum Platzhalter einen Standardwert festlegen?**  
A: Verwenden Sie `sdt.SetText("Default value")` nach dem Erstellen des SDT. Der Platzhalter verschwindet, sobald ein Wert gesetzt ist.

**F: Was ist, wenn ich den später eingegebenen Wert abrufen muss?**  
A: Laden Sie das Dokument, finden Sie das SDT über dessen `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) und lesen Sie `sdt.GetText()`.

## Fazit

Sie wissen jetzt, wie Sie **Platzhaltertext** in einem Word‑Dokument mit C# **setzen**. Durch das Erstellen eines Plain‑Text‑`StructuredDocumentTag`, das Zuweisen eines Titels und eines Platzhalters, das Einfügen mit einem `DocumentBuilder` und das Speichern der Datei können Sie **Controls hinzufügen** und **Word‑C#‑Dateien** programmgesteuert **generieren**.  

Von hier aus können Sie Folgendes erkunden:

* Hinzufügen von Rich‑Text‑ oder Dropdown‑List‑Controls (`SdtType.RichText`, `SdtType.DropDownList`).  
* Befüllen mehrerer Platzhalter aus einer Datenbank.  
* Konvertieren des erzeugten `.docx` in PDF mit Aspose.Words.

Experimentieren Sie mit verschiedenen Control‑Typen und Platzhalter‑Stilen, um den Anforderungen Ihrer Anwendung gerecht zu werden. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Platzhaltertext in Aspose.Words festlegen – Vollständiger C#‑Leitfaden](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Word‑Dokument programmgesteuert erstellen – Content‑Control und Platzhalter hinzufügen](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Wie man ein Content‑Control hinzufügt und ein Word‑Dokument mit Aspose erstellt – Komplett](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}