---
category: general
date: 2026-04-21
description: Speichern Sie Office-Mathematik‑LaTeX schnell mit Aspose.Words – lernen
  Sie außerdem, wie Sie Word-Plain‑Text speichern und Word‑Gleichungen als LaTeX in
  einem Schritt exportieren.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: de
og_description: Speichern Sie Office-Mathematik-LaTeX sofort; lernen Sie, Word-Gleichungen
  nach LaTeX zu exportieren und Word-Mathematik-LaTeX mit Aspose.Words in C# zu konvertieren.
og_title: Office-Mathe‑LaTeX speichern – Word‑Formeln nach LaTeX exportieren
tags:
- Aspose.Words
- C#
- LaTeX
title: save office math latex – Word‑Gleichungen nach LaTeX exportieren in C#
url: /de/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Export Word equations to LaTeX with Aspose.Words

Haben Sie jemals **office math latex speichern** aus einer `.docx`‑Datei benötigt, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein, und die gute Nachricht ist, dass die Lösung ziemlich einfach ist. In diesem Leitfaden gehen wir Schritt für Schritt durch, wie man Word‑Gleichungen nach LaTeX (und sogar MathML) mit Aspose.Words für .NET exportiert, und zeigen dabei, wie man **word plain text speichern** zusammen mit den Formeln ablegt.

Wir behandeln alles, was Sie sich fragen könnten: warum Sie LaTeX anderen Formaten vorziehen, wie Sie die `TxtSaveOptions` konfigurieren und was zu tun ist, wenn Sie **word math latex konvertieren** möchten. Am Ende haben Sie ein lauffähiges Snippet, das ein Word‑Dokument mit Office‑Math‑Objekten einliest und eine saubere `.txt`‑Datei mit LaTeX‑ (oder MathML‑) Gleichungen erzeugt. Keine externen Tools, kein manuelles Kopieren‑Einfügen – nur sauberer C#‑Code, den Sie in jedes Projekt einbinden können.

## Voraussetzungen

- **Aspose.Words for .NET** (v23.10 oder neuer). Das NuGet‑Paket heißt `Aspose.Words`.
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code mit der C#‑Erweiterung).
- Eine Word‑Datei (`.docx`), die mindestens eine Gleichung enthält, die mit dem Office‑Math‑Editor erstellt wurde.
- Grundkenntnisse in C#‑Syntax – nichts Aufwändiges, nur die üblichen `using`‑Anweisungen.

Wenn Sie diese Punkte bereits abgehakt haben, super – dann legen wir los.

## Schritt 1 – **save office math latex**‑Optionen einrichten

Als erstes müssen Sie Aspose.Words mitteilen, wie der mathematische Inhalt gerendert werden soll. Die Klasse `TxtSaveOptions` besitzt die Eigenschaft `OfficeMathExportMode`, die drei Werte akzeptiert: `LaTeX`, `MathML` oder `Text`. Für unser Hauptziel wählen wir `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Warum das wichtig ist:** Wenn Sie `OfficeMathExportMode` auf `LaTeX` setzen, wird jede Gleichung in ihren rohen LaTeX‑Quellcode umgewandelt. Dieser Quellcode kann später mit jeder LaTeX‑Engine kompiliert werden und liefert pixelgenaue Typografie, ohne dass Sie die Formeln neu tippen müssen.

> **Pro‑Tipp:** Wenn Sie jemals **word equations mathml konvertieren** müssen, ändern Sie einfach den Enum‑Wert zu `OfficeMathExportMode.MathML`. Der Rest des Codes bleibt unverändert.

## Schritt 2 – Word‑Dokument laden (das **save word plain text**‑Szenario)

Als Nächstes laden wir die Quell‑`.docx`. Dieser Schritt ist identisch, egal ob Sie nur reinen Text extrahieren oder zusätzlich die Gleichungen in LaTeX benötigen.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Was passiert hier?** Der `Document`‑Konstruktor liest die Datei in den Speicher. Die kurze Prüfung mit `GetChildNodes` hilft Ihnen, einen häufigen Sonderfall abzufangen – den Versuch, LaTeX aus einer Datei zu exportieren, die keine Gleichungen enthält. Das ist ein kleiner Schutzmechanismus, der später ein verwirrendes leeres Ergebnis verhindert.

## Schritt 3 – **save office math latex** in eine Textdatei schreiben

Jetzt schreiben wir schließlich die Datei. Die `Save`‑Methode berücksichtigt die zuvor konfigurierten `TxtSaveOptions`, sodass die resultierende `.txt` sowohl normalen Text als auch LaTeX‑Ausschnitte für jede Gleichung enthält.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Wenn Sie `Equations.txt` öffnen, sehen Sie etwa Folgendes:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Die LaTeX‑Blöcke werden automatisch in `\begin{equation}` … `\end{equation}` eingeschlossen, sodass sie sofort in jedes LaTeX‑Dokument eingefügt werden können.

## Schritt 4 – Alternative: **convert word equations mathml** statt LaTeX

Falls Ihre nachgelagerte Toolchain MathML bevorzugt (z. B. eine Webseite, die Gleichungen mit MathJax rendert), ändern Sie einfach den Exportmodus:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

Die Ausgabe enthält nun XML‑ähnliche MathML‑Tags, zum Beispiel:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Damit haben Sie den schnellen Weg, **word equations mathml zu konvertieren**, ohne einen eigenen Parser zu schreiben.

## Schritt 5 – Bonus: **save word plain text** und Gleichungen getrennt halten

Manchmal möchte man eine saubere Textversion des Dokuments *ohne* eingebettetes LaTeX oder MathML. Das erreichen Sie, indem Sie den Exportmodus auf `Text` umstellen und einen zweiten Speicherdurchlauf ausführen:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Jetzt haben Sie drei Dateien nebeneinander:

| Datei                         | Inhalt                                 |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Klartext **+** LaTeX‑Gleichungen       |
| `EquationsMathML.txt`        | Klartext **+** MathML‑Gleichungen       |
| `PlainDocument.txt`          | Reiner Text, Gleichungen entfernt       |

Dieses Muster ist praktisch, wenn Sie den Klartext in einen Suchindex einspeisen wollen, während die Original‑Mathematik für wissenschaftliche Veröffentlichungen erhalten bleibt.

## Vollständiges Beispiel (Einfaches Kopieren & Einfügen)

Unten finden Sie das komplette Programm, das Sie unverändert kompilieren und ausführen können. Es demonstriert **save office math latex**, **export word equations latex**, **convert word math latex** und **save word plain text** – alles in einem übersichtlichen Skript.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Erwartetes Ergebnis:** Nach dem Ausführen finden Sie drei Textdateien in `C:\MyDocs`. Öffnen Sie `Equations.txt` und Sie sehen LaTeX‑Blöcke; `EquationsMathML.txt` enthält MathML; `PlainDocument.txt` ist frei von jeglichen Gleichungs‑Markups.

## Häufige Fragen & Sonderfälle

- **Was, wenn ich LaTeX nur für einen Teil der Gleichungen brauche?**  
  Verwenden Sie die `OfficeMath`‑Node‑API, um über jede Gleichung zu iterieren, sie manuell mit `MathConverter` zu exportieren und den Platzhalter‑Text dort zu ersetzen, wo Sie ihn benötigen. Dieser Ansatz gibt Ihnen feinkörnige Kontrolle, erfordert jedoch ein paar zusätzliche Codezeilen.

- **Funktioniert das mit .NET Core / .NET 5+?**  
  Absolut. Aspose.Words ist plattformübergreifend, sodass derselbe Code unter Windows, Linux und macOS läuft, solange die Runtime‑Version den Bibliotheksanforderungen entspricht.

- **Kann ich den LaTeX‑Wrapper (`\begin{equation}`) anpassen?**  
  Ja. Setzen Sie `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` und passen Sie anschließend `txtOptions.MathExportSettings` (in neueren Releases verfügbar) an, um die Delimiter zu ändern.

- **Leistungsprobleme bei riesigen Dokumenten?**  
  Die Bibliothek streamt die Ausgabe, sodass der Speicherverbrauch moderat bleibt. Allerdings

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}