---
"date": "2025-03-28"
"description": "VML desteği, şifreleme, HTML içe aktarma seçenekleri ve daha fazlası dahil olmak üzere belge işleme konusunda uzmanlaşmak için Aspose.Words for Java'yı nasıl kullanacağınızı öğrenin."
"title": "Aspose.Words for Java&#58; Kapsamlı HTML Özellikleri ve Belge İşleme Kılavuzu"
"url": "/tr/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Java için Aspose.Words ile Kapsamlı HTML Özellikleri: Bir Geliştiricinin Kılavuzu

## giriiş

Karmaşık belge işleme dünyasında gezinmek, özellikle çeşitli HTML özelliklerini ele alırken göz korkutucu olabilir. İster Vektör İşaretleme Dili (VML) desteği, ister şifrelenmiş belgeler veya belirli HTML içe aktarma davranışlarıyla uğraşıyor olun, **Java için Aspose.Words** sağlam bir çözüm sunar. Bu kılavuzda, bu işlevleri Aspose.Words kullanarak sorunsuz bir şekilde nasıl uygulayacağınızı ve belge işleme yeteneklerinizi nasıl geliştireceğinizi inceleyeceğiz.

**Ne Öğreneceksiniz:**
- VML desteğiyle HTML dokümanları nasıl yüklenir.
- Sabit sayfa HTML ve uyarıları işleme teknikleri.
- Parola korumalı HTML belgelerini şifreleme ve yükleme yöntemleri.
- HTML Yükleme Seçeneklerinde temel URI'leri kullanma.
- HTML giriş öğelerini yapılandırılmış belge etiketleri veya form alanları olarak içe aktarma.
- Görmezden gelmek `<noscript>` HTML yükleme sırasında öğeler.
- HTML yapısının korunmasını kontrol etmek için blok içe aktarma modlarını yapılandırma.
- Destek `@font-face` özelleştirilmiş yazı tipleri için kurallar.

Bu içgörülerle, çok çeşitli HTML işleme görevlerini ele almak için iyi donanımlı olacaksınız. Önce ön koşullara ve kuruluma bir göz atalım!

## Ön koşullar

Aspose.Words for Java ile çeşitli HTML özelliklerini uygulamaya başlamadan önce, ortamınızın düzgün bir şekilde ayarlandığından emin olun:

- **Gerekli Kütüphaneler:** Aspose.Words kütüphanesinin 25.3 veya üzeri sürümüne ihtiyacınız var.
- **Geliştirme Ortamı:** Bu kılavuz, bağımlılık yönetimi için Maven veya Gradle kullandığınızı varsayar.
- **Bilgi Bankası:** Java'da temel bir anlayışa ve HTML belgelerine aşinalığa sahip olmak faydalı olacaktır.

## Aspose.Words'ü Kurma

Aspose.Words ile çalışmaya başlamak için öncelikle onu projenize dahil etmeniz gerekir. Aşağıda Maven ve Gradle kullanarak kütüphaneyi kurma adımları verilmiştir:

### Usta

Aşağıdaki bağımlılığı ekleyin `pom.xml` dosya:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Bunu da ekleyin `build.gradle` dosya:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lisans Edinimi

Aspose.Words tam işlevsellik için bir lisans gerektirir. Ücretsiz bir deneme edinebilir, geçici bir lisans talep edebilir veya kalıcı bir lisans satın alabilirsiniz. Ziyaret edin [satın alma sayfası](https://purchase.aspose.com/buy) Daha detaylı bilgi için.

Java projenizde Aspose.Words'ü başlatmak için lisanslamayı doğru şekilde ayarladığınızdan emin olun:

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

## Uygulama Kılavuzu

Uygulamayı, uygulamak istediğimiz özelliklere göre bölümlere ayıracağız.

### HTML Belgelerinde VML'yi Destekleyin

**Genel Bakış:**
VML desteğiyle veya desteği olmadan bir HTML belgesi yüklemek, vektör grafiklerinin çok yönlü işlenmesine olanak tanır. Bu özellik, grafikler ve şekiller gibi grafiksel öğeler içeren belgelerle uğraşırken çok önemlidir.

#### Adım Adım Uygulama:

1. **Yükleme Seçeneklerini Ayarla**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // VML desteğini etkinleştir
   ```

2. **Belgeyi Yükle**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **Görüntü Türünü Doğrula**
   
   Görüntü türünün beklentilerinizle uyumlu olduğundan emin olun:
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // Gerçek mantığa göre ayarlayın

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### HTML Sabit Yükle ve Uyarıları İşle

**Genel Bakış:**
Sabit sayfalı HTML belgelerinin yüklenmesi, doğru işleme için yönetilmesi gereken uyarılar üretebilir.

#### Adım Adım Uygulama:

1. **Uyarı Geri Aramasını Tanımla**
   
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

2. **Yükleme Seçeneklerini Yapılandırın**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   ListDocumentWarnings warningCallback = new ListDocumentWarnings();
   loadOptions.setWarningCallback(warningCallback);
   ```

3. **Belgeyi Yükle ve Uyarıları Kontrol Et**
   
   ```java
   Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

   if (warningCallback.warnings().size() != 1) {
       throw new AssertionError("Unexpected number of warnings.");
   }
   ```

### HTML Belgelerini Şifrele

**Genel Bakış:**
Bir HTML belgesinin parola ile şifrelenmesi, hassas bilgiler için olmazsa olmaz olan güvenli erişimi sağlar.

#### Adım Adım Uygulama:

1. **Dijital İmza Seçeneklerini Hazırlayın**
   
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

2. **Belgeyi İmzala ve Şifrele**
   
   ```java
   String inputFileName = "path/to/Encrypted.docx";
   String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

   DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
   ```

3. **Şifrelenmiş Belgeyi Yükle**
   
   ```java
   import com.aspose.words.Document;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
   Document doc = new Document(outputFileName, loadOptions);

   if (!doc.getText().trim().equals("Test encrypted document.")) {
       throw new AssertionError("Unexpected document text.");
   }
   ```

### HTML Yükleme Seçenekleri için Temel URI

**Genel Bakış:**
Temel bir URI belirtmek, özellikle resimler veya diğer bağlantılı kaynaklarla uğraşırken, göreli URI'lerin çözülmesine yardımcı olur.

#### Adım Adım Uygulama:

1. **Yükleme Seçeneklerini Temel URI ile Yapılandırın**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
   ```

2. **Belgeyi Yükle ve Resmi Doğrula**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;

   Document doc = new Document("path/to/Missing image.html", loadOptions);
   Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

   if (!imageShape.isImage()) {
       throw new AssertionError("Expected an image shape.");
   }
   ```

### HTML Seç'i Yapılandırılmış Belge Etiketi Olarak İçe Aktar

**Genel Bakış:**
İthalat `<select>` Öğeleri yapılandırılmış belge etiketleri olarak kullanmak Word belgelerinde daha iyi kontrol ve biçimlendirme sağlar.

#### Adım Adım Uygulama:

1. **Tercih Edilen Kontrol Türünü Ayarla**
   
   ```java
   import com.aspose.words.HtmlLoadOptions;
   import com.aspose.words.ControlType;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
   ```

2. **Belgeyi Yükle ve Yapıyı Doğrula**
   
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

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}