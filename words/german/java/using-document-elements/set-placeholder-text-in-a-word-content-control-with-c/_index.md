---
category: general
date: 2026-11-22
description: Platzhaltertext in einem Word‑Inhaltssteuerelement mit C# festlegen.
  Erfahren Sie, wie Sie ein benutzerdefiniertes Tag erstellen, ein Nur‑Text‑Steuerelement
  einfügen und dem Tag mithilfe von Aspose.Words einen Platzhalter hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: de
lastmod: 2026-11-22
og_description: Platzhaltertext in einem Word-Inhaltssteuerelement mit C# festlegen.
  Dieses Tutorial zeigt, wie man ein benutzerdefiniertes Tag erstellt, ein Nur-Text-Steuerelement
  einfügt und dem Tag einen Platzhalter hinzufügt, um die Dokumenteninteraktivität
  zu verbessern.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Platzhaltertext in einem Word-Inhaltssteuerelement festlegen – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Platzhaltertext in einem Word‑Inhaltssteuerelement mit C# festlegen
url: /de/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Platzhaltertext in einem Word‑Inhaltssteuerelement mit C# setzen

Wenn Sie **Platzhaltertext setzen** in einem Word‑Dokument programmgesteuert benötigen, zeigt Ihnen dieses Handbuch genau, wie das geht. Mit Aspose.Words für .NET können Sie ein benutzerdefiniertes Tag erstellen, ein Nur‑Text‑Steuerelement einfügen und dem Tag einen Platzhalter hinzufügen, sodass das Dokument für die Benutzereingabe bereit ist.

In diesem Tutorial lernen Sie, wie man **benutzerdefiniertes Tag erstellt**, **ein Inhaltssteuerelement einfügt** und **einem Tag einen Platzhalter hinzufügt**, während der Code knapp und produktionsreif bleibt. Keine externen Werkzeuge sind erforderlich – nur ein .NET‑Projekt und die Aspose.Words‑Bibliothek.

## Voraussetzungen

* .NET 6.0 SDK oder neuer installiert  
* Eine gültige Aspose.Words für .NET Lizenz (oder ein kostenloser Evaluierungsschlüssel)  
* Grundlegende Kenntnisse in C# und Visual Studio (oder einer IDE Ihrer Wahl)  

Die folgenden Abschnitte gehen davon aus, dass Sie ein Konsolenprojekt namens `WordPlaceholderDemo` erstellt haben.

## Schritt 1: Aspose.Words installieren

Add the NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Profi‑Tipp:** Verwenden Sie das `--version`‑Flag, um das Paket auf die neueste stabile Version zu fixieren (z. B. `Aspose.Words.NET 24.9`).

## Schritt 2: Das Quelldokument laden und einen `DocumentBuilder` erstellen

Der erste Schritt besteht darin, eine vorhandene `.docx`‑Datei zu laden (oder ein neues leeres Dokument zu erstellen) und einen `DocumentBuilder` zu instanziieren. Der Builder stellt Ihnen eine fluente API zum Einfügen von Steuerelementen und Text zur Verfügung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Dieser Code **bereitet den Weg** für das Einfügen eines Inhaltssteuerelements vor. Der `DocumentBuilder` arbeitet direkt am `doc`‑Objekt, sodass alle Änderungen automatisch übernommen werden.

## Schritt 3: Ein benutzerdefiniertes Tag erstellen (StructuredDocumentTag)

Ein *benutzerdefiniertes Tag* in Word wird **StructuredDocumentTag (SDT)** genannt. Man kann es sich als ein Inhaltssteuerelement vorstellen, das einen eindeutigen Bezeichner trägt. Das Erstellen ist der Kern des Schrittes **benutzerdefiniertes Tag erstellen**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Die `InsertStructuredDocumentTag`‑Methode nimmt zwei Argumente entgegen:

1. Der Typ des Steuerelements (`PlainText` in diesem Fall).  
2. Ein String, der das Tag eindeutig identifiziert (`"MyTag"`).  

Durch die Verwendung eines **benutzerdefinierten Tags** können Sie das Steuerelement später programmgesteuert finden oder manipulieren.

## Schritt 4: Einen Titel für Barrierefreiheit festlegen

Ein Titel verbessert die Barrierefreiheit und erleichtert das Auffinden des Steuerelements in der Word‑Benutzeroberfläche.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Die `Title`‑Eigenschaft ist optional, aber das Hinzufügen ist eine bewährte Praxis, wenn Sie **einem Tag einen Platzhalter hinzufügen** für eine bessere Benutzererfahrung.

## Schritt 5: Platzhaltertext zum Tag hinzufügen

Jetzt kommt das Hauptziel: **Platzhaltertext setzen**. Dieser Text erscheint, wenn das Steuerelement leer ist, und weist den Benutzer an, was er eingeben soll.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Die `PlaceholderText`‑Eigenschaft ist genau das, was Sie benötigen, um **einem Tag einen Platzhalter hinzuzufügen**. Sie verhält sich wie der graue Hinweis, den Sie in modernen Formularfeldern sehen.

## Schritt 6: Das modifizierte Dokument speichern

Nachdem das Steuerelement konfiguriert wurde, schreiben Sie das Dokument zurück auf die Festplatte.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Wenn Sie `output.docx` in Microsoft Word öffnen, sehen Sie ein Nur‑Text‑Inhaltssteuerelement mit der Bezeichnung „CustomerName“ und dem Platzhalter „Enter name…“. Ein Klick ins Steuerelement entfernt den Platzhalter, sodass der Benutzer tippen kann.

### Erwartete Ausgabe

* Eine Word‑Datei (`output.docx`) mit einem einzigen Nur‑Text‑Inhaltssteuerelement.  
* Das Steuerelement zeigt den Platzhalter „Enter name…“ an, bis der Benutzer etwas eingibt.  
* Der Tag‑Bezeichner des Steuerelements ist `MyTag`, den Sie später mit `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` abfragen können.

## Schritt 7: Inhaltssteuerelement an anderer Stelle einfügen (fortgeschritten)

Wenn Sie **ein Inhaltssteuerelement einfügen** an einer bestimmten Stelle benötigen – zum Beispiel nach einem bestimmten Absatz – verwenden Sie die `MoveTo`‑Methode, bevor Sie das Tag einfügen:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Dieses Snippet demonstriert das **Einfügen von Nur‑Text‑Steuerelementen** mehrmals im selben Dokument.

## Häufige Fallstricke und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Platzhalter nicht sichtbar | Das Steuerelement enthält bereits Text (auch ein Leerzeichen) | Stellen Sie sicher, dass `sdt.Text` leer ist, bevor Sie `PlaceholderText` setzen. |
| Tag‑Bezeichner‑Kollision | Wiederverwendung desselben Tag‑Namens (`MyTag`) im selben Dokument | Verwenden Sie eindeutige Bezeichner für jedes `StructuredDocumentTag`. |
| Lizenz‑Ausnahme | Ausführen ohne gültige Aspose.Words‑Lizenz | Laden Sie eine Lizenzdatei (`license.SetLicense("Aspose.Words.lic")`) zu Beginn von `Main`. |
| Dokument nicht gespeichert | Vergessen, `doc.Save` aufzurufen oder einen schreibgeschützten Pfad zu verwenden | Stellen Sie sicher, dass der Ausgabepfad beschreibbar ist, und rufen Sie `doc.Save` auf. |

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in `Program.cs` kopieren und einfügen können. Es enthält alle Schritte – **benutzerdefiniertes Tag erstellen**, **Inhaltssteuerelement einfügen**, **einem Tag einen Platzhalter hinzufügen** und **Nur‑Text‑Steuerelement einfügen** – in einem zusammenhängenden Ablauf.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Führen Sie das Programm mit `dotnet run` aus. Nach der Ausführung öffnen Sie `output.docx`, um zu überprüfen, dass beide Steuerelemente ihre jeweiligen Platzhalter anzeigen.

## Nächste Schritte

* **Aussehen anpassen** – Verwenden Sie `sdt.Font`, um Schriftgröße, Farbe oder Stil im Steuerelement zu ändern.  
* **An XML‑Daten binden** – Erkunden Sie `sdt.XmlMapping`, falls Sie das Steuerelement an Daten binden müssen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}