---
date: '2026-08-10'
description: Naučte se, jak přidat komentář v Javě pomocí Aspose.Words for Java. Podrobný
  návod krok za krokem pro vytvoření, odpověď, tisk, odstranění a označení komentářů
  jako dokončených, včetně získání časových razítek UTC.
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: Naučte se, jak přidat komentář v Javě pomocí Aspose.Words for Java.
  Podrobný návod krok za krokem pro vytvoření, odpověď, tisk, odstranění a označení
  komentářů jako dokončených, včetně získání časových razítek UTC.
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: Jak přidat komentář v Javě pomocí Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: Jak přidat komentář v Javě pomocí Aspose.Words for Java
url: /cs/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat komentář java pomocí Aspose.Words pro Word dokumenty

## Úvod
Přidávání komentářů programově do dokumentu Word může zefektivnit spolupráci, kontrolu kódu nebo automatické generování zpráv. V tomto tutoriálu se naučíte **how to add comment java** pomocí knihovny Aspose.Words, včetně vytváření, odpovědí, výpisu, odstraňování, označování jako dokončené a získávání UTC časových razítek. Na konci budete schopni vložit bohatou zpětnou vazbu přímo do svých dokumentů bez ručního zásahu.

## Rychlé odpovědi
- **Jaký je první krok?** Načtěte soubor Word pomocí `new Document("input.docx")`.  
- **Mohu odpovědět na komentář?** Ano — vytvořte objekt `Comment` a zavolejte `comment.getReplies().add(reply)`.  
- **Jak označím komentář jako dokončený?** Nastavte `comment.setDone(true)`, čímž jej označíte jako vyřešený.  
- **Je k dispozici UTC čas?** Každý komentář ukládá `getDateTime()` v UTC, který můžete číst přímo.  
- **Potřebuji licenci?** Zkušební verze funguje pro vývoj; plná licence odstraňuje omezení hodnocení.

## Co je „how to add comment java“?
`how to add comment java` označuje proces programového vložení komentáře do dokumentu Microsoft Word pomocí Java kódu a Aspose.Words API. Tento postup umožňuje automatizované smyčky zpětné vazby v pracovních postupech zaměřených na dokumenty.

## Proč používat Aspose.Words pro správu komentářů?
Aspose.Words podporuje **35+ vstupních a výstupních formátů** a dokáže zpracovat dokumenty přesahující **500 stránek**, přičemž spotřeba paměti zůstává pod **100 MB** na typickém serveru. Jeho API pro komentáře funguje bez nainstalovaného Microsoft Word, což vám dává plnou kontrolu v headless prostředích a snižuje náklady na licence až o **70 %** ve srovnání s automatizací Office.

## Požadavky
- Java Development Kit (JDK) 17 nebo novější nainstalovaný.  
- IDE jako IntelliJ IDEA nebo Eclipse.  
- Maven nebo Gradle pro správu závislostí.  
- Platná licence Aspose.Words pro Java (zkušební nebo plná).

### Nastavení Aspose.Words pro Java
Aspose.Words je distribuováno jako jediný JAR. Přidejte závislost odpovídající vašemu nástroji pro sestavení.

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### Získání licence
Aspose.Words je komerční produkt; můžete začít s bezplatnou zkušební verzí nebo požádat o dočasnou licenci pro plný přístup k funkcím. Navštivte [purchase page](https://purchase.aspose.com/buy) a prozkoumejte možnosti licencování.

## Jak přidat komentář v Javě pomocí Aspose.Words?
Načtěte svůj dokument, vytvořte objekt `Comment` a připojte jej k `Paragraph`. Tento dvoukrokový vzor vloží komentář na požadované místo a tvoří základ pro všechny následné operace. Zadáním autora, textu a časového razítka okamžitě poskytnete kontext recenzentům a komentář se stane součástí struktury dokumentu.

Třída `Document` je hlavní objekt Aspose.Words, který představuje jeden soubor Word v paměti. Po vytvoření objektu probíhají všechny operace čtení a zápisu skrze něj.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

Dále vytvoříte samotný komentář. Třída `Comment` ukládá informace o autorovi, textu a časovém razítku.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Nakonec přidejte odpověď pomocí kolekce `Replies` komentáře. Objekt `Comment` automaticky sleduje hierarchii odpovědí.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Jak vytisknout všechny komentáře a jejich odpovědi?
Procházejte `CommentCollection` dokumentu a vypište text, autora a UTC časové razítko každého komentáře. Odpovědi jsou vnořeny v každém komentáři, což umožňuje zobrazit celý konverzační řetězec. Rekurzivním procházením kolekce můžete zachovat hierarchii, formátovat výstup pro logy nebo UI a volitelně filtrovat podle autora či data.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

Použijte jednoduchý cyklus k procházení kolekce a výpisu detailů.  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```  

## Jak odstranit odpovědi na komentář?
Můžete smazat konkrétní odpověď nebo vymazat všechny odpovědi z komentáře. Odstraňování odpovědí pomáhá udržet dokument čistý po zapracování zpětné vazby. Použijte metodu `getReplies().remove(index)` pro cílené odstranění nebo zavolejte `clear()` k vyprázdnění celé seznamu odpovědí, čímž zajistíte, že nezůstane žádná osamělá diskuse.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

Zavolejte `comment.getReplies().clear()` nebo odstraňte jednotlivé odpovědi podle indexu.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## Jak označit komentář jako dokončený?
Nastavení příznaku `Done` u komentáře signalizuje, že problém byl vyřešen. Tento vizuální indikátor je užitečný pro recenzenty i nástroje následného zpracování. Když je zavoláno `setDone(true)`, Word zobrazí zaškrtnutí vedle komentáře a později můžete tento příznak dotazovat pro generování zpráv o nevyřešených položkách.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

Aplikujte příznak poté, co jste vyřešili obsah komentáře.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## Jak získat UTC datum a čas z komentáře?
Každý komentář ukládá čas vytvoření v UTC, přístupný přes `getDateTime()`. Toto časové razítko je nepostradatelné pro auditní stopy a správu verzí. Vrácený objekt `DateTime` lze formátovat pomocí vzorů ISO‑8601, což umožňuje přesné zaznamenání okamžiků zpětné vazby a synchronizaci dat komentářů napříč distribuovanými systémy.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Můžete formátovat časové razítko jako ISO‑8601 pro snadné logování.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Praktické aplikace
Pochopení těchto API vám umožní vytvořit robustní řešení pro:
- **Platformy pro kolaborativní úpravy** — vložte smyčky zpětné vazby přímo do generovaných zpráv.  
- **Automatizované revizní pipeline** — označujte, řešte a auditujte komentáře bez lidského zásahu.  
- **Dokumentaci pro soulad** — zachyťte časová razítka recenzentů pro regulatorní audity.

## Úvahy o výkonu
Při zpracování velkých souborů (500 + stránek) dodržujte tyto osvědčené postupy:
- Zpracovávejte komentáře po dávkách, abyste se vyhnuli načítání celé kolekce do paměti.  
- Použijte `Document.optimizeResources()` ke zmenšení dokumentu před uložením.  
- Udržujte Aspose.Words aktuální; verze 24.12 přinesla 30 % zrychlení při výčtu komentářů.

## Závěr
Nyní máte kompletní sadu nástrojů pro **how to add comment java** s Aspose.Words: vytváření komentářů, odpovídání, výpis, odstraňování, označování jako dokončené a získávání UTC časových razítek. Integrujte tyto úryvky do svých existujících Java služeb k automatizaci zpětné vazby, vynucení revizních politik a udržení čisté auditní stopy.

**Další kroky**
- Experimentujte s filtrováním komentářů podle autora nebo data.  
- Kombinujte správu komentářů s API Aspose.Words „track changes“ pro úplnou kontrolu revizí.  
- Prozkoumejte export dat komentářů do JSON pro následnou analytiku.

## Často kladené otázky

**Q: Mohu používat Aspose.Words bez licence v produkci?**  
**A:** Ne. Zkušební verze funguje pouze pro vývoj; plná licence je vyžadována pro nasazení do produkce.

**Q: Podporuje knihovna dokumenty chráněné heslem?**  
**A:** Ano. Načtěte chráněný soubor předáním hesla do konstruktoru `Document`.

**Q: Které verze Javy jsou kompatibilní?**  
**A:** Aspose.Words pro Java podporuje JDK 8 až JDK 21 s plnou funkční rovností napříč verzemi.

**Q: Jak se výkon komentářů mění s velikostí dokumentu?**  
**A:** Výčet komentářů probíhá lineárně; 1 000‑stránkový dokument se zpracuje za méně než 2 sekundy na typickém 4‑jádrovém serveru.

**Q: Mohu exportovat komentáře do samostatného souboru?**  
**A:** Rozhodně. Procházejte `CommentCollection` a zapisujte vlastnosti každého komentáře do CSV, JSON nebo XML podle potřeby.

---

**Last Updated:** 2026-08-10  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Související tutoriály

- [Mistrovství anotací a komentářů s tutoriály Aspose.Words pro Java](/words/java/annotations-comments/)
- [Sledování změn v dokumentech Word pomocí Aspose.Words Java: Kompletní průvodce revizemi dokumentů](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Komplexní průvodce zpracováním Word dokumentů](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}