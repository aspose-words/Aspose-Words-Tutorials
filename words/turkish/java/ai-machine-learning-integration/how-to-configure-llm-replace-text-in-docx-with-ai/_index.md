---
category: general
date: 2026-03-04
description: LLM'yi Document AI için nasıl yapılandırılır ve AI kullanarak DOCX'te
  metni nasıl değiştiririz – tam Java kodlu adım adım rehber.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: tr
og_description: LLM'yi Document AI için nasıl yapılandırır ve AI kullanarak DOCX'teki
  metni nasıl değiştirirsiniz – çalıştırılabilir Java kodlu tam rehber.
og_title: LLM Nasıl Yapılandırılır – DOCX'te Metni AI ile Değiştir
tags:
- LLM
- Document AI
- Java
- DOCX
title: LLM Nasıl Yapılandırılır – DOCX'teki Metni AI ile Değiştir
url: /tr/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# LLM'yi Nasıl Yapılandırılır – DOCX'te Metni AI ile Değiştir

Hiç **LLM'yi nasıl yapılandıracağınızı** merak ettiniz mi, böylece sizin için bir Word dosyasını düzenleyebilsin? Tek başınıza değilsiniz. Birçok geliştirici, Microsoft Word'ü açmadan programlı bir şekilde bir `.docx` içinde bir ifadeyi değiştirmesi gerektiğinde bir duvara çarpar. İyi haber? Yerel bir LLM ve küçük bir Document AI sarmalayıcı ile, sadece birkaç Java satırıyla bir DOCX dosyasındaki metni değiştirebilirsiniz.

Bu öğreticide tüm süreci adım adım göstereceğiz: LLM bağlantısını kurmaktan, bir DOCX yüklemeye, **Document AI** kullanarak hedef bir ifadeyi değiştirmeye kadar. Sonunda, herhangi bir Maven ya da Gradle projesine ekleyebileceğiniz, bağımsız ve çalıştırılabilir bir örnek elde edeceksiniz. Harici API anahtarları yok, bulut ücretleri yok—sadece `http://localhost:8080/v1` adresinde dinleyen kendi modeliniz.

> **Hızlı kazanç:** Eğer zaten bir yerel LLM'niz (Llama 3 veya Mistral gibi) OpenAI‑uyumlu bir uç nokta sunuyorsa, aşağıdaki kod doğrudan çalışır.

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="llm yapılandırma diyagramı"}

## İhtiyacınız Olanlar

- **Java 17** (veya herhangi bir yeni JDK)  
- Bir **local LLM** OpenAI‑stilinde `/v1` uç noktası sunar (örn., Ollama, LMStudio)  
- **Document AI Java kütüphanesi** (Maven Central'da `com.example:document-ai:1.2.0` olduğunu varsayın)  
- Bilinen bir klasöre yerleştirilmiş örnek bir DOCX dosyası (`input.docx`)  

Eğer bunlardan herhangi birine sahip değilseniz, Ollama'yı hızlıca başlatın:

```bash
ollama serve &
ollama run llama3
```

Bu, `http://localhost:8080/v1` adresinde istekleri kabul etmeye hazır bir sunucu başlatacaktır.

---

## Document AI için LLM Nasıl Yapılandırılır

İlk yaptığımız şey, `DocumentAi` istemcisine modeli nerede bulacağını ve hangi modeli kullanacağını söylemektir. Bu, birçok öğreticinin üzerinden geçtiği **LLM'yi nasıl yapılandıracağınız** adımıdır.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Neden önemli:*  
`AiModelConfig` nesnesi HTTP detaylarını soyutlayarak `DocumentAi`'nin içeriğe odaklanmasını sağlar. Eğer bir bulut sağlayıcıya geçerseniz, sadece `baseUrl` ve `apiKey`'i değiştirirsiniz—kodunuzun geri kalanı dokunulmaz kalır.

## DOCX Belgesini Yükleyin ve Hazırlayın

Sonra Word dosyasını belleğe alıyoruz. `Document` sınıfı altında hem `.docx` hem de `.pdf` dosyalarını işler, ancak burada sadece DOCX ile ilgileniyoruz.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*İpucu:* Hata ayıklama sırasında “dosya bulunamadı” sürprizinden kaçınmak için mutlak bir yol kullanın. Güvendiğinizde, taşınabilirlik için göreli yola geri dönün.

## AI Kullanarak DOCX'te Metni Değiştir

Şimdi öğreticinin kalbi geliyor—AI yardımıyla bir DOCX dosyasında **metni nasıl değiştireceğiniz**. `replaceText` yöntemi belge içeriğini LLM'ye gönderir, değişikliği yapmasını ister ve revize edilmiş metni döndürür.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Arka planda ne oluyor?*  
`DocumentAi` DOCX'i düz metne seri hale getirir, şu şekilde bir istem oluşturur:

> “Aşağıdaki belgede, ‘eski ifade’nin her geçtiğini ‘yeni ifade’ ile değiştirin ve yalnızca güncellenmiş metni döndürün.”

LLM isteği işler ve değiştirilmiş içeriği geri gönderir. Bu yaklaşım, ifadenin birden fazla satır veya paragraf boyunca uzandığı durumlarda bile çalışır—düz dize değiştirme genellikle kaçırır.

## Revize Edilen Metni Doğrulayın ve Çıktılayın

Son olarak AI‑revize edilmiş metni konsola yazdırıyoruz. Gerçek bir uygulamada muhtemelen sonucu yeni bir DOCX'e geri yazarsınız, ancak yazdırmak hızlıca doğrulamanızı sağlar.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Beklenen çıktı** (orijinal DOCX'in “This is the old phrase we want to change.” içerdiğini varsayarsak):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Yeni ifadenin göründüğünü görürseniz, tebrikler—**AI ile bir ifadeyi değiştirmek için Document AI'yi nasıl kullanacağınızı yeni öğrendiniz**.

## Tam Çalışan Örnek

Her şeyi bir araya getirerek, işte eksiksiz, çalıştırmaya hazır bir Java sınıfı. `src/main/java/com/example/ReplaceInDocx.java` içine kopyalayıp yapıştırabilirsiniz.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Nasıl Çalıştırılır

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Programı çalıştırmadan önce LLM sunucusunun açık olduğundan emin olun; aksi takdirde bağlantı zaman aşımına uğrayacaksınız.

## Kenar Durumları ve Yaygın Tuzaklar

| Durum | Dikkat Edilmesi Gereken | Önerilen Çözüm |
|-----------|-------------------|---------------|
| **İfade bulunamadı** | LLM, orijinal metni değişmeden döndürür. | Yazım ve büyük/küçük harf duyarlılığını tekrar kontrol edin; sarmalayıcınız destekliyorsa isteme `ignoreCase:true` ekleyebilirsiniz. |
| **Büyük belgeler (>5 MB)** | İstem boyutu modelin token limitini aşabilir. | DOCX'i bölümlere ayırın, her birini ayrı ayrı işleyin, ardından sonuçları birleştirin. |
| **Yerel LLM hatalar döndürür** | Genellikle eşleşmeyen model adı nedeniyle oluşur. | `ollama list` komutuyla LLM arayüzündeki model adının `modelConfig.setModelName` ile eşleştiğini doğrulayın. |
| **Unicode karakterler bozulur** | DOCX okunurken kodlama sorunları. | Java çalışma zamanınızın UTF‑8 kullandığından emin olun (JVM argümanlarına `-Dfile.encoding=UTF-8` ekleyin). |

## Sonraki Adımlar

Artık **DOCX'te metni AI ile nasıl değiştireceğinizi** bildiğinize göre, şunları keşfetmek isteyebilirsiniz:

- **Document AI'yi nasıl kullanacağınız** tablo çıkarma veya stil koruma gibi daha karmaşık görevler için.  
- **AI ile ifadeyi değiştir** PDF'lerde `Document` yapıcı argümanını değiştirerek.  
- **Toplu işleme**: bir DOCX dosyaları dizini üzerinde döngü kurup aynı değişikliği uygulayın.  

Bunların her biri aynı `AiModelConfig` ve `DocumentAi` temeli üzerine inşa edildiği için sıfırdan başlamak zorunda kalmayacaksınız.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}