---
"description": "Leer hoe je documenten als tekstbestanden opslaat in Aspose.Words voor Java. Volg onze stapsgewijze handleiding met Java-codevoorbeelden."
"linktitle": "Documenten opslaan als tekstbestanden"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Documenten opslaan als tekstbestanden in Aspose.Words voor Java"
"url": "/nl/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documenten opslaan als tekstbestanden in Aspose.Words voor Java


## Inleiding tot het opslaan van documenten als tekstbestanden in Aspose.Words voor Java

In deze tutorial laten we zien hoe je documenten als tekstbestanden kunt opslaan met behulp van de Aspose.Words for Java-bibliotheek. Aspose.Words is een krachtige Java API voor het werken met Word-documenten en biedt diverse opties voor het opslaan van documenten in verschillende formaten, waaronder platte tekst. We bespreken de stappen om dit te bereiken en geven daarbij ook voorbeeld-Java-code.

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende voorwaarden voldoet:

- Java Development Kit (JDK) op uw systeem geïnstalleerd.
- Aspose.Words voor Java-bibliotheek geïntegreerd in uw project. U kunt het downloaden van [hier](https://releases.aspose.com/words/java/).
- Basiskennis van Java-programmering.

## Stap 1: Een document maken

Om een document als tekstbestand op te slaan, moeten we eerst een document aanmaken met Aspose.Words. Hier is een eenvoudig Java-codefragment om een document met wat inhoud te maken:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In deze code maken we een nieuw document en voegen we er wat tekst aan toe, eventueel in verschillende talen.

## Stap 2: Definieer tekstopslagopties

Vervolgens moeten we de tekstopslagopties definiëren die aangeven hoe het document als tekstbestand moet worden opgeslagen. We kunnen verschillende instellingen configureren, zoals het toevoegen van bidi-markeringen, lijstinspringing en meer. Laten we twee voorbeelden bekijken:

### Voorbeeld 1: Bidi-markeringen toevoegen

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

In dit voorbeeld maken we een `TxtSaveOptions` object en stel de `AddBidiMarks` eigendom van `true` om bidi-merken in de tekstuitvoer op te nemen.

### Voorbeeld 2: Tab-teken gebruiken voor lijstinspringing

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Hier configureren we de opslagopties om een tabteken te gebruiken voor lijstinspringing met een aantal van 1.

## Stap 3: Sla het document op als tekst

Nu we de opties voor het opslaan van tekst hebben gedefinieerd, kunnen we het document opslaan als een tekstbestand. De volgende code laat zien hoe dit werkt:

```java
doc.save("output.txt", saveOptions);
```

Vervangen `"output.txt"` met het gewenste bestandspad waar u het tekstbestand wilt opslaan.

## Volledige broncode voor het opslaan van documenten als tekstbestanden in Aspose.Words voor Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Maak een lijst met drie inspringniveaus.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Maak een lijst met drie inspringniveaus.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Conclusie

In deze tutorial hebben we geleerd hoe je documenten als tekstbestanden kunt opslaan in Aspose.Words voor Java. We hebben de stappen besproken voor het aanmaken van een document, het definiëren van opties voor het opslaan van tekst en het opslaan van het document in tekstformaat. Aspose.Words biedt uitgebreide flexibiliteit bij het opslaan van documenten, zodat je de uitvoer kunt aanpassen aan je specifieke wensen.

## Veelgestelde vragen

### Hoe voeg ik bidi-markeringen toe aan de tekstuitvoer?

Om bidi-markeringen aan de tekstuitvoer toe te voegen, stelt u de `AddBidiMarks` eigendom van `TxtSaveOptions` naar `true`. Bijvoorbeeld:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kan ik het inspringteken voor lijsten aanpassen?

Ja, u kunt het inspringteken voor de lijst aanpassen door de `ListIndentation` eigendom van `TxtSaveOptions`Om bijvoorbeeld een tabteken te gebruiken voor lijstinspringing, kunt u het volgende doen:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Is Aspose.Words voor Java geschikt voor het verwerken van meertalige teksten?

Ja, Aspose.Words voor Java is geschikt voor het verwerken van meertalige tekst. Het ondersteunt verschillende talen en tekencoderingen, waardoor het een veelzijdige keuze is voor het werken met documenten in verschillende talen.

### Hoe kan ik meer documentatie en bronnen voor Aspose.Words voor Java krijgen?

Uitgebreide documentatie en bronnen voor Aspose.Words voor Java vindt u op de Aspose-documentatiewebsite: [Aspose.Words voor Java-documentatie](https://reference.aspose.com/words/java/).

### Waar kan ik Aspose.Words voor Java downloaden?

U kunt de Aspose.Words voor Java-bibliotheek downloaden van de Aspose-website: [Download Aspose.Words voor Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}