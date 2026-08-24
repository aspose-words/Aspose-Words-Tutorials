---
category: general
date: 2026-08-23
description: Erstelle einen Submit‑Button in C#‑Word‑Automatisierung. Lerne, wie man
  einen ActiveX‑Button hinzufügt und den Button‑Namen, die Beschriftung sowie den
  Text programmgesteuert festlegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: de
lastmod: 2026-08-23
og_description: Erstellen Sie einen Submit-Button in C# Word‑Automatisierung. Dieser
  Leitfaden zeigt, wie man einen ActiveX‑Button hinzufügt und dessen Name, Beschriftung
  und Text mit Aspose.Words festlegt.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Erstelle Absenden‑Schaltfläche in C#‑Word‑Automatisierung
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Wie man einen Submit‑Button in C#‑Word‑Automatisierung erstellt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So erstellen Sie eine Submit-Schaltfläche in C# Word‑Automatisierung

Wenn Sie eine **Submit-Schaltfläche** in einem Word‑Dokument mit C# erstellen müssen, führt Sie diese Anleitung durch den gesamten Prozess. Sie sehen, wie Sie eine ActiveX‑Schaltfläche hinzufügen, einen programmatischen Namen zuweisen und die Beschriftung der Schaltfläche festlegen, sodass sie wie ein reguläres *Submit*-Steuerelement aussieht.

Die Automatisierung von Formularsteuerelementen in Word kann manuelle Layout‑Arbeit ersetzen und Konsistenz über Hunderte von Dokumenten hinweg sicherstellen. In den nachfolgenden Schritten lernen Sie außerdem, wie Sie **set button text**, **set button name** und **set button caption** festlegen – alles wichtig, wenn die Schaltfläche an einem makro‑gesteuerten Workflow teilnimmt.

## Voraussetzungen

* .NET 6.0 (oder höher) installiert.
* Ein Verweis auf **Aspose.Words for .NET** (die Bibliothek, die `DocumentBuilder.InsertForms2OleControl` bereitstellt).
* Grundlegende Kenntnisse in C# und den ActiveX‑Formularsteuerelementen von Word.

You can install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

> **Profi‑Tipp:** Verwenden Sie die neueste stabile Version von Aspose.Words, um von Fehlerbehebungen und neuen Funktionen im Zusammenhang mit ActiveX‑Steuerelementen zu profitieren.

## Überblick über die Lösung

Das Tutorial ist in drei klare Schritte gegliedert:

1. **Add ActiveX button** – Verwenden Sie die Methode `InsertForms2OleControl`, um eine CommandButton in das Dokument einzufügen.  
2. **Set button name** – Weisen Sie mit der Eigenschaft `Name` einen eindeutigen programmatischen Bezeichner zu.  
3. **Set button caption** – Definieren Sie den sichtbaren Text der Schaltfläche über die Eigenschaft `Caption` (die ebenfalls das **set button text** in der Benutzeroberfläche steuert).

Am Ende des Leitfadens verfügen Sie über eine voll funktionsfähige **create submit button**‑Routine, die Sie in jedem Word‑Automatisierungsprojekt wiederverwenden können.

## Schritt 1: Eine ActiveX-Schaltfläche zum Dokument hinzufügen

Die erste Aufgabe besteht darin, **add activex button** zum Word‑Dokument hinzuzufügen. Aspose.Words stellt dafür das Enum `Forms2OleControlType.CommandButton` bereit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Warum dieser Schritt wichtig ist:**  
ActiveX‑Steuerelemente sind die einzigen Word‑Formular-Elemente, die VBA‑Makros ausführen oder mit externem Code interagieren können. Das Hinzufügen des Steuerelements erzeugt einen Platzhalter, den nachfolgende Schritte konfigurieren können.

> **Sonderfall:** Wenn das Dokument bereits ein Steuerelement mit demselben Namen enthält, benennt Word das neue automatisch um (z. B. `CommandButton1`). Durch das explizite Festlegen des Namens im nächsten Schritt werden solche Kollisionen vermieden.

## Schritt 2: Den Schaltflächennamen festlegen

Ein zuverlässiges **set button name** ist entscheidend, wenn Sie das Steuerelement aus VBA oder aus anderen Teilen Ihres C#‑Codes referenzieren müssen. Die Eigenschaft `Name` gibt der Schaltfläche einen programmatischen Bezeichner.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Warum Sie einen Namen festlegen sollten:**  
Wenn das Dokument geöffnet wird, kann VBA die Schaltfläche über `ActiveDocument.InlineShapes("btnSubmit")` abrufen. Ein aussagekräftiger Name wie `btnSubmit` verdeutlicht zudem die Absicht, wenn Sie das XML des Dokuments untersuchen.

> **Profi‑Tipp:** Halten Sie Namen kurz, alphanumerisch und beginnen Sie mit einem Buchstaben, um mit den VBA‑Namensregeln kompatibel zu bleiben.

## Schritt 3: Die Schaltflächenbeschriftung festlegen (sichtbarer Text)

Der Text, den Benutzer auf der Schaltfläche sehen, wird durch die Eigenschaft **set button caption** gesteuert. In der Word‑Benutzeroberfläche erscheint er als Beschriftung der Schaltfläche, was ebenfalls das **set button text** ist, das Sie anzeigen möchten.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Warum die Beschriftung wichtig ist:**  
Die Beschriftung ist die benutzerseitige Bezeichnung. Eine spätere Änderung beeinflusst nicht den Namen der Schaltfläche, sodass Sie die Benutzeroberfläche lokalisieren können, ohne Code zu brechen, der von `btnSubmit` abhängt.

> **Häufige Frage:** *Kann ich sowohl Caption als auch Value setzen?*  
> Für einen `CommandButton` steuert `Caption` die Beschriftung, während `Value` nicht verwendet wird. Wenn Sie einen versteckten Wert benötigen, speichern Sie ihn stattdessen in einer benutzerdefinierten Dokumenteigenschaft.

## Vollständiges funktionierendes Beispiel

Die Kombination der drei Schritte ergibt eine komplette Routine, die Sie in jede Konsolen‑ oder Windows‑App einbinden können:

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
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms erzeugt `SubmitButton.docx`. Wenn Sie die Datei in Microsoft Word öffnen:

* Es erscheint eine **Submit**‑Schaltfläche an der angegebenen Position.
* Der Name der Schaltfläche ist `btnSubmit` (prüfen Sie über *Entwickler → Entwurfsmodus → Eigenschaften*).
* Ein Klick auf die Schaltfläche im Entwurfsmodus zeigt die Beschriftung *Submit*.

Sie haben nun ein wiederverwendbares Baustein für jede formularbasierte Word‑Lösung.

## Weitere Überlegungen

### Umgang mit Namenskollisionen

Wenn Sie die Routine mehrmals auf demselben Dokument ausführen, kann Word doppelte Steuerelemente automatisch umbenennen. Um Eindeutigkeit zu gewährleisten, können Sie einen GUID voranstellen:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Lokalisierung der Schaltflächenbeschriftung

Für mehrsprachige Dokumente speichern Sie Beschriftungen in einer Ressourcendatei und weisen sie zur Laufzeit zu:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Reaktion auf den Klick der Schaltfläche

Die Schaltfläche selbst enthält keine Klick‑Logik in C#. In der Regel hängen Sie ein VBA‑Makro an:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Da Sie **set button name** auf `btnSubmit` gesetzt haben, folgt der Makroname automatisch der `<Name>_Click`‑Konvention.

## Fehlersuche – FAQ

| Frage | Antwort |
|----------|--------|
| **Warum erscheint die Schaltfläche leer?** | Stellen Sie sicher, dass Sie die Eigenschaft `Caption` setzen; ohne diese zeigt die Schaltfläche keinen Text. |
| **Kann ich ein anderes ActiveX‑Steuerelement verwenden?** | Ja. Ersetzen Sie `Forms2OleControlType.CommandButton` durch `CheckBox`, `OptionButton` usw., jedoch unterscheiden sich die Eigenschaften. |
| **Ist das mit .NET Core kompatibel?** | Aspose.Words for .NET unterstützt .NET 6+, sodass derselbe Code sowohl unter .NET Core als auch unter .NET Framework funktioniert. |
| **Was ist, wenn das Dokument bereits eine Schaltfläche enthält?** | Verwenden Sie einen eindeutigen `Name` (z. B. einen GUID anhängen), um Konflikte zu vermeiden. |

## Fazit

Sie wissen nun, wie Sie programmgesteuert eine **create submit button** in einem Word‑Dokument mit C# erstellen können. Indem Sie die drei Schritte – **add activex button**, **set button name** und **set button caption** – befolgen, können Sie zuverlässig **set button text**, **set button name** und **set button caption** für jede automatisierte Formularlösung festlegen.

Ab hier könnten Sie folgendes erkunden:

* Hinzufügen von VBA‑Makros, die auf den Klick der **submit button** reagieren.
* Gestaltung der Schaltfläche mit benutzerdefinierten Schriftarten oder Farben über das zugrunde liegende XML.
* Generieren mehrerer Schaltflächen in einer Schleife für dynamische Formulare.

Fühlen Sie sich frei, mit verschiedenen Beschriftungen, Namen und Positionen zu experimentieren, um Ihren spezifischen Workflow anzupassen. Viel Spaß beim Automatisieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Liniendiagramm in Word mit Aspose.Words für .NET erstellen](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Word‑Dokument mit Kopf‑ und Fußzeile mit Aspose.Words erstellen](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}