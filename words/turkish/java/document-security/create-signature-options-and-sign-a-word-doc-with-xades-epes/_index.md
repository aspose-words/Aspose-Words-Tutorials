---
category: general
date: 2026-10-10
description: Java’da XAdES EPES kullanarak imza seçenekleri oluşturun ve bir Word
  belgesini imzalayın. Birkaç net adımda bir sertifika ile ofis belgesini nasıl imzalayacağınızı
  öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: tr
lastmod: 2026-10-10
og_description: Java'da XAdES EPES kullanarak imza seçenekleri oluşturun ve bir Word
  belgesini imzalayın. Bu kılavuz, bir sertifika ile ofis belgesini güvenli bir şekilde
  nasıl imzalayacağınızı gösterir.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: İmza seçenekleri oluşturun ve bir Word belgesini XAdES EPES ile imzalayın
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: İmza seçenekleri oluşturun ve bir Word belgesini XAdES EPES ile imzalayın
url: /tr/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# İmza seçenekleri oluşturma ve XAdES EPES ile bir Word belgesini imzalama

Bir DOCX dosyası için **imza seçenekleri oluşturmanız** gerekiyorsa, bu kılavuz Java'da XAdES‑EPES seviyesini kullanarak bir Word belgesini nasıl imzalayacağınızı gösterir. Sadece birkaç satır kodla bir PFX sertifikasıyla Office belgesini imzalayan tam, çalıştırılabilir bir örnek elde edeceksiniz.

Office belgelerini imzalamak, yasal iş akışları, otomatik sözleşme işleme ve güvenli belge değişimi için yaygın bir gereksinimdir. Bu öğreticide şunları öğreneceksiniz:

* XAdES‑EPES için `SignatureOptions` nasıl yapılandırılır.
* `DigitalSignatureUtil.sign` metodunu **word doc** dosyalarını imzalamak için nasıl çağırılır.
* Sertifika yükleme ve şifre hataları gibi yaygın sorunların nasıl ele alınacağını.

> **Önkoşul** – Java 17 veya daha yeni bir sürüm, GroupDocs.Signature for Java kütüphanesi (veya uyumlu bir XAdES kütüphanesi) ve geçerli bir `.pfx` sertifika dosyası.

## İhtiyacınız olanlar

| Öğe | Sebep |
|------|--------|
| Java 17+ | Modern dil özellikleri ve daha iyi güvenlik API'leri |
| GroupDocs.Signature for Java (or equivalent) | `SignatureOptions`, `XmlDsigLevel` ve `DigitalSignatureUtil` sağlar |
| A PFX certificate (`.pfx`) | Dijital imza için özel anahtarı sağlar |
| Password for the certificate | Özel anahtarı açmak için gereklidir |
| An unsigned DOCX file (`Unsigned.docx`) | **sign office document** yapmak istediğiniz kaynak belge |

Kütüphane JAR'ının sınıf yolunuzda (classpath) olduğundan emin olun:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## Adım 1: Gerekli sınıfları içe aktarın

İmzaları ve dosya I/O'sunu yöneten sınıfları içe aktararak başlayın.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Bu içe aktarmalar, **imza seçenekleri oluşturmak** için kullanılan API'ye ve gerçek imzalama işlemini gerçekleştirmeye erişim sağlar.

## Adım 2: İmza seçeneklerini oluşturun

`SignatureOptions` nesnesi, imzalama süreci için gerekli tüm yapılandırmayı tutar; örneğin imza seviyesi, görsel görünüm ve zaman damgası ayarları.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Yeni bir `SignatureOptions` örneği oluşturmak, **docx nasıl imzalanır** dosyaları için ilk adımdır çünkü her imzalama isteğini izole eder, belge çapraz etkilerini önler.

## Adım 3: XAdES EPES imza seviyesini belirtin

XAdES‑EPES (Explicit Policy-based Electronic Signature), Office belge imzaları için yaygın olarak kabul edilen bir politikadır. Seviyeyi ayarlamak, kütüphaneye hangi kriptografik profilin kullanılacağını söyler.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Neden XAdES‑EPES? İmza politikasını doğrudan imzaya gömer, böylece imzalanan belge kendi içinde bütünleşik olur ve birçok e‑imza düzenlemesine uygun hâle gelir.

## Adım 4: DOCX dosyasını imzalayın

Şimdi `DigitalSignatureUtil.sign` metodunu çağırın. Bu metod kaynak dosyayı okur, imzayı uygular ve imzalı çıktıyı yazar.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**Arka planda ne olur?**  
1. Kütüphane `.pfx` dosyasını yükler ve verilen şifreyle özel anahtarı çıkarır.  
2. XAdES‑EPES profiline uygun bir XML‑DSig yapısı oluşturur.  
3. İmza, orijinal belge düzenini koruyarak DOCX paketine gömülür.  

Sertifika şifresi yanlışsa veya dosya okunamazsa, bir `IOException` fırlatılır; bu da gösterildiği gibi ele alınmalıdır.

## Adım 5: İmzalı belgeyi doğrulayın (isteğe bağlı)

İmzalama sonrası, imzanın mevcut ve geçerli olduğunu doğrulamak isteyebilirsiniz. GroupDocs bir doğrulama API'si sağlar, ancak hızlı bir manuel kontrol Microsoft Word ile yapılabilir:

1. `SignedXades.docx` dosyasını Word'de açın.  
2. **File → Info → View signatures** üzerine tıklayın.  
3. Word, geçerli bir dijital imzayı gösteren yeşil bir işaret (checkmark) göstermelidir.

Kütüphane ile otomatik doğrulama şu şekilde görünür:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Doğrulama adımını çalıştırmak, **sign office document** işleminin başarılı olduğuna programatik bir güven sağlar.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek, kopyalayıp yapıştırıp çalıştırabileceğiniz bağımsız bir Java sınıfı aşağıdadır.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Beklenen çıktı**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Bir şeyler ters giderse, konsol net bir hata mesajı gösterir ve sertifika ya da dosya yolu sorunlarını çözmenize yardımcı olur.

## Yaygın sorular ve uç‑durum yönetimi

| Soru | Cevap |
|----------|--------|
| **Farklı bir imza seviyesi kullanabilir miyim?** | Evet. Uyumluluk ihtiyaçlarına göre `XmlDsigLevel.XAdES_EPES` yerine `XAdES_BES`, `XAdES_T` vb. kullanın. |
| **Sertifikam .pfx dosyası yerine bir keystore'da depolanmışsa ne olur?** | `KeyStore`'u manuel olarak yükleyin, `PrivateKey` ve `Certificate`'ı çıkarın, ardından `sign` metodunun `KeyStore` nesnesi kabul eden aşırı yüklemesine geçirin. |
| **Görünür bir imza resmi nasıl eklenir?** | `sign` çağırmadan önce `signatureOptions.setSignatureImage("path/to/image.png")` kullanın. |
| **İmzalama işlemi thread‑safe mi?** | `DigitalSignatureUtil.sign` metodu durum içermez; her iş parçacığı kendi `SignatureOptions` örneğini kullandığı sürece güvenle birden çok iş parçacığından çağırabilirsiniz. |
| **DOCX mevcut imzalar içeriyorsa ne olur?** | Kütüphane yeni bir imza paketi girdisi ekler, önceki imzaları korur. Gerekirse imza politikasının birden çok imzaya izin verip vermediğini doğrulayın. |

## İpuçları ve en iyi uygulamalar (E‑E‑A‑T)

* **Pro tip:** Sertifika şifrenizi sabit kodlamak yerine güvenli bir kasada (ör. Azure Key Vault) saklayın.  
* **Watch out for:** Windows (`\`) ve Unix (`/`) dosya yolu ayırıcılarına dikkat edin. Platform bağımsız yollar oluşturmak için `Paths.get(...)` kullanın.  
* **Performance:** Büyük DOCX dosyalarını imzalamak I/O‑ağırlıklı olabilir; toplu işlem yapıyorsanız giriş dosyasını akış (stream) olarak ele almayı düşünün.  
* **Compliance:** XAdES‑EPES, AB eIDAS düzenlemesiyle uyumludur; bir imza seviyesi seçmeden önce yerel yasal gereksinimlerinizi doğrulayın.

## Sonuç

Bu öğreticide Java kullanarak XAdES‑EPES seviyesiyle **imza seçenekleri oluşturmayı** ve **Word belgesini imzalamayı** öğrendiniz. Tam örnek, sertifika yükleme, seçenek yapılandırması, imzalama çağrısı ve isteğe bağlı doğrulamayı kapsar; üretimde **docx nasıl imzalanır** dosyaları için hazır bir çözüm sunar.

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Java'da Yükleme Seçenekleri Oluşturma – Eksik Yazı Tiplerini Algıla ve DOCX Nasıl Yüklenir](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Aspose.Words for Java'da Belge Seçenekleri ve Ayarlarını Kullanma](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Aspose.Words for Java Kullanarak Salt Okunur Belgelerde Düzenlenebilir Aralıklar Nasıl Oluşturulur](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}