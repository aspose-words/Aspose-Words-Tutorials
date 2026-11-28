---
category: general
date: 2026-11-18
description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie mit C# einen ActiveX‑Button
  ein. Erfahren Sie, wie Sie das Steuerelement hinzufügen, die Beschriftung des Buttons
  festlegen und die Datei speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: de
lastmod: 2026-11-18
og_description: Erstellen Sie ein leeres Word‑Dokument und fügen Sie mit C# einen
  ActiveX‑Button ein. Folgen Sie diesem vollständigen Tutorial, um das Steuerelement
  hinzuzufügen, die Beschriftung des Buttons festzulegen und das Ergebnis zu speichern.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Erstellen Sie ein leeres Word‑Dokument und fügen Sie einen ActiveX‑Button
  ein – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Leeres Word‑Dokument erstellen und einen ActiveX‑Button einfügen
url: /de/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word-Dokument und fügen Sie einen ActiveX‑Button ein

Wenn Sie ein **leeres Word-Dokument erstellen** und darin einen interaktiven ActiveX‑Button platzieren müssen, zeigt Ihnen diese Anleitung genau, wie Sie dies mit Aspose.Words für .NET erledigen. Sie sehen den vollständigen Code, verstehen, warum jede Zeile wichtig ist, und lernen, wie Sie **die Beschriftung des Buttons festlegen** können, sodass das Steuerelement bereit für die Benutzerinteraktion aussieht.

Zusätzlich zum Hauptziel behandeln wir **wie man ActiveX einfügt**, die Schritte **wie man ein Steuerelement hinzufügt** zu einer Word‑Datei und die Feinheiten von **ActiveX‑Button einfügen** mit einer benutzerdefinierten Beschriftung. Am Ende haben Sie ein wiederverwendbares Muster für jedes Dokument‑Automatisierungsszenario, das eingebettete UI‑Elemente erfordert.

## Was Sie lernen werden

* Wie man programmgesteuert ein **leeres Word-Dokument erstellt**.  
* Die genauen API‑Aufrufe, die zum **Einfügen eines ActiveX‑Buttons** und zum Konfigurieren seiner Eigenschaften erforderlich sind.  
* Wie man **die Beschriftung des Buttons festlegt**, damit das Steuerelement den gewünschten Text anzeigt.  
* Tipps zum Speichern der Datei an einem gewünschten Ort und zum Umgang mit häufigen Fallstricken.

### Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+).  
* Aspose.Words für .NET installiert (`Install-Package Aspose.Words`).  
* Grundlegende Kenntnisse in C# und Visual Studio oder einer beliebigen .NET‑kompatiblen IDE.

---

## Erstellen Sie ein leeres Word-Dokument mit Aspose.Words

Der erste Schritt besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine Word‑Datei dar, die keinen Inhalt enthält, bis wir etwas hinzufügen.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Warum das wichtig ist*: Ein leeres `Document` gibt Ihnen eine saubere Leinwand. Sie können später Absätze, Tabellen oder Steuerelemente hinzufügen, ohne sich um vorhandene Formatierungen sorgen zu müssen.

---

## Initialisieren eines DocumentBuilder zum Arbeiten mit dem Dokument

`DocumentBuilder` ist eine Hilfsklasse, mit der Sie Inhalte an der aktuellen Cursor‑Position einfügen können. Sie verfolgt automatisch, wo Sie sich im Dokument befinden.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist*: Ohne einen `DocumentBuilder` müssten Sie den Low‑Level‑Knotenbaum manuell manipulieren. Der Builder vereinfacht das Einfügen von Text, Bildern und ActiveX‑Steuerelementen.

---

## Wie man einen ActiveX‑Button einfügt (insert activex button)

Jetzt verwenden wir `InsertForms2OleControl`, um ein ActiveX‑Steuerelement einzubetten. Die Methode erfordert drei Argumente:

1. Der Typ des Steuerelements (`OleControlType.CommandButton`).  
2. Ein interner Name für das Steuerelement (verwendet von VBA oder Makro‑Code).  
3. Ein `RectangleF`, das die Position und Größe auf der Seite definiert.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Warum das wichtig ist*: Dies ist das Kernstück davon, **wie man activex** in ein Word‑Dokument einfügt. Die Koordinaten des Rechtecks werden in Punkten angegeben (1 Punkt = 1/72 Zoll). Passen Sie sie an, um den Button dort zu positionieren, wo Sie ihn benötigen.

### Hinweis

Wenn der Button auf einer bestimmten Seite erscheinen soll, bewegen Sie zuerst den Cursor des Builders:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Wie man die Beschriftung des Buttons festlegt (set button caption)

Nachdem das Steuerelement platziert wurde, können Sie seine Eigenschaften ändern. Die sichtbarste Eigenschaft ist `Caption`, die den auf dem Button angezeigten Text bestimmt.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Warum das wichtig ist*: Benutzer sehen die Beschriftung, nicht den internen Namen. Das Ändern macht den Button im endgültigen Dokument sinnvoll.

---

## Speichern des Dokuments mit dem Button

Abschließend schreiben Sie das Dokument auf die Festplatte. Sie können jedes unterstützte Format wählen (`.docx`, `.pdf` usw.). Hier speichern wir als Word‑Dokument.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Warum das wichtig ist*: Das Persistieren der Datei ermöglicht es Ihnen, sie in Microsoft Word zu öffnen und den Button zu testen. Wenn das Dokument geöffnet wird, erscheint der Button mit der Beschriftung „Press“.

### Erwartetes Ergebnis

Das Öffnen von `with_button.docx` in Word zeigt eine leere Seite mit einem rechteckigen Button, der **Press** beschriftet ist. Ein Klick auf den Button bewirkt standardmäßig nichts, da kein VBA‑Makro angehängt ist, aber das Steuerelement ist voll funktionsfähig und kann später an Code angebunden werden.

---

## Wie man ein Steuerelement zu einem bestimmten Absatz hinzufügt (how to add control)

Manchmal möchten Sie den Button in einem bestimmten Absatz platzieren, zum Beispiel nach etwas Anleitungstext. Verwenden Sie `MoveTo`, um den Builder zu positionieren, bevor Sie das Steuerelement einfügen.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Warum das wichtig ist*: Dieses Muster demonstriert **wie man ein Steuerelement hinzufügt** im Kontext, sodass das Layout des Dokuments logisch bleibt.

---

## Häufige Fallstricke und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|-------|----------------|-----|
| Button erscheint außerhalb der Seite | Rechteckkoordinaten liegen außerhalb der Seitenränder | Verwenden Sie `builder.PageSetup`, um die Seitengröße zu erhalten und ein sicheres `RectangleF` zu berechnen. |
| Beschriftung wird nicht angezeigt | `Caption` wurde gesetzt, bevor das Steuerelement vollständig initialisiert war | Setzen Sie `Caption` **nach** dem Aufruf von `InsertForms2OleControl`, wie in Schritt 4 gezeigt. |
| Dokument wird ohne den Button gespeichert | Der Cursor des Builders wurde nach dem Einfügen verschoben, ohne Änderungen zu übernehmen | Halten Sie den Builder auf derselben Seite oder rufen Sie `builder.Document.UpdatePageLayout()` vor dem Speichern auf. |

---

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Es erstellt eine leere Word‑Datei, fügt einen ActiveX‑Button ein, legt dessen Beschriftung fest und speichert das Ergebnis.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ausgabe**: Nach dem Ausführen des Programms öffnen Sie `C:\Temp\with_button.docx` in Microsoft Word. Sie sehen eine einzelne Seite mit dem Text „Unten befindet sich ein programmgesteuerter ActiveX‑Button:“ gefolgt von einem Button mit der Beschriftung **Press**.

---

## Fazit

Sie wissen jetzt, wie man **ein leeres Word‑Dokument erstellt**, **einen ActiveX‑Button einfügt**, **die Beschriftung des Buttons festlegt** und das Ergebnis mit Aspose.Words für .NET **speichert**. Das gleiche Muster kann auf andere ActiveX‑Steuerelemente (Kontrollkästchen, Listboxen usw.) erweitert werden, indem man `OleControlType` ändert.

Als Nächstes könnten Sie **wie man ActiveX‑Button‑Ereignisse** mit VBA einfügt, oder **wie man ein Steuerelement** zu bereits vorhandenen Dokumenten hinzufügt, die bereits Inhalt enthalten, erkunden. Beide Themen bauen direkt auf den hier behandelten Konzepten auf.

Viel Spaß beim Programmieren und fühlen Sie sich frei, mit verschiedenen Größen, Positionen und Beschriftungen zu experimentieren, um die UI‑Anforderungen Ihrer Anwendung zu erfüllen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in dieser Anleitung gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Word‑Dokument in C# mit einem ActiveX‑Command‑Button erstellt](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Wie man einen ActiveX‑Button in ein Word‑Dokument mit Aspose.Words einfügt](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}