---
"date": "2025-03-28"
"description": "Aspose.Words Java için bir kod eğitimi"
"title": "Aspose.Words Geri Aramaları ile Java'da Özel Sayfa ve Resim Kaydetme"
"url": "/tr/java/images-shapes/aspose-words-java-callback-custom-savings/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Java'da Aspose.Words Geri Aramalarıyla Özel Sayfa ve Resim Kaydetme Nasıl Uygulanır

## giriiş

Günümüzün dijital ortamında, belgeleri HTML gibi çok yönlü biçimlere dönüştürmek, platformlar arasında sorunsuz içerik dağıtımı için olmazsa olmazdır. Ancak, çıktıyı yönetmek (örneğin, dönüştürme sırasında sayfalar veya resimler için dosya adlarını özelleştirmek) zorlayıcı olabilir. Bu eğitim, sayfa ve resim kaydetme süreçlerini etkili bir şekilde özelleştirmek için geri aramaları kullanarak bu sorunu çözmek için Java için Aspose.Words'ü kullanır.

### Ne Öğreneceksiniz
- Aspose.Words ile Java'da Sayfa Kaydetme Geri Çağrısının Uygulanması.
- Belgeleri özel parçalara bölmek için Belge Parçaları Kaydetme Geri Çağrılarını kullanma.
- HTML dönüştürme sırasında resimler için dosya adlarının özelleştirilmesi.
- Belge dönüştürme sırasında CSS stil sayfalarını yönetme.

Dalmaya hazır mısınız? Ortamınızı ayarlayarak ve Aspose.Words geri aramalarının güçlü yeteneklerini keşfederek başlayalım.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

### Gerekli Kütüphaneler
- **Java için Aspose.Words**: Word belgeleriyle çalışmak için sağlam bir kütüphane. 25.3 veya sonraki bir sürüme ihtiyacınız var.
  
### Çevre Kurulum Gereksinimleri
- Bilgisayarınıza Java Development Kit (JDK) kurulu.
- IntelliJ IDEA veya Eclipse gibi bir IDE.

### Bilgi Önkoşulları
- Java programlama ve dosya G/Ç işlemlerinin temel düzeyde anlaşılması.
- Bağımlılık yönetimi için Maven veya Gradle'a aşinalık.

## Aspose.Words'ü Kurma

Aspose.Words'ü kullanmaya başlamak için onu projenize dahil etmeniz gerekir. İşte nasıl:

### Maven Bağımlılığı
Aşağıdakileri ekleyin: `pom.xml`:
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle Bağımlılığı
Bunu da ekleyin `build.gradle` dosya:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Lisans Edinme Adımları

Tüm özelliklerin kilidini açmak için bir lisansa ihtiyacınız var. İşte adımlar:
1. **Ücretsiz Deneme**: Tüm işlevleri keşfetmek için geçici bir lisansla başlayın.
2. **Lisans Satın Al**Uzun süreli kullanım için ticari lisans satın almayı düşünebilirsiniz.

### Temel Başlatma ve Kurulum
```java
License license = new License();
license.setLicense("path/to/your/license/file");
```

## Uygulama Kılavuzu

Uygulamayı Aspose.Words geri aramalarını kullanarak temel özelliklere bölelim.

### Özellik 1: Sayfa Kaydetme Geri Araması

Bu özellik, bir belgenin her sayfasının özel dosya adlarına sahip ayrı HTML dosyalarına kaydedilmesini gösterir.

#### Genel bakış
Her bir sayfa için çıktı dosyalarının özelleştirilmesi, düzenli depolama ve kolay erişim sağlar.

#### Uygulama Adımları

##### Adım 1: Uygula `IPageSavingCallback` Arayüz
```java
import com.aspose.words.*;

public class CustomFileNamePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) throws Exception {
        String outFileName = "YOUR_DOCUMENT_DIRECTORY/SavingCallback.PageFileNames.Page_" + args.getPageIndex() + ".html";
        args.setPageFileName(outFileName);

        try (FileOutputStream outputStream = new FileOutputStream(outFileName)) {
            args.setPageStream(outputStream);
        }

        assert !args.getKeepPageStreamOpen();
    }
}
```

- **Parametreler Açıklandı**:
  - `PageSavingArgs`: Kaydedilen sayfa hakkında bilgi içerir.
  - `setPageFileName()`: Her HTML sayfası için özel dosya adını ayarlar.

#### Sorun Giderme İpuçları
- Dizin yollarının doğru olduğundan emin olun ve bu sayede hatalardan kaçının `FileNotFoundException`.
- Dosya izinlerinin yazma işlemlerine izin verdiğini doğrulayın.

### Özellik 2: Belge Parçaları Kaydetme Geri Araması

Belgeleri sayfalar, sütunlar veya bölümler gibi parçalara ayırın ve bunları özel dosya adlarıyla kaydedin.

#### Genel bakış
Bu özellik, çıktı dosyaları üzerinde ayrıntılı denetim sağlayarak karmaşık belge yapılarını yönetmeye yardımcı olur.

#### Uygulama Adımları

##### Adım 1: Uygula `IDocumentPartSavingCallback` Arayüz
```java
import com.aspose.words.*;
import org.apache.commons.io.FilenameUtils;
import java.io.FileOutputStream;
import java.text.MessageFormat;

public class SavedDocumentPartRename implements IDocumentPartSavingCallback {
    private int mCount = 0;
    private final String mOutFileName;
    private final int mDocumentSplitCriteria;

    public SavedDocumentPartRename(String outFileName, int documentSplitCriteria) {
        this.mOutFileName = outFileName;
        this.mDocumentSplitCriteria = documentSplitCriteria;
    }

    public void documentPartSaving(DocumentPartSavingArgs args) throws Exception {
        String partType = determinePartType();
        String partFileName = MessageFormat.format("{0} part {1}, of type {2}.{3}", 
                                                   mOutFileName, ++mCount, partType, FilenameUtils.getExtension(args.getDocumentPartFileName()));
        
        args.setDocumentPartFileName(partFileName);

        try (FileOutputStream outputStream = new FileOutputStream("YOUR_DOCUMENT_DIRECTORY" + partFileName)) {
            args.setDocumentPartStream(outputStream);
        }

        assert args.getDocumentPartStream() != null;
        assert !args.getKeepDocumentPartStreamOpen();
    }

    private String determinePartType() {
        switch (mDocumentSplitCriteria) {
            case DocumentSplitCriteria.PAGE_BREAK: return "Page";
            case DocumentSplitCriteria.COLUMN_BREAK: return "Column";
            case DocumentSplitCriteria.SECTION_BREAK: return "Section";
            case DocumentSplitCriteria.HEADING_PARAGRAPH: return "Paragraph from heading";
            default: return "";
        }
    }
}
```

- **Parametreler Açıklandı**:
  - `DocumentPartSavingArgs`: Kaydedilen belge bölümü hakkında bilgi içerir.
  - `setDocumentPartFileName()`: Her belge parçası için özel dosya adını ayarlar.

#### Sorun Giderme İpuçları
- Çıktı dosyalarında karışıklığı önlemek için tutarlı adlandırma kurallarının kullanıldığından emin olun.
- Dosyaları yazarken istisnaları zarif bir şekilde işleyin.

### Özellik 3: Görüntü Kaydetme Geri Araması

HTML dönüştürme sırasında oluşturulan görsellerin dosya adlarını özelleştirerek düzeni ve netliği koruyun.

#### Genel bakış
Bu özellik, Word belgesinden oluşturulan görsellerin açıklayıcı dosya adlarına sahip olmasını sağlayarak, bunların yönetilmesini kolaylaştırır.

#### Uygulama Adımları

##### Adım 1: Uygula `IImageSavingCallback` Arayüz
```java
import com.aspose.words.*;
import org.apache.commons.io.FilenameUtils;
import java.io.FileOutputStream;
import java.text.MessageFormat;

public static class SavedImageRename implements IImageSavingCallback {
    private int mCount = 0;
    private final String mOutFileName;

    public SavedImageRename(String outFileName) {
        this.mOutFileName = outFileName;
    }

    public void imageSaving(ImageSavingArgs args) throws Exception {
        String imageFileName = MessageFormat.format("{0} shape {1}, of type {2}.{3}", 
                                                    mOutFileName, ++mCount, args.getCurrentShape().getShapeType(), FilenameUtils.getExtension(args.getImageFileName()));
        
        args.setImageFileName(imageFileName);

        args.setImageStream(new FileOutputStream("YOUR_DOCUMENT_DIRECTORY" + imageFileName));

        assert args.getImageStream() != null;
        assert args.isImageAvailable();
        assert !args.getKeepImageStreamOpen();
    }
}
```

- **Parametreler Açıklandı**:
  - `ImageSavingArgs`: Kaydedilen görüntü hakkında bilgi içerir.
  - `setImageFileName()`: Her çıktı görüntüsü için özel dosya adını ayarlar.

#### Sorun Giderme İpuçları
- Dosya işlemleri sırasında hataları önlemek için dizin yollarının geçerli olduğundan emin olun.
- Apache Commons IO gibi gerekli tüm bağımlılıkların projenize dahil edildiğini doğrulayın.

### Özellik 4: CSS Kaydetme Geri Araması

Özel dosya adları ve akışları ayarlayarak HTML dönüştürme sırasında CSS stil sayfalarını etkili bir şekilde yönetin.

#### Genel bakış
Bu özellik, CSS dosyalarının nasıl oluşturulacağını ve adlandırılacağını kontrol etmenizi sağlayarak farklı belge dışa aktarımlarında tutarlılığı garanti eder.

#### Uygulama Adımları

##### Adım 1: Uygula `ICssSavingCallback` Arayüz
```java
import com.aspose.words.*;
import java.io.FileOutputStream;

public static class CustomCssSavingCallback implements ICssSavingCallback {
    private final String mCssTextFileName;
    private final boolean mIsExportNeeded;
    private final boolean mKeepCssStreamOpen;

    public CustomCssSavingCallback(String cssDocFilename, boolean isExportNeeded, boolean keepCssStreamOpen) {
        this.mCssTextFileName = cssDocFilename;
        this.mIsExportNeeded = isExportNeeded;
        this.mKeepCssStreamOpen = keepCssStreamOpen;
    }

    public void cssSaving(CssSavingArgs args) throws Exception {
        args.setCssStream(new FileOutputStream(mCssTextFileName));
        args.isExportNeeded(mIsExportNeeded);
        args.setKeepCssStreamOpen(mKeepCssStreamOpen);
    }
}
```

- **Parametreler Açıklandı**:
  - `CssSavingArgs`: Kaydedilen CSS hakkında bilgi içerir.
  - `setCssStream()`: Çıkış CSS dosyası için özel bir akış ayarlar.

#### Sorun Giderme İpuçları
- Yazma hatalarını önlemek için CSS dosya yollarının doğru şekilde belirtildiğini doğrulayın.
- CSS dosyalarının kolayca tanımlanması için tutarlı adlandırma kurallarının kullanıldığından emin olun.

## Pratik Uygulamalar

Bu özelliklerin uygulanabileceği bazı gerçek dünya kullanım örnekleri şunlardır:

1. **Belge Yönetim Sistemleri**: Daha iyi erişim ve yönetim için belge parçalarının ve görüntülerinin organizasyonunu otomatikleştirin.
2. **Web Yayıncılığı**: Sunucunuzda temiz bir dizin yapısı korumak için HTML dışa aktarımlarını belirli dosya adlarıyla özelleştirin.
3. **İçerik Portalları**: Farklı içerik türlerinde tutarlı adlandırma kurallarını garantilemek, SEO'yu ve kullanıcı deneyimini geliştirmek için geri aramaları kullanın.

## Performans Hususları

Bu özellikleri uygularken aşağıdaki performans ipuçlarını göz önünde bulundurun:

- **Dosya G/Ç İşlemlerini Optimize Edin**: Otomatik kaynak yönetimi için try-with-resources'ı kullanarak açık dosya tutamaklarını en aza indirin.
- **Toplu İşleme**: Bellek kullanımını azaltmak ve işlem hızını artırmak için büyük belgeleri daha küçük gruplar halinde işleyin.
- **Kaynak Yönetimi**: Dönüştürme işlemleri sırasında darboğazları önlemek için sistem kaynaklarını izleyin.

## Çözüm

Bu eğitimde, Java'da Aspose.Words geri aramalarıyla özel sayfa ve resim kaydetmeyi nasıl uygulayacağınızı öğrendiniz. Bu güçlü özelliklerden yararlanarak, uygulamalarınızda belge yönetimini geliştirebilir ve HTML dönüşümlerini kolaylaştırabilirsiniz. 

### Sonraki Adımlar
- Belge işleme yeteneklerinizi daha da genişletmek için Aspose.Words'ün ek işlevlerini keşfedin.
- Belirli ihtiyaçlarınıza uyacak şekilde farklı geri arama yapılandırmalarını deneyin.

### Harekete Geçirici Mesaj
Çözümü bugün uygulamaya çalışın ve özelleştirilmiş belge dışa aktarımının faydalarını ilk elden deneyimleyin!

## SSS Bölümü

1. **Java için Aspose.Words nedir?**
   - Geliştiricilerin Java uygulamalarında Word belgeleriyle çalışabilmelerini sağlayan, dönüştürme, düzenleme ve işleme gibi özellikler sunan bir kütüphanedir.

2. **Aspose.Words ile büyük belgeleri nasıl verimli bir şekilde yönetebilirim?**
   - Bellek kullanımını etkili bir şekilde yönetmek için toplu işlemeyi kullanın ve dosya G/Ç işlemlerini optimize edin.

3. **Sayfalar ve resimlerin dışında diğer belge öğelerinin dosya adlarını özelleştirebilir miyim?**
   - Evet, bölümler ve sütunlar dahil olmak üzere çeşitli belge parçaları için dosya adlarını özelleştirmek amacıyla geri aramaları kullanabilirsiniz.

4. **Maven projesinde Aspose.Words kurulumu sırasında karşılaşılan yaygın sorunlar nelerdir?**
   - Emin olun ki `pom.xml` Doğru bağımlılık sürümünü ve depo ayarlarınızın Aspose'un kütüphanelerine erişime izin verdiğini içerir.

5. **Aspose.Words ile HTML dönüşümü sırasında CSS dosyalarını nasıl yönetebilirim?**
   - Uygula `ICssSavingCallback` Belge dönüştürme sırasında CSS dosyalarının nasıl adlandırılacağı ve saklanacağını özelleştirmek için arayüz.

## Kaynaklar

- **Belgeleme**: [Aspose.Words Java Referansı](https://reference.aspose.com/words/java/)
- **İndirmek**: [Java için Aspose.Words Sürümleri](https://releases.aspose.com/words/java/)
- **Satın almak**: [Aspose Lisansı Satın Al](https://purchase.aspose.com/buy)
- **Ücretsiz Deneme**: [Aspose.Words Ücretsiz Deneme](https://releases.aspose.com/words/java/)
- **Geçici Lisans**: [Geçici Lisans Alın](https://purchase.aspose.com/temporary-license/)
- **Destek**: [Aspose Forum](https://forum.aspose.com/c/words/10)

Bu kılavuzu takip ederek, Aspose.Words geri aramalarını kullanarak Java uygulamalarınızda özel belge kaydetme özelliklerini etkili bir şekilde uygulayabilirsiniz. İyi kodlamalar!

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}