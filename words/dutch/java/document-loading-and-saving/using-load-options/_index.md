---
date: 2025-12-27
description: Leer hoe u LoadOptions instelt in Aspose.Words for Java, inclusief hoe
  u een tijdelijke map opgeeft, de Word‑versie instelt, metafiles naar PNG converteert
  en vormen naar wiskunde converteert voor flexibele documentverwerking.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Hoe LoadOptions instellen in Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe LoadOptions in te stellen in Aspose.Words voor Java

In deze tutorial lopen we stap voor stap door **hoe LoadOptions in te stellen** voor verschillende real‑world scenario's bij het werken met Aspose.Words voor Java. LoadOptions geven u fijnmazige controle over de manier waarop een document wordt geopend—of u nu vuile velden moet bijwerken, met versleutelde bestanden werkt, vormen naar Office Math converteert, of de bibliotheek vertelt waar tijdelijke gegevens moeten worden opgeslagen. Aan het einde kunt u het laadgedrag aanpassen aan de exacte vereisten van uw applicatie.

## Snelle Antwoorden
- **Wat is LoadOptions?** Een configuratie‑object dat beïnvloedt hoe Aspose.Words een document laadt.  
- **Kan ik velden bijwerken tijdens het laden?** Ja—stel `setUpdateDirtyFields(true)` in.  
- **Hoe open ik een met wachtwoord beveiligd bestand?** Geef het wachtwoord door aan de `LoadOptions` constructor.  
- **Is het mogelijk de tijdelijke map te wijzigen?** Gebruik `setTempFolder("path")`.  
- **Welke methode converteert vormen naar Office Math?** `setConvertShapeToOfficeMath(true)`.

## Waarom LoadOptions gebruiken?
LoadOptions stellen u in staat‑load verwerkingsstappen te vermijden, het geheugenverbruik te verminderen en ervoor te zorgen dat het document precies wordt geïnterpreteerd zoals u dat nodig heeft. Bijvoorbeeld, het converteren van metafiles naar PNG tijdens het laden voorkomt latere rasterisatie‑problemen, en het specificeren van de MS Word‑versie helpt de lay-outgetrouwheid te behouden bij het werken met legacy‑bestanden.

## Voorvereisten
- Java 17 of hoger  
- Aspose.Words for Java (nieuwste versie)  
- Een geldige Aspose‑licentie voor productiegebruik  

## Stapsgewijze handleiding

### Vuile velden bijwerken

Wanneer een document velden bevat die bewerkt zijn maar niet ververst, kunt u Aspose.Words laten weten deze automatisch bij te werken tijdens het laden.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*De aanroep `setUpdateDirtyFields(true)` zorgt ervoor dat alle vuile velden opnieuw worden berekend zodra het document wordt geopend.*

### Versleuteld document laden

Als uw bronbestand met een wachtwoord is beveiligd, geef dan het wachtwoord op bij het maken van de `LoadOptions`‑instantie. U kunt ook een nieuw wachtwoord instellen bij het opslaan naar een ander formaat.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Vorm naar Office Math converteren

Sommige legacy‑documenten slaan vergelijkingen op als teken‑vormen. Het inschakelen van deze optie converteert die vormen naar native Office Math‑objecten, die later gemakkelijker te bewerken zijn.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### MS Word‑versie instellen

Het specificeren van de doel‑Word‑versie helpt de bibliotheek de juiste renderingsregels te kiezen, vooral bij het werken met oudere bestandsformaten.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Tijdelijke map gebruiken

Grote documenten kunnen tijdelijke bestanden genereren (bijv. bij het extraheren van afbeeldingen). U kunt deze bestanden naar een map van uw keuze leiden, wat nuttig is voor sandbox‑omgevingen.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Waarschuwings‑callback

Tijdens het laden kan Aspose.Words waarschuwingen genereren (bijv. niet‑ondersteunde functies). Het implementeren van een callback stelt u in staat deze gebeurtenissen te loggen of erop te reageren.

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

### Metafiles naar PNG converteren

Metafiles zoals WMF kunnen tijdens het laden gerasterd worden naar PNG, waardoor consistente weergave over verschillende platforms wordt gegarandeerd.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Complete broncode voor het werken met Load Options in Aspose.Words voor Java

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

## Veelvoorkomende use‑cases & tips

- **Batch‑conversiepijplijnen** – Combineer `setTempFolder` met een geplande taak om honderden bestanden te verwerken zonder de systeem‑temp‑directory te vullen.  
- **Legacy‑documentmigratie** – Gebruik `setMswVersion` samen met `setConvertShapeToOfficeMath` om oude technische documenten naar een modern formaat te brengen terwijl vergelijkingen behouden blijven.  
- **Veilige documentafhandeling** – Combineer `loadEncryptedDocument` met `OdtSaveOptions` om bestanden opnieuw te versleutelen met een nieuw wachtwoord in een ander formaat.  

## Veelgestelde vragen

**Q: Hoe kan ik waarschuwingen tijdens het laden van een document afhandelen?**  
A: Implementeer een aangepaste `IWarningCallback` (zoals getoond in het *Waarschuwings‑callback* voorbeeld) en registreer deze via `loadOptions.setWarningCallback(...)`. Hiermee kunt u loggen, negeren of afbreken op basis van de ernst van de waarschuwing.

**Q: Kan ik vormen naar Office Math‑objecten converteren bij het laden van een document?**  
A: Ja—roep `loadOptions.setConvertShapeToOfficeMath(true)` aan voordat u de `Document` construeert. De bibliotheek zal compatibele vormen automatisch vervangen door native Office Math‑objecten.

**Q: Hoe specificeer ik de MS Word‑versie voor het laden van een document?**  
A: Gebruik `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (of een andere enum‑waarde) om Aspose.Words te vertellen welke Word‑versie‑renderingsregels moeten worden toegepast.

**Q: Wat is het doel van de `setTempFolder`‑methode in LoadOptions?**  
A: Het leidt alle tijdelijke bestanden die tijdens het laden worden gegenereerd (zoals geëxtraheerde afbeeldingen) naar een map die u beheert, wat essentieel is voor omgevingen met beperkte systeem‑temp‑directories.

**Q: Is het mogelijk om metafiles zoals WMF tijdens het laden naar PNG te converteren?**  
A: Absoluut—schakel dit in met `loadOptions.setConvertMetafilesToPng(true)`. Hiermee worden rasterafbeeldingen opgeslagen als PNG, wat de compatibiliteit met moderne viewers verbetert.

## Conclusie

We hebben de essentiële technieken behandeld voor **hoe LoadOptions in te stellen** in Aspose.Words voor Java, van het bijwerken van vuile velden tot het verwerken van versleutelde bestanden, het converteren van vormen, het specificeren van de Word‑versie, het richten van tijdelijke opslag en meer. Door deze opties te benutten kunt u robuuste, high‑performance documentverwerkings‑pijplijnen bouwen die zich aanpassen aan een breed scala aan invoerscenario's.

---

**Laatst bijgewerkt:** 2025-12-27  
**Getest met:** Aspose.Words for Java 24.11  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}