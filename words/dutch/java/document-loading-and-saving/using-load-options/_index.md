---
"description": "Beheers laadopties in Aspose.Words voor Java. Pas het laden van documenten aan, verwerk encryptie, converteer vormen, stel Word-versies in en meer voor efficiënte verwerking van Java-documenten."
"linktitle": "Laadopties gebruiken"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Laadopties gebruiken in Aspose.Words voor Java"
"url": "/nl/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Laadopties gebruiken in Aspose.Words voor Java


## Inleiding tot het werken met laadopties in Aspose.Words voor Java

In deze tutorial verkennen we hoe je met laadopties in Aspose.Words voor Java kunt werken. Met laadopties kun je aanpassen hoe documenten worden geladen en verwerkt. We behandelen verschillende scenario's, waaronder het bijwerken van 'dirty fields', het laden van gecodeerde documenten, het converteren van vormen naar Office Math, het instellen van de MS Word-versie, het specificeren van een tijdelijke map, het afhandelen van waarschuwingen en het converteren van metabestanden naar PNG. Laten we stap voor stap aan de slag gaan.

## Update Vuile Velden

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Dit codefragment laat zien hoe u gewijzigde velden in een document kunt bijwerken. `setUpdateDirtyFields(true)` Deze methode wordt gebruikt om ervoor te zorgen dat vuile velden worden bijgewerkt tijdens het laden van documenten.

## Gecodeerd document laden

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Hier laden we een gecodeerd document met behulp van een wachtwoord. De `LoadOptions` constructor accepteert het documentwachtwoord, en u kunt ook een nieuw wachtwoord opgeven bij het opslaan van het document met behulp van `OdtSaveOptions`.

## Vorm converteren naar Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Deze code laat zien hoe u vormen kunt converteren naar Office Math-objecten tijdens het laden van een document. `setConvertShapeToOfficeMath(true)` methode maakt deze conversie mogelijk.

## MS Word-versie instellen

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

U kunt de MS Word-versie voor het laden van documenten opgeven. In dit voorbeeld stellen we de versie in op Microsoft Word 2010 met behulp van `setMswVersion`.

## Tijdelijke map gebruiken

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Door de tijdelijke map in te stellen met `setTempFolder`, kunt u bepalen waar tijdelijke bestanden worden opgeslagen tijdens de documentverwerking.

## Waarschuwing Terugbellen

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Ga om met waarschuwingen die ontstaan tijdens het laden van documenten.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Deze code demonstreert hoe u een waarschuwingscallback instelt om waarschuwingen af te handelen tijdens het laden van documenten. U kunt het gedrag van uw applicatie aanpassen wanneer er waarschuwingen optreden.

## Metabestanden naar PNG converteren

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

Om metabestanden (bijvoorbeeld WMF) naar PNG-afbeeldingen te converteren tijdens het laden van een document, kunt u de `setConvertMetafilesToPng(true)` methode.

## Volledige broncode voor het werken met laadopties in Aspose.Words voor Java

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
	// Maak een nieuw LoadOptions-object, dat documenten standaard laadt volgens de MS Word 2019-specificatie
	// en verander de laadversie naar Microsoft Word 2010.
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
		// Drukt waarschuwingen en de bijbehorende details af zodra ze zich voordoen tijdens het laden van het document.
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

## Conclusie

In deze tutorial hebben we ons verdiept in verschillende aspecten van het werken met laadopties in Aspose.Words voor Java. Laadopties spelen een cruciale rol bij het aanpassen van de manier waarop documenten worden geladen en verwerkt, zodat u uw documentverwerking kunt afstemmen op uw specifieke behoeften. Laten we de belangrijkste punten uit deze handleiding nog eens samenvatten:

## Veelgestelde vragen

### Hoe kan ik waarschuwingen tijdens het laden van documenten verwerken?

U kunt een waarschuwingscallback instellen zoals weergegeven in de `warningCallback()` methode hierboven. Pas de `DocumentLoadingWarningCallback` klasse om waarschuwingen te verwerken volgens de vereisten van uw toepassing.

### Kan ik vormen converteren naar Office Math-objecten bij het laden van een document?

Ja, u kunt vormen omzetten naar Office Math-objecten met behulp van `loadOptions.setConvertShapeToOfficeMath(true)`.

### Hoe geef ik de MS Word-versie op voor het laden van documenten?

Gebruik `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` om de MS Word-versie voor het laden van documenten op te geven.

### Wat is het doel van de `setTempFolder` methode in Laadopties?

De `setTempFolder` Met deze methode kunt u de map opgeven waarin tijdelijke bestanden worden opgeslagen tijdens de verwerking van documenten.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}