---
category: general
date: 2026-02-18
description: Skapa laddningsalternativ i Java för att upptäcka saknade teckensnitt
  och lär dig hur du laddar DOCX-filer med en varningsåteruppringning.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: sv
og_description: Skapa laddningsalternativ i Java för att upptäcka saknade teckensnitt
  och lär dig hur du laddar DOCX-filer med en varningsåteruppringning.
og_title: Skapa laddningsalternativ i Java – Upptäck saknade teckensnitt & hur man
  laddar DOCX
tags:
- java
- aspose-words
- document-processing
title: Skapa laddningsalternativ i Java – Detektera saknade teckensnitt och hur man
  laddar DOCX
url: /sv/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Load Options i Java – Upptäck saknade typsnitt & hur du laddar DOCX

Har du någonsin funderat på hur du **skapar load options** som inte bara läser en DOCX utan också talar om när ett typsnitt saknas? Du är inte ensam. Saknade typsnitt kan förvandla ett perfekt formaterat dokument till ett rörigt kaos, och att upptäcka dem tidigt sparar timmar av felsökning. I den här handledningen går vi igenom exakt hur du **upptäcker saknade typsnitt** samtidigt som vi visar dig **hur du laddar DOCX**‑filer med en anpassad varnings‑callback.

## Vad du kommer att lära dig

- Hur du instansierar `LoadOptions` och konfigurerar en varnings‑handler.  
- Varför varnings‑callbacken är avgörande för att fånga problem med typsnittssubstitution.  
- Den exakta koden som behövs för att **ladda en DOCX**‑fil på ett säkert sätt, samt några praktiska tips för verkliga projekt.  
- Hantering av kantfall, som att hantera andra varningstyper eller ladda PDF‑filer med samma tillvägagångssätt.

Ingen extern dokumentation behövs – allt du behöver finns här.

## Förutsättningar

- Java 17 eller senare (API:et fungerar på äldre versioner, men 17 är den optimala).  
- Aspose.Words for Java‑biblioteket tillagt i ditt projekt (`aspose-words-x.x.jar`).  
- Grundläggande förståelse för Java‑undantagshantering.  

Om du har detta, låt oss dyka ner.

![Diagram som visar flödet för att skapa load options, sätta en varnings‑callback och ladda en DOCX‑fil](/images/create-load-options-diagram.png){: .center-image alt="Diagram över flödet för att skapa Load Options"}

## Steg 1: Skapa Load Options (Hur du laddar DOCX)

Det första du måste göra är att **skapa load options**. Detta objekt talar om för Aspose.Words hur det ska bete sig när det öppnar en fil. Tänk på det som en uppsättning instruktioner du ger biblioteket innan det ens ser DOCX‑filen.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Varför inte bara anropa `new Document("file.docx")`? För utan `LoadOptions` förlorar du möjligheten att reagera på varningar – som saknade typsnitt – tills efter att dokumentet redan har laddats, vilket kan vara för sent för vissa arbetsflöden.

## Steg 2: Ställ in en varnings‑callback för att upptäcka saknade typsnitt

Nu fäster vi en callback som kommer att anropas varje gång Aspose.Words stöter på en situation som den vill varna dig för. I vårt fall är vi intresserade av `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Några saker att notera:

- **Varför en callback?** Den körs *under* laddningsprocessen, vilket ger dig möjlighet att logga eller till och med avbryta operationen innan dokumentet är helt materialiserat.  
- **Varför kontrollera `WarningType.FONT_SUBSTITUTION`?** Det är exakt det enum‑värde Aspose.Words använder för scenarier med saknade typsnitt. Andra varningstyper (t.ex. `TABLE_STRUCTURE`) kan filtreras på liknande sätt om du behöver dem.  
- **Prestandatips:** Callbacken är lättviktig; undvik tunga I/O‑operationer i den. Om du måste skriva till en fil, köa meddelandena och skriv ut dem efter laddning.

## Steg 3: Ladda DOCX‑filen med de konfigurerade alternativen

Med alternativen och callbacken på plats kan du äntligen ladda DOCX‑filen. Detta är delen som svarar på **hur du laddar docx** samtidigt som du respekterar de varningar du ställt in.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Vad händer under huven?** När filen strömmas in kontrollerar Aspose.Words varje typsnittreferens. Om ett refererat typsnitt inte är installerat, triggas varnings‑callbacken vi definierade tidigare. Du får utdata som:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Den omedelbara återkopplingen är ovärderlig när du bearbetar batcher av filer på en server.

## Fullt fungerande exempel

Sätter vi ihop allt får du ett självständigt program som du kan kopiera och klistra in i din IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Förväntad utdata**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Om filen inte innehåller några saknade typsnitt förblir callbacken tyst och raden “DOCX loaded” visas.

## Pro‑tips & kantfall

| Situation | Vad du ska göra |
|-----------|-----------------|
| **Flera saknade typsnitt** | Callbacken avfyras för varje typsnitt, så du får en rad per typsnitt. Samla dem i en `List<String>` om du senare behöver en sammanfattning. |
| **Du vill också fånga andra varningar** | Lägg till `else if`‑grenar för `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` osv. |
| **Laddar stora DOCX‑filer** | Använd `LoadOptions.setLoadFormat(LoadFormat.DOCX)` för att ge en hint om formatet och snabba upp upptäckten. |
| **Kör i en webbtjänst** | Undvik `System.out.println`; injicera istället en logger (`SLF4J`, `Log4j`) i callbacken. |
| **Typsnitt installeras vid körning** | Efter att ha upptäckt ett saknat typsnitt kan du programatiskt ladda det via `GraphicsEnvironment.registerFont(...)` och ladda om dokumentet. |

## Varför detta tillvägagångssätt slår “endast try‑catch”

Många utvecklare omsluter helt enkelt `new Document(...)` med ett try‑catch‑block i hopp om att ett undantag ska meddela dem om saknade typsnitt. Tyvärr behandlar Aspose.Words typsnittssubstitution som en *varning*, inte ett fel, så inget undantag kastas. Genom att **skapa load options** och fästa en varnings‑callback får du deterministisk insikt i typsnittsproblem utan att offra prestanda.

## Nästa steg

- **Upptäck saknade typsnitt i PDF‑filer** – samma `LoadOptions`‑mönster fungerar för PDF, byt bara filväg och laddningsformat.  
- **Automatisera typsnittsinstallation** – kombinera callbacken med ett skript som hämtar saknade typsnitt från ett gemensamt arkiv.  
- **Utforska andra varningstyper** – Aspose.Words kan varna dig om föråldrade taggar, komplexa tabeller och mer.  

Känn dig fri att experimentera: byt ut `Document`‑konstruktorn mot en ström (`new Document(InputStream, loadOptions)`) om du arbetar med data i minnet, eller kedja flera callbacks med ett composite‑mönster för storskaliga bearbetningspipeline‑lösningar.

---

### TL;DR

Vi har visat hur du **skapar load options** i Java, ställer in en callback som **upptäcker saknade typsnitt**, och slutligen **laddar en DOCX**‑fil på ett säkert sätt. Med bara tre koncisa steg har du nu ett återanvändbart mönster som kan droppas in i vilket Aspose.Words‑projekt som helst.

Har du frågor om andra filformat eller behöver hjälp med att finjustera callbacken för din specifika miljö? Lämna en kommentar nedan, och lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}