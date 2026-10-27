---
category: general
date: 2026-10-23
description: Erstellen Sie ein leeres Word‑Dokument mit C# und lernen Sie, wie Sie
  ActiveX‑Steuerelemente, einschließlich eines Buttons, mit Aspose.Words einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: de
lastmod: 2026-10-23
og_description: Erstellen Sie ein leeres Word‑Dokument mit C# und lernen Sie, wie
  Sie ActiveX‑Steuerelemente, einschließlich eines Buttons, mit Aspose.Words einfügen.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Erstelle ein leeres Word‑Dokument und füge in C# einen ActiveX‑Button hinzu
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Erstelle ein leeres Word‑Dokument und füge in C# einen ActiveX‑Button hinzu.
url: /de/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word‑Dokument und fügen Sie einen ActiveX‑Button in C# hinzu

Wenn Sie ein **leeres Word‑Dokument erstellen** programmgesteuert benötigen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen ein vollständiges, ausführbares Beispiel, das ein neues Dokument erstellt, einen ActiveX CommandButton einfügt und die Datei speichert – alles mit Aspose.Words für .NET.

Das Hinzufügen eines **ActiveX‑Buttons** ermöglicht das Einbetten interaktiver Funktionalität, die in makroaktivierten Vorlagen oder rein Windows‑basierten Lösungen verwendet werden kann. Am Ende dieses Tutorials können Sie jedes ActiveX‑Steuerelement einfügen, aber wir konzentrieren uns auf das häufigste Szenario: ein **Word‑Dokument‑ActiveX‑Button**, der ein Formular übermittelt.

## Voraussetzungen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
* Visual Studio 2022 (oder jede C#‑IDE)
* **Aspose.Words for .NET** NuGet‑Paket  
  ```bash
  dotnet add package Aspose.Words
  ```
* Grundlegende Kenntnisse der C#‑Syntax

> **Profi‑Tipp:** Aspose.Words ist eine kommerzielle Bibliothek, bietet aber eine kostenlose temporäre Lizenz zum Testen an. Installieren Sie die Lizenz frühzeitig, um das Evaluations‑Wasserzeichen zu vermeiden.

## Schritt 1: Erstellen Sie ein leeres Word‑Dokument mit Aspose.Words

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses stellt eine leere `.docx`‑Datei im Speicher dar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` beginnt ohne Abschnitte, Seiten oder Inhalt. Es ist die leere Leinwand, die Sie für **leeres Word‑Dokument erstellen**‑Szenarien benötigen, wie z. B. das Erzeugen von Berichten von Grund auf.

## Schritt 2: Einen DocumentBuilder erhalten, um das Dokument zu bearbeiten

`DocumentBuilder` bietet eine praktische API zum Hinzufügen von Text, Bildern und Steuerelementen. Wir werden ihn verwenden, um das ActiveX‑Steuerelement zu positionieren.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Der Builder fügt automatisch einen Standardabschnitt und eine erste Seite hinzu, sodass Sie sofort mit dem Einfügen von Objekten beginnen können.

## Schritt 3: So fügen Sie ActiveX‑Steuerelemente in das Dokument ein

Aspose.Words stellt `InsertForms2OleControl` zum Einbetten von OLE/ActiveX‑Objekten bereit. Die Methode benötigt den Steuertyp, die Breite und die Höhe (in Punkten). Im Folgenden fügen wir einen **CommandButton** ein – den klassischen Formular‑Button, den Sie in alten Word‑Vorlagen sehen.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Warum das funktioniert:** `Forms2OleControlType.COMMANDBUTTON` weist Word an, einen Button zu erstellen, der auf Klick‑Ereignisse reagieren kann, wenn das Dokument in einer Windows‑Umgebung geöffnet wird, die ActiveX unterstützt.

## Schritt 4: Ein ActiveX‑Steuerelement erstellen – seine Eigenschaften festlegen

Jetzt geben wir dem Button einen programmatischen Namen und eine sichtbare Beschriftung. Dies ist der Teil von **ActiveX‑Steuerelement erstellen**, den Entwickler häufig übersehen.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` ist der Bezeichner, den Sie aus VBA‑Makros referenzieren (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` ist die Beschriftung, die auf dem Button selbst angezeigt wird.

## Schritt 5: Das Word‑Dokument mit dem ActiveX‑Button speichern

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Die Dateierweiterung muss `.docx` sein (oder `.docm`, wenn Sie später Makros hinzufügen möchten). Das Beispiel speichert in einen Platzhalter‑Ordner – ersetzen Sie diesen durch Ihren eigenen Pfad.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie die resultierende Datei in Microsoft Word öffnen (nur Windows), sehen Sie einen funktionalen **Word‑Dokument‑ActiveX‑Button**, der an VBA‑Code angebunden werden kann.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie in ein neues Konsolenprojekt kopieren und einfügen können.

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe, wenn Sie das Programm ausführen**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Öffnen Sie die erzeugte `ActiveXButton.docx` in Word, und Sie sehen einen Button mit der Aufschrift **Submit**, der oben auf der ersten Seite positioniert ist.

## Randfälle und häufige Stolperfallen

| Situation | Worauf zu achten ist | Empfehlung |
|-----------|----------------------|------------|
| Ausführen unter macOS oder Linux | ActiveX ist eine Windows‑exklusive Technologie, daher wird der Button als Platzhalter angezeigt. | Verwenden Sie das Tutorial nur für Windows‑zielgerichtete Vorlagen. |
| Dokument, das in Word Online geöffnet wird | ActiveX‑Steuerelemente werden in der Browser‑Ansicht nicht unterstützt. | Stellen Sie eine alternative UI bereit oder weisen Sie Benutzer an, die Datei im Desktop‑Client zu öffnen. |
| Bedarf an einer makroaktivierten Datei | `.docx`‑Dateien können keinen VBA‑Code speichern. | Speichern Sie als `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) und fügen Sie das Makro separat hinzu. |
| Größenabweichung des Steuerelements | Breiten‑/Höhenwerte sind in Punkten (1 pt ≈ 1/72 in). | Passen Sie die numerischen Werte an, um die gewünschte visuelle Größe zu erreichen. |

## Häufig gestellte Fragen

**Wie füge ich ActiveX‑Steuerelemente ein, die keine Schaltfläche sind?**  
Verwenden Sie dieselbe `InsertForms2OleControl`‑Methode, übergeben jedoch einen anderen `Forms2OleControlType`‑Enum‑Wert, wie `COMBOBOX` oder `LISTBOX`.

**Kann ich die Schriftart oder Farbe des Buttons ändern?**  
Das Aussehen des ActiveX‑Buttons wird von der Host‑Anwendung (Word) und dem zugrunde liegenden Windows‑Theme bestimmt. Sie können Eigenschaften wie `ForeColor` und `BackColor` über VBA ändern, nachdem das Dokument geöffnet wurde.

**Gibt es eine Möglichkeit, einen Klick‑Handler direkt aus C# hinzuzufügen?**  
Nein. Das Klick‑Ereignis muss von VBA oder einem Word‑Add‑In behandelt werden, da der Button im Prozess von Word läuft, nicht in Ihrer .NET‑Anwendung.

## Fazit

Sie wissen jetzt, wie Sie programmgesteuert ein **leeres Word‑Dokument erstellen** und einen **ActiveX‑Button** mit Aspose.Words für .NET einbetten. Die behandelten Schritte:

1. Ein `Document` instanziieren.  
2. `DocumentBuilder` verwenden, um mit der Datei zu arbeiten.  
3. `InsertForms2OleControl` aufrufen, um **ActiveX‑Steuerelemente einzufügen**.  
4. Die Eigenschaften des Steuerelements konfigurieren (**ActiveX‑Steuerelement erstellen**).  
5. Die Datei speichern, wodurch ein **Word‑Dokument‑ActiveX‑Button** entsteht, der für die VBA‑Integration bereit ist.

Ab hier können Sie weitere Steuerelementtypen hinzufügen, VBA‑Makros anbinden oder das Dokument in PDF konvertieren, wobei der Button (als statisches Bild) erhalten bleibt. Experimentieren Sie mit verschiedenen Größen, Beschriftungen und Namen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}