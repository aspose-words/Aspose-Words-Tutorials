---
title: Belge Metin Yönü
linktitle: Belge Metin Yönü
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım kılavuzla Aspose.Words for .NET kullanarak Word'de belge metin yönünü nasıl ayarlayacağınızı öğrenin. Sağdan sola dilleri işlemek için mükemmeldir.
weight: 10
url: /tr/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belge Metin Yönü

## giriiş

Word belgeleriyle çalışırken, özellikle birden fazla dil veya özel biçimlendirme gereksinimleri içeren belgelerde, metin yönünü ayarlamak çok önemli olabilir. Örneğin, İbranice veya Arapça gibi sağdan sola dillerle çalışırken, metin yönünü buna göre ayarlamanız gerekebilir. Bu kılavuzda, .NET için Aspose.Words kullanarak belge metin yönünün nasıl ayarlanacağını ele alacağız. 

## Ön koşullar

Koda dalmadan önce aşağıdakilerin mevcut olduğundan emin olun:

-  Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET'in yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/words/net/).
- Visual Studio: C# kodu yazmak ve çalıştırmak için bir geliştirme ortamı.
- Temel C# Bilgisi: Biraz kod yazacağımız için C# programlamaya aşina olmanız faydalı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için, projenizde Aspose.Words ile çalışmak için gerekli ad alanlarını içe aktarmanız gerekir. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Bu ad alanları, Word belgelerini yönetmek için gereken sınıflara ve yöntemlere erişim sağlar.

## Adım 1: Belge Dizininize Giden Yolu Tanımlayın

Öncelikle belgenizin bulunduğu yolu ayarlayın. Bu, dosyaları doğru şekilde yüklemek ve kaydetmek için çok önemlidir.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` Belgenizin saklandığı gerçek yol ile.

## Adım 2: Belge Yön Ayarı ile TxtLoadOptions Oluşturun

 Daha sonra, bir örnek oluşturmanız gerekecek`TxtLoadOptions` ve ayarla`DocumentDirection` özellik. Bu, Aspose.Words'e belgedeki metnin yönünü nasıl işleyeceğini söyler.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

 Bu örnekte şunu kullanıyoruz:`DocumentDirection.Auto` Aspose.Words'ün içeriğe göre yönü otomatik olarak belirlemesini sağlamak.

## Adım 3: Belgeyi Yükleyin

 Şimdi, belgeyi kullanarak yükleyin`Document` sınıf ve daha önce tanımlanmış`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

 Burada,`"Hebrew text.txt"` metin dosyanızın adıdır. Bu dosyanın belirtilen dizinde bulunduğundan emin olun.

## Adım 4: Paragrafın Çift Yönlü Biçimlendirmesine Erişim ve Kontrol

Metin yönünün doğru ayarlandığını doğrulamak için belgenin ilk paragrafına erişin ve çift yönlü biçimlendirmesini kontrol edin.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Bu adım, belgenin metin yönünün beklendiği gibi uygulandığını doğrulamak ve hata ayıklamak için yararlıdır.

## Adım 5: Belgeyi Yeni Ayarlarla Kaydedin

Son olarak değişiklikleri uygulamak ve kalıcı hale getirmek için belgeyi kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

 Burada,`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` çıktı dosyasının adıdır. Yaptığınız değişiklikleri yansıtan bir ad seçtiğinizden emin olun.

## Çözüm

Word belgelerinde metin yönünü ayarlamak, Aspose.Words for .NET ile basit bir işlemdir. Bu adımları izleyerek, belgenizin sağdan sola veya soldan sağa metni nasıl işleyeceğini kolayca yapılandırabilirsiniz. Çok dilli belgelerle çalışıyor veya belirli diller için metin yönünü biçimlendirmeniz gerekiyorsa, Aspose.Words ihtiyaçlarınızı karşılamak için sağlam bir çözüm sunar.

## SSS

###  Nedir?`DocumentDirection` property used for?

 The`DocumentDirection` mülk`TxtLoadOptions` belge için metin yönünü belirler. Şu şekilde ayarlanabilir`DocumentDirection.Auto`, `DocumentDirection.LeftToRight` , veya`DocumentDirection.RightToLeft`.

### Tüm belge yerine belirli paragraflar için metin yönünü ayarlayabilir miyim?

 Evet, belirli paragraflar için metin yönünü şu şekilde ayarlayabilirsiniz:`ParagraphFormat.Bidi` mülkiyet, ancak`TxtLoadOptions.DocumentDirection` özellik, tüm belge için varsayılan yönü ayarlar.

###  Yükleme için hangi dosya biçimleri destekleniyor?`TxtLoadOptions`?

`TxtLoadOptions` öncelikle metin dosyalarını (.txt) yüklemek için kullanılır. Diğer dosya biçimleri için, aşağıdaki gibi farklı sınıflar kullanın`DocLoadOptions` veya`DocxLoadOptions`.

### Karışık metin yönlerine sahip belgeleri nasıl işleyebilirim?

 Karışık metin yönlerine sahip belgeler için, biçimlendirmeyi paragraf bazında yapmanız gerekebilir.`ParagraphFormat.Bidi` Her paragrafın yönünü gerektiği gibi ayarlama özelliği.

### Aspose.Words for .NET hakkında daha fazla bilgiyi nerede bulabilirim?

 Daha fazla ayrıntı için şuraya bakın:[Aspose.Words .NET Belgeleri için](https://reference.aspose.com/words/net/) Ayrıca şu gibi ek kaynakları da keşfedebilirsiniz:[İndirme bağlantısı](https://releases.aspose.com/words/net/), [Satın almak](https://purchase.aspose.com/buy), [Ücretsiz deneme](https://releases.aspose.com/), [Geçici lisans](https://purchase.aspose.com/temporary-license/) , Ve[Destek](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
