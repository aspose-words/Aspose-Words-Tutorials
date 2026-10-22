---
category: general
date: 2026-09-18
description: Erstelle ein leeres Word‑Dokument mit C# und setze Platzhaltertext, dann
  speichere das Dokument als docx. Lerne, ein Textsteuerelement einzufügen und einen
  Platzhalternamen hinzuzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: de
lastmod: 2026-09-18
og_description: Erstelle ein leeres Word‑Dokument mit C#. Setze Platzhaltertext, füge
  ein Nur‑Text‑Steuerelement ein, füge den Platzhalternamen hinzu und speichere das
  Dokument als docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Erstelle ein leeres Word‑Dokument mit Platzhaltertext – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Leeres Word‑Dokument erstellen und ein Nur‑Text‑Steuerelement einfügen
url: /de/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leeres Word‑Dokument erstellen und ein Nur‑Text‑Steuerelement einfügen

Wenn Sie programmgesteuert **ein leeres Word‑Dokument erstellen** möchten, zeigt Ihnen diese Anleitung, wie Sie das mit C# erledigen. Sie lernen, **ein Nur‑Text‑Steuerelement einzufügen**, **Platzhaltertext zu setzen**, **einen Platzhalternamen hinzuzufügen** und schließlich **das Dokument als docx zu speichern**. Die Schritte sind vollständig eigenständig, sodass Sie den Code in jedes .NET‑Projekt kopieren und sofort ausführen können.

Die Arbeit mit Word‑Dateien erfordert oft einen sauberen Ausgangspunkt — ein leeres Dokument, das bereits die Steuerelemente enthält, die Ihre Benutzer ausfüllen sollen. Am Ende dieses Tutorials besitzen Sie eine `.docx`‑Datei, die ein Nur‑Text‑Inhaltssteuerelement mit einem hilfreichen Platzhalter enthält, gefolgt von normalem Inhalt.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
- Ein Verweis auf die **Aspose.Words for .NET**‑Bibliothek (verfügbar über NuGet `Install-Package Aspose.Words`)
- Grundkenntnisse in C#‑Konsolenanwendungen
- Schreibrechte für den Ausgabepfad, den Sie in `doc.save(...)` angeben

## Was Sie bauen werden

Das fertige Dokument (`SDT.docx`) enthält:

1. Eine leere Word‑Datei (das **leere Word‑Dokument**, das Sie erstellt haben)
2. Ein Nur‑Text‑Inhaltssteuerelement (der **Insert plain text control**‑Schritt)
3. Platzhaltertext, der im Steuerelement angezeigt wird, bis der Benutzer etwas eingibt (der **Set placeholder text**‑Schritt)
4. Einen Platzhalternamen, der später für den programmgesteuerten Zugriff verwendet werden kann (der **Add placeholder name**‑Schritt)
5. Eine Zeile regulären Textes nach dem Steuerelement, die zeigt, dass normaler Inhalt folgen kann

## Schritt 1: Ein leeres Word‑Dokument erstellen

Der erste Vorgang besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert ein komplett neues, **leeres Word‑Dokument** im Speicher.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Warum das wichtig ist:* Ein leeres `Document` gibt Ihnen die volle Kontrolle über jedes Element, das Sie hinzufügen, und verhindert, dass versteckte Formatvorlagen oder Abschnitte das spätere Inhaltssteuerelement beeinträchtigen.

## Schritt 2: Einen DocumentBuilder initialisieren

`DocumentBuilder` ist die Hilfsklasse, mit der Sie in das `Document` schreiben. Sie verfolgt die aktuelle Cursor‑Position und stellt Methoden zum Einfügen aller möglichen Word‑Objekte bereit.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist:* Die Verwendung eines `DocumentBuilder` vereinfacht das Hinzufügen eines **plain‑text control**, weil der Builder den genauen Einfügepunkt kennt.

## Schritt 3: Nur‑Text‑Steuerelement einfügen

Jetzt fügen wir ein **plain‑text content control** (auch bekannt als Structured Document Tag, SDT) hinzu. Der Steuertyp `StructuredDocumentTagType.PLAIN_TEXT` weist Word an, den Inhalt als Nur‑Text zu behandeln, nicht als Rich‑Formatting.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Warum das wichtig ist:* Die Methode `InsertStructuredDocumentTag` erstellt das Steuerelement und gibt eine Referenz (`sdt`) zurück, die Sie weiter konfigurieren können, z. B. Platzhaltertext oder einen benutzerdefinierten Namen hinzufügen.

## Schritt 4: Platzhaltertext setzen und Platzhalternamen hinzufügen

Platzhaltertext gibt Benutzern einen visuellen Hinweis darauf, was einzugeben ist. Der **add placeholder name**‑Schritt weist einen programmgesteuerten Bezeichner zu, den Sie später mit `doc.GetChildNodes` oder ähnlichen APIs abfragen können.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Warum das wichtig ist:* `SetPlaceholderName` steuert den grauen Hinweistext, der im Inhaltssteuerelement angezeigt wird. Das Setzen von `Tag` (die **add placeholder name**‑Aktion) ermöglicht es Ihnen, das Steuerelement im Dokumenten‑Baum zu finden, ohne die gesamte Datei zu durchsuchen.

## Schritt 5: Regulären Inhalt nach dem Steuerelement hinzufügen

Um zu zeigen, dass das Dokument nach dem Steuerelement normal weitergeht, schreiben wir eine einfache Textzeile.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Schritt 6: Dokument als docx speichern

Abschließend persistieren wir das im Speicher befindliche Dokument auf die Festplatte. Dies ist die **save document as docx**‑Operation, die die Datei erzeugt, die Sie in Microsoft Word öffnen können.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Warum das wichtig ist:* Das `.docx`‑Format sorgt für maximale Kompatibilität mit modernen Word‑Versionen, Google Docs und anderen Office‑kompatiblen Tools.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in ein Konsolen‑App‑Projekt kopieren können. Ersetzen Sie `YOUR_DIRECTORY` durch einen tatsächlichen Ordnerpfad auf Ihrem Rechner.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Erwartetes Ergebnis

- Beim Öffnen von `SDT.docx` in Word wird ein leeres graues Feld mit dem Text **Enter text…** angezeigt.
- Das Feld ist ein Nur‑Text‑Inhaltssteuerelement; Sie können direkt darin tippen.
- Unterhalb des Feldes erscheint die Zeile **After the tag.** als normaler Absatztext.

Falls der Platzhalter nicht erscheint, prüfen Sie, ob Sie eine aktuelle Version von Aspose.Words (v23.1 oder später) verwenden und das Dokument in einer Word‑Version geöffnet wird, die Inhaltssteuerelemente unterstützt (Word 2007+).

## Häufige Varianten und Sonderfälle

| Szenario | Wie der Code anzupassen ist |
|----------|-----------------------------|
| **Mehrere Platzhalter** | Rufen Sie `InsertStructuredDocumentTag` erneut mit einer anderen Tag‑ID und einem anderen Platzhalternamen auf. |
| **Rich‑Text‑Steuerelement** | Verwenden Sie `StructuredDocumentTagType.RichText` anstelle von `PlainText`. |
| **Standardtext setzen** | Nach dem Einfügen: `sdt.Text = "Default value";` — dieser Text ersetzt den Platzhalter, wenn das Dokument geladen wird. |
| **In einen Stream speichern** | Ersetzen Sie `doc.Save(outputPath);` durch `doc.Save(stream, SaveFormat.Docx);`, um die Datei per HTTP zu senden. |
| **Platzhalterfarbe ändern** | Verwenden Sie `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (erfordert `using System.Drawing`). |

## Pro‑Tipps

- **Tag‑ID wiederverwenden**: Wenn Sie das Tag (`MyTag`) über Dokumente hinweg konsistent halten, können Sie später Daten automatisiert einfügen mit `doc.Range.Replace` oder der `StructuredDocumentTagCollection`.
- **Keine hartkodierten Pfade**: Nutzen Sie `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` für einen portablen Ausgabepfad.
- **Performance**: Wenn Sie Tausende von Dokumenten erzeugen müssen, erstellen Sie eine einzelne `Document`‑Vorlage mit bereits vorhandenem SDT und klonen Sie diese mit `doc.Clone()` für jede Iteration.

## Fazit

Sie wissen jetzt, wie Sie **ein leeres Word‑Dokument erstellen**, **ein Nur‑Text‑Steuerelement einfügen**, **Platzhaltertext setzen**, **einen Platzhalternamen hinzufügen** und **das Dokument als docx speichern** – und das mit Aspose.Words for .NET. Dieses Muster bildet die Grundlage für formularbasierte Word‑Vorlagen, automatisierte Berichte oder jede Lösung, die benutzereditierbare Platzhalter erfordert.

Experimentieren Sie gern mit anderen Steuerelementtypen, kombinieren Sie mehrere Platzhalter oder integrieren Sie diesen Code in eine Web‑API, die die erzeugte `.docx`‑Datei direkt an Aufrufer zurückgibt. Im nächsten Schritt können Sie **ein Inhaltssteuerelement programmgesteuert mit Daten füllen** oder **die erzeugte Word‑Datei mit Aspose.Words in PDF konvertieren**. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}