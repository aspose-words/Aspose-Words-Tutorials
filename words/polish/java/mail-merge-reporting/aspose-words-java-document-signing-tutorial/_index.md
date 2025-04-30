---
"date": "2025-03-28"
"description": "Dowiedz się, jak zautomatyzować podpisywanie dokumentów za pomocą Aspose.Words for Java. Ten samouczek obejmuje konfigurację środowiska, tworzenie danych testowych, dodawanie wierszy podpisu i cyfrowe podpisywanie dokumentów."
"title": "Automatyzacja podpisywania dokumentów w Javie za pomocą Aspose.Words&#58; Kompleksowy przewodnik"
"url": "/pl/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Automatyzacja podpisywania dokumentów w Javie za pomocą Aspose.Words: kompleksowy przewodnik

## Wstęp

dzisiejszym dynamicznym świecie biznesu efektywne zarządzanie dokumentami jest niezbędne. Automatyzacja tworzenia i cyfrowego podpisywania dokumentów może zaoszczędzić czas i zminimalizować błędy. Ten samouczek przeprowadzi Cię przez korzystanie z Aspose.Words for Java w celu tworzenia danych testowych dla sygnatariuszy, dodawania linii podpisu i cyfrowego podpisywania dokumentów.

**Czego się nauczysz:**
- Konfigurowanie Aspose.Words w projekcie Java
- Tworzenie danych sygnatariusza testowego za pomocą języka Java
- Dodawanie linii podpisu do dokumentów Word
- Cyfrowe podpisywanie dokumentów przy użyciu certyfikatów cyfrowych

Zacznijmy od przygotowania środowiska programistycznego!

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że Twoja konfiguracja spełnia poniższe wymagania:

- **Zestaw narzędzi programistycznych Java (JDK):** Wersja 8 lub nowsza.
- **Zintegrowane środowisko programistyczne (IDE):** Takie jak IntelliJ IDEA czy Eclipse.
- **Aspose.Words dla Javy:** Bibliotekę tę można dołączyć za pomocą Maven lub Gradle.

### Wymagania wstępne dotyczące wiedzy

Podstawowa znajomość programowania w Javie i obsługa plików i strumieni będzie przydatna. Jeśli jesteś nowy w Aspose, nie martw się — omówimy podstawy.

## Konfigurowanie Aspose.Words

Aby użyć Aspose.Words for Java w swoim projekcie, wykonaj następujące kroki:

### Zależność Maven

Dodaj następującą zależność do swojego `pom.xml` plik:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Zależność Gradle

W przypadku projektów Gradle należy uwzględnić tę linię w pliku `build.gradle` plik:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Nabycie licencji

Aspose oferuje różne opcje licencjonowania:

- **Bezpłatna wersja próbna:** Pobierz bezpłatną wersję próbną, aby przetestować funkcje.
- **Licencja tymczasowa:** Uzyskaj tymczasową licencję w celach ewaluacyjnych.
- **Zakup:** Aby uzyskać pełny dostęp, należy zakupić licencję na stronie internetowej Aspose.

Upewnij się, że Twój projekt jest skonfigurowany z niezbędnymi zależnościami i wszelkimi wymaganymi licencjami. Ta konfiguracja pozwoli Ci bezproblemowo wykorzystać potężne możliwości manipulacji dokumentami Aspose.

## Przewodnik wdrażania

Przeprowadzimy Cię krok po kroku przez każdą funkcję, zaczynając od utworzenia danych sygnatariusza testowego.

### Funkcja 1: Utwórz dane testowe dla sygnatariuszy

#### Przegląd

Ta funkcja generuje listę sygnatariuszy z unikalnymi identyfikatorami, nazwami, stanowiskami i obrazami. Jest to niezbędne do testowania scenariuszy podpisywania dokumentów bez używania prawdziwych danych.

##### Krok 1: Skonfiguruj swoją klasę Java

Utwórz klasę o nazwie `SignPersonCreator` i zaimportuj niezbędne biblioteki:

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

##### Wyjaśnienie

- **UUID:** Generuje unikalny identyfikator dla każdego sygnatariusza.
- **pobierzBytesFromStream:** Konwertuje plik obrazu na tablicę bajtów w celu przechowywania.

### Funkcja 2: Dodaj wiersz podpisu do dokumentu

#### Przegląd

Funkcja ta dodaje do dokumentu linię podpisu, kojarząc ją z danymi osoby podpisującej.

##### Krok 1: Utwórz klasę SignatureLineAdder

Wdrożyć `SignatureLineAdder` klasa w następujący sposób:

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

##### Wyjaśnienie

- **Opcje SignatureLine:** Konfiguruje imię i nazwisko oraz tytuł osoby podpisującej.
- **wstawLinięPodpisu:** Wstawia wiersz podpisu do dokumentu w aktualnej pozycji kursora.

### Funkcja 3: Podpisz dokument za pomocą certyfikatu cyfrowego

#### Przegląd

Funkcja ta umożliwia cyfrowe podpisanie dokumentu za pomocą certyfikatu cyfrowego, co gwarantuje autentyczność i integralność.

##### Krok 1: Utwórz klasę DocumentSigner

Wdrożyć `DocumentSigner` klasa:

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

##### Wyjaśnienie

- **Posiadacz certyfikatu:** Reprezentuje certyfikat cyfrowy używany do podpisywania.
- **podpisać:** Metoda podpisywania dokumentu przy użyciu określonych opcji i certyfikatu.

## Wniosek

W tym samouczku dowiedziałeś się, jak zautomatyzować tworzenie i podpisywanie dokumentów w Javie za pomocą Aspose.Words. Wykonując te kroki, możesz usprawnić procesy zarządzania dokumentami, zwiększyć bezpieczeństwo i zapewnić integralność danych. Aby uzyskać dalsze informacje, rozważ zanurzenie się w bardziej zaawansowanych funkcjach Aspose.Words.

**Następne kroki:**
- Poznaj dodatkowe funkcje Aspose.Words, takie jak korespondencja seryjna czy generowanie raportów.
- Aby uzyskać szczegółowe instrukcje i informacje na temat interfejsu API, przejrzyj dokumentację Aspose.
- Eksperymentuj z różnymi formatami dokumentów obsługiwanymi przez Aspose.Words.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}