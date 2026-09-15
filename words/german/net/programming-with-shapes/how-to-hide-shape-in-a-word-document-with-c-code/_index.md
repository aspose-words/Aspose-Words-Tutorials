---
category: general
date: 2026-09-14
description: Erfahren Sie, wie Sie Formen in Word mit C# ausblenden – einschließlich
  Code zum Erstellen eines Word‑Dokuments, Einfügen einer Rechteckform in Word und
  programmgesteuertes Ausblenden von Formen in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: de
lastmod: 2026-09-14
og_description: Wie man eine Form in Word mit C# ausblendet – Schritt‑für‑Schritt‑Anleitung,
  die auch zeigt, wie man Word‑Dokumentcode erstellt und ein Rechteck in Word einfügt.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Wie man eine Form in einem Word-Dokument mit C#‑Code ausblendet
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man eine Form in einem Word‑Dokument mit C#‑Code ausblendet
url: /de/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man eine Form in einem Word-Dokument mit C#-Code ausblendet

Wenn Sie **how to hide shape** in einer Word-Datei benötigen, zeigt dieses Tutorial die vollständige Lösung. Sie sehen, wie man ein Word-Dokument erstellt, eine Rechteckform einfügt, eine Ellipse hinzufügt und diese Ellipse ausblendet, sodass beim Öffnen der Datei nur das Rechteck angezeigt wird.

Der Leitfaden deckt alles ab, was Sie benötigen – keine externen Referenzen, nur der Code und die Erklärungen. Am Ende können Sie versteckte Grafiken in jedes Word-Dokument einbetten, das Sie programmgesteuert erzeugen.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET (kostenlose Testversion oder lizenzierte Version)  
  Installieren Sie es über NuGet: `dotnet add package Aspose.Words`
- Grundlegende Kenntnisse in C# und Visual Studio oder einer beliebigen IDE Ihrer Wahl

## Schritt 1: Projekt einrichten und Namespaces importieren

Starten Sie eine neue Konsolenanwendung und fügen Sie die erforderlichen `using`‑Anweisungen hinzu. Diese Importe geben Ihnen Zugriff auf die Klassen `Document`, `DocumentBuilder` und Drawing, die zum Manipulieren von Formen benötigt werden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Warum das wichtig ist** – Das Importieren der richtigen Namespaces verhindert Kompilierungsfehler und stellt die API‑Oberfläche für die Erstellung von Formen und die Steuerung der Sichtbarkeit bereit.

## Schritt 2: Ein neues Word-Dokument und einen Builder erstellen

Ein `Document` repräsentiert die Datei, während ein `DocumentBuilder` eine fluente API zum Hinzufügen von Inhalten bereitstellt. Dies ist der erste Ort, an dem Sie die **how to hide shape**‑Logik anwenden: Sie benötigen einen Dokumentkontext, bevor irgendeine Form existieren kann.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Erklärung** – Das `Document`‑Objekt beginnt leer. Der `DocumentBuilder` ist am Anfang des ersten Absatzes positioniert und bereit, Formen oder Text einzufügen.

## Schritt 3: Sichtbare Rechteckform einfügen

Das Rechteck wird die Form sein, die beim Öffnen des Dokuments sichtbar bleibt. Sie können Größe, Position und Formatierung direkt über das Form‑Objekt steuern.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Warum dieser Schritt** – Das Hinzufügen eines Rechtecks demonstriert die Anforderung **insert rectangle shape word**. Das Setzen von `FillColor` und `LineColor` macht die Form im finalen Dokument leicht erkennbar.

## Schritt 4: Ellipsenform einfügen und ausblenden

Jetzt fügen Sie die Form hinzu, die Sie verbergen möchten. Die Eigenschaft `Hidden` weist Word an, die Form nicht in der Benutzeroberfläche darzustellen, obwohl sie Teil der Dokumentstruktur bleibt.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Erklärung** – Das Setzen von `Hidden = true` ist das Kernstück von **hide shape in word**. Word respektiert dieses Flag beim normalen Anzeigen und Drucken, aber die Form kann bei Bedarf weiterhin programmgesteuert abgerufen werden.

## Schritt 5: Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Wählen Sie einen Ordner, auf den Sie Schreibzugriff haben, und geben Sie der Datei einen klaren Namen, der den Zweck des Tutorials widerspiegelt.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Ergebnis** – Beim Öffnen von `ShapeVisibility.docx` in Microsoft Word wird nur das hellblaue Rechteck angezeigt. Die versteckte Ellipse erscheint nicht, was bestätigt, dass Sie **how to hide shape** in einer Word-Datei erfolgreich gemeistert haben.

## Vollständiges funktionierendes Beispiel

Wenn Sie alle Snippets zusammenfügen, erhalten Sie ein einzelnes, ausführbares Programm:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Erwartete Ausgabe

- **Visuell**: Wenn Sie `ShapeVisibility.docx` öffnen, sehen Sie ein hellblaues Rechteck, das nahe dem linken Rand positioniert ist. Keine Ellipse ist sichtbar.
- **Programmgesteuert**: Die versteckte Ellipse bleibt im XML des Dokuments (`<w:drawing>`‑Element) mit dem gesetzten `w:hidden`‑Attribut, was Sie überprüfen können, indem Sie die Datei als ZIP öffnen und `document.xml` inspizieren.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| *Kann ich mehrere Formen ausblenden?* | Ja. Setzen Sie `Hidden = true` für jede Form, die Sie verbergen möchten. |
| *Werden ausgeblendete Formen gedruckt?* | Standardmäßig druckt Word ausgeblendete Objekte nicht. Wenn Sie sie drucken müssen, entfernen Sie das `Hidden`‑Flag vor dem Drucken. |
| *Wird die versteckte Eigenschaft in älteren Word-Versionen unterstützt?* | Das `Hidden`‑Attribut ist Teil des Office Open XML‑Standards und funktioniert in Word 2007 und später. |
| *Was, wenn ich die Sichtbarkeit zur Laufzeit umschalten muss?* | Rufen Sie die Form über `document.GetChildNodes(NodeType.Shape, true)` ab und ändern Sie die `Hidden`‑Eigenschaft basierend auf Ihrer Logik. |

## Pro‑Tipps

- **Performance**: Wenn Sie viele Dokumente erzeugen, verwenden Sie eine einzelne `DocumentBuilder`‑Instanz wieder, anstatt für jede Datei eine neue zu erstellen.
- **Versionskontrolle**: Speichern Sie die erzeugten `.docx`‑Dateien in einem versionierten Ordner; ausgeblendete Formen können als Metadaten‑Marker für nachgelagerte Verarbeitung dienen.
- **Testing**: Automatisieren Sie einen schnellen visuellen Test, indem Sie das DOCX mit Aspose.Words (`document.Save("out.pdf")`) in PDF konvertieren. Das PDF blendet die Ellipse ebenfalls aus, was bestätigt, dass das Hidden‑Flag bei Formatkonvertierungen weitergegeben wird.

## Fazit

Sie wissen jetzt, wie man **how to hide shape** in einem Word-Dokument mit C# ausblendet. Das Tutorial führte Sie durch das Erstellen eines Dokuments, **insert rectangle shape word**, das Hinzufügen einer Ellipse und das Anwenden des `Hidden`‑Flags, um das Verhalten **hide shape in word** zu erreichen. Mit dem vollständigen, ausführbaren Code können Sie versteckte Grafiken in jede automatisierte Berichts‑ oder Vorlagen‑Workflow integrieren.

### Nächste Schritte

- Untersuchen Sie weitere Formeigenschaften wie Drehung, Schatten und Textumbruch.  
- Kombinieren Sie ausgeblendete Formen mit benutzerdefinierten Dokumenteigenschaften, um maschinenlesbare Daten einzubetten.  
- Schauen Sie sich Muster für **create word document code** für Tabellen, Diagramme und Inhaltssteuerelemente an, um Ihr Automatisierungs‑Toolkit zu erweitern.

Fühlen Sie sich frei, mit verschiedenen Formtypen und Sichtbarkeitseinstellungen zu experimentieren – Ihr nächstes Word‑Automatisierungsprojekt ist nur ein paar Codezeilen entfernt!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Leeres Word-Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Schatten zu Word‑Form in C# hinzufügen](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}