---
category: general
date: 2026-08-04
description: Fußnotentrennzeichen in C# mit Aspose.Words ändern – lernen Sie, wie
  Sie das Fußnotentrennzeichen bearbeiten und das Endnotentrennzeichen in Word‑Dokumenten
  ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: de
lastmod: 2026-08-04
og_description: Fußnotentrennzeichen in C# mit Aspose.Words ändern. Dieser Leitfaden
  zeigt Ihnen, wie Sie das Fußnotentrennzeichen bearbeiten, das Endnotentrennzeichen
  anpassen und das aktualisierte Dokument speichern.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Fußnotentrennzeichen in C# ändern – vollständige Aspose.Words-Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Fußnotentrennzeichen in C# mit Aspose.Words ändern
url: /de/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fußnotentrennzeichen in C# mit Aspose.Words ändern

Wenn Sie das **Fußnotentrennzeichen** in einem Word‑Dokument ändern müssen, führt Sie dieses Tutorial Schritt für Schritt mit Aspose.Words für .NET durch. Egal, ob Sie die Standardlinie durch ein Symbol ersetzen oder einen anderen Stil für Endnotentrennzeichen anwenden möchten, der untenstehende Code deckt den gesamten Arbeitsablauf ab.

Sie lernen außerdem, wie man **Fußnotentrennzeichen bearbeitet** und die zugehörige **Endnotentrennzeichen ändern**‑Operation durchführt, sodass dasselbe Dokument ein konsistentes Styling für Fußnoten und Endnoten hat. Es werden keine externen Tools benötigt – nur ein paar Zeilen C#.

## Was Sie erreichen werden

* Eine vorhandene *.docx*-Datei laden, die Fußnoten und Endnoten enthält.  
* Auf die Trennzeichen‑Knoten für Fußnoten, Fußnoten‑Fortsetzungen und Endnoten zugreifen.  
* Das Trennzeichen‑Zeichen ersetzen (z. B. die Standardlinie durch ein Sternchen ändern).  
* Das geänderte Dokument speichern, ohne anderen Inhalt zu verlieren.  

Das Tutorial geht davon aus, dass Sie Grundkenntnisse in C# besitzen und das **Aspose.Words**‑NuGet‑Paket (Version 24.9 oder neuer) installiert haben.

---

## Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6.0 oder .NET Framework 4.7.2+ | Erforderliche Laufzeit für Aspose.Words |
| Aspose.Words for .NET Bibliothek | Stellt die APIs `Document` und `FootnoteOptions` bereit |
| Eine Eingabe‑Word‑Datei (`input.docx`) mit mindestens einer Fußnote oder Endnote | Demonstriert die Trennzeichen‑Änderung |

Sie können Aspose.Words zu Ihrem Projekt mit folgendem CLI‑Befehl hinzufügen:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Schritt 1: Laden des Dokuments mit Fußnoten

Der erste Schritt besteht darin, die Quelldatei in ein `Document`‑Objekt zu lesen. Dieses Objekt repräsentiert die gesamte Word‑Datei im Speicher und ermöglicht den Zugriff auf alle Knoten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Warum das wichtig ist:** Das Laden des Dokuments ist der Einstiegspunkt für jede Manipulation. Wenn die Datei nicht gefunden wird, wirft Aspose.Words eine `FileNotFoundException`, stellen Sie also sicher, dass der Pfad korrekt ist, bevor Sie fortfahren.

---

## Schritt 2: Zugriff auf die Trennzeichen‑Knoten von Fußnoten und Endnoten

`Document.FootnoteOptions` stellt drei Trennzeichen‑Knoten bereit:

* `Separator` – die Linie, die nach der Fußnotensammlung auf der ersten Seite erscheint.  
* `ContinuationSeparator` – die Linie, die verwendet wird, wenn Fußnoten auf die nächste Seite fortgesetzt werden.  
* `EndnoteSeparator` – die Linie, die den Haupttext von der Endnotenliste trennt.  

Sie rufen diese Knoten als generische `Node`‑Objekte ab und casten sie anschließend zu `Run`, um den Text zu ändern.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Warum das wichtig ist:** Diese Knoten sind die einzigen Stellen, an denen das visuelle Trennzeichen‑Zeichen gespeichert ist. Das Ändern eines anderen Knotens (z. B. eines normalen Absatzes) wirkt sich nicht auf die Fußnotenformatierung aus.

---

## Schritt 3: Das Fußnotentrennzeichen ändern

Die häufigste Anforderung besteht darin, die Standardlinie durch ein Symbol wie ein Sternchen (`*`) zu ersetzen. Da das Trennzeichen als `Run` gespeichert ist, können Sie dessen `Text`‑Eigenschaft sicher ändern.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Warum das wichtig ist:** Durch das direkte Bearbeiten von `Run.Text` wird die visuelle Darstellung im endgültigen Dokument aktualisiert, ohne anderen Fußnoteninhalt zu beeinflussen. Das gleiche Muster kann verwendet werden, um beliebige Zeichenketten, einschließlich Unicode‑Symbole, anzuwenden.

---

## Schritt 4: Endnotentrennzeichen ändern (optional)

Wenn Sie ebenfalls das **Endnotentrennzeichen ändern** müssen, folgt der Vorgang dem der Fußnotenänderung. Ersetzen Sie den Text von `endnoteSeparator` durch das gewünschte Zeichen.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Warum das wichtig ist:** Endnoten werden häufig anders formatiert als Fußnoten. Ein separates Trennzeichen ermöglicht es, die visuelle Konsistenz mit den Gestaltungsrichtlinien Ihres Dokuments beizubehalten.

---

## Schritt 5: Das geänderte Dokument speichern

Nach allen Änderungen speichern Sie die Änderungen mit `Document.Save`. Sie können die Originaldatei überschreiben oder an einem neuen Ort speichern.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Warum das wichtig ist:** `Save` schreibt die im Speicher befindliche Darstellung auf die Festplatte und bewahrt alle anderen Elemente (Stile, Bilder, Tabellen) unverändert.

---

## Vollständiges, ausführbares Beispiel

Wenn man alle Teile zusammenfügt, erhalten Sie eine eigenständige Konsolenanwendung, die den gesamten Arbeitsablauf demonstriert:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Erwartetes Ergebnis:** Öffnen Sie *ModifiedSeparators.docx* in Microsoft Word. Die Fußnotentrennlinie am unteren Rand der ersten Fußnotenseite wird nun ein einzelnes Sternchen (`*`) sein. Enthält das Dokument Endnoten, erscheint die Linie, die den Haupttext von der Endnotenliste trennt, als Bindestrich (`-`). Alle anderen Inhalte (Text, Bilder, Tabellen) bleiben unverändert.

---

## Häufige Fragen & Edge‑Case‑Behandlung

| Frage | Antwort |
|-------|---------|
| **Was ist, wenn das Dokument keine Fußnoten hat?** | `FootnoteOptions.Separator` gibt immer noch einen `Run`‑Knoten zurück, dessen Text jedoch leer sein kann. Der Code prüft den Knotentyp sicher, bevor er ihn ändert. |
| **Kann ich eine Zeichenkette mit mehreren Zeichen verwenden (z. B. "***")?** | Ja. Die `Run.Text`‑Eigenschaft akzeptiert jede Zeichenkette, einschließlich Unicode‑Zeichen. |
| **Beeinflusst das Ändern des Trennzeichens die vorhandene Fußnotennummerierung?** | Nein. Das Trennzeichen ist unabhängig vom Nummerierungsschema. |
| **Muss ich das `Document`‑Objekt freigeben?** | `Document` implementiert `IDisposable` implizit über `Node`. In einer kurzlebigen Konsolenanwendung ist es optional, aber für langlaufende Dienste können Sie es in einem `using`‑Block einbetten. |
| **Wie funktioniert das mit .NET Core vs .NET Framework?** | Die API ist über alle Laufzeitumgebungen hinweg identisch; nur die Ziel‑Framework‑Version ist relevant (muss vom Aspose.Words‑Paket unterstützt werden). |

**Pro‑Tipp:** Wenn Sie unterschiedliche Trennzeichen für verschiedene Abschnitte anwenden müssen, können Sie über `doc.GetChildNodes(NodeType.Footnote, true)` iterieren und die `Separator`‑Eigenschaft jeder Fußnote einzeln anpassen. Dies ist fortgeschrittener, aber nützlich für komplexe Dokumente.

---

## Fazit

Sie wissen jetzt, wie man **Fußnotentrennzeichen ändert** und **Endnotentrennzeichen ändert** in einer Word‑Datei mit Aspose.Words für C#. Der Leitfaden behandelte das Laden des Dokuments, den Zugriff auf die relevanten Trennzeichen‑Knoten, das Ändern ihres Textes und das Speichern des Ergebnisses – alles in einem einzigen, eigenständigen Programm.

Ab hier können Sie verwandte Themen erkunden, wie **Fußnotentrennzeichenstil bearbeiten**, die Anpassung der Fußnotennummerierung oder das Anwenden bedingter Formatierungen basierend auf dem Seitenlayout. Das gleiche Muster (einen Knoten abrufen, zu `Run` casten, `Text` ändern) funktioniert für viele andere Word‑Verarbeitungsszenarien.

Viel Spaß beim Programmieren und fühlen Sie sich frei, mit verschiedenen Symbolen zu experimentieren oder sogar Bilder als Trennzeichen einzubetten, um ein wirklich einzigartiges Dokumentlayout zu erzielen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wortverarbeitung mit Fußnoten und Endnoten](/words/english/net/working-with-footnote-and-endnote/)
- [Paragraph‑Stil‑Trennzeichen im Word‑Dokument erhalten](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Dokument‑Stil‑Trennzeichen in Word einfügen](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}