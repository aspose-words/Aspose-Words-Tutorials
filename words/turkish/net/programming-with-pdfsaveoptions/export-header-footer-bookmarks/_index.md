---
"description": "Aspose.Words for .NET'i kullanarak adım adım kılavuzumuzla Word belgesinden üst bilgi ve alt bilgi yer imlerini PDF'ye nasıl aktaracağınızı öğrenin."
"linktitle": "Word Belgesi Üstbilgi Altbilgi Yer İşaretlerini PDF Belgesine Aktar"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Word Belgesi Üstbilgi Altbilgi Yer İşaretlerini PDF Belgesine Aktar"
"url": "/tr/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesi Üstbilgi Altbilgi Yer İşaretlerini PDF Belgesine Aktar

## giriiş

Word belgelerini PDF'ye dönüştürmek, özellikle biçimlendirmelerini koruyarak belgeleri paylaşmak veya arşivlemek istediğinizde yaygın bir görevdir. Bazen bu belgeler, başlıklar ve altbilgiler içinde önemli yer imleri içerir. Bu eğitimde, bu yer imlerini .NET için Aspose.Words kullanarak bir Word belgesinden bir PDF'ye aktarma sürecini ele alacağız.

## Ön koşullar

Başlamadan önce, aşağıdakilere sahip olduğunuzdan emin olun:

- Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olması gerekir. Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Geliştirme ortamınızı kurun. Visual Studio veya herhangi bir .NET uyumlu IDE kullanabilirsiniz.
- Temel C# Bilgisi: Kod örneklerini takip edebilmek için C# programlamaya aşinalık gereklidir.

## Ad Alanlarını İçe Aktar

İlk önce, C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Kod dosyanızın en üstüne şu satırları ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Sürecin kolay takip edilebilir adımlara bölünmesine izin verin.

## Adım 1: Belgeyi Başlatın

İlk adım Word belgenizi yüklemektir. Bunu şu şekilde yapabilirsiniz:

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Bu adımda, yalnızca belge dizininize giden yolu belirtmeniz ve Word belgesini yüklemeniz yeterli olacaktır.

## Adım 2: PDF Kaydetme Seçeneklerini Yapılandırın

Daha sonra, başlık ve altbilgilerdeki yer imlerinin doğru şekilde dışa aktarılmasını sağlamak için PDF kaydetme seçeneklerini yapılandırmanız gerekir.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Burada, şunu kuruyoruz: `PdfSaveOptions`. `DefaultBookmarksOutlineLevel` özellik, yer imleri için anahat düzeyini ayarlar ve `HeaderFooterBookmarksExportMode` özellik, yer imlerinin yalnızca başlık ve altbilgilerdeki ilk oluşumunun dışa aktarılmasını sağlar.

## Adım 3: Belgeyi PDF olarak kaydedin

Son olarak belgenizi yapılandırdığınız seçeneklerle PDF olarak kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Bu adımda, belgeyi yapılandırdığınız seçeneklerle belirtilen yola kaydediyorsunuz.

## Çözüm

İşte bu kadar! Bu adımları izleyerek, Aspose.Words for .NET kullanarak bir Word belgesinin başlık ve alt bilgilerinden yer imlerini kolayca bir PDF'ye aktarabilirsiniz. Bu yöntem, belgenizdeki önemli gezinme yardımcılarının PDF formatında korunmasını sağlayarak okuyucuların belgenizde gezinmesini kolaylaştırır.

## SSS

### Word belgesindeki tüm yer imlerini PDF'e aktarabilir miyim?

Evet, yapabilirsiniz. `PdfSaveOptions`Gerekirse ayarları tüm yer imlerini içerecek şekilde düzenleyebilirsiniz.

### Belgenin gövdesinden de yer imlerini dışa aktarmak istersem ne olur?

Şunu yapılandırabilirsiniz: `OutliçindeeOptions` in `PdfSaveOptions` Belgenin gövdesinden yer imlerini dahil etmek için.

### PDF'deki yer imi düzeylerini özelleştirmek mümkün mü?

Kesinlikle! Özelleştirebilirsiniz `DefaultBookmarksOutlineLevel` Yer imleriniz için farklı anahat düzeyleri ayarlama özelliği.

### Yer imi olmayan belgeleri nasıl işlerim?

Belgenizde yer imi yoksa, PDF herhangi bir yer imi taslağı olmadan oluşturulacaktır. PDF'te yer imlerine ihtiyacınız varsa belgenizin yer imleri içerdiğinden emin olun.

### Bu yöntemi DOCX veya RTF gibi diğer belge türleri için de kullanabilir miyim?

Evet, Aspose.Words for .NET DOCX, RTF ve diğerleri de dahil olmak üzere çeşitli belge türlerini destekler.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}