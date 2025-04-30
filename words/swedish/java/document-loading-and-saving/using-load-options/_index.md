---
"description": "Bemästra laddningsalternativ i Aspose.Words för Java. Anpassa dokumentinläsning, hantera kryptering, konvertera former, ställ in Word-versioner och mer för effektiv Java-dokumentbehandling."
"linktitle": "Använda laddningsalternativ"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Använda laddningsalternativ i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda laddningsalternativ i Aspose.Words för Java


## Introduktion till att arbeta med laddningsalternativ i Aspose.Words för Java

I den här handledningen utforskar vi hur man arbetar med laddningsalternativ i Aspose.Words för Java. Med laddningsalternativ kan du anpassa hur dokument laddas och bearbetas. Vi kommer att gå igenom olika scenarier, inklusive uppdatering av smutsiga fält, laddning av krypterade dokument, konvertering av former till Office Math, inställning av MS Word-version, ange en tillfällig mapp, hantering av varningar och konvertering av metafiler till PNG. Låt oss gå vidare steg för steg.

## Uppdatera smutsiga fält

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Det här kodavsnittet visar hur man uppdaterar smutsiga fält i ett dokument. `setUpdateDirtyFields(true)` Metoden används för att säkerställa att dirty fields uppdateras under dokumentinläsning.

## Ladda krypterat dokument

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Här laddar vi ett krypterat dokument med ett lösenord. `LoadOptions` konstruktorn accepterar dokumentlösenordet, och du kan också ange ett nytt lösenord när du sparar dokumentet med hjälp av `OdtSaveOptions`.

## Konvertera form till kontorsmatematik

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Den här koden visar hur man konverterar former till Office Math-objekt under dokumentinläsning. `setConvertShapeToOfficeMath(true)` Metoden möjliggör denna konvertering.

## Ange MS Word-version

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

Du kan ange MS Word-versionen för dokumentinläsning. I det här exemplet ställer vi in versionen till Microsoft Word 2010 med hjälp av `setMswVersion`.

## Använd tillfällig mapp

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Genom att ställa in den temporära mappen med hjälp av `setTempFolder`, kan du styra var tillfälliga filer lagras under dokumentbearbetning.

## Varning återuppringning

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Hantera varningar när de uppstår under dokumentinläsning.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Den här koden visar hur man konfigurerar ett varningsmotring för att hantera varningar under dokumentinläsning. Du kan anpassa programmets beteende när varningar uppstår.

## Konvertera metafiler till PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

För att konvertera metafiler (t.ex. WMF) till PNG-bilder under dokumentinläsning kan du använda `setConvertMetafilesToPng(true)` metod.

## Komplett källkod för att arbeta med laddningsalternativ i Aspose.Words för Java

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
	// Skapa ett nytt LoadOptions-objekt, som laddar dokument enligt MS Word 2019-specifikationen som standard.
	// och ändra laddningsversionen till Microsoft Word 2010.
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
		// Skriver ut varningar och deras detaljer allt eftersom de uppstår vid dokumentinläsning.
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

## Slutsats

I den här handledningen har vi fördjupat oss i olika aspekter av att arbeta med laddningsalternativ i Aspose.Words för Java. Laddningsalternativ spelar en avgörande roll för att anpassa hur dokument laddas och bearbetas, så att du kan skräddarsy din dokumentbearbetning efter dina specifika behov. Låt oss sammanfatta de viktigaste punkterna som tas upp i den här guiden:

## Vanliga frågor

### Hur kan jag hantera varningar vid inläsning av dokument?

Du kan ställa in ett varningsåteruppringning enligt vad som visas i `warningCallback()` metoden ovan. Anpassa `DocumentLoadingWarningCallback` klassen för att hantera varningar enligt din applikations krav.

### Kan jag konvertera former till Office Math-objekt när jag laddar ett dokument?

Ja, du kan konvertera former till Office Math-objekt med hjälp av `loadOptions.setConvertShapeToOfficeMath(true)`.

### Hur anger jag MS Word-versionen för dokumentinläsning?

Använda `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` för att ange MS Word-versionen för dokumentinläsning.

### Vad är syftet med `setTempFolder` metod i laddningsalternativ?

De `setTempFolder` Metoden låter dig ange mappen där temporära filer lagras under dokumentbearbetning.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}