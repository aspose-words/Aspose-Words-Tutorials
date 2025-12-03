---
"date": "2025-03-29"
"description": "XAML akış biçimi ve ilerleme geri aramalarını kullanarak Python için Aspose.Words ile belge kaydetmeyi nasıl optimize edeceğinizi öğrenin. Belgeleri yönetmede verimliliği artırın."
"title": "Python'da Belge Kaydetmeyi Optimize Etme&Aspose.Words XAML Akışı ve İlerleme Geri Aramaları"
"url": "/tr/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# Aspose.Words Kullanarak Python'da Belge Kaydetme Nasıl Optimize Edilir: XAML Akışı ve İlerleme Geri Aramaları

## giriiş

Python kullanarak belge dönüşümlerini verimli bir şekilde yönetmek mi istiyorsunuz? Belge kaydederken görüntüleri işleme ve ilerlemeyi izleme konusunda zorluk mu çekiyorsunuz? Bu eğitim, Python için Aspose.Words ile belge kaydetmeyi optimize etme konusunda size rehberlik eder ve iki güçlü özelliğe odaklanır: `XamlFlowSaveOptions` Görüntü Klasörü ve Belge Kaydetme İlerleme Geri Araması ile.

Bu kapsamlı kılavuz, Aspose.Words kütüphanesini kullanarak belge işleme iş akışlarını geliştirmek isteyen geliştiriciler için mükemmeldir.

**Ne Öğreneceksiniz:**
- Görüntü kaynaklarını yönetirken bir belgeyi XAML akış biçiminde nasıl kaydedersiniz.
- Uzun işlemleri önlemek için belge kaydetme sırasında ilerleme geri aramalarını uygulama.
- Geliştirme ortamınızda Python için Aspose.Words'ü kurma ve yapılandırma.
- Bu özelliklerin belge yönetim sistemlerindeki gerçek dünya uygulamaları.

Kodlamaya başlamadan önce ön koşullara bir göz atalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

### Gerekli Kütüphaneler ve Sürümler
- **Aspose.Python için Kelimeler**: 23.3 veya üzeri bir sürüme sahip olduğunuzdan emin olun.
- **piton**: 3.6 veya üzeri sürüm önerilir.

### Çevre Kurulum Gereksinimleri
- VSCode veya PyCharm gibi bir kod düzenleyici.
- Python programlamanın temel bilgisi.

### Bilgi Önkoşulları
- Belge işleme kavramlarına aşinalık.
- Python'da dosya işleme ve dizin yönetiminin anlaşılması.

## Python için Aspose.Words Kurulumu

Aspose.Words'ü kullanmaya başlamak için pip aracılığıyla yüklemeniz gerekir. Terminalinizi veya komut isteminizi açın ve şunu çalıştırın:

```bash
pip install aspose-words
```

### Lisans Edinme Adımları
1. **Ücretsiz Deneme**: Geçici bir lisansa erişin [Burada](https://purchase.aspose.com/temporary-license/) test amaçlı.
2. **Satın almak**: Uzun süreli kullanım için lisans satın alın [Burada](https://purchase.aspose.com/buy).
3. **Temel Başlatma ve Kurulum**:
   - Belgenizi kullanarak yükleyin `aw.Document()`.
   - Gerektiği gibi kaydetme seçeneklerini yapılandırın.

## Uygulama Kılavuzu

Bu bölüm, bu eğitimin iki ana özelliğinin uygulanmasında size yol gösterecektir: Görüntü Klasörü ile XamlFlowSaveOptions ve Belge Kaydetme İlerleme Geri Araması.

### Özellik 1: Görüntü Klasörü ile XamlFlowSaveOptions

#### Genel bakış
Bu özellik, bir görüntü klasörü ve takma ad belirtirken bir belgeyi XAML akış biçiminde kaydetmenize olanak tanır. Gömülü görüntülere sahip büyük belgeleri verimli bir şekilde yönetmek için idealdir.

#### Uygulama Adımları

##### Adım 1: Gerekli Kitaplıkları İçe Aktarın
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Adım 2: ImageUriPrinter Geri Arama Sınıfını Tanımlayın
Bu sınıf, dönüştürme sırasında görüntü akışlarını sayar ve belirtilen bir takma ad klasörüne yönlendirir.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # tür: Liste[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Temel Yapılandırma Seçenekleri:**
- `images_folder`: Görüntülerin kaydedileceği dizini belirtir.
- `images_folder_alias`: Belge dönüştürme sırasında kullanılan bir takma ad yolu ayarlar.

##### Sorun Giderme İpuçları
- Dosya bulunamadı hatalarını önlemek için kodu çalıştırmadan önce tüm dizinlerin mevcut olduğundan emin olun.
- Çıktı dizininizde yazma izinlerini kontrol edin.

### Özellik 2: Belge Kaydetme İlerlemesi Geri Araması

#### Genel bakış
Bu özellik, ilerleme geri aramasını kullanarak kaydetme işlemini yönetir ve uzun süren kaydetme işlemlerini iptal etmenize olanak tanır.

#### Uygulama Adımları

##### Adım 1: SavingProgressCallback Sınıfını Tanımlayın
Sınıf, belge kaydetme süresini izler ve belirtilen zaman sınırını aşarsa iptal eder.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Saniye cinsinden izin verilen maksimum süre.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Temel Yapılandırma Seçenekleri:**
- `save_format`: XAML_FLOW ve XAML_FLOW_PACK arasında seçim yapın.
- `progress_callback`: Uzun operasyonları yönetmek için ilerlemeyi kaydeder.

##### Sorun Giderme İpuçları
- Ayarlamak `max_duration` belgenin boyutuna ve karmaşıklığına göre.
- Bilgilendirici hata mesajları sağlamak için istisnaları zarif bir şekilde işleyin.

## Pratik Uygulamalar

Bu özelliklerin gerçek dünyadaki kullanım örnekleri şunlardır:
1. **Belge Yönetim Sistemleri**:Görüntü klasörlerini belirleyerek gömülü görüntülere sahip büyük belgeleri verimli bir şekilde yönetin, performansı ve organizasyonu artırın.
2. **Otomatik Raporlama Araçları**: Raporların kabul edilebilir zaman dilimleri içinde oluşturulmasını sağlamak ve kullanıcı deneyimini iyileştirmek için ilerleme geri aramalarını kullanın.
3. **İçerik Dağıtım Ağları**:Kaynakları etkili bir şekilde yönetirken, belgelerin web dağıtımına dönüştürülmesini kolaylaştırın.

## Performans Hususları

Aspose.Words'ü Python ile kullanırken performansı optimize etmek için:
- **Bellek Yönetimi**: Nesneleri kullanımdan sonra atarak kaynak kullanımını izleyin ve belleği verimli bir şekilde yönetin.
- **Dosya G/Ç İşlemleri**: Hızı artırmak için dosya okuma/yazma işlemlerini en aza indirin.
- **Toplu İşleme**: Mümkün olduğunda, genel giderleri azaltmak için belgeleri gruplar halinde işleyin.

## Çözüm

Bu eğitimde, XAML Flow ve ilerleme geri aramalarını kullanarak Python için Aspose.Words ile belge kaydetmeyi nasıl optimize edeceğinizi inceledik. Bu özellikleri uygulayarak, belge işleme iş akışlarınızın verimliliğini artırabilir, kaynakları etkili bir şekilde yönetebilir ve zamanında operasyonlar sağlayabilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}