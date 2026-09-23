---
date: '2026-02-06'
description: Aspose.Words for Java ile HTML VML nasıl yüklenir, HTML Java dosyaları
  nasıl şifrelenir, HTML temel URI'si nasıl ayarlanır ve HTML kontrol seçenekleri
  nasıl yapılandırılır öğrenin.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Aspose.Words for Java kullanarak HTML VML yükleme – Tam Kılavuz
url: /tr/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile Kapsamlı HTML Özellikleri: Geliştirici Rehberi

## Giriş

Belge işleme dünyasının karmaşık yapısında gezinmek zorlayıcı olabilir, özellikle çeşitli HTML özellikleriyle uğraşırken. Vector Markup Language (VML) desteği, şifreli belgeler veya belirli HTML içe aktarma davranışlarıyla ilgileniyor olsanız, **Aspose.Words for Java** sağlam bir çözüm sunar. Bu rehberde **how to load html vml**'yi verimli ve güvenli bir şekilde nasıl yapacağınızı öğrenecek, ayrıca **encrypt html java**, **set html base uri**, ve **configure html control** gibi ilgili görevleri de kapsayacaksınız.

**Öğrenecekleriniz:**
- HTML belgelerini VML desteğiyle nasıl yükleyeceğinizi.
- Sabit sayfa HTML ve uyarıların işlenmesi teknikleri.
- Şifreli ve parola korumalı HTML belgelerinin şifrelenmesi ve yüklenmesi yöntemleri.
- HTML Load Options içinde temel URI'ların kullanılması.
- HTML giriş öğelerinin yapılandırılmış belge etiketleri veya form alanları olarak içe aktarılması.
- `<noscript>` öğelerinin HTML yüklemesi sırasında yok sayılması.
- HTML yapı korumasını kontrol etmek için blok içe aktarma modlarının yapılandırılması.
- Özel yazı tipleri için `@font-face` kurallarının desteklenmesi.

## Hızlı Yanıtlar
- **HTML yüklerken VML'i etkinleştirmenin temel yolu nedir?** `loadOptions.setSupportVml(true)` ayarlayın.
- **Parola korumalı HTML dosyalarını yükleyebilir miyim?** Evet, parolayı `HtmlLoadOptions`'a geçirin.
- **Göreceli resim yollarını nasıl çözerim?** `loadOptions.setBaseUri("your/base/uri")` kullanın.
- **`<select>` öğesini bir form alanı olarak içe aktarmak mümkün mü?** `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` ayarlayın.
- **Yükleme sırasında uyarıları yakalayan sınıf hangisidir?** `IWarningCallback` uygulayın ve `loadOptions.setWarningCallback(...)`'a atayın.

## Önkoşullar

Aspose.Words for Java ile çeşitli HTML özelliklerini uygulamaya başlamadan önce, ortamınızın doğru şekilde ayarlandığından emin olun:

- **Gerekli Kütüphaneler:** Aspose.Words kütüphanesinin 25.3 veya daha yeni bir sürümüne ihtiyacınız var.
- **Geliştirme Ortamı:** Bu rehber, bağımlılık yönetimi için Maven veya Gradle kullandığınızı varsayar.
- **Bilgi Temeli:** Java'ya temel bir anlayış ve HTML belgelerine aşinalık faydalı olacaktır.

## Aspose.Words Kurulumu

Aspose.Words ile çalışmaya başlamak için önce projeye eklemeniz gerekir. Aşağıda kütüphaneyi Maven ve Gradle kullanarak kurma adımları verilmiştir:

### Maven

Aşağıdaki bağımlılığı `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

`build.gradle` dosyanıza şunu ekleyin:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lisans Alımı

Aspose.Words tam işlevsellik için bir lisans gerektirir. Ücretsiz deneme alabilir, geçici bir lisans talep edebilir veya kalıcı bir lisans satın alabilirsiniz. Daha fazla detay için [satın alma sayfasını](https://purchase.aspose.com/buy) ziyaret edin.

Java projenizde Aspose.Words'i başlatmak için lisanslamayı doğru şekilde yaptığınızdan emin olun:

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

## Uygulama Rehberi

Uygulamayı, uygulamak istediğimiz özelliklere göre bölümlere ayıracağız.

### Aspose.Words ile html vml nasıl yüklenir

**Genel Bakış:**  
VML desteğiyle bir HTML belgesi yüklemek, grafikler ve şekiller gibi vektör grafiklerin çok yönlü işlenmesini sağlar. Bu, temel anahtar kelime **load html vml** için temel adımdır.

#### Adım‑adım

1. **Yükleme Seçeneklerini Ayarlama**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Belgeyi Yükleme**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Görsel Türünü Doğrulama**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Sabit HTML Yükleme ve Uyarıları İşleme

**Genel Bakış:**  
Sabit sayfa HTML belgelerini yüklemek, doğru işleme için yönetilmesi gereken uyarılar üretebilir.

#### Adım‑adım

1. **Uyarı Geri Çağrısını Tanımlama**

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

2. **Yükleme Seçeneklerini Yapılandırma**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Belgeyi Yükleme ve Uyarıları Kontrol Etme**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### HTML Belgelerini Şifreleme

**Genel Bakış:**  
Bir HTML belgesini parola ile şifrelemek, hassas bilgiler için güvenli erişim sağlar—bu, **encrypt html java** senaryosunu ele alır.

#### Adım‑adım

1. **Dijital İmza Seçeneklerini Hazırlama**

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

2. **Belgeyi İmzalama ve Şifreleme**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Şifreli Belgeyi Yükleme**

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
**set html base uri** belirtmek, özellikle resimler veya diğer bağlı kaynaklarla çalışırken göreceli URI'ların çözülmesine yardımcı olur.

#### Adım‑adım

1. **Temel URI ile Yükleme Seçeneklerini Yapılandırma**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Belgeyi Yükleme ve Görseli Doğrulama**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### HTML Select'i Yapılandırılmış Belge Etiketi Olarak İçe Aktarma

**Genel Bakış:**  
**configure html control** davranışını ayarlamak için, `<select>` öğelerini Yapılandırılmış Belge Etiketleri olarak içe aktarabilir, Word belgelerindeki form alanları üzerinde daha ince kontrol elde edebilirsiniz.

#### Adım‑adım

1. **Tercih Edilen Kontrol Türünü Ayarlama**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Belgeyi Yükleme ve Yapıyı Doğrulama**

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

## Yaygın Sorunlar ve Çözümler

| Sorun | Sebep | Çözüm |
|-------|--------|-----|
| VML grafikleri görünmüyor | `supportVml` bayrağı varsayılan (`false`) olarak bırakıldı | Yüklemeden önce `loadOptions.setSupportVml(true)` ayarlandığından emin olun. |
| Yükleme sonrası resimler eksik | Göreceli yollar çözülemedi | **set html base uri** (`loadOptions.setBaseUri(...)`) kullanarak doğru klasöre işaret edin. |
| Parola korumalı HTML istisna fırlatıyor | Parola sağlanmadı | Parolayı `new HtmlLoadOptions("yourPassword")`'a geçirin. |
| Form kontrolleri düz metin olarak görünüyor | Yanlış `HtmlControlType` | Gerekli olduğunda `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` veya `FormField` ayarlayın. |
| Beklenmeyen uyarılar | İşlenmemiş HTML öğeleri | Uyarıları yakalamak ve incelemek için `IWarningCallback` uygulayın. |

## Sıkça Sorulan Sorular

**S: VML ve modern SVG grafiklerini içeren HTML dosyalarını yükleyebilir miyim?**  
C: Evet. VML'i `setSupportVml(true)` ile etkinleştirin; SVG otomatik olarak Aspose.Words tarafından işlenir.

**S: Dijital sertifika kullanmadan bir HTML belgesini nasıl şifrelerim?**  
C: Parola kabul eden `HtmlLoadOptions` yapıcıyı kullanın ve parolayı ayarladıktan sonra belgeyi `Document.save(..., SaveFormat.HTML)` ile kaydedin.

**S: Temel URI var olmayan bir klasöre işaret ederse ne olur?**  
C: Aspose.Words eksik kaynaklar için bir `FileNotFoundException` fırlatır. Yüklemeden önce yolu doğrulayın.

**S: Tüm HTML form öğeleri için varsayılan kontrol tipini değiştirmek mümkün mü?**  
C: Evet. Global olarak uygulamak için `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` kullanın.

**S: Uyarı geri çağrıları thread‑safe mi?**  
C: Belgeleri eşzamanlı olarak yüklemeyi planlıyorsanız, geri çağrı uygulaması thread‑safe olmalıdır. Senkronize koleksiyonlar veya thread‑local depolama kullanın.

---

**Son Güncelleme:** 2026-02-06  
**Test Edilen Versiyon:** Aspose.Words for Java 25.3  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}