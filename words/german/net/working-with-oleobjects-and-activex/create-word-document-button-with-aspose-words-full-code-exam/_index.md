---
category: general
date: 2026-07-23
description: Word‑Dokument‑Schaltfläche mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung
  zum Einfügen eines ActiveX‑CommandButtons in eine .docx‑Datei.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: de
lastmod: 2026-07-23
og_description: 'Word-Dokument-Schaltfläche mit Aspose.Words erstellen: Erfahren Sie,
  wie Sie in wenigen Minuten ein ActiveX‑CommandButton in eine Word‑Datei einbetten.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Schaltfläche zum Erstellen eines Word‑Dokuments – Aspose.Words Komplettanleitung
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Schaltfläche zum Erstellen eines Word‑Dokuments mit Aspose.Words – Vollständiges
  Codebeispiel
url: /de/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument‑Schaltfläche mit Aspose.Words – Vollständiger Programmierleitfaden

Haben Sie jemals eine **Word‑Dokument‑Schaltfläche** erstellen müssen, waren sich aber nicht sicher, welche API Sie dafür verwenden sollen? Sie sind nicht allein – die meisten Entwickler stoßen an Grenzen, wenn sie interaktive Steuerelemente in eine .docx‑Datei einbetten wollen. Die gute Nachricht? Mit Aspose.Words für .NET können Sie in nur wenigen Codezeilen ein voll funktionsfähiges ActiveX CommandButton in ein Word‑Dokument einfügen.

In diesem Tutorial führen wir Sie durch den gesamten Prozess: von der Einrichtung des Projekts, der Initialisierung eines `DocumentBuilder`, dem Einfügen der Schaltfläche mit `InsertForms2OleControl` und schließlich dem Speichern der Datei, sodass Word das Steuerelement erkennt. Am Ende haben Sie eine einsatzbereite Word‑Datei, die eine anklickbare Schaltfläche enthält – ohne COM‑Interop‑Akrobatik.

## Was Sie benötigen

- **.NET 6.0** oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
- **Aspose.Words for .NET** NuGet‑Paket (Version 23.9 oder neuer).  
- Grundlegendes Verständnis von C# (wir halten die Syntax einsteigerfreundlich).  
- Visual Studio 2022 oder eine beliebige IDE Ihrer Wahl.

Das war’s – keine zusätzlichen COM‑Referenzen, kein Office‑Interop, nur reiner Managed‑Code.

---

## Schritt 1: Aspose.Words einrichten, um **Word‑Dokument‑Schaltfläche erstellen**

Zuerst fügen Sie das Aspose.Words‑Paket zu Ihrem Projekt hinzu:

```bash
dotnet add package Aspose.Words
```

Oder, wenn Sie die Visual‑Studio‑NuGet‑Benutzeroberfläche verwenden, suchen Sie nach „Aspose.Words“ und klicken Sie auf **Install**. Diese eine Zeile gibt Ihnen Zugriff auf die Klassen `Document`, `DocumentBuilder` und die Methode `InsertForms2OleControl`, die wir später benötigen.

> **Pro‑Tipp:** Halten Sie Ihre NuGet‑Pakete auf dem neuesten Stand; neuere Versionen enthalten häufig Fehlerbehebungen für die ActiveX‑Verarbeitung.

---

## Schritt 2: **DocumentBuilder** für ein **ActiveX CommandButton** initialisieren

Jetzt erstellen wir ein neues Word‑Dokument und erzeugen einen `DocumentBuilder`. Denken Sie an `DocumentBuilder` als Pinsel, mit dem Sie Inhalte auf die Leinwand zeichnen können.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Beachten Sie, dass wir `System.Drawing` importieren – die Struktur `Rectangle` definiert die Position und Größe der Schaltfläche. Hier wird das **ActiveX CommandButton** platziert.

## Schritt 3: **InsertForms2OleControl** verwenden, um ein **CommandButton** hinzuzufügen

Hier ist das Herzstück des Tutorials: das Einfügen der Schaltfläche selbst. Die Methode `InsertForms2OleControl` erwartet drei Argumente – den Steuertyp, ein `Rectangle` und optional einen Namen. Wir verwenden `OleControlType.CommandButton`, um das gewünschte Steuerelement zu spezifizieren.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Dieser einzelne Aufruf erledigt viel:

1. **Erstellt** ein OLE‑Objekt innerhalb der Word‑Datei.  
2. **Registriert** es als ActiveX CommandButton, das Word als anklickbares UI‑Element darstellt.  
3. **Positioniert** es gemäß dem übergebenen Rechteck.

Wenn Sie die Beschriftung der Schaltfläche oder andere Eigenschaften ändern müssen, können Sie dies nach dem Einfügen tun, indem Sie auf das zugrunde liegende `OleFormat` zugreifen. Für die meisten Szenarien reicht die Standardbeschriftung („CommandButton1“) aus.

## Schritt 4: Das Word‑Dokument mit dem **CommandButton** speichern

Das Speichern ist einfach – geben Sie einfach einen Ordner an, in den Sie Schreibzugriff haben. Die Dateierweiterung muss `.docx` sein, damit die Schaltfläche den Rundweg überlebt.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wenn Sie `CommandButton.docx` in Microsoft Word öffnen, sehen Sie eine kleine Schaltfläche in der oberen linken Ecke der ersten Seite. Ein Klick bewirkt zunächst nichts (das würde VBA erfordern), aber das Steuerelement ist voll funktionsfähig und kann später verkabelt werden.

> **Warum das funktioniert:** Aspose.Words schreibt den OLE‑Stream direkt in das DOCX‑Paket, wodurch die Notwendigkeit umgangen wird, dass Word das Steuerelement zur Laufzeit erzeugt. Das garantiert, dass die Schaltfläche genau dort erscheint, wo Sie sie platziert haben.

## Schritt 5: Die Schaltfläche in Word überprüfen

Öffnen Sie die erzeugte Datei:

1. Starten Sie Microsoft Word.  
2. Navigieren Sie zu **Datei → Öffnen** und wählen Sie `CommandButton.docx`.  
3. Sie sollten eine rechteckige Schaltfläche mit der Aufschrift „CommandButton1“ sehen.

Falls Sie die Schaltfläche nicht sehen, stellen Sie sicher, dass der **Entwurfsmodus** aktiviert ist (Entwickler → Entwurfsmodus). Dieser schaltet die visuelle Darstellung von ActiveX‑Steuerelementen ein.

## Schritt 6: Erweiterte Optionen – Anpassen des **ActiveX CommandButton**

Im Folgenden finden Sie einige schnelle Anpassungen, die nützlich sein könnten:

| Ziel | Code‑Snippet |
|------|--------------|
| Beschriftung ändern | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Makronamen festlegen (erfordert Word‑Makro‑Unterstützung) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Nach dem Einfügen Größe ändern | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Diese Snippets demonstrieren die Flexibilität von `InsertForms2OleControl`. Sie können sogar andere ActiveX‑Steuerelemente wie `CheckBox` oder `ListBox` einbetten, indem Sie das `OleControlType`‑Enum austauschen.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort einsetzbare Programm, das **eine Word‑Dokument‑Schaltfläche** von Grund auf **erstellt**:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Erwartete Ausgabe, wenn Sie das Programm ausführen:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Öffnen Sie die resultierende Datei und Sie sehen die Schaltfläche genau dort, wo der Code sie platziert hat.

## Häufige Fallstricke & wie man sie vermeidet

- **Fehlende `System.Drawing`‑Referenz** – Die Struktur `Rectangle` befindet sich dort; ohne sie meldet der Compiler einen Fehler.  
- **Verwendung einer älteren Aspose.Words‑Version** – Frühere Releases unterstützten `InsertForms2OleControl` nicht vollständig. Aktualisieren Sie auf das neueste stabile Paket.  
- **Speichern als `.doc` statt `.docx`** – Der OLE‑Stream wird im älteren Binärformat entfernt, wodurch die Schaltfläche verschwindet.  
- **Ausführen auf einem headless Server ohne installierte Word‑Version** – Die Schaltfläche bleibt zwar in der Datei, kann aber ohne Word nicht angezeigt werden. Das ist für automatisierte Generierungspipelines in Ordnung.

## Nächste Schritte – Erweiterung des **Word‑Dokument‑Schaltfläche**‑Workflows

Jetzt, wo Sie die Grundlagen beherrschen, überlegen Sie sich diese weiterführenden Ideen:

- **VBA‑Makros** an die Schaltfläche anhängen, um benutzerdefinierte Geschäftslogik zu implementieren.  
- **Mehrere Schaltflächen** in einer Schleife generieren für dynamische Formulare.  
- **Mit Aspose.PDF kombinieren**, um dasselbe Dokument nach PDF zu exportieren und dabei das Layout beizubehalten (die Schaltfläche wird im PDF zu einem statischen Bild).  
- **

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält komplette, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Inline‑Bild in Word‑Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}