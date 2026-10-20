---
category: general
date: 2026-02-10
description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí Aspose.Words pro Java.
  Naučte se, jak nastavit barvu stínu, jak přidat stín a jak programově vytvořit Word
  dokument.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: cs
og_description: Vytvořte obdélníkový tvar ve Word dokumentu pomocí Aspose.Words pro
  Java. Postupujte podle tohoto krok‑za‑krokem tutoriálu, abyste nastavili barvu stínu,
  přidali stín a vytvořili Word dokument.
og_title: Vytvořte obdélníkový tvar ve Wordu pomocí Javy – kompletní průvodce
tags:
- Aspose.Words
- Java
- Document Automation
title: Vytvořte obdélníkový tvar ve Wordu pomocí Javy – kompletní průvodce
url: /cs/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Wordu pomocí Javy – Kompletní průvodce

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v dokumentu Word, ale nevedeli ste, kde začít? Nejste v tom sami — mnoho vývojářů narazí na tuto překážku, když poprvé zkusí programově kreslit grafiku ve Wordu. Dobrá zpráva? S Aspose.Words pro Java můžete během několika sekund vložit obdélník na stránku, přidat mu pěkný stín a soubor uložit. V tomto tutoriálu vás provedeme přesně **jak přidat stín**, **nastavit barvu stínu** a **vytvořit Word dokument** od nuly.

Probereme vše, co potřebujete: požadované knihovny, každý řádek kódu, proč jsou některá nastavení důležitá, a pár triků, které v oficiální dokumentaci nemusíte najít. Na konci budete mít připravený spustitelný příklad, který vytvoří obdélníkový tvar s jemným šedým stínem, uložený jako *Shadow.docx*.

## Požadavky – Co potřebujete před začátkem

Než se pustíme do kódu, ujistěte se, že máte následující:

| Požadavek | Důvod |
|-------------|--------|
| Java Development Kit (JDK) 8 nebo novější | Aspose.Words běží na libovolném moderním JDK. |
| Maven nebo Gradle (volitelné) | Zjednodušuje přidání závislosti Aspose.Words. |
| Aspose.Words for Java licence (nebo bezplatná zkušební verze) | Knihovna je komerční; zkušební verze stačí pro testování. |
| IDE (IntelliJ IDEA, Eclipse, VS Code, atd.) | Umožní rychle spustit a ladit příklad. |

Pokud již máte Java projekt, stačí přidat Maven koordináty:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Žádné složité nastavení nad rámec toho — stačí obyčejná metoda `public static void main`.

![create rectangle shape example](https://example.com/rectangle-shadow.png "vytvoření obdélníkového tvaru se stínem ve Wordu")

*Obrázek: příklad vytvoření obdélníkového tvaru ukazující cyanový obdélník se šedým stínem.*

## Krok 1 – Vytvoření nového Word dokumentu

První věc, kterou musíme udělat, je vytvořit prázdný dokument. Představte si to jako otevření čerstvého souboru Word, na který později „malujete“.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Proč začít s prázdným `Document`? Protože Aspose.Words považuje třídu `Document` za plátno pro všechny následné operace — přidávání odstavců, tabulek nebo tvarů. Pokud tento krok přeskočíte, okamžitě při pokusu o vložení čehokoli dostanete `NullPointerException`.

## Krok 2 – Nastavení DocumentBuilderu

`DocumentBuilder` je vaše přátelská tužka, která zapisuje do `Document`. Je to doporučený způsob přidávání obsahu, protože automaticky spravuje pozici kurzoru.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Možná se ptáte: „Proč nepracovat přímo s dokumentem?“ Odpověď: builder abstrahuje nízkoúrovňové detaily, jako je správa sekcí, a dělá kód čistším a méně náchylným k chybám.

## Krok 3 – Vložení obdélníkového tvaru

Nyní přichází zábavná část — **jak vytvořit tvar**. Vložíme obdélník o rozměrech 100 × 50 bodů a nastavíme mu cyanovou výplň, aby byl viditelný.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Několik poznámek:

* `ShapeType.RECTANGLE` říká Aspose, že chceme obdélník; můžete jej nahradit `OVAL`, `LINE` atd.
* Rozměry jsou vyjádřeny v bodech (1 pt ≈ 1/72 palce). Upravit je můžete podle potřeby.
* Bez výplňové barvy by byl tvar neviditelný na bílé stránce — proto cyan.

## Krok 4 – Přidání stínu a **nastavení barvy stínu**

Zde odpovídáme na část **jak přidat stín**. Objekt `ShadowFormat` řídí každý vizuální aspekt stínu, od barvy po poloměr rozostření.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Proč právě tyto hodnoty?

* **Visibility** – Bez `setVisible(true)` jsou ostatní nastavení ignorována.
* **Color** – Šedá je neutrální volba, která funguje na světlých i tmavých pozadích. Klidně ji nahraďte libovolnou `java.awt.Color`.
* **Blur radius** – Hodnota `5.0` poskytuje jemný přechod; vyšší čísla udělají stín rozptýlenější.
* **OffsetX/Y** – Posuny posunou stín doprava a dolů, napodobujíc světelný zdroj z levého horního rohu.
* **Transparency** – Poloprůhledný stín se lépe mísí se stránkou, zejména při tisku.

Pokud chcete ostřejší vzhled, snižte rozostření na `0` a zvýšte offset. Experimentujte — stíny jsou vizuální a správná nastavení závisí na designu vašeho dokumentu.

## Krok 5 – Uložení dokumentu

Nakonec vše uložíme do souboru `.docx`. Můžete zvolit libovolnou cestu, jen se ujistěte, že adresář existuje.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Když otevřete *Shadow.docx* v Microsoft Word, uvidíte cyanový obdélník s jemným šedým stínem posunutým o 4 pt doprava a dolů. To je kompletní workflow **vytvoření Word dokumentu**.

### Očekávaný výsledek

| Prvek | Vzhled |
|---------|------------|
| Obdélník | Cyanová výplň, velikost 100 × 50 pt |
| Stín | Šedý, 30 % průhledný, rozostření 5 pt, offset (4, 4) |
| Soubor | `Shadow.docx` uložený na zadané cestě |

Pokud se tvar neobjeví, zkontrolujte, že výplňová barva není stejná jako pozadí stránky a že je stín nastaven jako viditelný.

## Pro tipy a časté úskalí

* **Pro tip:** Použijte `rectangle.setStrokeColor(java.awt.Color.BLACK);`, pokud chcete okraj kolem tvaru. Pomůže to, aby obdélník lépe vynikl na tištěné stránce.
* **Dejte pozor na:** Ukládání do složky jen pro čtení vyvolá `IOException`. Vyberte zapisovatelnou lokaci nebo upravte oprávnění souboru.
* **Hraniční případ:** Pokud potřebujete průhlednou výplň (žádnou barvu), zavolejte `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Tvar stále vrhá stín, což může být užitečné pro vodotiskové grafiky.
* **Poznámka o výkonu:** Přidání stovek tvarů ve smyčce může zvýšit spotřebu paměti. Volání `document.save` proveďte jen jednou po přidání všech tvarů.

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do Java třídy s názvem `ShadowDemo`. Překládá se a spouští tak, jak je (při přítomnosti Aspose.Words JAR v classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Spusťte program, otevřete vzniklý *Shadow.docx* a uvidíte obdélník se stínem přesně tak, jak je popsáno.

## Co když potřebuji více tvarů?

Možná se ptáte: „Mohu **vytvořit obdélníkový tvar** vícekrát nebo použít jiné tvary?“ Rozhodně. Stačí obalit kód vkládání do smyčky a upravit souřadnice pomocí `builder.moveTo` nebo `builder.insertParagraph`. Stejná nastavení stínu můžete znovu použít tak, že je vytáhnete do pomocné metody:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Zavolejte `applyStandardShadow(rectangle);` po každém vložení tvaru, aby byl kód DRY (Don’t Repeat Yourself).

## Další kroky – Přesah základů

Nyní, když víte **jak přidat stín**, můžete prozkoumat související témata:

* **Jak nastavit barvu stínu** pro textové běhy — dává nadpisům jemný nádech.
* **Vytvořit Word dokument** s tabulkami a obrázky — kombinujte tvary s dalším obsahem.
* **Jak vytvořit animaci tvaru** pomocí vestavěných funkcí Wordu

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}