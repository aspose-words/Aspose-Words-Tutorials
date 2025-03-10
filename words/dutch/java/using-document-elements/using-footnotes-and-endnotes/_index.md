---
title: Voetnoten en eindnoten gebruiken in Aspose.Words voor Java
linktitle: Voetnoten en eindnoten gebruiken
second_title: Aspose.Words Java Documentverwerkings-API
description: Leer voetnoten en eindnoten effectief te gebruiken in Aspose.Words voor Java. Verbeter vandaag nog uw vaardigheden in documentopmaak!
weight: 13
url: /nl/java/using-document-elements/using-footnotes-and-endnotes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Voetnoten en eindnoten gebruiken in Aspose.Words voor Java


In deze tutorial leiden we u door het proces van het gebruiken van voetnoten en eindnoten in Aspose.Words voor Java. Voetnoten en eindnoten zijn essentiële elementen in documentopmaak, vaak gebruikt voor citaten, referenties en aanvullende informatie. Aspose.Words voor Java biedt robuuste functionaliteit om naadloos met voetnoten en eindnoten te werken.

## 1. Inleiding tot voetnoten en eindnoten

Voetnoten en eindnoten zijn aantekeningen die aanvullende informatie of citaten in een document bieden. Voetnoten verschijnen onderaan de pagina, terwijl eindnoten aan het einde van een sectie of het document worden verzameld. Ze worden vaak gebruikt in academische papers, rapporten en juridische documenten om te verwijzen naar bronnen of om inhoud te verduidelijken.

## 2. Uw omgeving instellen

Voordat we beginnen met werken met voetnoten en eindnoten, moet u uw ontwikkelomgeving instellen. Zorg ervoor dat u de Aspose.Words voor Java API hebt geïnstalleerd en geconfigureerd in uw project.

## 3. Voetnoten toevoegen aan uw document

Volg deze stappen om voetnoten aan uw document toe te voegen:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Geef het aantal kolommen op waarmee het voetnotengebied wordt opgemaakt.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Voetnootopties wijzigen

U kunt voetnootopties wijzigen om hun uiterlijk en gedrag aan te passen. Dit is hoe:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Eindnoten toevoegen aan uw document

Het toevoegen van eindnoten aan uw document is eenvoudig. Hier is een voorbeeld:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Endnote-instellingen aanpassen

U kunt de eindnootinstellingen verder aanpassen aan de vereisten van uw document.

## Volledige broncode
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Geef het aantal kolommen op waarmee het voetnotengebied wordt opgemaakt.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. Conclusie

In deze tutorial hebben we onderzocht hoe je met voetnoten en eindnoten in Aspose.Words voor Java kunt werken. Deze functies zijn van onschatbare waarde voor het maken van goed gestructureerde documenten met de juiste citaten en referenties.

Nu u weet hoe u voetnoten en eindnoten gebruikt, kunt u de opmaak van uw document verbeteren en uw inhoud professioneler maken.

### Veelgestelde vragen

### 1. Wat is het verschil tussen voetnoten en eindnoten?
Voetnoten worden onderaan de pagina weergegeven, terwijl eindnoten aan het einde van een sectie of het document worden geplaatst.

### 2. Hoe kan ik de positie van voetnoten of eindnoten wijzigen?
 U kunt de`setPosition` Methode om de positie van voetnoten of eindnoten te wijzigen.

### 3. Kan ik de opmaak van voetnoten en eindnoten aanpassen?
Ja, u kunt de opmaak van voetnoten en eindnoten aanpassen met Aspose.Words voor Java.

### 4. Zijn voetnoten en eindnoten belangrijk bij de opmaak van documenten?
Ja, voetnoten en eindnoten zijn essentieel voor het verstrekken van referenties en aanvullende informatie in documenten.

Ontdek gerust meer functies van Aspose.Words voor Java en verbeter uw documentcreatiemogelijkheden. Veel plezier met coderen!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
