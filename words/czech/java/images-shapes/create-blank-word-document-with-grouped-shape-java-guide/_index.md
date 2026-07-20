---
category: general
date: 2026-07-20
description: Vytvořte prázdný dokument Word v Javě pomocí Aspose.Words. Naučte se,
  jak vytvořit skupinu, vložit obdélníkový tvar a vložit obrázek do tvaru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: cs
lastmod: 2026-07-20
og_description: Vytvořte prázdný dokument Word v Javě pomocí Aspose.Words. Tento průvodce
  ukazuje, jak vytvořit skupinu, vložit obdélníkový tvar a vložit obrázek do tvaru
  pro dynamické soubory Word.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Vytvořte prázdný dokument Word se seskupeným tvarem – Java průvodce
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Vytvořte prázdný dokument Word se seskupeným tvarem – Java průvodce
url: /cs/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření prázdného dokumentu Word se seskupeným tvarem – průvodce v Javě

Už jste se někdy zamysleli, jak **vytvořit prázdný dokument Word**, který už obsahuje pěkně seskupený tvar? Možná vytváříte šablonu zprávy, nebo potřebujete zástupný prvek pro logo a popisek. V každém případě je problém běžný: začnete s prázdným souborem, pak musíte přidat skupinu, vložit do ní obdélník a nakonec vložit obrázek – vše programově.

V tomto tutoriálu projdeme kompletním, připraveným k běhu Java příkladem, který přesně to provádí. Naučíte se **jak vytvořit skupinu**, **vložit obdélníkový tvar** a **přidat obrázek do dokumentu Word** ve stejné skupině. Na konci budete mít soubor Word, který vypadá jako vylepšená šablona, připravená k dalším úpravám.

> **Co získáte:** plně funkční Java třídu, podrobné vysvětlení krok za krokem, tipy pro práci s cestami k souborům a náhled očekávaného výstupu. Nepotřebujete žádnou externí dokumentaci – vše, co potřebujete, je zde.

---

## Vytvoření prázdného dokumentu Word – přehled krok za krokem

Prvním, co potřebujeme, je skutečně prázdný soubor Word. Aspose.Words to dělá jednoduchým: stačí vytvořit instanci třídy `Document` pomocí jejího výchozího konstruktoru. Získáte tak čisté plátno, ekvivalentní otevření Wordu a kliknutí na **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč začít s prázdným dokumentem?**  
> Prázdný dokument zaručuje, že žádné skryté styly nebo sekce nebudou zasahovat do tvarů, které později přidáte. Také udržuje velikost souboru na minimu, což je užitečné při generování desítek souborů v dávkovém úkolu.

---

## Jak vytvořit skupinu a přidat tvary

**Group shape** je v podstatě kontejner, který může obsahovat více podřízených tvarů – představte si ho jako složku pro kreslicí objekty. Seskupením můžete celý soubor přesouvat, měnit jeho velikost nebo otáčet jedním příkazem.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Metoda `insertGroupShape` vrací objekt `GroupShape`, který použijeme jako rodiče pro obdélník a obrázek. Velikost je vyjádřena v bodech (1 bod = 1/72 palce), takže 200 bodů vám dává přibližně krabici o rozměrech 2,78 × 2,78 palce.

> **Tip:** Pokud potřebujete, aby skupina byla průhledná, po vytvoření nastavte `group.setFillColor(Color.getWhite());`.

Nyní, když skupina existuje, musíme builderu říci, kam umístit další tvary. Kurzor builderu musí být umístěn uvnitř prvního odstavce skupiny.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Vložení obdélníkového tvaru do skupiny

Obdélník se často používá jako zástupný prvek pro text nebo jako vizuální nápověda. Přidáním jako **první podřízený** skupiny zajistíte, že bude ležet za všemi následnými obrázky.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Obdélník dědí souřadnicový systém skupiny, takže jeho velikost 100 × 50 bodů bude ve výchozím nastavení centrována. Můžete jej dále stylovat – přidat okraj, změnit barvu výplně nebo aplikovat stín – pomocí přístupu k vrácenému objektu `Shape`.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Přidání obrázku do dokumentu Word – vložení obrázku do tvaru

Nyní zábavná část: **vložit obrázek do tvaru**. Vložíme JPEG obrázek jako druhý podřízený stejném skupině. Protože kurzor je stále uvnitř skupiny, obrázek se automaticky stane podřízeným uzlem.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Pokud soubor obrázku není nalezen, Aspose.Words vyhodí `FileNotFoundException`. Aby se tomu předešlo, umístěte `sample.jpg` do pracovního adresáře projektu nebo použijte absolutní cestu.

> **Co když potřebujete jiný formát **obrázku**?**  
> Aspose.Words podporuje PNG, BMP, GIF, TIFF a dokonce i SVG. Stačí změnit příponu souboru a knihovna se postará o konverzi.

---

## Uložení dokumentu a zobrazení výsledku

Nakonec uložíme dokument v paměti na disk. Výsledný `.docx` bude obsahovat jednu stránku se seskupeným tvarem, který drží jak obdélník, tak obrázek.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Když otevřete `output.docx` v Microsoft Word, měli byste vidět 200 × 200‑bodovou skupinu v levém horním rohu. Uvnitř skupiny leží světle šedý obdélník nahoře a přímo pod ním se objeví obrázek, který jste zadali, dokonale zarovnaný.

![Grouped shape example](grouped-shape.png){:alt="Snímek obrazovky prázdného dokumentu Word se seskupeným tvarem obsahujícím obdélník a vložený obrázek"}

---

## Common variations and edge‑case handling

| Scénář | Co změnit | Proč je to důležité |
|----------|----------------|----------------|
| **Různá velikost skupiny** | Upravte parametry `insertGroupShape(width, height)` | Větší skupiny mohou pojmout složitější rozvržení. |
| **Více obrázků** | Opakovaně volejte `builder.insertImage()` po přesunutí kurzoru do odstavce skupiny při každém volání | Každé volání přidá nový podřízený; můžete je také umístit pomocí `Shape.setLeft()` / `setTop()`. |
| **Dynamické cesty k obrázkům** | Použijte `String.format("images/%s.jpg", imageName)` | Umožňuje znovupoužitelnost kódu pro dávkové zpracování. |
| **Ukládání jako PDF** | Nahraďte `doc.save("output.pdf")` | Aspose.Words může převádět za běhu, což vám umožní přímo generovat PDF. |
| **Otáčení skupiny** | `group.setRotation(45);` | Užitečné pro dekorativní vodoznaky nebo stylizované záhlaví. |

---

## Očekávaný výstup a ověření

Po spuštění třídy:

1. `output.docx` se objeví ve složce projektu.  
2. Otevřením souboru se zobrazí jedna stránka se seskupeným tvarem.  
3. Uvnitř skupiny je obdélník umístěn v levém horním rohu a obrázek leží přímo pod ním.  
4. Výběrem skupiny ve Wordu se zvýrazní oba podřízené objekty, což potvrzuje, že jsou skutečně seskupeny.

Pokud některý z těchto kroků selže, zkontrolujte znovu cestu k obrázku a ujistěte se, že je Aspose.Words JAR na vaší classpath.

---

## Závěr

Nyní víte **jak vytvořit prázdný dokument Word** a obohatit jej o seskupený tvar, který obsahuje obdélník a vložený obrázek. Ovládnutím **jak vytvořit skupinu**, **vložit obdélníkový tvar** a **přidat obrázek do dokumentu Word** můžete vytvořit sofistikované šablony Word kompletně v kódu – bez nutnosti ručních úprav.

Jste připraveni na další výzvu? Zkuste přidat textová pole do stejné skupiny nebo experimentovat s různými styly tvarů, aby odpovídaly vaší firemní identitě. Můžete dokonce vygenerovat celou knihovnu zpráv, kde každý dokument začíná tímto přesným rozvržením.

Šťastné programování a neváhejte sdílet své vlastní varianty v komentářích níže!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními krok za krokem, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření dokumentu Word v Javě – Přidání obdélníkového tvaru s efektem stínu](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak vytvořit PDF dokumenty s Aspose.Words pro Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}