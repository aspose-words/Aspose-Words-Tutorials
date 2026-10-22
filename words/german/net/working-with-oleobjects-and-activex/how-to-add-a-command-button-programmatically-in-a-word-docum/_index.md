---
category: general
date: 2026-10-13
description: Erfahren Sie, wie Sie programmgesteuert eine Schaltfläche mit Aspose.Words
  hinzufügen. Dieser Leitfaden zeigt außerdem, wie Sie eine Schaltfläche in einem
  Word‑Dokument mit vollständigem C#‑Code erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: de
lastmod: 2026-10-13
og_description: Fügen Sie einem Word-Dokument programmgesteuert einen Befehlsbutton
  hinzu, indem Sie Aspose.Words verwenden. Folgen Sie diesem vollständigen Tutorial,
  um einen Word‑Dokument‑Button mit C# zu erstellen.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Eine Befehlsschaltfläche programmgesteuert zu einem Word‑Dokument hinzufügen
  – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man programmgesteuert eine Befehlsschaltfläche in ein Word‑Dokument einfügt
url: /de/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So fügen Sie programmgesteuert eine Befehls‑Schaltfläche in ein Word‑Dokument ein  

Wenn Sie **programmgesteuert eine Befehls‑Schaltfläche hinzufügen** müssen, bietet Aspose.Words eine saubere API, mit der Sie OLE‑Formularsteuerelemente direkt in eine .docx‑Datei einbetten können. Dieses Tutorial führt Sie durch jeden Schritt, der erforderlich ist, um **eine Word‑Dokument‑Schaltfläche zu erstellen**, die sich wie eine reguläre Formularschaltfläche verhält, wenn das Dokument in Microsoft Word geöffnet wird.  

Sie lernen, wie Sie die Entwicklungsumgebung einrichten, die Schaltfläche einfügen, ihre Eigenschaften konfigurieren und das Ergebnis überprüfen. Es werden keine externen Hilfsprogramme benötigt – nur ein .NET‑Projekt und die Aspose.Words‑Bibliothek für .NET.  

## Voraussetzungen  

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:  

* .NET 6.0 SDK oder höher installiert.  
* Eine aktuelle Version von Aspose.Words für .NET (die Beispiele verwenden 23.12, aber jede Version 22.x+ funktioniert).  
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code.  

Der Code läuft unter Windows, macOS und Linux, da Aspose.Words plattformunabhängig ist.  

## Schritt 1: Projekt einrichten und Aspose.Words referenzieren  

1. Erstellen Sie ein neues Konsolenprojekt:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Fügen Sie das Aspose.Words NuGet‑Paket hinzu:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Öffnen Sie **Program.cs** und ersetzen Sie dessen Inhalt durch das Gerüst, das in den nächsten Schritten gezeigt wird.  

Durch diese Einrichtung des Projekts wird sichergestellt, dass der Compiler die für Formularsteuerelemente erforderlichen Namespaces `Aspose.Words` und `Aspose.Words.Drawing.Forms` finden kann.  

## Schritt 2: Leeres Dokument und DocumentBuilder initialisieren  

Die Klasse `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` eine fluente API zum Hinzufügen von Inhalten bereitstellt.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Warum dieser Schritt wichtig ist* – Ohne einen `DocumentBuilder` können Sie die Schaltfläche nicht präzise auf der Seite positionieren. Der Builder respektiert zudem die aktuelle Cursor‑Position, was das spätere Einfügen mehrerer Steuerelemente erleichtert.  

## Schritt 3: OLE‑Steuerelement für die Befehls‑Schaltfläche einfügen  

Aspose.Words behandelt eine Befehls‑Schaltfläche als OLE‑Steuerelement vom Typ `ControlType.CommandButton`. Sie definieren deren Position und Größe mit einem `RectangleF`, gemessen in Punkten (1 Punkt = 1/72 Zoll).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Wichtige Punkte**  

* Der Ursprung des Rechtecks (X, Y) ist relativ zur oberen linken Ecke der Seite.  
* Das Ändern von `Width` oder `Height` ändert die visuelle Größe der Schaltfläche.  
* `InsertForms2OleControl` gibt ein `Forms2OleControl`‑Objekt zurück, das Sie weiter konfigurieren können.  

## Schritt 4: Namen und Beschriftung der Schaltfläche konfigurieren  

Der **Name** wird von Word‑Makro‑Engine verwendet, um das Steuerelement zu identifizieren, während die **Beschriftung** der Text ist, den der Benutzer sieht.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Wenn Sie später VBA‑Makros hinzufügen möchten, verwenden Sie einen beschreibenden Namen, da der Makro‑Recorder von Word diese Eigenschaft referenziert.  

## Schritt 5: (Optional) Dokument speichern und Ergebnis überprüfen  

Durch das Speichern der Datei können Sie sie in Microsoft Word öffnen, um zu bestätigen, dass die Schaltfläche erscheint und funktioniert.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Wenn Sie *CommandButtonDemo.docx* in Word öffnen, sollten Sie eine Schaltfläche mit der Beschriftung **Submit** sehen, die etwa 1,4 Zoll vom linken Rand und 2,1 Zoll vom oberen Seitenrand positioniert ist. Ein Klick auf die Schaltfläche bewirkt standardmäßig nichts, da kein Makro zugeordnet ist, aber das visuelle Steuerelement ist voll funktionsfähig.  

## Schritt 6: Randfälle und häufige Stolperfallen  

| Situation | Worauf zu achten ist | Empfohlene Lösung |
|-----------|----------------------|-------------------|
| **Schaltfläche überlappt vorhandenen Text** | Das Rechteck kann mit einem Absatz überschneiden, was zu Layout‑Problemen führt. | Fügen Sie die Schaltfläche nach dem Aufruf von `builder.Writeln()` ein, um den Cursor in eine neue Zeile zu bewegen, oder passen Sie die `Y`‑Koordinate an. |
| **Dokument öffnet mit einer Warnung** | Einige Word‑Versionen kennzeichnen OLE‑Steuerelemente, denen ein verknüpftes Programm fehlt. | Stellen Sie sicher, dass der Steuertyp `CommandButton` ist; Word behandelt ihn als Standard‑Formularelement und erfordert kein externes Programm. |
| **Ausführung unter Linux mit Headless‑Umgebung** | Word kann nicht gestartet werden, um die UI zu testen, aber die Datei bleibt gültig. | Verwenden Sie einen Unit‑Test, der die Eigenschaften des Steuerelements (`commandButton.Name`, `commandButton.Caption`) ausliest, um zu prüfen, ob sie korrekt gesetzt wurden. |
| **Mehrere Schaltflächen benötigt** | Die Wiederverwendung desselben `DocumentBuilder` ohne Cursorbewegung fügt die Schaltfläche über der vorherigen ein. | Rufen Sie `builder.MoveToDocumentEnd()` auf oder passen Sie den `Y`‑Wert des Rechtecks vor jeder Einfügung an. |

Das frühzeitige Berücksichtigen dieser Randfälle spart Zeit, wenn die Lösung auf vollständige Formulare mit Dutzenden von Steuerelementen skaliert wird.  

## Schritt 7: Vollständiges, ausführbares Beispiel  

Unten finden Sie ein eigenständiges Programm, das Sie kopieren, einfügen und ohne Änderungen ausführen können (abgesehen von der NuGet‑Wiederherstellung).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe**  

Das Ausführen des Programms gibt einen Pfad ähnlich wie folgt aus:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Das Öffnen des erzeugten *CommandButtonDemo.docx* zeigt eine einzelne **Submit**‑Schaltfläche, die an den im Code definierten Koordinaten platziert ist. Es erscheinen keine zusätzlichen UI‑Elemente, was bestätigt, dass der **add command button programmatically**‑Workflow erfolgreich war.  

## Fazit  

Sie wissen jetzt, wie Sie mit Aspose.Words **programmgesteuert eine Befehls‑Schaltfläche** zu einem Word‑Dokument hinzufügen, und Sie verstehen außerdem, wie Sie **eine Word‑Dokument‑Schaltfläche** erstellen, die später an VBA‑Makros oder externe Automatisierungstools angebunden werden kann. Der Prozess besteht aus dem Initialisieren eines Dokuments, dem Einfügen eines OLE‑`CommandButton`‑Steuerelements, dem Konfigurieren seiner Eigenschaften und dem Speichern der Datei.  

Ab hier könnten Sie:  

* Weitere Steuerelemente (Checkboxen, Textfelder) hinzufügen, indem Sie Schritt 3 mit anderen `ControlType`‑Werten wiederholen.  
* VBA‑Makros an die Schaltfläche anhängen, um Aktionen wie das Speichern eines Formulars oder das Senden einer E‑Mail auszuführen.  
* Gesamte Formulare dynamisch erzeugen, indem Sie über eine datenbasierte Sammlung von Felddefinitionen iterieren.  

Experimentieren Sie mit den Rechteckkoordinaten und der Beschriftung der Schaltfläche, um Ihr UI‑Design anzupassen. Viel Spaß beim Coden!  


## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Combo‑Box‑Formularfeld zu einem Word‑Dokument hinzufügen mit Aspose.Words für .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Checkbox‑Formularfeld zu einem Word‑Dokument hinzufügen mit Aspose.Words für .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Leeres Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}