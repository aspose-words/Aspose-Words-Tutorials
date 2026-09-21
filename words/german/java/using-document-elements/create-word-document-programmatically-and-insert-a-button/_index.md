---
category: general
date: 2026-09-21
description: Erstelle ein Word‑Dokument programmgesteuert und lerne, wie man die Schaltfläche
  zum Speichern des Word‑Dokuments, die Schaltfläche zum Einfügen von Befehlen und
  die Beschriftung der Befehls‑Schaltfläche mit DocumentBuilder festlegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words.
  Erfahren Sie, wie Sie die Schaltfläche zum Speichern des Word‑Dokuments, das Einfügen
  einer Befehls‑Schaltfläche, das Festlegen der Beschriftung einer Befehls‑Schaltfläche
  und die Verwendung von DocumentBuilder für interaktive Formulare nutzen.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Word‑Dokument programmgesteuert erstellen und einen Button hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Word‑Dokument programmgesteuert erstellen und einen Button einfügen
url: /de/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert erstellen und eine Schaltfläche einfügen

Wenn Sie **Word-Dokument programmgesteuert erstellen** müssen, bietet Aspose.Words eine fluente API, mit der Sie interaktive Steuerelemente wie einen CommandButton hinzufügen können. Dieses Tutorial erklärt außerdem **wie man DocumentBuilder verwendet**, wie man **Word-Dokument-Schaltfläche speichert** und wie man **die Beschriftung der CommandButton-Schaltfläche festlegt**, sodass die Schaltfläche genau so erscheint, wie Sie es in der .docx-Datei erwarten.

Sie lernen:

* Ein leeres Dokument mit `Document` initialisieren.
* Mit `DocumentBuilder` das Dokument bearbeiten.
* Ein **CommandButton** einfügen (`insert command button word`).
* Den Namen und die sichtbare Beschriftung der Schaltfläche festlegen (`set command button caption`).
* Das Ergebnis auf dem Datenträger speichern (`save word document button`).

Die Schritte sind für .NET‑Entwickler geschrieben, die C# und das aktuelle Aspose.Words für .NET (v24.10) verwenden. Keine zusätzlichen NuGet‑Pakete sind über Aspose.Words hinaus erforderlich.

---

## Was Sie vor dem Start benötigen

| Voraussetzung | Grund |
|--------------|--------|
| Visual Studio 2022 (oder jede C#‑IDE) | Zum Kompilieren und Ausführen des Beispielcodes. |
| .NET 6.0 SDK oder neuer | Stellt die Laufzeit für das Beispiel bereit. |
| Aspose.Words für .NET (v24.10 oder neuer) | Die Bibliothek, die es Ihnen ermöglicht, **Word-Dokument programmgesteuert zu erstellen** und Formularsteuerelemente zu manipulieren. |
| Grundlegende Kenntnisse in C# und OOP-Konzepten | Erforderlich, um den Codeablauf zu verstehen. |

You can install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Word-Dokument programmgesteuert erstellen

Der erste Schritt besteht darin, ein leeres `Document` zu instanziieren. Dieses Objekt repräsentiert die gesamte Word‑Datei im Speicher.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Das programmgesteuerte Erstellen des Dokuments gibt Ihnen eine leere Leinwand, auf der Sie Absätze, Tabellen oder interaktive Steuerelemente hinzufügen können.  

---

## Wie man DocumentBuilder verwendet

`DocumentBuilder` ist die Hauptklasse zum Bearbeiten eines `Document`. Sie bietet Methoden zum Einfügen von Text, Bildern und Formularfeldern. In diesem Tutorial verwenden wir sie, um einen CommandButton zu platzieren.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder hält einen internen Cursor, der auf die aktuelle Einfügeposition zeigt. Standardmäßig startet er am Anfang des ersten Abschnitts, was für unser Beispiel ideal ist.

---

## CommandButton in Word einfügen

Aspose.Words behandelt einen CommandButton als ActiveX‑Steuerelement. Die Methode `InsertForms2OleControl` erstellt ein generisches OLE‑Steuerelement, das wir anschließend als Schaltfläche konfigurieren.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Zu diesem Zeitpunkt existiert das Steuerelement im Dokument, hat jedoch keine visuelle Darstellung, bis wir seinen Typ festlegen.

---

## Beschriftung des CommandButton festlegen

Jetzt teilen wir dem OLE‑Steuerelement mit, dass es sich wie ein CommandButton verhalten und ihm eine benutzerfreundliche Bezeichnung geben soll.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Das Festlegen der **CommandButton‑Beschriftung** ist entscheidend, da Word diesen Text auf der Schaltfläche anzeigt. Wenn Sie `SetCaption` weglassen, erscheint die Schaltfläche mit einer generischen Bezeichnung.

---

## Word-Dokument mit Schaltfläche speichern

Abschließend das Dokument auf dem Datenträger speichern. Die Methode `Save` schreibt das gesamte Word‑Paket, einschließlich der neu eingefügten Schaltfläche, in eine .docx‑Datei.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Die Datei `CommandButton.docx` enthält nun eine voll funktionsfähige Schaltfläche mit der Beschriftung **Submit**. Wenn der Benutzer die Datei in Microsoft Word öffnet und die Schaltfläche anklickt, wird die Standardaktion (die Sie später über VBA binden können) ausgelöst.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Es demonstriert den gesamten Arbeitsablauf vom Erstellen des Dokuments bis zum Speichern der Schaltfläche.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Erwartetes Ergebnis**

* Eine Datei namens `CommandButton.docx` am von Ihnen angegebenen Pfad.
* Beim Öffnen der Datei in Microsoft Word wird auf der ersten Seite eine einzelne **Submit**‑Schaltfläche angezeigt.
* Die Schaltfläche kann ausgewählt, in der Größe geändert oder über die **Entwickler**‑Registerkarte von Word mit einem Makro verknüpft werden.

---

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| *Was, wenn ich mehr als eine Schaltfläche benötige?* | Wiederholen Sie die Schritte 3–6 mit unterschiedlichen Namen und Beschriftungen. Jede Schaltfläche muss einen eindeutigen `SetName`‑Wert haben. |
| *Kann ich die Größe der Schaltfläche festlegen?* | Ja. Nach dem Einfügen des Steuerelements können Sie dessen `Width`‑ und `Height`‑Eigenschaften über das `OleFormat`‑Objekt ändern. |
| *Funktioniert die Schaltfläche in allen Word‑Versionen?* | ActiveX‑Steuerelemente werden in der Desktop‑Version von Word (Windows) unterstützt. Sie werden nicht in Word Online oder auf macOS dargestellt. |
| *Wie fügt man einen Klick‑Handler hinzu?* | Sie müssen VBA‑Code schreiben, der den Namen der Schaltfläche (`btnSubmit`) referenziert. Das VBA‑Makro kann über `doc.VbaProject` eingebettet werden. |
| *Was, wenn ich die Schaltfläche in einer Tabellenzelle einfügen muss?* | Bewegen Sie den Cursor des Builders in die gewünschte Zelle (`builder.MoveTo(cell.FirstParagraph)`) bevor Sie `InsertForms2OleControl` aufrufen. |

---

## Profi‑Tipps

* **Pro‑Tipp:** Immer einen aussagekräftigen Namen mit `SetName` festlegen. Das vereinfacht die VBA‑Automatisierung und erleichtert das Debuggen.
* **Achtung:** Vergessen, `SetControlType` aufzurufen. Ohne diesen Aufruf erscheint das OLE‑Objekt als generischer Platzhalter statt als anklickbare Schaltfläche.
* **Performance‑Tipp:** Wenn Sie viele Dokumente in einer Schleife erzeugen, verwenden Sie eine einzelne `DocumentBuilder`‑Instanz und rufen Sie `builder.MoveToDocumentEnd()` vor jeder Einfügung auf, um unnötige Cursor‑Resets zu vermeiden.

---

## Nächste Schritte

Jetzt, da Sie wissen, wie man **Word-Dokument programmgesteuert erstellt**, **CommandButton in Word einfügt**, **die Beschriftung des CommandButton festlegt** und **Word-Dokument mit Schaltfläche speichert**, können Sie weiterführende Szenarien erkunden:

* Fügen Sie **TextFormField**‑Steuerelemente für Benutzereingaben hinzu.
* Kombinieren Sie Schaltflächen mit **MacroButton**‑Feldern, um VBA direkt auszuführen.
* Verwenden Sie **DocumentBuilder.InsertImage**, um Symbole auf Ihren Schaltflächen zu platzieren.
* Integrieren Sie mit ASP.NET, um Word‑Formulare zu erzeugen auf

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Neues Word-Dokument erstellen](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Inline‑Bild in Word-Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}