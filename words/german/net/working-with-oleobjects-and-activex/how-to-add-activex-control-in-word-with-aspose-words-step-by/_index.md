---
category: general
date: 2026-08-07
description: Lernen Sie, wie Sie ein ActiveX-Steuerelement in ein Word‑Dokument mit
  C# einfügen. Enthält das Zuordnen eines Makros zu einer Schaltfläche und das Hinzufügen
  anklickbarer Schaltflächen in Word‑Beispielen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: de
lastmod: 2026-08-07
og_description: Wie man ein ActiveX-Steuerelement in ein Word-Dokument mit Aspose.Words
  einfügt. Folgen Sie dieser Anleitung, um einen Button einzufügen, ein Makro mit
  dem Button zu verknüpfen und ein anklickbares Schaltflächenwort hinzuzufügen.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Wie man ein ActiveX‑Steuerelement in Word hinzufügt – vollständiges C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man ein ActiveX‑Steuerelement in Word mit Aspose.Words hinzufügt – Schritt‑für‑Schritt‑Anleitung
url: /de/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein ActiveX-Steuerelement in Word mit Aspose.Words hinzufügt

Wenn Sie **ein ActiveX-Steuerelement hinzufügen** in einer Microsoft Word-Datei programmgesteuert benötigen, zeigt Ihnen dieses Tutorial die genauen Schritte mit Aspose.Words für .NET. Sie sehen, wie man einen CommandButton einfügt, seine Beschriftung festlegt und **ein Makro mit dem Button verknüpfen** , sodass das Steuerelement reagiert, wenn ein Benutzer darauf klickt. Am Ende haben Sie eine makro‑aktivierte `.docm`‑Datei, die einen voll funktionsfähigen Button enthält.

Das Hinzufügen eines ActiveX‑Buttons ist eine häufige Anforderung beim Erstellen interaktiver Vorlagen wie Kreditanträgen, Onboarding-Formularen für Mitarbeiter oder automatisierten Berichten. Dieser Leitfaden führt jede Codezeile durch, erklärt **warum** jeder Schritt wichtig ist und behandelt die typischen Fallstricke, denen Sie begegnen könnten.

## Voraussetzungen

* .NET 6 (oder .NET Core 3.1 / .NET Framework 4.8) installiert.
* Eine gültige Aspose.Words für .NET Lizenz oder ein temporärer Evaluierungsschlüssel.
* Visual Studio 2022 (oder jede IDE, die C# unterstützt).
* Grundlegende Kenntnisse von Word-Makros (VBA), falls Sie das Makro schreiben möchten, das der Button auslöst.

> **Pro tip:** Wenn Sie das Beispiel ausführen, speichern Sie die Ausgabe in einen Ordner, für den Sie Schreibrechte haben, sonst wirft `doc.Save` eine Ausnahme.

## Wie man ein ActiveX-Steuerelement in einem Word-Dokument mit Aspose.Words hinzufügt

Der Kern der Lösung ist ein kurzes C#‑Programm, das ein neues Dokument erstellt, ein ActiveX **CommandButton**‑Steuerelement einfügt und die Datei als makro‑aktiviertes Dokument (`.docm`) speichert. Der Code ist vollständig und bereit zum Kopieren‑Einfügen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Warum jede Zeile wichtig ist

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Instanziiert ein frisches Word‑Paket im Speicher. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Stellt eine fluente API zum Einfügen von Inhalten bereit, einschließlich ActiveX‑Steuerelementen. |
| `InsertForms2OleControl` | Die einzige Aspose.Words‑Methode, die ein ActiveX‑Steuerelement erstellt; Sie geben den Steuertyp (`CommandButton`) und seine Geometrie an. |
| `commandButton.Caption = "Click Me";` | Setzt das **beschriftung des anklickbaren Buttons**, das der Endbenutzer sieht. Ohne Beschriftung erscheint der Button leer. |
| `commandButton.OnAction = "MyMacro";` | **ein Makro mit dem Button verknüpfen** – teilt Word mit, welches VBA‑Makro ausgeführt werden soll, wenn das Steuerelement angeklickt wird. |
| `doc.Save("CommandButton.docm");` | Speichert das Dokument als makro‑aktivierte Datei; ein reguläres `.docx` würde das Steuerelement und das Makro entfernen. |

> **Note:** Die Koordinaten (links, oben) werden in Punkten gemessen (1 pt ≈ 1/72 in). Passen Sie sie an, um den Button an die gewünschte Stelle auf der Seite zu positionieren.

## Wie man ein Makro mit einem Button verknüpft

Die `OnAction`‑Eigenschaft verknüpft den Button mit einem VBA‑Makro namens `MyMacro`. Sie müssen dieses Makro noch innerhalb der Word‑Datei erstellen, entweder manuell oder durch programmatisches Einfügen von VBA‑Code (Aspose.Words schreibt keinen VBA‑Code). Hier ist ein minimales Makro, das Sie über den **Entwickler → Visual Basic**‑Editor von Word hinzufügen können:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Wenn der Benutzer `CommandButton.docm` öffnet und den Button anklickt, führt Word `MyMacro` aus und zeigt ein Meldungsfeld an. Wenn die Makrosicherheit auf **Alle Makros ohne Benachrichtigung deaktivieren** eingestellt ist, erscheint der Button deaktiviert. Empfehlen Sie den Benutzern, Makros für das Dokument zu aktivieren oder das Makro mit einem vertrauenswürdigen Zertifikat zu signieren.

### Häufige Fallstricke beim Verknüpfen eines Makros

* **Makrosicherheitseinstellungen** – Wenn das Dokument auf einem Rechner mit strengen Sicherheitsrichtlinien geöffnet wird, kann das Makro blockiert werden. Geben Sie Anweisungen, um das Sicherheitsniveau zu senken oder das Makro zu signieren.
* **Namenskonflikte** – Der Makroname muss innerhalb des VBA‑Projekts des Dokuments eindeutig sein; andernfalls gibt Word einen Fehler „duplicate procedure name“ aus.
* **64‑Bit vs 32‑Bit Word** – ActiveX‑Steuerelemente funktionieren gleich, aber der VBA‑Editor kann je nach Office‑Version unterschiedliche Warnmeldungen anzeigen.

## Wie man ein anklickbares Button‑Wort zu einem Word-Formular hinzufügt

Die `Caption`‑Eigenschaft ist das, was Benutzer auf dem Button sehen. Sie können sie weiter anpassen:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Wenn Sie die Beschriftung dynamisch basierend auf Benutzereingaben ändern müssen, können Sie später über das Objektmodell von Word auf das Steuerelement zugreifen:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Sonderfall: Lange Beschriftungen

Word kürzt Beschriftungen, die die Breite des Buttons überschreiten. Um Abschneiden zu vermeiden, erhöhen Sie entweder das Breitenargument in `InsertForms2OleControl` oder verkürzen Sie den Text. Tests mit verschiedenen Sprachen (z. B. Deutsch oder Japanisch) sind empfehlenswert, da die Zeichenbreite variiert.

## Wie man ein CommandButton‑Wort für die Formularautomatisierung hinzufügt

Beyond the visual caption, the **add command button word** concept covers the programmatic name of the control. Aspose.Words stellt keine direkte `Name`‑Eigenschaft für ActiveX‑Steuerelemente bereit, aber Sie können das Feld `AltText` setzen, das Word als Kennung des Steuerelements verwendet:

```csharp
commandButton.AltText = "SubmitButton";
```

Später können Sie in VBA den Button über seinen `AltText`‑Wert referenzieren:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Diese Technik ist nützlich, wenn Sie mehrere Buttons haben und sie programmatisch unterscheiden müssen.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie als Konsolenanwendung kompilieren und ausführen können. Es enthält optionale Formatierungen, Makro‑Verknüpfungen und einen Kommentarblock, der jeden Schritt beschreibt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Erwartetes Ergebnis:** Beim Öffnen von `SubmitForm.docm` in Microsoft Word wird ein blau umrandeter Button mit der Aufschrift *Submit Form* angezeigt. Ein Klick auf den Button löst das VBA‑Makro `SubmitMacro` aus (vorausgesetzt, Sie haben das Makro dem Dokument hinzugefügt). Der Button kann verschoben, in der Größe geändert oder weiter formatiert werden, indem das gleiche `Forms2OleControl`‑Objekt verwendet wird.

## Testen der Lösung

1. Kompilieren und führen Sie die C#‑Konsolenanwendung aus.
2. Öffnen Sie das erzeugte `SubmitForm.docm` in Word.
3. Falls aufgefordert, aktivieren Sie Makros.
4. Klicken Sie den *Submit Form*‑Button – Sie sollten das in `SubmitMacro` definierte Meldungsfeld sehen.

Wenn der Button erscheint, aber nichts tut, prüfen Sie doppelt, dass der Makroname exakt (`SubmitMacro`) übereinstimmt und dass die Makrosicherheit die Ausführung nicht blockiert.

## Häufig gestellte Fragen

| Frage | Antwort |
|-------|--------|
| *Kann ich mehr als einen ActiveX‑Button hinzufügen?* | Ja. Rufen Sie `InsertForms2OleControl` mehrmals mit unterschiedlichen Koordinaten auf. Verwenden Sie unterschiedliche `OnAction`‑ und `AltText`‑Werte, um sie zu unterscheiden. |
| *Ist das ActiveX‑Steuerelement in Word Online sichtbar?* | Nein. |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Inhalt mit Document Builder in Aspose.Words für .NET hinzufügen](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Schatten zu Word‑Form hinzufügen in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Neuen Abschnitt zu Word‑Dokument hinzufügen | Aspose.Words für .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}