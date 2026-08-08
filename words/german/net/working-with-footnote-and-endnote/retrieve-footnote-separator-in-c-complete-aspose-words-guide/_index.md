---
category: general
date: 2026-08-07
description: Fußnotentrennzeichen mit Aspose.Words für .NET abrufen. Erfahren Sie,
  wie Sie Fußnoten‑ und Endnotentrennzeichen extrahieren, Knotentypen prüfen und sie
  in C# ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: de
lastmod: 2026-08-07
og_description: Fußnotentrennzeichen mit Aspose.Words für .NET abrufen. Dieser Leitfaden
  zeigt, wie man Fußnoten‑ und Endnotentrennzeichen extrahiert, deren Knotentypen
  prüft und Änderungen speichert.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Fußnoten‑Trennzeichen in C# abrufen – Schritt‑für‑Schritt Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Fußnotentrennzeichen in C# abrufen – vollständiger Aspose.Words‑Leitfaden
url: /de/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fußnotentrennzeichen in C# abrufen – vollständiger Aspose.Words Leitfaden

Wenn Sie das **footnote separator abrufen** aus einem Word-Dokument benötigen, zeigt Ihnen dieses Tutorial genau, wie Sie dies mit Aspose.Words für .NET tun können. Egal, ob Sie einen Dokumenten‑Verarbeitungsservice erstellen oder die Fußnotenformatierung bereinigen, Sie sehen ein vollständiges, ausführbares Beispiel, das sowohl Fußnoten‑ als auch Endnoten‑Trennzeichen extrahiert.

In diesem Leitfaden lernen Sie, wie Sie eine `.docx`‑Datei laden, die Eigenschaften `FootnoteSeparator` und `EndnoteSeparator` aufrufen, die zurückgegebenen `Node`‑Objekte inspizieren und optional die Trennlinien ersetzen. Keine externe Dokumentation ist erforderlich – alles, was Sie benötigen, ist unten enthalten.

## Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch unter .NET Framework 4.7.2)
* Aspose.Words for .NET NuGet‑Paket (Version 24.9 oder neuer)
* Ein Word‑Dokument, das Fußnoten und/oder Endnoten enthält (z. B. `Footnotes.docx`)

Sie können das Aspose.Words‑Paket mit dem folgenden CLI‑Befehl hinzufügen:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt oder fügen Sie den Code zu einem bestehenden hinzu. Die erforderlichen `using`‑Direktiven sind unten aufgeführt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Diese Namespaces geben Ihnen Zugriff auf die Klasse `Document`, die `Node`‑Hierarchie und die Aufzählung `NodeType`, die für **footnote separator abrufen**‑Operationen benötigt werden.

## Schritt 2: Laden des Dokuments, das Fußnoten und Endnoten enthält

Der erste Schritt in jedem Aspose.Words‑Workflow besteht darin, die Quelldatei zu laden. Ersetzen Sie den Platzhalterpfad durch den tatsächlichen Speicherort Ihrer `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Das Laden der Datei bereitet den internen Knotbaum vor, was für **footnote separator abrufen** entscheidend ist, da die Trennzeichen‑Knoten in diesem Baum leben.

## Schritt 3: Fußnotentrennzeichen‑Knoten abrufen

Jetzt können Sie **footnote separator abrufen**, indem Sie die Eigenschaft `FootnoteSeparator` des `Document`‑Objekts aufrufen. Dieser Knoten stellt die Linie dar, die Fußnoten vom Haupttext trennt.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

Der `NodeType` wird für eine Standard‑Trennlinien‑Paragraph `Paragraph` sein. Das Wissen um den Knotentyp hilft Ihnen zu entscheiden, ob Sie das Trennzeichen ändern oder vollständig ersetzen müssen.

## Schritt 4: Endnotentrennzeichen‑Knoten abrufen

Ähnlich können Sie **endnote separator abrufen** mittels der Eigenschaft `EndnoteSeparator`. Dieser Knoten trennt Endnoten vom Hauptinhalt.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Beide Trennzeichen‑Knoten teilen in den meisten Dokumenten denselben `NodeType` (`Paragraph`), können jedoch unabhängig voneinander angepasst werden.

## Schritt 5: Inhalt des Trennzeichens prüfen oder ändern (optional)

Wenn Sie das visuelle Erscheinungsbild des Trennzeichens ändern müssen – z. B. eine Strichlinie durch eine dünne Regel ersetzen – können Sie den `Paragraph`‑Knoten direkt bearbeiten. Unten finden Sie ein Beispiel, das den Standard‑Trennzeichen‑Text durch einen benutzerdefinierten String ersetzt.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Nach dem Ändern der Knoten können Sie das Dokument speichern, um die Änderungen in Word zu sehen.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Erwartete Konsolenausgabe

Wenn Sie das Programm mit dem ursprünglichen `Footnotes.docx` ausführen, sollten Sie etwas Ähnliches sehen wie:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Wenn Sie `Footnotes_Updated.docx` in Microsoft Word öffnen, zeigen die Fußnoten‑ und Endnoten‑Trennzeichen den von Ihnen eingefügten benutzerdefinierten Text an.

## Häufige Fragen und Sonderfälle

**Was ist, wenn das Dokument keine Fußnoten hat?**  
Die Eigenschaft `FootnoteSeparator` gibt immer noch einen `Paragraph`‑Knoten zurück, da Word stets einen Trennzeichen‑Platzhalter einfügt. Der Knoten ist leer, sodass Sie sicher Inhalt hinzufügen oder ihn unverändert lassen können.

**Kann ich das Trennzeichen für einen bestimmten Abschnitt abrufen?**  
Fußnoten‑ und Endnoten‑Trennzeichen gelten für das gesamte Dokument und nicht abschnittsspezifisch. Wenn Sie eine Steuerung auf Abschnittsebene benötigen, müssen Sie stattdessen mit `Section.FootnoteOptions` und `Section.EndnoteOptions` arbeiten, anstatt die globalen Trennzeichen‑Knoten zu verwenden.

**Funktioniert das mit .NET Core?**  
Ja. Aspose.Words für .NET ist plattformübergreifend, und derselbe Code läuft unter Windows, Linux und macOS mit .NET 6+.

**Welchen Knotentyp sollte ich erwarten?**  
Sowohl `FootnoteSeparator` als auch `EndnoteSeparator` geben einen `Paragraph`‑Knoten zurück (`NodeType.Paragraph`). Wenn Sie einen anderen Typ finden, könnte das Dokument beschädigt sein; Sie sollten die Quelldatei neu laden oder validieren.

## Vollständiger Quellcode für schnelles Kopieren‑Einfügen

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Kopieren Sie den Code in eine `Program.cs`‑Datei, passen Sie die Dateipfade an und führen Sie `dotnet run` aus. Das Programm demonstriert den vollständigen **footnote separator abrufen**‑Workflow, vom Laden des Dokuments bis zum Speichern der Änderungen.

## Fazit

Sie wissen jetzt, wie Sie **footnote separator abrufen** und **endnote separator abrufen** mit Aspose.Words für .NET durchführen, deren `document node type` inspizieren und optional deren Inhalt ersetzen. Diese Technik ermöglicht es Ihnen, die Fußnotenformatierung zu automatisieren, benutzerdefinierte Trennlinien zu erzeugen oder die Dokumentstruktur in jeder C#‑Anwendung zu validieren.

Als Nächstes könnten Sie verwandte Themen wie **C# footnote extraction** für einzelne Fußnotentexte erkunden oder lernen, wie man **footnote reference marks** mit `FootnoteOptions` **modifiziert**. Beide Konzepte bauen direkt auf den hier behandelten Grundlagen des Knotbaums auf.

Viel Spaß beim Programmieren und fühlen Sie sich frei, mit verschiedenen Trennzeichen‑Stilen zu experimentieren, um sie an das Branding Ihres Projekts anzupassen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}