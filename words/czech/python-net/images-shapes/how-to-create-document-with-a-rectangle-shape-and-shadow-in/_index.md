---
category: general
date: 2026-10-04
description: Jak vytvořit dokument v Pythonu a přidat stín k tvaru pomocí Aspose.Words.
  Naučte se nastavit barvu stínu, vložit obdélníkový tvar a přizpůsobit vnější stín.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: cs
lastmod: 2026-10-04
og_description: Jak vytvořit dokument v Pythonu a přidat stín k tvaru. Tento průvodce
  vám ukáže, jak nastavit barvu stínu, vložit obdélníkový tvar a aplikovat vnější
  stín pomocí Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Jak vytvořit dokument s obdélníkovým tvarem a stínem v Pythonu
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Jak vytvořit dokument s obdélníkovým tvarem a stínem v Pythonu
url: /cs/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit dokument s obdélníkovým tvarem a stínem v Pythonu

Pokud potřebujete **jak vytvořit dokument**, který obsahuje stylovaný obdélník, tento průvodce poskytuje kompletní řešení. Uvidíte, jak **přidat stín k tvaru**, nastavit barvu stínu a ovládat jeho posun a rozostření – vše pomocí Aspose.Words for Python. Na konci tutoriálu můžete vygenerovat soubor `.docx`, který vypadá profesionálně a je připraven k distribuci.

Níže uvedené kroky pokrývají vše od instalace knihovny po přizpůsobení vzhledu stínu. Není potřeba žádná externí dokumentace; kód je připraven ke zkopírování, spuštění a úpravě pro vaše vlastní projekty. Také se naučíte, jak **vložit obdélníkový tvar**, vybrat **vnější styl stínu** a řešit běžné problémy, jako jsou neviditelné stíny nebo nesprávná nastavení obtékání.

## Požadavky

* Nainstalovaný Python 3.8 nebo novější.
* Aktivní licence Aspose.Words for Python (nebo bezplatný evaluační klíč).
* Základní znalost skriptování v Pythonu.
* Přístup k umístění v souborovém systému, kam bude vygenerovaný dokument uložen.

Můžete nainstalovat SDK pomocí pip:

```bash
pip install aspose-words
```

## Krok 1: Naimportujte knihovnu a vytvořte nový prázdný dokument

Vytvoření nového dokumentu je první akcí v jakémkoli scénáři automatizace Wordu. Konstruktor `aw.Document()` vám poskytne prázdný soubor, který můžete naplnit textem, obrázky nebo tvary.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Objekt `DocumentBuilder` usnadňuje vkládání obsahu. Sleduje aktuální pozici kurzoru, takže můžete přidávat prvky sekvenčně, aniž byste museli ručně spravovat sekce.

## Krok 2: Vložte obdélníkový tvar požadované velikosti

Obdélníkový tvar funguje jako kontejner pro vizuální prvky. Můžete definovat jeho šířku a výšku v bodech (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

V tomto okamžiku tvar nemá žádné vizuální stylování, takže se zobrazuje jako jednoduchý obrys. Další kroky mu přidají hloubku a barvu.

## Krok 3: Nastavte tvar, aby plynule proudil inline s okolním textem

Když je tvar **inline**, chová se jako znak v odstavci. To zajišťuje, že obdélník zůstane tam, kde jej v rozložení dokumentu očekáváte.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Pokud dáváte přednost tomu, aby tvar plaval nad textem, můžete použít `WrapType.SQUARE` nebo `WrapType.TOP_BOTTOM`, ale pro většinu zpráv inline tvar udržuje rozložení předvídatelné.

## Krok 4: Zviditelněte stín a vyberte jeho barvu

Stín, který není viditelný, nepřináší žádný vizuální přínos. Příznak `visible` aktivuje efekt a vlastnost `color` určuje jeho odstín. Použití černé barvy poskytuje klasickou, jemnou hloubku.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Můžete nahradit `aw.drawing.Color.black` libovolnou jinou barvou, například `aw.drawing.Color.gray` nebo vlastní RGB hodnotou (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Krok 5: Definujte posun a rozostření stínu, aby získal hloubku

Posun určuje, jak daleko je stín posunut od tvaru, zatímco poloměr rozostření změkčuje hrany. Malé hodnoty vytvářejí ostrý stín; větší hodnoty produkují měkčí vzhled.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimentujte s těmito čísly, aby odpovídala vašim designovým směrnicím. Pro výrazný vržený stín můžete zvýšit jak posun, tak rozostření.

## Krok 6: Vyberte vnější styl stínu

Aspose.Words nabízí několik stylů stínů, jako `INNER`, `OUTER` a `PERSPECTIVE`. **Vnější** styl umisťuje stín mimo okraj tvaru, což je ideální pro čistý, profesionální vzhled.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Pokud potřebujete dramatický efekt, vyzkoušejte `ShadowStyle.PERSPECTIVE` – přidá trojrozměrný náklon.

## Krok 7: Uložte dokument se stínovaným tvarem

Uložení dokončí soubor a zapíše veškeré formátování na disk. Vyberte adresář, do kterého máte oprávnění zapisovat, a dejte souboru popisný název.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Spuštěním skriptu získáte soubor Word, který obsahuje obdélník s viditelným, barevným stínem. Otevřete soubor v Microsoft Word nebo LibreOffice a ověřte výsledek.

## Kompletní spustitelný příklad

Níže je kompletní skript, který zahrnuje všechny zmíněné kroky. Zkopírujte kód do souboru s názvem `create_shadowed_shape.py` a spusťte jej pomocí `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Očekávaný výstup**

Když otevřete `ShapeWithShadow.docx`, uvidíte jediný obdélník uprostřed stránky. Obdélník je doprovázen jemným černým stínem posunutým směrem dolů a vpravo, mírně rozostřeným pro vytvoření hloubky. Stín respektuje vnější styl, takže neprotíná vnitřek obdélníku.

## Časté otázky a okrajové případy

### Proč se stín někdy zobrazuje neviditelně?

Stín se vykreslí pouze tehdy, pokud je `shadow.visible` nastaven na `True` **a** `wrap_type` tvaru umožňuje jeho zobrazení. Inline tvar funguje spolehlivě; plovoucí tvary mohou vyžadovat další úpravy rozložení.

### Jak mohu změnit barvu stínu tak, aby odpovídala firemní paletě?

Nahradit `aw.drawing.Color.black` vlastní RGB hodnotou:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Co když potřebuji, aby se tvar zobrazoval za textem?

Nastavte typ obtékání na `WrapType.BEHIND` a v případě potřeby upravte `z_order_position`. Mějte na paměti, že některé prohlížeče mohou vykreslovat tvary za textem odlišně.

### Mohu použít stejná nastavení stínu na více tvarů?

Ano. Vytvořte pomocnou funkci, která nastaví stín, a zavolejte ji pro každý vložený tvar. To podporuje opětovné použití kódu a zajišťuje konzistentní stylování.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Závěr

Nyní víte, **jak vytvořit dokument**, který obsahuje obdélníkový tvar s přizpůsobeným stínem pomocí Aspose.Words for Python. Tutoriál pokryl vkládání obdélníku, nastavení tvaru jako inline, aktivaci stínu, nastavení jeho barvy, posunu, rozostření a stylu a nakonec uložení souboru.

Odtud můžete zkoumat související témata, jako **přidat stín k tvaru** pro jiné typy tvarů, **nastavit barvu stínu** dynamicky na základě dat, nebo **jak přidat stín** k obrázkům a textovým rámečkům. Experimentujte s různými rozměry, barvami a styly stínů, aby odpovídaly vašim firemním směrnicím nebo designovému systému.

Jste připraveni automatizovat další dokumenty Word? Zkuste přidat tabulky, záhlaví nebo dynamický obsah – každý krok staví na stejných principech předvedených zde. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar, přidat stín a uložit jako PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Vytvořit prázdný dokument Word s obdélníkovým tvarem se stínem – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Jak spravovat proměnné dokumentu s Aspose.Words v Pythonu: Kompletní průvodce](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}