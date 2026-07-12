---
category: general
date: 2026-06-27
description: Naučte se, jak vložit obdélníkový tvar v Pythonu pomocí Aspose.Words,
  změnit barvu stínu, přidat vnější stín a aplikovat efekt stínu na tvar – vše v jednom
  tutoriálu.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: cs
og_description: Naučte se, jak vložit obdélníkový tvar v Pythonu, změnit barvu jeho
  stínu, přidat vnější stín a aplikovat efekt stínu na tvar pomocí Aspose.Words.
og_title: Jak vložit obdélníkový tvar v Pythonu – tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Jak vložit obdélníkový tvar v Pythonu – kompletní průvodce Aspose.Words
url: /cs/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit obdélníkový tvar v Pythonu – Kompletní průvodce Aspose.Words

Už jste se někdy zamýšleli **jak vložit obdélníkový tvar** do dokumentu Word pomocí Pythonu? Nejste jediní – mnoho vývojářů narazí na tento problém při automatizaci reportů nebo tvorbě šablon. Dobrou zprávou je, že Aspose.Words to dělá hračkou, a v tomto tutoriálu projdeme celý proces, od nakreslení obdélníku až po přidání elegantního vnějšího stínu.

Také se podíváme na **jak změnit barvu stínu**, **jak přidat vnější stín** a na poslední krok **aplikovat efekt stínu na tvar**. Na konci budete mít plně stylovaný obdélník, který můžete programově vložit do libovolného souboru .docx.

## Požadavky

- Python 3.8+ nainstalovaný na vašem počítači  
- Aspose.Words pro Python přes `pip install aspose-words`  
- Základní znalost skriptování v Pythonu (není potřeba hluboká znalost Word‑API)  

Pokud už máte vše připravené, skvěle – pustíme se do toho. Pokud ne, nejprve si stáhněte knihovnu; zbytek průvodce předpokládá, že import proběhne bez problémů.

## Jak vložit obdélníkový tvar s Aspose.Words pro Python

Prvním krokem je přesně to, co hlavní klíčové slovo slibuje: **jak vložit obdélníkový tvar**. Vytvoříme nový dokument, inicializujeme `DocumentBuilder` a vložíme obdélník na stránku.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Proč je to důležité:** Volání `insert_shape` je jádrem *jak vložit obdélníkový tvar*. Vrací objekt `Shape`, který můžete později upravovat – velikost, pozici, výplň, okraje, cokoliv. Všimněte si, že také nastavujeme `fill_color`; bez ní by se stín mohl sloučit s bílou stránkou a byl by těžko viditelný.

### Profesionální tip
Pokud potřebujete obdélník umístit na konkrétní místo, použijte `builder.move_to` před vložením, nebo upravte `rectangle.left` a `rectangle.top` po vytvoření.

## Změna barvy stínu tvaru

Nyní, když obdélník existuje v dokumentu, odpovíme na otázku **jak změnit barvu stínu**. Aspose.Words poskytuje objekt `ShadowEffect`, kde můžete nastavit vlastnost `color` na libovolnou RGB hodnotu.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Proč byste to chtěli:** Tmavý černý stín může být příliš drsný, zejména v dokumentech se světlým pozadím. Úprava barvy vám umožní sladit stín s firemní identitou nebo prostě dosáhnout jemnějšího vizuálního efektu.

### Okrajový případ
Pokud zapomenete nastavit `shadow.opacity`, výchozí hodnota je plně neprůhledná, což může způsobit, že stín vypadá jako pevný tvar. Vždy kombinujte změnu barvy s vhodnou úrovní průhlednosti.

## Přidání vnějšího stínového efektu

Další otázka, kterou mnoho lidí klade, je **jak přidat vnější stín**. Příznak `ShadowStyle.OUTER` říká Aspose.Words, aby vykreslil stín mimo obrys tvaru, nikoli uvnitř něj.

Výše uvedený úryvek kódu již používá `ShadowStyle.OUTER`, ale pro přehlednost si tuto volbu vyčleníme:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Pokud přepnete na `ShadowStyle.INNER`, stín se objeví *uvnitř* obdélníku, což je užitečné pro efekty embossingu. Pro většinu scénářů návrhu dokumentů poskytuje vnější styl přirozený vzhled padajícího stínu.

## Aplikace stínového efektu na váš tvar

Již jsme **aplikovali stínový efekt na tvar** přiřazením `rectangle.shadow = shadow`. Spojíme vše dohromady a uložíme dokument, abychom potvrdili, že efekt přetrvává.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Když otevřete `RectangleWithShadow.docx` v Microsoft Word, měli byste vidět světle modrý obdélník s jemným šedým vnějším stínem vrženým pod úhlem 45°. Stín bude mírně rozostřený a posunutý, přesně tak, jak jsme jej nakonfigurovali.

### Časté úskalí
- **Chybějící adresář:** `doc.save` vyvolá chybu, pokud složka neexistuje. Vytvořte ji nejprve nebo použijte `os.makedirs`.
- **Nesoulad verzí:** API pro stíny vyžaduje Aspose.Words 22.9+; starší verze stínová nastavení tiše ignorují.

## Kompletní funkční příklad

Níže je kompletní, připravený ke spuštění skript, který kombinuje všechny kroky. Zkopírujte jej do souboru pojmenovaného `rectangle_shadow.py` a spusťte pomocí `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Očekávaný výstup:** Word dokument (`RectangleWithShadow.docx`) obsahující jediný obdélník se šedým vnějším stínem. Otevřete jej ve Wordu a ověřte vizuální efekt.

## Často kladené otázky

| Otázka | Odpověď |
|----------|--------|
| *Mohu použít jiný typ tvaru?* | Samozřejmě – nahraďte `ShapeType.RECTANGLE` za `ShapeType.OVAL`, `ShapeType.TRIANGLE` atd., a stejná logika stínů bude fungovat. |
| *Co když potřebuji silnější okraj?* | Nastavte `rectangle.line_width = 2.0` (body) před aplikací stínu. |
| *Je možné stín animovat?* | Přímo v Aspose.Words ne – pro animaci byste museli exportovat do HTML/CSS. |
| *Funguje to na macOS?* | Ano – Aspose.Words je platformně nezávislý, pokud běží Python. |

## Závěr

Prošli jsme **jak vložit obdélníkový tvar**, ukázali **jak změnit barvu stínu**, vysvětlili **jak přidat vnější stín** a nakonec vám ukázali **jak aplikovat stínový efekt na tvar** pomocí Aspose.Words pro Python. Kompletní skript je připraven k nasazení do jakéhokoli automatizačního pipeline, což vám během několika sekund poskytne profesionálně vypadající obdélník s vylepšeným stínem.

Jste připraveni na další krok? Zkuste změnit barvu výplně, experimentovat s různými úhly `direction` nebo přidat na stránku více tvarů. Můžete také prozkoumat bohaté API pro formátování textu v Aspose.Words a kombinovat stíny se stylovaným textem – ideální pro poutavé reporty.

Pokud se vám tento tutoriál líbil, dejte mu palec nahoru, sdílejte ho s kolegy nebo zanechte komentář s vlastními variantami. Šťastné programování!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}