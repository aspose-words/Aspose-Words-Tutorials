---
category: general
date: 2026-09-21
description: Erfahren Sie, wie Sie eine ActiveX‑Schaltfläche in einem Word‑Dokument
  mit Aspose.Words und C# erstellen. Die Schritt‑für‑Schritt‑Anleitung behandelt das
  Einfügen, Positionieren und Speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie eine ActiveX-Schaltfläche in einem Word-Dokument mit
  C# und Aspose.Words. Folgen Sie diesem vollständigen Tutorial, um die Schaltfläche
  programmgesteuert einzufügen, zu positionieren und zu speichern.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Erstellen Sie eine ActiveX‑Schaltfläche in Word mit C# – vollständige Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Wie man in Word eine ActiveX‑Befehlsschaltfläche mit C# erstellt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man einen ActiveX‑Befehlsschaltfläche in Word mit C# erstellt

Wenn Sie **eine ActiveX‑Befehlsschaltfläche** in einer Word‑Datei erstellen müssen, zeigt Ihnen diese Anleitung die genauen Schritte. Mit Aspose.Words für .NET können Sie die Schaltfläche vollständig aus C#‑Code hinzufügen, positionieren und konfigurieren.

Das programmgesteuerte Einfügen einer ActiveX‑Schaltfläche eliminiert manuelle UI‑Arbeit und ermöglicht die automatisierte Dokumentenerstellung für Formulare, Berichte oder interaktive Vorlagen. In diesem Tutorial lernen Sie, wie Sie **DocumentBuilder**, die **InsertForms2OleControl**‑Methode und zugehörige Eigenschaften verwenden, um eine voll funktionsfähige Schaltfläche zu erzeugen.

## Was Sie benötigen

* .NET 6.0 SDK oder neuer (der Code funktioniert auch mit .NET Framework 4.7+)
* Aspose.Words für .NET (NuGet-Paket `Aspose.Words`)
* Eine IDE wie Visual Studio 2022 oder VS Code
* Grundkenntnisse in C# und Word‑Dokumentkonzepten

Keine zusätzliche Office-Installation ist erforderlich, da Aspose.Words unabhängig von Microsoft Word funktioniert.

## Schritt 1: Das C#‑Projekt einrichten

Erstellen Sie ein neues Konsolenprojekt und fügen Sie das Aspose.Words‑Paket hinzu.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Die Bibliothek `Aspose.Words` stellt die **DocumentBuilder**‑Klasse bereit, die wir zur Manipulation des Dokuments verwenden werden.

## Schritt 2: Dokument und Builder initialisieren

Der erste Codeblock erstellt ein leeres Dokument und eine `DocumentBuilder`‑Instanz. Dieses Objekt ist der Einstiegspunkt für alle Word‑Verarbeitungsoperationen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:** `DocumentBuilder` behält die aktuelle Cursorposition bei, sodass jede nachfolgende Einfügung genau dort erscheint, wo Sie den Cursor platzieren.

## Schritt 3: Die ActiveX‑Befehlsschaltfläche einfügen

Die **InsertForms2OleControl**‑Methode erstellt ein ActiveX‑Steuerelement des gewünschten Typs. Hier fordern wir ein `CommandButton` an und geben seine Größe in Punkten an (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Erklärung:**  
* `OleControlType.CommandButton` weist Aspose.Words an, einen Button statt eines anderen Steuerelementtyps zu erstellen.  
* Die Methode gibt ein `Forms2OleControl`‑Objekt zurück, das Positionierungs‑ und Eigenschaftsfelder bereitstellt.

## Schritt 4: Die Schaltfläche positionieren und ihre Eigenschaften festlegen

Nach dem Einfügen können Sie die Schaltfläche an jede Position auf der Seite verschieben und ihr einen programmatischen Namen sowie eine sichtbare Beschriftung geben.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Profi‑Tipp:** Das Koordinatensystem beginnt in der oberen linken Ecke der Seite. Passen Sie `Left` und `Top` an, um die Schaltfläche mit anderen Formularfeldern auszurichten.

## Schritt 5: Das Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Die Datei enthält die ActiveX‑Schaltfläche und kann in Microsoft Word geöffnet werden, wo die Schaltfläche interaktiv wird.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Wenn Sie `ActiveXCommandButton.docx` in Word öffnen, sehen Sie eine Schaltfläche mit der Beschriftung **Submit** an der angegebenen Position. Ein Klick darauf in Word löst das Standard‑Button‑Verhalten aus (das Sie später mit VBA oder Word‑Add‑Ins anpassen können).

## Vollständiges, ausführbares Beispiel

Wenn Sie alle Teile zusammenfügen, erhalten Sie ein eigenständiges Programm, das Sie kopieren, einfügen und ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Erwartete Ausgabe:** Die Konsole gibt *„Document created successfully.“* aus und der Ordner enthält nun `ActiveXCommandButton.docx`. Das Öffnen der Datei in Microsoft Word zeigt eine anklickbare **Submit**‑Schaltfläche, die 100 pt vom linken Rand und 150 pt vom oberen Rand der Seite positioniert ist.

## Häufige Fallstricke und wie man sie vermeidet

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Die Schaltfläche erscheint außerhalb der Seite | `Left`/`Top`‑Werte überschreiten die Seitenabmessungen | Verwenden Sie `doc.FirstSection.PageSetup.PageWidth` und `PageHeight`, um sichere Koordinaten zu berechnen |
| Schaltfläche ist in Word nicht sichtbar | Das Dokument wurde in einem Format gespeichert, das ActiveX‑Steuerelemente entfernt (z. B. `.txt`) | Immer als `.docx` oder `.doc` speichern |
| Laufzeitfehler `ArgumentOutOfRangeException` | Breite oder Höhe ist null oder negativ | Stellen Sie sicher, dass die an `InsertForms2OleControl` übergebenen Größenangaben positive Zahlen sind |

## Erweiterung der Lösung

Sie können die Schaltfläche weiter anpassen, indem Sie zusätzliche Eigenschaften wie `Enabled`, `Visible` setzen oder ein Makro über VBA anhängen. Die Klasse **Forms2OleControl** ermöglicht zudem das Einfügen anderer ActiveX‑Steuerelemente wie Kontrollkästchen (`OleControlType.CheckBox`) oder Kombinationsfelder (`OleControlType.ComboBox`).

Wenn Sie mehrere Schaltflächen in einer Schleife erzeugen müssen, kapseln Sie die Einfügelogik in einer Hilfsmethode ein:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Fazit

Sie wissen jetzt, wie Sie mit C# und Aspose.Words eine **ActiveX‑Befehlsschaltfläche** in einem Word‑Dokument erstellen. Das Tutorial behandelte das Einrichten des Projekts, das Einfügen der Schaltfläche mit `InsertForms2OleControl`, das Positionieren und das Speichern der finalen Datei. Mit dieser Grundlage können Sie komplexe Formulare automatisieren, interaktive Steuerelemente einbetten und Word‑Dokumente in größere .NET‑Lösungen integrieren.

Als Nächstes erkunden Sie verwandte Themen wie **Aspose.Words ActiveX**‑Formularfelder, **C# DocumentBuilder**‑Erweiterte Formatierung oder das programmgesteuerte Hinzufügen von **ActiveX‑Steuerelementen in Word** für Kontrollkästchen und Dropdown‑Listen. Experimentieren Sie mit verschiedenen Koordinaten und Größen, um Ihre spezifischen Layoutanforderungen zu erfüllen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Ein Word-Dokument mit Tabelle mit Aspose.Words erstellen](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}