---
category: general
date: 2026-09-30
description: Naučte se, jak vytvořit obdélníkový tvar, přidat stín k tvaru a uložit
  dokument Word s tvarem pomocí Aspose.Words pro Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: cs
lastmod: 2026-09-30
og_description: Rychle vytvořte obdélníkový tvar v dokumentu Word. Tento tutoriál
  ukazuje, jak přidat tvar, aplikovat stín na tvar, nastavit rozostření stínu a uložit
  Word s tvarem.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Vytvořte obdélníkový tvar ve Wordu pomocí Pythonu – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Jak vytvořit obdélníkový tvar ve Word dokumentu pomocí Pythonu
url: /cs/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit obdélníkový tvar ve Word dokumentu pomocí Pythonu

Pokud potřebujete **vytvořit obdélníkový tvar** ve Word souboru, tento návod vám ukáže kompletní, spustitelné řešení. Uvidíte, jak přidat tvar, aplikovat efekt stínu, nastavit rozostření a nakonec **uložit Word s tvarem**, aby výsledek šel otevřít v Microsoft Word nebo jakémkoli kompatibilním prohlížeči.

Příklad používá **Aspose.Words for Python via .NET**, knihovnu, která umožňuje manipulovat s Word dokumenty bez nainstalovaného Microsoft Office. Není potřeba žádná předchozí zkušenost s API – stačí základní znalost Pythonu.

## Co dosáhnete

- Vložíte obdélník do první sekce nového dokumentu.  
- Nakonfigurujete měkký stín nastavením rozostření, posunu a barvy.  
- Uložíte dokument na disk a ověříte vizuální výsledek.

## Předpoklady

- Python 3.8 nebo novější.  
- Nainstalovaný balíček `aspose-words` (`pip install aspose-words`).  
- Oprávnění k zápisu do výstupního adresáře.

## Vytvoření obdélníkového tvaru a nastavení jeho vzhledu

Prvním krokem je vytvořit prázdný dokument a přidat do něj obdélníkový tvar. Tento tvar bude sloužit jako podklad pro efekt stínu.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Proč je to důležité:**  
Vytvořením obdélníku získáte konkrétní objekt (`shape`), který můžete později stylovat. Explicitní nastavení rozměrů zajišťuje, že tvar bude vypadat stejně na všech platformách.

## Jak přidat tvar do Word dokumentu

I když výše uvedený kód již obdélník přidává, můžete později potřebovat přidat další tvary (např. kruhy, šipky). Stejný vzor platí: zavolejte `append_child` na těle dokumentu a předáte požadovaný `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tip:** Používejte výčtový typ `ShapeType` k prozkoumání všech podporovaných tvarů. To udržuje kód čitelný a vyhýbá se „magickým“ číslům.

## Aplikace stínu na tvar a nastavení rozostření stínu

Stín přidává hloubku a vizuální zajímavost. Třída `ShadowEffect` vám umožní řídit rozostření, posun a barvu. Níže aplikujeme měkký černý stín na obdélník.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Proč nastavit rozostření?**  
`blur` určuje, jak rozptýlený stín vypadá. Nízká hodnota (např. 1.0) dává ostrý okraj, zatímco vyšší hodnota (např. 5.0) vytváří jemný přechod, který je často esteticky příjemnější.

**Hraniční případ:** Pokud nastavíte `blur` na 0, stín se stane pevnou siluetou. Některé prohlížeče jej mohou vykreslit s artefakty aliasingu, takže pro hladší výstup zvolte hodnotu větší než 0.

## Uložení Wordu s tvarem

Uložení dokumentu finalizuje všechny změny. Metoda `save` zapíše soubor `.docx`, který může otevřít jakýkoli moderní textový procesor.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Když otevřete `output.docx`, uvidíte obdélník umístěný jeden palec od levého horního rohu, s měkkým černým stínem posunutým o dva body doprava a dolů. Rozostření stínu působí, jako by byl tvar nad stránkou.

**Profesionální tip:** Pokud potřebujete generovat mnoho dokumentů ve smyčce, znovu použijte stejnou instanci `Document` a mezi iteracemi vyprázdněte její tělo, čímž snížíte paměťovou zátěž.

## Běžné varianty a řešení problémů

| Situace | Co změnit | Důvod |
|-----------|----------------|--------|
| Jiná barva stínu | `shadow.color = aw.Color.red` | Použijte firemní barvy nebo zvýrazněte důležité tvary. |
| Větší posun stínu | Zvyšte `shadow.offset_x`/`offset_y` | Zvýrazněte hloubku pro UI mock‑upy. |
| Žádný stín | Vynechte řádek `shape.shadow = shadow` | Vhodné pro minimalistické zprávy. |
| Export do PDF místo DOCX | `doc.save("output.pdf")` | PDF je ideální pro distribuci pouze ke čtení. |

Pokud se tvar nezobrazí, ověřte, že jej přidáváte do správné sekce (`get_first_section()`) a že dokument je uložen po provedení úprav.

## Kompletní, spustitelný příklad

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Spuštěním skriptu vznikne `output.docx` obsahující obdélník s měkkým stínem. Otevřete soubor v Microsoft Word a potvrďte, že vizuální efekt odpovídá popisu.

## Závěr

Nyní víte, jak **vytvořit obdélníkový tvar**, **přidat tvar** do Word dokumentu, **aplikovat stín na tvar**, **nastavit rozostření stínu** a nakonec **uložit Word s tvarem** pomocí Aspose.Words for Python. Stejný vzor lze rozšířit na další typy tvarů, barvy a efekty, což vám dává plnou kontrolu nad grafikou dokumentu bez nutnosti automatizace Office.

**Další kroky**

- Experimentujte s `Shape.fill` pro přidání gradientních nebo obrázkových pozadí.  
- Použijte objekty `Paragraph` k umístění textu uvnitř obdélníku.  
- Kombinujte více tvarů pro tvorbu složitých diagramů a poté exportujte do PDF pro distribuci.  

Neváhejte přizpůsobit kód pro své vlastní reporty nebo šablony a podělte se o výsledky v komentářích!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar se stínem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vytvořit obdélníkový tvar, přidat stín a uložit PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Přidat stín k Word tvaru v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}