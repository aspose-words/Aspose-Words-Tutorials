---
category: general
date: 2026-07-29
description: Fügen Sie dem Word-Dokument mit Aspose.Words einen Befehlsbutton hinzu.
  Erfahren Sie, wie Sie die Eigenschaften von ActiveX-Steuerelementen festlegen und
  die Beschriftung des Befehlsbuttons in wenigen einfachen Schritten setzen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: de
lastmod: 2026-07-29
og_description: Fügen Sie einem Word-Dokument mit Aspose.Words eine Schaltfläche hinzu.
  Dieses Tutorial zeigt, wie man ActiveX-Steuereigenschaften festlegt und die Beschriftung
  der Schaltfläche schnell einstellt.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Befehlsschaltfläche zu Word-Dokument hinzufügen – Aspose.Words Schritt für
  Schritt
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Befehlsschaltfläche zu Word‑Dokument mit Aspose.Words hinzufügen – Vollständige
  Anleitung
url: /de/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Befehls‑Schaltfläche zum Word‑Dokument hinzufügen – Vollständiger Programmier‑Durchlauf

Haben Sie jemals **add command button to word document** müssen, waren sich aber nicht sicher, welche API‑Aufrufe zu verwenden sind? Sie sind nicht allein; viele Entwickler stoßen an diese Grenze, wenn sie zum ersten Mal interaktive Steuerelemente in eine DOCX‑Datei einbetten wollen. Die gute Nachricht ist, dass Aspose.Words das überraschend einfach macht. In diesem Leitfaden gehen wir Schritt für Schritt durch das Erstellen eines CommandButton‑ActiveX‑Steuerelements, **set activex control properties**, und **set command button caption** – alles mit sauberem C#‑Code, den Sie sofort kopieren‑und‑einfügen können.

Am Ende dieses Tutorials haben Sie eine voll funktionsfähige Word‑Datei, die einen anklickbaren „Submit“-Button enthält und bereit ist, in Microsoft Word geöffnet zu werden. Keine externen VBA‑Skripte, kein manuelles UI‑Herumfummeln – nur reine programmatische Steuerung.

## Was Sie lernen werden

* Wie man ein leeres Word‑Dokument und einen `DocumentBuilder` erstellt.
* Der genaue Methodenaufruf, um **add command button to word document** mit Aspose.Words zu verwenden.
* Möglichkeiten, **set activex control properties** wie Größe, Position und Name festzulegen.
* Die richtige Technik, um **set command button caption** festzulegen, sodass der Button genau den gewünschten Text anzeigt.
* Tipps zum Umgang mit Sonderfällen wie verschiedenen Button‑Typen, DPI‑Skalierung und Word‑Version‑Kompatibilität.

> **Voraussetzung:** Visual Studio (oder jede C#‑IDE) mit installiertem Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`). Keine vorherige ActiveX‑Erfahrung erforderlich.

---

## Schritt 1: Projekt einrichten und Namespaces importieren

Bevor wir **add command button to word document** ausführen können, benötigen wir ein C#‑Projekt, das Aspose.Words referenziert. Erstellen Sie eine neue .NET‑Konsolenanwendung und fügen Sie anschließend das NuGet‑Paket hinzu:

```bash
dotnet add package Aspose.Words
```

Jetzt fügen Sie die erforderlichen Namespaces in Ihre Quellcodedatei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Diese drei `using`‑Direktiven geben Ihnen Zugriff auf die Klassen `Document`, `DocumentBuilder` und `Forms2OleControl`, die das Einfügen von ActiveX‑Steuerelementen ermöglichen.

*Pro‑Tipp:* Wenn Sie Visual Studio verwenden, schlägt die IDE das automatische Hinzufügen dieser Direktiven vor, sobald Sie die Klassennamen eingeben.

---

## Schritt 2: Leeres Dokument und Builder erstellen

Ein frisches `Document`‑Objekt repräsentiert eine leere Word‑Datei. Der `DocumentBuilder` ist unser praktisches „Stift“, mit dem wir zeichnen, Text einfügen und – entscheidend – ActiveX‑Steuerelemente platzieren können.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

An diesem Punkt ist das Dokument nur eine leere Leinwand – denken Sie an ein sauberes Blatt Papier, das auf Ihren Befehls‑Button wartet.

---

## Schritt 3: CommandButton‑ActiveX‑Steuerelement einfügen

Jetzt fügen wir endlich **add command button to word document** hinzu. Aspose.Words stellt die Methode `InsertForms2OleControl` bereit, die den Steuerelementtyp und die Abmessungen akzeptiert. Wir verwenden `Forms2OleControlType.CommandButton` und geben ihm eine angenehme Breite von 150 Punkten und eine Höhe von 30 Punkten.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Die Methode gibt eine Instanz von `Forms2OleControl` zurück, die wir im nächsten Schritt verwenden, um **set activex control properties** festzulegen.

## Schritt 4: Steuerelement konfigurieren – Name, Beschriftung und Position

### Beschriftung festlegen

Die Beschriftung ist der Text, der auf dem Button selbst erscheint. Um **set command button caption** festzulegen, weisen Sie einfach einen String der Eigenschaft `Caption` zu:

```csharp
commandButton.Caption = "Submit";
```

Sie können `"Submit"` in beliebigen Text ändern – z. B. „Save“, „Export“, „Launch“ usw. – und Word zeigt genau diesen Text an.

### Steuerelement benennen

Dem Steuerelement einen sinnvollen Namen zu geben, erleichtert das spätere Referenzieren (z. B. beim Automatisieren von Word‑Makros). Wir setzen die Eigenschaft `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Positionierung auf der Seite

Word verwendet Punkte (1/72 Zoll) für das Layout. Passen Sie die Eigenschaften `Left` und `Top` an, um den Button an die gewünschte Stelle zu setzen:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Falls Sie den Button relativ zu einem Absatz ausrichten müssen, können Sie zuerst den Cursor des Builders verschieben und dann das Steuerelement einfügen; die Koordinaten beziehen sich dann auf diese Position.

*Sonderfall:* Auf Hoch‑DPI‑Monitoren kann die visuelle Größe in Word leicht abweichen. Um die physische Größe des Buttons über Geräte hinweg konsistent zu halten, können Sie die Punkte basierend auf der Ziel‑DPI (normalerweise 96 DPI für Word) berechnen.

## Schritt 5: Dokument speichern

Nachdem der Button vollständig konfiguriert ist, lässt sich die Datei mit einer einzigen Zeile speichern:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Das resultierende `CommandButton.docx` enthält einen voll funktionsfähigen ActiveX‑Button. Öffnen Sie es in Microsoft Word, und Sie sehen einen „Submit“-Button, der genau an der von Ihnen festgelegten Position liegt.

### Erwartetes Ergebnis

1. Das Word‑Dokument öffnet sich mit einer einzigen Seite.
2. Ein rechteckiger Button mit der Beschriftung **Submit** erscheint an den von Ihnen angegebenen Koordinaten.
3. Wenn Sie mit der rechten Maustaste auf den Button klicken und **Properties** wählen, sehen Sie den Namen `btnSubmit` sowie die von Ihnen gesetzten Eigenschaften.

## Schritt 6: Erweiterte Varianten und häufige Stolperfallen

### Einfügen anderer ActiveX‑Typen

Die Methode `InsertForms2OleControl` ist nicht nur auf CommandButtons beschränkt. Sie können Kontrollkästchen, Optionsschaltflächen oder sogar benutzerdefinierte ActiveX‑Objekte einbetten:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Das gleiche **set activex control properties**‑Muster gilt – Sie müssen lediglich das Typ‑Enum austauschen.

### Umgang mit Word‑Versionen

Ältere Word‑Versionen (vor 2007) verwenden das binäre `.doc`‑Format, das ActiveX‑Steuerelemente anders speichert. Aspose.Words konvertiert das Steuerelement automatisch, wenn Sie als `.doc` speichern, aber einige Eigenschaften (wie die genaue Positionierung) können sich verschieben. Wenn Sie Legacy‑Formate anvisieren, testen Sie die Ausgabe in der jeweiligen Word‑Version.

### Sicherheitseinstellungen

Word kann ActiveX‑Steuerelemente auf Rechnern mit strenger Makro‑Sicherheit deaktivieren. Um einen „Security Warning“-Dialog zu vermeiden, sollten Sie Folgendes in Betracht ziehen:

* Das Dokument mit einem vertrauenswürdigen Zertifikat signieren.
* Benutzer anweisen, ActiveX‑Inhalte für diesen Dateipfad zu aktivieren.
* Eine makrofrei‑Alternative verwenden (z. B. einfache Inhaltssteuerelemente), falls Sicherheit ein Thema ist.

## Schritt 7: Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort ausführbare Programm, das alle besprochenen Schritte enthält. Kopieren Sie es in Ihre `Program.cs`, passen Sie bei Bedarf den Ausgabepfad an und klicken Sie auf **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Was dieser Code macht:**

* Beginnt mit einem frischen Dokument.
* Fügt einen CommandButton ein, **sets activex control properties** und **sets command button caption**.
* Fügt einen kurzen erklärenden Absatz hinzu.
* Speichert die Datei als `CommandButton.docx`.

Führen Sie das Programm aus, öffnen Sie die erzeugte Datei, und Sie sehen den Button unter dem erklärenden Text.

## Fazit

Wir haben gerade gezeigt, wie man **add command button to word document** mit Aspose.Words verwendet, wie man **set activex control properties** festlegt und wie man **set command button caption** definiert – alles in einem knappen, produktionsreifen C#‑Snippet. Der Ansatz skaliert: Tauschen Sie den Steuerelementtyp aus, passen Sie die Abmessungen an oder iterieren Sie über eine Datenquelle, um automatisch Dutzende von Buttons einzufügen.

Möchten Sie weitergehen? Versuchen Sie:

* Den Button an ein Makro binden, das einen Datenexport auslöst.
* Bilder oder benutzerdefinierte Symbole in den Button einfügen mittels der `Picture`‑Eigenschaft.
* Ein komplettes Formular mit mehreren ActiveX‑Steuerelementen (Textfelder, Kombinationsfelder usw.) erstellen.

Experimentieren ist der beste Weg, um die Word‑Automatisierung zu meistern. Wenn Sie auf ein Problem stoßen, überprüfen Sie nochmals Ihre DPI‑Berechnungen und die Word‑Sicherheitseinstellungen. Viel Spaß beim Coden, und mögen Ihre Dokumente immer interaktiver werden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}