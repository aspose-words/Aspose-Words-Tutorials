---
category: general
date: 2026-09-05
description: Erstellen Sie ein Word-Dokument mit Aspose.Words C# und lernen Sie, wie
  Sie eine ActiveX‑Befehlsschaltfläche einfügen, die Größe der Schaltfläche festlegen
  und interaktive Schaltflächenfunktionalität hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: de
lastmod: 2026-09-05
og_description: Erstelle ein Word‑Dokument in C# und füge einen ActiveX‑Befehlsschalter
  ein. Dieses Tutorial zeigt, wie man die Größe des Buttons festlegt und interaktive
  Button‑Funktionen hinzufügt.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Word-Dokument mit ActiveX‑Befehlsschaltfläche in C# erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Wie man ein Word‑Dokument mit einer ActiveX‑Schaltfläche in C# erstellt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word-Dokument mit einer ActiveX-Schaltfläche in C# erstellt

Wenn Sie **ein Word-Dokument** programmgesteuert erstellen und ein anklickbares UI-Element einbetten müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Mit Aspose.Words für .NET können Sie **ein Word-Dokument** **erstellen**, **eine Schaltfläche hinzufügen** und ihr Aussehen steuern – alles, ohne Microsoft Word zu öffnen.

Sie lernen, **wie man ActiveX**-Steuerelemente **einfügt**, **die Größe der Schaltfläche festlegt** und die Schaltfläche wie ein interaktives UI‑Komponente funktionieren lässt. Vorkenntnisse in COM oder VBA sind nicht erforderlich; Sie benötigen lediglich eine .NET‑Entwicklungsumgebung und die Aspose.Words‑Bibliothek.

## Was Sie erreichen werden

* **Ein Word-Dokument** von Grund auf mit C# erstellen.  
* **Ein ActiveX‑Befehlsschaltfläche** (die klassische „Click Me“-Steuerung) **einfügen**.  
* **Die Größe der Schaltfläche** und Position präzise **festlegen**.  
* Optional einfache **interaktive Schaltfläche**‑Logik hinzufügen (z. B. ein Makro‑Platzhalter).  
* Speichern Sie die Datei als `.docx`, die in Microsoft Word oder jedem kompatiblen Viewer geöffnet werden kann.

### Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6.0 oder höher | Stellt die Laufzeit für C#‑Code bereit. |
| Aspose.Words für .NET (neueste Version) | Stellt die im Beispiel verwendeten APIs `Document`, `DocumentBuilder` und `Forms2OleControl` bereit. |
| Visual Studio 2022 (oder jede C#‑IDE) | Ermöglicht einfaches Kompilieren und Ausführen des Beispiels. |
| Grundlegende C#‑Kenntnisse | Erforderlich, um den Codeablauf zu verstehen. |

> **Profi‑Tipp:** Wenn Sie eine Testversion von Aspose.Words verwenden, stellen Sie sicher, dass Sie die Lizenz setzen, bevor Sie den Code ausführen, um Evaluierungs‑Wasserzeichen zu vermeiden.

## Wie man ein Word-Dokument erstellt – Gesamtablauf

Der Prozess besteht aus vier logischen Schritten:

1. **Ein neues Dokument initialisieren** und einen `DocumentBuilder` zum Bearbeiten verwenden.  
2. **Eine ActiveX‑Befehlsschaltfläche einfügen** mit `InsertForms2OleControl`.  
3. **Die Schaltfläche konfigurieren** – Beschriftung, Größe und Position.  
4. **Speichern** Sie das Dokument auf dem Datenträger.

Jeder Schritt wird im Folgenden in einem eigenen Abschnitt erklärt.

![Word-Dokument mit einer ActiveX-Schaltfläche](/images/activex-button.png "Screenshot eines Word-Dokuments, das eine mit C# erstellte ActiveX‑Befehlsschaltfläche enthält")

## Wie man eine ActiveX‑Befehlsschaltfläche einfügt

Der **Teil zum Einfügen von ActiveX** beginnt mit der Methode `InsertForms2OleControl`. Diese Methode erstellt ein COM‑basiertes Steuerelement, das Word als ActiveX‑Objekt behandelt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Warum das funktioniert:** `OleControlType.CommandButton` weist Aspose.Words an, die klassische VB‑artige Schaltfläche zu erstellen. Größe und Position werden in Punkten angegeben (1 Punkt = 1/72 Zoll), was eine präzise Layout‑Steuerung ermöglicht.

## Wie man eine Schaltfläche hinzufügt und die Größe festlegt

Nachdem das Steuerelement eingefügt wurde, können Sie dessen visuelle Eigenschaften anpassen. Der Schritt **Schaltfläche hinzufügen** behandelt zudem das **Festlegen der Schaltflächengröße**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Erklärung:**  

* `Caption` ist die Beschriftung, die auf der Schaltfläche angezeigt wird.  
* `Width` und `Height` ermöglichen es Ihnen, die **Schaltflächengröße** nach dem ersten Einfügen festzulegen – nützlich, wenn die Größe von Laufzeitdaten abhängt.  
* `Left` und `Top` verschieben das Steuerelement, ohne das Dokument neu zu erstellen.

> **Häufiges Problem:** Wenn Sie Punkte anstelle von Pixeln verwenden, erscheint die Schaltfläche zu klein oder zu groß. Konvertieren Sie Pixelwerte immer (`px * 72 / DPI`), wenn Sie von Bildschirmmaßen ausgehen.

## Wie man eine interaktive Schaltfläche hinzufügt (optional)

Eine ActiveX‑Schaltfläche kann beim Klicken ein Makro ausführen, aber das Einbetten von VBA‑Code aus C# liegt außerhalb des reinen Aspose.Words‑Workflows. Stattdessen können Sie eine Platzhalter‑Eigenschaft hinzufügen, die Word als Makronamen erkennt.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Wenn der Benutzer das erzeugte `.docx` in Word öffnet, versucht ein Klick auf die Schaltfläche, `MyMacroName` auszuführen. Existiert das Makro nicht, fordert Word den Benutzer zur Erstellung auf.

**Warum Sie das verwenden könnten:** Für Unternehmensformulare, bei denen ein Makro Felder ausfüllt, muss der C#‑Code nur die Schaltfläche platzieren; die Makro‑Logik befindet sich im VBA‑Projekt des Dokuments.

## Dokument speichern und Ergebnis überprüfen

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Erwartete Ausgabe:** Beim Öffnen von `CommandButton.docx` in Microsoft Word wird eine Schaltfläche mit der Aufschrift **Click Me** angezeigt, die 100 pts vom linken Rand und 120 pts vom oberen Rand positioniert ist. Die Abmessungen der Schaltfläche betragen **200 pts × 80 pts**. Ein Klick auf die Schaltfläche löst den Makro‑Platzhalter aus (falls vorhanden).

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige, ausführbare Programm, das alles zusammenführt. Kopieren Sie es in ein neues Konsolen‑App‑Projekt, fügen Sie das Aspose.Words‑NuGet‑Paket hinzu und führen Sie es aus.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Führen Sie das Programm aus und öffnen Sie anschließend die erzeugte Datei. Sie sehen die **interaktive Schaltfläche**, bereit für weitere Anpassungen.

## Häufig gestellte Fragen

| Frage | Antwort |
|-------|---------|
| **Funktioniert das mit .NET Core?** | Ja. Aspose.Words unterstützt .NET Standard, sodass derselbe Code auf .NET 5/6/7 läuft. |
| **Kann ich andere ActiveX‑Steuerelemente verwenden (z. B. CheckBox)?** | Absolut. Ersetzen Sie `OleControlType.CommandButton` durch `OleControlType.CheckBox`, `OleControlType.OptionButton` usw. |
| **Was, wenn ich eine größere Schaltfläche auf einer Querformatseite benötige?** | Passen Sie die Eigenschaften `Width`, `Height`, `Left` und `Top` proportional an. Denken Sie daran, dass Punkte unabhängig von der Seitenausrichtung gleich bleiben. |
| **Ist ein Makro erforderlich, damit die Schaltfläche anklickbar ist?** | Nein. Die Schaltfläche ist als UI‑Element voll funktionsfähig; ein Makro fügt nur benutzerdefiniertes Verhalten beim Klicken hinzu. |

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words **ein Word-Dokument erstellt**, **eine Schaltfläche hinzufügt**, **die Schaltflächengröße festlegt** und optional die Schaltfläche mit einem Makro für das Verhalten **interaktive Schaltfläche hinzufügen** verknüpft. Dieser Ansatz ermöglicht es Ihnen, die Formularerstellung zu automatisieren, dynamische Berichte zu erzeugen oder Word‑basierte UI‑Prototypen direkt aus C# zu erstellen.

Als Nächstes könnten Sie erkunden:

* **Wie man ActiveX‑Kontrollkästchen einfügt** für Umfrageformulare.  
* **Wie man Rich‑Text‑Inhalte** um die Schaltfläche herum mit `DocumentBuilder` hinzufügt.  
* **Wie man das Dokument schützt**, während die Schaltfläche funktionsfähig bleibt.  

Fühlen Sie sich frei, mit verschiedenen Steuerelementtypen, Größen und Makronamen zu experimentieren, um sie an Ihr konkretes Szenario anzupassen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Inline‑Bild in Word-Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Word-Dokument mit Tabelle mit Aspose.Words erstellen](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}