---
category: general
date: 2026-09-30
description: Fügen Sie ein ActiveX-Steuerelement zu einem Word-Dokument mit C# hinzu.
  Erfahren Sie, wie Sie eine ActiveX-Schaltfläche einfügen, einen Befehlsbutton hinzufügen
  und ihn anklickbar machen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: de
lastmod: 2026-09-30
og_description: Fügen Sie ein ActiveX-Steuerelement zu einem Word-Dokument mit C#
  hinzu. Folgen Sie dieser umfassenden Anleitung, um einen ActiveX-Button einzufügen,
  einen Befehlsbutton hinzuzufügen und ihn anklickbar zu machen.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Ein ActiveX‑Steuerelement zu Word‑Dokumenten hinzufügen – Schritt‑für‑Schritt
  C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Wie man ein ActiveX‑Steuerelement in Word mit C# hinzufügt
url: /de/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein ActiveX‑Steuerwort in Word mit C# hinzufügt

Wenn Sie ein **ActiveX-Steuerwort** in eine Microsoft Word‑Datei einbetten müssen, zeigt Ihnen dieser Leitfaden genau, wie das geht. Sie sehen ein komplettes, ausführbares Beispiel, das einen anklickbaren Button einfügt, das Dokument speichert und mit der neuesten Aspose.Words for .NET funktioniert.

Das Hinzufügen eines ActiveX-Steuerworts ermöglicht es Ihnen, interaktive Formulare, benutzerdefinierte Dialoge oder einfache UI‑Elemente zu erstellen, die sich wie native Word‑Steuerelemente verhalten. Egal, ob Sie eine Vertragvorlage erstellen, die Benutzerinteraktion erfordert, oder einen Bericht, der einen „Ausführen“-Button benötigt, die nachstehenden Schritte decken alles ab, was Sie benötigen.

## Voraussetzungen

* .NET 6.0 SDK oder neuer (der Code funktioniert auch mit .NET Framework 4.8)
* Visual Studio 2022 (oder jede IDE, die C# unterstützt)
* Aspose.Words for .NET installiert (`dotnet add package Aspose.Words`)
* Grundlegendes Verständnis von C# und der Word‑Dokumentstruktur

> **Profi‑Tipp:** Die Methode `InsertForms2OleControl` funktioniert nur mit den Legacy‑„Forms 2.0“-Steuerelementen, die die ActiveX‑Steuerelemente sind, die Word für Formularfelder verwendet. Wenn Sie neuere Office‑Versionen anvisieren, wird das Steuerelement dennoch korrekt im Desktop‑Client dargestellt.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt und fügen Sie die erforderlichen `using`‑Anweisungen hinzu. Dadurch kann der Compiler die Klassen `Document`, `DocumentBuilder` und `OleControlType` finden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Der Namespace `Aspose.Words` stellt High‑Level‑APIs für die Word‑Verarbeitung bereit, während `Aspose.Words.Drawing` die Aufzählung `OleControlType` enthält, die zum Festlegen des Typs eines ActiveX‑Steuerelements benötigt wird.

## Schritt 2: Quell‑Word‑Dokument laden

Sie müssen mit einer Word‑Datei beginnen, die Sie ändern möchten. Der folgende Code lädt `input.docx` aus einem von Ihnen angegebenen Ordner.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Falls die Datei nicht existiert, wirft Aspose.Words eine `FileNotFoundException`. Um eine elegante Fehlerbehandlung zu ermöglichen, können Sie den Aufruf in einen `try/catch`‑Block einbetten.

## Schritt 3: DocumentBuilder zum Bearbeiten des Dokuments erstellen

`DocumentBuilder` ist das Arbeitspferd zum Einfügen von Text, Bildern und Steuerelementen. Er hält einen Cursor, der auf die Position zeigt, an der das nächste Element eingefügt wird.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Standardmäßig ist der Cursor des Builders am Anfang des ersten Abschnitts positioniert. Sie können ihn mit Methoden wie `MoveToDocumentEnd()` oder `MoveToParagraph(index)` verschieben, falls Sie den Button an einer anderen Stelle platzieren möchten.

## Schritt 4: ActiveX‑CommandButton‑Steuerelement einfügen

Jetzt kommt der Kern des Tutorials: Ein **ActiveX-Steuerwort** einfügen, das als anklickbarer Button erscheint. Die Methode `InsertForms2OleControl` nimmt zwei Argumente entgegen – den Steuertyp und eine Beschriftung (oder Name) für das Steuerelement.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Warum `OleControlType.CommandButton` verwenden?**  
  Es weist Word an, einen klassischen Forms 2.0‑CommandButton zu erstellen, der eine Beschriftung anzeigt und später an ein Makro oder VBA‑Skript gebunden werden kann.

* **Was bewirkt die Beschriftung?**  
  Der String `"ClickMe"` wird zum sichtbaren Text des Buttons. Sie können ihn in beliebigen Text ändern, der zu Ihrer UI passt.

### Einfügen des Buttons an einer bestimmten Position

Falls Sie den Button nach einem bestimmten Absatz benötigen, verschieben Sie zuerst den Builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Schritt 5: Modifiziertes Dokument speichern

Nach dem Einfügen des Steuerelements speichern Sie die Änderungen in einer neuen Datei (oder überschreiben die Originaldatei).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie `output.docx` in der Desktop‑Version von Word öffnen, sehen Sie den Button mit der Beschriftung **ClickMe** (oder **Submit**, je nach verwendeter Beschriftung). Das Klicken des Buttons im Entwurfsmodus bewirkt standardmäßig nichts; Sie können später über die Registerkarte „Entwicklertools“ ein Makro zuweisen.

## Vollständiges, ausführbares Beispiel

Unten finden Sie ein eigenständiges Programm, das den gesamten Arbeitsablauf demonstriert. Kopieren Sie es in `Program.cs` einer neuen Konsolen‑App und führen Sie es aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Erwartete Ausgabe

* Die Konsole gibt die Erfolgsmeldung mit dem Ausgabepfad aus.
* Beim Öffnen von `output.docx` wird ein **ClickMe**‑Button an der Stelle angezeigt, an der der Builder ihn eingefügt hat.
* Der Button kann ausgewählt, in der Größe geändert oder über Word’s **Entwicklertools → Entwurfsmodus** ein Makro zugewiesen werden.

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| **Wie fügt man einen ActiveX‑Button in die Kopf‑/Fußzeile ein?** | Verschieben Sie den Builder mit `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` in die Kopf‑/Fußzeile, bevor Sie `InsertForms2OleControl` aufrufen. |
| **Was, wenn ich ein Kontrollkästchen anstelle eines Buttons benötige?** | Verwenden Sie `OleControlType.CheckBox` und geben Sie eine Beschriftung wie `"Agree"` an. |
| **Funktioniert der Button in Word Online?** | Nein. Word Online unterstützt keine Legacy‑Forms 2.0‑ActiveX‑Steuerelemente. Der Button wird nur im Desktop‑Client dargestellt. |
| **Kann ich die Größe des Buttons programmgesteuert festlegen?** | Nach dem Einfügen holen Sie das `Shape`‑Objekt über `builder.CurrentParagraph.Runs[0].GetShape()` und passen `Width`/`Height` an. |
| **Gibt es eine Möglichkeit, ein Makro per Code zuzuweisen?** | Aspose.Words bietet keine Makro‑Bearbeitung an. Sie müssen das Dokument in Word öffnen und ein Makro manuell zuweisen oder die Office‑Interop‑API verwenden. |

## Tipps für den Produktionseinsatz

* **Vermeiden Sie hartkodierte Pfade** – verwenden Sie `Path.Combine` und Konfigurationsdateien.
* **Entsorgen Sie `Document`** – wickeln Sie es in eine `using`‑Anweisung, wenn Sie mit großen Dateien arbeiten, um den Speicher zeitnah freizugeben.
* **Validieren Sie die Ausgabe** – prüfen Sie programmgesteuert, dass das Dokument eine Form vom Typ `OleControl` enthält, indem Sie `doc.GetChildNodes(NodeType.Shape, true)` iterieren.
* **Sicherheitshinweis** – ActiveX‑Steuerelemente können Code auf dem Client‑Rechner ausführen. Verteilen Sie Dokumente nur an vertrauenswürdige Benutzer und erwägen Sie digitale Signaturen.

## Fazit

Sie wissen jetzt, wie Sie ein **ActiveX-Steuerwort** zu einem Word‑Dokument mit C# hinzufügen. Durch das Laden eines Dokuments, das Erstellen eines `DocumentBuilder`, das Einfügen eines CommandButtons mit `InsertForms2OleControl` und das Speichern der Datei können Sie die Erstellung interaktiver Word‑Formulare automatisieren. Experimentieren Sie mit anderen `OleControlType`‑Werten, platzieren Sie Steuerelemente in Kopf‑ oder Tabellen und kombinieren Sie sie mit Makros für ein reichhaltigeres Benutzererlebnis.

---

*Nächste Schritte*: Erkunden Sie **wie man ActiveX**‑Steuerelemente anderer Typen einfügt, lernen Sie **wie man Ereignishandler für CommandButton** via VBA hinzuzufügen und lesen Sie über **Best Practices zum Einfügen von ActiveX‑Buttons** für plattformübergreifende Kompatibilität.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Einbetten von OLE‑Objekten und ActiveX‑Steuerelementen in Word‑Dokumenten](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Hinzufügen eines Kombinationsfeld‑Formularfelds zu einem Word‑Dokument mit Aspose.Words für .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Hinzufügen eines Kontrollkästchen‑Formularfelds zu einem Word‑Dokument mit Aspose.Words für .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}