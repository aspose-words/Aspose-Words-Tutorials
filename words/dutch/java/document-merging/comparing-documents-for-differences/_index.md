---
title: Documenten vergelijken op verschillen
linktitle: Documenten vergelijken op verschillen
second_title: Aspose.Words Java Documentverwerkings-API
description: Leer hoe u documenten kunt vergelijken op verschillen met Aspose.Words in Java. Onze stapsgewijze handleiding zorgt voor nauwkeurig documentbeheer.
weight: 12
url: /nl/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Documenten vergelijken op verschillen

## Invoering

Heb je je ooit afgevraagd hoe je elk verschil tussen twee Word-documenten kunt vinden? Misschien ben je een document aan het herzien of probeer je wijzigingen te vinden die door een medewerker zijn aangebracht. Handmatige vergelijkingen kunnen vervelend en foutgevoelig zijn, maar met Aspose.Words voor Java is het een fluitje van een cent! Met deze bibliotheek kun je documentvergelijkingen automatiseren, revisies markeren en wijzigingen moeiteloos samenvoegen.

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u aan de code begint:  
1. Java Development Kit (JDK) op uw systeem geïnstalleerd.  
2.  Aspose.Words voor Java-bibliotheek. U kunt[download het hier](https://releases.aspose.com/words/java/).  
3. Een ontwikkelomgeving zoals IntelliJ IDEA of Eclipse.  
4. Basiskennis van Java-programmering.  
5.  Een geldige Aspose-licentie. Als u die niet hebt, haal er dan een[tijdelijke licentie hier](https://purchase.aspose.com/temporary-license/).

## Pakketten importeren

Om Aspose.Words te gebruiken, moet u de benodigde klassen importeren. Hieronder staan de vereiste imports:

```java
import com.aspose.words.*;
import java.util.Date;
```

Zorg ervoor dat deze pakketten correct aan uw projectafhankelijkheden zijn toegevoegd.


In dit gedeelte leggen we het proces uit in eenvoudige stappen.


## Stap 1: Stel uw documenten in

Om te beginnen heb je twee documenten nodig: een die het origineel vertegenwoordigt en de andere die de bewerkte versie vertegenwoordigt. Zo maak je ze:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Dit creëert twee documenten in het geheugen met basisinhoud. U kunt ook bestaande Word-documenten laden met`new Document("path/to/document.docx")`.


## Stap 2: Controleer op bestaande revisies

Revisies in Word-documenten vertegenwoordigen bijgehouden wijzigingen. Controleer voor het vergelijken of geen van beide documenten reeds bestaande revisies bevat:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Als er revisies zijn, kunt u deze het beste accepteren of afwijzen voordat u verdergaat.


## Stap 3: Vergelijk de documenten

 Gebruik de`compare` methode om verschillen te vinden. Deze methode vergelijkt het doeldocument (`doc2`) met het bron document (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Hier:
- AuteurNaam is de naam van de persoon die de wijzigingen aanbrengt.
- Datum is het tijdstempel van de vergelijking.


## Stap 4: Procesrevisies

Nadat ze zijn vergeleken, genereert Aspose.Words revisies in het brondocument (`doc1`Laten we deze revisies eens analyseren:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Deze lus biedt gedetailleerde informatie over elke revisie, zoals het type wijziging en de betreffende tekst.


## Stap 5: Accepteer alle revisies

Als u het bron document wilt (`doc1`) om het doeldocument te matchen (`doc2`), accepteer alle revisies:

```java
doc1.getRevisions().acceptAll();
```

 Deze update`doc1` om alle wijzigingen weer te geven die zijn aangebracht in`doc2`.


## Stap 6: Sla het bijgewerkte document op

Sla ten slotte het bijgewerkte document op schijf op:

```java
doc1.save("Document.Compare.docx");
```

Om de wijzigingen te bevestigen, laadt u het document opnieuw en controleert u of er geen resterende revisies zijn:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Stap 7: Controleer de gelijkheid van het document

Om er zeker van te zijn dat de documenten identiek zijn, vergelijkt u de tekst:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Als de teksten overeenkomen, gefeliciteerd: u hebt de documenten succesvol vergeleken en gesynchroniseerd!


## Conclusie

Documenten vergelijken is niet langer een klusje, dankzij Aspose.Words voor Java. Met slechts een paar regels code kunt u verschillen lokaliseren, revisies verwerken en zorgen voor consistentie in documenten. Of u nu een gezamenlijk schrijfproject beheert of juridische documenten controleert, deze functie is een game-changer.

## Veelgestelde vragen

### Kan ik documenten vergelijken met afbeeldingen en tabellen?  
Ja, Aspose.Words ondersteunt het vergelijken van complexe documenten, inclusief documenten met afbeeldingen, tabellen en opmaak.

### Heb ik een licentie nodig om deze functie te gebruiken?  
 Ja, voor volledige functionaliteit is een licentie vereist. Koop een[tijdelijke licentie hier](https://purchase.aspose.com/temporary-license/).

### Wat gebeurt er als er reeds bestaande revisies zijn?  
U moet ze accepteren of afwijzen voordat u documenten gaat vergelijken, om conflicten te voorkomen.

### Kan ik de revisies in het document markeren?  
Ja, met Aspose.Words kunt u aanpassen hoe revisies worden weergegeven. U kunt bijvoorbeeld wijzigingen markeren.

### Is deze functie beschikbaar in andere programmeertalen?  
Ja, Aspose.Words ondersteunt meerdere talen, waaronder .NET en Python.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
