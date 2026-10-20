---
category: general
date: 2026-10-20
description: Erstellen Sie ein Word-Dokument programmgesteuert und fügen Sie einen
  Befehlsbutton mit Aspose.Words hinzu. Erfahren Sie, wie Sie ein ActiveX-Steuerelement
  einfügen und die Beschriftung des Buttons festlegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: de
lastmod: 2026-10-20
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert und betten Sie eine
  ActiveX‑Schaltfläche ein. Dieses Tutorial erklärt, wie das Steuerelement eingefügt
  und seine Beschriftung mit Aspose.Words festgelegt wird.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Word-Dokument programmgesteuert erstellen – ActiveX-Schaltfläche hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Word‑Dokument programmgesteuert mit einem ActiveX‑Button erstellen
url: /de/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert mit einer ActiveX-Schaltfläche erstellen

Erstellen Sie ein Word-Dokument programmgesteuert mit Aspose.Words und fügen Sie anschließend eine Schaltfläche hinzu, die Benutzer anklicken können. Dieser Leitfaden führt Sie durch das Einfügen eines ActiveX-Steuerelements, das Konfigurieren seiner Eigenschaften und das Speichern des Ergebnisses als **.docx**‑Datei.

Sie sehen ein vollständiges, ausführbares Beispiel, das Sie in eine Konsolenanwendung kopieren können. Am Ende des Tutorials können Sie eine Word‑Datei erzeugen, die eine voll funktionsfähige Schaltfläche enthält, und Sie verstehen, wie Sie **add command button**, **add activex control**, **insert activex button** und **set button caption** ohne Verlassen Ihres C#‑Codes hinzufügen.

## Voraussetzungen

* .NET 6.0 SDK oder neuer installiert  
* Visual Studio 2022 (oder jede C#‑kompatible IDE)  
* Eine Aspose.Words für .NET Lizenzdatei (die kostenlose Testversion funktioniert für dieses Beispiel)  
* Grundlegende Kenntnisse in C# und dem .NET‑Projektsystem  

Es sind keine zusätzlichen NuGet‑Pakete über **Aspose.Words** hinaus erforderlich, da die ActiveX‑Unterstützung in die Bibliothek integriert ist.

## Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

1. Öffnen Sie ein Terminal oder Visual Studio und erstellen Sie ein neues Konsolenprojekt:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Fügen Sie das Aspose.Words‑Paket hinzu:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Optional) Wenn Sie eine Lizenzdatei haben, legen Sie sie im Projektstamm ab und fügen Sie die folgende Zeile am Anfang von `Program.cs` hinzu, um Evaluationswasserzeichen zu vermeiden:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Schritt 2: Word-Dokument programmgesteuert erstellen – Dokument initialisieren

Der erste Vorgang ist das **create Word document programmatically**. Sie tun dies, indem Sie ein `Document`‑Objekt und einen `DocumentBuilder` instanziieren, mit dem Sie den Dokumentinhalt bearbeiten können.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

Das `Document` repräsentiert die gesamte Datei, während der `DocumentBuilder` einen Cursor verwaltet, den Sie an jede Stelle im Dokument bewegen können. Diese Trennung hält die API sauber und ermöglicht es Ihnen, später **add activex control** hinzuzufügen, ohne Low‑Level‑Strukturen manuell zu verwalten.

## Schritt 3: Schaltfläche hinzufügen – Einfügen eines ActiveX‑Steuerelements

Jetzt werden Sie **add command button** durchführen, indem Sie ein ActiveX‑Steuerelement vom Typ `OleControlType.CommandButton` einfügen. Die Methode `InsertForms2OleControl` erfordert den Steuertyp, einen Standort (`Point`) und eine Größe (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Der obige Aufruf **insert activex button** in das Dokument an den von Ihnen angegebenen genauen Koordinaten. Die Koordinaten werden in Punkten gemessen (1 pt ≈ 1/72 in). Wenn Sie die Schaltfläche in einem bestimmten Absatz benötigen, bewegen Sie zuerst den Cursor des Builders:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Schritt 4: Schaltflächenbeschriftung festlegen – Text der Schaltfläche anpassen

Eine Schaltfläche ohne Beschriftung ist verwirrend, daher werden Sie **set button caption** auf etwas Sinnvolles setzen. Die Eigenschaft `Caption` definiert den auf der Schaltfläche angezeigten Text, während `Name` dem Steuerelement einen programmatischen Bezeichner gibt.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Wenn Sie das Dokument später in ein makroaktiviertes Format (`.docm`) exportieren, muss der `OnClick`‑Wert mit einem VBA‑Makronamen übereinstimmen. Für ein einfaches `.docx` wird die Eigenschaft gespeichert, aber nicht ausgeführt, was für die meisten Automatisierungsszenarien in Ordnung ist.

## Schritt 5: Dokument mit der ActiveX‑Schaltfläche speichern

Nachdem Sie das Steuerelement konfiguriert haben, können Sie **save the document**. Wählen Sie ein Verzeichnis, in das Sie Schreibzugriff haben, und verwenden Sie die `.docx`‑Erweiterung für maximale Kompatibilität.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Wenn Sie die erzeugte Datei in Microsoft Word öffnen, sehen Sie eine Schaltfläche mit der Beschriftung **Submit** an den von Ihnen angegebenen Koordinaten. Das Klicken der Schaltfläche im Desktop‑Client versucht, das Makro `SubmitForm` auszuführen (falls es existiert).

## Schritt 6: Ergebnis überprüfen und häufige Probleme beheben

1. Öffnen Sie `ActiveXCommandButton.docx` in Microsoft Word.  
2. Wechseln Sie in den **Design Mode** (Registerkarte **Entwicklertools** → **Design Mode**), um die Rahmen der Schaltfläche zu sehen.  
3. Wenn die Schaltfläche nicht erscheint, prüfen Sie, ob die Registerkarte **Entwicklertools** aktiviert ist und Ihre Word‑Version ActiveX‑Steuerelemente unterstützt.  
4. Für makroaktivierte Dateien (`.docm`) stellen Sie sicher, dass der Makroname in `OnClick` mit einer VBA‑Routine übereinstimmt; andernfalls zeigt Word eine Sicherheitswarnung an.

### Profi‑Tipp

ActiveX‑Steuerelemente funktionieren nur unter Windows. Wenn Sie plattformübergreifende Interaktivität benötigen, sollten Sie stattdessen **Content Controls** (`RichTextContentControl`) anstelle einer ActiveX‑Schaltfläche verwenden.

## Vollständiger Quellcode

Unten finden Sie das vollständige, sofort ausführbare Programm. Kopieren Sie es in `Program.cs` und führen Sie `dotnet run` aus.



## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument mit ActiveX‑Schaltfläche erstellen – C#‑Leitfaden](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Schaltfläche zu Word-Dokument mit Aspose.Words hinzufügen – Vollständiger Leitfaden](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Word-Dokument‑Schaltfläche mit Aspose.Words erstellen – Vollständiges Codebeispiel](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}