---
category: general
date: 2026-10-04
description: Aktivera återställningsläge i Aspose.Words för att säkert återställa
  ett korrupt Word-dokument. Följ den steg‑för‑steg‑guiden med fullständig Python‑kod
  och förklaringar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: sv
lastmod: 2026-10-04
og_description: Aktivera återställningsläge för att återställa ett korrupt Word-dokument
  med Aspose.Words. Denna handledning visar den exakta Python‑koden, varför den fungerar
  och hur man hanterar kantfall.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Aktivera återställningsläge för att återställa ett skadat Word‑dokument
  – fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Aktivera återställningsläge för att återställa ett korrupt Word-dokument
url: /sv/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera återställningsläge för att återställa ett skadat Word-dokument

Om du behöver **aktivera återställningsläge** när du laddar en Word‑fil, visar den här guiden exakt hur du gör det med Aspose.Words för Python. Genom att slå på återställningsläge kan du **återställa ett skadat Word‑dokument** som annars skulle kasta ett undantag.

I de följande avsnitten kommer du att lära dig:

* Vilka klasser och egenskaper som styr återställningsbeteendet.  
* Hur du laddar en potentiellt skadad `.docx`‑fil utan att krascha din applikation.  
* Tips för felsökning av vanliga laddningsproblem och anpassning av återställningsstrategin.

> **Förutsättning** – Du har Aspose.Words för Python installerat (`pip install aspose-words`) och en grundläggande förståelse för Python fil‑I/O.

## Vad återställningsläge gör och varför du bör aktivera det

Aspose.Words analyserar den interna strukturen i en Word‑fil innan den exponeras som ett `Document`‑objekt. När filen är skadad—saknade delar, trasig XML eller ogiltiga relationer—kan parsern antingen:

| Läge | Beteende |
|------|----------|
| `STRICT` | Kastar ett undantag vid det första tecknet på korruption. |
| `IGNORE_ERRORS` | Hoppar över oläsbara delar men kan tyst förlora innehåll. |
| `RECOVER` (alternativet **aktivera återställningsläge**) | Försöker bygga om dokumentet, bevarar så mycket innehåll som möjligt och visar det valda läget via `load_options.recovery_mode`. |

`RECOVER` är det rekommenderade valet när du måste **återställa korrupta Word‑dokument** för efterföljande bearbetning, såsom att extrahera text eller konvertera till PDF.

## Steg 1: Skapa LoadOptions och aktivera återställningsläge

Det första steget är att instansiera `LoadOptions` och sätta egenskapen `recovery_mode` till `RecoveryMode.RECOVER`. Detta talar om för biblioteket att gå in i återställningsvägen under parsning.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Varför detta är viktigt:**  
Om du hoppar över detta steg och dokumentet är skadat, kommer konstruktorn `aw.Document(...)` att kasta `InvalidOperationException`. Att aktivera återställningsläge förhindrar kraschen och ger dig ett delvis reparerat `Document`‑objekt som du fortfarande kan arbeta med.

## Steg 2: Ladda det potentiellt skadade dokumentet med de angivna alternativen

Skicka `load_options`‑instansen till `Document`‑konstruktorn. Laddaren kommer nu att automatiskt tillämpa återställningsalgoritmen.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Tips:** Ersätt `YOUR_DIRECTORY` med den absoluta eller relativa sökväg som din körmiljö kan komma åt. Om filen inte finns kommer Aspose.Words att kasta ett `FileNotFoundError` innan den ens når återställningslogiken.

## Steg 3: Verifiera att återställningsläge har tillämpats

Du kan bekräfta det aktiva läget genom att inspektera `load_options.recovery_mode`. Detta är användbart för loggning eller villkorad hantering senare i pipeline.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Förväntad output**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Om outputen visar `RECOVER` har du framgångsrikt **aktiverat återställningsläge** och dokumentet är nu redo för vidare bearbetning (t.ex. textutdrag, konvertering till PDF eller sparande av en reparerad kopia).

## Steg 4 (valfritt): Spara en reparerad kopia för framtida bruk

Efter laddning kan du vilja persistera det återställda dokumentet så att du inte behöver upprepa återställningssteget.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Sparande skapar en ny `.docx` som Aspose.Words anser vara giltig, och som kan öppnas i Microsoft Word utan varningar.

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| **Vad händer om dokumentet är helt oläsbart?** | Även i `RECOVER`‑läge är vissa filer bortom reparation. `Document`‑objektet kommer att skapas men kan bara innehålla en enda tom sida. Kontrollera `doc.get_page_count()` för att verifiera innehållet. |
| **Kan jag byta till `IGNORE_ERRORS` efter laddning?** | Nej. Återställningsläget måste sättas **innan** `Document`‑konstruktorn körs. Skapa en ny `LoadOptions`‑instans om du behöver en annan strategi. |
| **Påverkar återställningsläge prestanda?** | Ja, det lägger till en liten overhead eftersom biblioteket försöker rekonstruera trasiga delar. Påverkan är försumbar för de flesta filer (< 2 MB). |
| **Är detta tillvägagångssätt språkoberoende?** | Samma koncept finns i .NET-, Java- och Node.js‑API:erna (`LoadOptions.RecoveryMode`). Kodsyntaxen förändras, men logiken är identisk. |

## Proffstips: Logga detaljerad återställningsinformation

Aspose.Words tillhandahåller en `LoadOptions.recovery_callback` som får detaljerade meddelanden om varje återställningssteg. Att koppla den kan hjälpa dig att diagnostisera varför ett specifikt dokument misslyckades.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Nu kommer varje intern korrigering (t.ex. “Removed duplicate relationship”) att skrivas ut till konsolen.

## Fullt, körbart exempel

När alla bitar sätts ihop, här är ett självständigt skript som du kan kopiera‑klistra in och köra omedelbart:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Att köra skriptet skriver ut återställningsläget, sidantalet och en lista med ord som extraherats från det reparerade dokumentet. Om du sätter `save_repaired=True` visas en ny ren fil bredvid originalet.

## Slutsats

Du vet nu hur du **aktiverar återställningsläge** i Aspose.Words för Python och på ett pålitligt sätt **återställer korrupta Word‑dokument**. Nyckelstegen är:

1. Skapa `LoadOptions` och sätt `recovery_mode` till `RECOVER`.  
2. Ladda `.docx`‑filen med de alternativen.  
3. Verifiera läget och spara eventuellt en reparerad kopia.

Härifrån kan du utforska vidare ämnen såsom **extrahera text från ett återställt dokument**, **konvertera det till PDF**, eller **automatisera batch‑återställning** för stora dokumentbibliotek.

---


## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Återställ skadat DOCX – Komplett guide för att aktivera återställningsläge & få sida](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Återställ skadat DOCX – Öppna & ladda Word‑dokument](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [återställ skadat docx med Aspose.Words – sätt återställningsläge och laddningsalternativ](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}