---
category: general
date: 2026-09-14
description: Erstelle ein ActiveX-Steuerelement in einem Word-Dokument mit C#. Erfahre,
  wie man ActiveX einfügt, einen interaktiven Button hinzufügt und die .docx-Datei
  programmgesteuert erzeugt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: de
lastmod: 2026-09-14
og_description: Erstellen Sie ein ActiveX-Steuerelement in einem Word‑Dokument mit
  C#. Folgen Sie diesem vollständigen Beispiel, um ActiveX einzufügen, einen interaktiven
  Button hinzuzufügen und die Datei zu speichern.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: ActiveX‑Steuerelement in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Wie man ein ActiveX‑Steuerelement in einem Word‑Dokument mit C# erstellt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein ActiveX‑Steuerelement in einem Word‑Dokument mit C# erstellt

Wenn Sie ein **ActiveX‑Steuerelement** in einer Microsoft Word‑Datei erstellen müssen, zeigt Ihnen dieser Leitfaden eine vollständige, sofort einsatzbereite Lösung. Sie sehen genau, wie Sie einen ActiveX‑CommandButton einfügen, dessen Eigenschaften festlegen und die resultierende `.docx`‑Datei nur mit C#‑Code speichern.

Das Hinzufügen eines interaktiven Buttons zu einem Word‑Dokument ist ein häufiges Bedürfnis, wenn Endbenutzer Makros oder benutzerdefinierte Logik direkt über die Benutzeroberfläche des Dokuments auslösen sollen. Das nachstehende Beispiel demonstriert **wie man ActiveX einfügt** ohne Drittanbieter‑Tools zu verwenden und behandelt außerdem **wie man ein Word‑Dokument** programmgesteuert erstellt.

Am Ende dieses Tutorials können Sie **einen Button mit Code erstellen**, dessen Beschriftung anpassen und eine portable Word‑Datei erzeugen, die das ActiveX‑Steuerelement beibehält.

## Voraussetzungen

- .NET 6.0 oder höher (die Aspose.Words‑für‑.NET‑Bibliothek funktioniert mit .NET Core und .NET Framework)
- Ein Verweis auf das NuGet‑Paket `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Grundkenntnisse in C# und objektorientierter Programmierung

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt (oder integrieren Sie den Code in eine bestehende C#‑Anwendung). Importieren Sie die erforderlichen Namespaces, damit der Compiler die Word‑Verarbeitungs‑Klassen finden kann.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Warum dieser Schritt wichtig ist** – Die `Aspose.Words`‑API stellt die Klassen `Document`, `DocumentBuilder` und `Forms2OleControl` bereit, mit denen Sie Word‑Dateien auf Objektebene manipulieren können. Ohne diese Verweise würde der restliche Code nicht kompilieren.

## Schritt 2: Ein neues Word‑Dokument und einen DocumentBuilder erstellen

Das Objekt `Document` repräsentiert das gesamte `.docx`‑Paket, während `DocumentBuilder` eine fluente API zum Einfügen von Inhalten bereitstellt.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Erklärung** – Das Erzeugen eines neuen `Document` liefert Ihnen eine leere Leinwand. Der Cursor des Builders befindet sich am Anfang des ersten Abschnitts und ist bereit für die nächste Einfügung.

## Schritt 3: Das ActiveX‑CommandButton einfügen

Verwenden Sie `InsertForms2OleControl`, um ein ActiveX‑Steuerelement an einer bestimmten Position zu platzieren. Die Methode benötigt den Steuertyp und ein `RectangleF`, das die X/Y‑Koordinaten sowie die Größe (in Punkten) definiert.

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Warum das funktioniert** – `OleControlType.CommandButton` weist die API an, ein Standard‑Windows‑CommandButton zu erstellen. Das Rechteck positioniert den Button relativ zur oberen linken Ecke der Seite, sodass Sie **einen interaktiven Button** genau dort hinzufügen können, wo Sie ihn benötigen.

## Schritt 4: Eigenschaften des Buttons konfigurieren

Legen Sie nun den sichtbaren Text des Buttons (`Caption`) und dessen internen Namen (`Name`) fest. Diese Eigenschaften sehen die Benutzer und kann später VBA‑Code darauf verweisen.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Praktischer Hinweis** – Der `Name` muss innerhalb des Dokuments eindeutig sein; andernfalls könnten VBA‑Makros auf das falsche Steuerelement verweisen.

## Schritt 5: Dokument speichern

Schließlich schreiben Sie die Datei auf die Festplatte. Das ActiveX‑Steuerelement wird im Word‑Paket gespeichert, sodass die gespeicherte Datei beim Öffnen in Microsoft Word ihre volle Funktionalität beibehält.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Ergebnis** – Beim Öffnen von `CommandButton.docx` in Word wird ein anklickbarer CommandButton mit der Beschriftung „Click Me“ angezeigt. Das Steuerelement kann über die Word‑Benutzeroberfläche (`Entwicklertools → Entwurfsmodus → Eigenschaften`) mit einem Makro verknüpft werden.

## Vollständige Quellcode‑Auflistung

Wenn Sie alle Schritte zusammenführen, erhalten Sie ein einzelnes, eigenständiges Programm, das Sie kopieren, einfügen und ausführen können.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms gibt eine Bestätigungszeile aus:

```
Document saved to C:\Temp\CommandButton.docx
```

Wenn Sie die erzeugte Datei in Microsoft Word öffnen, sehen Sie einen **CommandButton** an den angegebenen Koordinaten. Das Klicken des Buttons im Entwurfsmodus hebt ihn hervor; im Ausführungsmodus verhält er sich wie jeder andere Standard‑ActiveX‑Button.

## Häufige Variationen und Sonderfälle

| Szenario | Anpassung |
|----------|------------|
| **Anderer Steuertyp** | Ersetzen Sie `OleControlType.CommandButton` durch `OleControlType.CheckBox`, `OleControlType.OptionButton` usw. |
| **Mehrere Buttons** | Rufen Sie `InsertForms2OleControl` wiederholt auf und aktualisieren Sie die `RectangleF`‑Koordinaten für jeden neuen Button. |
| **Dynamische Größenanpassung** | Berechnen Sie die Rechteckabmessungen basierend auf der Seitengröße (`builder.PageSetup.PageWidth`). |
| **Speichern in einen Stream** | Verwenden Sie `document.Save(stream, SaveFormat.Docx)`, wenn Sie die Datei über eine Web‑API zurückgeben müssen. |
| **Word‑97‑2003‑Format** | Ändern Sie das Speicherformat zu `SaveFormat.Doc`, um eine `.doc`‑Datei zu erzeugen, die das ActiveX‑Steuerelement weiterhin einbettet. |

> **Pro‑Tipp:** Testen Sie das erzeugte Dokument stets in der Zielversion von Word, da ältere Versionen standardmäßig Sicherheitseinstellungen durchsetzen können, die ActiveX‑Steuerelemente deaktivieren.

## Häufig gestellte Fragen

**Funktioniert das mit .NET Core?**  
Ja. Die Aspose.Words‑Bibliothek ist plattformübergreifend und vollständig kompatibel mit .NET Core sowie .NET 5/6+.

**Kann ich einem Button programmgesteuert ein Makro zuweisen?**  
Die API bettet keinen VBA‑Code direkt ein. Nachdem das Dokument erzeugt wurde, öffnen Sie es in Word, aktivieren Sie die Registerkarte Entwicklertools und nehmen Sie ein Makro auf oder schreiben Sie ein Makro, das `btnClick` referenziert.

**Was ist, wenn der Button nicht angezeigt wird?**  
Stellen Sie sicher, dass die Registerkarte `Developer` in Word aktiviert ist und das Dokument nicht im **geschützten Modus** geöffnet wird. Überprüfen Sie außerdem, dass die Rechteckkoordinaten innerhalb der Seitenränder liegen.

## Fazit

Sie wissen jetzt, wie Sie mit C# ein **ActiveX‑Steuerelement** in einer Word‑Datei erstellen. Das Tutorial behandelte **wie man ActiveX einfügt**, zeigte **wie man einen interaktiven Button hinzufügt**, demonstrierte **wie man ein Word‑Dokument** von Grund auf erstellt und veranschaulichte **wie man einen Button mit Code erstellt**, der nach dem Speichern erhalten bleibt.  

Ab hier können Sie weitere ActiveX‑Typen erkunden, den Button mit VBA‑Makros verbinden oder die Logik in einen größeren Dokument‑Generierungs‑Service einbetten. Experimentieren Sie mit verschiedenen Größen, Positionen und Steuereigenschaften, um das gewünschte Benutzererlebnis zu erzielen.

---

## Was Sie als Nächstes lernen sollten?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Neues Word‑Dokument erstellen](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [VBA‑Projekt in Word‑Dokument erstellen](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Word‑Dokument in Aspose.Words für .NET erstellen und formatieren](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}