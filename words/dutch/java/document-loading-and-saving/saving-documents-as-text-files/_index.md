---
date: 2025-12-24
description: Leer hoe je een platte‑tekstbestand maakt van Word‑documenten met Aspose.Words
  voor Java. Deze gids laat zien hoe je Word naar txt converteert, tabinspringing
  gebruikt en Word opslaat als txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Hoe maak je een platte‑tekstbestand met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een platte tekstbestand met Aspose.Words voor Java

## Introductie tot het opslaan van documenten als tekstbestanden in Aspose.Words voor Java

In deze tutorial leer je **hoe je een platte tekstbestand** maakt van een Word‑document met behulp van de Aspose.Words voor Java‑bibliotheek. Of je nu **word naar txt wilt converteren**, rapportgeneratie wilt automatiseren, of simpelweg ruwe tekst wilt extraheren voor verdere verwerking, deze gids leidt je door de volledige workflow—van het maken van een document tot het fijn afstellen van opslaan‑opties zoals **tab‑inspringing gebruiken** of bidi‑tekens toevoegen. Laten we beginnen!

## Snelle antwoorden
- **Wat is de primaire klasse om een document te maken?** `Document` van Aspose.Words.
- **Welke optie voegt bidi‑tekens toe voor rechts‑naar‑links talen?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Hoe kan ik lijstitems inspringen met tabs?** Stel `ListIndentation.Character` in op `'\t'`.
- **Heb ik een licentie nodig voor ontwikkeling?** Een gratis proefversie werkt voor testen; een licentie is vereist voor productie.
- **Kan ik het bestand opslaan met een aangepaste naam en pad?** Ja—geef het volledige pad door aan `doc.save()`.

## Vereisten

Voordat we beginnen, zorg ervoor dat je de volgende vereisten hebt:

- Java Development Kit (JDK) geïnstalleerd op je systeem.  
- Aspose.Words voor Java‑bibliotheek geïntegreerd in je project. Je kunt het downloaden van [hier](https://releases.aspose.com/words/java/).  
- Basiskennis van Java‑programmeren.

## Stap 1: Maak een document

Om **word naar txt op te slaan**, hebben we eerst een `Document`‑instantie nodig. Hieronder staat een eenvoudige Java‑codefragment dat een document maakt en een paar regels meertalige tekst schrijft:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In deze code maken we een nieuw document, voegen Engels, Hebreeuws en Arabisch toe, en schakelen we rechts‑naar‑links opmaak in voor de Hebreeuwse alinea in.

## Stap 2: Definieer tekst‑opslaan‑opties

Vervolgens configureren we hoe het document wordt opgeslagen als een platte tekstbestand. Aspose.Words biedt de `TxtSaveOptions`‑klasse, waarmee je alles kunt regelen, van bidi‑tekens tot lijstinspringing.

### Voorbeeld 1: Bidi‑tekens toevoegen (hoe txt op te slaan met juiste RTL‑ondersteuning)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Het instellen van `AddBidiMarks` op `true` zorgt ervoor dat rechts‑naar‑links tekens correct worden weergegeven in het resulterende **platte tekstbestand**.

### Voorbeeld 2: Tab‑teken gebruiken voor lijstinspringing (tab‑inspringing gebruiken)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Hier vertellen we Aspose.Words om een tab‑teken (`'\t'`) voor elk lijstniveau toe te voegen, waardoor de tekstuitvoer makkelijker leesbaar wordt.

## Stap 3: Sla het document op als tekst

Nu de opslaan‑opties klaar zijn, kun je het document opslaan als een **plat tekstbestand**:

```java
doc.save("output.txt", saveOptions);
```

Vervang `"output.txt"` door het volledige pad waar je het bestand wilt opslaan.

## Complete broncode voor het opslaan van documenten als tekstbestanden in Aspose.Words voor Java

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Veelvoorkomende problemen en oplossingen

| Probleem | Oplossing |
|----------|-----------|
| **Bidi‑tekens verschijnen als onleesbare tekst** | Zorg ervoor dat `setAddBidiMarks(true)` is ingeschakeld en dat het uitvoerbestand wordt geopend met UTF‑8‑codering. |
| **Lijstinspringing ziet er verkeerd uit** | Controleer of `ListIndentation.Count` en `Character` zijn ingesteld op de gewenste waarden (tab `'\t'` of spatie `' '` ). |
| **Bestand niet aangemaakt** | Controleer of het mappad bestaat en of de applicatie schrijfrechten heeft. |

## Veelgestelde vragen

### Hoe voeg ik bidi‑tekens toe aan de tekstoutput?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Kan ik het lijstinspringings‑teken aanpassen?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Is Aspose.Words voor Java geschikt voor het verwerken van meertalige tekst?

Ja, Aspose.Words voor Java ondersteunt een breed scala aan talen en teken‑coderingen, waardoor het ideaal is voor het extraheren en opslaan van meertalige inhoud als platte tekst.

### Hoe kan ik meer documentatie en bronnen voor Aspose.Words voor Java vinden?

Je kunt uitgebreide documentatie en bronnen vinden op de Aspose.Words voor Java‑documentatiepagina: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Waar kan ik Aspose.Words voor Java downloaden?

Je kunt de bibliotheek downloaden van de officiële site: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Wat als ik **word naar txt moet converteren** in een batch‑proces?

Plaats de bovenstaande code in een lus die elk `.docx`‑bestand laadt, dezelfde `TxtSaveOptions` toepast en elk opslaat als `.txt`. Zorg ervoor dat je de bronnen beheert door `Document`‑objecten na elke iteratie te verwijderen.

### Ondersteunt de API het opslaan direct naar een stream in plaats van een bestand?

Ja, je kunt een `OutputStream` doorgeven aan `doc.save(outputStream, saveOptions)` voor in‑memory verwerking of bij integratie met webservices.

**Laatst bijgewerkt:** 2025-12-24  
**Getest met:** Aspose.Words for Java 24.12 (latest)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}