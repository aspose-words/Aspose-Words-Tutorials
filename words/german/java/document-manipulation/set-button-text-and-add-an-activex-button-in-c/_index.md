---
category: general
date: 2026-10-10
description: Setze den Button-Text und füge einen ActiveX-Button in C# mit Aspose.Words
  hinzu. Erfahre, wie man einen Button einfügt, ein Button-Steuerelement erstellt
  und die Beschriftung in einem Word-Dokument anpasst.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: de
lastmod: 2026-10-10
og_description: Setze den Button-Text und füge einen ActiveX-Button in C# mit Aspose.Words
  hinzu. Befolge diese Schritt‑für‑Schritt‑Anleitung, um einen Button einzufügen,
  ein Button‑Steuerelement zu erstellen und dessen Beschriftung anzupassen.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Button-Text festlegen und einen ActiveX-Button in C# hinzufügen – vollständige
  Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Button-Text festlegen und einen ActiveX-Button in C# hinzufügen
url: /de/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Button‑Text festlegen und einen ActiveX‑Button in C# hinzufügen

Wenn Sie **Button‑Text festlegen** bei einem ActiveX‑Button in einem Word‑Dokument benötigen, zeigt Ihnen diese Anleitung genau, wie das geht. Am Ende des Tutorials können Sie **Button einfügen**, ein **Button‑Steuerelement erstellen** und dessen Beschriftung mit nur wenigen Zeilen C#‑Code anpassen.

Die Arbeit mit ActiveX‑Steuerelementen ist üblich, wenn Sie interaktive Formulare in Word benötigen – sei es für eine Vertragsvorlage, eine Umfrage oder ein internes Tool. Das Beispiel verwendet Aspose.Words für .NET, eine Bibliothek, mit der Sie Word‑Dateien manipulieren können, ohne Microsoft Office installiert zu haben.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Visual Studio 2022 (oder jede IDE, die C# unterstützt)  
* Eine Aspose.Words für .NET‑Lizenz (die kostenlose Evaluation reicht für Lernzwecke)  

Sie benötigen außerdem einen Verweis auf das NuGet‑Paket `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## So fügen Sie einen Button in ein Word‑Dokument ein

Der erste Schritt besteht darin, ein neues `Document` und einen `DocumentBuilder` zu erstellen. Der Builder ist der Einstiegspunkt zum Hinzufügen von Inhalten, einschließlich ActiveX‑Steuerelementen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:** `Document` repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` hoch‑level Methoden wie `InsertParagraph` und `InsertFormField` bereitstellt. Ein sauberes Dokument zu beginnen stellt sicher, dass der Button genau dort erscheint, wo Sie ihn haben möchten.

## Button‑Steuerelement mit Forms2OleControl erstellen

Jetzt erstellen wir das eigentliche Button‑Steuerelement. `Forms2OleControl` ist die Klasse, die Aspose.Words für alle ActiveX‑Objekte verwendet, und der Typ `COMMANDBUTTON` wird in Word als anklickbarer Button dargestellt.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Erläuterung:**  
* `InsertForms2OleControl` platziert das Steuerelement an den genauen Koordinaten, die Sie angeben.  
* Die Größe wird in Punkten definiert (1 Punkt = 1/72 Zoll). Passen Sie diese Werte an Ihr Layout an.

## ActiveX‑Steuerelement hinzufügen und ihm einen eindeutigen Namen geben

Jedes ActiveX‑Objekt sollte einen eindeutigen Namen besitzen, damit Sie später darauf verweisen können (z. B. beim Behandeln von Ereignissen in VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tipp:** Vermeiden Sie Leerzeichen oder Sonderzeichen im Namen; Word behandelt den Namen als Bezeichner im internen Formularmodell.

## Button‑Text (Caption) auf dem ActiveX‑Button festlegen

Hier kommt das Schlüsselwort **set button text** ins Spiel. Die Eigenschaft `Caption` definiert die Beschriftung, die Benutzer auf dem Button sehen.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Sie können die Caption jederzeit vor dem Speichern des Dokuments ändern. Wenn Sie später die Benutzeroberfläche lokalisieren möchten, rufen Sie einfach erneut `SetCaption` mit einer anderen Zeichenkette auf.

## Dokument speichern und Ergebnis überprüfen

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Öffnen Sie die Datei in Microsoft Word, um den Button mit der benutzerdefinierten Caption zu sehen.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Erwartete Ausgabe:** Wenn Sie *ActiveXButton.docx* in Word öffnen, sehen Sie einen Button an den angegebenen Koordinaten mit der Beschriftung **Click Me**. Ein Klick auf den Button löst das Standard‑Word‑Command‑Button‑Verhalten aus (das Sie später mit VBA anpassen können).

![Set button text example](https://example.com/activex-button.png){alt="Beispiel für Set button text"}

## ActiveX‑Button hinzufügen und Ereignisse behandeln (optional)

Falls der Button eine benutzerdefinierte Aktion ausführen soll, können Sie ein VBA‑Makro hinzufügen, das auf das `Click`‑Ereignis reagiert. Das Makro kann programmgesteuert injiziert werden, das liegt jedoch außerhalb des Umfangs dieses Tutorials. Wichtig ist, dass der Button bereits vorhanden ist und seine Caption gesetzt ist – bereit für jede von Ihnen gewünschte Ereignisbehandlung.

## Häufige Stolperfallen und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Button erscheint verschoben | Koordinaten sind in Punkten, nicht in Pixeln | Pixelwerte in Punkte umrechnen (`points = pixels * 72 / DPI`) |
| Caption ändert sich nach dem Speichern nicht | `SetCaption` nach `Save` aufgerufen | Caption immer **vor** `doc.Save` setzen |
| Steuerelement in älteren Word‑Versionen nicht sichtbar | Ältere Word‑Builds unterstützen ActiveX nicht vollständig | Auf Ziel‑Word‑Version testen; ggf. `CheckBox` oder `DropDownList` als Alternative verwenden |
| Lizenzwarnung in der Ausgabe | Evaluierungslizenz ist abgelaufen | Gültige Aspose.Words‑Lizenz anwenden via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle erforderlichen `using`‑Direktiven und demonstriert den gesamten Workflow von der Dokumenterstellung bis zum Speichern.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Führen Sie das Programm mit `dotnet run` aus. Nach der Ausführung öffnen Sie *ActiveXButton.docx* und prüfen, dass die Caption des Buttons **Click Me** lautet.

## Zusammenfassung des Gelernten

* Sie haben gelernt, wie man **set button text** auf einem ActiveX‑Button mit Aspose.Words festlegt.  
* Sie haben die genauen Schritte gesehen, um **how to insert button**, **create button control** und **add activex control** in ein Word‑Dokument einzufügen.  
* Sie besitzen nun ein wiederverwendbares Code‑Snippet, das Sie für jedes formularbasierte Word‑Automatisierungsprojekt anpassen können.

## Nächste Schritte

* Erkunden Sie weitere `Forms2OleControlType`‑Werte wie `CHECKBOX` oder `LISTBOX`, um umfangreichere Formulare zu bauen.  
* Kombinieren Sie den Button mit einem VBA‑Makro, um Berechnungen oder Datenvalidierungen durchzuführen.  
* Nutzen Sie Aspose.Words’ `FormField`‑API, um Benutzereingaben nach dem Ausfüllen des Dokuments auszulesen.

Experimentieren Sie gern mit Größe, Position und Caption, um Ihre Design‑Anforderungen zu erfüllen. Bei Problemen hilft Ihnen die Aspose.Words‑Dokumentation mit detaillierten Referenzen zu jeder in diesem Tutorial verwendeten Klasse.

Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}