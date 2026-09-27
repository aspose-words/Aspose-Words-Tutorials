---
category: general
date: 2026-09-27
description: Konvertera docx till txt i Python med Aspose.Words. Lär dig att läsa
  in ett Word‑dokument, ställa in UTF‑8‑kodning och exportera Word‑dokumentet som
  txt på några få rader.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: sv
lastmod: 2026-09-27
og_description: Konvertera docx till txt i Python med Aspose.Words. Den här handledningen
  visar hur du laddar ett Word‑dokument, konfigurerar kodning och sparar Word som
  ren text.
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: Konvertera docx till txt i Python – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: Hur man konverterar docx till txt i Python med Aspose.Words
url: /sv/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man konverterar docx till txt i Python med Aspose.Words

Om du snabbt behöver **convert docx to txt**, visar den här guiden en komplett lösning i Python. Du kommer att lära dig hur du **load word document python**, konfigurerar UTF‑8‑kodning och **export word document txt** med bara några rader kod.

Tutorialen täcker allt du behöver för att köra konverteringen på vilken plattform som helst som stödjer Python 3. I slutet av artikeln kommer du att kunna **save word as plain text** på ett pålitligt sätt, även när källdokumentet innehåller specialtecken eller icke‑ASCII‑symboler.

## Förutsättningar

* Python 3.8 eller nyare installerat.
* En aktiv Aspose.Words för Python-licens (gratis provversion fungerar för utvärdering).
* `aspose-words`-paketet installerat via `pip install aspose-words`.
* En DOCX-fil du vill konvertera (exemplet använder `input.docx`).

> **Pro tip:** Behåll din licensfil (`Aspose.Words.lic`) i samma mapp som ditt skript eller ange `Aspose.Words.License`-sökvägen explicit för att undvika vattenstämplar i utvärderingsläge.

## Installera Aspose.Words

Kör följande kommando i din terminal eller kommandoprompt:

```bash
pip install aspose-words
```

Paketet innehåller `aw`-namnutrymmet som används i hela kodexemplen.

## Steg 1 – Ladda Word-dokumentet (convert docx to txt)

Den första operationen är att läsa DOCX-filen till ett `aw.Document`-objekt. Detta steg motsvarar kravet **load word document python**.

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Varför detta är viktigt*: Att ladda dokumentet skapar en minnesrepresentation som Aspose.Words kan manipulera, oavsett originalfilens format.

## Steg 2 – Konfigurera TXT‑sparalternativ (convert word to plain text)

Aspose.Words tillhandahåller `TxtSaveOptions` för att styra hur plain‑text‑utdata genereras. Genom att sätta egenskapen `encoding` till `"utf-8"` säkerställs att alla Unicode‑tecken bevaras.

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Varför detta är viktigt*: Utan explicit kodning kan standard‑systemets kodsida ersätta icke‑ASCII‑tecken med frågetecken. UTF‑8 är det säkraste valet för flerspråkiga dokument.

## Steg 3 – Spara dokumentet som ren text (save word as plain text)

Skriv nu dokumentet till en `.txt`-fil med de alternativ som definierats ovan.

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

Den resulterande `out.txt`-filen innehåller endast den textuella innehållet från `input.docx`, med radbrytningar som matchar den ursprungliga styckestrukturen.

### Förväntat resultat

Om `input.docx` innehåller meningen:

> **“Hello, world! Привет мир!”**

kommer den genererade `out.txt` att visa:

```
Hello, world! Привет мир!
```

Alla tecken förblir intakta eftersom UTF‑8‑kodning har använts.

## Hantera vanliga kantfall

| Situation | Recommended approach |
|-----------|----------------------|
| **Document contains tables** | Aspose.Words plattar till tabellceller till ren text separerade med tabbar. Om du behöver en anpassad avgränsare, sätt `txt_options.table_cell_separator` därefter. |
| **Large files (≥ 100 MB)** | Strömma dokumentet för att undvika hög minnesanvändning: använd `doc.save(output_stream, txt_options)` där `output_stream` är ett filobjekt öppnat i binärt läge. |
| **Missing fonts** | Installera de nödvändiga teckensnitten på värdmaskinen eller bädda in dem i DOCX innan konvertering. Saknade teckensnitt påverkar endast visuell rendering, inte extrahering av ren text. |
| **Password‑protected DOCX** | Ange lösenordet vid inläsning: `doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`. |

## Fullt skript – redo att köras

Spara följande kod som `convert_docx_to_txt.py` och kör den med `python convert_docx_to_txt.py`.

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

När skriptet körs skrivs en bekräftelse rad ut och `out.txt` skapas i den angivna katalogen.

## Verifiera resultatet

Efter körning, öppna `out.txt` i någon textredigerare (t.ex. VS Code, Notepad++) och bekräfta att innehållet matchar originaltexten i DOCX. Om du ser felaktiga tecken, dubbelkolla att `txt_options.encoding` är satt till `"utf-8"`.

## Nästa steg och relaterade ämnen

* **Convert docx to pdf** – använd `aw.saving.PdfSaveOptions` för PDF‑utdata med hög noggrannhet.
* **Extract images from a Word document** – utforska `aw.NodeType.SHAPE` och `Shape`-klassen.
* **Batch conversion** – iterera över en mapp med DOCX‑filer och anropa `convert_docx_to_txt` för varje fil.
* **Advanced encoding** – experimentera med `txt_options.add_bidi_marks` när du hanterar skript som skrivs från höger till vänster.

Genom att behärska stegen ovan kan du **export word document txt** i vilken automatiseringspipeline som helst, oavsett om du bygger ett kommandoradsverktyg, integrerar med en webbtjänst eller bearbetar dokument i molnet.

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Convert docx till txt – Komplett guide för att spara Word som ren text](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Spara docx som txt och exportera Word‑ekvationer som LaTeX – Komplett guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Word till PDF‑handledning: Konvertera DOCX till PDF med Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}