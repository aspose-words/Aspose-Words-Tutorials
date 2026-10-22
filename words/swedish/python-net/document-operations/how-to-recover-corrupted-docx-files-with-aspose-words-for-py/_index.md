---
category: general
date: 2026-10-16
description: Lär dig hur du återställer korrupta docx‑filer, aktiverar återställningsläge
  och kontrollerar sidantalet i ett enda Python‑skript med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- enable recovery mode
- check page count
- recover word document
- how to open corrupted docx
language: sv
lastmod: 2026-10-16
og_description: Återställ korrupta docx‑filer med Aspose.Words för Python. Den här
  guiden visar hur du aktiverar återställningsläge, öppnar den skadade filen och kontrollerar
  sidantalet.
og_image_alt: Screenshot of Python code that recovers a corrupted docx document using
  Aspose.Words
og_title: Återställ korrupt docx med Aspose.Words – aktivera återställningsläge och
  verifiera sidantal
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to recover corrupted docx, enable recovery mode, and check
    page count in a single Python script using Aspose.Words.
  headline: How to recover corrupted docx files with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
- DOCX
title: Hur man återställer korrupta docx-filer med Aspose.Words för Python
url: /sv/python/document-operations/how-to-recover-corrupted-docx-files-with-aspose-words-for-py/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man återställer korrupta docx‑filer med Aspose.Words för Python

Om du behöver **återställa korrupta docx**‑filer gör Aspose.Words för Python det enkelt. Denna handledning visar hur du **aktiverar återställningsläge**, laddar det skadade dokumentet och **kontrollerar sidantalet** för att bekräfta att **återställningsoperationen för Word‑dokumentet** lyckades.

Korrupta DOCX‑filer uppstår ofta efter en avbruten sparning, en felaktig konvertering eller diskfel. Istället för att be användarna skicka om filen kan du automatiskt försöka återställa den på serversidan. Nedan lär du dig hela arbetsflödet, från installation av SDK till verifiering att dokumentet öppnades korrekt.

## Förutsättningar

Innan du börjar, se till att du har:

* Python 3.8 eller senare installerat.
* En giltig Aspose.Words för Python‑licens (gratis provversion fungerar för utvärdering).
* `aspose-words`‑paketet installerat via `pip`:

```bash
pip install aspose-words
```

* En korrupt DOCX‑fil tillgänglig på disk (t.ex. `corrupted.docx`).  
  Om du inte har en kan du simulera korruption genom att öppna en DOCX i en textredigerare och ta bort några byte.

## Steg 1: Aktivera återställningsläge för att återställa korrupta docx

Återställningsläge instruerar Aspose.Words att ignorera strukturella problem och försöka bygga om dokumentträdet. Utan detta skulle inläsning av en skadad fil kasta ett undantag.

```python
import aspose.words as aw

# Create LoadOptions and turn on recovery mode
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
```

**Varför detta är viktigt:**  
`LoadOptions.RecoveryMode.RECOVER` instruerar parsern att behandla filen som om den vore delvis giltig, hoppa över oläsliga delar och rädda resten. Detta är kärnsteg som gör att du automatiskt kan **återställa korrupta docx**‑filer.

## Steg 2: Ladda dokumentet med de återställningsaktiverade alternativen

Nu när återställningsläge är aktivt, ladda filen. Om dokumentet är allvarligt skadat kommer Aspose.Words fortfarande att returnera ett `Document`‑objekt som innehåller allt innehåll som kunde räddas.

```python
# Load the potentially corrupted DOCX using the recovery options
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Tips:** Ersätt `YOUR_DIRECTORY` med den faktiska sökvägen. Att använda en absolut sökväg undviker tvetydiga relativ‑sökvägsfel, särskilt när skriptet körs som en bakgrundstjänst.

## Steg 3: Kontrollera sidantalet för att verifiera återställningsoperationen för Word‑dokumentet

Ett snabbt sätt att bekräfta att filen öppnades är att läsa dess `page_count`. Om antalet är större än noll har återställningen lyckats tillräckligt för att rendera åtminstone en sida.

```python
# Verify that the document was loaded by printing its page count
print("Document loaded, pages:", doc.page_count)
```

Om utskriften visar `pages: 0` kan filen vara bortom reparation, eller så har korruptionen tagit bort allt utskrivbart innehåll. I så fall bör du meddela användaren och be om en ny uppladdning.

## Fullt skript – återställ korrupta docx i ett enda körning

Genom att kombinera de tre stegen får du ett kompakt, produktionsklart kodexempel:

```python
import aspose.words as aw

def recover_docx(file_path: str) -> int:
    """
    Attempts to recover a corrupted DOCX file and returns the page count.
    Returns -1 if the file cannot be opened at all.
    """
    # Step 1: Enable recovery mode
    load_options = aw.LoadOptions()
    load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

    try:
        # Step 2: Load the document with recovery enabled
        doc = aw.Document(file_path, load_options)

        # Step 3: Check page count – this also confirms the file was recovered
        page_count = doc.page_count
        print(f"Recovered document page count: {page_count}")
        return page_count
    except Exception as e:
        # If loading fails even with recovery mode, report the error
        print(f"Failed to recover '{file_path}': {e}")
        return -1

if __name__ == "__main__":
    # Example usage – replace with your actual file location
    recover_docx("YOUR_DIRECTORY/corrupted.docx")
```

**Förklaring av funktionen:**

* **Parametrar** – `file_path` pekar på den DOCX du vill öppna.  
* **Returvärde** – Antalet sidor efter återställning, eller `-1` om filen inte kan öppnas.  
* **Felhantering** – Även med återställningsläge kan vissa filer vara oåterställbara; `except`‑blocket säkerställer att skriptet misslyckas på ett kontrollerat sätt.

## Hur man öppnar korrupta docx i en webbtjänst (valfritt)

Om du exponerar denna logik via en Flask‑ eller FastAPI‑endpoint kan du låta klienter ladda upp en fil och få ett JSON‑svar med sidantalet.

```python
from fastapi import FastAPI, File, UploadFile
import shutil, os

app = FastAPI()

@app.post("/recover")
async def recover_endpoint(file: UploadFile = File(...)):
    temp_path = f"/tmp/{file.filename}"
    with open(temp_path, "wb") as buffer:
        shutil.copyfileobj(file.file, buffer)

    pages = recover_docx(temp_path)
    os.remove(temp_path)  # Clean up temporary file

    return {"filename": file.filename, "page_count": pages}
```

**Varför du kan behöva detta:**  
I företagsdokument‑processeringspipelines minskar automatiska återställningsförsök manuella supportärenden och förbättrar användarupplevelsen.

## Vanliga fallgropar och felsökning

| Symtom | Trolig orsak | Åtgärd |
|---|---|---|
| `Exception: File not found` | Fel sökväg eller saknad fil | Verifiera den absoluta sökvägen och säkerställ att filen finns. |
| `pages: 0` även efter återställning | Filen innehåller endast icke‑visuell data (t.ex. bara metadata) | Kontrollera om originaldokumentet faktiskt hade sidor; annars begär en ny fil. |
| `LicenseException` | Ingen giltig Aspose.Words‑licens | Använd en prov- eller kommersiell licens med `aw.License().set_license("path/to/license.xml")`. |
| Långsam laddning på mycket stora filer | Återställningsläge bearbetar många trasiga delar | Överväg att strömma filen eller öka minnesgränserna. |

**Proffstips:** Logga alltid det ursprungliga undantagsmeddelandet när återställning misslyckas. Meddelandet innehåller ofta den exakta XML‑noden som orsakade problemet, vilket kan hjälpa dig förbättra den uppströms dokumentgenereringsprocessen.

## Förväntat resultat

Att köra skriptet mot en återställningsbar `corrupted.docx` skriver ut något liknande:

```
Recovered document page count: 5
```

Om filen inte kan räddas får du:

```
Failed to recover 'YOUR_DIRECTORY/corrupted.docx': The file is corrupted and cannot be opened.
```

Att se ett positivt sidantal bekräftar att du framgångsrikt **återställt korrupta docx** och nu kan fortsätta bearbeta dokumentet (t.ex. konvertera till PDF, extrahera text osv.).

## Nästa steg

Nu när du vet **hur man öppnar korrupta docx** kan du utöka arbetsflödet:

* **Konvertera det återställda dokumentet till PDF** – anropa `doc.save("output.pdf")`.
* **Extrahera text för indexering** – iterera över `doc.get_child_nodes(aw.NodeType.PARAGRAPH, True)`.
* **Batch‑processa en mapp med skadade filer** – loopa över filer och lagra resultat i en databas.

Varje av dessa utökningar använder samma `Document`‑objekt som du fick efter **aktivering av återställningsläge**, så återställningssteget förblir grunden i alla robusta dokument‑hanteringspipelines.

---

*Du har lärt dig hur du återställer en korrupt DOCX‑fil, aktiverar återställningsläge och verifierar framgång genom att kontrollera sidantalet. Använd dessa mönster för att hålla dina dokument‑processeringstjänster motståndskraftiga och användarvänliga.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Återställ korrupt DOCX – Komplett guide för att aktivera återställningsläge och hämta sidantal](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [hur man återställer docx – sätt återställningsläge & öppna korrupta Word‑filer](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Hur man återställer docx – Aktivera återställningsläge & läs varningar](/words/english/java/document-loading-and-saving/how-to-recover-docx-enable-recovery-mode-read-warnings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}