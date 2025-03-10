---
title: Porovnání rozdílů mezi dokumenty
linktitle: Porovnání rozdílů mezi dokumenty
second_title: Aspose.Words Java Document Processing API
description: Naučte se, jak porovnávat rozdíly mezi dokumenty pomocí Aspose.Words v Javě. Náš průvodce krok za krokem zajišťuje přesnou správu dokumentů.
weight: 12
url: /cs/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Porovnání rozdílů mezi dokumenty

## Zavedení

Přemýšleli jste někdy, jak rozpoznat každý jednotlivý rozdíl mezi dvěma dokumenty aplikace Word? Možná revidujete dokument nebo se snažíte najít změny provedené spolupracovníkem. Ruční porovnávání může být zdlouhavé a náchylné k chybám, ale s Aspose.Words pro Java je to hračka! Tato knihovna umožňuje automatizovat porovnání dokumentů, zvýrazňovat revize a slučovat změny bez námahy.

## Předpoklady

Než skočíte do kódu, ujistěte se, že máte připraveno následující:  
1. Java Development Kit (JDK) nainstalovaný ve vašem systému.  
2.  Aspose.Words pro knihovnu Java. Můžete[stáhněte si to zde](https://releases.aspose.com/words/java/).  
3. Vývojové prostředí jako IntelliJ IDEA nebo Eclipse.  
4. Základní znalost programování v Javě.  
5.  Platná licence Aspose. Pokud žádný nemáte, pořiďte si a[dočasná licence zde](https://purchase.aspose.com/temporary-license/).

## Importujte balíčky

Chcete-li používat Aspose.Words, musíte importovat potřebné třídy. Níže jsou uvedeny požadované importy:

```java
import com.aspose.words.*;
import java.util.Date;
```

Ujistěte se, že jsou tyto balíčky správně přidány do závislostí vašeho projektu.


V této části rozdělíme proces do jednoduchých kroků.


## Krok 1: Nastavte své dokumenty

Chcete-li začít, potřebujete dva dokumenty: jeden představuje originál a druhý představuje upravenou verzi. Takto je vytvoříte:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Tím se v paměti vytvoří dva dokumenty se základním obsahem. Můžete také načíst existující dokumenty aplikace Word pomocí`new Document("path/to/document.docx")`.


## Krok 2: Zkontrolujte existující revize

Revize v dokumentech aplikace Word představují sledované změny. Před porovnáním se ujistěte, že žádný dokument neobsahuje již existující revize:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Pokud existují revize, můžete je před pokračováním přijmout nebo odmítnout.


## Krok 3: Porovnejte dokumenty

 Použijte`compare` způsob, jak najít rozdíly. Tato metoda porovnává cílový dokument (`doc2`) se zdrojovým dokumentem (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Zde:
- AuthorName je jméno osoby, která provádí změny.
- Datum je časové razítko porovnání.


## Krok 4: Revize procesu

Po porovnání Aspose.Words vygeneruje revize ve zdrojovém dokumentu (`doc1`). Pojďme analyzovat tyto revize:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Tato smyčka poskytuje podrobné informace o každé revizi, jako je typ změny a dotčený text.


## Krok 5: Přijměte všechny revize

Pokud chcete zdrojový dokument (`doc1`), aby odpovídal cílovému dokumentu (`doc2`), přijměte všechny revize:

```java
doc1.getRevisions().acceptAll();
```

 Toto se aktualizuje`doc1` odrážet všechny provedené změny`doc2`.


## Krok 6: Uložte aktualizovaný dokument

Nakonec uložte aktualizovaný dokument na disk:

```java
doc1.save("Document.Compare.docx");
```

Chcete-li potvrdit změny, znovu načtěte dokument a ověřte, že nezbývají žádné revize:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Krok 7: Ověřte rovnost dokumentu

Aby byly dokumenty totožné, porovnejte jejich text:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Pokud se texty shodují, gratulujeme – úspěšně jste porovnali a synchronizovali dokumenty!


## Závěr

Díky Aspose.Words pro Javu již není porovnávání dokumentů žádná fuška. Pomocí několika řádků kódu můžete přesně určit rozdíly, zpracovat revize a zajistit konzistenci dokumentu. Ať už řídíte projekt společného psaní nebo kontrolujete právní dokumenty, tato funkce změní hru.

## FAQ

### Mohu porovnávat dokumenty s obrázky a tabulkami?  
Ano, Aspose.Words podporuje porovnávání složitých dokumentů, včetně těch s obrázky, tabulkami a formátováním.

### Potřebuji k používání této funkce licenci?  
 Ano, pro plnou funkčnost je nutná licence. Získejte a[dočasná licence zde](https://purchase.aspose.com/temporary-license/).

### Co se stane, pokud existují již existující revize?  
Před porovnáváním dokumentů je musíte přijmout nebo odmítnout, abyste předešli konfliktům.

### Mohu zvýraznit revize v dokumentu?  
Ano, Aspose.Words vám umožňuje přizpůsobit způsob zobrazení revizí, například zvýraznění změn.

### Je tato funkce dostupná v jiných programovacích jazycích?  
Ano, Aspose.Words podporuje více jazyků, včetně .NET a Pythonu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
