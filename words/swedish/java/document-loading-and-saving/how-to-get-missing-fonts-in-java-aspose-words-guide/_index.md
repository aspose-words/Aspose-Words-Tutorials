---
category: general
date: 2026-02-15
description: Lär dig hur du får tag på saknade teckensnitt när du laddar ett Word‑dokument
  i Java med Aspose.Words. Inkluderar varningsåteranrop och hantering av teckensnittssubstitution.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: sv
og_description: Hur du får tag på saknade teckensnitt i Java med Aspose.Words. Upptäck
  varningsåteranrop, hantering av teckensnittssubstitution och bästa praxis för dokumentbehandling.
og_title: Hur du hämtar saknade teckensnitt i Java – Aspose.Words‑guide
tags:
- Aspose.Words
- Java
- Font Management
title: Hur man hämtar saknade teckensnitt i Java – Aspose.Words guide
url: /sv/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man får saknade teckensnitt i Java – Aspose.Words Guide

Har du någonsin öppnat ett Word‑dokument i Java bara för att se märkliga teckensnittsbyten och undrat **hur man får saknade teckensnitt**? Du är inte den första som stöter på den överraskningen. I många företagsapplikationer kan varningar om saknade teckensnitt förstöra den visuella integriteten i rapporter, kontrakt eller marknadsföringsmaterial.

Den goda nyheten? Aspose.Words ger dig ett rent sätt att fånga dessa varningar via en callback, så att du kan logga, ersätta eller till och med varna användare innan dokumentet renderas. I den här handledningen går vi igenom ett komplett, körbart exempel som visar **hur man får saknade teckensnitt**, förklarar varför callbacken är viktig och täcker några edge‑case‑trick du kan behöva i verkliga projekt.

> **Pro tip:** Om du redan använder Aspose.Words 22.12 eller nyare fungerar API‑et nedan direkt utan extra konfiguration.

---

![Diagram som illustrerar hur man får saknade teckensnitt med Aspose.Words varnings‑callback](how-to-get-missing-fonts-diagram.png "diagram för hur man får saknade teckensnitt")

## Vad den här handledningen täcker

- Att konfigurera en **Java LoadOptions varnings‑callback** för att fånga teckensnitt‑substitutionsvarningar.  
- Filtrera varningarna så att du bara ser de som rör saknade teckensnitt.  
- Skriva ut en tydlig, mänskligt läsbar rapport om vilka teckensnitt som ersattes och vad de ersattes med.  
- Tips för att hantera stora dokument, anpassa varningsnivån och integrera lösningen i en större bearbetningspipeline.

När du är klar med den här guiden kan du svara på frågan “**hur man får saknade teckensnitt**?” med ett färdigt kodexempel och en solid förståelse för de underliggande mekanismerna.

### Förutsättningar

- Java 8 eller nyare installerat.  
- Aspose.Words för Java‑biblioteket (ladda ner från den officiella webbplatsen eller lägg till via Maven/Gradle).  
- Ett Word‑dokument som refererar till ett teckensnitt som inte är installerat på din maskin (t.ex. `MissingFont.docx`).  

Om du saknar någon av dessa, hämta biblioteket nu—att lägga till det i Maven är så enkelt som:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Steg 1: Förbered en samling för teckensnitt‑substitutionsvarningar

Innan vi laddar dokumentet behöver vi en plats att lagra eventuella varningar som Aspose.Words avger. En `ArrayList<WarningInfo>` fungerar bra eftersom den bevarar ordningen och låter oss iterera senare.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Varför detta är viktigt:* Varnings‑callbacken kan avfyras dussintals gånger för en enda fil—tänk på varje saknad glyf, varje inbäddat bildproblem osv. Genom att samla dem först håller du inläsningsfasen snabb och skjuter bearbetningen till en kontrollerad loop.

---

## Steg 2: Konfigurera LoadOptions med en varnings‑callback

Aspose.Words låter dig ansluta en `IWarningCallback`. Inuti callbacken lägger vi till varje `WarningInfo` i vår lista från Steg 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Förklaring:* `warning`‑metoden anropas **synkront** under dokumentladdning. Genom att helt enkelt pusha `WarningInfo` in i `fontWarnings` undviker vi tung I/O (som att logga till en fil) som kan sakta ner inläsningen. Detta samla‑sedan‑bearbeta‑mönster är det rekommenderade sättet att hantera stora varningssatser.

---

## Steg 3: Ladda dokumentet med de konfigurerade alternativen

Nu läser vi faktiskt Word‑filen. Om dokumentet innehåller teckensnitt som inte är installerade kommer Aspose.Words automatiskt att ersätta dem och avfyra varnings‑callbacken vi just kopplat.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Vad händer under huven?* Aspose.Words analyserar filens teckensnittstabell, jämför den med teckensnitten som finns på värd‑OS‑et, och för varje saknad post skapar den ett `WarningInfo` med `WarningSource.FontSubstitution`. Den källan är nyckeln vi använder för att isolera varningarna om saknade teckensnitt.

---

## Steg 4: Filtrera och visa endast teckensnitt‑substitutionsvarningar

Efter inläsning kan `fontWarnings` innehålla en blandning av meddelanden (t.ex. föråldrade funktioner, bildproblem). Vi är bara intresserade av saknade teckensnitt, så vi loopar igenom listan och skriver ut en koncis rapport.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Exempel på utdata**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Varför detta är användbart:* `description`‑fältet talar om vilket teckensnitt dokumentet efterfrågade, medan `additionalInfo` visar vad Aspose.Words faktiskt använde. Med den informationen kan du:

- Be användaren installera det saknade teckensnittet.  
- Programatiskt bädda in ett ersättningsteckensnitt i dokumentet (`doc.getFontInfos().add(...)`).  
- Logga händelsen för efterlevnadsrevisioner.

---

## Hantera edge‑cases och vanliga variationer

### 1. Undertrycka icke‑teckensnittsvarningar

Om du bara vill ha teckensnittsrelaterade meddelanden kan du strama åt callbacken:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Detta minskar minnesanvändningen när du bearbetar enorma satser.

### 2. Justera varningsallvarlighet

Aspose.Words kategoriserar varningar med `WarningType`. För saknade teckensnitt ser du vanligtvis `WarningType.FontSubstitution`. Om du vill behandla dem som fel (t.ex. avbryta inläsning) kastar du ett undantag i callbacken:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Arbeta med strömmar istället för filer

Ibland kommer dokument från en databas eller ett HTTP‑anrop. Samma tillvägagångssätt fungerar med en `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Kom bara ihåg att stänga strömmen efter inläsning.

### 4. Använda en anpassad teckensnittsmapp

Om du har en samling företags‑teckensnitt lagrade på en gemensam enhet, peka Aspose.Words till den mappen:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Nu kommer biblioteket att leta där *innan* det faller tillbaka på systemteckensnitt, vilket dramatiskt minskar antalet varningar om saknade teckensnitt.

---

## Fullt fungerande exempel

Sätter vi ihop allt får du en självständig klass som du kan slänga in i vilket Java‑projekt som helst:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Kör detta program så får du en prydlig lista över varje teckensnitt som Aspose.Words var tvungen att ersätta. Inga extra bibliotek, ingen dold magi—bara ren Java och kraften i **Aspose.Words missing font**‑API:t.

---

## Slutsats

Vi har besvarat kärnfrågan **hur man får saknade teckensnitt** i en Java‑miljö med Aspose.Words. Genom att fästa en `LoadOptions`‑varnings‑callback, samla `WarningInfo`‑objekt och filtrera på `FontSubstitution`‑källor får du full insyn i teckensnittsrelaterade problem innan någon rendering sker. Tillvägagångssättet skalar från enkla fil‑verktyg till massiva batch‑processorer och är flexibelt nog att hantera anpassade teckensnittsmappar, allvarlighets‑hantering eller strömbaserade indata.

Nästa steg? Prova att bädda in de ersatta teckensnitten direkt i dokumentet (`doc.getFontInfos().add(...)`) så att den slutgiltiga filen blir helt självförsörjande, eller integrera varningsrapporten i en övervakningsdashboard. Du kan också utforska relaterade ämnen som **document processing Java**, **Aspose.Words font substitution warning** och **Java LoadOptions warning callback** för att fördjupa din expertis.

Lycka till med kodningen, och må dina dokument alltid renderas med de teckensnitt du förväntar dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}