---
category: general
date: 2026-09-08
description: Endnoten‑Trennzeichen abrufen und Fußnoten‑Trennzeichen anzeigen, wenn
  Sie ein Word‑Dokument mit Aspose.Words für .NET laden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: de
lastmod: 2026-09-08
og_description: Rufen Sie den Endnotenseparator ab und zeigen Sie den Fußnotenseparator
  an, wenn Sie ein Word‑Dokument mit Aspose.Words für .NET laden.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Endnoten‑Trennzeichen beim Laden eines Word‑Dokuments in C# abrufen
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Endnotentrennzeichen beim Laden eines Word‑Dokuments in C# abrufen
url: /de/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Endnote‑Trennzeichen beim Laden eines Word‑Dokuments in C# abrufen

Wenn Sie das **Endnote‑Trennzeichen** aus einer Word‑Datei abrufen müssen, zeigt Ihnen diese Anleitung genau, wie Sie das tun. Sie lernen außerdem, wie Sie ein **Word‑Dokument** mit Aspose.Words **laden** und den Text des **Fußnoten‑Trennzeichens** in der Konsole anzeigen, alles in einem einzigen, ausführbaren Beispiel.

Die Arbeit mit Fußnoten und Endnoten ist eine häufige Anforderung für juristische, akademische oder Verlags‑Anwendungen. Dieses Tutorial deckt alles ab, was Sie benötigen – vom Öffnen der Datei bis zum Umgang mit Fällen, in denen ein Trennzeichen fehlt – sodass Sie die Lösung ohne Rätselraten in jedes .NET‑Projekt integrieren können.

## Was dieses Tutorial abdeckt

* Wie man ein **Word‑Dokument** mit der Aspose.Words‑API **lädt**.  
* Wie man das **Endnote‑Trennzeichen** **abrufen** kann und warum das Trennzeichen wichtig ist.  
* Wie man das **Fußnoten‑Trennzeichen** in der Konsole **anzeigen** kann, zum Debuggen oder Protokollieren.  
* Edge‑Case‑Behandlung, wenn ein Dokument keine Fußnoten oder Endnoten enthält.  
* Ein vollständiges, copy‑paste‑fertiges Code‑Beispiel, das auf .NET 6 oder höher läuft.

### Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6 SDK oder neuer | Stellt die Laufzeit für das C#‑Beispiel bereit. |
| Aspose.Words for .NET (NuGet‑Paket `Aspose.Words`) | Die Bibliothek, die `Document.Footnotes` und `Document.Endnotes` bereitstellt. |
| Eine Word‑Datei (`Footnotes.docx`), die mindestens eine Fuß‑ oder Endnote enthält | Demonstriert die Trennzeichen. |
| Beliebige IDE (Visual Studio, Rider, VS Code) | Zum Kompilieren und Ausführen des Programms. |

> **Pro‑Tipp:** Wenn Sie kein Dokument mit Fußnoten haben, erstellen Sie schnell eines in Microsoft Word: Einfügen → Fußnote → Text eingeben und dann als `Footnotes.docx` speichern.

## Word‑Dokument mit Aspose.Words laden

Der erste Schritt besteht darin, das **Word‑Dokument** in den Speicher zu **laden**. Aspose.Words liest das Dateiformat und baut ein Objektmodell auf, das Sie abfragen können.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Warum das wichtig ist*: Das Laden des Dokuments ist die Voraussetzung für jede weitere Manipulation. Ist der Dateipfad falsch, wirft `Document` eine `FileNotFoundException`, daher sollten Sie den Pfad vor dem Ausführen prüfen.

## Fußnoten‑Trennzeichen‑Absatz abrufen

Ein Fußnoten‑Trennzeichen ist der Absatz, der den Haupttext visuell von der Fußnotenliste trennt. Das Abrufen ermöglicht es Ihnen, dessen Formatierung zu inspizieren oder zu ändern.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Warum das wichtig ist*: **Fußnoten‑Trennzeichen anzeigen** hilft Ihnen zu überprüfen, dass der richtige Absatz angesprochen wird, besonders wenn Sie ein benutzerdefiniertes Styling anwenden müssen (z. B. eine Linie oder eine bestimmte Schriftart).

## Endnote‑Trennzeichen‑Absatz abrufen

Jetzt **abrufen wir das Endnote‑Trennzeichen**. Der Vorgang spiegelt die Fußnoten‑Verarbeitung wider, nutzt jedoch die `Endnotes`‑Sammlung.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Warum das wichtig ist*: Der Schritt **Endnote‑Trennzeichen abrufen** ist entscheidend, wenn Sie den visuellen Abstand zwischen Hauptinhalt und Endnotenliste anpassen müssen – üblich im akademischen Publizieren, wo Endnoten am Kapitelende erscheinen.

### Umgang mit fehlenden Trennzeichen

Sowohl `Footnotes.Separator` als auch `Endnotes.Separator` geben `null` zurück, wenn das Dokument kein Trennzeichen definiert. Prüfen Sie immer auf `null`, bevor Sie `GetText()` aufrufen, um eine `NullReferenceException` zu vermeiden. Wenn Sie ein Standard‑Trennzeichen benötigen, können Sie eines erstellen:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Dieser Code fügt ein minimales Trennzeichen ein, sodass nachfolgende Verarbeitung sich auf dessen Existenz verlassen kann.

## Erwartete Konsolenausgabe

Wenn das Beispiel gegen ein Dokument läuft, das eine Fußnote und eine Endnote enthält, sollten Sie etwas Ähnliches sehen:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Fehlt das Dokument Fußnoten oder Endnoten, gibt das Programm die entsprechenden „nicht gefunden“-Meldungen aus und demonstriert damit eine elegante Fehlerbehandlung.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in ein neues C#‑Konsolenprojekt kopieren können. Es wird kein zusätzlicher Code benötigt.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Speichern Sie die Datei als `Program.cs`, fügen Sie das Aspose.Words‑NuGet‑Paket hinzu (`dotnet add package Aspose.Words`) und führen Sie `dotnet run` aus. Das Programm gibt die Trennzeichen‑Texte aus oder informiert Sie, wenn sie fehlen.

## Häufige Variationen und Was‑wenn‑Szenarien

| Szenario | Wie der Code anzupassen ist |
|----------|-----------------------------|
| **Mehrere benutzerdefinierte Trennzeichen** | Verwenden Sie `doc.Footnotes.Separator`, um das Standard‑Trennzeichen zu ersetzen, und fügen Sie dann zusätzliche Trennzeichen‑Absätze manuell mit `doc.Footnotes.Add(separatorParagraph)` hinzu. |
| **Trennzeichen‑Stil ändern** | Nachdem Sie das Trennzeichen abgerufen haben, ändern Sie dessen `ParagraphFormat` (z. B. `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Arbeiten mit .doc‑Dateien** | Die gleiche API funktioniert; stellen Sie nur sicher, dass der Dateipfad mit `.doc` endet. |
| **Verarbeitung vieler Dokumente** | Verpacken Sie das Laden und das Abrufen der Trennzeichen in einer `foreach`‑Schleife; verwenden Sie eine einzelne `Document`‑Instanz nur, wenn Sie sie mit `doc = new Document(path)` zurücksetzen. |

## Checkliste bewährter Methoden

- ✅ **Immer auf `null` prüfen**, bevor Sie auf den Trennzeichen‑Text zugreifen.  
- ✅ **Trim** das Ergebnis von `GetText()`, um versteckte Zeilenumbruch‑Zeichen zu entfernen.  
- ✅ **Dispose** großer `Document`‑Objekte, wenn Sie viele Dateien stapelweise verarbeiten (verwenden Sie `using` oder rufen Sie `doc.Dispose()` auf).  
- ✅ **Log** Trennzeichen‑Text nur in der Entwicklung; vermeiden Sie dessen Anzeige in Produktions‑Logs, sofern nicht erforderlich.  

## Fazit

Sie wissen jetzt, wie Sie das **Endnote‑Trennzeichen** **abrufen**, während Sie ein **Word‑Dokument** **laden** und das **Fußnoten‑Trennzeichen** in einer .NET‑Konsolenanwendung **anzeigen**. Das vollständige Beispiel demonstriert das Laden, Abfragen und den sicheren Umgang mit fehlenden Trennzeichen und bietet Ihnen eine solide Grundlage für jede Fuß‑ oder Endnoten‑Manipulation.

Als Nächstes könnten Sie folgendes erkunden:

* **Anpassen von Fuß‑/Endnoten‑Formatierungen** – Schriftarten, Rahmen oder Nummerierungsstile ändern.  
* **Extrahieren von Fuß‑/Endnoten‑Inhalten** – `doc.Footnotes` oder `doc.Endnotes`‑Sammlungen iterieren.  
* **Speichern des modifizierten Dokuments** – `doc.Save("output.docx")` verwenden, um Änderungen zu persistieren.

Experimentieren Sie gern mit verschiedenen Word‑Dateien, Trennzeichen‑Stilen und den Funktionen von Aspose.Words. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Word‑Dokumente mit Aspose.Words LoadOptions lädt](/words/english/net/programming-with-loadoptions/)
- [Paragraph‑Stil‑Trennzeichen in Word‑Dokumenten erhalten](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Ein Word‑Dokument in Aspose.Words für .NET erstellen und formatieren](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}