---
date: '2026-01-27'
description: Leer hoe u commentaar in Java kunt toevoegen en Word‑commentaren kunt
  toevoegen en verwijderen in Word‑documenten met Aspose.Words voor Java. Beheer,
  print, verwijder en tijdstempel commentaren moeiteloos.
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
title: Commentaar toevoegen Java met Aspose.Words – Beheer van commentaren
url: /nl/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Beheersen van commentaarbeheer in Word-documenten

## Inleiding
Als je **add comment java** programmatisch wilt toevoegen en volledige controle over de levenscyclus van commentaren wilt behouden, ben je hier aan het juiste adres. Of je nu een collaboratief beoordelingshulpmiddel bouwt of documentworkflows automatiseert, het beheren van commentaren—toevoegen, beantwoorden, verwijderen en timestamps bijhouden—kan een knelpunt zijn. In deze tutorial lopen we elke essentiële bewerking door met Aspose.Words for Java, zodat je vol vertrouwen **add remove word comments** kunt toevoegen en verwijderen, ze kunt afdrukken, markeren als voltooid, en UTC‑timestamps kunt extraheren.

**Wat je zult leren**
- Hoe je commentaren en antwoorden kunt toevoegen met één regel code  
- Hoe je alle top‑level commentaren en hun geneste antwoorden kunt afdrukken  
- Hoe je commentaarantwoorden kunt verwijderen of een volledige commentaarthread kunt wissen  
- Hoe je een commentaar kunt markeren als voltooid (opgelost)  
- Hoe je de exacte UTC‑datum en -tijd kunt ophalen waarop een commentaar is aangemaakt  

Klaar? Zorg ervoor dat je omgeving is ingesteld voordat we in de code duiken.

## Vereisten
Zorg ervoor dat je het volgende hebt voordat je begint:

- Java Development Kit (JDK) 8 of hoger geïnstalleerd  
- Basiskennis van Java‑syntaxis en objectgeoriënteerd programmeren  
- Een IDE zoals IntelliJ IDEA of Eclipse voor eenvoudig projectbeheer  

### Instellen van Aspose.Words voor Java
Aspose.Words is een krachtige bibliotheek waarmee je Word‑documenten in vele formaten kunt manipuleren. Voeg de afhankelijkheid toe die bij je buildsysteem past:

**Maven**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Licentie‑acquisitie
Aspose.Words is een commercieel product, maar je kunt beginnen met een gratis proefversie of een tijdelijke licentie aanvragen voor volledige functionaliteit. Bezoek de [purchase page](https://purchase.aspose.com/buy) om de licentieopties te bekijken.

## Snelle antwoorden
- **Kan ik add comment java zonder licentie gebruiken?** Ja, een proefversie werkt maar voegt evaluatiewatermerken toe.  
- **Welke methode voegt een antwoord toe?** `comment.addReply(author, initials, date, text)`.  
- **Hoe markeer ik een commentaar als voltooid?** Roep `comment.setDone(true)` aan.  
- **Is een UTC‑timestamp beschikbaar?** Gebruik `comment.getDateTimeUtc()`.  
- **Welke versie is getest?** Aspose.Words 25.3 (Java).

## Implementatie‑gids
In de onderstaande secties splitsen we elke functie stap voor stap uit, met context en praktische tips.

### Functie 1: Commentaar toevoegen met antwoord
#### Overzicht
Het toevoegen van een commentaar en een antwoord is de basis van collaboratieve bewerking. Je ziet hoe je een commentaar maakt, het aan een alinea koppelt en vervolgens een genest antwoord toevoegt.

#### Implementatiestappen
**Stap 1:** Initialiseer het Document‑object  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

**Stap 2:** Maak een commentaar aan en voeg het toe  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Stap 3:** Voeg een antwoord toe aan het commentaar  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### Functie 2: Alle commentaren afdrukken
#### Overzicht
Bij het beoordelen van een groot document bespaart het afdrukken van elk top‑level commentaar samen met de antwoorden tijd. Deze code laat zien hoe je een document laadt en de commentaarhiërarchie doorloopt.

#### Implementatiestappen
**Stap 1:** Laad het document  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

**Stap 2:** Haal commentaren op en druk ze af  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```

### Functie 3: Commentaarantwoorden verwijderen
#### Overzicht
Soms wordt een commentaarthread rommelig. Dit voorbeeld toont hoe je een enkel antwoord verwijdert of de volledige antwoellijst wist.

#### Implementatiestappen
**Stap 1:** Initialiseer en voeg commentaren met antwoorden toe  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

**Stap 2:** Verwijder antwoorden  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### Functie 4: Commentaar markeren als voltooid
#### Overzicht
Een commentaar markeren als "voltooid" geeft aan dat het probleem is opgelost. Deze vlag kan in UI‑lagen worden gebruikt om voltooide feedback te filteren.

#### Implementatiestappen
**Stap 1:** Maak een document aan en voeg een commentaar toe  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

**Stap 2:** Markeer het commentaar als voltooid  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### Functie 5: UTC‑datum en -tijd ophalen uit commentaar
#### Overzicht
Precieze tijdstempels zijn essentieel voor audit‑trails. Aspose.Words slaat de creatietijd op in UTC, die je kunt ophalen en vergelijken.

#### Implementatiestappen
**Stap 1:** Maak een document met een getimestamped commentaar  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Stap 2:** Sla op en haal de UTC‑datum op  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## Praktische toepassingen
Het begrijpen van deze API's kan je document‑gerichte oplossingen aanzienlijk verbeteren:

- **Collaborative Editing:** Laat meerdere beoordelaars feedback achterlaten, antwoorden en problemen direct in het bestand oplossen.  
- **Document Review Pipelines:** Automatiseer het extraheren van commentaren voor rapportage of compliance‑controles.  
- **Audit Trails:** Sla UTC‑timestamps op voor juridische of regelgevende doeleinden.  

Deze fragmenten kunnen worden geïntegreerd in grotere systemen zoals content‑managementplatforms, geautomatiseerde rapportgeneratoren of aangepaste Word‑verwerkingstools.

## Prestaties overwegingen
Bij het werken met grote Word‑bestanden (honderden pagina's, duizenden commentaren), houd deze tips in gedachten:

- Verwerk commentaren in batches in plaats van ze allemaal in één keer in het geheugen te laden.  
- Hergebruik een enkele `Document`‑instantie bij het uitvoeren van meerdere bewerkingen.  
- Upgrade naar de nieuwste Aspose.Words‑versie om te profiteren van prestatie‑optimalisaties en bug‑fixes.

## Veelvoorkomende problemen en oplossingen
| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **`NullPointerException` bij het benaderen van antwoorden** | Het commentaar heeft geen antwoorden (`getReplies()` retourneert leeg). | Controleer altijd `comment.getReplies().getCount() > 0` voordat je een element benadert. |
| **Commentaren verschijnen niet na opslaan** | Document is opgeslagen in een andere map of overschreven. | Controleer of `YOUR_DOCUMENT_DIRECTORY` naar de beoogde locatie wijst en dat je schrijfrechten hebt. |
| **UTC‑timestamp verschilt van lokale tijd** | `Date` gebruikt de systeem‑locale; `getDateTimeUtc()` converteert naar UTC. | Gebruik `new Date()` voor creatie en vertrouw op `getDateTimeUtc()` voor consistente opslag. |

## FAQ‑sectie
1. **Wat is Aspose.Words for Java?**  
   - Het is een bibliotheek die programmatiche manipulatie van Word‑documenten in verschillende formaten mogelijk maakt.  

2. **Hoe installeer ik Aspose.Words voor mijn project?**  
   - Voeg de eerder getoonde Maven‑ of Gradle‑afhankelijkheid toe aan je projectbestand.  

3. **Kan ik Aspose.Words gebruiken zonder licentie?**  
   - Ja, met beperkingen (evaluatiewatermerken en functiebeperkingen).  

4. **Wat zijn enkele veelvoorkomende problemen bij het beheren van commentaren?**  
   - Zorg voor correcte documentlading, behandel null‑referenties voor antwoorden, en verifieer de commentaarhiërarchie.  

5. **Hoe volg ik wijzigingen over meerdere documenten?**  
   - Implementeer versie‑controllogica in je applicatie of gebruik de ingebouwde revisietracering van Aspose.Words.  

---

**Laatst bijgewerkt:** 2026-01-27  
**Getest met:** Aspose.Words 25.3 for Java  
**Auteur:** Aspose  

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}