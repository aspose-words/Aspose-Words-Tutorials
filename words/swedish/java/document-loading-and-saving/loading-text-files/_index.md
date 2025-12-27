---
date: 2025-12-27
description: Lär dig hur du ställer in riktning, laddar txt-filer, tar bort mellanslag
  och konverterar txt till docx med Aspose.Words för Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Hur man ställer in riktning och laddar textfiler med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Så ställer du in riktning och laddar textfiler med Aspose.Words för Java

## Introduktion till att ladda textfiler med Aspose.Words för Java

I den här guiden får du veta **hur du ställer in riktning** när du laddar rena textdokument och ser praktiska sätt att **ladda txt**, **trimma mellanslag** och **konvertera txt till docx** med Aspose.Words för Java. Oavsett om du bygger en dokument‑konverteringstjänst eller behöver fin‑granulär kontroll över listdetektering, går den här handledningen igenom varje steg med tydliga förklaringar och färdig‑körbar kod.

## Snabba svar
- **Hur ställer jag in textriktning för en inläst TXT‑fil?** Använd `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` eller specificera `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Kan Aspose.Words upptäcka numrerade listor i ren text?** Ja – aktivera `DetectNumberingWithWhitespaces` i `TxtLoadOptions`.
- **Hur kan jag trimma inledande och avslutande mellanslag?** Ställ in `TxtLeadingSpacesOptions.TRIM` och `TxtTrailingSpacesOptions.TRIM`.
- **Är det möjligt att konvertera en TXT‑fil till DOCX i ett enda steg?** Ladda TXT‑filen med `TxtLoadOptions` och anropa `Document.save("output.docx")`.
- **Vilken Java‑version krävs?** Java 8+ räcker för Aspose.Words 24.x.

## Vad betyder “hur man ställer in riktning” i Aspose.Words?
När en textfil innehåller höger‑till‑vänster‑skript (t.ex. hebreiska eller arabiska) måste biblioteket känna till läsriktningen. `DocumentDirection`‑enumen låter dig **ställa in riktning** manuellt eller låta Aspose auto‑detektera den, vilket säkerställer korrekt layout och bidi‑formatering.

## Varför använda Aspose.Words för att ladda TXT‑filer?
- **Noggrann listdetektering** – hanterar numrerade, punktlistor och mellanslags‑avgränsade listor.
- **Fin‑granulär mellanslagshantering** – trimma eller bevara inledande/avslutande mellanslag.
- **Automatisk textriktningsdetektering** – perfekt för flerspråkiga dokument.
- **Enkel konvertering** – ladda en `.txt` och spara som `.docx`, `.pdf` eller något annat stödd format.

## Förutsättningar
- Java 8 eller nyare.
- Aspose.Words för Java‑biblioteket (lägg till Maven/Gradle‑beroendet eller JAR‑filen i ditt projekt).
- Grundläggande kunskap om Java‑I/O‑strömmar.

## Steg‑för‑steg‑guide

### Steg 1: Detektera listor (hur man laddar txt)
För att ladda ett textdokument och automatiskt detektera listor, skapa en `TxtLoadOptions`‑instans och aktivera listdetektering. Koden nedan visar flera liststilar och aktiverar mellanslags‑medveten numrering.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Proffstips:** Om du bara behöver grundläggande listdetektering kan du hoppa över mellanslagsalternativet – Aspose kommer ändå att känna igen standardmönstren `1.` och `1)`.

### Steg 2: Hantera mellanslagsalternativ (hur man trimmar mellanslag)
Inledande och avslutande mellanslag orsakar ofta formateringsproblem. Använd `TxtLeadingSpacesOptions` och `TxtTrailingSpacesOptions` för att styra detta beteende.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Varför det är viktigt:** Att trimma mellanslag förhindrar oönskad indragning i den resulterande DOCX‑filen, vilket gör dokumentet snyggt utan manuell efterbehandling.

### Steg 3: Styr textriktning (hur man ställer in riktning)
För språk som skrivs från höger till vänster, ställ in dokumentriktningen innan du laddar. Exemplet nedan laddar en hebreisk textfil och skriver ut bidi‑flaggan för att bekräfta riktningen.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Vanligt fallgropp:** Att glömma att sätta `DocumentDirection` kan leda till förvrängd arabisk/hebreisk text där tecken visas i fel ordning.

### Komplett källkod för att ladda textfiler med Aspose.Words för Java
Nedan finns den fullständiga, färdig‑körbara källkoden som kombinerar listdetektering, mellanslagshantering och riktningskontroll. Du kan kopiera‑klistra in den i en enda klass och köra de tre testmetoderna var för sig.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Vanliga problem och lösningar
| Problem | Orsak | Lösning |
|-------|-------|-----|
| Listor upptäcks inte | `DetectNumberingWithWhitespaces` är `false` för mellanslags‑avgränsade listor | Aktivera `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Extra indragning efter laddning | Inledande mellanslag bevarades | Sätt `TxtLeadingSpacesOptions.TRIM` |
| Hebreisk text visas baklänges | Dokumentriktning ej satt eller satt till `LEFT_TO_RIGHT` | Använd `DocumentDirection.AUTO` eller `RIGHT_TO_LEFT` |
| Utdata‑DOCX är tom | Inmatningsströmmen återställdes inte innan andra laddningen | Skapa en ny `ByteArrayInputStream` för varje laddningsanrop |

## Vanliga frågor

### Q: Vad är Aspose.Words för Java?
A: Aspose.Words för Java är ett kraftfullt dokumentbehandlingsbibliotek som låter utvecklare skapa, manipulera och konvertera Word‑dokument programatiskt i Java‑applikationer. Det stödjer ett brett spektrum av funktioner, från enkel textladdning till komplex formatering och konvertering.

### Q: Hur kommer jag igång med Aspose.Words för Java?
A: 1. Ladda ner och installera Aspose.Words för Java‑biblioteket. 2. Läs dokumentationen på [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) för detaljerad information och exempel. 3. Utforska exempel‑kod och handledningar för att lära dig använda biblioteket effektivt.

### Q: Hur laddar jag ett textdokument med Aspose.Words för Java?
A: Använd klassen `TxtLoadOptions` tillsammans med `Document`‑konstruktorn. Specificera alternativ som listdetektering, mellanslagshantering eller textriktning enligt exemplen i steg‑för‑steg‑avsnitten ovan.

### Q: Kan jag konvertera ett inläst textdokument till andra format?
A: Ja. Efter att ha laddat TXT‑filen i ett `Document`‑objekt, anropa `doc.save("output.pdf")`, `doc.save("output.docx")` eller något annat stödd format.

### Q: Hur hanterar jag mellanslag i inlästa textdokument?
A: Styr inledande och avslutande mellanslag med `TxtLeadingSpacesOptions` och `TxtTrailingSpacesOptions`. Sätt dem till `TRIM` för att ta bort oönskat whitespace, eller till `PRESERVE` om du vill behålla originalavståndet.

### Q: Vad är betydelsen av textriktning i Aspose.Words för Java?
A: Textriktning säkerställer korrekt rendering av höger‑till‑vänster‑skript (hebreiska, arabiska osv.). Genom att sätta `DocumentDirection` garanteras att bidi‑text visas korrekt i det slutliga dokumentet.

### Q: Var kan jag hitta fler resurser och support för Aspose.Words för Java?
A: Besök [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) för API‑referenser, kodexempel och detaljerade guider. Du kan också gå med i Aspose‑community‑forum eller kontakta Aspose‑support för specifika frågor.

### Q: Är Aspose.Words för Java lämpligt för kommersiella projekt?
A: Ja. Det erbjuder licensalternativ för både personligt och kommersiellt bruk. Granska licensvillkoren på Aspose‑webbplatsen för att välja rätt plan för ditt projekt.

## Slutsats
Du har nu ett komplett verktyg för att **ladda txt‑filer**, **detektera listor**, **trimma mellanslag** och **ställa in riktning** när du konverterar ren text till rika Word‑dokument med Aspose.Words för Java. Använd dessa mönster för att automatisera dokumentarbetsflöden, förbättra flerspråkigt stöd och säkerställa rena, professionella resultat varje gång.

---

**Senast uppdaterad:** 2025-12-27  
**Testat med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}