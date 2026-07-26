---
category: general
date: 2026-07-26
description: Jak vložit ActiveX tlačítko do dokumentu Word pomocí Aspose.Words – naučte
  se nastavit popisek tlačítka, jeho pozici a velikost během několika řádků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: cs
lastmod: 2026-07-26
og_description: Jak vložit ActiveX tlačítko do dokumentu Word pomocí Aspose.Words.
  Postupujte podle tohoto krok‑za‑krokem tutoriálu a nastavte popisek tlačítka, jeho
  umístění a velikost.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Jak vložit tlačítko ActiveX do Wordu – rychlý průvodce
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Jak vložit ActiveX tlačítko do Wordu – nastavit popisek tlačítka
url: /cs/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit ActiveX tlačítko do Wordu – nastavit popisek tlačítka

Už jste se někdy zamýšleli **jak vložit ActiveX** ovládací prvky do souboru Word, aniž byste otevírali uživatelské rozhraní? Nejste v tom sami. V mnoha podnikových aplikacích potřebujete klikatelné tlačítko, které spustí makro, a provedení toho programově vám ušetří hodiny. Tento návod vám ukáže přesně **jak vložit ActiveX** CommandButton pomocí Aspose.Words for Java a — ano — jak **nastavit popisek tlačítka**, aby uživatel věděl, na co má kliknout.

Provedeme vás celým procesem: od nastavení knihovny, vytvoření nového dokumentu, vložení tlačítka, úpravy jeho velikosti a umístění, nastavení přátelského popisku a nakonec uložení souboru. Na konci budete mít spustitelný `.docx`, který se otevře ve Wordu s plně funkčním ActiveX tlačítkem připraveným spustit vaše makro.

---

## Co se naučíte

- Instalovat a odkazovat na Aspose.Words v Java projektu.  
- Vytvořit nový `Document` a `DocumentBuilder`.  
- **Vložit ActiveX** CommandButton ovládací prvek jedním řádkem kódu.  
- **Nastavit popisek tlačítka**, upravit jeho pozici a definovat rozměry.  
- Uložit dokument a otevřít jej ve Wordu, abyste viděli výsledek.

Předchozí zkušenosti s ActiveX nejsou vyžadovány; stačí základní znalost Javy a kopie Aspose.Words.

---

## Předpoklady

- Java 8 nebo novější nainstalovaná na vašem počítači.  
- Maven nebo Gradle pro správu závislostí (ukážeme ukázku pro Maven).  
- Licencovaná nebo zkušební kopie **Aspose.Words for Java** (bezplatná zkušební verze pro tento demo funguje).  
- Microsoft Word (jakákoli recentní verze) pro testování vygenerovaného souboru.

---

## Krok 1: Nastavení Aspose.Words ve vašem projektu

Nejprve přidejte závislost Aspose.Words. Pokud používáte Maven, vložte následující do souboru `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Uživatelé Gradlu mohou přidat:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Po rychlém `mvn clean install` (nebo `gradle build`) bude knihovna na vašem classpath a můžete začít kódovat.

---

## Krok 2: Vytvoření nového dokumentu a builderu

`Document` představuje celý Word soubor, zatímco `DocumentBuilder` vám umožňuje jej upravovat. Builder lze představit jako pero, které kreslí na čisté plátno.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Proč začínat prázdným dokumentem? Zaručuje vám plnou kontrolu nad každým prvkem, který přidáte, a nebudete překvapeni skrytým formátováním později.

---

## Krok 3: Vložení ActiveX CommandButton ovládacího prvku

A teď hvězda celého představení. Aspose.Words poskytuje `insertForms2OleControl`, který může umístit libovolný ActiveX ovládací prvek, který specifikujete. Zde požadujeme **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Metoda vrací objekt `Forms2OleControl`, který vám dává programový přístup k vlastnostem tlačítka. Právě zde se **jak vložit activex** stává jedním řádkem — žádné manipulace s nízkoúrovňovými COM API.

---

## Krok 4: Pozice, velikost a nastavení popisku tlačítka

Tlačítko, které levituje uprostřed stránky, není příliš užitečné. Budete ho chtít umístit tam, kde ho uživatelé očekávají, dát mu rozumnou velikost a — co je nejdůležitější — **nastavit popisek tlačítka**, aby věděli, co se stane po kliknutí.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Proč právě tyto čísla?** Word používá body (1 pt ≈ 1/72 palce). `100 pt` ≈ 1,4 palce od levého okraje, `150 pt` ≈ 2,1 palce od horního okraje — přibližně střed standardní stránky A4. Přizpůsobte je podle svého rozvržení.

Nastavení popisku je klíčové; bez něj tlačítko vypadá jako prázdný obdélník. Metoda `setCaption` přijímá libovolný řetězec, takže jej můžete později lokalizovat, pokud bude potřeba.

---

## Krok 5: Uložení dokumentu

Nakonec zapíšete dokument na disk. Můžete zvolit libovolnou složku, jen se ujistěte, že cesta existuje.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Když otevřete `ActiveXButton.docx` ve Wordu, uvidíte pěkně umístěné tlačítko s popiskem **„Click Me.“** Pokud na něj dvojkliknete, Word vás vyzve k povolení maker (protože ActiveX ovládací prvky jsou považovány za makra). Odtud můžete přiřadit VBA rutinu k události `Click` tlačítka.

---

## Okrajové případy a tipy, které můžete přehlédnout

- **Formát s povolenými makry**: Word v plain `.docx` souborech ActiveX ovládací prvky zakáže, pokud uživatel nepovolí makra. Pokud chcete, aby tlačítko fungovalo hned po otevření, zvažte uložení jako `.docm` (macro‑enabled) pomocí `doc.save(outputPath, SaveFormat.DOCM);`.  
- **Kompatibilita**: Starší verze Wordu (před 2007) používají binární formát `.doc`. Aspose.Words umí ukládat i do tohoto formátu, ale vlastnosti ovládacího prvku se mohou mírně lišit.  
- **Bezpečnostní nastavení**: Některá firemní prostředí blokují ActiveX. Pokud se vaše tlačítko nezobrazí, zkontrolujte Word → Trust Center → ActiveX Settings.  
- **Více tlačítek**: Potřebujete více než jedno? Stačí opakovat volání `insertForms2OleControl` a upravit hodnoty `Left`/`Top` každého tlačítka. Sledujte vrácené objekty, abyste mohli nastavit individuální popisky.  
- **Styling popisku**: Popisek dědí výchozí font. Pro jeho změnu byste museli upravit podkladové XML nebo po vložení aplikovat Word styl — což přesahuje rámec tohoto rychlého návodu, ale je proveditelné pomocí `ParagraphFormat` API v Aspose.Words.

---

## Kompletní funkční příklad

Níže je kompletní, připravená ke spuštění Java třída. Zkopírujte ji do svého IDE, upravte výstupní cestu a spusťte **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Očekávaný výstup**: Po spuštění se v konzoli vypíše cesta uložení. Otevřením vygenerovaného souboru ve Wordu se zobrazí tlačítko umístěné přibližně ve středu stránky s popiskem „Click Me“. Kliknutí spustí standardní ActiveX událost kliknutí (budete muset připojit VBA makro, aby reagovalo).

---

## Závěr

Nyní víte **jak vložit ActiveX** CommandButton ovládací prvky do Word dokumentu programově pomocí Aspose.Words a přesně jste viděli, jak **nastavit popisek tlačítka**, pozici a velikost ovládacího prvku. Tento přístup eliminuje ruční práci s UI, integruje se čistě do automatizovaných generátorů reportů a dává vám plnou kontrolu nad

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}