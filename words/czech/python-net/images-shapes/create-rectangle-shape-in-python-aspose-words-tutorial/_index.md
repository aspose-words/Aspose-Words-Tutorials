---
category: general
date: 2026-06-21
description: Vytvořte obdélníkový tvar v Pythonu pomocí Aspose.Words. Naučte se, jak
  přidat stín k tvaru, nastavit barvu výplně tvaru a během několika minut uložit dokument
  jako PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: cs
og_description: Vytvořte obdélníkový tvar v Pythonu s Aspose.Words. Tento průvodce
  ukazuje, jak přidat stín k tvaru, nastavit barvu výplně tvaru a uložit dokument
  jako PDF.
og_title: Vytvořte obdélníkový tvar v Pythonu – tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Vytvořte obdélníkový tvar v Pythonu – tutoriál Aspose.Words
url: /cs/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru v Pythonu – tutoriál Aspose.Words

Už jste se někdy zamýšleli **jak vytvořit obdélníkový tvar** ve Word dokumentu během programování v Pythonu? Nejste v tom sami. Mnoho vývojářů narazí na problém, když potřebují rychlý vizuální prvek – například barevné políčko s jemným stínem – a pak celý výstup exportují jako PDF.  

V tomto průvodci projdeme kompletním, spustitelným příkladem, který **vytvoří obdélníkový tvar**, **nastaví barvu výplně tvaru**, **přidá stín k tvaru** a nakonec **uloží dokument jako PDF**. Žádné vágní odkazy, jen konkrétní kód, který můžete dnes zkopírovat‑vložit a spustit.

## Co budete potřebovat

Než se pustíme do detailů, ujistěte se, že máte na svém počítači následující:

- Python 3.8 nebo novější (syntaxe, kterou používáme, funguje na jakékoli nedávné verzi).
- Aktivní licence Aspose.Words for Python nebo bezplatná zkušební verze (knihovna je čistě Python, nevyžaduje COM interop).
- Textový editor nebo IDE, ve kterém se cítíte pohodlně – VS Code funguje skvěle, ale stačí jakýkoli.

To je vše. Žádné těžké frameworky, žádné další závislosti na úrovni OS. Pojďme na to.

## Krok 1: Instalace Aspose.Words for Python

Nejprve. Pokud jste tak ještě neučinili, stáhněte balíček z PyPI:

```bash
pip install aspose-words
```

Proč je tento krok důležitý: Aspose.Words poskytuje třídy `Document` a `DocumentBuilder`, na které se budeme spoléhat. Bez knihovny neexistují žádné pozdější volání – například `insert_shape` – a skript by spadl ještě před tím, než nakreslí čáru.

> **Tip:** Udržujte virtuální prostředí přehledné. Spusťte `python -m venv .venv && source .venv/bin/activate` před instalací, aby knihovna zůstala izolovaná od systémových balíčků.

## Krok 2: Vytvoření nového dokumentu a DocumentBuilderu

Nyní **vytvoříme obdélníkový tvar** – ale nejprve potřebujeme prázdné plátno.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Objekt `Document` představuje celý soubor, zatímco `DocumentBuilder` je praktický pomocník, který ví, kde je kurzor, a může vkládat elementy na dané místo. Přemýšlejte o builderu jako o peru, který píše na stránku.

## Krok 3: Vložení obdélníkového tvaru

Zde se odehrává hlavní akce. **Vytvoříme obdélníkový tvar** s pevnou šířkou a výškou a umístíme jej na stránku.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Proč obdélník? Je to nejjednodušší tvar, který nám stále umožňuje ukázat výplňové barvy a stíny. Pokud později potřebujete kruh nebo hvězdu, stačí zaměnit `ShapeType.RECTANGLE` za jinou hodnotu výčtu.

## Krok 4: Nastavení barvy výplně tvaru

Bílá krabička není moc zajímavá, takže **nastavíme barvu výplně tvaru** na něco jemného – světle modrá dobře funguje v reportech.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Můžete použít jakýkoli předdefinovaný člen `aw.Color` (`red`, `green`, `dark_gray` atd.) nebo předat RGB trojici (`aw.Color.from_argb(255, 30, 144, 255)`). Barva výplně je to, co uživatel vidí před aplikací stínu nebo okraje.

## Krok 5: Přidání stínu k tvaru

Nyní k vizuálnímu vylepšení: **přidáme stín k tvaru**. Stíny dodávají hloubku a způsobí, že obdélník na stránce „vyskočí“.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Jak přidat stín**? Výše uvedený kód to přesně dělá, ale rozebráme si, proč každá vlastnost má význam:

- `visible` – zapíná nebo vypíná efekt.
- `color` – určuje odstín; tmavě šedá napodobuje přirozené osvětlení.
- `blur` – vyšší hodnoty vytvářejí měkčí okraj.
- `offset_x` / `offset_y` – posouvají stín od tvaru; upravte je pro simulaci různých úhlů světla.
- `transparency` – 0 je neprůhledný, 1 je neviditelný; 0.2 dává jemný dojem.
- `type` – `OUTER` vrhá stín mimo tvar, zatímco `INNER` by ho vložil dovnitř.

Pokud potřebujete dramatický „drop shadow“, zvyšte `blur` na 10‑15 a posuňte `offset_x`/`offset_y` na 6‑8.

## Krok 6: Uložení dokumentu jako PDF

Všechen ten výstup je zbytečný, pokud ho neuložíme **jako PDF** a nesdílíme. Aspose.Words to zvládne jedním řádkem:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Proč PDF? PDF zachovává rozvržení napříč platformami, což je ideální pro reporty, faktury nebo jakýkoli tisknutelný materiál. Metoda `save` automaticky rozpozná příponu souboru a vybere správný formát – jen se ujistěte, že cesta končí na `.pdf`.

### Očekávaný výsledek

Otevřete vzniklý soubor `ShapeWithShadow.pdf` a měli byste vidět světle modrý obdélník umístěný uprostřed blízko horní části první stránky, s jemným tmavě šedým stínem posunutým mírně doprava a dolů. Hrany tvaru jsou ostré, stín je decentní a velikost souboru je obvykle pod 100 KB.

## Bonus: Ladění stínů – odpovědi na „jak přidat stín“

Možná se ptáte, *„Mohu změnit směr stínu, aniž bych posunul tvar?“* Rozhodně. Pozice stínu je nezávislá na souřadnicích tvaru; stačí upravit `offset_x` a `offset_y`. Kladné hodnoty posunou stín doprava/dolů, záporné hodnoty ho posunou doleva/nahoru. Pro světlo ze špičky vlevo nahoře použijte `offset_x = -3` a `offset_y = -3`.

Další častá otázka: *„Co když potřebuji na stejném tvaru více stínů?“* Aspose.Words podporuje pouze jeden stín na tvar. Pokud potřebujete vrstvené efekty, vytvořte duplicitní tvar, posuňte ho mírně a každému přiřaďte jiný stín. Je to trochu hack, ale funguje.

## Kompletní skript – připravený ke spuštění

Níže je kompletní, samostatný skript. Zkopírujte jej do souboru pojmenovaného `create_rectangle_with_shadow.py` a spusťte příkazem `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Poznámka:** Nahraďte `YOUR_DIRECTORY` absolutní nebo relativní cestou, která na vašem počítači existuje. Pokud složka neexistuje, Python vyvolá `FileNotFoundError`.

## Časté problémy a jak se jim vyhnout

| Problém | Proč se vyskytuje | Řešení |
|---------|-------------------|--------|
| Stín se nezobrazuje | `shadow.visible` zůstalo ve výchozím nastavení `False` | Ujistěte se, že `shadow.visible = True` |
| Tvar je neviditelný | Výplň nastavena na `aw.Color.transparent` nebo `None` | Použijte plnou barvu, např. `aw.Color.light_blue` |
| PDF je prázdné | Zapomněli jste zavolat `doc.save` nebo jste uložili s nesprávnou příponou | Zavolejte `doc.save("output.pdf")` a ověřte cestu |
| Runtime error `ImportError` | Aspose.Words není nainstalován nebo používáte špatné virtuální prostředí | Spusťte `pip install aspose-words` v aktivním venv |

## Další kroky – prozkoumejte další tvary a formátování

Nyní, když ovládáte **vytvoření obdélníkového tvaru**, můžete:

- Nahradit `ShapeType.RECTANGLE` za `ShapeType.ELLIPSE` nebo `ShapeType.PENTAGON` a experimentovat s dalšími geometriemi.
- Přidat text uvnitř tvaru pomocí `builder.move_to(rectangle.absolute_position)` a následně `builder.writeln("Hello World")`.
- Spojit více tvarů do skupiny pomocí `group = aw.drawing.GroupShape(doc)` pro složitější diagramy.
- Exportovat do dalších formátů, jako DOCX (`doc.save("output.docx")`) nebo HTML (`doc.save("output.html")`) a podívat se, jak se stín přenáší.

Každé z těchto rozšíření staví na stejných základních konceptech: **přidat stín k tvaru**, **nastavit barvu výplně tvaru** a **uložit dokument jako PDF** (nebo jiný formát).

---

### Náhled obrázku *(volitelné)*

![Vytvoření obdélníkového tvaru se stínem v Pythonu](https://example.com/rectangle-shadow.png "Vytvoření obdélníkového tvaru se stínem v Pythonu")

*Screenshot ukazuje finální PDF výstup se světle modrým obdélníkem a jemným vnějším stínem.*

---

## Závěr

Prošli jsme všemi kroky potřebnými k **vytvoření obdélníkového tvaru** v Pythonu, aplikaci vlastní výplně, **přidání stínu k tvaru** a nakonec **uložení dokumentu jako PDF**. Kód je plně spustitelný, vysvětlení pokrývají *proč* za každou vlastností a dotkli jsme se běžných okrajových případů a dalších možností.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}