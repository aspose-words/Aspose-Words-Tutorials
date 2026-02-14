---
date: 2026-02-14
description: Naučte se, jak zobrazit matematiku v řádku, vložit matematickou rovnici
  a snadno manipulovat s objekty Office Math pomocí Aspose.Words pro Javu.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Zobrazit matematiku inline s Office Math v Aspose.Words pro Java
url: /cs/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazení matematiky inline pomocí Office Math v Aspose.Words pro Java

V tomto komplexním tutoriálu se dozvíte, jak **zobrazit matematiku inline** pomocí objektů Office Math v Aspose.Words pro Java. Ať už potřebujete **vložit matematickou rovnici** do zprávy nebo jemně doladit formátování složitých vzorců, tento průvodce vás provede každým krokem – od načtení dokumentu Word až po uložení konečného výsledku.

## Rychlé odpovědi
- **Co znamená „display math inline“?** Rovnice se zobrazí v rámci toku textu, nikoli na samostatném řádku.  
- **Která třída představuje matematický objekt?** `OfficeMath` v API Aspose.Words.  
- **Mohu změnit zarovnání?** Ano, použijte `setJustification` s hodnotami LEFT, CENTER nebo RIGHT.  
- **Potřebuji licenci pro tuto funkci?** Pro produkční použití je vyžadována platná licence Aspose.Words pro Java.  
- **Jaká verze je demonstrována?** Kód funguje s nejnovější verzí Aspose.Words pro Java (2026).  

## Co je „display math inline“?
Zobrazení matematiky inline znamená, že rovnice je považována za součást textu odstavce, což umožňuje její přirozené zalamování s okolními slovy. To je užitečné pro krátké vzorce, které by neměly narušovat tok čtení.

## Proč používat objekty Office Math v Aspose.Words pro Java?
- **Přesná kontrola** nad rozvržením rovnice (inline vs. display).  
- **Programová manipulace** s rovnicemi bez nutnosti ručně otevírat Word.  
- **Konzistentní vykreslování** napříč platformami, ideální pro automatizovanou tvorbu zpráv.

## Předpoklady
Než se pustíme dál, ujistěte se, že máte:

- Aspose.Words pro Java nainstalovaný a odkazovaný ve vašem projektu.  
- Soubor Word, který již obsahuje rovnici Office Math (např. `OfficeMath.docx`).  
- Platnou licenci, pokud plánujete spouštět kód mimo režim hodnocení.

## Průvodce krok za krokem

### Načtení dokumentu
Nejprve načtěte dokument, který obsahuje rovnici Office Math, se kterou chcete pracovat:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Přístup k objektu Office Math
Získejte první uzel Office Math z dokumentu:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Nastavení typu zobrazení (Inline vs. Display)
Ovládejte, zda se rovnice zobrazí inline s okolním textem nebo na samostatném řádku. Pro **display math inline** použijte výčtový typ `INLINE`; pro samostatný řádek použijte `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Pokud chcete, aby rovnice zůstala inline, nahraďte `DISPLAY` hodnotou `INLINE`.*

### Nastavení zarovnání
Upravte zarovnání rovnice. Níže ji zarovnáváme vlevo, ale můžete také zvolit `CENTER` nebo `RIGHT`:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Uložení upraveného dokumentu
Nakonec zapište změny zpět do nového souboru:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Kompletní zdrojový kód pro používání objektů Office Math v Aspose.Words pro Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Časté problémy a řešení
- **Rovnice nenalezena:** Ujistěte se, že dokument skutečně obsahuje objekt Office Math; jinak `doc.getChild` vrátí `null`.  
- **Typ zobrazení nemá žádný efekt:** Ověřte, že používáte aktuální verzi Aspose.Words; starší verze mohou mít omezenou podporu pro `OfficeMathDisplayType`.  
- **Výjimka licence:** Pokud se zobrazí chyba licence, zkontrolujte, že je soubor licence správně načten před vytvořením instance `Document`.  

## Často kladené otázky

**Q: Jaký je účel objektů Office Math v Aspose.Words pro Java?**  
A: Objekty Office Math vám umožňují programově reprezentovat a manipulovat s matematickými rovnicemi, což vám dává plnou kontrolu nad jejich zobrazením a formátováním.

**Q: Mohu v dokumentu zarovnat rovnice Office Math různě?**  
A: Ano, použijte metodu `setJustification` pro zarovnání vlevo, vpravo nebo na střed.

**Q: Je Aspose.Words pro Java vhodný pro práci s komplexními matematickými dokumenty?**  
A: Rozhodně. Knihovna plně podporuje složité rovnice, vnořené zlomky, matice a další.

**Q: Jak se mohu dozvědět více o Aspose.Words pro Java?**  
A: Pro komplexní dokumentaci a ke stažení navštivte [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**Q: Odkud si mohu stáhnout Aspose.Words pro Java?**  
A: Aspose.Words pro Java můžete stáhnout z webu: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Poslední aktualizace:** 2026-02-14  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější k únoru 2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}