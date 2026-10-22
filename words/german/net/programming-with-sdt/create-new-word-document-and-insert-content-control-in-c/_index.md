---
category: general
date: 2026-10-13
description: Erstelle ein neues Word‑Dokument in C# und füge ein Inhaltssteuerelement
  mit Platzhaltertext ein. Erfahre, wie du Platzhaltertext festlegst und das Word‑Dokument
  effizient speicherst.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: de
lastmod: 2026-10-13
og_description: Erstellen Sie ein neues Word‑Dokument in C# mit Aspose.Words, fügen
  Sie ein Inhaltssteuerelement ein, setzen Sie Platzhaltertext und speichern Sie das
  Word‑Dokument – alles in einer einzigen Anleitung.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Neues Word-Dokument erstellen und Inhaltssteuerelement in C# einfügen
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Ein neues Word-Dokument erstellen und ein Inhaltssteuerelement in C# einfügen
url: /de/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines neuen Word-Dokuments und Einfügen eines Inhaltssteuerelements in C#

Wenn Sie programmgesteuert ein **neues Word-Dokument erstellen** müssen, zeigt Ihnen dieser Leitfaden, wie Sie dies mit Aspose.Words für .NET tun. Sie lernen, **ein Inhaltssteuerelement einzufügen**, **Platzhaltertext** zuzuweisen und schließlich **Word-Dokument in C# speichern** Code, den Sie in Ihr Projekt kopieren können.

Das Tutorial führt Sie durch jeden Schritt, erklärt, warum jeder API-Aufruf wichtig ist, und behandelt gängige Varianten wie das Hinzufügen eines Rich‑Text‑SDT oder das Verarbeiten vorhandener Dokumente. Am Ende haben Sie ein vollständiges, ausführbares Beispiel, das Sie an Rechnungen, Verträge oder jede andere vorlagenbasierte Word-Ausgabe anpassen können.

## Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
* Aspose.Words für .NET NuGet-Paket (`Install-Package Aspose.Words`)
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code

Es sind keine zusätzlichen Bibliotheken erforderlich.

## Neues Word-Dokument mit Aspose.Words erstellen

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine leere Word‑Datei im Speicher dar.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` bietet Ihnen eine fluente API zum Einfügen von Elementen an der aktuellen Cursor‑Position. Da das Dokument leer ist, startet der Cursor am Anfang des ersten (und einzigen) Abschnitts.

## Inhaltssteuerelement einfügen (StructuredDocumentTag)

Ein **Inhaltssteuerelement** in Word wird Structured Document Tag (SDT) genannt. Der folgende Code erstellt ein Plain‑Text‑SDT, setzt dessen Titel und definiert Platzhaltertext, der erscheint, wenn der Benutzer die Datei öffnet.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Warum das wichtig ist:**  
* `SdtType.PlainText` beschränkt den Inhalt auf eine einzelne Zeile reinen Textes, was ideal für einfache Felder wie einen Namen oder eine E‑Mail ist.  
* Das Setzen von `PlaceholderName` liefert einen visuellen Hinweis (`Enter name here`), der den Endbenutzer leitet.

Wenn Sie ein umfangreicheres Feld benötigen (z. B. mehrzeiligen Text oder einen Datumsauswahl‑Steuerung), ersetzen Sie `SdtType.PlainText` durch `SdtType.RichText` oder `SdtType.Date`.

## Optionalen umgebenden Text hinzufügen

Die meisten Vorlagen enthalten ein Etikett vor dem Inhaltssteuerelement. Sie können es mit derselben `DocumentBuilder`‑Instanz hinzufügen:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Die resultierende Word‑Datei zeigt:

```
Customer Name: [Enter name here]
```

## Word-Dokument im C#‑Stil speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Aspose.Words ermittelt das Format automatisch anhand der Dateierweiterung.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie `output.docx` in Microsoft Word öffnen, sehen Sie den Platzhaltertext innerhalb eines grau schattierten Inhaltssteuerelements. Benutzer können das Steuerelement anklicken und den Platzhalter durch ihren eigenen Wert ersetzen.

## Vollständiges, ausführbares Beispiel

Unten finden Sie ein eigenständiges Konsolenprogramm, das alles zusammenführt. Kopieren Sie den Code in ein neues Konsolenprojekt und führen Sie es aus.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe** (Konsole):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Das Öffnen von `output.docx` zeigt eine einzelne Zeile mit dem Etikett *Customer Name:* gefolgt von einem Inhaltssteuerelement, das *Enter name here* anzeigt.

## Häufige Variationen und Randfälle

| Scenario | Code change | Reason |
|----------|-------------|--------|
| **Rich‑Text‑Feld** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Erlaubt mehrzeilige Eingabe und grundlegende Formatierung. |
| **Nur‑Lese‑Steuerelement** | `sdt.LockContentControl = true;` | Verhindert, dass Benutzer den Inhalt des Steuerelements bearbeiten. |
| **Vorbefüllen mit Daten** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Fügt einen Standardwert ein, der den Platzhalter überschreibt. |
| **Zu einem bestehenden Dokument hinzufügen** | Load with `new Document("template.docx")` instead of an empty `Document` | Ermöglicht Templating‑Szenarien, bei denen das Steuerelement in einem vordefinierten Layout platziert wird. |
| **Mehrere Steuerelemente** | Repeat the creation block with different titles and placeholders | Nützlich für Formulare, die mehrere Informationen sammeln. |

### Profi‑Tipp

Beim Erzeugen großer Dokumente sollten Sie eine einzelne `DocumentBuilder`‑Instanz wiederverwenden, anstatt für jedes Steuerelement eine neue zu erstellen. Dies reduziert den Speicherverbrauch und verbessert die Leistung.

## Das Ergebnis testen

1. Führen Sie die Konsolen‑App aus.  
2. Öffnen Sie `output.docx` in Microsoft Word.  
3. Vergewissern Sie sich, dass der Platzhaltertext innerhalb einer grau schattierten Box erscheint.  
4. Klicken Sie die Box an, geben Sie einen Namen ein und speichern Sie die Datei. Der eingegebene Text ersetzt den Platzhalter.

Falls der Platzhalter nicht erscheint, prüfen Sie, dass Sie Aspose.Words Version 23.9 oder höher verwenden, da ältere Versionen einen Fehler mit `PlaceholderName` bei Plain‑Text‑SDTs hatten.

## Fazit

Sie wissen jetzt, wie man **ein neues Word‑Dokument erstellt**, **ein Inhaltssteuerelement einfügt**, **Platzhaltertext setzt** und **ein Word‑Dokument in C# speichert** mit Aspose.Words. Das vollständige Beispiel demonstriert das Standard‑Muster, und die Variationstabelle zeigt, wie die Lösung für umfangreichere Szenarien angepasst werden kann.

Als Nächstes könnten Sie erkunden:

* **Inhaltssteuerelement für Daten einfügen** – verwenden Sie die `SdtType.Date`‑Aufzählung.  
* **Eine Vorlage mit Daten füllen** – kombinieren Sie `StructuredDocumentTag` mit Seriendruckfeldern.  
* **Exportieren nach PDF** – rufen Sie `doc.Save("output.pdf")` nach dem Hinzufügen von Steuerelementen auf.

Fühlen Sie sich frei, mit verschiedenen SDT‑Typen, Sperreinstellungen und Stilvorlagen zu experimentieren, um die Anforderungen Ihres Projekts zu erfüllen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Neues Word-Dokument erstellen](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Text‑Eingabe‑Formularfeld in Word-Dokument einfügen](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}