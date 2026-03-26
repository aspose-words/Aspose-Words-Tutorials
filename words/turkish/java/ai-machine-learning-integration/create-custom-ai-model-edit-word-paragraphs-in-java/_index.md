---
category: general
date: 2026-03-25
description: Word belgelerini düzenlemek için özel bir AI modeli oluşturun – metni
  daha resmi hâle getirmeyi, paragraf metnini değiştirmeyi ve Aspose.Words AI kullanarak
  bir Word paragrafını yeniden yazmayı öğrenin.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: tr
og_description: Word belgelerini düzenlemek için özel bir AI modeli oluşturun. Metni
  daha resmi hâle getirmeyi, paragraf metnini değiştirmeyi ve Aspose.Words AI kullanarak
  bir Word paragrafını yeniden yazmayı öğrenin.
og_title: Özel AI Modeli Oluştur – Java'da Word Paragraflarını Düzenle
tags:
- Aspose.Words
- Java
- AI integration
title: Özel AI Modeli Oluştur – Java'da Word Paragraflarını Düzenle
url: /tr/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Özel AI Modeli Oluştur – Java’da Word Paragraflarını Düzenle

Hiç **create custom AI model** oluşturmanız gerektiğini düşündünüz mü? Belki bir dizi sözleşmeniz var ve hepsi biraz fazla samimi geliyor, tek bir kod satırıyla metni daha resmi hâle getirmek istiyorsunuz. İyi haber şu ki, bunu tam da yapabilirsiniz—harici hizmetler, ağır SDK'lar yok, sadece Aspose.Words for Java ve OpenAI‑compatible bir uç nokta.

Bu öğreticide, **create custom AI model** oluşturmak için gereken tüm adımları, yerel bir LLM sunucusuna bağlamayı ve ardından *replace paragraph text* işlemini daha resmi bir versiyonla gerçekleştirmeyi adım adım göstereceğiz. Sonunda, **edit paragraph with AI** yapan, bir Word paragrafını yeniden yazan ve sonucu diske kaydeden çalıştırılabilir bir Java programına sahip olacaksınız. Gereksiz ayrıntı yok, sadece kendi projenize kopyalayıp‑yapıştırabileceğiniz pratik bir çözüm.

> **İhtiyacınız olanlar**  
> • Java 17 veya daha yeni (kod daha eski sürümlerle de derlenebilir, ancak 17 en uygun sürüm)  
> • Aspose.Words for Java 23.9 (veya en son sürüm)  
> • Çalışan bir OpenAI‑compatible LLM sunucusu (ör. Ollama, LocalAI) `http://localhost:8000/v1` adresinde dinleniyor  
> • Kontrol ettiğiniz bir klasörde bulunan bir giriş Word belgesi (`input.docx`)

OpenAI'yi doğrudan çağırmak yerine *why bother building a custom model* düşündüğünüzde, cevap esnekliktir: uç noktayı kontrol edersiniz, kod değişikliği yapmadan modelleri değiştirebilirsiniz ve API anahtarlarını kaynak deponuzdan uzak tutarsınız. Hadi başlayalım.

---

## Özel AI Modeli Oluştur – Kurulum ve Yapılandırma

İlk olarak Aspose.Words'a LLM'imizin nerede olduğunu söylememiz gerekiyor. `AiModelEndpoint` sınıfı URL'yi ve isteğe bağlı API anahtarını tutar. Yerel bir sunucu kullandığımız için anahtar boş bir dize olabilir, ancak parametre zorunludur.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Eğer bir hosted modele (ör. Azure OpenAI) geçerseniz, sadece URL ve anahtarı değiştirin—başka bir kod değişikliğine gerek yok.

---

## Word Belgesini Yükle

Şimdi kaynak dosyayı belleğe alıyoruz. `Document` `.docx`, `.doc`, `.rtf` ve birçok diğer formatı okuyabilir, ancak bu örnek için `.docx` ile devam ediyoruz.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

`YOUR_DIRECTORY`'nin gerçek bir klasöre işaret ettiğinden emin olun; aksi takdirde bir `FileNotFoundException` alırsınız. Gerçek bir uygulamada yolu komut satırı argümanı olarak geçirebilir veya bir yapılandırma dosyasından okuyabilirsiniz.

---

## Özel AI Modelini Başlat

Önceden tanımladığımız uç noktayı kullanarak `CUSTOM` tipinde bir `AiModel` oluşturuyoruz. Bu, Aspose.Words'a tüm AI çağrılarını kendi sunucumuz üzerinden yönlendirmesini söyler.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Arka planda Aspose.Words, LLM ile standart OpenAI sohbet/tamamlayıcı şemasını kullanarak iletişim kuran küçük bir HTTP istemcisi oluşturur. Bu yüzden uç nokta *OpenAI‑compatible* olmalıdır.

---

## İlk Paragrafı Al ve Yeniden Yaz

İşte metni gerçekten **make text more formal** yaptığımız yer. İlk paragrafı alıyoruz, ham metnini bir istemle modele gönderiyoruz ve düzenlenmiş sürümü alıyoruz.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

İkinci argüman (`"Make it more formal"`) modele verdiğimiz talimattır. Bunu herhangi bir yönergeyle değiştirebilirsiniz—**replace paragraph text**, **summarize**, **translate**, vb. Metot düz bir string döndürür, bunu daha sonra belgeye geri ekleyeceğiz.

> **Why this works:** `editText` `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }` gibi bir JSON yükü gönderir. LLM orijinal paragrafı ve talimatı görür, ardından revize edilmiş metinle yanıt verir.

---

## Orijinal Paragraf İçeriğini Değiştir

Şimdi Word nesne modelinde **replace paragraph text** yapıyoruz. Mevcut tüm run'ları (metnin düşük seviyeli parçaları) temizliyoruz ve AI‑generated string içeren yeni bir `Run` ekliyoruz.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

`firstParagraph.setText()` çağırmamaya dikkat edin—bu metot tüm biçimlendirmeyi kaldırır. `Run` kullanmak, paragrafın stilini (başlık, madde işareti vb.) korurken gerçek karakterleri değiştirir.

---

## Düzenlenmiş Belgeyi Kaydet

Son olarak, değiştirilmiş belgeyi diske geri yazıyoruz. Orijinal dosyanın üzerine yazabilir ya da burada yaptığımız gibi yeni bir kopya oluşturabilirsiniz.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

`output.docx` dosyasını açtığınızda, ilk paragrafın artık oldukça daha resmi bir şekilde duyulduğunu görmelisiniz. LLM talimatı tam olarak takip etmediyse, istemi ayarlayabilir veya farklı bir model sürümü deneyebilirsiniz.

---

## Tam Çalışan Örnek

Aşağıda tam program yer alıyor—`LlmDemo.java` dosyasına kopyalayın, yolları ayarlayın ve `javac` + `java` ile çalıştırın.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** `output.docx` dosyasını açın ve orijinal paragrafın dönüştüğünü göreceksiniz. Örneğin, “We’ll get the thing done soon.” gibi samimi bir cümle “We shall complete the task promptly.” şeklinde olabilir. Tam ifadeler kullandığınız modele bağlıdır.

---

## Yaygın Sorular ve Kenar Durumları

### Belgem birden fazla bölüm içeriyorsa ne olur?

Yukarıdaki kod sadece *first* bölümün *first* paragrafına dokunur. Tüm dosyada **edit paragraph with AI** yapmak için `document.getSections()` üzerinden döngü kurup ardından her `section.getBody().getParagraphs()` üzerinden geçin. Boş paragrafları atlamayı unutmayın, aksi takdirde LLM boş bir string alır ve hiçbir şey döndürmez.

### Token limitlerini aşan büyük paragrafları nasıl yönetirim?

Çoğu LLM girişini yaklaşık 4 000 token ile sınırlar. Bir paragraf olağanüstü uzun ise, `editText` çağırmadan önce daha küçük parçalara bölün. Aynı `AiModel` örneğini yeniden kullanabilirsiniz; sadece yerel sunucunuzdaki oran limitlerine dikkat edin.

### “summarize” veya “translate to French” gibi farklı bir talimat kullanabilir miyim?

Kesinlikle. `editText`'in ikinci argümanı serbest biçimlidir. Özet için `"Summarize in one sentence"` geçirebilirsiniz. Çeviri için `"Translate to French, keep the tone formal"` aynı şekilde çalışır. Bu esneklik, kodda değişiklik yapmadan birçok senaryo için **replace paragraph text** yapmanıza olanak tanır.

### Model paragraf stilini (fontlar, renkler) korur mu?

Aynı `Paragraph` nesnesi içinde sadece `Run`'ı değiştirdiğimiz için mevcut stiller (başlık seviyesi, madde listesi, girinti) aynı kalır. Stili kendisini değiştirmeniz gerekiyorsa, değişimden sonra `Paragraph.getParagraphFormat()` ile manipüle edebilirsiniz.

### LLM sunucum HTTPS ve kendinden imzalı sertifika gerektiriyorsa ne olur?

`AiModelEndpoint` `https://` ile başlayan bir URL kabul eder. Sertifika güvenilir değilse, Java’nın SSL bağlamını güvene alacak şekilde yapılandırmanız veya sunucuyu geçerli bir sertifika ile çalıştırmanız gerekir. Bu kurulum bu öğreticinin kapsamı dışında olup Java SSL rehberlerinde iyi belgelenmiştir.

---

## Üretim‑Hazır Entegrasyon İçin İpuçları

| Tip | Neden önemli |
|-----|----------------|
| **Cache the endpoint** | Her istekte `AiModelEndpoint` yeniden oluşturmak ek yük getirir. |
| **Batch edits** | Çok sayıda paragrafınız varsa, gecikmeyi azaltmak için tek bir istek (ör. JSON dizisi) içinde gönderin. |
| **Validate LLM output** | Eklemeye başlamadan önce dönen stringi null veya boş değerler için her zaman kontrol edin. |
| **Log prompts and responses** | Hata ayıklama ve yasal metinleri yeniden yazarken uyumluluk için faydalıdır. |
| **Graceful fallback** | LLM hizmeti kapalıysa, orijinal paragrafı ya da basit bir kural tabanlı yeniden yazmayı kullanın. |

---

## Sonuç

Aspose.Words ile **create custom AI model** oluşturmayı, onu OpenAI‑compatible bir uç noktaya bağlamayı ve ardından **edit paragraph with AI** kullanarak **make text more formal** yapmayı gösterdik. Altı adımı izleyerek—uç noktayı tanımlayın, belgeyi yükleyin, modeli başlatın,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}