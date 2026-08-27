---
date: '2026-02-06'
description: Leer hoe u HTML VML laadt met Aspose.Words voor Java, HTML‑Java‑bestanden
  versleutelt, de HTML‑basisi‑URI instelt en HTML‑controleopties configureert.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: HTML VML laden met Aspose.Words voor Java – Complete gids
url: /nl/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uitgebreide HTML-functies met Aspose.Words voor Java: Een ontwikkelaarsgids

## Introductie

Het navigeren door de complexe wereld van documentverwerking kan ontmoedigend zijn, vooral bij het omgaan met verschillende HTML-functies. Of u nu te maken heeft met Vector Markup Language (VML)-ondersteuning, versleutelde documenten, of specifieke HTML-importgedragingen, **Aspose.Words for Java** biedt een robuuste oplossing. In deze gids leert u **how to load html vml** efficiënt en veilig, terwijl ook gerelateerde taken worden behandeld zoals **encrypt html java**, **set html base uri**, en **configure html control** opties.

**Wat u zult leren:**
- Hoe HTML-documenten met VML-ondersteuning te laden.
- Technieken voor het verwerken van vaste‑pagina HTML en waarschuwingen.
- Methoden voor het versleutelen en laden van met wachtwoord beveiligde HTML-documenten.
- Het gebruiken van base-URI's in HTML Load Options.
- HTML-invoerelementen importeren als gestructureerde documenttags of formuliervelden.
- `<noscript>`-elementen negeren tijdens het laden van HTML.
- Blok‑importmodi configureren om het behoud van HTML-structuur te regelen.
- `@font-face`-regels ondersteunen voor aangepaste lettertypen.

## Snelle antwoorden
- **Wat is de primaire manier om VML in te schakelen bij het laden van HTML?** Stel `loadOptions.setSupportVml(true)` in.
- **Kan ik met wachtwoord‑beveiligde HTML‑bestanden laden?** Ja, geef het wachtwoord door aan `HtmlLoadOptions`.
- **Hoe los ik relatieve afbeeldingspaden op?** Gebruik `loadOptions.setBaseUri("your/base/uri")`.
- **Is het mogelijk om `<select>` te importeren als een formulierveld?** Stel `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` in.
- **Welke klasse vangt waarschuwingen tijdens het laden?** Implementeer `IWarningCallback` en wijs deze toe aan `loadOptions.setWarningCallback(...)`.

## Voorvereisten

Voordat we beginnen met het implementeren van verschillende HTML-functies met Aspose.Words voor Java, zorg ervoor dat uw omgeving correct is ingesteld:

- **Vereiste bibliotheken:** U heeft de Aspose.Words-bibliotheek versie 25.3 of later nodig.
- **Ontwikkelomgeving:** Deze gids gaat ervan uit dat u Maven of Gradle gebruikt voor afhankelijkheidsbeheer.
- **Kennisbasis:** Een basisbegrip van Java en vertrouwdheid met HTML-documenten is nuttig.

## Aspose.Words instellen

Om met Aspose.Words te beginnen, moet u het eerst in uw project opnemen. Hieronder staan de stappen om de bibliotheek in te stellen met Maven en Gradle:

### Maven

Voeg de volgende afhankelijkheid toe aan uw `pom.xml`-bestand:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Neem dit op in uw `build.gradle`-bestand:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Licentie‑acquisitie

Aspose.Words vereist een licentie voor volledige functionaliteit. U kunt een gratis proefversie verkrijgen, een tijdelijke licentie aanvragen, of een permanente licentie kopen. Bezoek de [purchase page](https://purchase.aspose.com/buy) voor meer details.

Om Aspose.Words in uw Java‑project te initialiseren, zorg ervoor dat u de licentie correct heeft ingesteld:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Implementatie‑gids

We zullen de implementatie opdelen in secties op basis van de functies die we willen implementeren.

### Hoe html vml te laden met Aspose.Words

**Overzicht:**  
Het laden van een HTML‑document met VML‑ondersteuning maakt veelzijdige weergave van vectorafbeeldingen zoals grafieken en vormen mogelijk. Dit is de kernstap voor het primaire trefwoord **load html vml**.

#### Stapsgewijs

1. **Load‑opties instellen**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Document laden**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Afbeeldingstype verifiëren**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### HTML Fixed laden en waarschuwingen verwerken

**Overzicht:**  
Het laden van vaste‑pagina HTML‑documenten kan waarschuwingen opleveren die beheerd moeten worden voor nauwkeurige verwerking.

#### Stapsgewijs

1. **Waarschuwings‑callback definiëren**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Load‑opties configureren**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Document laden en waarschuwingen controleren**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### HTML‑documenten versleutelen

**Overzicht:**  
Het versleutelen van een HTML‑document met een wachtwoord zorgt voor veilige toegang, wat essentieel is voor gevoelige informatie—dit behandelt het **encrypt html java**‑scenario.

#### Stapsgewijs

1. **Digitale handtekening‑opties voorbereiden**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Document ondertekenen en versleutelen**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Versleuteld document laden**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base‑URI voor HTML Load Options

**Overzicht:**  
Het specificeren van een **set html base uri** helpt bij het oplossen van relatieve URI's, vooral bij afbeeldingen of andere gekoppelde bronnen.

#### Stapsgewijs

1. **Load‑opties configureren met base‑URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Document laden en afbeelding verifiëren**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### HTML‑select importeren als gestructureerde documenttag

**Overzicht:**  
Om het gedrag van **configure html control** te regelen, kunt u `<select>`‑elementen importeren als Structured Document Tags, waardoor u fijnmazigere controle krijgt over formuliervelden in Word‑documenten.

#### Stapsgewijs

1. **Voorkeur‑controltype instellen**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Document laden en structuur verifiëren**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Veelvoorkomende problemen en oplossingen

| Probleem | Reden | Oplossing |
|-------|--------|-----|
| VML‑grafieken verschijnen niet | `supportVml`‑vlag staat op de standaardwaarde (`false`) | Zorg ervoor dat `loadOptions.setSupportVml(true)` vóór het laden is ingesteld. |
| Afbeeldingen ontbreken na het laden | Relatieve paden kunnen niet worden opgelost | Gebruik **set html base uri** (`loadOptions.setBaseUri(...)`) om naar de juiste map te wijzen. |
| Met wachtwoord beveiligde HTML veroorzaakt een uitzondering | Wachtwoord niet opgegeven | Geef het wachtwoord door aan `new HtmlLoadOptions("yourPassword")`. |
| Formulierelementen verschijnen als platte tekst | Verkeerde `HtmlControlType` | Stel `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` of `FormField` in zoals nodig. |
| Onverwachte waarschuwingen | Niet‑afgehandelde HTML‑elementen | Implementeer `IWarningCallback` om waarschuwingen vast te leggen en te beoordelen. |

## Veelgestelde vragen

**V: Kan ik HTML‑bestanden laden die zowel VML‑ als moderne SVG‑grafieken bevatten?**  
A: Ja. Schakel VML in met `setSupportVml(true)`; SVG wordt automatisch door Aspose.Words afgehandeld.

**V: Hoe versleutel ik een HTML‑document zonder een digitaal certificaat te gebruiken?**  
A: Gebruik de `HtmlLoadOptions`‑constructor die een wachtwoord accepteert en sla het document op met `Document.save(..., SaveFormat.HTML)` nadat het wachtwoord is ingesteld.

**V: Wat gebeurt er als de base‑URI naar een niet‑bestaande map wijst?**  
A: Aspose.Words zal een `FileNotFoundException` werpen voor ontbrekende bronnen. Controleer het pad vóór het laden.

**V: Is het mogelijk om het standaard‑controltype voor alle HTML‑formelementen te wijzigen?**  
A: Ja. Gebruik `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` om dit globaal toe te passen.

**V: Zijn waarschuwings‑callbacks thread‑veilig?**  
A: De callback‑implementatie moet thread‑veilig zijn als u van plan bent documenten gelijktijdig te laden. Gebruik gesynchroniseerde collecties of thread‑local opslag.

---

**Laatst bijgewerkt:** 2026-02-06  
**Getest met:** Aspose.Words for Java 25.3  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}