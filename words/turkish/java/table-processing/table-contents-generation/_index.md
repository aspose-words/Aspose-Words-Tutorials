---
"description": "Java için Aspose.Words kullanarak dinamik İçindekiler Tablosu oluşturmayı öğrenin. Adım adım rehberlik ve kaynak kodu örnekleriyle İçindekiler Tablosu oluşturma konusunda uzmanlaşın."
"linktitle": "İçindekiler Üretimi"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "İçindekiler Üretimi"
"url": "/tr/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# İçindekiler Üretimi

## giriiş

Word belgelerinizde dinamik ve profesyonel görünümlü bir İçindekiler Tablosu (TOC) oluşturmakta hiç zorluk çektiniz mi? Başka yere bakmayın! Aspose.Words for Java ile tüm süreci otomatikleştirebilir, zamandan tasarruf edebilir ve doğruluğu garantileyebilirsiniz. Kapsamlı bir rapor veya akademik bir makale oluşturuyor olun, bu eğitim size Java ile programatik olarak bir TOC oluşturma konusunda yol gösterecektir. Başlamaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Kodlamaya başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Java Geliştirme Kiti (JDK): Sisteminize kuruludur. Buradan indirebilirsiniz [Oracle'ın web sitesi](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java Kütüphanesi: En son sürümü şu adresten indirin: [yayın sayfası](https://releases.aspose.com/words/java/).
3. Entegre Geliştirme Ortamı (IDE): IntelliJ IDEA, Eclipse veya NetBeans gibi.
4. Geçici Lisans Alın: Değerlendirme sınırlamalarından kaçınmak için, [geçici lisans](https://purchase.aspose.com/temporary-license/).

## Paketleri İçe Aktar

Aspose.Words for Java'yı etkili bir şekilde kullanmak için, gerekli sınıfları içe aktardığınızdan emin olun. İşte içe aktarımlar:

```java
import com.aspose.words.*;
```

Word belgenizde dinamik İçindekiler tablosu oluşturmak için şu adımları izleyin.

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

İlk adım yeni bir belge oluşturmak ve kullanmaktır `DocumentBuilder` onu manipüle etmek için sınıf.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Word belgesini temsil eder.
- `DocumentBuilder`: Belgenin kolayca düzenlenmesini sağlayan yardımcı sınıf.

## Adım 2: İçindekiler Tablosunu Ekleyin

Şimdi İçindekiler bölümünü belgenin başına ekleyelim.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: İçindekiler alanı ekler. Parametreler şunları belirtir:
  - `\o "1-3"`: 1. seviyeden 3. seviyeye kadar olan başlıkları ekleyin.
  - `\h`: Girişlere köprü metni ekleyin.
  - `\z`: Web belgelerinde sayfa numaralarını gizle.
  - `\u`: Köprü metinlerinin stillerini koru.
- `insertBreak`: İçindekiler bölümünden sonra sayfa sonu ekler.

## Adım 3: İçindekiler Tablosunu Doldurmak İçin Başlıklar Ekleyin

İçindekiler tablosunu doldurmak için başlık stilleri içeren paragraflar eklemeniz gerekir.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: Paragraf stilini belirli bir başlık düzeyine ayarlar (örneğin, `HEADING_1`, `HEADING_2`).
- `writeln`:Belgeye belirtilen stilde metin ekler.

## Adım 4: İç İçe Başlıklar Ekleyin

İçindekiler düzeylerini göstermek için iç içe başlıklar ekleyin.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- İçindekiler tablosunda hiyerarşiyi göstermek için daha derin düzeylerde başlıklar ekleyin.

## Adım 5: İçindekiler Alanlarını Güncelleyin

En son başlıkların görüntülenebilmesi için İçindekiler alanının güncellenmesi gerekmektedir.


```java
doc.updateFields();
```

- `updateFields`: Belgedeki tüm alanları yeniler ve İçindekiler tablosunun eklenen başlıkları yansıtmasını sağlar.

## Adım 6: Belgeyi Kaydedin

Son olarak belgeyi istediğiniz formatta kaydedin.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: Belgeyi bir `.docx` dosya. Diğer biçimleri de belirtebilirsiniz. `.pdf` veya `.txt` eğer gerekirse.

## Çözüm

Tebrikler! Aspose.Words for Java kullanarak bir Word belgesinde dinamik bir İçindekiler Tablosu oluşturmayı başardınız. Sadece birkaç satır kodla, aksi takdirde saatler sürebilecek bir görevi otomatikleştirdiniz. Peki, sırada ne var? İçindekiler Tablonuzu belirli ihtiyaçlara göre uyarlamak için farklı başlık stilleri ve biçimleri denemeyi deneyin.

## SSS

### İçindekiler formatını daha fazla özelleştirebilir miyim?
Kesinlikle! Sayfa numaraları ekleme, metni hizalama veya özel başlık stilleri kullanma gibi İçindekiler parametrelerini ayarlayabilirsiniz.

### Aspose.Words for Java için lisans zorunlu mudur?
Evet, tam işlevsellik için bir lisans gereklidir. Bir lisansla başlayabilirsiniz [geçici lisans](https://purchase.aspose.com/temporary-license/).

### Mevcut bir belge için İçindekiler tablosu oluşturabilir miyim?
Evet! Belgeyi bir `Document` nesneyi seçin ve İçindekiler tablosunu eklemek ve güncellemek için aynı adımları izleyin.

### Bu PDF çıktıları için de işe yarıyor mu?
Evet, belgeyi PDF'e kaydederseniz İçindekiler tablosu PDF'te görünecektir. `.pdf` Biçim.

### Daha fazla dokümanı nerede bulabilirim?
Şuna bir göz atın: [Java için Aspose.Words belgeleri](https://reference.aspose.com/words/java/) Daha fazla örnek ve ayrıntı için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}