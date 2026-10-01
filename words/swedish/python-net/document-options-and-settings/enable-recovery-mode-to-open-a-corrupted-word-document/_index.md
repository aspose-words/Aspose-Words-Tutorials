---
category: general
date: 2026-09-30
description: Aktivera återställningsläge för att öppna ett skadat Word-dokument med
  Aspose.Words. Lär dig hur du återställer skadade docx-filer på ett säkert och pålitligt
  sätt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: sv
lastmod: 2026-09-30
og_description: Aktivera återställningsläge för att öppna ett skadat Word‑dokument
  med Aspose.Words. Denna guide visar steg‑för‑steg hur du återställer skadade docx‑filer
  och håller ditt arbetsflöde stabilt.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Aktivera återställningsläge för att öppna skadade Word-dokument
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Aktivera återställningsläge för att öppna ett korrupt Word-dokument
url: /sv/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera återställningsläge för att öppna ett skadat Word-dokument

Om du behöver **aktivera återställningsläge** när du öppnar ett skadat Word-dokument, visar den här handledningen exakt hur du gör det med Aspose.Words för Python. Oavsett om filen skadades under överföring eller redigerades av ett inkompatibelt program, låter aktivering av återställningsläge biblioteket försöka reparera dokumentet istället för att kasta ett undantag.

I den här guiden kommer du att lära dig hur du **öppnar skadade Word-dokument** filer, **återställer skadat docx**-innehåll, och förstår de alternativ som styr processen **ladda dokument med återställning**. Stegen fungerar med Aspose.Words 23.10 (den senaste versionen vid skrivtillfället) och kräver bara en standard Python-miljö.

## Förutsättningar

Innan du börjar, se till att du har:

* Python 3.9 eller nyare installerat.
* Aspose.Words för Python via .NET (`aspose-words`) installerat (`pip install aspose-words`).
* En DOCX-fil som är känd för att vara skadad (för testning kan du byta namn på en giltig `.docx` till `.zip` och manuellt förstöra XML).

> **Proffstips:** Behåll en säkerhetskopia av originalfilen. Återställningsläge modifierar dokumentet i minnet men skriver aldrig tillbaka till källan om du inte explicit sparar det.

## Steg 1: Importera biblioteket och skapa laddningsalternativ

Det första du måste göra är att importera `aspose.words` och skapa ett `LoadOptions`-objekt. Detta objekt innehåller alla inställningar som påverkar hur filen läses.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Varför detta är viktigt:* `LoadOptions` är porten till finjustering av parsern. Utan den använder Aspose.Words standard‑strikt läge, vilket avbryter vid varje strukturellt fel.

## Steg 2: Aktivera återställningsläge

Sätt egenskapen `recovery_mode` till `RecoveryMode.RECOVER`. Detta instruerar laddaren att försöka automatiskt reparera trasiga delar som saknade XML‑noder, brutna relationer eller avkortade strömmar.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Att aktivera återställningsläge **garanterar inte** ett perfekt dokument, men det ökar avsevärt chansen att du fortfarande kan extrahera text, bilder eller tabeller.

## Steg 3: Ladda det potentiellt skadade DOCX‑dokumentet med de konfigurerade alternativen

Använd nu `Document`‑konstruktorn som accepterar både filsökvägen och `LoadOptions`‑instansen.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Varför detta är viktigt:* `try/except`‑blocket visar **hur man öppnar skadade docx** på ett säkert sätt. Utan återställningsläge skulle samma anrop omedelbart kasta ett undantag och stoppa ditt program.

## Steg 4: Verifiera det återställda innehållet (valfritt men rekommenderat)

Efter laddning bör du kontrollera om dokumentet innehåller meningsfullt innehåll. Ett snabbt sätt är att extrahera ren text och skriva ut de första tecknen.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Om utskriften visar en rimlig förhandsgranskning kan du fortsätta bearbeta dokumentet (t.ex. konvertera till PDF, extrahera tabeller osv.). Om texten är tom kan filen vara oåterställbar och du kan behöva begära en ny kopia.

## Steg 5: Spara det reparerade dokumentet (om du vill ha en ren kopia)

När du är nöjd med det återställda innehållet kan du spara ett nytt, rent DOCX. Detta steg är valfritt men ofta användbart för efterföljande arbetsflöden.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Sparandet skapar en ny fil som inte längre innehåller den korruption som utlöst återställningsläge.

## Kantfall och ytterligare tips

| Situation                               | Rekommenderad metod |
|----------------------------------------|----------------------|
| **Filen är inte ett DOCX** (t.ex. `.doc`) | Använd `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` innan du laddar. |
| **Endast partiell återställning**              | Efter laddning, inspektera `document.get_text()` och `document.get_page_count()`. Om sidantalet är 0 kan dokumentet vara oåterställbart. |
| **Stora dokument**                    | Aktivera `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` för att minska RAM‑användning under återställning. |
| **Behöver logga vad som reparerades**      | Sätt `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` och läs sedan `document.get_last_save_options().recovery_log` (om tillgängligt) för detaljer. |

> **Observera:** Återställningsläge kan tyst ta bort osupporterade element (t.ex. saknade typsnitt). Om visuell trohet är kritisk, jämför det reparerade filen mot en känd‑bra version.

## Fullständigt fungerande exempel

Genom att sätta ihop allt, här är ett självständigt skript du kan köra omedelbart:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

När skriptet körs skrivs ett framgångsmeddelande, ett kort textutdrag, och `repaired.docx` skapas i samma mapp.

## Slutsats

Du vet nu hur du **aktiverar återställningsläge** för att **öppna skadade Word-dokument** filer, **återställer skadat docx**‑innehåll, och säkert **laddar dokument med återställning** med Aspose.Words för Python. De primära stegen — att skapa `LoadOptions`, slå på `RecoveryMode.RECOVER` och hantera undantag — bildar ett pålitligt mönster som du kan återanvända i vilken automatiseringspipeline som helst.

Nästa steg är att utforska relaterade ämnen såsom **konvertera det återställda dokumentet till PDF**, **extrahera tabeller med `DocumentVisitor`**, eller **batch‑processa en mapp med skadade filer**. Alla dessa bygger på samma återställningsläges‑grund som demonstrerats här.

Lycka till med kodandet, och må dina dokument förbli friska!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [hur man återställer docx – sätt återställningsläge & öppna skadade Word-filer](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [återställ skadat docx med Aspose.Words – sätt återställningsläge och laddningsalternativ](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Återställ skadad DOCX med Aspose.Words LoadOptions – Komplett C#‑guide](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}