---
category: general
date: 2026-09-11
description: Erfahren Sie, wie Sie forms2olecontrol im Code mit Aspose.Words DocumentBuilder erstellen.
  Diese Schritt‑für‑Schritt‑Anleitung behandelt das Einfügen von ActiveX‑Befehlsschaltflächen,
  die Verwendung von setOleClassName und die Größenanpassung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: de
lastmod: 2026-09-11
og_description: Erstellen Sie forms2olecontrol im Code mit Aspose.Words. Befolgen
  Sie diese Anleitung, um eine ActiveX-Schaltfläche einzufügen, ihren Klassennamen
  festzulegen und ihre Größe anzupassen.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Erstellen von forms2olecontrol im Code – vollständiger Aspose.Words-Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Wie man forms2olecontrol im Code mit Aspose.Words erstellt
url: /de/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So erstellen Sie forms2olecontrol im Code mit Aspose.Words

Wenn Sie **forms2olecontrol im Code erstellen** müssen, zeigt Ihnen dieser Leitfaden genau, wie Sie dies mit der Aspose.Words .NET API tun. Egal, ob Sie eine Vorlage automatisieren, die einen ActiveX command button erfordert, oder ein Word-Dokument programmgesteuert anreichern möchten – die nachstehenden Schritte decken alles ab, vom Einfügen des Steuerelements bis zur Konfiguration seines Aussehens.

In diesem Tutorial lernen Sie, wie Sie den **Aspose.Words DocumentBuilder** verwenden, um einen **ActiveX command button** einzufügen, seine Klasse mit der **setOleClassName method** festzulegen und die **Forms2OleControl size** anzupassen. Es werden keine externen Werkzeuge benötigt – nur eine .NET‑Entwicklungsumgebung und die Aspose.Words‑Bibliothek.

## Prerequisites

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher installiert (der Code funktioniert auch mit .NET Framework 4.7+)
* Eine aktuelle Version des Aspose.Words für .NET NuGet‑Pakets
* Grundlegende Kenntnisse in C# und dem Konzept von ActiveX‑Steuerelementen in Word‑Dokumenten

Falls etwas fehlt, installieren Sie das NuGet‑Paket mit:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* Erstellen einer `DocumentBuilder`‑Instanz
* Einfügen eines `Forms2OleControl` (das zugrunde liegende Objekt für einen ActiveX command button)
* Zuweisen des korrekten Klassennamens mit `setOleClassName`
* Festlegen der visuellen Breite und Höhe über die **Forms2OleControl size**‑Eigenschaften
* Speichern des Dokuments und Überprüfen des Ergebnisses

Am Ende des Leitfadens besitzen Sie eine voll funktionsfähige Word‑Datei, die einen anklickbaren Button enthält, den Sie weiter anpassen oder an VBA‑Makros binden können.

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialisieren Sie den DocumentBuilder

Die `DocumentBuilder`‑Klasse ist der Einstiegspunkt für die meisten Dokument‑Generierungsaufgaben in Aspose.Words. Sie bietet Methoden zum Hinzufügen von Text, Bildern, Tabellen und – wichtig für dieses Tutorial – OLE‑Steuerelementen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:**  
`DocumentBuilder` behält die aktuelle Cursorposition im Dokument bei. Wenn Sie ihn früh erstellen, stellen Sie sicher, dass jede nachfolgende Einfügung – wie der **ActiveX command button** – genau dort erscheint, wo Sie es wünschen.

### Step 2: Insert the Forms2OleControl

Die `insertForms2OleControl`‑Methode gibt ein `Forms2OleControl`‑Objekt zurück. Dieses Objekt stellt den OLE‑Steuerelement‑Platzhalter dar, den Word als ActiveX‑Button rendert.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Warum das wichtig ist:**  
Ohne diesen Aufruf können Sie die Eigenschaften des Steuerelements nicht manipulieren. Das zurückgegebene `Forms2OleControl` gibt Ihnen vollen Zugriff auf die **setOleClassName method**, Größenattribute und weitere OLE‑spezifische Einstellungen.

### Step 3: Specify the ActiveX class with setOleClassName

Word muss wissen, welchen Typ von ActiveX‑Steuerelement es rendern soll. Der Klassenname für einen Standard‑Befehlsschalter lautet `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Warum das wichtig ist:**  
Die `setOleClassName`‑Methode ist die Brücke zwischen dem generischen OLE‑Platzhalter und dem konkreten **ActiveX command button**. Ein falscher Klassenname führt zu einem leeren Objekt oder zu einem Laufzeitfehler beim Öffnen des Dokuments.

### Step 4: Adjust the Forms2OleControl size

Ein Button, der zu klein oder zu groß ist, wirkt unprofessionell. Sie können seine Abmessungen mit `setWidth` und `setHeight` steuern.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Warum das wichtig ist:**  
Diese Eigenschaften bilden die **Forms2OleControl size**. Sie beeinflussen, wie der Button in der Word‑Benutzeroberfläche erscheint, und stellen sicher, dass ein angehängtes Makro genügend anklickbare Fläche hat.

### Step 5: Save the document and test

Nach der Konfiguration des Steuerelements speichern Sie das Dokument an einem Ort Ihrer Wahl.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Öffnen Sie `ActiveXButton.docx` in Microsoft Word. Sie sollten einen Button mit der Beschriftung „CommandButton1“ (Standard‑Caption) sehen. Ein Klick bewirkt nichts, solange Sie kein VBA‑Makro hinzufügen, aber das Steuerelement selbst ist voll funktionsfähig.

**Erwartete Ausgabe:**  

![Word-Dokument mit eingefügtem ActiveX‑Befehlsschalter](/images/activeX-button.png "Screenshot eines Word-Dokuments, das einen neu erstellten ActiveX‑Befehlsschalter zeigt, der per Code eingefügt wurde")

*Der Alt‑Text des Bildes enthält das primäre Schlüsselwort für Barrierefreiheit und SEO.*

## Understanding the ActiveX Forms2OleControl class

Die `Forms2OleControl`‑Klasse kapselt die Low‑Level‑OLE‑Infrastruktur, die Word für ActiveX‑Elemente verwendet. Sie erbt von `Shape`, sodass Sie bei Bedarf auch typische Shape‑Formatierungen (z. B. Rahmen, Drehung) anwenden können.

* **ActiveX command button** – Der häufigste Anwendungsfall; Sie können ihn über die Entwicklertools von Word an ein Makro binden.
* **setOleClassName method** – Bestimmt, welche COM‑Klasse Word lädt; weitere gültige Werte sind `"Forms.TextBox.1"` und `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Wird über `SetWidth`/`SetHeight` gesteuert. Diese Methoden akzeptieren Punkte (1 pt = 1/72 in).

### When to use Forms2OleControl vs. Content Controls

Wenn Sie nur einfache Dateneingaben benötigen (z. B. ein reines Textfeld), sind Word‑eingebaute Content Controls leichtergewichtig. Verwenden Sie `Forms2OleControl`, wenn Sie volle ActiveX‑Funktionalität wie Ereignisbehandlung oder benutzerdefinierte VBA‑Interaktion benötigen.

## Setting additional properties (optional)

Während die Kernschritte ausreichen, um **forms2olecontrol in code** zu erstellen, möchten Sie häufig das Aussehen oder Verhalten des Buttons feinjustieren.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Warum das wichtig ist:**  
`SetOleData` ermöglicht das Schreiben beliebiger Property‑Werte direkt in den OLE‑Stream. Dies ist der flexibelste Weg, einen **ActiveX command button** ohne VBA anzupassen.

## Common pitfalls and troubleshooting

| Symptom | Wahrscheinliche Ursache | Lösung |
|--------|--------------------------|--------|
| Schaltfläche erscheint als graues Feld | Falscher Klassenname an `setOleClassName` übergeben | Stellen Sie sicher, dass der String exakt `"Forms.CommandButton.1"` lautet (Groß‑/Kleinschreibung beachten) |
| Größe ändert sich nicht | Breite/Höhe vor dem Einfügen des Steuerelements gesetzt | Rufen Sie `SetWidth`/`SetHeight` **nach** `InsertForms2OleControl` immer auf |
| Dokument wirft beim Öffnen „OLE object not found“ | Fehlende Aspose.Words‑Lizenz (Evaluierungs‑Version kann OLE einschränken) | Eine gültige Lizenz anwenden oder die kostenlose Testversion mit voller OLE‑Unterstützung nutzen |
| Schaltflächenbeschriftung bleibt „CommandButton1“ | `SetOleData` nicht verwendet oder Makro liest die Eigenschaft nicht | Verwenden Sie ein VBA‑Makro, um die `"Caption"`‑Eigenschaft zu lesen, oder setzen Sie die Beschriftung über die Word‑Benutzeroberfläche |

## Full, runnable example

Unten finden Sie eine vollständige Konsolenanwendung, die Sie kopieren, einfügen und ausführen können. Sie demonstriert alles, was in diesem Tutorial behandelt wurde.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erklärung jedes Abschnitts**

* **Using‑Direktiven** – Importieren den für `Document`, `DocumentBuilder` und `Forms2OleControl` erforderlichen Aspose.Words‑Namensraum.
* **Dokumenterstellung** – Erstellt eine leere Word‑Datei.
* **InsertForms2OleControl** – Platziert das OLE‑Steuerelement an der aktuellen Cursorposition des Builders.
* **SetOleClassName** – Teilt Word mit, dass das Steuerelement ein **ActiveX command button** ist.
* **SetWidth / SetHeight** – Passt die **Forms2OleControl size** für ein professionelles Aussehen an.
* **SetOleData (optional)** – Zeigt, wie zusätzliche Eigenschaften wie eine Beschriftung geschrieben werden können.
* **Speichern** – Schreibt die endgültige `.docx`‑Datei auf die Festplatte.

Führen Sie das Programm (`dotnet run`) aus und öffnen Sie `ActiveXButton.docx`. Sie sollten einen Button sehen, den Sie später an ein Makro binden können.

## Conclusion

Sie wissen nun, wie Sie **forms2olecontrol in code** mit Aspose.Words erstellen, vom Initialisieren des `DocumentBuilder` bis zur Konfiguration des **ActiveX command button** mit `setOleClassName` und der Steuerung seiner **Forms2OleControl size**. Dieser Ansatz ermöglicht die Automatisierung komplexer Word‑Dokumente, das Einbetten interaktiver UI‑Elemente und das Halten aller Logik innerhalb Ihrer .NET‑Anwendung.

## Was Sie als Nächstes lernen sollten?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Gruppiertes Shape in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechteckiges Shape in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}