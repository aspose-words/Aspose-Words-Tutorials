---
date: 2026-01-03
description: Lär dig hur du ersätter text med HTML i Word‑dokument med Aspose.Words
  för Java. Steg‑för‑steg‑guide med kodexempel, regex‑ersättning av text, Java‑tips
  och mer.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: Ersätt text med HTML med Aspose.Words för Java
url: /sv/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ersätt text med HTML i Aspose.Words för Java

## Introduktion till att hitta och ersätta text i Aspose.Words för Java

Aspose.Words for Java är ett kraftfullt Java‑API som låter dig manipulera Word‑dokument programmässigt. En av de vanligaste uppgifterna är **replace text with html**, oavsett om du uppdaterar platshållare i en mall, injicerar formaterat innehåll eller utför massiva textomvandlingar. I den här guiden går vi igenom hur du ersätter text, hur du använder regex replace text java, och till och med hur du ersätter text i rubriker – allt medan du håller din kod ren och effektiv.

## Snabba svar
- **Vad är den primära metoden för att ersätta text med html?** Använd `FindReplaceOptions` med en anpassad callback som `ReplaceWithHtmlEvaluator`.  
- **Kan jag ignorera fält vid ersättning?** Ja – sätt `options.setIgnoreFields(true)`.  
- **Behöver jag en licens för produktionsanvändning?** En giltig Aspose.Words‑licens krävs för kommersiella distributioner.  
- **Vilken Java‑version stöds?** Aspose.Words för Java fungerar med Java 8 och senare.  
- **Stöds regex replace text java?** Absolut – skicka ett `Pattern`‑objekt till `replace`‑metoden.

## Vad är “replace text with html”?

Att ersätta text med HTML innebär att byta ut en ren‑text‑platshållare mot rik HTML‑markup (tabeller, listor, styling) samtidigt som den omgivande Word‑dokumentstrukturen bevaras. Aspose.Words analyserar HTML‑koden och infogar motsvarande Word‑objekt, vilket ger dig full kontroll över den slutgiltiga layouten.

## Varför använda Aspose.Words för denna uppgift?

- **Full Word‑fidelity** – biblioteket behåller all formatering, rubriker, sidfötter och spårade ändringar intakta.  
- **Inbyggt regex‑stöd** – perfekt för komplexa sökmönster (`regex replace text java`).  
- **Fin‑granulerad kontroll** – alternativ som `IgnoreFields`, `IgnoreDeleted` och `UseLegacyOrder` låter dig anpassa operationen exakt efter dina behov.  
- **Plattformsoberoende** – fungerar på alla OS som kör Java.

## Förutsättningar

- Java‑utvecklingsmiljö (JDK 8+)
- Aspose.Words för Java‑biblioteket – ladda ner det från [here](https://releases.aspose.com/words/java/).
- Ett exempel‑Word‑dokument (`.docx`) att experimentera med.

## Hitta och ersätta enkel text

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Detta enkla exempel visar **how to replace text** med `replace`‑metoden. Det är grunden för mer avancerade scenarier.

## Använda reguljära uttryck (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Reguljära uttryck ger dig kraftfull mönstermatchning, idealiskt för dynamiska platshållare eller komplexa ordgränser.

## Ignorera text i fält (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Ställ in `IgnoreFields` för att behålla sammanslagningsfält, sidnummer eller andra fältkoder orörda medan du ersätter omgivande innehåll.

## Ignorera text i raderade revisioner

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Detta förhindrar att text markerad för radering (spårade ändringar) ändras.

## Ignorera text i infogade revisioner

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Användbart när du vill behålla nyinfogad text intakt under en massersättning.

## Ersätta text med HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Här **replace text with html** genom att tillhandahålla en anpassad evaluator som analyserar HTML‑strängen och infogar lämpliga Word‑noder.

## Ersätta text i rubriker och sidfötter (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Målinriktad ersättning i rubriker eller sidfötter säkerställer att ditt dokumentvarumärke förblir konsekvent.

## Visa ändringar för rubrik‑ och sidfot‑ordning

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Detta exempel loggar ändringar, vilket hjälper dig att granska modifieringar av rubrik-/sidfot‑ordning.

## Ersätta text med fält

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Att injicera fält (t.ex. sammanslagningsfält) låter dig bygga dynamiska dokument som kan fyllas i senare.

## Ersätta med en evaluator

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Anpassade evaluatorer ger dig full programmatisk kontroll över ersättningstexten.

## Ersätta med regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Ett koncist sätt att utföra mönsterbaserade ersättningar i hela dokumentet.

## Känna igen och ersättningar inom ersättningsmönster

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Aktivera `UseSubstitutions` för att referera till fångstgrupper direkt i ersättningssträngen.

## Ersätta med en sträng (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Den enklaste formen av ersättning – perfekt för statiska platshållare.

## Använda legacy‑ordning

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Legacy‑ordning kan vara nödvändig när du hanterar äldre dokument som förlitar sig på den ursprungliga traverseringssekvensen.

## Ersätta text i en tabell

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Målinriktade ersättningar i tabeller förhindrar oavsiktliga ändringar på andra ställen i dokumentet.

## Vanliga problem och lösningar

- **HTML renderas inte korrekt** – Se till att din HTML är välformad och innehåller nödvändiga taggar (t.ex. `<p>`, `<table>`).  
- **Regex matchar inte** – Kom ihåg att escapera specialtecken och använd `Pattern.CASE_INSENSITIVE` om det behövs.  
- **Fält ersätts oavsiktligt** – Ställ in `options.setIgnoreFields(true)` för att skydda dem.  
- **Prestanda på stora dokument** – Använd `UseLegacyOrder` eller bearbeta sektioner individuellt för att minska minnesfotavtrycket.

## Vanliga frågor

**Q: Hur laddar jag ner Aspose.Words för Java?**  
A: Du kan ladda ner Aspose.Words för Java från webbplatsen genom att besöka [this link](https://releases.aspose.com/words/java/).

**Q: Kan jag använda reguljära uttryck för textersättning?**  
A: Ja, du kan använda reguljära uttryck för textersättning i Aspose.Words för Java. Detta gör att du kan utföra mer avancerade och flexibla sök‑ och ersättningsoperationer.

**Q: Hur kan jag ignorera text i fält under ersättning?**  
A: Ställ in `IgnoreFields`‑egenskapen i `FindReplaceOptions` till `true`. Detta exkluderar fältinnehåll såsom sammanslagningsfält från att bli ersatta.

**Q: Är det möjligt att ersätta text i rubriker och sidfötter?**  
A: Absolut. Åtkomst den önskade rubriken eller sidfoten via `HeaderFooterCollection` och tillämpa `replace`‑metoden med lämpliga alternativ.

**Q: Vad gör alternativet `UseLegacyOrder`?**  
A: `UseLegacyOrder` tvingar sök‑/ersättningsmotorn att traversera noder i den ursprungliga ordning som användes av äldre versioner av Aspose.Words, vilket kan vara användbart för kompatibilitet med äldre dokument.

**Last Updated:** 2026-01-03  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}