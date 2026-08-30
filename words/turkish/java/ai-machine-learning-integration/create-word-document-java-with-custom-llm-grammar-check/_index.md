---
category: general
date: 2026-05-04
description: Aspose.Words kullanarak Java ile Word belgesi oluşturun ve özel bir LLM
  ile dilbilgisini nasıl kontrol edeceğinizi öğrenin. Java geliştiricileri için adım
  adım rehber.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: tr
og_description: Java ile Word belgesi oluşturun ve özel bir LLM kullanarak dilbilgisini
  nasıl kontrol edeceğinizi görün. Çalıştırılabilir kod içeren eksiksiz Java öğreticisi.
og_title: Java ile Özel LLM Dilbilgisi Kontrolü Kullanarak Word Belgesi Oluştur
tags:
- Java
- Aspose.Words
- LLM
title: Java ile Özel LLM Dilbilgisi Kontrolü Kullanarak Word Belgesi Oluştur
url: /tr/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java ile Word belgesi oluşturma ve Özel LLM Dilbilgisi Kontrolü

Kendini otomatik olarak düzeltme yeteneğine sahip **create word document java** projelerini hiç merak ettiniz mi? Yalnız değilsiniz—birçok geliştirici, birden fazla aracı yönetmeden şık bir *.docx* dosyası üreten tek bir akış istiyor. Bu öğreticide tam olarak bunu adım adım göstereceğiz; Aspose.Words ile **how to create docx** dosyalarını nasıl oluşturacağınızı, yerel bir LLM'yi nasıl bağlayacağınızı ve sonunda **how to check grammar** adımını otomatik olarak nasıl yapacağınızı göstereceğiz. Sonunda, bir Word belgesi yazan, doğrulayan ve kaydeden, **using custom LLM** uç noktalarını kontrol ettiğiniz bağımsız bir Java programına sahip olacaksınız.

## İhtiyacınız Olanlar

İlerlemeye başlamadan önce, çalışma istasyonunuzda aşağıdakilerin olduğundan emin olun:

| Ön Koşul | Neden Önemli |
|--------------|----------------|
| Java 17+ (veya herhangi bir yeni JDK) | Modern dil özellikleri ve daha iyi modül desteği |
| Aspose.Words for Java (latest version) | Programatik olarak **create word document java** dosyaları oluşturmanıza olanak tanıyan kütüphane |
| Yerel olarak barındırılan bir LLM sunucusu (ör. Ollama, LMStudio) `http://localhost:11434/api/generate` adresinde dinliyor | **use custom llm** adımı için gereklidir ve dilbilgisi kontrolünü sağlar |
| Maven veya Gradle (örneklerde Maven kullanacağız) | Bağımlılık yönetimini basitleştirir |
| Bir IDE veya metin düzenleyici (IntelliJ IDEA, VS Code, vb.) | Kodlamayı ve hata ayıklamayı kolaylaştırır |

Eğer bunlardan herhangi biri size yabancı geliyorsa, panik yapmayın—her bir öğe ücretsizdir ya da öğrenme amaçları için mükemmel çalışan bir topluluk sürümüne sahiptir.

## Adım 1 – Maven Projenizi Kurun

**create word document java** projelerini hızlıca oluşturmak için, minimal bir Maven `pom.xml` ile başlayın. Bu dosya Aspose.Words kütüphanesini ve tercih ettiğiniz herhangi bir HTTP istemcisini (Apache HttpClient kullanacağız) çeker.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Eğer Gradle kullanıyorsanız, aynı bağımlılıklar `build.gradle` içinde `implementation` altında yer alır.

Şimdi `mvn clean install` komutunu çalıştırarak jar dosyalarını indirin. Derleme başarılı olduğunda, **creates word document java** dosyaları yazmaya hazır olacaksınız.

## Adım 2 – **Creates word document java** yapan Java Sınıfını Yazın

Aşağıda tam, çalıştırmaya hazır kaynak dosya yer alıyor. Tüm akışı gösterir: boş bir belge başlatma, özel bir LLM uç noktasını yapılandırma, dilbilgisi kontrolünü çağırma ve sonunda sonucu kaydetme.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Neden bu çalışıyor:**  
> * `Document`, bellekte bir *.docx* temsil eden temel Aspose.Words sınıfıdır.  
> * `AiEndpoint`, Aspose’un AI modülüne istemciyi nereye göndereceğini söyler. `localhost:11434` adresine yönlendirerek bir bulut hizmeti yerine **use custom llm** kullanıyoruz.  
> * `checkGrammar`, `AiModelType.CUSTOM` ile belgenin metnini LLM'ye gönderir, düzeltilmiş metni alır ve temel Word düğümlerini yeniden yazar.  
> * Son olarak `save` çağrısı dosyayı diske yazar ve size şık bir Word dosyası verir.

### Beklenen Çıktı

`mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` komutunu çalıştırdıktan sonra şu çıktıyı görmelisiniz:

```
Document saved to output/GrammarChecked.docx
```

Oluşan `GrammarChecked.docx` dosyasını Microsoft Word (veya LibreOffice) ile açın. Orijinal cümle *“Ths sentence has a typo and a grammer error.”* artık *“This sentence has a typo and a grammar error.”* olarak görünecek – **how to check grammar** adımının başarılı olduğunun kanıtı.

## Adım 3 – Farklı İçerikle docx Nasıl Oluşturulur (Opsiyonel)

Daha zengin belgeler—tablolar, görseller veya biçimlendirilmiş metin—oluşturmak istiyorsanız, `DocumentBuilder` kullanmaya devam edin. İşte bir başlık ve tablo eklemeyi gösteren hızlı bir kod parçacığı:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Bu kodu belge‑oluşturma bloğu (Adım 2.1) ile dilbilgisi‑kontrol çağrısı (Adım 2.3) arasında istediğiniz yere ekleyebilirsiniz. LLM hâlâ tam metni alacak, böylece tabloları dokunmadan doğal dil bölümlerini düzeltebilecek.

## Adım 4 – Uç Nokta Sorunlarıyla Baş Etme (Özel LLM'yi Güvenli Kullanma)

**using custom llm** uç noktalarını kullanırken, birkaç sıkıntı yaygındır:

| Semptom | Muhtemel neden | Çözüm |
|---------|--------------|-----|
| `Connection refused` hatası | LLM sunucusu çalışmıyor veya yanlış port | Ollama'yı başlatın (`ollama serve`) ve `http://localhost:11434/api/generate` adresinin `curl` ile çalıştığını doğrulayın. |
| Yanıt JSON'inde `completion` alanı eksik | Model adı uyuşmazlığı | Ayarladığınız modelin (`llama3.1:8b`) kurulu olduğundan emin olun (`ollama list`). |
| Dilbilgisi kontrolü orijinal metni değiştirmeden döndürüyor | İstemci LLM tarafından tanınmıyor | Modelin sistem ayarını değiştirin. |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}