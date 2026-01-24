---
date: 2026-01-24
description: Leer hoe u XML-gegevens kunt samenvoegen met Aspose.Words voor Java,
  documentgeneratie in Java kunt automatiseren en Mustache-syntaxis kunt gebruiken
  voor dynamische documenten.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Hoe XML samenvoegen in Aspose.Words voor Java
url: /nl/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe XML samenvoegen in Aspose.Words voor Java

In deze uitgebreide gids ontdek je **hoe je XML**-gegevens kunt samenvoegen met Aspose.Words voor Java. We lopen door basis- en geneste mail‑merge‑scenario's, laten je zien hoe je **Mustache‑syntaxis** kunt **gebruiken**, en leggen uit hoe je **documentgeneratie in Java**‑stijl projecten kunt **automatiseren**. Aan het einde kun je gepersonaliseerde Word‑documenten rechtstreeks uit XML‑bronnen genereren met slechts een paar regels code.

## Snelle antwoorden
- **Wat is de primaire klasse voor mail merge?** `Document` and its `MailMerge` property.  
- **Kan ik geneste XML‑tabellen samenvoegen?** Ja – gebruik `executeWithRegions` voor hiërarchische gegevens.  
- **Wordt Mustache‑syntaxis ondersteund?** Schakel het in met `setUseNonMergeFields(true)`.  
- **Heb ik een licentie nodig voor productie?** Een commerciële Aspose.Words‑licentie is vereist.  
- **Welke Java‑versie is compatibel?** Java 8+ en hoger worden volledig ondersteund.

## Wat is XML‑mail‑merge in Aspose.Words?
XML‑mail‑merge stelt je in staat XML‑gebaseerde datasets te koppelen aan plaatshouders in een Word‑sjabloon. De engine vervangt elke plaatshouder door de overeenkomstige XML‑knooppuntwaarde, waardoor een voltooid document ontstaat zonder handmatige bewerking.

## Waarom Aspose.Words gebruiken voor XML‑gebaseerde documentgeneratie?
- **Automatiseer documentgeneratie Java**‑projecten zonder Microsoft Office‑afhankelijkheden.  
- **Ondersteuning voor complexe hiërarchieën** – geneste tabellen, herhalende secties en conditionele inhoud.  
- **Mustache‑syntaxis** biedt flexibele, niet‑merge‑field plaatshouders voor geavanceerde templating.  
- **Cross‑platform** – werkt op Windows, Linux en macOS.

## Voorwaarden

- [Aspose.Words for Java](https://products.aspose.com/words/java/) geïnstalleerd (de nieuwste versie).  
- Voorbeeld‑XML‑bestanden voor klanten, bestellingen en leveranciers (de tutorial gebruikt `Mail merge data - Customers.xml`, `Orders.xml` en `Vendors.xml`).  
- Word‑sjabloondocumenten die merge‑velden bevatten (bijv. `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Hoe XML samenvoegen – Basis‑mail‑merge

Een basis‑mail‑merge haalt een enkele XML‑tabel in een Word‑sjabloon. Volg deze stappen:

1. Laad het XML‑bestand in een `DataSet`.  
2. Open het doel‑Word‑document.  
3. Voer de merge uit met de tabelnaam.  
4. Sla het samengevoegde document op.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Pro tip:** Houd je XML‑structuur plat voor eenvoudige merges – elke tabel moet direct overeenkomen met een set merge‑velden.

## Hoe XML samenvoegen – Geneste mail‑merge

Wanneer je XML ouder‑kind‑relaties bevat (bijv. bestellingen met regelitems), heb je een geneste merge nodig. De `executeWithRegions`‑methode verwerkt elke regio recursief.

1. Laad de hiërarchische XML in een `DataSet`.  
2. Schakel whitespace‑trimmen uit als je exacte opmaak nodig hebt.  
3. Roep `executeWithRegions` aan om alle geneste tabellen te verwerken.  
4. Sla het resultaat op.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Veelvoorkomend valkuil:** Het vergeten instellen van `setTrimWhitespaces(false)` kan ongewenste spaties veroorzaken in het uiteindelijke document, vooral bij valuta‑ of numerieke velden.

## Hoe Mustache‑syntaxis te gebruiken met een DataSet

Mustache‑syntaxis stelt je in staat niet‑merge‑field plaatshouders (bijv. `{{CustomerName}}`) in je sjsteuning in met `setUse merge uit met regio's.  
4. Sla de output op.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Waarom Must gebruiken?** Het biedt een schone, taal‑agnostische manier om naar gegevens te verwijzen, waardoor je sjablonen makkelijker leesbaar en onderhoudbaar zijn, vooral bij **het genereren van documenten**‑gedreven XML‑workflows.

## Veelvoorkomende problemen en oplossingen

| Probleem | Oplossing |
|----------|-----------|
| XML‑knooppunten komen niet overeen met‑ | Controleer of de XML‑elementnamen exact overeenkomen met de merge‑veldnamen (hoofdlettergevoelig). |
| Whitespace verschijnt rond samengevoegde waarden | Gebruik `doc.getMailMerge().setTrimWhitespaces(false)` om de oorspronkelijke spatiëring te behouden. |
| Geneste tabellen worden genegeerd | Zorg ervoor dat de regio van de bovenliggende tabel is gedefinieerd in het sjabloon (bijv. `{{#Orders}} … {{/Orders}}`). |
| Mustache‑plaatshouders worden niet vervangen | Roep `setUseNonMergeFields(true)` aan vóór het uitvoeren van de merge. |

## Veelgestelde vragen

### Hoe kan ik mijn XML‑gegevens voorbereiden voor mail‑merge?

Zorg ervoor dat je XML een tabelstructuur volgt waarbij elk `<TableName>`‑element rijen (`<Row>`) en kolommen bevat die overeenkomen met de merge‑velden in je Word‑sjabloon.

### Kan ik het trim‑gedrag voor mail‑merge‑waarden aanpassen?

Ja. Gebruik `doc.getMailMerge().setTrimWhitespaces(false)` om voor‑ en achtervoegspele spaces precies te behouden zoals ze in de XML staan.

### Wat is de Mustache‑syntaxis, en wanneer moet ik deze gebruiken?

Mustache‑syntaxis (`{{FieldName}}`) biedt flexibele plaatshouders die niet beperkt zijn tot traditionele merge‑velden. Schakel het in met `setUseNonMergeFields(true)` wanneer je een schoner sjabloon‑projecten met deze aanpak?

Integreer de bovenstaande code‑aties. evaluatie.

---

**Laatst bijgewerkt:** 2026-01-24  
**Getest met:** Aspose.Words for Java (latest release)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}