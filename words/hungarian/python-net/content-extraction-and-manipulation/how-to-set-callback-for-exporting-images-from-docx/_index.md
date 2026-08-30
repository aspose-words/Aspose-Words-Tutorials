---
category: general
date: 2026-06-24
description: Hogyan állítsunk be visszahívást a képek exportálásához a DOCX‑ből Markdown
  formátumba mentéskor. Tanulja meg, hogyan lehet képeket kinyerni, SVG‑t kinyerni
  a Wordből, és a DOCX‑et egyedi kezeléssel Markdown formátumba menteni.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: hu
og_description: Hogyan állítsunk be visszahívást a képek exportálásához a DOCX-ből
  Markdown konvertálásakor. Ez az útmutató megmutatja, hogyan lehet hatékonyan kinyerni
  a képeket és az SVG-ket.
og_title: Hogyan állítsunk be visszahívást a DOCX-ből képek exportálásához
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Hogyan állítsunk be visszahívást a DOCX-ből képek exportálásához
url: /hu/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állíts be visszahívást a képek exportálásához DOCX-ből

Gondolkodtál már azon, **hogyan állíts be visszahívást**, hogy **exportálhass képeket DOCX-ből**, miközben Markdownra konvertálsz? Nem vagy egyedül. Sok fejlesztő akad el, amikor az alapértelmezett konverzió az összes képet egy általános mappába helyezi, vagy még rosszabb, teljesen elveszíti az SVG grafikákat.

Ebben az útmutatóban végigvezetünk egy teljes, azonnal futtatható megoldáson, amely megválaszolja a “hogyan állíts be visszahívást” kérdést, bemutatja, **hogyan kell kinyerni a képeket**, és még a **SVG kinyerését a Wordből** is lefedi. A végére képes leszel **DOCX-et Markdownként menteni** egy egyedi elnevezési sémával minden képernyforrásra — manuális beavatkozás nélkül.

## Mit fogsz megtanulni

- Miért a visszahívás a legkcleanebb módja a képfájlnevek szabályozásának a konverzió során.  
- Hogyan kapcsolódj az Aspose.Words `MarkdownSaveOptions.resource_saving_callback`-hez.  
- Lépésről‑lépésre kód, amely **PNG**, **JPG**, **SVG**, és bármely más beágyazott erőforrást kinyer.  
- Tippek a névütközések, nagy fájlok és platformközi útvonalak sajátosságainak kezelésére.  

> **Pro tipp:** Ha már használod az Aspose.Words‑t egy nagyobb folyamatban, egyszerűen beillesztheted ezt a visszahívást anélkül, hogy a kód többi részét módosítanád.

![Hogyan állíts be visszahívást diagram](https://example.com/images/how-to-set-callback.png "hogyan állíts be visszahívást")

## Előfeltételek

- Python 3.8+ (a példa f‑stringeket használ, így a 3.6+ is megfelelő).  
- `aspose-words` csomag telepítve (`pip install aspose-words`).  
- Egy DOCX fájl, amely raszteres képeket **és** vektorgrafikákat (SVG) tartalmaz.  
- Alapvető ismeretek a Python függvényekről és a fájl I/O‑ról.

Ha ezek megvannak, merüljünk el.

## Hogyan állíts be visszahívást a képek exportálásához DOCX-ből

A megoldás központja egy **erőforrás‑mentő visszahívás**. Az Aspose.Words minden egyes kép vagy SVG esetén meghívja ezt a delegáltat, amikor a `document.save`‑et hívod. Egy `(new_name, data)` tuple visszaadásával meghatározod a fájlnevet és a bájt tartalmat.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Miért visszahívás?

Visszahívás nélkül az Aspose.Words `image1.png`, `image2.svg` stb. nevű fájlokat hoz létre, és a Markdown fájl mellett lévő mappába helyezi őket. Ez gyors demókhoz megfelelő, de a produkcióban gyakran szükség van:

1. **Determinista nevek** – hasznos verziókezeléshez vagy CDN közzétételhez.  
2. **Ütközés elkerülése** – két azonos eredeti névű kép nem írja felül egymást.  
3. **Egyedi mappaszerkezetek** – például minden eszközt a `/assets/docs/` alatt szeretnél.

A visszahívás teljes irányítást ad ezen három szempont felett.

## Képek exportálása DOCX-ből erőforrás visszahívással

Az alábbiakban a visszahívás implementációja látható. A bináris adatot hash-eli, hogy egyedi utótagot hozzon létre, megőrzi az eredeti fájlkiterjesztést, és visszaadja az új fájlnevet a nyers bájtokkal együtt.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Szélsőséges esetek kezelése

- **Nagy fájlok:** A SHA‑256 bármilyen méretnél működik; a hash memóriában számítódik, ezért figyelj a memória korlátokra, ha hatalmas PDF-eket dolgozol fel.  
- **Hiányzó kiterjesztések:** Egyes régebbi Word fájlok képeket tárolhatnak kifejezett kiterjesztés nélkül. Ebben az esetben az `extension` üres lesz; alapértelmezésként használhatod a `.bin`‑t vagy megvizsgálhatod az első néhány bájtot a formátum kitalálásához.  
- **Nem‑képes erőforrások:** A visszahívás minden külső erőforrásra meghívódik (pl. OLE objektumok). Ha csak a képekre/SVG‑kre vagy kíváncsi, szűrd le a `resource.type` alapján, mielőtt folytatnád.

## Hogyan nyerj ki képeket és SVG‑ket a Wordből

Most bekötjük a visszahívást a Markdown mentési csővezetékbe. A `MarkdownSaveOptions` objektum kifejezetten a `resource_saving_callback` tulajdonságot teszi elérhetővé erre a célra.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

A `resource_folder` beállítása opcionális, de gyakran hasznos. Ha kihagyod, a képek a Markdown fájl mellett kerülnek, ami elzsúfolhatja a projekt gyökerét.

### A dokumentum mentése

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

A szkript futtatásakor egy sor fájlt látsz majd, például:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

És a generált `output.md` képlinkeket tartalmaz majd, amelyek ezekre a pontos fájlnevekre mutatnak:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Ez a **képek kinyerésének** része működés közben — minden kép, legyen az raszteres vagy vektori, most egy külön, egyedi névvel ellátott eszköz.

## DOCX mentése Markdownként egyedi kézkezeléssel

Mindent egy helyre téve, itt a teljes szkript, amelyet beilleszthetsz egy `convert_docx_to_md.py` nevű fájlba:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Miért működik ez:**

- A `resource_callback` garantálja, hogy minden kép egyedi, reprodukálható nevet kap.  
- `resource_folder` rendezetten tartja a Markdown‑t az eszközök szétválasztásával.  
- Az `os.makedirs` hívások megvédnek a „mappa nem található” hibáktól, amikor a szkript egy új gépen fut.

## SVG kinyerése a Wordből – Mi a helyzet a vektorgrafikákkal?

Az SVG‑ket a visszahívás ugyanúgy kezeli, mint a PNG‑ket, mivel csak egy másik `resource`. Az egyetlen különbség, hogy egyes régebbi Word verziók SVG‑ket *OfficeArt* objektumként ágyazzák be, amelyet az Aspose.Words automatikusan raszteres PNG‑re konvertál, hacsak nem engedélyezed kifejezetten a **preserve SVG** jelzőt:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Add hozzá ezt a sort a mentés előtt, és a visszahívás `.svg` kiterjesztésű erőforrásokat kap, megőrizve a tiszta vektor adatot — tökéletes a reszponzív webdokumentumokhoz.

## Gyakori kérdések és buktatók

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha két kép azonos?** | A SHA‑256 hash azonos lesz, így a fájlnevek ütköznek. Ha mindkét példányra szükséged van, vedd bele az eredeti `resource.name`‑t a hash számításba (pl. `hash(resource.name + resource.data)`). |
| **Módosíthatom a mappát fájltípusonként?** | Igen. A `resource_callback`‑ben ellenőrizheted az `extension`‑t, és visszaadhatsz egy útvonalat, például `f"png/{new_name}"` raszteres képekhez és `f"svg/{new_name}"` vektorokhoz. |
| **Működik ez Linuxon/macOS-en?** | Természetesen. A kód az `os.path`‑t használja, amely elrejti az útvonalelválasztókat. Csak győződj meg róla, hogy a Aspose.Words licencfájl (`aspose.words.lic`) elérhető legyen, ha fizetős verziót használsz. |
| **Mi a helyzet a memóriahasználattal hatalmas dokumentumok esetén?** | A visszahívás minden erőforrásra a **teljes bájt tömböt** kapja, ami azt jelenti, hogy a teljes kép ideiglenesen a memóriában van. Több gigabájtos fájlok esetén érdemes lehet a visszahíváson belül a adatot lemezre streamelni a visszaadás helyett. |

## Következtetés

Most már tudod, **hogyan állíts be visszahívást** a képek kinyerésének szabályozásához, amikor **DOCX-et Markdownként mented**. A megközelítés lehetővé teszi a **képek exportálását DOCX-ből**, a **SVG kinyerését a Wordből**, és a Markdown tiszta és determinisztikus megtartását.

Egyetlen, önálló szkriptben lefedtük a dokumentum betöltését, egy erőforrás‑mentő visszahívás definiálását, a `MarkdownSaveOptions` konfigurálását, valamint a szélsőséges esetek, például névütközések és vektorgrafikák kezelését. Az eredmény egy egyedi névvel ellátott eszközkészlet a tökéletesen hivatkozott Markdown fájl mellett — készen áll statikus weboldalkészítők, dokumentációs csővezetékek vagy bármely munkafolyamat számára, amely tiszta, újrahasználható eszközöket igényel.

**Következő lépések?**  
- Próbáld meg összekapcsolni egy statikus weboldalkészítővel, például MkDocs‑szel, hogy automatikusan publikáld a Word‑alapú dokumentumokat.  
- Kísérletezz a `markdown_options.export_images_as_base64 = True` beállítással, ha inkább beágyazott képeket szeretnél külső fájlok helyett.  
- Mélyedj el az Aspose.Words további visszahívásaiban (pl. `document_saving_callback`), hogy magát a Markdown kimenetet is szabályozhasd.

További kérdéseid vannak arról, **hogyan nyerj ki képeket** más Office formátumokból, vagy segítségre van szükséged a visszahívás egy adott elnevezési konvencióra szabásához? Hagyj egy megjegyzést alább, és jó kódolást!

## Mit érdemes még megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan nevezd át a képeket DOCX‑ről Markdownra konvertáláskor](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Hogyan mentsd a Markdown‑t DOCX‑ből – Lépésről‑lépésre útmutató](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}