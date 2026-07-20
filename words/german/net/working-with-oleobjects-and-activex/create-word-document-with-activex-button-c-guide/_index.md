---
category: general
date: 2026-07-19
description: Erstellen Sie ein Word‑Dokument mit Aspose.Words C# und lernen Sie, wie
  Sie eine ActiveX‑Befehlsschaltfläche hinzufügen, die Größe der Schaltfläche festlegen
  und die Schaltfläche programmgesteuert einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: de
lastmod: 2026-07-19
og_description: Erstellen Sie ein Word‑Dokument mit Aspose.Words C# und betten Sie
  in Sekundenschnelle eine ActiveX‑Befehlsschaltfläche ein. Folgen Sie der Schritt‑für‑Schritt‑Anleitung,
  um die Button‑Größe festzulegen und die Schaltfläche einfach einzufügen.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Word-Dokument mit ActiveX-Schaltfläche erstellen – C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word-Dokument mit ActiveX-Schaltfläche erstellen – C#‑Leitfaden
url: /de/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument mit ActiveX‑Button erstellen – Vollständige C#‑Anleitung

Haben Sie sich jemals gefragt, wie man ein **Word‑Dokument** erstellt, das einen funktionierenden ActiveX‑Button enthält? Vielleicht automatisieren Sie einen Bericht und benötigen ein anklickbares „Genehmigen“-Steuerelement direkt in der Datei. In diesem Tutorial gehen wir genau darauf ein – wir verwenden Aspose.Words für .NET, um einen ActiveX‑Befehlsschalter hinzuzufügen, seine Größe festzulegen und ihn an die gewünschte Stelle einzufügen.  

Wenn Sie sich jemals gefragt haben, *wie man activex*‑Steuerelemente hinzufügt, ohne Word manuell zu öffnen, sind Sie hier genau richtig. Am Ende haben Sie ein lauffähiges Beispiel, eine klare Erklärung jedes Schrittes und Tipps zum Umgang mit häufigen Stolperfallen.

## Was Sie lernen werden

- Wie man Aspose.Words in einem C#‑Projekt einrichtet  
- Der genaue Code, um ein **Word‑Dokument** zu **erstellen** und einen ActiveX‑Befehlsschalter einzubetten  
- Möglichkeiten, die **Button‑Größe festzulegen** und Beschriftung sowie Name anzupassen  
- Die korrekte Methode, um einen **Befehlsschalter einzufügen** und **wie man einen Button** an beliebiger Stelle im Dokument **einfügt**  
- Edge‑Case‑Überlegungen (Word‑Version, Plattform‑Beschränkungen, Sicherheitswarnungen)

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+).  
- Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder ein kostenloser Evaluierungsschlüssel).  
- Visual Studio 2022 (oder jede andere IDE Ihrer Wahl).  
- Grundlegende Kenntnisse in C# und objektorientierter Programmierung.

Weitere Bibliotheken von Drittanbietern sind nicht erforderlich.

---

## Schritt 1: Word‑Dokument erstellen – Projekt‑Setup

Bevor wir einen **Befehlsschalter einfügen** können, benötigen wir eine leere Word‑Datei. Dieser Schritt zeigt außerdem das klassische „Word‑Dokument erstellen“‑Muster mit Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Warum das wichtig ist:** `Document` repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` die aktuelle Cursor‑Position verfolgt. Alle nachfolgenden Einfügungen (einschließlich unseres ActiveX‑Steuerelements) erfolgen relativ zu diesem Builder.

---

## Schritt 2: Wie man ActiveX hinzufügt – den CommandButton‑Steuerung bauen

Jetzt, wo das Dokument existiert, gehen wir den **how to add activex**‑Teil an. Aspose.Words stellt die Klasse `Forms2OleControl` für ActiveX‑Objekte bereit. Hier erstellen wir einen Befehlsschalter und konfigurieren seine Eigenschaften, einschließlich der Anforderung **set button size**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro‑Tipp:** Die Größe wird in Punkten gemessen (1 Punkt = 1/72 Zoll). Passen Sie die Werte an Ihr Layout an; für einen typischen Toolbar‑Button funktionieren 120 × 30 gut.

---

## Schritt 3: Befehlsschalter einfügen – Der Kern von **Insert Command Button**

Nachdem das Steuerelement bereit ist, **insert command button** wir nun an der aktuellen Position des Builders in das Dokument. Sie können den Builder beliebig verschieben (z. B. nach einem Absatz), bevor Sie diese Methode aufrufen.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Wenn Sie **how to insert button** an einem bestimmten Lesezeichen benötigen, verschieben Sie zuerst den Builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Was passiert im Hintergrund?** Aspose.Words schreibt die notwendigen OLE‑Objekt‑Streams in das .docx‑Paket, sodass Word den Button ohne zusätzliche Makros rendern kann.

---

## Schritt 4: Dokument speichern – Abschluss des **Create Word Document**‑Zyklus

Der letzte Schritt ist simpel: Die Datei auf die Festplatte schreiben. Damit ist der Rundlauf von **create word document**, Einbetten des ActiveX und Speichern abgeschlossen.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Öffnen Sie die resultierende Datei in Microsoft Word (nur Windows). Sie sollten einen anklickbaren Button mit der Aufschrift „Click Me“ sehen. Ein Klick löst die Standard‑Aktion eines CommandButton aus – es passiert nichts, solange Sie keinen VBA‑Code anhängen, aber das Steuerelement ist voll funktionsfähig.

> **Erwartetes Ergebnis:** Eine .docx‑Datei mit einer einzelnen Seite, ein Button zentriert am Einfügepunkt, Größe 120 × 30 pt, Beschriftung „Click Me“.  
> ![ActiveX‑Button in ein Word‑Dokument eingefügt](placeholder-image.png)  
> *Bild‑Alt‑Text:* **ActiveX‑Button in ein Word‑Dokument eingefügt mit C#** (entspricht `og_image_alt`).

---

## Schritt 5: Edge Cases, Sicherheit und bewährte Vorgehensweisen

### Plattform‑Beschränkungen
- ActiveX‑Steuerelemente funktionieren nur in der Windows‑Version von Word. Auf macOS oder Word Online erscheint der Button als statisches Bild.  
- In manchen Unternehmensumgebungen ist ActiveX aus Sicherheitsgründen deaktiviert; Sie müssen das Dokument ggf. signieren oder Nutzer informieren, den Inhalt zu aktivieren.

### VBA‑Interaktion (optional)
Wenn der Button ein Makro ausführen soll, müssen Sie nach dem Speichern ein VBA‑Projekt zum Dokument hinzufügen. Aspose.Words erzeugt keinen VBA‑Code automatisch, aber Sie können die API `Document.VbaProject` nutzen, um ihn einzufügen.

### Namenskollisionen
Geben Sie jedem Steuerelement einen eindeutigen `Name`. Die Wiederverwendung desselben Namens kann Laufzeitfehler verursachen, wenn Word das Steuerelement auflösen soll.

### Performance‑Tipp
Beim Einfügen vieler Steuerelemente verwenden Sie eine einzige `DocumentBuilder`‑Instanz und vermeiden Aufrufe von `doc.Save` innerhalb einer Schleife. Sammeln Sie die Einfügungen und speichern Sie einmal am Ende.

---

## Vollständiges funktionierendes Beispiel

Alles zusammengeführt, hier ein komplettes, copy‑and‑paste‑bereites Programm:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Führen Sie das Programm aus, öffnen Sie die gespeicherte Datei, und Sie sehen den Button exakt dort, wo der Builder positioniert war.

---

## Fazit

Wir haben ein **Word‑Dokument** von Grund auf **erstellt**, gelernt, **how to add activex** zu konfigurieren, die **set button size**‑Eigenschaften zu nutzen und die korrekte Vorgehensweise zum **insert command button** sowie **how to insert button** an beliebiger Stelle im Dokument demonstriert.  

Aus einem einzigen Code‑Beispiel haben Sie nun eine solide Basis für umfangreichere Word‑Automatisierung – sei es beim Erstellen von Vorlagen mit interaktiven Formularen, beim Generieren von Verträgen, die eine Benutzerbestätigung erfordern, oder einfach beim Einfügen einiger nützlicher Steuerelemente in einen Bericht.

### Was kommt als Nächstes?

- **Button stylen** – Schriftarten, Farben ändern oder ein Bild‑Hintergrund hinzufügen.  
- **VBA‑Makros anhängen** – den Button Berechnungen ausführen oder externe Programme starten lassen.  
- **Mit anderen Steuerelementen kombinieren** – Kontrollkästchen, Listboxen oder sogar eingebettete Excel‑Tabellen.  

Probieren Sie es aus, und falls Sie auf Probleme stoßen, hinterlassen Sie einen Kommentar unten. Viel Spaß beim Coden und beim Automatisieren von Word mit Aspose.Words!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}