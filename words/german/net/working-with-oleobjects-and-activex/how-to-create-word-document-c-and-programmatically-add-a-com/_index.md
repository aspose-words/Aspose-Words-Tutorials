---
category: general
date: 2026-09-11
description: Erfahren Sie, wie Sie in C# ein Word‑Dokument erstellen und programmgesteuert
  eine Befehlsschaltfläche mit Aspose.Words hinzufügen – in wenigen einfachen Schritten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: de
lastmod: 2026-09-11
og_description: Erstellen Sie ein Word‑Dokument in C# und fügen Sie programmgesteuert
  einen Befehls‑Button mit Aspose.Words hinzu. Folgen Sie diesem vollständigen Leitfaden
  für eine funktionierende Lösung.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Word-Dokument in C# erstellen – einen Befehls‑Button programmgesteuert hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Wie man ein Word‑Dokument in C# erstellt und programmgesteuert eine Befehlsschaltfläche
  hinzufügt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word‑Dokument in C# erstellt und programmgesteuert einen Command‑Button hinzufügt

Wenn Sie ein **Word‑Dokument in C#** erstellen und einen interaktiven Button einbetten möchten, zeigt Ihnen diese Anleitung genau, wie das geht. Mit Aspose.Words können Sie programmgesteuert einen Command‑Button in nur wenigen Code‑Zeilen hinzufügen und damit manuelle UI‑Arbeit in Word vermeiden.

In diesem Tutorial lernen Sie:

* Ein leeres Word‑Dokument mit C# initialisieren.
* Ein ActiveX **CommandButton**‑Steuerelement einfügen.
* Die Eigenschaften des Buttons wie Name und Beschriftung festlegen.
* Das Dokument speichern, sodass der Button beim Öffnen in Microsoft Word angezeigt wird.

Es werden keine externen Werkzeuge außer der Aspose.Words for .NET‑Bibliothek benötigt, und die Schritte funktionieren mit .NET 6+ oder .NET Framework 4.6.2 und höher.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

| Anforderung | Grund |
|------------|--------|
| .NET 6 SDK (oder .NET Framework 4.6.2+) | Stellt die Laufzeit für das C#‑Projekt bereit. |
| Visual Studio 2022 (oder jede C#‑IDE) | Erleichtert das Schreiben, Erstellen und Ausführen des Codes. |
| Aspose.Words for .NET NuGet‑Paket | Liefert die Klassen `Document`, `DocumentBuilder` und `Forms2OleControl`, die im Beispiel verwendet werden. |
| Grundkenntnisse in C#‑Syntax | Ermöglicht das Verstehen des Codes ohne zusätzliche Lernkurven. |

Sie können das Aspose.Words‑Paket über die NuGet‑Konsole hinzufügen:

```powershell
Install-Package Aspose.Words
```

## Schritt 1: Ein neues C#‑Konsolenprojekt einrichten

Erstellen Sie eine Konsolenanwendung, die die Word‑Datei generiert. Öffnen Sie ein Terminal und führen Sie aus:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Die erzeugte Datei `Program.cs` enthält den Code, der in den folgenden Schritten gezeigt wird.

## Schritt 2: Ein leeres Dokument und einen DocumentBuilder erstellen

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren, das eine leere `.docx`‑Datei repräsentiert, sowie einen `DocumentBuilder`, mit dem Sie den Inhalt des Dokuments bearbeiten können.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:**  
`Document` ist der Container für alle Word‑Elemente (Absätze, Tabellen, Steuerelemente). `DocumentBuilder` bietet eine fluente API, um Objekte an der aktuellen Cursor‑Position einzufügen, ohne sich mit Low‑Level‑Knoten‑Sammlungen beschäftigen zu müssen.

## Schritt 3: Ein ActiveX CommandButton‑Steuerelement einfügen

Aspose.Words unterstützt das Einfügen von Legacy‑ActiveX‑Steuerelementen über die Methode `InsertForms2OleControl`. Die Methode benötigt den Steuerelementtyp und die gewünschte Größe in Punkten.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Was im Hintergrund passiert:**  
Word behandelt ein ActiveX‑Steuerelement als OLE‑Objekt (Object Linking and Embedding). Die Klasse `Forms2OleControl` kapselt die OLE‑Daten und stellt Eigenschaften wie `Name` und `Caption` bereit.

## Schritt 4: Namen und Beschriftung des Buttons konfigurieren

Nachdem das Steuerelement platziert ist, können Sie dessen Laufzeit‑Eigenschaften anpassen. Das Setzen eines aussagekräftigen `Name` hilft Ihnen, den Button später zu identifizieren, während `Caption` den auf dem Button angezeigten Text definiert.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro‑Tipp:**  
Wenn Sie das Klick‑Ereignis des Buttons mit VBA verarbeiten wollen, wird `Name` zum Makronamen, den Sie referenzieren, z. B. `Sub btnSubmit_Click()`.

## Schritt 5: Das Dokument auf die Festplatte speichern

Zum Schluss schreiben Sie das Dokument in eine `.docx`‑Datei. Wählen Sie einen Ordner, in den Sie Schreibzugriff haben; das Beispiel verwendet einen relativen Pfad, der im Ausgabeverzeichnis des Projekts aufgelöst wird.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Das Ausführen des Programms erzeugt `CommandButton.docx`. Öffnen Sie die Datei in Microsoft Word, um einen anklickbaren **Submit**‑Button zu sehen:

![Word document with a Submit command button](/images/command-button.png "Screenshot of a Word document containing a Submit command button created with C#")

*Image alt text (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Ergebnis überprüfen

1. Starten Sie Word und öffnen Sie `CommandButton.docx`.  
2. Sie sollten einen Button mit der Beschriftung **Submit** im Dokumentenkörper sehen.  
3. Wenn Sie mit der Maus über den Button fahren, wird im **Properties**‑Fenster (Entwicklertools → Eigenschaften) der Name `btnSubmit` angezeigt.  

Falls der Button nicht erscheint, stellen Sie sicher, dass die **Entwicklertools**‑Registerkarte in Word aktiviert ist (Datei → Optionen → Menüband anpassen → **Entwicklertools** aktivieren). ActiveX‑Steuerelemente werden ausgeblendet, wenn diese Registerkarte deaktiviert ist.

## Häufige Varianten und Sonderfälle behandeln

| Situation | Empfohlene Anpassung |
|-----------|------------------------|
| **Andere Button‑Größe** | Ändern Sie die Breiten‑ und Höhen‑Argumente in `InsertForms2OleControl`. Zum Beispiel erzeugt `150, 40` einen größeren Button. |
| **Mehrere Buttons** | Rufen Sie `InsertForms2OleControl` mehrfach auf und bewegen Sie den Cursor des Builders zwischen den Aufrufen (`builder.Writeln();`). |
| **Button ohne ActiveX** | Verwenden Sie `InsertFormField`, um ein Legacy‑Formularfeld (z. B. ein Kontrollkästchen) hinzuzufügen, wenn Sie Kompatibilität zu älteren Word‑Versionen benötigen, die ActiveX blockieren. |
| **Plattformübergreifende Nutzung** | ActiveX‑Steuerelemente funktionieren nur in Windows‑Versionen von Word. Für Mac oder webbasierte Viewer sollten Sie stattdessen einen Hyperlink einfügen, der wie ein Button formatiert ist. |
| **Sicherheitswarnungen** | Word kann beim Öffnen eines Dokuments mit ActiveX‑Steuerelementen eine Sicherheitsabfrage anzeigen. Das Signieren des Dokuments mit einem vertrauenswürdigen Zertifikat reduziert diese Hürde. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in `Program.cs` einfügen können. Es kompiliert und läuft ohne Änderungen, nachdem das Aspose.Words‑NuGet‑Paket hinzugefügt wurde.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Erwartete Konsolenausgabe:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Das Öffnen der erzeugten Datei zeigt den **Submit**‑Button, bereit zur Interaktion.

## Fazit

Sie wissen jetzt, wie Sie **Word‑Dokument in C#** erstellen und **programmgesteuert Command‑Button‑Steuerelemente** mit Aspose.Words hinzufügen. Der Prozess reduziert sich auf das Initialisieren eines `Document`, das Einfügen eines `Forms2OleControl`, das Konfigurieren seiner Eigenschaften und das Speichern der Datei. Von hier aus können Sie:

* Weitere Steuerelemente (z. B. Checkboxen, Textfelder) hinzufügen, indem Sie `ControlType` ändern.
* VBA‑Makros an den Button anhängen, um benutzerdefinierte Logik zu implementieren.
* Diese Technik mit anderen Aspose.Words‑Funktionen wie Seriendruck oder Vorlagenbefüllung kombinieren.

Experimentieren Sie mit unterschiedlichen Größen, Beschriftungen und mehreren Buttons, um Ihr Automatisierungsszenario zu optimieren. Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}