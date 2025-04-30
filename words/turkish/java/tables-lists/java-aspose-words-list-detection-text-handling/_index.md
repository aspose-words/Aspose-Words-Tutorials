---
"date": "2025-03-28"
"description": "Aspose.Words for Java kullanarak liste algılama, metin işleme ve daha fazlasında ustalaşmayı öğrenin. Bu kılavuz, boşluklarla ayrılmış listeleri algılamayı, boşlukları kırpmayı, belge yönünü belirlemeyi, otomatik numaralandırma algılamayı devre dışı bırakmayı ve köprü metinlerini yönetmeyi kapsar."
"title": "Aspose.Words ile Java'da Ana Liste Algılama ve Metin İşleme&#58; Tam Bir Kılavuz"
"url": "/tr/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Aspose.Words ile Java'da Ana Liste Algılama ve Metin İşleme: Eksiksiz Bir Kılavuz

## giriiş

Düz metin belgeleriyle çalışmak, tutarsız sınırlayıcılar ve biçimlendirme sorunları nedeniyle listeler gibi yapılandırılmış verileri tanımlamada sıklıkla zorluklar sunar. Java için Aspose.Words kitaplığı, boşluklarla numaralandırmayı algılama, boşlukları kırpma, belge yönünü belirleme, otomatik numaralandırma algılamayı devre dışı bırakma ve metin belgelerindeki köprüleri yönetme gibi bu sorunları ele almak için sağlam özellikler sunar. Bu eğitim, Aspose.Words kullanarak metin verilerini etkili bir şekilde işlemenizi sağlar.

**Ne Öğreneceksiniz:**
- Boşluklarla ayrılmış listeleri algılama teknikleri
- Belge içeriğinden istenmeyen boşlukları kesme yöntemleri
- Bir metin dosyasının okuma yönünü belirlemeye yönelik yaklaşımlar
- Otomatik numaralandırma algılamayı devre dışı bırakmanın yolları
- Düz metin belgelerindeki köprü metinlerini tespit etme ve yönetme stratejileri

Bu özellikleri uygulamadan önce gerekli ön koşulları gözden geçirelim.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

### Gerekli Kütüphaneler:
- **Java için Aspose.Words**: Sürüm 25.3 veya üzeri.

### Çevre Kurulumu:
- Bağımlılıkları yönetmek için gerekli olduklarından, geliştirme ortamınızın Maven veya Gradle'ı desteklediğinden emin olun.

### Bilgi Ön Koşulları:
- Java programlamanın temel anlayışı
- Maven veya Gradle yapı sistemlerine aşinalık

## Aspose.Words'ü Kurma

Projenizde Aspose.Words for Java kullanmaya başlamak için gerekli bağımlılığı eklemeniz gerekir. İşte nasıl:

**Usta:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lisans Edinimi

Aspose.Words'ü tam olarak kullanabilmek için lisans almayı düşünebilirsiniz:
- **Ücretsiz Deneme**: Özellikleri test etmek için kullanılabilir.
- **Geçici Lisans**: Sınırlama olmaksızın değerlendirme amaçlıdır.
- **Satın almak**: Sürekli kullanım için tam lisans.

Lisansınızı aldıktan sonra, kütüphanenin tüm işlevlerini açmak için onu uygulamanızda başlatın.

## Uygulama Kılavuzu

Her bir özelliği inceleyelim ve Aspose.Words for Java kullanarak bunların nasıl uygulanacağını görelim.

### Boşluklarla Numaralandırmayı Algıla

**Genel Bakış:** Bu özellik, ayırıcı olarak boşluk kullanan düz metin belgelerindeki listeleri tanımlamanıza olanak tanır.

#### Adım 1: Belgeyi Yükleyin
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Adım 2: Liste Algılamasını Doğrula
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Parametreler ve Yöntemler:*
- `setDetectNumberingWithWhitespaces(true)`: Ayrıştırıcıyı boşluk ayırıcıları olan listeleri tanıyacak şekilde yapılandırır.
- `doc.getLists().getCount()`: Belgede algılanan listelerin sayısını alır.

### Öndeki ve Arkadaki Boşlukları Kırp

**Genel Bakış:** Bu özellik, düz metin belgelerinde satırların başında veya sonunda bulunan gereksiz boşlukları keserek temiz metin biçimlendirmesini sağlar.

#### Adım 1: Yükleme Seçeneklerini Yapılandırın
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Adım 2: Kırpmayı Doğrulayın
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Anahtar Yapılandırmalar:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Satırların başından itibaren boşlukları kırpar.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Satır sonlarındaki boşlukları kaldırır.

### Belge Yönünü Algıla

**Genel Bakış:** İbranice veya Arapça metin gibi bir belgenin sağdan sola (RTL) okunması gerekip gerekmediğini belirleyin.

#### Adım 1: Otomatik Algılamayı Ayarlayın
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Otomatik Numaralandırma Algılamayı Devre Dışı Bırak

**Genel Bakış:** Kütüphanenin liste öğelerini otomatik olarak algılamasını ve biçimlendirmesini önleyin.

#### Adım 1: Yükleme Seçeneklerini Yapılandırın
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Metindeki Köprüleri Algıla

**Genel Bakış:** Düz metin belgelerindeki köprü metinlerini tanımlayın ve yönetin.

#### Adım 1: Algılama Seçeneklerini Ayarlayın
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Pratik Uygulamalar

1. **İçerik Yönetim Sistemleri (CMS):** Kullanıcı tarafından oluşturulan içeriği otomatik olarak yapılandırılmış listeler halinde biçimlendirin.
2. **Veri Çıkarma Araçları:** Analiz için yapılandırılmamış verileri düzenlemek amacıyla liste algılamayı kullanın.
3. **Metin İşleme Boru Hatları:** Boşlukları kırparak ve metin yönünü algılayarak belge ön işlemeyi geliştirin.

## Performans Hususları

Performansı optimize etmek için:
- Gerekli özelliklere odaklanarak, belgeleri minimum işlemle yükleyin.
- Mümkün olan durumlarda büyük belgeleri parçalar halinde işleyerek bellek kullanımını yönetin.

## Çözüm

Java için Aspose.Words'ü kullanarak, düz metin belgelerindeki metinsel verileri verimli bir şekilde yönetebilirsiniz. Boşluklarla ayrılmış listeleri algılamaktan metin yönünü ve köprü metinlerini işlemeye kadar, bu güçlü araçlar sağlam belge düzenleme olanağı sağlar. Daha fazla araştırma için bkz. [Aspose.Words belgeleri](https://reference.aspose.com/words/java/) veya ücretsiz denemeyi deneyin.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}