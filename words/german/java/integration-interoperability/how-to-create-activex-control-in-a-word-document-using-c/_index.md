---
category: general
date: 2026-08-20
description: Erfahren Sie, wie Sie ein ActiveX‑Steuerelement erstellen, die Button‑Größe
  festlegen und einen Button zu Word hinzufügen – mit einem vollständigen C#‑Beispiel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: de
lastmod: 2026-08-20
og_description: Erstelle ein ActiveX-Steuerelement in einer Word-Datei mit C#. Dieses
  Tutorial zeigt, wie man die Button-Größe festlegt, den Button zu Word hinzufügt
  und einen anklickbaren Button erstellt.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Erstellen eines ActiveX‑Steuerelements in Word – Schritt‑für‑Schritt C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Wie man ein ActiveX‑Steuerelement in einem Word‑Dokument mit C# erstellt
url: /de/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein ActiveX‑Steuerelement in einem Word‑Dokument mit C# erstellt

Wenn Sie ein **ActiveX‑Steuerelement** in einer Microsoft‑Word‑Datei erstellen müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen, wie Sie **einen Button zu Word hinzufügen**, die Abmessungen des Buttons festlegen und das Steuerelement anklickbar machen – alles mit einem kurzen, eigenständigen C#‑Programm.

In diesem Tutorial lernen Sie:

* Warum ein ActiveX‑Steuerelement für interaktive Word‑Dokumente nützlich ist.  
* Den genauen Code, der **die Button‑Größe festlegt** und eine Beschriftung zuweist.  
* Wie man **einen anklickbaren Button erstellt**, den Sie später an ein Makro oder externe Logik binden können.  

Die Schritte funktionieren mit Aspose.Words .NET 23.12 oder höher und benötigen nur eine .NET‑Entwicklungsumgebung.

> **Voraussetzung** – Sie besitzen eine gültige Aspose.Words‑Lizenz (oder verwenden die Evaluierungs‑Version) und Visual Studio 2022 oder eine beliebige C#‑IDE.

---

## Wie man ein ActiveX‑Steuerelement in einem Word‑Dokument erstellt

Der erste Schritt besteht darin, ein leeres `Document` und einen `DocumentBuilder` zu instanziieren. Der Builder stellt die High‑Level‑API zum Einfügen von Objekten wie ActiveX‑Steuerelementen bereit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Die Methode `InsertActiveXButton` (nachfolgend definiert) enthält die Logik, **wie ein Button eingefügt** und konfiguriert wird.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Beim Ausführen des Programms wird **ActiveXButton.docx** erstellt. Öffnet man die Datei in Word, erscheint ein Button mit der Beschriftung **Submit**. Das Steuerelement ist voll funktionsfähig – ein Klick löst das Standard‑`CommandButton_Click`‑Ereignis aus, das Sie später an ein VBA‑Makro binden können.

### Warum das funktioniert

* `InsertForms2OleControl` weist Word an, ein OLE‑Objekt vom Typ **CommandButton** einzubetten, die klassische ActiveX‑Button‑Klasse.  
* Die Parameter für Breite und Höhe **setzen die Button‑Größe** direkt; Word wandelt die Werte von Punkten (1 pt ≈ 1/72 in) um.  
* Das Benennen des Steuerelements (`Name = "btnSubmit"`) erleichtert das Auffinden aus VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Button‑Größe und Beschriftung festlegen

Wenn Sie ein anderes Aussehen benötigen, passen Sie die numerischen Argumente im Aufruf von `InsertForms2OleControl` an. Die Methodensignatur lautet:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Der programmatische Bezeichner der ActiveX‑Klasse (`"CommandButton"` für einen Standard‑Button).  
* **width / height** – Größe in Punkten. Für einen 2 cm breiten Button verwenden Sie `width = 56.7` (2 cm ≈ 56.7 pt).  

Sie können die Beschriftung auch nach dem Einfügen ändern:

```csharp
commandButton.Caption = "Send Request";
```

Das Ändern der Beschriftung beeinflusst nicht die Größe, aber es ändert das visuelle Feedback für den Benutzer.

### Profi‑Tipp

Wenn Sie einen quadratischen Button möchten, setzen Sie beide Dimensionen auf denselben Wert:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Button zu Word hinzufügen und anklickbar machen

Der obige Code **fügt bereits einen Button zu Word hinzu**. Damit der Button eine Aktion ausführt, müssen Sie ein VBA‑Makro schreiben, das das `Click`‑Ereignis verarbeitet. Hier ein minimales Makro, das Sie in den Word‑VBA‑Editor einfügen können (`Alt+F11` → Einfügen → Modul):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Da das Steuerelement `btnSubmit` heißt, mappt Word das `Click`‑Ereignis automatisch auf `btnSubmit_Click`. Das ist der Standardweg, um **einen anklickbaren Button** zu erstellen, ohne externe Bibliotheken zu verwenden.

> **Hinweis:** Die Makrosicherheits‑Einstellungen in Word können ActiveX‑Steuerelemente blockieren. Stellen Sie sicher, dass „Alle Makros aktivieren“ oder „VBA‑Makros aktivieren“ für das Dokument ausgewählt ist, oder signieren Sie das Makro digital für den Produktionseinsatz.

---

## Häufige Fragen: Button einfügen und Fehlersuche

### 1. Was tun, wenn der Button nach dem Speichern nicht erscheint?

* Prüfen Sie, ob Ihre Aspose.Words‑Version `InsertForms2OleControl` unterstützt. Versionen vor 22.5 besitzen diese Funktion nicht.  
* Stellen Sie sicher, dass das Zielformat `.docx` oder `.doc` ist. Ältere Formate wie `.rtf` können keine ActiveX‑Objekte speichern.

### 2. Kann ich den Button an einer bestimmten Lesezeichen‑Position einfügen?

Ja. Bewegen Sie den Builder zum Lesezeichen, bevor Sie `InsertForms2OleControl` aufrufen:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Wie **setze ich die Button‑Größe** dynamisch basierend auf der Textlänge?

Berechnen Sie die erforderliche Breite mit der Methode `Graphics.MeasureString` (aus `System.Drawing`) und wandeln Sie Pixel in Punkte um (`points = pixels * 72 / DPI`). Übergeben Sie dann die berechnete Breite an `InsertForms2OleControl`.

### 4. Gibt es eine Möglichkeit, mehrere Buttons in einer Schleife hinzuzufügen?

Natürlich. Verpacken Sie die Einfügelogik in eine `for`‑Schleife und passen Sie die Eigenschaften `Left` und `Top` für jede Iteration an:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Erwartete Ausgabe

Wenn Sie das Programm ausführen und **ActiveXButton.docx** öffnen:

* Ein einzelner **Submit**‑Button erscheint oben‑links auf der ersten Seite.  
* Die Button‑Größe entspricht den von Ihnen angegebenen Abmessungen (`100 pt × 30 pt`).  
* Wenn Sie das VBA‑Makro hinzugefügt haben, zeigt ein Klick auf den Button eine Meldungsbox: „You clicked the Submit button!“.

Sie haben nun erfolgreich **ein ActiveX‑Steuerelement erstellt**, **die Button‑Größe festgelegt** und **einen Button zu Word hinzugefügt**, wobei Sie auch gelernt haben, **wie man einen Button einfügt** und **einen anklickbaren Button** für zukünftige Automatisierungsaufgaben zu erstellen.

---

## Fazit

In diesem Tutorial haben Sie gelernt, wie man mit C# **ein ActiveX‑Steuerelement** in ein Word‑Dokument einfügt. Durch Befolgen der Schritte können Sie **die Button‑Größe festlegen**, dem Steuerelement einen sinnvollen Namen geben und **einen Button zu Word hinzufügen**, sodass er zu einem **anklickbaren Button** wird, der an ein VBA‑Makro gebunden ist.  

Von hier aus können Sie:

* Das Binding des Buttons an ein .NET‑COM‑Add‑in statt an VBA untersuchen.  
* Andere ActiveX‑Klassen wie `CheckBox` oder `ComboBox` verwenden.  
* Die Erstellung vollständiger Formulare mit mehreren Steuerelementen automatisieren.

Viel Spaß beim Experimentieren mit verschiedenen Größen


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}