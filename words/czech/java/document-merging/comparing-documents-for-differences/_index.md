---
"description": "Naučte se, jak porovnávat dokumenty a hledat mezi nimi rozdíly pomocí Aspose.Words v Javě. Náš podrobný návod vám zajistí přesnou správu dokumentů."
"linktitle": "Porovnávání dokumentů a hledání rozdílů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Porovnávání dokumentů a hledání rozdílů"
"url": "/cs/java/document-merging/comparing-documents-for-differences/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Porovnávání dokumentů a hledání rozdílů

## Zavedení

Přemýšleli jste někdy, jak najít každý jednotlivý rozdíl mezi dvěma dokumenty Wordu? Možná revidujete dokument nebo se snažíte najít změny provedené spolupracovníkem. Ruční porovnávání může být zdlouhavé a náchylné k chybám, ale s Aspose.Words pro Javu je to hračka! Tato knihovna vám umožňuje automatizovat porovnávání dokumentů, zvýrazňovat revize a bez námahy sloučit změny.

## Předpoklady

Než se pustíte do kódu, ujistěte se, že máte připravené následující:  
1. Na vašem systému nainstalovaná sada pro vývoj Java (JDK).  
2. Aspose.Words pro knihovnu Java. Můžete [stáhněte si to zde](https://releases.aspose.com/words/java/).  
3. Vývojové prostředí jako IntelliJ IDEA nebo Eclipse.  
4. Základní znalost programování v Javě.  
5. Platná licence Aspose. Pokud ji nemáte, zařiďte si ji. [dočasná licence zde](https://purchase.aspose.com/temporary-license/).

## Importovat balíčky

Pro použití Aspose.Words je nutné importovat potřebné třídy. Níže jsou uvedeny požadované importy:

```java
import com.aspose.words.*;
import java.util.Date;
```

Ujistěte se, že jsou tyto balíčky správně přidány do závislostí vašeho projektu.


V této části si celý proces rozdělíme na jednoduché kroky.


## Krok 1: Nastavení dokumentů

Pro začátek potřebujete dva dokumenty: jeden představující originál a druhý upravenou verzi. Zde je návod, jak je vytvořit:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

Tím se v paměti vytvoří dva dokumenty se základním obsahem. Existující dokumenty Wordu můžete také načíst pomocí `new Document("path/to/document.docx")`.


## Krok 2: Kontrola existujících revizí

Revize v dokumentech Word představují sledované změny. Před porovnáním se ujistěte, že žádný z dokumentů neobsahuje již existující revize:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Pokud existují revize, můžete je před pokračováním přijmout nebo odmítnout.


## Krok 3: Porovnejte dokumenty

Použijte `compare` metoda pro nalezení rozdílů. Tato metoda porovnává cílový dokument (`doc2`) se zdrojovým dokumentem (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Zde:
- Jméno autora je jméno osoby, která provádí změny.
- Datum je časové razítko porovnání.


## Krok 4: Revize procesu

Po porovnání Aspose.Words vygeneruje revize ve zdrojovém dokumentu (`doc1`). Pojďme si analyzovat tyto revize:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Tato smyčka poskytuje podrobné informace o každé revizi, například typ změny a ovlivněný text.


## Krok 5: Přijmout všechny revize

Pokud chcete zdrojový dokument (`doc1`) pro shodu s cílovým dokumentem (`doc2`), přijmout všechny revize:

```java
doc1.getRevisions().acceptAll();
```

Tato aktualizace `doc1` aby se odrážely všechny provedené změny `doc2`.


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


## Krok 7: Ověření rovnosti dokumentů

Abyste se ujistili, že jsou dokumenty identické, porovnejte jejich text:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Pokud se texty shodují, gratulujeme – dokumenty se vám úspěšně porovnaly a synchronizovaly!


## Závěr

Porovnávání dokumentů už není otrava díky Aspose.Words pro Javu. S několika řádky kódu můžete přesně určit rozdíly, zpracovat revize a zajistit konzistenci dokumentů. Ať už řídíte projekt společného psaní nebo auditujete právní dokumenty, tato funkce je převratná.

## Často kladené otázky

### Mohu porovnávat dokumenty s obrázky a tabulkami?  
Ano, Aspose.Words podporuje porovnávání složitých dokumentů, včetně těch s obrázky, tabulkami a formátováním.

### Potřebuji k používání této funkce licenci?  
Ano, pro plnou funkčnost je vyžadována licence. Získejte [dočasná licence zde](https://purchase.aspose.com/temporary-license/).

### Co se stane, když existují již existující revize?  
Před porovnáním dokumentů je musíte přijmout nebo odmítnout, abyste předešli konfliktům.

### Mohu v dokumentu zvýraznit revize?  
Ano, Aspose.Words umožňuje přizpůsobit způsob zobrazení revizí, například zvýraznění změn.

### Je tato funkce dostupná i v jiných programovacích jazycích?  
Ano, Aspose.Words podporuje více jazyků, včetně .NET a Pythonu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}