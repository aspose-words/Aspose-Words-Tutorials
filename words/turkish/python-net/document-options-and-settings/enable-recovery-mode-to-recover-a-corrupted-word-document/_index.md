---
category: general
date: 2026-10-04
description: Aspose.Words'ta kurtarma modunu etkinleştirerek bozuk bir Word belgesini
  güvenli bir şekilde kurtarın. Tam Python kodu ve açıklamaları içeren adım adım kılavuzu
  izleyin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: tr
lastmod: 2026-10-04
og_description: Aspose.Words kullanarak bozuk bir Word belgesini kurtarmak için kurtarma
  modunu etkinleştirin. Bu öğreticide tam Python kodu, neden işe yaradığını ve kenar
  durumlarını nasıl ele alacağınızı gösterir.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Bozuk bir Word belgesini kurtarmak için kurtarma modunu etkinleştirin –
  tam rehber
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Bozuk bir Word belgesini kurtarmak için kurtarma modunu etkinleştirin
url: /tr/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bozuk bir Word belgesini kurtarmak için kurtarma modunu etkinleştir

Bir Word dosyasını yüklerken **kurtarma modunu etkinleştirmeniz** gerekiyorsa, bu kılavuz Aspose.Words for Python ile bunu tam olarak nasıl yapacağınızı gösterir. Kurtarma modunu açarak, aksi takdirde bir istisna fırlatacak **bozuk bir Word belgesini kurtarabilirsiniz**.

Aşağıdaki bölümlerde şunları öğreneceksiniz:

* Kurtarma davranışını kontrol eden sınıflar ve özellikler.  
* Uygulamanızı çökertmeden potansiyel olarak hasarlı bir `.docx` dosyasını nasıl yükleyeceğinizi.  
* Yaygın yükleme sorunlarını gidermek ve kurtarma stratejisini özelleştirmek için ipuçları.

> **Önkoşul** – `pip install aspose-words` ile Aspose.Words for Python yüklü ve Python dosya I/O hakkında temel bir anlayışa sahipsiniz.

## Kurtarma modunun ne yaptığı ve neden etkinleştirilmesi gerektiği

Aspose.Words, bir Word dosyasının iç yapısını `Document` nesnesi olarak ortaya çıkarmadan önce ayrıştırır. Dosya bozulmuşsa—eksik parçalar, kırık XML veya geçersiz ilişkiler—ayrıştırıcı şu iki yolu izleyebilir:

| Mod | Davranış |
|------|------------|
| `STRICT` | Bozulmanın ilk işaretinde bir istisna fırlatır. |
| `IGNORE_ERRORS` | Okunamayan bölümleri atlar ancak içeriği sessizce kaybedebilir. |
| `RECOVER` (**kurtarma modunu etkinleştir** seçeneği) | Belgeyi yeniden oluşturmaya çalışır, mümkün olduğunca çok içeriği korur ve seçilen modu `load_options.recovery_mode` aracılığıyla ortaya çıkarır. |

`RECOVER`, metin çıkarma veya PDF'ye dönüştürme gibi sonraki işlemler için **bozuk Word belgelerini kurtarmanız** gerektiğinde önerilen seçimdir.

## Adım 1: Yükleme seçeneklerini oluşturun ve kurtarma modunu etkinleştirin

İlk adım, `LoadOptions` nesnesini oluşturmak ve `recovery_mode` özelliğini `RecoveryMode.RECOVER` olarak ayarlamaktır. Bu, kütüphaneye ayrıştırma sırasında kurtarma yoluna girmesini söyler.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Neden önemli:**  
Bu adımı atlayıp belge hasarlıysa, `aw.Document(...)` yapıcı `InvalidOperationException` hatası verir. Kurtarma modunu etkinleştirmek çöküşü önler ve hâlâ çalışabileceğiniz kısmen‑tamir edilmiş bir `Document` nesnesi sağlar.

## Adım 2: Belirtilen seçenekleri kullanarak potansiyel olarak bozuk belgeyi yükleyin

`load_options` örneğini `Document` yapıcısına geçirin. Yükleyici artık kurtarma algoritmasını otomatik olarak uygulayacak.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**İpucu:** `YOUR_DIRECTORY` ifadesini çalışma zamanınızın erişebileceği mutlak ya da göreli yol ile değiştirin. Dosya mevcut değilse, Aspose.Words kurtarma mantığına ulaşmadan önce bir `FileNotFoundError` hatası verir.

## Adım 3: Kurtarma modunun uygulandığını doğrulayın

Aktif modu `load_options.recovery_mode` inceleyerek doğrulayabilirsiniz. Bu, günlük kaydı veya işlem hattının ilerleyen aşamalarında koşullu işleme için faydalıdır.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Beklenen çıktı**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Çıktı `RECOVER` gösteriyorsa, **kurtarma modunu etkinleştirmiş**siniz demektir ve belge artık daha ileri işleme (ör. metin çıkarma, PDF'ye dönüştürme veya tamir edilmiş bir kopyayı kaydetme) hazırdır.

## Adım 4 (isteğe bağlı): Gelecekte kullanmak için tamir edilmiş bir kopya kaydedin

Yükledikten sonra, kurtarılan belgeyi kalıcı hale getirerek kurtarma adımını tekrarlamak zorunda kalmayabilirsiniz.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Kaydetme, Aspose.Words tarafından geçerli kabul edilen yeni bir `.docx` oluşturur; bu dosya Microsoft Word'de uyarı olmadan açılabilir.

## Yaygın sorular ve uç‑durum yönetimi

| Soru | Cevap |
|----------|--------|
| **Belge tamamen okunamazsa ne olur?** | `RECOVER` modunda bile bazı dosyalar onarılamaz. `Document` nesnesi oluşturulur ancak yalnızca tek bir boş sayfa içerebilir. İçeriği doğrulamak için `doc.get_page_count()` kontrol edin. |
| **Yükleme sonrası `IGNORE_ERRORS`'a geçebilir miyim?** | Hayır. Kurtarma modu, `Document` yapıcısı çalışmadan **önce** ayarlanmalıdır. Farklı bir stratejiye ihtiyacınız varsa yeni bir `LoadOptions` örneği oluşturun. |
| **Kurtarma modu performansı etkiler mi?** | Evet, kütüphane kırık bölümleri yeniden oluşturmayı denediği için küçük bir ek yük ekler. Etki, çoğu dosya için önemsizdir (< 2 MB). |
| **Bu yaklaşım dil‑bağımsız mı?** | Aynı kavram .NET, Java ve Node.js API'lerinde (`LoadOptions.RecoveryMode`) mevcuttur. Kod sözdizimi değişir, ancak mantık aynıdır. |

## Pro ipucu: Ayrıntılı kurtarma bilgilerini günlüğe kaydedin

Aspose.Words, her kurtarma adımıyla ilgili ayrıntılı mesajlar alan bir `LoadOptions.recovery_callback` sağlar. Bunu bağlamak, belirli bir belgenin neden başarısız olduğunu teşhis etmenize yardımcı olabilir.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Artık her iç düzeltme (ör. “Removed duplicate relationship”) konsola yazdırılacak.

## Tam, çalıştırılabilir örnek

Tüm parçaları bir araya getirerek, hemen kopyalayıp çalıştırabileceğiniz bağımsız bir betik burada:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Betik çalıştırıldığında kurtarma modu, sayfa sayısı ve tamir edilmiş belgeden çıkarılan kelimeler listesi yazdırılır. `save_repaired=True` ayarlarsanız, orijinalin yanında yeni temiz bir dosya oluşur.

## Sonuç

Artık Aspose.Words for Python'da **kurtarma modunu etkinleştirmenin** ve güvenilir bir şekilde **bozuk Word belgelerini kurtarmanın** yollarını biliyorsunuz. Temel adımlar şunlardır:

1. `LoadOptions` oluşturun ve `recovery_mode`'u `RECOVER` olarak ayarlayın.  
2. Bu seçeneklerle `.docx` dosyasını yükleyin.  
3. Modu doğrulayın ve isteğe bağlı olarak tamir edilmiş bir kopya kaydedin.

Buradan, **kurtarılmış bir belgeden metin çıkarma**, **PDF'ye dönüştürme** veya büyük belge kütüphaneleri için **toplu kurtarmayı otomatikleştirme** gibi konuları keşfedebilirsiniz.

---

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalarla tam çalışan kod örnekleri içerir.

- [Bozuk DOCX Kurtarma – Kurtarma Modunu Etkinleştirme ve Sayfa Alma Tam Kılavuzu](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Bozuk DOCX Kurtarma – Word Belgesini Açma ve Yükleme](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [hasarlı docx'i Aspose.Words ile kurtarma – kurtarma modunu ayarlama ve yükleme seçenekleri](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}