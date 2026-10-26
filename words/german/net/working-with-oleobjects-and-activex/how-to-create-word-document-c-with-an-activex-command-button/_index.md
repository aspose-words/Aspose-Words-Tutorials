---
category: general
date: 2026-10-26
description: Erfahren Sie, wie Sie ein Word‑Dokument in C# erstellen und programmgesteuert
  eine ActiveX‑Schaltfläche hinzufügen. Diese Schritt‑für‑Schritt‑Anleitung behandelt
  das Einfügen einer Befehls‑Schaltfläche, das Ausblenden zur Entwurfszeit und das
  Speichern der Datei.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: de
lastmod: 2026-10-26
og_description: Erstellen Sie ein Word‑Dokument in C# und fügen Sie programmgesteuert
  einen ActiveX‑Button hinzu. Folgen Sie diesem vollständigen Tutorial, um einen Befehls‑Button
  einzubetten, der nur zur Laufzeit angezeigt wird.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Ein Word‑Dokument in C# mit einer ActiveX‑Schaltfläche erstellen – vollständige
  Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Wie man ein Word‑Dokument in C# mit einer ActiveX‑Befehlsschaltfläche erstellt
url: /de/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word-Dokument in C# mit einem ActiveX‑Befehlsschalter erstellt

Wenn Sie ein **Word-Dokument in C#** erstellen müssen, das einen interaktiven Button enthält, zeigt Ihnen diese Anleitung genau, wie es geht. Am Ende der ersten beiden Sätze kennen Sie den Gesamtansatz, und die folgenden Schritte führen Sie durch jede Code‑Zeile, die Sie schreiben müssen.

Sie lernen, wie man einen ActiveX‑Button hinzufügt, ihn während des Designs ausblendet und ihn erst sichtbar macht, wenn der Benutzer die Datei öffnet. Das Tutorial behandelt außerdem häufige Fallstricke wie Sicherheitswarnungen und Versionskompatibilität, sodass Sie zuverlässige Dokumente bereitstellen können.

## Voraussetzungen

* .NET 6.0 oder höher installiert  
* Eine lizenzierte Kopie von **Aspose.Words for .NET** (die kostenlose Testversion eignet sich zum Experimentieren)  
* Grundlegende Kenntnisse in C# und Visual Studio (jede IDE, die .NET unterstützt, reicht)

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Schritt 1: Word-Dokument in C# erstellen und DocumentBuilder initialisieren

Der erste Schritt besteht darin, ein `Document`‑Objekt und einen `DocumentBuilder` zu instanziieren. Das `Document` repräsentiert die gesamte .docx‑Datei, während der `DocumentBuilder fluente Methoden zum Hinzufügen von Inhalten bereitstellt.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:** Ohne einen `DocumentBuilder` müssten Sie das OpenXML‑DOM manuell manipulieren, was fehleranfällig und schwerer zu lesen ist. Der Builder abstrahiert diese Details und garantiert eine wohlgeformte Word‑Datei.

## Schritt 2: Hinzufügen eines ActiveX‑Buttons – Einfügen eines CommandButton‑Steuerelements

Jetzt fügen wir ein **CommandButton ActiveX‑Steuerelement** an einer bestimmten Position ein. Das Rechteck definiert die Position des Buttons (X, Y) und die Größe (Breite, Höhe) in Punkten.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Warum das wichtig ist:** `InsertForms2OleControl` ist die einzige Aspose.Words‑Methode, die ein echtes ActiveX‑OLE‑Objekt erzeugt. Der Enum‑Wert `Forms2OleControlType.CommandButton` weist Word an, einen anklickbaren Button einzubetten statt eines generischen OLE‑Containers.

## Schritt 3: Programmgesteuertes Hinzufügen des CommandButton – Ausblenden bis zur Laufzeit

Word behandelt jede eingefügte Form standardmäßig als sichtbar. Um den Button während der Gestaltung der Vorlage unsichtbar zu halten, setzen Sie die `Hidden`‑Eigenschaft der Form, die der Builder gerade erstellt hat.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Warum das wichtig ist:** Durch das Setzen von `Hidden = true` wird verhindert, dass der Button die Design‑Ansicht überfüllt. Wenn das Dokument in Word geöffnet wird, zeigt die Laufzeitumgebung das Steuerelement automatisch an und bewahrt die beabsichtigte Benutzererfahrung.

## Schritt 4: Datei speichern – Word-Dokument mit CommandButton erstellen

Abschließend schreiben Sie das Dokument auf die Festplatte. Wählen Sie einen Pfad, in den Ihre Anwendung schreiben kann, und verwenden Sie die `.docx`‑Erweiterung, um moderne Kompatibilität sicherzustellen.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Warum das wichtig ist:** Das Speichern als `.docx` stellt sicher, dass das eingebettete ActiveX‑Steuerelement dem Office Open XML‑Standard entspricht, der von Word 2007 und neuer unterstützt wird. Wenn Sie Legacy‑`.doc`‑Unterstützung benötigen, ändern Sie die Erweiterung und verwenden Sie `SaveFormat.Doc`.

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenführen, finden Sie hier das komplette Programm, das Sie kopieren, einfügen und ausführen können:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Erwartete Ausgabe:** Nach dem Ausführen des Programms öffnen Sie `C:\Temp\ActiveX.docx` in Microsoft Word. Sie sehen ein leeres Dokument; der Button ist im Design‑Modus nicht sichtbar. Drücken Sie **Alt + F9**, um Feldfunktionen umzuschalten, und klicken Sie dann auf den Button‑Bereich – Word rendert das ActiveX‑Steuerelement, und Sie können damit interagieren (z. B. doppelklicken, um die Eigenschaften anzuzeigen).

## Randfälle und bewährte Vorgehensweisen

| Situation | Worauf zu achten ist | Empfohlene Lösung |
|-----------|----------------------|-------------------|
| **Benutzer deaktiviert ActiveX** | Word kann eine Sicherheitswarnung anzeigen oder das Steuerelement blockieren. | Weisen Sie Endbenutzer an, „ActiveX‑Steuerelemente“ im Trust Center zu aktivieren, oder bieten Sie eine makro‑signierte Alternative an. |
| **Dokument in Word Online geöffnet** | Word Online unterstützt kein ActiveX; der Button wird weggelassen. | Verwenden Sie einen Ersatz‑Hyperlink oder ein Inhaltssteuerelement, wenn Sie Cloud‑Kompatibilität benötigen. |
| **Unterschiedliche DPI‑Einstellungen** | Die Rechteckgröße kann auf hochauflösenden Displays größer oder kleiner erscheinen. | Verwenden Sie `GraphicsUnit.Point` (der Standard) und testen Sie gängige DPI‑Einstellungen (96 dpi, 120 dpi). |
| **Mehrere Buttons** | Der Aufruf `GetChildNodes(NodeType.Shape, true)[0]` gibt nur die erste Form zurück. | Durchlaufen Sie `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` und setzen Sie `Hidden` für jede hinzugefügte Form. |
| **Legacy‑.doc‑Format** | Einige ActiveX‑Eigenschaften gehen beim Speichern als `.doc` verloren. | Bevorzugen Sie `.docx`, es sei denn, Sie haben eine strenge Legacy‑Anforderung. |

**Pro‑Tipp:** Nach dem Einfügen des Buttons können Sie über die Word‑Benutzeroberfläche ein Makro seiner `OnAction`‑Eigenschaft zuweisen. Damit können Sie benutzerdefiniertes Klick‑Verhalten definieren, ohne zusätzlichen C#‑Code zu schreiben.

## Häufig gestellte Fragen

* **Funktioniert das mit .NET Core?**  
  Ja. Aspose.Words for .NET ist vollständig kompatibel mit .NET 5, .NET 6 und späteren Versionen. Verweisen Sie einfach auf dasselbe NuGet‑Paket.

* **Kann ich die Beschriftung des Buttons ändern, nachdem das Dokument erzeugt wurde?**  
  Die in `InsertForms2OleControl` festgelegte Beschriftung wird zum Standard‑Design‑Text. Benutzer können sie in Word bearbeiten, aber Sie können die Beschriftung auch programmgesteuert aktualisieren, indem Sie über die API `Shape.OleFormat` auf die Eigenschaften des OLE‑Objekts zugreifen.

* **Was ist, wenn ich eine andere Größe für den Button benötige?**  
  Passen Sie die Werte von `RectangleF` an. Die ersten beiden Parameter sind die X‑ und Y‑Koordinaten; die letzten beiden sind Breite und Höhe in Punkten (1 pt = 1/72 Zoll).

## Fazit

Sie wissen jetzt, wie man **Word-Dokumente in C# erstellt** und **programmgesteuert einen CommandButton hinzufügt** mit Aspose.Words. Das Tutorial behandelte das Initialisieren des Dokuments, das Einfügen eines ActiveX‑Buttons, das Ausblenden bis zur Laufzeit und das Speichern der finalen Datei. Mit diesen Bausteinen können Sie interaktive Steuerelemente in jede von Ihnen erzeugte Word‑Vorlage einbetten.

Als Nächstes erkunden Sie verwandte Themen wie **wie man ActiveX‑Button‑Ereignisse behandelt**, **CommandButton‑Styling in Word** mit VBA und **programmgesteuertes Hinzufügen von CommandButton** zu bestehenden Dokumenten. Die Erweiterung dieses Musters auf Kontrollkästchen, Kombinationsfelder oder benutzerdefinierte OLE‑Objekte folgt denselben Schritten – ändern Sie einfach den Enum‑Wert `Forms2OleControlType`.

Beginnen Sie zu experimentieren: Ersetzen Sie die Beschriftung, passen Sie die Position an oder verketten Sie mehrere Steuerelemente. Je mehr Sie üben, desto sicherer werden Sie darin, reichhaltige, interaktive Word‑Dokumente aus C# bereitzustellen. Viel Spaß beim Coden!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man programmgesteuert einen CommandButton in ein Word-Dokument einfügt](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Wie man einen ActiveX‑Button in ein Word-Dokument mit Aspose.Words einfügt](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Word-Dokument mit ActiveX‑Button erstellen – C#‑Leitfaden](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}