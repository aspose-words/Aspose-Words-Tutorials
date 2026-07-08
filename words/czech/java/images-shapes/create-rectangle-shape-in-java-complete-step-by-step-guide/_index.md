---
category: general
date: 2026-07-03
description: Vytvořte obdélníkový tvar v Javě a naučte se, jak přidat stín k tvaru,
  aplikovat efekt stínu, nastavit průhlednost tvaru a rychle vytvořit prázdný dokument.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: cs
og_description: Vytvořte obdélníkový tvar v Javě se stínem, průhledností a prázdným
  dokumentem. Postupujte podle tohoto průvodce a ovládněte práci s tvary.
og_title: Vytvořte obdélníkový tvar v Javě – kompletní programovací tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Vytvořte tvar obdélníku v Javě – Kompletní průvodce krok za krokem
url: /cs/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru v Javě – Kompletní průvodce krok za krokem

Už jste se někdy zamýšleli, jak **create rectangle shape** v dokumentu Word pomocí Javy? Nejste jediní — vývojáři často potřebují rychlý způsob, jak přidat geometrické grafiky a následně jim dát jemný stín, aby rozvržení působilo uhlazeněji. V tomto tutoriálu projdeme celý proces: od vytvoření **create blank document** až po **add shadow to shape**, **apply shadow effect** a dokonce **set shape transparency** pro profesionální vzhled.

Ukázkový úryvek níže je plně funkční příklad, který můžete zkopírovat a vložit do svého projektu. Nepotřebujete žádnou externí dokumentaci — stačí sledovat kroky, pochopit „proč“ a během několika vteřin budete generovat obdélníky se stínem.

## Co se naučíte

- Jak programově **create rectangle shape** pomocí Aspose.Words for Java.
- Jaké volání jsou potřeba k **add shadow to shape** a nastavení jeho vizuálních vlastností.
- Jak **apply shadow effect** a upravit parametry jako offset, blur radius a barvu.
- Techniky pro **set shape transparency** pro jemnější vzhled.
- Jak **create blank document**, vložit tvar a výsledek uložit.

> **Tip:** Všechny tyto akce jsou prováděny na jedné instanci `Document`, což znamená, že je můžete řetězit bez starostí o mezilehlé I/O soubory.

## Požadavky

Než se pustíme dál, ujistěte se, že máte:

- Java 17 (nebo jakoukoli novější JDK) nainstalovanou.
- Knihovnu Aspose.Words for Java přidanou do projektu (Maven koordináty: `com.aspose:aspose-words:23.12`).
- Java IDE nebo jednoduchý textový editor — nic složitého, jen místo, kde můžete kód zkompilovat a spustit.

Pokud vám něco chybí, stáhněte JDK od Oracle a přidejte závislost Aspose přes Maven nebo Gradle. Jakmile budete připraveni, můžete začít.

## Krok 1: **Create blank document** – plátno pro vše

První věc, kterou potřebujete, je prázdný objekt `Document`. Představte si ho jako čistý list papíru; bez něj nemáte kam umístit svůj obdélník.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Proč začít s prázdným dokumentem? Protože každý tvar žije uvnitř `Section` a nově vytvořený `Document` již obsahuje výchozí sekci s tělem připraveným přijmout uzly. Přeskočení tohoto kroku by vás donutilo ručně vytvářet sekce později, což zvyšuje složitost.

## Krok 2: **Create rectangle shape** a definujte jeho velikost

Nyní, když máme plátno, **create rectangle shape**. Třída `Shape` přijímá odkaz na dokument a `ShapeType`. Zvolíme `RECTANGLE` a nastavíme šířku/výšku v bodech (1 pt ≈ 1/72 palce).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Proč nastavit `WrapType.INLINE`? Inline zalamování způsobí, že se tvar chová jako znak v odstavci, takže se pohybuje spolu s okolním textem. Pokud potřebujete plovoucí chování, přepněte na `WrapType.SQUARE` nebo `WrapType.TOP_BOTTOM`.

## Krok 3: **Apply shadow effect** – dejte obdélníku hloubku

Plochý obdélník vypadá… no, plochě. Přidání stínu ho oživí. **apply shadow effect** vytvoříme vytvořením instance `ShadowEffect` a následným doladěním jejích vizuálních vlastností.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Rozbalme si to trochu:

- **Color** – `Color.getGray(0.5)` dává 50 % šedou, což je neutrální a funguje na většině pozadí.
- **OffsetX/Y** – Kladné hodnoty posunou stín doprava a dolů; záporné by ho posunuly vlevo/nahoru.
- **BlurRadius** – Větší hodnoty vytvoří měkčí, rozptýlenější stín.
- **Transparency** – Rozsah od `0` (neprůhledný) po `1` (zcela průhledný). Zde jsme zvolili `0.3` pro decentní efekt.

## Krok 4: **Add shadow to shape** – přiřaďte efekt

Vytvoření efektu nestačí; musíme **add shadow to shape** přiřazením objektu `ShadowEffect` k obdélníku.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Za scénou tato volání aktualizují podkladový OpenXML markup (`<w:shdw>`), který Word používá k vykreslení stínů. Pokud si prohlédnete uložený `.docx`, uvidíte element `<w:effect>` naplněný parametry, které jsme nastavili.

## Krok 5: **Set shape transparency** – volitelné, ale často užitečné

Někdy chcete, aby byl samotný obdélník částečně průhledný, aby se pod ním zobrazoval text. Třída `Shape` nabízí `setFillColor` a `setFillTransparency`. Zde je rychlý příklad, který dělá obdélník 40 % průhledný:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Proč byste to dělali? Představte si vodoznak nebo zvýrazněný výkřik, kde musí zůstat čitelný podkladový obsah. Upravením hodnoty průhlednosti přizpůsobíte vzhled svému designu.

## Krok 6: Vložte tvar do dokumentu

Postavili jsme obdélník, přidali stín a (volitelně) nastavili průhlednost. Poslední krok je **add the shape to the first section of the document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Přidání tvaru do těla umístí tvar na konec prvního odstavce. Pokud potřebujete konkrétní místo vložení, získejte cílový `Paragraph` a použijte `insertBefore` nebo `insertAfter`.

## Krok 7: Uložte dokument – podívejte se na výsledek

Veškerá ta práce končí jednou voláním `save`. Zvolte cestu, která dává smysl pro vaše prostředí.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Otevřete vzniklý `ShadowShape.docx` v Microsoft Word nebo LibreOffice a uvidíte ostrý obdélník s jemným šedým stínem, lehce průhledný, pokud jste použili volitelný krok. Vzhled odpovídá parametrům, které jsme definovali programově.

---

![vytvořit obdélníkový tvar se stínem v dokumentu Word](https://example.com/images/rectangle-shadow.png "vytvořit obdélníkový tvar se stínem")

*Alternativní text obrázku:* **vytvořit obdélníkový tvar se stínem** – vizuální znázornění finálního výstupu.

## Často kladené otázky a okrajové případy

### Co když chci jinou barvu stínu?

Jednoduše změňte volání `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Pamatujte, že příliš výrazné stíny mohou vypadat neprofesionálně; jemné tóny obvykle fungují nejlépe.

### Můžu použít stejný stín pro více tvarů?

Ano. Vytvořte jednu instanci `ShadowEffect`, nakonfigurujte ji a poté ji znovu použijte:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Jen se vyhněte změně `ShadowEffect` po jeho přiřazení k dalším tvarům, pokud nechcete aktualizovat všechny najednou.

### Jak mohu dynamicky měnit rozostření stínu?

Vytvořte UI posuvník, který mapuje na `setBlurRadius`. Hodnoty mezi `2` a `12` jsou typické; vyšší čísla produkují spíše „záři“ než ostrý stín.

### Co když potřebuji, aby se tvar vznášel místo toho, aby byl inline?

Vyměňte typ zalamování:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Vznášející se tvary poskytují větší volnost v rozvržení, ale vyžadují další logiku pro jejich umístění.

## Kompletní funkční příklad

Níže je kompletní program připravený ke zkopírování, který zahrnuje všechny kroky, o kterých jsme mluvili. Spusťte jej jako běžnou Java aplikaci.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Očekávaný výstup:** Po otevření `ShadowShape.docx` uvidíte bílý obdélník 200 × 100 pt, vycentrovaný v prvním odstavci, se středně šedým stínem posunutým o 5 pt, rozostřeným s radius 8 a 30 % průhledností. Samotný obdélník je 40 % průhledný, takže podkladový text lehce prosvítá.

## Závěr

Právě jsme **create rectangle shape** od nuly, **add shadow to shape**, **apply shadow effect** a dokonce **set shape transparency** — vše při **create blank document** jako základu. Přístup je přímočarý, využívá plynulé API Aspose.Words a lze jej rozšířit na kruhy, hvězdy nebo vlastní mnohoúhelníky.

Co bude dál na vaší cestě? Vyzkoušejte výměnu `ShapeType.RECTANGLE` za `ShapeType.OVAL` a vytvořte obdélníky s kruhovým stínem, nebo experimentujte s gradientními výplněmi pro


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořit Word dokument v Javě – Přidat obdélníkový tvar se stínem](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Vytvořit prázdný Word dokument se stínovaným obdélníkovým tvarem – Průvodce krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Přidat stín k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}