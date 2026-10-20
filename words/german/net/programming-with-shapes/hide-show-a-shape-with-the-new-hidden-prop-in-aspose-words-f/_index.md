---
category: general
date: 2026-10-20
description: Ein Shape mit der neuen `Hidden`‑Eigenschaft ausblenden/anzeigen mit
  Aspose.Words für C#. Erfahren Sie, wie Sie die Sichtbarkeit von Shapes umschalten,
  Sonderfälle behandeln und das Ergebnis speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: de
lastmod: 2026-10-20
og_description: Verstecken/Anzeigen einer Form mit der neuen `Hidden`‑Eigenschaft
  unter Verwendung von Aspose.Words für C#. Beherrschen Sie das Umschalten der Sichtbarkeit
  von Formen und vermeiden Sie häufige Fallstricke.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Form ausblenden/anzeigen mit der neuen `Hidden`‑Eigenschaft in Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Ein Shape ausblenden/anzeigen mit der neuen `Hidden`‑Eigenschaft in Aspose.Words
  für C#
url: /de/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ein Shape mit der neuen `Hidden`‑Eigenschaft in Aspose.Words für C# ausblenden/anzeigen

Wenn Sie ein **Shape mit der neuen `Hidden`‑Eigenschaft** in einem Word‑Dokument ausblenden/anzeigen müssen, zeigt Ihnen dieser Leitfaden genau, wie Sie dies mit Aspose.Words für .NET erledigen können. Egal, ob Sie Berichte generieren, Vorlagen erstellen oder importierte Dokumente bereinigen, die programmgesteuerte Steuerung der Sichtbarkeit von Shapes erspart Ihnen manuelle Nachbearbeitung.

In diesem Tutorial lernen Sie, wie Sie ein Dokument laden, ein Shape finden, die `Hidden`‑Eigenschaft umschalten und die geänderte Datei speichern. Die Schritte behandeln zudem gängige Varianten, wie das Verarbeiten mehrerer Shapes und den Umgang mit Inline‑ gegenüber schwebenden Grafiken.

## Voraussetzungen

* .NET 6.0 (oder höher) installiert – Aspose.Words unterstützt .NET Standard 2.0 und .NET Core.
* Eine lizenzierte Kopie von **Aspose.Words für .NET** (die kostenlose Testversion eignet sich zum Ausprobieren).
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code.
* Ein Word‑Dokument (`input.docx`), das mindestens ein Shape enthält (z. B. ein Bild, SmartArt oder eine Zeichenfläche).

## Schritt 1: Word‑Dokument laden

Der erste Vorgang besteht darin, ein `Document`‑Objekt zu erstellen, das die .docx‑Datei auf dem Datenträger repräsentiert.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Warum dieser Schritt wichtig ist*: `Document` ist der Einstiegspunkt für alle Aspose.Words‑Operationen. Das Laden der Datei in den Speicher verschafft Ihnen vollständigen Zugriff auf den Knotenbaum, einschließlich der Shapes.

## Schritt 2: Ziel‑Shape abrufen

Um die Sichtbarkeit umzuschalten, müssen Sie eine Referenz auf den Shape‑Knoten erhalten. Das nachstehende Beispiel holt das erste Shape im Dokument, Sie können die Logik jedoch anpassen, um Shapes nach Name, Typ oder Index zu finden.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Warum dieser Schritt wichtig ist*: `GetChild` mit `true` führt eine Tiefensuche durch und stellt sicher, dass Sie Shapes finden, selbst wenn sie in Tabellen oder Kopf‑/Fußzeilen verschachtelt sind. Die Prüfung auf `null` verhindert eine `NullReferenceException`, wenn das Dokument keine Shapes enthält.

## Schritt 3: Shape mit der `Hidden`‑Eigenschaft ausblenden

Aspose.Words hat die `Hidden`‑Eigenschaft eingeführt, um zu steuern, ob ein Shape gerendert oder gedruckt wird. Wird sie auf `true` gesetzt, wird das Shape ausgeblendet; wird sie auf `false` gesetzt, erscheint das Shape wieder.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Wenn Sie ein zuvor ausgeblendetes Shape **anzeigen** müssen, weisen Sie einfach `false` zu:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Warum dieser Schritt wichtig ist*: Die `Hidden`‑Eigenschaft funktioniert sowohl für schwebende als auch für Inline‑Shapes und integriert sich in das native „Hidden“-Format von Word. Dieser Ansatz ist zuverlässiger als das Entfernen des Shapes, da der Knoten im Dokumentbaum erhalten bleibt und Layout sowie Verweise bewahrt.

## Schritt 4: Geändertes Dokument speichern

Nach der Anpassung der Sichtbarkeit schreiben Sie die Änderungen in eine neue Datei zurück (oder überschreiben die Originaldatei, falls gewünscht).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Warum dieser Schritt wichtig ist*: `Save` serialisiert den im Speicher befindlichen Knotenbaum in ein .docx‑Paket, das Word öffnen kann. Das Hidden‑Flag wird gespeichert, sodass das Öffnen der Datei in Microsoft Word das Shape gemäß der `Hidden`‑Einstellung anzeigt.

## Vollständiges, ausführbares Beispiel

Wenn Sie alle Schritte zusammenführen, erhalten Sie ein eigenständiges Programm, das Sie kopieren, kompilieren und ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Erwartete Ausgabe** beim Ausführen des Programms:

```
Document saved. Shape hidden = True
```

Wenn Sie `ShapeHidden.docx` in Microsoft Word öffnen, wird das Dokument ohne das Ziel‑Shape angezeigt. Setzen Sie `shape.Hidden = false;` vor dem Speichern, erscheint das Shape wieder.

## Umgang mit mehreren Shapes

Das obige Beispiel funktioniert für ein einzelnes Shape. In realen Dokumenten sind häufig viele Grafiken enthalten. Verwenden Sie eine Schleife, um alle Shapes, die einer Bedingung entsprechen (z. B. ein bestimmter Name oder Typ), auszublenden oder anzuzeigen.

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tipp*: Das Filtern nach `ShapeType` verhindert das unbeabsichtigte Ausblenden von dekorativen Elementen wie Textfeldern oder SmartArt.

## Sonderfälle und bewährte Vorgehensweisen

| Situation | Empfohlene Vorgehensweise |
|-----------|---------------------------|
| **Shape befindet sich in einer Kopf‑/Fußzeile** | Rufen Sie zuerst den Kopf‑/Fußzeilen‑Knoten ab und rufen Sie dann `GetChild(NodeType.Shape, …)` auf diesem Unterdokument auf. |
| **Dokument enthält keine Shapes** | Prüfen Sie immer nach `GetChild` auf `null` oder verifizieren Sie `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Sie müssen das Hidden‑Flag über verschiedene Word‑Versionen hinweg erhalten** | Die `Hidden`‑Eigenschaft wird im XML des Shapes als `<w:hidden/>` gespeichert, was von Word 2007 und später unterstützt wird. |
| **Leistung bei großen Dokumenten** | Verwenden Sie `doc.GetChildNodes(NodeType.Shape, true)` einmal und wiederverwenden Sie die Sammlung, anstatt `GetChild` wiederholt aufzurufen. |

## Profi‑Tipp: `Hidden` mit `WrapType` kombinieren

Wenn ein Shape ausgeblendet ist, reserviert Word weiterhin den Platz, den es einnehmen würde, sofern Sie nicht auch das Umbruchverhalten ändern. Das Setzen von `WrapType = WrapType.None` entfernt den Platzhalterbereich.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Damit kollabiert das Layout, als ob das Shape nie existiert hätte, was für die Erstellung sauberer Berichte nützlich ist.

## Fazit

Sie wissen jetzt, wie Sie **ein Shape mit der neuen `Hidden`‑Eigenschaft** mithilfe von Aspose.Words für C# ausblenden/anzeigen können. Die Lösung umfasst das Laden eines Dokuments, das Auffinden eines Shapes, das Umschalten der `Hidden`‑Eigenschaft und das Persistieren der Änderung. Durch Befolgen der bewährten Tipps – Prüfung auf `null`, Umgang mit mehreren Shapes und Anpassen der Umbruch‑Einstellungen – können Sie die Sichtbarkeit von Shapes in jedem Word‑Automatisierungsszenario zuverlässig steuern.

Bereit, mehr zu entdecken? Berücksichtigen Sie die folgenden nächsten Schritte:

* **Mehrere Shapes ausblenden/anzeigen** basierend auf benutzerdefinierten Metadaten (verwendet die „programmgesteuerte Ausblend‑Technik“).
* **`Hidden` mit bedingtem Inhalt kombinieren** mittels Aspose.Words‑Felder für die dynamische Berichtserstellung.
* **Andere Knoteneigenschaften erkunden**, wie `Visible` für Diagrammobjekte oder `IsDeleted` für die Steuerung auf Absatzebene.

Viel Spaß beim Coden und genießen Sie die feinkörnige Kontrolle, die Aspose.Words für die Sichtbarkeit von Shapes in Word‑Dokumenten bietet!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}