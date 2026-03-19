---
category: general
date: 2026-03-19
description: Erstellen Sie ein Word-Dokument mit Aspose.Words und einer variablen
  Schriftart. Erfahren Sie, wie Sie die Schriftstärke ändern, die Schriftbreite festlegen
  und die Schriftvariation in C# definieren.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: de
og_description: Erstellen Sie ein Word‑Dokument mit einer variablen Schriftart mithilfe
  von Aspose.Words. Dieses Tutorial zeigt Ihnen, wie Sie die Schriftart laden, die
  Schriftstärke ändern, die Schriftbreite einstellen und die Schriftvariation definieren.
og_title: Word-Dokument mit variabler Schrift erstellen – Komplettanleitung
tags:
- Aspose.Words
- C#
- Variable Font
title: Word‑Dokument mit variabler Schrift erstellen – Anleitung
url: /de/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument mit Variablem Font erstellen – Anleitung

Haben Sie schon einmal ein **Word‑Dokument** erstellen müssen, das einen modernen variablen Font verwendet, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein. In vielen Projekten – denken Sie an dynamische Berichte oder markenkonforme Broschüren – ist die Möglichkeit, **die Schriftstärke** on‑the‑fly zu ändern, ein echter Game‑Changer.  

In diesem Tutorial führen wir Sie durch den gesamten Prozess: vom Laden eines variablen Fonts in Aspose.Words, über das Setzen von Gewicht und Breite, bis hin zum Speichern einer DOCX, die exakt so aussieht, wie Sie sie entworfen haben. Keine vagen Verweise, sondern konkreter Code, den Sie jetzt in Ihr C#‑Projekt einfügen können.

## Was Sie lernen werden

- Wie man **variable Font**‑Dateien in Aspose.Words mit `FontSettings` lädt.
- Die Syntax zum **Definieren von Font‑Variations‑Achsen** wie `wght` (weight) und `wdth` (width).
- Wege, **die Font‑Breite zu setzen** und **die Font‑Stärke** bei einem einzelnen `Run` zu ändern.
- Tipps zur Fehlersuche bei gängigen Stolperfallen (fehlende Glyphen, falsche Ordnerpfade usw.).
- Ein vollständiges, ausführbares Beispiel, das Sie kopieren, einfügen und sofort testen können.

> **Voraussetzungen**: .NET 6+ (oder .NET Framework 4.6+), Aspose.Words für .NET über NuGet installiert und eine Variable‑Font‑Datei wie *RobotoFlex.ttf* in einem lokalen *Fonts*‑Ordner abgelegt.

---

## Schritt 1 – Laden des variablen Fonts in Aspose.Words

Zuerst müssen wir Aspose.Words mitteilen, wo nach unseren benutzerdefinierten Fonts gesucht werden soll. Die Klasse `FontSettings` übernimmt die schwere Arbeit.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Warum das wichtig ist**: Ohne die Registrierung des Ordners greift Aspose.Words auf System‑Fonts zurück und ignoriert sämtliche OpenType‑Variationsdaten, die Sie später anwenden möchten. Durch das Angeben eines konkreten Verzeichnisses stellen Sie sicher, dass *RobotoFlex* (oder jeder andere variable Font) jedes Mal gefunden wird, wenn der Code ausgeführt wird.

> **Pro‑Tipp**: Setzen Sie den zweiten Parameter von `SetFontsFolder` auf `true`, wenn Aspose auch Unterordner durchsuchen soll. Das hilft, wenn Sie Fonts nach Stil oder Gewicht organisieren.

---

## Schritt 2 – Neues Dokument erstellen und Beispieltext hinzufügen

Jetzt, wo die Font‑Engine weiß, wo sie suchen muss, erzeugen wir ein leeres `Document` und fügen einen Absatz mit einem `Run` ein.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Was passiert**: `Run` steht für ein zusammenhängendes Textstück mit einheitlicher Formatierung. Durch das frühzeitige Erzeugen können Sie die Formatierungslogik isoliert halten – ideal, um später unterschiedliche Variations‑Achsen auf separate Runs anzuwenden.

---

## Schritt 3 – Gewünschte Variations‑Achsen definieren (Weight & Width)

Variable Fonts stellen *Achsen* bereit, die Sie zur Laufzeit anpassen können. Die beiden gebräuchlichsten sind `wght` (Font‑Weight) und `wdth` (Font‑Width). Aspose.Words modelliert das mit der Sammlung `OpenTypeFontVariation`.  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Warum diese Zahlen**: In der OpenType‑Spezifikation reicht `wght` von dem minimalen bis maximalen Gewicht des Fonts (oft 100–900). Ein Wert von **700** entspricht einem fetten Aussehen. `wdth` funktioniert analog; **100** bedeutet die Standard‑Breite, während Werte unter 100 die Glyphen verdichten.

> **Randfall**: Manche variablen Fonts unterstützen eine bestimmte Achse nicht. Wenn Sie ein nicht unterstütztes Tag übergeben, ignoriert Aspose es stillschweigend. Prüfen Sie stets die Spezifikation des Fonts (meist in den Metadaten der `.ttf`‑ oder `.otf`‑Datei zu finden).

---

## Schritt 4 – Variation auf den Run anwenden über den Font‑Namen

Jetzt binden wir die Variationsdaten an den eigentlichen Text. Die Klasse `FontInfo` enthält den Font‑Familiennamen und die Achsensammlung.  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Erklärung**: Durch das Setzen von `FontInfo` umgehen wir die übliche `Font.Name`‑Eigenschaft und übergeben der Engine eine vollständig qualifizierte Font‑Konfiguration. Das ist der einzige Weg, Aspose.Words mitzuteilen, dass ein variabler Font mit benutzerdefinierten Achsen verwendet werden soll.

> **Häufiger Fehler**: Der exakte Familienname im Font‑File (`RobotoFlex` in diesem Beispiel) wird nicht exakt übernommen. Ein Tippfehler führt dazu, dass Aspose auf einen Standardschrift zurückfällt und Ihre Variation verloren geht.

---

## Schritt 5 – Dokument speichern und Ergebnis prüfen

Zum Schluss schreiben wir das Dokument auf die Festplatte. Die erzeugte DOCX enthält die Anweisungen für den variablen Font, die Microsoft Word (2016+) korrekt rendern kann.  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Öffnen Sie die resultierende Datei in Word, markieren Sie den Text und schauen Sie im **Schriftart**‑Dialog nach. Sie sollten *Roboto Flex* gelistet sehen und der Text erscheint fetter als der umgebende Inhalt – genau das, was unsere Einstellung `wght = 700` bewirkt.

> **Verifizierungstipp**: Wenn der Text unverändert aussieht, prüfen Sie, ob die Font‑Datei tatsächlich die `wght`‑Achse unterstützt. Manche „variablen“ Fonts bieten nur `ital` (italic) oder `opsz` (optical size) an.

---

## Optional: Weitere Variation – Breite dynamisch ändern

Wenn Sie die **Font‑Breite** für einen anderen Absatz anders setzen wollen, wiederholen Sie einfach die Schritte 3‑4 mit einer neuen `OpenTypeFontVariation`‑Sammlung.  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Jetzt haben Sie zwei Runs – einen fett, einen leicht breiter – und demonstrieren sowohl **change font weight** als auch **set font width** im selben Dokument.

---

## Vollständiges funktionierendes Beispiel

Kopieren Sie das Snippet unten in eine neue Konsolen‑App (`Program.cs`) und führen Sie sie aus. Stellen Sie sicher, dass der Ordner `Fonts` die Datei `RobotoFlex.ttf` (oder einen anderen gewünschten variablen Font) enthält.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Erwartete Ausgabe**: Eine Datei `VariableFont.docx`, in der die Phrase „Variable‑weight text“ dank der Achse `wght = 700` fett dargestellt wird, während die Standard‑Breite erhalten bleibt.

---

## Häufig gestellte Fragen & Randfälle

| Frage | Antwort |
|----------|--------|
| *Was, wenn der Font nicht gefunden wird?* | Prüfen Sie den Ordnerpfad, stellen Sie sicher, dass der Dateiname exakt stimmt, und dass der Prozess Lese‑Rechte hat. Sie können auch `fontSettings.GetFonts()` aufrufen, um gefundene Fonts aufzulisten. |
| *Kann ich mehrere Runs mit unterschiedlichen Variationen kombinieren?* | Absolut. Jeder `Run` kann sein eigenes `FontInfo` besitzen. Wiederholen Sie einfach die Schritte 3‑4 für jeden Run. |
| *Unterstützen ältere Word‑Versionen variable Fonts?* | Word 2016 (Build 16.0.8001) führte die Grundunterstützung ein. Zielen Sie auf ältere Versionen, fällt das Dokument auf die nächstgelegene statische Instanz des Fonts zurück. |
| *Gibt es ein Limit, wie viele Achsen ich setzen kann?* | Sie können beliebig viele Achsen setzen, die der Font definiert. Gängige Tags sind `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Ein nicht unterstütztes Tag hat einfach keine Wirkung. |
| *Wie debugge ich fehlende Glyphen?* | Nutzen Sie `FontSettings.GetFontSources()`, um geladene Fonts zu inspizieren, und `FontInfo.HasGlyph(char)`, um einzelne Zeichen zu testen. |

---

## Fazit

In wenigen Schritten haben wir gezeigt, **wie man Word‑Dokumente** erstellt, die die Leistungsfähigkeit variabler Fonts nutzen, sodass Sie **die Font‑Stärke ändern**, **die Font‑Breite setzen**, **variable Font‑Dateien laden** und **Font‑Variations‑Achsen definieren** – alles mit Aspose.Words für .NET.  

Der Kern ist simpel: Font‑Ordner registrieren, gewünschte Achsen beschreiben, sie einem `Run` zuweisen und speichern. Von hier aus können Sie die Technik auf ganze Abschnitte, Tabellen oder sogar programmgesteuert brand‑spezifische Berichte ausweiten.

**Nächste Schritte**: Tauschen Sie `RobotoFlex` gegen einen anderen variablen Font aus, experimentieren Sie mit der `ital`‑Achse (italic) oder erzeugen Sie eine PDF‑Version desselben Dokuments mit Aspose.PDF. Das gleiche Muster gilt – laden, definieren, anwenden, speichern.

Viel Spaß beim Coden und genießen Sie die Flexibilität, die variable Fonts Ihren Word‑Automatisierungsprojekten verleihen!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}