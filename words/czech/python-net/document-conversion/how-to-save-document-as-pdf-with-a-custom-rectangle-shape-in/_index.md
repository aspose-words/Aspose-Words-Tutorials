---
category: general
date: 2026-10-07
description: Naučte se, jak uložit dokument jako PDF a přitom přidat obdélníkový tvar
  a vlastní stín pomocí Aspose.Words pro Python. Kód krok za krokem je zahrnut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: cs
lastmod: 2026-10-07
og_description: Uložte dokument jako PDF s vlastním obdélníkovým tvarem pomocí Aspose.Words
  pro Python. Sledujte celý příklad, jak kreslit, stylovat a exportovat Word do PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Uložte dokument jako PDF s obdélníkovým tvarem – kompletní průvodce Pythonem
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Jak uložit dokument jako PDF s vlastním obdélníkovým tvarem v Pythonu
url: /cs/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uložit dokument jako PDF s vlastním obdélníkovým tvarem v Pythonu

Pokud potřebujete **save document as PDF** při přidávání vlastních grafik, tento návod vám ukáže, jak na to. Provedeme vás vytvořením prázdného souboru Word, **drawing a rectangle shape**, nastavením jeho velikosti, aplikací viditelného stínu a nakonec **export Word to PDF** pomocí knihovny Aspose.Words for Python.

Výsledkem bude PDF, které obsahuje perfektně umístěný obdélník, připravený pro zprávy, faktury nebo jakýkoli scénář automatizace dokumentů. Nepotřebujete žádné externí nástroje – stačí Python a balíček Aspose.Words.

## Co budete potřebovat

| Požadavek | Proč je důležité |
|-------------|----------------|
| Python 3.8+ | API Aspose.Words for Python cílí na moderní interpretery. |
| `aspose-words` package (`pip install aspose-words`) | Poskytuje jmenný prostor `aw` používaný v ukázkovém kódu. |
| Basic familiarity with Python and object‑oriented programming | Tutoriál manipuluje s objekty jako `Document` a `Shape`. |
| Write permission to a folder where the PDF will be saved | `save document as pdf` krok zapisuje soubor na disk. |

> **Tip:** Použijte virtuální prostředí (`python -m venv venv`) pro izolaci závislostí.

## Jak uložit dokument jako PDF s obdélníkovým tvarem

Níže je kompletní, spustitelný příklad. Každý krok je vysvětlen, abyste pochopili **why**, proč akci provádíme, ne jen **what**, co kód dělá.

### Krok 1: Inicializace nového prázdného dokumentu

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Vytvoření nového objektu `Document` vám poskytne čistou kolekci stránek. Můžete také načíst existující *.docx*, pokud chcete později **export Word to PDF**, ale začátek s prázdným dokumentem udržuje příklad zaměřený.

### Krok 2: Přidání obdélníkového tvaru do dokumentu

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Krok `add rectangle shape` používá `ShapeType.RECTANGLE`. Připojením tvaru k odstavci Aspose.Words ví, kde jej vykreslit v konečném PDF.

### Krok 3: Nastavení rozměrů obdélníku

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Nastavení explicitních **rectangle dimensions** zajišťuje, že tvar vypadá konzistentně napříč platformami. Můžete také použít pomocníky `convert_to_inches`, pokud dáváte přednost imperiálním jednotkám.

### Krok 4: (Volitelné) Aplikace viditelného vlastního stínu

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Stín způsobí, že obdélník v PDF vynikne. Příznak `shadow.visible` je povinný; bez něj ostatní vlastnosti nemají žádný efekt.

### Krok 5: Uložení dokumentu jako PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Volání `document.save` s příponou **.pdf** automaticky **save document as pdf** pomocí vestavěného PDF rendereru Aspose.Words. Není potřeba žádných dalších kroků konverze, což je důvod, proč je tato metoda doporučeným způsobem **export Word to PDF**.

> **Proč to funguje:** Aspose.Words zapisuje rozvržení dokumentu, včetně obdélníku a jeho stínu, přímo do PDF proudu. Proces je bezztrátový a zachovává vektorovou kvalitu.

## Kompletní zdrojový kód (jediný skript)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Spuštěním tohoto skriptu vznikne `shadow_rectangle.pdf`, který vypadá takto:

![Diagram vygenerovaného PDF zobrazující obdélníkový tvar po uložení dokumentu jako PDF](placeholder-image.png)

*PDF obsahuje jednu stránku s černě stínovaným obdélníkem uprostřed dokumentu.*

## Časté otázky a okrajové případy

| Question | Answer |
|----------|--------|
| **Mohu umístit obdélník na konkrétní místo?** | Ano. Nastavte `rectangle.left` a `rectangle.top` (v bodech) před uložením. |
| **Co když potřebuji více tvarů?** | Vytvořte další objekty `Shape`, nakonfigurujte je a připojte je ke stejnému nebo různým odstavcům. |
| **Ovlivňuje stín velikost PDF?** | Pouze mírně; stín je uložen jako vektorová metadata, nikoli jako rastrový obrázek. |
| **Mohu to použít k převodu existujících *.docx* souborů?** | Rozhodně. Nahraďte `aw.Document()` za `aw.Document("input.docx")` a zbytek kroků zůstane beze změny. |
| **Existuje způsob, jak změnit barvu výplně obdélníku?** | Nastavte `rectangle.fill_color = aw.drawing.Color.light_blue` (nebo libovolnou `Color`, kterou preferujete). |

## Další kroky

Nyní, když víte, jak **save document as PDF** s vlastním obdélníkem, můžete zkoumat:

* **Export Word to PDF** s hlavičkami, patičkami a čísly stránek.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) pomocí stejné třídy `Shape`.  
* **Batch process** složku souborů Word, aplikací stejného obdélníkového překryvu na každý.  

Tyto rozšíření následují stejný vzor: vytvořte tvar, nakonfigurujte jeho vlastnosti a **save document as pdf**.

---

**Shrnutí:** Tento tutoriál vám ukázal, jak **save document as PDF** při **add rectangle shape**, **set rectangle dimensions**, a aplikaci vlastního stínu pomocí Aspose.Words for Python. Kompletní skript je připraven ke zkopírování, spuštění a přizpůsobení vašim vlastním pipeline automatizace dokumentů. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar, přidat stín a uložit PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Přidat obdélník do PDF pomocí Aspose.Words – krok za krokem průvodce](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Uložit dokument jako PDF s Aspose.Words – kompletní C# průvodce](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}