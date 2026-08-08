---
category: general
date: 2026-08-07
description: Nakreslete obdélník v PDF pomocí Aspose.Words pro Python a naučte se,
  jak přidat stín k tvaru, nakonfigurovat stín tvaru a uložit dokument jako PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: cs
lastmod: 2026-08-07
og_description: Vykreslete obdélník v PDF pomocí Aspose.Words pro Python. Tento tutoriál
  ukazuje, jak přidat stín k tvaru, konfigurovat stín tvaru a uložit dokument jako
  PDF pro profesionální generování dokumentů.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Nakreslete obdélník v PDF pomocí Aspose.Words pro Python – průvodce
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Nakreslete obdélník v PDF pomocí Aspose.Words pro Python
url: /cs/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nakreslit obdélník v PDF pomocí Aspose.Words pro Python

Pokud potřebujete **nakreslit obdélník v PDF** při práci v Pythonu, tento průvodce vám poskytne kompletní, připravené řešení. Uvidíte přesně, jak **přidat stín k tvaru**, nakonfigurovat tento stín a nakonec **uložit dokument jako PDF** pro distribuci nebo archivaci.

Vytvoření obdélníku se stínem je běžná potřeba pro zprávy, faktury nebo vizuální anotace. Na konci tohoto tutoriálu budete mít jeden skript, který vytvoří PDF obsahující obdélník s realistickým stínem, a pochopíte, jak upravit velikost, barvu a posunutí tak, aby vyhovovaly jakémukoli designu.

## Požadavky

* Python 3.8+ nainstalován.
* Balíček Aspose.Words for Python via .NET (`aspose-words`) – nainstalujte pomocí:

```bash
pip install aspose-words
```

* Oprávnění k zápisu do složky, kam chcete PDF uložit.

Žádné další knihovny nejsou vyžadovány; Aspose.Words interně zajišťuje vytváření tvarů, konfiguraci stínu a export do PDF.

## Krok 1: Vytvořit nový prázdný dokument (nakreslit obdélník v PDF – inicializace)

Prvním krokem je vytvořit instanci objektu `Document`. Tento objekt představuje celý PDF soubor a poskytuje kontejner pro sekce, odstavce a tvary.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Proč je to důležité:** Aspose.Words považuje generování PDF za konverzi z modelu Word dokumentu, takže začínáme s `Document`, i když je konečný výstup PDF.

## Krok 2: Vložit tvar obdélníku do těla dokumentu

Obdélník je konkrétní `ShapeType`. Přidáme jej do těla první sekce, což při uložení jako PDF automaticky vytvoří novou stránku.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Vysvětlení:** Vlastnosti `width` a `height` řídí vizuální velikost tvaru v PDF. Přidání textu usnadňuje ověření obdélníku během testování.

## Krok 3: Přidat stín k tvaru – povolit a přizpůsobit

Nyní zapneme efekt stínu a jemně doladíme jeho vzhled. Zde vstupuje do hry klíčové slovo **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Proč konfigurovat stín tvaru?** Úprava `blur`, `distance` a `angle` vám umožní simulovat realistické osvětlení, což zlepšuje čitelnost a vizuální hierarchii v generovaných PDF.

## Krok 4: Uložit dokument jako PDF – finální výstup

S definovaným obdélníkem a jeho stínem je posledním krokem exportovat Word dokument do PDF. Tím splníme požadavek **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Když otevřete `shadow_rectangle.pdf`, uvidíte jedinou stránku obsahující šedě ohraničený obdélník s názvem „Shadow demo“ a ostrý, diagonální stín.

### Očekávaný výstup

* PDF soubor pojmenovaný `shadow_rectangle.pdf`.
* Jedna stránka s obdélníkem 200 pt × 100 pt.
* Viditelný stín posunutý o 5 pt pod úhlem 45°, rozostřený o 8 pt.

## Krok 5: Prozkoumat varianty a okrajové případy (volitelné)

Níže jsou běžné úpravy, které můžete v reálných projektech potřebovat:

| Varianta | Ukázka kódu | Kdy použít |
|-----------|--------------|-------------|
| **Různý typ tvaru** (např. elipsa) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Pro zakulacenou grafiku nebo odznaky |
| **Vlastní barva stínu** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Když je potřeba šedý nebo značkový stín |
| **Více tvarů** | Repeat the shape‑creation block and adjust `left`/`top` properties | Pro tvorbu složitých diagramů |
| **Žádný text uvnitř tvaru** | Omit `rectangle.text = "..."` | Když je tvar čistě dekorativní |
| **Vyšší DPI výstup** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Pro PDF připravené k tisku |

**Pro tip:** Vždy nastavte `shadow.visible = True` před úpravou dalších vlastností; jinak jsou změny tiše ignorovány.

## Kompletní skript – zkopírujte, vložte a spusťte

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Spusťte skript z terminálu nebo IDE. Nahraďte `YOUR_DIRECTORY` skutečnou cestou ke složce, například `"/tmp"` nebo `"C:\\Users\\Me\\Documents"`.

## Závěr

Nyní víte, jak **nakreslit obdélník v PDF** pomocí Aspose.Words pro Python, **přidat stín k tvaru**, **konfigurovat stín tvaru** a **uložit dokument jako PDF**. Kompletní příklad ukazuje každý krok od vytvoření dokumentu po finální export a volitelné varianty ukazují, jak přizpůsobit kód pro složitější scénáře.

Další kroky, které můžete prozkoumat:

* Přidání dalších typů tvarů (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Použití gradientových výplní nebo okrajů pro zvýšení vizuálního dojmu.
* Použití `PdfSaveOptions` k vložení fontů nebo řízení komprese obrázků.

Neváhejte experimentovat s parametry, aby odpovídaly vaší značce nebo designovým směrnicím. Šťastné skriptování PDF!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}