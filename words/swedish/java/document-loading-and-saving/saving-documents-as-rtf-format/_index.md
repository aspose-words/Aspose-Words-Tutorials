---
date: 2025-12-24
description: Lär dig hur du konverterar Word till RTF med Aspose.Words för Java. Denna
  steg‑för‑steg‑handledning visar hur du laddar en DOCX, konfigurerar RTF‑sparalternativ
  och sparar som rik text.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Konvertera Word till RTF med Aspose.Words för Java-handledning
url: /sv/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera Word till RTF med Aspose.Words för Java

I den här handledningen kommer du att lära dig **hur man konverterar Word till RTF** snabbt och pålitligt med Aspose.Words för Java. Att konvertera en DOCX till det rika textformatet RTF är ett vanligt krav när du behöver bred kompatibilitet med äldre ordbehandlare, e‑postklienter eller dokumentarkiveringssystem. Vi går igenom hur du laddar ett Word‑dokument i Java, justerar RTF‑sparalternativen (inklusive att spara bilder som WMF), och slutligen skriver utdatafilen.

## Snabba svar
- **Vad betyder “convert word to rtf”?** Det omvandlar en DOCX/Word‑fil till Rich Text Format samtidigt som text, stilar och eventuellt bilder bevaras.  
- **Behöver jag en licens?** En gratis provversion fungerar för utveckling; en kommersiell licens krävs för produktion.  
- **Vilken Java‑version stöds?** Aspose.Words för Java stödjer Java 8 och högre.  
- **Kan jag behålla bilder vid konvertering?** Ja – använd `saveImagesAsWmf`‑alternativet för att bädda in bilder som WMF i RTF‑filen.  
- **Hur lång tid tar konverteringen?** Vanligtvis under en sekund för standarddokument; större filer kan ta några sekunder.

## Vad är “convert word to rtf”?
Att konvertera ett Word‑dokument till RTF skapar en plattformsoberoende fil som lagrar text, formatering och eventuellt bilder i en ren‑text‑baserad markup. Detta gör att dokumentet kan visas i nästan alla ordbehandlare utan att förlora layout.

## Varför använda Aspose.Words för Java för att spara som rich text?
- **Fullständig trohet** – Alla Word‑funktioner (stilar, tabeller, sidhuvuden/sidfötter) bevaras.  
- **Ingen Microsoft Office krävs** – Fungerar på vilken server eller molnmiljö som helst.  
- **Finjusterad kontroll** – Sparalternativen låter dig bestämma hur bilder lagras, vilken kodning som används och mer.

## Förutsättningar
1. **Aspose.Words för Java‑bibliotek** – Ladda ner och lägg till JAR‑filen i ditt projekt från [here](https://releases.aspose.com/words/java/).  
2. **En källa Word‑fil** – Till exempel `Document.docx` som du vill spara som RTF.  
3. **Java‑utvecklingsmiljö** – JDK 8+ och din favorit‑IDE.

## Steg 1: Ladda Word‑dokumentet (load word document java)
Först laddas den befintliga DOCX‑filen in i ett `Document`‑objekt. Detta är grunden för all konvertering.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Proffstips:** Använd absoluta sökvägar eller class‑path‑resurser för att undvika `FileNotFoundException`.

## Steg 2: Konfigurera RTF‑sparalternativ (save images as wmf)
Aspose.Words erbjuder klassen `RtfSaveOptions` för att finjustera utdata. I detta exempel aktiverar vi **save images as WMF**, vilket är det föredragna formatet för RTF‑filer.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Du kan också justera andra inställningar, såsom `saveOptions.setEncoding(Charset.forName("UTF-8"))` om du behöver en specifik teckenkodning.

## Steg 3: Spara dokumentet som RTF (save docx as rtf)
Skriv nu ut dokumentet med de konfigurerade alternativen. Detta steg **sparar DOCX som RTF**, vilket skapar en rich‑text‑fil klar för distribution.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Komplett källkod för att konvertera Word till RTF
Nedan är den kompakta versionen som du kan kopiera‑klistra in i en Java‑klass. Den demonstrerar **save as rich text** med WMF‑bildalternativet i ett enda block.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Vanliga fallgropar och felsökning
| Problem | Orsak | Lösning |
|-------|--------|-----|
| Utdata‑RTF är tom | Källfilen hittades inte eller laddades inte | Verifiera sökvägen i `new Document(...)` |
| Bilder saknas | `saveImagesAsWmf` är satt till `false` | Aktivera `saveOptions.setSaveImagesAsWmf(true)` |
| Felaktiga tecken | Fel kodning | Ange `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Vanliga frågor

**Q: Hur ändrar jag andra RTF‑sparalternativ?**  
A: Använd klassen `RtfSaveOptions` – den erbjuder egenskaper för komprimering, teckensnitt och mer. Se Aspose.Words Java API‑dokumentationen för hela listan.

**Q: Kan jag spara RTF‑dokumentet med en annan kodning?**  
A: Ja. Anropa `saveOptions.setEncoding(Charset.forName("UTF-8"))` (eller någon annan stödjande teckenuppsättning) före sparning.

**Q: Är det möjligt att spara RTF‑dokumentet utan bilder?**  
A: Absolut. Ange `saveOptions.setSaveImagesAsWmf(false)` för att utesluta bilder från utdata.

**Q: Hur bör jag hantera undantag under konverteringen?**  
A: Omge laddnings‑ och sparningsanropen med ett try‑catch‑block som fångar `Exception`. Logga felet och eventuellt kasta ett eget undantag för din applikation.

**Q: Fungerar detta för lösenordsskyddade Word‑filer?**  
A: Ladda dokumentet med ett `LoadOptions`‑objekt som innehåller lösenordet, och fortsätt sedan med samma sparsteg.

## Slutsats
Du har nu en komplett, produktionsklar metod för att **konvertera Word till RTF** med Aspose.Words för Java. Genom att ladda DOCX, konfigurera `RtfSaveOptions` (inklusive **save images as WMF**) och anropa `doc.save(...)` kan du generera högkvalitativa rich‑text‑filer som fungerar överallt. Känn dig fri att utforska ytterligare sparalternativ för att anpassa utdata efter dina exakta behov.

---

**Senast uppdaterad:** 2025-12-24  
**Testat med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}