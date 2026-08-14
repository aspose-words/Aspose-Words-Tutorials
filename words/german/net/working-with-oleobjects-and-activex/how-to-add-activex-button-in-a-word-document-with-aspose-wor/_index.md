---
category: general
date: 2026-08-14
description: Wie man mit Aspose.Words eine ActiveX-Schaltfläche in ein Word‑Dokument
  einfügt – lernen Sie, ein leeres Word‑Dokument zu erstellen und programmgesteuert
  eine ActiveX‑Schaltfläche einzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: de
lastmod: 2026-08-14
og_description: Wie man mit Aspose.Words eine ActiveX-Schaltfläche in ein Word-Dokument
  einfügt. Dieses Tutorial zeigt, wie man ein leeres Word-Dokument erstellt, eine
  ActiveX-Schaltfläche einfügt und das Ergebnis speichert.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Wie man in Word eine ActiveX-Schaltfläche hinzufügt – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Wie man mit Aspose.Words einen ActiveX‑Button in ein Word‑Dokument einfügt
url: /de/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine ActiveX-Schaltfläche in ein Word-Dokument mit Aspose.Words hinzufügt

Wenn Sie **ActiveX**‑Steuerelemente zu einer generierten Word‑Datei hinzufügen möchten, zeigt Ihnen dieser Leitfaden die genauen Schritte. Sie lernen, wie man programmgesteuert **eine ActiveX‑Schaltfläche einfügt**, beginnend mit einem **leeren Word‑Dokument erstellen** und endend mit einer gespeicherten Datei, die in Microsoft Word geöffnet werden kann.

Das Hinzufügen einer Schaltfläche, die VBA‑Code ausführt oder ein Makro auslöst, ist eine häufige Anforderung für automatisierte Berichtsgeneratoren, Formulartemplates oder interaktive Verträge. Mit Aspose.Words für .NET können Sie das Dokument erstellen, ohne Office zu starten, was den Prozess schnell und serverfreundlich macht.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 (oder neuer) SDK installiert.
* Visual Studio 2022 oder eine beliebige C#‑kompatible IDE.
* Aspose.Words für .NET NuGet‑Paket (`Aspose.Words` Version 24.9 oder neuer).  
  Installieren Sie es mit:
  ```bash
  dotnet add package Aspose.Words
  ```
* Eine Windows‑Umgebung, wenn Sie die ActiveX‑Schaltfläche testen möchten, da ActiveX‑Steuerelemente die Windows‑Version von Microsoft Word benötigen.

## Schritt 1: Ein leeres Word‑Dokument erstellen

Die erste Aufgabe besteht darin, **ein leeres Word‑Dokument** im Speicher zu **erstellen**. Aspose.Words stellt dafür die Klasse `Document` bereit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` repräsentiert die gesamte .docx‑Datei. Zu diesem Zeitpunkt enthält das Dokument noch keine Seiten, Sie können jedoch sofort Inhalte hinzufügen.

## Schritt 2: Einen DocumentBuilder initialisieren

`DocumentBuilder` ist ein Helfer, mit dem Sie Text, Bilder und andere Objekte in das Dokument einfügen können. Er arbeitet mit der `Document`‑Instanz, die Sie gerade erstellt haben.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder hält eine Cursor‑Position; alles, was Sie nach dieser Zeile einfügen, erscheint am Anfang der ersten Seite.

## Schritt 3: Ein ActiveX‑CommandButton‑Steuerelement einfügen

Aspose.Words stellt die Methode `InsertForms2OleControl` zum Hinzufügen von Legacy‑Formularsteuerelementen, einschließlich ActiveX, bereit. Die Methode benötigt den Steuerelementtyp und seine Größe in Punkten.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Das zurückgegebene `Forms2OleControl`‑Objekt ermöglicht das Konfigurieren von Eigenschaften wie dem Namen und der Beschriftung des Steuerelements.

## Schritt 4: Die Eigenschaften der Schaltfläche konfigurieren

Durch das Setzen eines aussagekräftigen `Name` können Sie später im VBA‑Code auf das Steuerelement verweisen. Die `Caption` ist der Text, den der Benutzer auf der Schaltfläche sieht.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro‑Tipp:** Halten Sie den Namen kurz und alphanumerisch; Word verwirft Namen, die Leerzeichen oder Sonderzeichen enthalten.

## Schritt 5: Das Dokument speichern

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Verwenden Sie die `.docx`‑Erweiterung für moderne Word‑Dateien; die ActiveX‑Schaltfläche funktioniert genauso in `.doc`‑Dateien, aber `.docx` ist das bevorzugte Format für neue Projekte.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Wenn Sie `ActiveXButton.docx` in Microsoft Word öffnen, sehen Sie eine anklickbare **Submit**‑Schaltfläche. Wenn Sie Makros aktivieren, können Sie VBA‑Code an `btnSubmit_Click` anhängen, der ausgeführt wird, sobald der Benutzer die Schaltfläche klickt.

## Vollständiges, ausführbares Beispiel

Alle Teile zusammen ergeben ein eigenständiges Programm, das Sie kopieren, einfügen und ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe** – Nach dem Ausführen des Programms gibt die Konsole den Speicherort aus, und das erzeugte Dokument zeigt in Word eine Schaltfläche mit der Beschriftung **Submit**, die oben auf der ersten Seite positioniert ist.

## Häufige Fragen und Sonderfälle behandeln

### Funktioniert die Schaltfläche in allen Word‑Versionen?

ActiveX‑Steuerelemente werden in der Desktop‑Version von Word unter Windows unterstützt. Sie werden nicht in Word Online, Word für macOS oder mobilen Clients dargestellt. Wenn Sie plattformübergreifende Interaktivität benötigen, sollten Sie stattdessen Inhaltssteuerelemente oder HTML‑basierte Lösungen in Betracht ziehen.

### Was, wenn ich eine andere Größe oder Position benötige?

`InsertForms2OleControl` platziert das Steuerelement an der aktuellen Builder‑Cursor‑Position. Um es zu verschieben, passen Sie den Cursor mit `builder.MoveTo` vor dem Einfügen an oder ändern Sie nach der Erstellung die Eigenschaften `Left` und `Top` des Steuerelements:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Kann ich andere ActiveX‑Typen hinzufügen?

Ja. Die Aufzählung `Forms2OleControlType` enthält `CheckBox`, `OptionButton`, `ListBox` und mehr. Ersetzen Sie `CommandButton` durch den gewünschten Enum‑Wert und passen Sie die Eigenschaften entsprechend an.

### Ist ein Makro erforderlich, damit die Schaltfläche etwas tut?

Die Schaltfläche selbst tut nichts, bis Sie VBA‑Code anhängen. In Word drücken Sie **Alt+F11**, um den VBA‑Editor zu öffnen, suchen `btnSubmit_Click` und schreiben die gewünschte Logik. Das erzeugte Dokument behält das VBA‑Projekt bei, wenn Sie das **SaveFormat.Doc** (Legacy‑`.doc`) Format verwenden, aber `.docx`‑Dateien können keine VBA‑Makros speichern. Verwenden Sie das `.doc`‑Format, wenn Sie eingebettetes VBA benötigen.

## Fazit

Sie wissen jetzt, **wie man ActiveX‑Steuerelemente** zu einer Word‑Datei mit Aspose.Words hinzufügt. Indem Sie die Schritte zum **leeren Word‑Dokument erstellen**, einen `DocumentBuilder` initialisieren, **eine ActiveX‑Schaltfläche einfügen**, deren Eigenschaften konfigurieren und die Datei speichern, können Sie interaktive Word‑Templates direkt aus Ihrem .NET‑Code generieren.

Als Nächstes können Sie verwandte Themen wie **Event‑Handling für ActiveX‑Schaltflächen**, das Hinzufügen von **Word‑Dokumenten mit Aspose** für Tabellen oder Bilder sowie die Sicherung von makroaktivierten Dokumenten für den Unternehmenseinsatz erkunden. Experimentieren Sie mit verschiedenen Steuerelementtypen und Layout‑Optionen, um das Benutzererlebnis an die Anforderungen Ihrer Anwendung anzupassen.

Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument mit Kopf‑ und Fußzeile erstellen mit Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Gruppierungsform in Word‑Dokument erstellen mit Aspose.Words für .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Word‑Dokument mit Tabelle erstellen mit Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}