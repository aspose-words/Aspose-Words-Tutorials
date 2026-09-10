---
date: 2025-12-27
description: Lär dig hur du ställer in LoadOptions i Aspose.Words för Java, inklusive
  hur du anger temporär mapp, sätter Word-version, konverterar metafiler till PNG
  och konverterar form till matematik för flexibel dokumentbehandling.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Hur man ställer in LoadOptions i Aspose.Words för Java
url: /sv/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ställer in LoadOptions i Aspose.Words för Java

I den här handledningen går vi igenom **hur man ställer in LoadOptions** för en rad verkliga scenarier när du arbetar med Aspose.Words för Java. LoadOptions ger dig fin‑granulär kontroll över hur ett dokument öppnas—oavsett om du behöver uppdatera smutsiga fält, arbeta med krypterade filer, konvertera former till Office Math, eller tala om för biblioteket var temporära data ska lagras. När du är klar kan du anpassa laddningsbeteendet så att det exakt matchar dina applikationskrav.

## Snabba svar
- **Vad är LoadOptions?** Ett konfigurationsobjekt som påverkar hur Aspose.Words laddar ett dokument.  
- **Kan jag uppdatera fält vid laddning?** Ja—sätt `setUpdateDirtyFields(true)`.  
- **Hur öppnar jag en lösenordsskyddad fil?** Skicka lösenordet till `LoadOptions`‑konstruktorn.  
- **Är det möjligt att ändra den temporära mappen?** Använd `setTempFolder("path")`.  
- **Vilken metod konverterar former till Office Math?** `setConvertShapeToOfficeMath(true)`.

## Varför använda LoadOptions?
LoadOptions låter dig undvika efter‑laddningsbearbetning, minska minnesanvändning och säkerställa att dokumentet tolkas exakt som du behöver. Till exempel förhindrar konvertering av metafiler till PNG under laddning senare rasteriseringsproblem, och att ange MS Word‑versionen hjälper till att bevara layoutens noggrannhet när du hanterar äldre filer.

## Förutsättningar
- Java 17 eller senare  
- Aspose.Words för Java (senaste version)  
- En giltig Aspose‑licens för produktionsbruk  

## Steg‑för‑steg‑guide

### Uppdatera smutsiga fält

När ett dokument innehåller fält som har redigerats men inte uppdaterats kan du låta Aspose.Words automatiskt uppdatera dem under laddning.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Anropet `setUpdateDirtyFields(true)` säkerställer att alla smutsiga fält räknas om så snart dokumentet öppnas.*

### Ladda krypterat dokument

Om din källfil är lösenordsskyddad, ange lösenordet när du skapar `LoadOptions`‑instansen. Du kan också sätta ett nytt lösenord när du sparar till ett annat format.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Konvertera form till Office Math

Vissa äldre dokument lagrar ekvationer som ritade former. Genom att aktivera detta alternativ konverteras dessa former till inbyggda Office Math‑objekt, vilket är enklare att redigera senare.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Ange MS Word‑version

Att specificera mål‑Word‑version hjälper biblioteket att välja rätt renderingsregler, särskilt när du arbetar med äldre filformat.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Använd temporär mapp

Stora dokument kan generera temporära filer (t.ex. vid extrahering av bilder). Du kan dirigera dessa filer till en mapp du själv väljer, vilket är praktiskt i sandlådemiljöer.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Varnings‑callback

Under laddning kan Aspose.Words ge varningar (t.ex. om ej stödda funktioner). Genom att implementera en callback kan du logga eller reagera på dessa händelser.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Konvertera metafiler till PNG

Metafiler som WMF kan rasteriseras till PNG under laddning, vilket säkerställer enhetlig rendering på olika plattformar.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Komplett källkod för att arbeta med Load Options i Aspose.Words för Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Vanliga användningsfall & tips

- **Batch‑konverteringspipelines** – Kombinera `setTempFolder` med ett schemalagt jobb för att bearbeta hundratals filer utan att fylla systemets temporära katalog.  
- **Migrering av äldre dokument** – Använd `setMswVersion` tillsammans med `setConvertShapeToOfficeMath` för att föra in gamla ingenjörsdokument i ett modernt format samtidigt som ekvationerna bevaras.  
- **Säker dokumenthantering** – Para `loadEncryptedDocument` med `OdtSaveOptions` för att återkryptera filer med ett nytt lösenord i ett annat format.  

## Vanliga frågor

**Q: Hur kan jag hantera varningar under dokumentladdning?**  
A: Implementera ett anpassat `IWarningCallback` (som visas i *Varnings‑callback*-exemplet) och registrera det via `loadOptions.setWarningCallback(...)`. Detta låter dig logga, ignorera eller avbryta baserat på varningsallvarligheten.

**Q: Kan jag konvertera former till Office Math‑objekt när jag laddar ett dokument?**  
A: Ja—anropa `loadOptions.setConvertShapeToOfficeMath(true)` innan du konstruerar `Document`. Biblioteket ersätter automatiskt kompatibla former med inbyggda Office Math‑objekt.

**Q: Hur specificerar jag MS Word‑version för dokumentladdning?**  
A: Använd `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (eller något annat enum‑värde) för att tala om för Aspose.Words vilka renderingsregler som ska tillämpas.

**Q: Vad är syftet med metoden `setTempFolder` i LoadOptions?**  
A: Den dirigerar alla temporära filer som genereras under laddning (såsom extraherade bilder) till en mapp du kontrollerar, vilket är viktigt i miljöer med begränsade system‑temp‑kataloger.

**Q: Är det möjligt att konvertera metafiler som WMF till PNG under laddning?**  
A: Absolut—aktivera det med `loadOptions.setConvertMetafilesToPng(true)`. Detta säkerställer att rasterbilder lagras som PNG, vilket förbättrar kompatibiliteten med moderna visare.

## Slutsats

Vi har gått igenom de viktigaste teknikerna för **hur man ställer in LoadOptions** i Aspose.Words för Java, från att uppdatera smutsiga fält till att hantera krypterade filer, konvertera former, ange Word‑version, dirigera temporär lagring och mer. Genom att utnyttja dessa alternativ kan du bygga robusta, högpresterande dokumentbehandlingspipelines som anpassar sig till ett brett spektrum av indata‑scenarier.

---

**Senast uppdaterad:** 2025-12-27  
**Testat med:** Aspose.Words för Java 24.11  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}