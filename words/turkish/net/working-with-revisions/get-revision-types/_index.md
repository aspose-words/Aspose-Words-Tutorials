---
title: Kelime Türlerinin Gözden Geçirilmesini Alın
linktitle: Kelime Türlerinin Gözden Geçirilmesini Alın
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak bir Word belgesindeki kelimelerin revizyon türlerini nasıl alacağınızı öğrenin. Bu adım adım kılavuz, belge revizyonlarını verimli bir şekilde yönetmenize yardımcı olur.
weight: 10
url: /tr/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kelime Türlerinin Gözden Geçirilmesini Alın

## giriiş

Hiç kendinizi belge revizyonlarının denizinde, kimin neyi ne zaman taşıdığını merak ederken buldunuz mu? Yalnız değilsiniz. Belge revizyonlarını yönetmek, özellikle kapsamlı belgelerle uğraşırken sıkıcı bir görev olabilir. Ancak endişelenmeyin! Aspose.Words for .NET ile bu revizyonları kolayca belirleyebilir ve yönetebilirsiniz. Bu kılavuzda, Aspose.Words for .NET kullanarak bir Word belgesindeki kelimelerin revizyon türlerini nasıl edineceğinize dair adım adım bir süreçte size yol göstereceğiz. O halde kemerlerinizi bağlayın ve başlayalım!

## Ön koşullar

Kodlarla uğraşmaya başlamadan önce, ihtiyacınız olacak birkaç şey var:

1.  Aspose.Words for .NET Kütüphanesi: Henüz yapmadıysanız, şu adresten indirin:[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
3. Temel C# Bilgisi: C# programlama dilini anlamak faydalı olacaktır.
4.  Revizyonları Olan Bir Word Belgesi: Bir tane olduğundan emin olun`.docx`Kodu test etmek için izlenen değişiklikleri içeren dosya.

## Ad Alanlarını İçe Aktar

Başlamak için, C# projenize gerekli ad alanlarını içe aktarmanız gerekir. Bu, Aspose.Words for .NET tarafından sağlanan işlevlere erişmenizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Daha iyi anlaşılması ve uygulanması için örneği birden fazla adıma bölelim.

## Adım 1: Belge Dizininizi Ayarlayın

İlk önce, belgeler dizininize giden yolu tanımlamanız gerekir. Revizyonlu Word belgeniz burada bulunacaktır.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` Belgelerinizin bulunduğu klasöre giden gerçek yol ile.

## Adım 2: Word Belgenizi Yükleyin

Sonra, Word belgesini projenize yüklemeniz gerekir. Bu belgede analiz etmek istediğiniz revizyonlar bulunmalıdır.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

 Dosyanın güvenli olduğundan emin olun`Revisions.docx` belirtilen dizinde mevcuttur.

## Adım 3: Paragraf Koleksiyonuna Erişim

Artık belgeniz yüklendiğine göre, belgenin gövdesinin ilk bölümündeki paragraflara erişmeniz gerekiyor. Bu, revizyonları kontrol etmek için her paragrafı yinelemenize yardımcı olacaktır.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Adım 4: Paragraflarda Yineleme Yapın ve Revizyonları Kontrol Edin

İşte sihir burada gerçekleşir. Her paragrafı tekrar tekrar inceleyecek ve taşınıp taşınmadığını (silindiğini veya eklendiğini) kontrol edeceksiniz.

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

 Bu döngü her paragrafı dolaşır ve kullanır`IsMoveFromRevision` Ve`IsMoveToRevision` Paragrafın taşındığını (silindiğini) veya taşındığını (eklendiğini) belirlemek için özellikler.

## Çözüm

Ve işte karşınızda! Sadece birkaç satır kodla, Aspose.Words for .NET kullanarak Word belgenizdeki revizyon türlerini kolayca belirleyebilirsiniz. Bu güçlü kütüphane, belge revizyonlarını yönetmeyi kolaylaştırır ve daha önemli görevlere odaklanmanızı sağlar. 

## SSS

### Belirli kullanıcılar tarafından yapılan değişiklikleri izlemek için Aspose.Words for .NET'i kullanabilir miyim?

Evet, Aspose.Words for .NET, değişikliklerin yazarı da dahil olmak üzere revizyon ayrıntılarına erişim işlevi sağlar.

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?

 Kesinlikle! Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET için geçici lisans başvurusunu nasıl yapabilirim?

 Geçici lisans talebinde bulunabilir ve başvuruda bulunabilirsiniz.[Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET için daha detaylı dokümanları nerede bulabilirim?

 Ayrıntılı dokümantasyon şu adreste mevcuttur:[Aspose web sitesi](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET'i ticari olmayan bir projede kullanabilir miyim?

Evet, Aspose.Words for .NET hem ticari hem de ticari olmayan projelerde kullanılabilir, ancak lisans koşullarını kontrol ettiğinizden emin olun.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
