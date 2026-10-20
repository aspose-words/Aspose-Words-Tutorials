---
category: general
date: 2026-10-20
description: Erfahren Sie, wie Sie ein leeres Word‑Dokument erstellen, Formen in Word
  gruppieren, die Füllfarbe von Formen festlegen und den Umbruchtyp Inline verwenden
  – mit einem vollständigen C#‑Beispiel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: de
lastmod: 2026-10-20
og_description: Erstellen Sie ein leeres Word‑Dokument, gruppieren Sie Formen in Word
  und setzen Sie die Füllfarbe der Form mit dem Umbruchtyp Inline mithilfe von Aspose.Words
  und C#. Folgen Sie dem vollständigen Tutorial.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Erstelle ein leeres Word‑Dokument und gruppiere Formen in Word – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und Formen in Word mit Aspose.Words
  gruppiert
url: /de/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument erstellt und Formen in Word gruppiert

Wenn Sie ein **leeres Word-Dokument** erstellen müssen, das mehrere Formen enthält, die als eine Einheit agieren, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen, wie man **Formen in Word gruppiert**, die Füllfarbe einer Form festlegt und **wrap type inline** anwendet – alles mit einem knappen, ausführbaren C#‑Programm.

Das Tutorial führt Sie Zeile für Zeile durch den Code, erklärt, warum jeder Schritt wichtig ist, und weist auf häufige Fallstricke hin. Am Ende haben Sie eine .docx‑Datei, die ein Rechteck und ein Textfeld gruppiert anzeigt, bereit für weitere Automatisierung.

## Was Sie lernen werden

* Wie man eine leere Word‑Datei mit Aspose.Words initialisiert.
* Der korrekte Weg, ein **GroupShape** zu erstellen und Kind‑Formen hinzuzufügen.
* Techniken zum **set shape fill color** und zur Positionssteuerung.
* Verwendung von **wrap type inline**, sodass die Gruppe wie ein einzelnes Inline‑Objekt wirkt.
* Wie man das Ergebnis speichert und überprüft.

Vorkenntnisse mit Aspose.Words sind nicht erforderlich, aber Sie sollten mit grundlegender C#‑Syntax vertraut sein und Visual Studio (oder eine andere IDE) installiert haben.

## Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6.0 oder höher | Stellt die Laufzeit für das C#‑Projekt bereit. |
| Aspose.Words for .NET (neueste Version) | Stellt die im Beispiel verwendeten Klassen `Document`, `DocumentBuilder` und Shape bereit. |
| Ein beschreibbarer Ordnerpfad | Der Aufruf `doc.Save` benötigt ein gültiges Verzeichnis, um die Ausgabedatei zu schreiben. |
| Grundkenntnisse in C# | Ermöglicht Ihnen, dem Code zu folgen und ihn für eigene Szenarien anzupassen. |

Installieren Sie Aspose.Words über NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Schritt 1: Erstellen eines leeren Word-Dokuments

Der erste Vorgang besteht darin, ein **leeres Word-Dokument** zu **erstellen**. Die `Document`‑Klasse von Aspose.Words repräsentiert eine Word‑Datei im Speicher, und `DocumentBuilder` bietet eine bequeme API zum Bearbeiten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist*: Der Start mit einem leeren Dokument garantiert, dass die von Ihnen hinzugefügte Gruppierungsform die einzige Inhaltseinheit ist, was die Überprüfung vereinfacht.

## Schritt 2: Definieren einer GroupShape mit wrap type inline

Ein **GroupShape** fungiert als Container für andere Formen. Das Setzen von `WrapType` auf `Inline` sorgt dafür, dass die Gruppe wie ein einzelnes Inline‑Objekt im Absatzfluss agiert.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Warum das wichtig ist*: Die Verwendung von **wrap type inline** verhindert, dass die Gruppe vom umgebenden Text weggeschwemmt wird – entscheidend, wenn die Gruppe als Einheit bewegt werden soll.

## Schritt 3: Ein Rechteck hinzufügen und shape fill color setzen

Ein Rechteck ist ein häufiges visuelles Element. Der `Shape`‑Konstruktor nimmt einen `ShapeType`; anschließend geben wir Größe und Füllfarbe an.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Warum das wichtig ist*: Die Eigenschaft `FillColor` demonstriert **set shape fill color** in der Praxis und verleiht dem Rechteck einen hellblauen Hintergrund, der im fertigen Dokument hervorsticht.

## Schritt 4: Ein Textfeld hinzufügen – wie man Formen effektiv gruppiert

Ein Textfeld liefert editierbaren Text innerhalb der Gruppe. Positionieren Sie es relativ zum Koordinatensystem der Gruppe, indem Sie die `Top`‑Eigenschaft anpassen.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Warum das wichtig ist*: Dieser Schritt beantwortet **how to group shapes** – indem jedes Kind‑Shape derselben `GroupShape`‑Instanz hinzugefügt wird. Der `Top`‑Versatz sorgt dafür, dass das Textfeld unter dem Rechteck erscheint und demonstriert präzise Layout‑Kontrolle.

## Schritt 5: Die fertige GroupShape in das Dokument einfügen

Jetzt, wo die Gruppe beide Kind‑Formen enthält, fügen Sie sie an der aktuellen Builder‑Position ein.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Warum das wichtig ist*: Das Einfügen der Gruppe als einzelner Knoten stellt sicher, dass Word das Rechteck und das Textfeld als ein logisches Objekt behandelt und ihre relativen Positionen beim Bearbeiten beibehält.

## Schritt 6: Das Dokument speichern und das Ergebnis überprüfen

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Ersetzen Sie `YOUR_DIRECTORY` durch einen echten Pfad auf Ihrem Rechner.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Wenn Sie `GroupShape.docx` in Microsoft Word öffnen, sollten Sie ein hellblaues Rechteck mit einem Textfeld sehen, das mit „Grouped text“ beschriftet ist und direkt darunter positioniert ist. Das Auswählen einer der Formen wählt die gesamte Gruppe aus, was bestätigt, dass **group shapes in Word** wie gewünscht funktioniert.

### Erwartetes Ergebnis

* Eine .docx‑Datei mit einem einzigen Absatz.
* Im Absatz ein Inline‑Group, das wie ein einzelnes Composite‑Objekt aussieht.
* Das Rechteck ist hellblau gefüllt, und das Textfeld zeigt „Grouped text“.

![Screenshot des erzeugten Word-Dokuments](grouped_shapes.png){.center width=600 alt="Screenshot eines leeren Word-Dokuments mit gruppiertem Rechteck und Textfeld, erstellt mit Aspose.Words"}

## Häufige Fragen und Edge‑Case‑Behandlung

### Was tun, wenn die Gruppe schweben statt inline sein soll?

Ersetzen Sie `WrapType.Inline` durch `WrapType.TopBottom` (oder einen anderen `WrapType`‑Enum‑Wert). Schwebende Gruppen können unabhängig vom Absatzfluss positioniert werden, verlieren jedoch die automatische Inline‑Ausrichtung.

### Kann ich weitere Formen hinzufügen, z. B. Kreise oder Bilder?

Ja. Erstellen Sie zusätzliche `Shape`‑Objekte mit `ShapeType.Ellipse` oder `ShapeType.Image`, konfigurieren Sie deren Eigenschaften und rufen Sie `group.AppendChild(newShape)` auf. Die Gruppe erweitert automatisch ihre Grenzen, wenn Sie `group.Bounds` entsprechend aktualisieren.

### Wie ändere ich die Gesamtabmessungen der Gruppe nach dem Hinzufügen von Kindern?

Passen Sie `group.Bounds` an, nachdem alle Kinder hinzugefügt wurden, oder berechnen Sie programmgesteuert die Vereinigung der Kind‑Bounds. So stimmt der Trefferbereich der Gruppe mit dem visuellen Inhalt überein.

### Was passiert, wenn der Ausgabepfad nicht existiert?

Aspose.Words wirft eine `DirectoryNotFoundException`. Erstellen Sie das Verzeichnis zuerst:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Funktioniert das mit .NET Framework statt .NET Core?

Alle verwendeten APIs (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) sind in der .NET‑Framework‑Version von Aspose.Words verfügbar, sodass derselbe Code unverändert funktioniert.

## Pro‑Tipps

* **Performance‑Tipp** – Verwenden Sie eine einzelne `DocumentBuilder`‑Instanz, wenn Sie viele Gruppen einfügen; das Erzeugen eines neuen Builders pro Gruppe verursacht zusätzlichen Aufwand.
* **Visuelle Konsistenz** – Setzen Sie `rectangle.StrokeColor` auf denselben Wert wie `FillColor` für ein nahtloses Aussehen, oder setzen Sie `rectangle.LineWidth = 0`, um den Rand zu verbergen.
* **Debugging** – Rufen Sie `doc.UpdatePageLayout()` vor dem Speichern auf, wenn Sie viele Formen ändern; das zwingt Word, das Layout neu zu berechnen und kann unerwartetes Abschneiden verhindern.

## Fazit

Sie wissen jetzt, wie man ein **leeres Word‑Dokument erstellt**, **Formen in Word gruppiert**, **shape fill color setzt** und **wrap type inline** mit Aspose.Words für .NET anwendet. Das vollständige Beispiel demonstriert den Standardansatz zum Erstellen zusammengesetzter Grafiken, die sich in Word wie ein einzelnes Objekt verhalten.

Ab hier können Sie:

* Weitere Formen wie Bilder oder Diagramme hinzufügen.
* Mit verschiedenen `WrapType`‑Werten für schwebende Gruppen experimentieren.
* Die stapelweise Erstellung gruppierter Diagramme über mehrere Dokumente automatisieren.

Passen Sie den Code gern an Ihre eigenen Automatisierungsszenarien an und teilen Sie Ihre Ergebnisse in den Kommentaren!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeres Word-Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Wie man PDF aus Word mit Inline‑Formen speichert – Komplett‑Anleitung](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}