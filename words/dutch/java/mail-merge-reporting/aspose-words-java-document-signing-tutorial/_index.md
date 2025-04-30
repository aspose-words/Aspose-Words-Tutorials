---
"date": "2025-03-28"
"description": "Leer hoe u documentondertekening kunt automatiseren met Aspose.Words voor Java. Deze tutorial behandelt het instellen van uw omgeving, het maken van testgegevens, het toevoegen van handtekeningregels en het digitaal ondertekenen van documenten."
"title": "Automatiseer het ondertekenen van documenten in Java met Aspose.Words&#58; een uitgebreide handleiding"
"url": "/nl/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Automatiseer documentondertekening in Java met Aspose.Words: een uitgebreide handleiding

## Invoering

In de huidige snelle zakenwereld is efficiënt documentbeheer essentieel. Het automatiseren van het aanmaken en digitaal ondertekenen van documenten kan tijd besparen en fouten minimaliseren. Deze tutorial begeleidt je bij het gebruik van Aspose.Words voor Java om testgegevens voor ondertekenaars te maken, handtekeningregels toe te voegen en documenten digitaal te ondertekenen.

**Wat je leert:**
- Aspose.Words instellen in een Java-project
- Test-ondertekenaarsgegevens maken met Java
- Handtekeningregels toevoegen aan Word-documenten
- Documenten digitaal ondertekenen met behulp van digitale certificaten

Laten we beginnen met het voorbereiden van uw ontwikkelomgeving!

## Vereisten

Voordat u met de tutorial begint, moet u ervoor zorgen dat uw configuratie aan de volgende vereisten voldoet:

- **Java-ontwikkelingskit (JDK):** Versie 8 of hoger.
- **Geïntegreerde ontwikkelomgeving (IDE):** Zoals IntelliJ IDEA of Eclipse.
- **Aspose.Words voor Java:** Deze bibliotheek kan worden opgenomen via Maven of Gradle.

### Kennisvereisten

Een basiskennis van Java-programmering en vertrouwdheid met het werken met bestanden en streams zijn een pré. Ben je nieuw met Aspose? Geen zorgen, we behandelen de basisprincipes.

## Aspose.Words instellen

Volg deze stappen om Aspose.Words voor Java in uw project te gebruiken:

### Maven-afhankelijkheid

Voeg de volgende afhankelijkheid toe aan uw `pom.xml` bestand:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle-afhankelijkheid

Voor Gradle-projecten neemt u deze regel op in uw `build.gradle` bestand:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Licentieverwerving

Aspose biedt verschillende licentieopties:

- **Gratis proefperiode:** Download een gratis proefversie om de functies te testen.
- **Tijdelijke licentie:** Vraag een tijdelijke vergunning aan voor evaluatiedoeleinden.
- **Aankoop:** Voor volledige toegang koopt u een licentie op de website van Aspose.

Zorg ervoor dat uw project is geconfigureerd met de benodigde afhankelijkheden en eventuele vereiste licenties. Met deze configuratie kunt u de krachtige mogelijkheden van Aspose voor documentbewerking naadloos benutten.

## Implementatiegids

We leggen elke functie stap voor stap uit, te beginnen met het maken van testondertekeningsgegevens.

### Functie 1: Testgegevens voor ondertekenaars maken

#### Overzicht

Deze functie genereert een lijst met ondertekenaars met unieke ID's, namen, functies en afbeeldingen. Dit is essentieel voor het testen van documentondertekeningsscenario's zonder gebruik te maken van echte data.

##### Stap 1: Stel uw Java-klasse in

Maak een klasse met de naam `SignPersonCreator` en importeer de benodigde bibliotheken:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### Uitleg

- **UUID:** Genereert een unieke identificatie voor elke ondertekenaar.
- **Bytes ophalen uit Stream:** Converteert een afbeeldingsbestand naar een byte-array voor opslag.

### Functie 2: Handtekeningregel toevoegen aan document

#### Overzicht

Met deze functie voegt u een handtekeningregel toe aan uw document en koppelt u deze aan de gegevens van de ondertekenaar.

##### Stap 1: SignatureLineAdder-klasse maken

Implementeer de `SignatureLineAdder` klasse als volgt:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### Uitleg

- **Handtekeningregelopties:** Configureert de naam en titel van de ondertekenaar.
- **Handtekeningregel invoegen:** Voegt een handtekeningregel in het document in op de huidige cursorpositie.

### Functie 3: Document ondertekenen met digitaal certificaat

#### Overzicht

Met deze functie wordt het document digitaal ondertekend met een digitaal certificaat, waardoor de authenticiteit en integriteit ervan worden gegarandeerd.

##### Stap 1: DocumentSigner-klasse maken

Implementeer de `DocumentSigner` klas:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### Uitleg

- **Certificaathouder:** Geeft het digitale certificaat weer dat wordt gebruikt voor ondertekening.
- **teken:** Methode waarmee het document wordt ondertekend met de opgegeven opties en het certificaat.

## Conclusie

In deze tutorial heb je geleerd hoe je het maken en ondertekenen van documenten in Java kunt automatiseren met Aspose.Words. Door deze stappen te volgen, kun je je documentbeheerprocessen stroomlijnen, de beveiliging verbeteren en de gegevensintegriteit waarborgen. Voor meer informatie kun je je verdiepen in de meer geavanceerde functies van Aspose.Words.

**Volgende stappen:**
- Ontdek extra Aspose.Words-functies zoals samenvoegen en rapporten genereren.
- Raadpleeg de Aspose-documentatie voor gedetailleerde handleidingen en API-referenties.
- Experimenteer met verschillende documentformaten die door Aspose.Words worden ondersteund.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}