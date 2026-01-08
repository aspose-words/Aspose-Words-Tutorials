---
date: 2025-12-20
description: Lär dig hur du laddar HTML och konverterar HTML till DOCX med Aspose.Words
  för Java. En steg‑för‑steg‑guide visar hur du sparar DOCX‑filer och använder strukturerade
  dokumenttaggar.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Hur man laddar HTML och sparar som DOCX med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Så laddar du HTML och sparar som DOCX med Aspose.Words för Java

## Introduktion till att ladda och spara HTML-dokument med Aspose.Words för Java

I den här artikeln kommer vi att utforska **hur man laddar html** och sparar den som en DOCX‑fil med hjälp av Aspose.Words för Java‑biblioteket. Aspose.Words är ett kraftfullt API som låter dig manipulera Word‑dokument programmässigt, och det inkluderar robust stöd för HTML‑import/‑export. Vi går igenom hela processen, från att konfigurera laddningsalternativen till att spara resultatet som ett Word‑dokument.

## Snabba svar
- **Vad är den primära klassen för att ladda HTML?** `Document` tillsammans med `HtmlLoadOptions`.
- **Vilket alternativ aktiverar Structured Document Tags?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Kan jag konvertera HTML till DOCX i ett steg?** Ja – ladda HTML och anropa `doc.save(...".docx")`.
- **Behöver jag en licens för utveckling?** En gratis provversion fungerar för testning; en kommersiell licens krävs för produktion.
- **Vilken Java‑version krävs?** Java 8 eller högre stöds.

## Vad betyder “how to load html” i samband med Aspose.Words?

Att ladda HTML innebär att läsa en HTML‑sträng eller -fil och konvertera den till ett Aspose.Words `Document`‑objekt. Detta objekt kan sedan redigeras, formateras eller sparas till vilket format som helst som stöds av API‑et, såsom DOCX, PDF eller RTF.

## Varför använda Aspose.Words för HTML‑till‑DOCX‑konvertering?
- **Bevarar layout** – tabeller, listor och bilder behålls intakta.
- **Stöder Structured Document Tags** – idealiskt för att skapa innehållskontroller i Word.
- **Ingen Microsoft Office krävs** – fungerar på vilken server‑ eller molnmiljö som helst.
- **Hög prestanda** – bearbetar stora HTML‑filer snabbt.

## Prerequisites

1. **Aspose.Words för Java‑bibliotek** – ladda ner det från [here](https://releases.aspose.com/words/java/).
2. **Java‑utvecklingsmiljö** – JDK 8+ installerat och konfigurerat.
3. **Grundläggande kunskap om Java I/O** – vi kommer att använda `ByteArrayInputStream` för att mata in HTML‑strängen.

## Så laddar du HTML‑dokument

Nedan är ett koncist exempel som demonstrerar hur man laddar ett HTML‑snutt samtidigt som **structured document tag**‑funktionen aktiveras.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Förklaring**

- Vi skapar en `HTML`‑sträng som innehåller en enkel `<select>`‑kontroll.
- `HtmlLoadOptions` låter oss specificera hur HTML ska tolkas. Genom att sätta den föredragna kontrolltypen till `STRUCTURED_DOCUMENT_TAG` talar vi om för Aspose.Words att konvertera HTML‑formulärkontroller till Word‑innehållskontroller.
- `Document`‑konstruktorn läser HTML från en `ByteArrayInputStream` med UTF‑8‑kodning.

## Så sparar du som DOCX (konvertera HTML till DOCX)

När HTML har laddats in i ett `Document` är det enkelt att spara det som en DOCX‑fil:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Byt ut `"Your Directory Path"` mot den faktiska mappen där du vill att utdatafilen ska placeras.

## Komplett källkod för att ladda och spara HTML‑dokument

Nedan är det fullständiga, färdiga exemplet som kombinerar laddnings- och sparstegen. Kopiera och klistra in det i din IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Vanliga fallgropar & tips

| Problem | Varför det händer | Hur man åtgärdar |
|---------|-------------------|------------------|
| **Saknade typsnitt** | HTML refererar till typsnitt som inte är installerade på servern. | Bädda in typsnitt i DOCX med `FontSettings` eller se till att de nödvändiga typsnitten finns tillgängliga. |
| **Bilder visas inte** | Relativa bildvägar kan inte lösas. | Använd absoluta URL:er eller ladda bilder i ett `MemoryStream` och sätt `HtmlLoadOptions.setImageSavingCallback`. |
| **Kontrolltyp konverteras inte** | `setPreferredControlType` är inte satt eller är satt till fel enum. | Verifiera att du använder `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Kodningsproblem** | HTML‑strängen är kodad med ett annat teckensnitt (charset). | Använd alltid `StandardCharsets.UTF_8` när du konverterar strängen till byte. |

## Vanliga frågor

### Hur installerar jag Aspose.Words för Java?
Aspose.Words för Java kan laddas ner från [here](https://releases.aspose.com/words/java/). Följ installationsguiden på nedladdningssidan för att lägga till JAR‑filerna i ditt projekts classpath.

### Kan jag ladda komplexa HTML‑dokument med Aspose.Words?
Ja, Aspose.Words för Java kan hantera komplex HTML, inklusive nästlade tabeller, CSS‑styling och JavaScript‑fria interaktiva element. Justera `HtmlLoadOptions` (t.ex. `setLoadImages` eller `setCssStyleSheetFileName`) för att finjustera importen.

### Vilka andra dokumentformat stöder Aspose.Words?
Aspose.Words stöder DOC, DOCX, RTF, HTML, PDF, EPUB, XPS och många fler. API‑et möjliggör enradig sparning till något av dessa format.

### Är Aspose.Words lämpligt för dokumentautomatisering på företagsnivå?
Absolut. Det används av stora företag för automatiserad rapportgenerering, masskonvertering av dokument och server‑sidig dokumentbehandling utan beroenden av Microsoft Office.

### Var kan jag hitta mer dokumentation och exempel för Aspose.Words för Java?
Du kan utforska den fullständiga API‑referensen och ytterligare handledningar på Aspose.Words för Java‑dokumentationssidan: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Senast uppdaterad:** 2025-12-20  
**Testat med:** Aspose.Words för Java 24.12 (senaste vid skrivtillfället)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}