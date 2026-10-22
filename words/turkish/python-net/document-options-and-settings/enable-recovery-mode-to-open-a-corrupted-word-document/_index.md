---
category: general
date: 2026-09-30
description: Aspose.Words kullanarak bozuk bir Word belgesini açmak için kurtarma
  modunu etkinleştirin. Bozuk docx dosyalarını güvenli ve güvenilir bir şekilde nasıl
  kurtaracağınızı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: tr
lastmod: 2026-09-30
og_description: Aspose.Words ile bozuk bir Word belgesini açmak için kurtarma modunu
  etkinleştirin. Bu kılavuz, bozuk docx dosyalarını adım adım nasıl kurtaracağınızı
  ve iş akışınızı istikrarlı tutacağınızı gösterir.
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: Bozuk Word belgelerini açmak için kurtarma modunu etkinleştir
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: Bozuk bir Word belgesini açmak için kurtarma modunu etkinleştir
url: /tr/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bozuk bir Word belgesini açmak için kurtarma modunu etkinleştirin

Bozuk bir Word belgesi açarken **recovery mode'u etkinleştir**meniz gerekiyorsa, bu öğretici Aspose.Words for Python ile bunu tam olarak nasıl yapacağınızı gösterir. Dosya aktarım sırasında zarar görmüş ya da uyumsuz bir program tarafından düzenlenmiş olsun, recovery mode'u etkinleştirmek, kütüphanenin belgeyi bir istisna fırlatmak yerine onarmaya çalışmasını sağlar.

Bu rehberde **bozuk Word belgesini aç** dosyalarını nasıl **bozuk docx'i kurtar** içeriğini ve **recovery ile belge yükle** sürecini kontrol eden seçenekleri anlayacaksınız. Adımlar, yazının yazıldığı sırada en yeni sürüm olan Aspose.Words 23.10 ile çalışır ve yalnızca standart bir Python ortamı gerektirir.

## Önkoşullar

* Python 3.9 ve üzeri yüklü.
* Aspose.Words for Python via .NET (`aspose-words`) yüklü (`pip install aspose-words`).
* Bozuk olduğu bilinen bir DOCX dosyası (test için geçerli bir `.docx` dosyasını `.zip` olarak yeniden adlandırıp XML'i manuel olarak bozabilirsiniz).

> **Pro tip:** Orijinal dosyanın bir yedeğini tutun. Recovery mode, belgenin bellekteki kopyasını değiştirir ancak açıkça kaydetmediğiniz sürece kaynağa geri yazmaz.

## Adım 1: Kütüphaneyi içe aktarın ve yükleme seçeneklerini oluşturun

İlk yapmanız gereken `aspose.words`'i içe aktarmak ve bir `LoadOptions` nesnesi örneklemektir. Bu nesne, dosyanın nasıl okunacağını etkileyen tüm ayarları tutar.

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*Neden önemli:* `LoadOptions`, ayrıştırıcıyı ince ayar yapmanın kapısıdır. Olmasaydı, Aspose.Words varsayılan katı modu kullanır ve herhangi bir yapısal hatada işlemi durdurur.

## Adım 2: Recovery mode'u etkinleştirin

`recovery_mode` özelliğini `RecoveryMode.RECOVER` olarak ayarlayın. Bu, yükleyiciye eksik XML düğümleri, bozuk ilişkiler veya kesilmiş akışlar gibi kırık parçaları otomatik olarak onarmaya çalışmasını söyler.

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

Recovery mode'u etkinleştirmek **mükemmel bir belge** garantilemez, ancak hâlâ metin, resim veya tabloları çıkarma şansını büyük ölçüde artırır.

## Adım 3: Olası bozuk DOCX'i yapılandırılmış seçeneklerle yükleyin

Şimdi dosya yolunu ve `LoadOptions` örneğini kabul eden `Document` yapıcısını kullanın.

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*Neden önemli:* `try/except` bloğu **bozuk docx'i güvenli bir şekilde nasıl aç** gösterir. Recovery mode olmadan aynı çağrı hemen bir istisna fırlatır ve programınız durur.

## Adım 4: Kurtarılan içeriği doğrulayın (isteğe bağlı ama önerilir)

Yükledikten sonra belgenin anlamlı içerik içerip içermediğini kontrol etmelisiniz. Hızlı bir yol, düz metni çıkarmak ve ilk birkaç karakteri yazdırmaktır.

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

Eğer çıktı makul bir önizleme gösteriyorsa, belgeyi işlemeye devam edebilirsiniz (ör. PDF'ye dönüştürme, tablo çıkarma vb.). Metin boşsa, dosya onarımın ötesinde olabilir ve yeni bir kopya talep etmeniz gerekebilir.

## Adım 5: Onarılan belgeyi kaydedin (temiz bir kopya istiyorsanız)

Kurtarılan içerikten memnun olduğunuzda, yeni, temiz bir DOCX kaydedebilirsiniz. Bu adım isteğe bağlıdır ancak genellikle sonraki iş akışları için faydalıdır.

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Kaydetmek, recovery mode'u tetikleyen bozulmayı artık içermeyen yeni bir dosya oluşturur.

## Kenar durumları ve ek ipuçları

| Situation                               | Recommended approach |
|----------------------------------------|----------------------|
| **Dosya DOCX değil** (ör. `.doc`) | Use `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` before loading. |
| **Yalnızca kısmi kurtarma**              | Yükledikten sonra `document.get_text()` ve `document.get_page_count()`'ı inceleyin. Sayfa sayısı 0 ise, belge kurtarılamaz olabilir. |
| **Büyük belgeler**                    | `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE`'ı etkinleştirerek kurtarma sırasında RAM kullanımını azaltın. |
| **Neğin onarıldığını kaydetme ihtiyacı**      | `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` ayarlayın ve ardından detaylar için `document.get_last_save_options().recovery_log`'u (varsa) okuyun. |

> **Dikkat:** Recovery mode, desteklenmeyen öğeleri sessizce atabilir (ör. eksik yazı tipleri). Görsel doğruluk kritikse, onarılan dosyayı bilinen iyi bir sürümle karşılaştırın.

## Tam çalışan örnek

Her şeyi bir araya getirerek, hemen çalıştırabileceğiniz bağımsız bir betik burada:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

Betik çalıştırıldığında bir başarı mesajı, kısa bir metin alıntısı yazdırır ve aynı klasörde `repaired.docx` dosyasını oluşturur.

## Sonuç

Artık Aspose.Words for Python kullanarak **recovery mode'u etkinleştirerek** **bozuk Word belgesi** dosyalarını **açmayı**, **bozuk docx** içeriğini **kurtarmayı** ve güvenli bir şekilde **recovery ile belge yüklemeyi** biliyorsunuz. Temel adımlar—`LoadOptions` oluşturma, `RecoveryMode.RECOVER`'ı açma ve istisnaları yakalama—herhangi bir otomasyon hattında yeniden kullanabileceğiniz güvenilir bir desen oluşturur.

Sonra, **kurtarılan belgeyi PDF'ye dönüştürme**, **`DocumentVisitor` ile tabloları çıkarma** veya **bozuk dosyaların bir klasörünü toplu işleme** gibi ilgili konuları keşfetmeyi düşünün. Bunların tümü burada gösterilen aynı recovery‑mode temelini üzerine inşa edilmiştir.

Kodlamaktan keyif alın ve belgeleriniz sağlıklı kalsın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [docx'i kurtarma – recovery mode'u ayarla ve bozuk Word dosyalarını aç](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Aspose.Words ile hasarlı docx'i kurtar – recovery mode ve load options ayarla](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [Aspose.Words LoadOptions ile bozuk DOCX'i kurtar – Tam C# Kılavuzu](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}