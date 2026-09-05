---
category: general
date: 2026-09-05
description: Erfahren Sie, wie Sie ein Gruppierungs‑Shape in einer DOCX-Datei erstellen,
  einen ActiveX‑Befehlsschalter einfügen und Markdown in ein Word‑Dokument laden –
  mit einem vollständigen C#‑Beispiel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: de
lastmod: 2026-09-05
og_description: Erstelle ein Gruppen‑Shape‑Docx, füge einen ActiveX‑Befehlsschalter
  ein und lade Markdown in ein Word‑Dokument mit C#. Folge dieser Schritt‑für‑Schritt‑Anleitung.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Gruppen‑Shape in docx erstellen und ActiveX‑Steuerelemente einbetten – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Wie man ein Gruppen‑Shape in docx erstellt und interaktive Steuerelemente in
  C# hinzufügt
url: /de/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man group shape docx erstellt und interaktive Steuerelemente in C# hinzufügt

Wenn Sie programmgesteuert **create group shape docx**-Dateien erstellen müssen, zeigt Ihnen dieser Leitfaden genau, wie das geht. Sie sehen außerdem, wie Sie **insert ActiveX command button**-Steuerelemente **einfügen** und **load Markdown into a Word document** können, ohne die Unterstreichungsformatierung zu verlieren. Am Ende des Tutorials haben Sie ein voll funktionsfähiges `.docx`, das Vektorgrafiken, interaktive UI-Elemente und markdown‑basierten Inhalt kombiniert.

Dieses Tutorial geht davon aus, dass Sie eine grundlegende C#-Entwicklungsumgebung und die Aspose.Words für .NET-Bibliothek installiert haben. Es werden keine externen Tools benötigt – alles läuft innerhalb einer Standard-.NET-Konsole oder Desktop-Anwendung.

## Voraussetzungen

- .NET 6.0 SDK oder neuer (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET (NuGet-Paket `Aspose.Words`)
- Ein gültiges X.509-Zertifikat (`.pfx`), wenn Sie den Signierungsschritt testen möchten
- Eine Bilddatei (z. B. `logo.png`) und eine Markdown-Datei (`sample.md`) in einem bekannten Ordner abgelegt

> **Pro Tipp:** Bewahren Sie alle Eingabedateien in einem einzigen *resources*-Ordner auf, um relative Pfade zu vereinfachen.

## Schritt 1: Projekt einrichten und Namespaces importieren

Erstellen Sie ein neues Konsolenprojekt und fügen Sie die erforderlichen `using`-Direktiven hinzu. Dieser Block demonstriert auch, wie Sie die Aspose.Words-Klassen referenzieren, die Sie später verwenden werden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Die `using`-Anweisungen geben Ihnen direkten Zugriff auf `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` und andere Typen, die im gesamten Tutorial verwendet werden.

## Schritt 2: **Create group shape docx** – fügt eine gruppierte Form mit Kind-Elementen hinzu

Eine *group shape* ermöglicht es, mehrere Zeichenobjekte als eine Einheit zu behandeln. Das ist nützlich, um verwandte Grafiken gemeinsam zu verschieben oder zu skalieren.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Warum eine group shape?**  
Durch Gruppierung bleiben Rechteck und Ellipse ausgerichtet, wenn der Benutzer sie in Word verschiebt. Sie vereinfacht außerdem spätere Vorgänge wie das Anwenden eines gemeinsamen Rahmens oder das programmgesteuerte Verschieben der gesamten Grafik.

## Schritt 3: Einfügen eines Plain‑Text‑Content‑Controls (Platzhalter für Benutzereingaben)

Content‑Controls bieten Endbenutzern einen strukturierten Bereich zum Eingeben von Text. Der Platzhaltertext verschwindet, sobald der Benutzer mit der Eingabe beginnt.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Die Eigenschaft `PlaceholderName` ist das, was Word als hellgrauen Hinweis anzeigt. Benutzer können sie durch eigenen Text ersetzen, und das zugrunde liegende XML bleibt wohlgeformt.

## Schritt 4: **Insert ActiveX command button** – interaktive UI zum Dokument hinzufügen

ActiveX‑Steuerelemente werden in modernen Word‑Dateien weiterhin unterstützt und können Makros oder externe Automatisierungen auslösen. Im Folgenden fügen wir einen *command button* hinzu und setzen dessen Beschriftung.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Wann sollte man einen ActiveX‑Button verwenden?**  
Wenn Sie das Dokument in einer Unternehmensumgebung verteilen, die auf VBA‑Makros angewiesen ist, kann ein ActiveX‑Button ein Makro starten oder eine externe Anwendung aufrufen. Für rein HTML‑basierte Interaktivität sollten Sie stattdessen *Content‑Controls* mit *Office.js* verwenden.

## Schritt 5: Einfügen eines versteckten Bildes (z. B. ein Logo) für Branding oder späteren Skriptzugriff

Versteckte Formen werden im gedruckten Dokument nicht angezeigt, bleiben jedoch im XML erhalten, sodass Sie sie später programmgesteuert abrufen können.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Schritt 6: **Load markdown into a Word document** und Unterstreichungsformatierung beibehalten

Aspose.Words kann Markdown direkt importieren. Durch Aktivieren von `ImportUnderlineFormatting` wird sichergestellt, dass Markdown‑Unterstreichungen (`<u>` oder `__text__`) zu Word‑Unterstreichungsformaten werden und nicht als Klartext erscheinen.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Sonderfall:** Wenn die Markdown‑Datei Tabellen enthält, werden diese automatisch in Word‑Tabellen konvertiert. Wenn Sie benutzerdefinierte Tabellenstile benötigen, wenden Sie nach dem Einfügen einen `DocumentBuilder` an.

## Schritt 7: Dokument mit XAdES‑EPES signieren (optionaler Sicherheitsschritt)

Digitale Signaturen gewährleisten die Dokumentenintegrität. Der folgende Code signiert die **create group shape docx**‑Datei mit einem XAdES‑EPES‑Profil.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Sicherheitshinweis:** Halten Sie das Zertifikatspasswort außerhalb der Quellcodeverwaltung. Verwenden Sie Umgebungsvariablen oder einen sicheren Tresor in der Produktion.

## Vollständiges ausführbares Beispiel

Wenn Sie alle Schritte zusammenfügen, erhalten Sie ein einzelnes, eigenständiges Programm. Speichern Sie die Datei als `Program.cs` und führen Sie sie über die Befehlszeile aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Das Ausführen des Programms erzeugt `CompleteGroupShape.docx` mit folgendem Inhalt:

- Ein gruppiertes Rechteck + Ellipse (der Kern von **create group shape docx**)
- Ein Plain‑Text‑Content‑Control mit Platzhaltertext
- Ein **insert ActiveX command button** mit der Beschriftung „Click Me“
- Ein verstecktes Logo‑Bild
- Markdown‑Inhalt mit erhaltenen Unterstreichungen
- Eine XAdES‑EPES‑Digitalsignatur (falls ein Zertifikat bereitgestellt wurde)

## Häufige Fragen und Fehlerbehebung

| Frage | Antwort |
|---|---|
| **Funktioniert der ActiveX‑Button in Word für macOS?** | Word für macOS unterstützt keine ActiveX‑Steuerelemente. Der Button wird als statisches Bild angezeigt. Verwenden Sie Content‑Controls mit Office.js für plattformübergreifende Interaktivität. |
| **Was ist, wenn die Markdown‑Datei benutzerdefiniertes CSS enthält?** | Aspose.Words ignoriert CSS; es wird nur die standardmäßige Markdown‑Syntax verarbeitet. Konvertieren Sie CSS‑gestylte Elemente nach dem Import manuell in Word‑Stile. |
| **Kann ich später weitere Formen zur gleichen Gruppe hinzufügen?** | Ja. Rufen Sie die `GroupShape` über ihren Namen oder Index ab und rufen Sie dann `AppendChild(newShape)` auf. Denken Sie daran, das Dokument nach Änderungen erneut zu speichern. |
| **Wie ändere ich den Signaturalgorithmus?** | Setzen Sie `signature.SignatureAlgorithm` bevor Sie `Sign` aufrufen. Der Standard ist SHA‑256, der die meisten Compliance‑Anforderungen erfüllt. |
| **Ist das versteckte Bild in der Word‑Benutzeroberfläche sichtbar?** | Nein, aber es kann angezeigt werden, indem Sie *Show hidden text* in den Word‑Optionen aktivieren. Das ist nützlich, um Metadaten zu speichern, ohne das Layout zu überladen. |

## Nächste Schritte

Jetzt, da Sie **create group shape docx**, **insert ActiveX command button** und **load markdown into a Word document** durchführen können, könnten Sie folgendes erkunden:

- **Einbetten von VBA‑Makros**, die auf den Klick des ActiveX‑Buttons reagieren.
- **Anwenden benutzerdefinierter Stile** auf die durch Markdown erzeugten Absätze.
- **Erzeugen von PDFs** aus demselben Dokument mittels `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automatisieren der Stapelverarbeitung** mehrerer Markdown‑Dateien zu einem einzigen zusammengefassten Bericht.

Diese Erweiterungen ermöglichen den Aufbau vollständig automatisierter Dokument‑Pipelines, die reichhaltige Grafiken, interaktive Steuerelemente und markdown‑basiertes Authoring kombinieren – alles aus C#.

---

*Viel Spaß beim Programmieren! Wenn Ihnen dieses Tutorial*

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Erstelle Group Shape in Word-Dokument mit Aspose.Words für .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Erstelle Rechteckform in Word mit C# – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Erstelle Markdown aus Word – Vollständiger C#‑Leitfaden](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}