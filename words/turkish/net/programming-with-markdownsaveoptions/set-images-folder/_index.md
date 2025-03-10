---
title: Görüntüler Klasörünü Ayarla
linktitle: Görüntüler Klasörünü Ayarla
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerini uygun tablo hizalamasıyla Markdown'a dönüştürün. Mükemmel sonuçlar için ayrıntılı kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Görüntüler Klasörünü Ayarla

## giriiş

Word belgenizi tabloların ve içeriğin mükemmel şekilde hizalanmasını sağlayarak Markdown formatına aktarmak istediniz mi hiç? Aspose.Words for .NET bu görev için başvuracağınız çözümdür. Bu makalede, Aspose.Words'ü kurma, belgenizi hazırlama ve uygun tablo içerik hizalamasıyla Markdown'a aktarma sürecinde size yol göstereceğiz. Her adımı takip etmeyi ve anlamayı kolaylaştırmak için parçalara ayıracağız. Hadi, başlayalım ve Word belgelerinizi güzelce hizalanmış Markdown dosyalarına dönüştürelim!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

-  Aspose.Words for .NET: İndirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
-  Geçerli bir lisans: Ücretsiz deneme edinin[Burada](https://releases.aspose.com/) veya geçici bir lisans[Burada](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Veya .NET geliştirmeyi destekleyen herhangi bir IDE.
- C# temel bilgisi: C# programlama dilinin anlaşılması.

## Ad Alanlarını İçe Aktar

Başlamak için, C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu ad alanları, Aspose.Words işlevselliğine erişmenizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Adım 1: Projenizi Kurun

İlk önce, .NET projenizi IDE'nizde kurun. Yeni bir konsol uygulaması oluşturun ve .NET için Aspose.Words'e bir referans ekleyin.

### 1.1 Yeni Bir Proje Oluşturun

Visual Studio'yu açın ve yeni bir Konsol Uygulaması projesi oluşturun. "MarkdownExporter" veya benzeri bir isim verin.

### 1.2 Aspose.Words Referansını Ekle

 Projenize Aspose.Words'ü eklemek için DLL'yi şu adresten indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/words/net/) ve bunu manuel olarak ekleyin veya NuGet Paket Yöneticisini kullanın:

```bash
Install-Package Aspose.Words
```

## Adım 2: Markdown Olarak Dışa Aktarılacak Kodu Yazın

Şimdi Word belgesini okuyup, uygun tablo hizalamasıyla Markdown dosyası olarak kaydedecek kodu yazalım.

### 2.1 Belgenize Giden Yolu Tanımlayın

Word belgenizin yolunu ve görselleri kaydetmek istediğiniz klasörü ayarlayın.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Belgeyi Yükle

Word belgenizi Aspose.Words kullanarak yükleyin.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Markdown Kaydetme Seçeneklerini Yapılandırma

 Yapılandırın`MarkdownSaveOptions` resimlerin nerede saklanacağını belirtmek için.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Belgeyi Markdown Olarak Kaydet

 Birini kullan`MemoryStream` Belgeyi Markdown formatında kaydetmek için.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Çözüm

Bu adımları takip ettiğinizde, Aspose.Words for .NET kullanarak tablo içerik hizalamasıyla bir Word belgesini Markdown'a aktarmak kolaydır. Birkaç satır kodla, dönüştürme sürecini otomatikleştirebilir ve içeriğinizin iyi biçimlendirildiğinden emin olabilirsiniz. Artık, harika görüneceklerini ve yapılarını koruyacaklarını bilerek belgelerinizi Markdown biçiminde kolayca paylaşabilirsiniz.

## SSS

### Aspose.Words for .NET'i diğer programlama dilleriyle birlikte kullanabilir miyim?

Evet, Aspose.Words for .NET, VB.NET, F# ve daha fazlası gibi herhangi bir .NET uyumlu dille kullanılabilir.

### Aspose.Words için geçici lisansı nasıl alabilirim?

Geçici bir lisans alabilirsiniz[Burada](https://purchase.aspose.com/temporary-license/).

### Hangi tür belgeleri Markdown'a dönüştürebilirim?

.doc, .docx, .rtf ve daha fazlası dahil olmak üzere çeşitli Word belgelerini dönüştürebilirsiniz.

### Aspose.Words'ün deneme sürümünde herhangi bir sınırlama var mı?

Deneme sürümünde çıktı dosyalarında filigran gibi bazı sınırlamalar vardır. Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Words için daha fazla örnek ve dokümanı nerede bulabilirim?

 Ayrıntılı dokümanları ve örnekleri şu adreste bulabilirsiniz:[Aspose web sitesi](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
