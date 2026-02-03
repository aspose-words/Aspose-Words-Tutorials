---
date: '2026-02-03'
description: Lär dig hur du konverterar docx till odt, exporterar dokument till ODT-schema
  1.1, använder olika måttenheter och lösenordsskyddar ODT-filer med Aspose.Words
  för Java.
keywords:
- Aspose.Words Java
- ODT conversion
- document security
title: konvertera docx till odt med Aspose.Words Java – Dokumentkonvertering och säkerhet
url: /sv/java/document-operations/aspose-words-java-document-conversion-security/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Behärska dokumenttering **convert sädda kännas överväldigande utan rätt verktyg. Denna handledning visar hur du **convert docx to odt** med **Aspose.Words för Java**, samtidigt som den täcker ODT 1.1‑schemakompatibilitet, anpassning av måttenheter och lösenordsskydd för ODT/OTT‑filer.

I den här guiden kommer du att lära dig hur du:
- Exporterar dokument som följer ODT 1.1‑specifikationerna.
- Använder olika måttenheter (centimeter eller tum) i ODT‑utdata.
- Krypterar ODT/OTT‑fåt oss?** Använd `OdtSaveOptions` med `Document.save()` i Aspose.Words för Java.  
- **Kan jag ange måttenhet vid export?** Ja, anropa `saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS)` eller `INCHES`.  
- **Hur skyddar jag ett ODT‑fil med lösenord?** Ställ in ett lösenord på `OdtSaveOptions` via `saveOptions.setPassword("yourPassword")`.  
- **Behöver jag en licens för dessa funktioner?** En gratis tillfällig licens fungerar för utvärdering; en full licens krävs för produktion.  
- **Vilken version av Aspose.Words stödjer dessa alternativ?** Version 25.3 eller senare inkluderar stöd för ODT 1.1‑schema och kryptering.

## Förutsättningar

Innan vi börjar, se till att du har följande konfigurerat:

### Nödvändiga bibliotek
Du behöver **Aspose.Words för Java** version 25.3 eller senare. Så här inkluderar du det i ditt projekt med Maven eller Gradle:

#### Maven:
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

#### Gradle:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Miljöinställning
Se till att Java är installerat på din maskin och att du har en IDE eller textredigerare redo för Java‑utveckling.

### Kunskapsförutsättningar
En grundläggande förståelse för Java‑programmering hjälper dig att följa exemplen smidigt.

## Konfigurera Aspose.Words

För att börja använda Aspose.Words, se först till att det är korrekt integrerat i ditt projekt. Här är stegen:

1. **Skaffa en licens**: Du kan få en gratis provlicens från [Aspose](https://purchase.aspose.com/temporary-license/) för att testa alla funktioner utan begränsningar.
2. **Grundläggande initiering**:
```java
import com.aspose.words.Document;

public class AsposeSetup {
    public static void main(String[] args) throws Exception {
        // Load a document from the disk
        Document doc = new Document("path/to/your/document.docx");
        
        // Save it to ODT format as an example usage
        doc.save("output/path/OdtSaveOptions.odt", com.aspose.words.SaveFormat.ODT);
    }
}
```

## Implementeringsguide

### Exportera dokument till ODT-schema 1.1

Denna funktion säkerställer att den exporterade filen följer ODT 1.1‑schemat, vilket är viktigt för kompatibilitet med äldre applikationer.

#### Översikt
Kodsnutten nedan visar hur du konfigurerar exportalternativ för schemakompatibilitet och val av måttenhet.

#### Steg‑för‑steg-implementering

**3.1 Configure Export Options**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

// Load your source Word document
Document document = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");

// Initialize ODT save options and configure schema compliance
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);
saveOptions.isStrictSchema11(true); // Set to true for ODT 1.1 compliance

// Save the document with these settings
document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt", saveOptions);
```

**3.2 Verify Export Settings**
After saving, you can double‑check that the measurement unit was applied correctly:
```java
import com.aspose.words.MeasurementUnits;

Document loadedDoc = new Document("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Odt11Schema.odt");
MeasurementUnits mu = loadedDoc.getLayoutOptions().getRevisionOptions().getMeasurementUnit();

assert mu == MeasurementUnits.CENTIMETERS;
```

### Använda olika måttenheter

Ibland behöver du exportera ODT‑filer med tum istället för centimeter, särskilt för dokument som riktar sig till en publik i USA.

#### Översikt
Du kan växla mellan metriska och imperiella enheter genom att justera `OdtSaveOptions`.

**3.3 Set Measurement Unit**
```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
// Choose your desired unit: CENTIMETERS or INCHES
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.CENTIMETERS);

document.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", saveOptions);
```

**3.4 Verify Measurement Unit in Styles**
To be absolutely sure the correct unit made it into the ODT package, inspect the `styles.xml` entry:
```java
if (saveOptions.getMeasureUnit() == OdtSaveMeasureUnit.CENTIMETERS) {
    assert TestUtil.docPackageFileContainsString(
        "<style:paragraph-properties fo:orphans=\"2\" fo:widows=\"2\" style:tab-stop-distance=\"1.27cm\" />",
        "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Measurements.odt", "styles.xml");
}
```

### Kryptera ODT/OTT‑dokument

Att skydda konfidentiella rapporter, kontrakt eller annat känsligt innehåll är ett måste. Aspose.Words låter dig lösenordsskydda ODT‑filer med bara några rader kod.

#### Översikt
Lösenordet du anger krävs varje gång dokumentet öppnas, vilket förhindrar obehörig åtkomst.

**3.5 Encrypt Document**
```java
import com.aspose.words.Document;
import com.aspose.words.OdtSaveOptions;

Document doc = new Document();
doc.getRange().appendText("Hello world!");

OdtSaveOptions saveOptions = new OdtSaveOptions(com.aspose.words.SaveFormat.ODT);
saveOptions.setPassword("@sposeEncrypted_1145");

// Save the document with encryption
doc.save("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt", saveOptions);
```

**3.6 Verify Encryption**
You can programmatically confirm that the file is encrypted and then load it with the correct password:
```java
import com.aspose.words.FileFormatUtil;
import com.aspose.words.LoadOptions;

FileFormatInfo docInfo = FileFormatUtil.detectFileFormat("YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt");
assert docInfo.isEncrypted();

// Load the document using the correct password
Document loadedDoc = new Document(
    "YOUR_OUTPUT_DIRECTORY/OdtSaveOptions.Encrypt.odt",
    new LoadOptions("@sposeEncrypted_1145")
);

assert loadedDoc.getText().trim() == "Hello world!";
```

## Praktiska tillämpningar

Här är några verkliga scenarier där dessa funktioner kommer till sin rätt:

1. **Företagsöverensstämmelse** – Export till ODT 1.1 garanterar att äldre kontorspaket kan öppna dina filer utan fel.  
2. **Internationalisering** – Genom att byta måttenhet kan du tillgodose både metriska och imperiella målgrupper utan manuell efterbehandling.  
3. **Dataskydd** – Lösenordsskydd av ODT/OTT‑filer skyddar konfidentiella kontrakt, finansiella rapporter eller personuppgifter och uppfyller regulatoriska krav.

## Prestandaöverväganden

För att hålla din konverteringsprocess snabb:

- Undvik att bädda in extremt högupplösta bilder om det inte är nödvändigt.  
- Håll dokumentstrukturen (stilar, sektioner) så enkel som möjligt.  
- Uppgradera regelbundet till den senaste versionen av Aspose.Words för Java för att dra nytta av prestandaförbättringar.

## Slutsats

I den här handledningen har du lärt dig hur du **convert docx to odt**, upprätthåller ODT 1.1‑schemakompatibilitet, anpassar måttenheter och krypterar ODT‑filer med **Aspose.Words för Java**. Dessa tekniker hjälper dig att leverera kompatibla, region‑anpassade och säkra dokument i en mängd affärsscenarier.

Redo att sätta dessa lösningar i praktiken? Gå till [Aspose.Words Documentation](https://reference.aspose.com/words/java/) för djupare insikter och fler exempel.

## Vanliga frågor

**Q: Hur säkerställer jag kompatibilitet med äldre ODT‑versioner?**  
A: Använd `saveOptions.isStrictSchema11(true)` för att tvinga ODT 1.1‑kompatibilitet.

**Q: Kan jag enkelt växla mellan metriska och imperiella enheter?**  
A: Ja, ställ in måttenheten i `OdtSaveOptions.setMeasureUnit()` till antingen `CENTIMETERS` eller `INCHES`.

**Q: Vad händer om mitt dokument inte krypteras som förväntat?**  
A: Verifiera att du anropade `saveOptions.setPassword()` innan du sparade och bekräfta kryptering med `FileFormatUtil.detectFileFormat()`.

**Q: Hur felsöker jag laddningsproblem för krypterade dokument?**  
A: Se till att rätt lösenord anges via `LoadOptions` när filen öppnas.

**Q: Finns det ett sätt att programatiskt kontrollera vilken måttenhet som användes?**  
A: Inspektera `styles.xml` i ODT‑paketet eller fråga `saveOptions.getMeasureUnit()` efter inläsning.

---

**Senast uppdaterad:** 2026-02-03  
**Testad med:** Aspose.Words for Java 25.3  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}