---
category: general
date: 2026-05-04
description: Naučte se, jak vytvořit obdélníkový tvar, jak přidat tvar se stíny, změnit
  barvu stínu, nastavit vzdálenost stínu a uložit dokument jako PDF pomocí Aspose.Words
  pro Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: cs
og_description: Vytvořte obdélníkový tvar pomocí Aspose.Words pro Python, naučte se,
  jak přidat tvar, změnit barvu stínu, nastavit vzdálenost stínu a uložit dokument
  jako PDF.
og_title: Vytvořte obdélníkový tvar – přidejte stín, změňte barvu a uložte jako PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Vytvořte obdélníkový tvar v Pythonu – Kompletní průvodce přidáváním stínů a
  ukládáním do PDF
url: /cs/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru – Kompletní tutoriál pro vývojáře Pythonu

Už jste někdy potřebovali **create rectangle shape** v dokumentu Word a přemýšleli, jak mu dát vylepšený stín? Možná vytváříte generátor zpráv a vizuální dokonalost je důležitá—obzvláště když je konečný výstup PDF. Dobrá zpráva? S Aspose.Words pro Python můžete nejen **how to add shape**, ale také doladit každou vlastnost stínu, od barvy po vzdálenost, a poté **save document as pdf** v jednom plynulém toku.

V tomto průvodci projdeme celý proces krok za krokem. Uvidíte přesný kód, který můžete zkopírovat‑vložit, pochopíte *proč* je každý řádek důležitý, a získáte několik tipů pro řešení okrajových případů (jako jsou průhledné stíny nebo nestandardní DPI). Na konci budete schopni **create rectangle shape**, přizpůsobit jeho stín a exportovat ostrý PDF bez potíží.

## Požadavky

- Python 3.8+ nainstalovaný na vašem počítači.  
- Aspose.Words pro Python pomocí `pip install aspose-words`.  
- Základní znalost objektově orientovaného Pythonu (nic složitého).  

Pokud již máte nastavené virtuální prostředí, stačí spustit instalační příkaz a můžete pokračovat.

## Krok 1: Inicializace dokumentu a builderu

Než budete moci **how to add shape**, potřebujete prázdný dokument, se kterým budete pracovat. Třída `Document` představuje celý soubor a `DocumentBuilder` je váš štětec.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Proč je to důležité:* `Document` obsahuje všechny sekce, stránky a zdroje. `DocumentBuilder` vám poskytuje plynulé API pro vkládání obsahu přesně tam, kde ho potřebujete—představte si to jako kurzor ve word procesoru.

## Krok 2: Vložení obdélníkového tvaru

Nyní skutečně **how to add shape**. Metoda `insert_shape` potřebuje typ tvaru a jeho rozměry (v bodech). Zde vybíráme obdélník 200 × 100 pt a nastavíme mu světle modrou výplň.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Tip:* Pokud potřebujete, aby se tvar zarovnal s existujícím textem, použijte `builder.move_to` před vložením, nebo po vytvoření upravte vlastnosti `left`/`top`.

## Krok 3: Zapnutí stínu

Tvar bez stínu vypadá plochý. Pro **set shadow distance** a zviditelnění efektu získáte formát stínu a povolíte jej.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Proč tento krok:* Formát stínu je samostatný objekt; přepnutí `visible` je první věc, kterou musíte udělat, jinak jsou všechny ostatní vlastnosti stínu ignorovány.

## Krok 4: Stylování stínu – Barva, Rozostření, Vzdálenost, Směr

Zde se děje kouzlo. **change shadow color**, upravíme poloměr rozostření, nastavíme, jak daleko je stín od obdélníku, a otočíme jej o 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Vysvětlení každé vlastnosti:*

| Vlastnost | Co dělá | Typické hodnoty |
|----------|--------------|----------------|
| `style` | Určuje, zda je stín *inner* nebo *outer*. | `OUTER` (nejčastější) |
| `blur_radius` | Řídí měkkost; vyšší = rozmazanější okraje. | 0–20 px je obvyklé |
| `distance` | Jak daleko je stín odsazen od tvaru. | 0–10 pt pro jemný, >10 pro dramatický |
| `direction` | Úhel světelného zdroje, měřený po směru hodinových ručiček od osy x. | 0‑360° |
| `color` | Odstín stínu. | Jakákoliv `aw.Color` (např. `gray`, `dark_red`) |

*Okrajový případ:* Pokud nastavíte `distance` na `0`, stín bude ležet přímo pod tvarem, což efektivně skryje výplň tvaru. Udržujte ho nad `0` pro viditelný posun.

## Krok 5: Uložení dokumentu jako PDF

Nakonec **save document as pdf**. Aspose.Words automaticky rasterizuje stín, takže PDF vypadá přesně jako zobrazení ve Wordu.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Proč PDF?* PDF zachovávají rozvržení napříč platformami, což je činí ideálními pro zprávy, faktury nebo jakýkoli tisknutelný výstup.

![Vytvořit obdélníkový tvar se stínem](https://example.com/images/rectangle-shadow.png){: .align-center alt="vytvořit obdélníkový tvar se stínem příklad"}

*Obrázek výše ukazuje finální výstup PDF – světle modrý obdélník s měkkým šedým vnějším stínem, přesně tak, jak jsme nakonfigurovali.*

## Časté otázky a varianty

### Co když potřebuji **transparent** stín?

Nastavte alfa kanál na barvu stínu:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Mohu použít stejný stín na více tvarů?

Ano. Extrahujte `ShadowFormat` z jednoho tvaru a přiřaďte jej druhému:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Jak změním stín pro **different shape type**?

Všechny typy tvarů sdílejí stejné vlastnosti `ShadowFormat`, takže můžete znovu použít stejný konfigurační blok—stačí nahradit `ShapeType.RECTANGLE` za `ShapeType.OVAL`, `ShapeType.TRIANGLE` atd.

### Co takhle **high‑resolution PDFs** pro tisk?

Zadejte `PdfSaveOptions` s vyšším DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Shrnutí

Probrali jsme vše, co potřebujete k **create rectangle shape**, **how to add shape**, přizpůsobení **shadow colour**, **set shadow distance**, a nakonec **save document as pdf**. Kompletní, spustitelný skript vypadá takto:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Spusťte skript, otevřete vzniklý `ShadowedShape.pdf` a uvidíte ostrý obdélník s jemným šedým stínem—přesně to, co očekáváte od profesionálně formátované zprávy.

## Co dál?

- **Prozkoumejte další typy tvarů** (`ShapeType.OVAL`, `ShapeType.LINE`) pro obohacení vašich dokumentů.  
- **Kombinujte více stínů** vrstvením tvarů; můžete dokonce vytvořit efekt „záře“ pomocí vnitřního stínu s jasnou barvou.  
- **Automatizujte dávkové zpracování**: projděte kolekci řádků dat, vygenerujte tvar pro každý řádek a vše sloučte do jednoho PDF.  
- **Integrujte s dalšími knihovnami Aspose** (např. Aspose.Slides), pokud potřebujete exportovat stejnou vizualizaci do PowerPointu.

Nebojte se experimentovat—změňte `blur_radius`, pohrávejte si s `direction`, nebo vyměňte `gray` za barvu specifickou pro vaši značku. API je dostatečně flexibilní, takže několik úprav může dramaticky změnit vizuální dopad.

Máte otázky nebo složitý scénář? Zanechte komentář níže nebo napište na fóra komunity Aspose. Šťastné kódování a užívejte si ty krásně stínované obdélníky!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}