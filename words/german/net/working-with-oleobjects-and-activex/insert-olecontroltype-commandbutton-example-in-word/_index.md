---
category: general
date: 2026-08-17
description: Fügen Sie ein OleControlType.CommandButton‑Beispiel in Word mit Aspose.Words
  ein. Erfahren Sie, wie Sie Formularsteuerelemente programmgesteuert zu einem Word‑Dokument
  hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: de
lastmod: 2026-08-17
og_description: Fügen Sie ein OleControlType.CommandButton‑Beispiel in Word mit Aspose.Words
  ein. Folgen Sie dieser Anleitung, um Formularsteuerelemente zu einem Word‑Dokument
  hinzuzufügen.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: OleControlType.CommandButton‑Beispiel in Word einfügen
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: OleControlType.CommandButton‑Beispiel in Word einfügen
url: /de/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OleControlType.CommandButton Beispiel in Word einfügen

Wenn Sie ein **insert OleControlType.CommandButton example** in eine Word-Datei einfügen müssen, zeigt Ihnen diese Anleitung, wie das geht. Sie lernen **wie man Formularsteuerelemente zu einem Word-Dokument hinzufügt** mit Aspose.Words, mit einem vollständigen, ausführbaren C#‑Programm.

Formularsteuerelemente wie ActiveX‑Buttons ermöglichen es Ihnen, interaktive Word‑Vorlagen zu erstellen – nützlich für Verträge, Fragebögen oder interne Werkzeuge. Die nachfolgenden Schritte decken alles ab, von der Projektkonfiguration bis zur Überprüfung, dass der Button korrekt in der gespeicherten `.docx`‑Datei erscheint.

## Voraussetzungen

- .NET 6.0 SDK oder später installiert  
- Visual Studio 2022 (oder jede C#‑IDE)  
- Eine Aspose.Words‑für‑.NET‑Lizenz oder eine kostenlose temporäre Lizenz  
- Grundlegende Kenntnisse in C# und Word‑Dateikonzepten  

> **Pro‑Tipp:** Wenn Sie die kostenlose Testversion verwenden, legen Sie die Lizenzdatei im selben Ordner wie die ausführbare Datei ab und laden Sie sie zu Beginn von `Main`.

## Schritt 1: Neues Konsolenprojekt erstellen und Aspose.Words hinzufügen

Öffnen Sie ein Terminal und führen Sie aus:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Dies erstellt ein sauberes Projekt und holt das neueste Aspose.Words‑Paket, das die `Document`, `DocumentBuilder` und `InsertForms2OleControl`‑APIs bereitstellt, die für das **insert OleControlType.CommandButton example** benötigt werden.

## Schritt 2: Das vollständige Programm schreiben

Erstellen Sie `Program.cs` neu oder ersetzen Sie es durch den folgenden Code. Er enthält alle erforderlichen `using`‑Direktiven, das Laden der Lizenz und den vier‑Schritte‑Ablauf, der im ursprünglichen Snippet gezeigt wird.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Warum jede Zeile wichtig ist

- **License loading** – stellt sicher, dass Sie nicht durch Evaluierungsbeschränkungen limitiert sind.  
- **`Document doc = new Document();`** – erstellt den Container für den gesamten Word‑Inhalt; dies ist die Grundlage des **insert OleControlType.CommandButton example**.  
- **`DocumentBuilder builder = new DocumentBuilder(doc);`** – bietet eine fluente API zum Hinzufügen von Text, Bildern und Steuerelementen.  
- **`InsertForms2OleControl`** – die Kernmethode, die **wie man Formularsteuerelemente zu einem Word‑Dokument hinzufügt** implementiert. Der `OleControlType.CommandButton`‑Enum‑Wert weist Aspose.Words an, einen ActiveX‑Button zu erstellen.  
- **`new Rectangle(100, 100, 80, 30)`** – positioniert den Button 100 pt vom linken und oberen Rand, mit einer Breite von 80 pt und einer Höhe von 30 pt. Passen Sie diese Werte an Ihr Layout an.  
- **`doc.Save`** – schreibt die .docx‑Datei auf die Festplatte; die Datei enthält nun den eingebetteten Button.

## Schritt 3: Das Programm bauen und ausführen

Im Projektordner führen Sie aus:

```bash
dotnet run
```

Sie sollten die Konsolenausgabe sehen:

```
Document saved to ActiveXButton.docx
```

Öffnen Sie `ActiveXButton.docx` in Microsoft Word. Sie sehen einen Button mit der Beschriftung **ClickMe**, der etwa in der Mitte der Seite positioniert ist. Das Klicken des Buttons löst das Standard‑ActiveX‑Verhalten aus (was normalerweise nichts tut, es sei denn, Sie hängen ein Makro an).

![insert olecontroltype.commandbutton example](/images/activex-button.png "ActiveX‑CommandButton in ein Word‑Dokument eingefügt")

*Bild‑Alt‑Text:* insert olecontroltype.commandbutton example – ein ActiveX‑CommandButton, der in einem Word‑Dokument angezeigt wird.

## Schritt 4: Anpassen des Buttons (optional)

Das grundlegende **insert OleControlType.CommandButton example** erstellt einen Standard‑Button. Sie können dessen Beschriftung, Schriftart oder sogar ein Makro anhängen, indem Sie das zugrunde liegende OLE‑Objekt bearbeiten. Nachfolgend ein kurzer Weg, die Beschriftung des Buttons nach dem Einfügen zu ändern:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Hinweis:** Die direkte Manipulation von OLE‑Eigenschaften erfordert ein Verständnis der zugrunde liegenden COM‑Schnittstelle. Für die meisten Szenarien ist die Standard‑Beschriftung ausreichend.

## Schritt 5: Häufige Fallstricke und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Der Button erscheint nicht in Word | Das Dokument wurde als `.docx` gespeichert, aber in einem Viewer geöffnet, der OLE‑Steuerelemente entfernt (z. B. Google Docs). | Öffnen Sie die Datei in Microsoft Word oder Word Online mit Bearbeitungsrechten. |
| Laufzeitfehler `ArgumentOutOfRangeException` | Die `Rectangle`‑Koordinaten liegen außerhalb der Seitenränder. | Verwenden Sie Werte innerhalb der Seitengröße (z. B. 0‑500 für A4). |
| Lizenz‑Ausnahme | Eine Testlizenz läuft nach 30 Tagen ab. | Laden Sie eine gültige Lizenzdatei oder beantragen Sie eine erweiterte Testversion bei Aspose. |

## Schritt 6: Wie dieses Beispiel in größere Automatisierungsprojekte passt

Wenn Sie **wie man Formularsteuerelemente zu einem Word‑Dokument hinzufügt** in großem Umfang benötigen – z. B. beim Erzeugen von Hunderten von Vertragsvorlagen – kapseln Sie die Einfügelogik in einer wiederverwendbaren Methode:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Sie können dann `AddCommandButton` in Schleifen aufrufen, die Datenzeilen verarbeiten, und sicherstellen, dass jedes erzeugte Dokument einen eindeutig benannten Button enthält (z. B. `Approve_001`, `Approve_002`).

## Fazit

Sie haben jetzt ein vollständiges **insert OleControlType.CommandButton example**, das **wie man Formularsteuerelemente zu einem Word‑Dokument hinzufügt** mit Aspose.Words für .NET demonstriert. Das Tutorial behandelte die Projektkonfiguration, den vollständigen Quellcode, Anpassungstipps und gängige Fehlersuchschritte.

Von hier aus können Sie folgendes erkunden:

- Hinzufügen anderer Steuerelementtypen wie **CheckBox** oder **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Das Binden des Buttons an ein VBA‑Makro für umfangreichere Interaktivität.  
- Generieren von PDFs aus demselben Dokument, wobei die Formularfelder erhalten bleiben.

Experimentieren Sie mit verschiedenen Größen, Positionen und Steuerelementnamen, um Ihren spezifischen Anwendungsfall zu erfüllen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Combo‑Box‑Formularfeld in Word‑Dokument einfügen](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Check‑Box‑Formularfeld in Word‑Dokument einfügen](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Text‑Eingabe‑Formularfeld in Word‑Dokument einfügen](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}