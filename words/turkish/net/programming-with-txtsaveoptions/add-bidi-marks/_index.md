---
title: Word Belgesine Bidi İşaretleri Ekleme
linktitle: Word Belgesine Bidi İşaretleri Ekleme
second_title: Aspose.Words Belge İşleme API'si
description: Bu kılavuzla Aspose.Words for .NET kullanarak Word belgelerine çift yönlü (Bidi) işaretlerin nasıl ekleneceğini öğrenin. Çok dilli içerik için uygun metin yönünü sağlayın.
weight: 10
url: /tr/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesine Bidi İşaretleri Ekleme

## giriiş

Belge işleme dünyasında, çift yönlü (Bidi) metinleri yönetmek genellikle biraz zor olabilir. Bu, özellikle Arapça veya İbranice gibi farklı metin yönlerine sahip dillerle uğraşırken geçerlidir. Neyse ki, Aspose.Words for .NET bu tür senaryoları yönetmeyi kolaylaştırır. Bu eğitimde, Aspose.Words for .NET kullanarak bir Word belgesine Bidi işaretlerinin nasıl ekleneceğini ele alacağız.

## Ön koşullar

Koda dalmadan önce aşağıdakilerin mevcut olduğundan emin olun:

1. Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olması gerekir. Bunu şuradan indirebilirsiniz:[Aspose İndirmeler sayfası](https://releases.aspose.com/words/net/).
2. .NET Framework veya .NET Core: Örnekleri çalıştırmak için uyumlu bir .NET ortamınızın kurulu olduğundan emin olun.
3. Temel C# Bilgisi: C# programlama dili ve .NET'teki temel işlemlere aşinalık.

## Ad Alanlarını İçe Aktar

Başlamak için gerekli ad alanlarını içe aktarmanız gerekir. Bunları projenize nasıl dahil edebileceğiniz aşağıda açıklanmıştır:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Word belgesine Bidi işaretleri ekleme sürecini net adımlara bölelim. Her adım sizi kod ve amacı konusunda yönlendirecektir.

## Adım 1: Belgenizi Ayarlayın

 Yeni bir örnek oluşturarak başlayın`Document` sınıf ve bir`DocumentBuilder` belgeye içerik eklemek için.

```csharp
// Belgelerinizin dizinine giden yol
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Belgeyi oluşturun ve içerik ekleyin
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Bu adımda yeni bir Word belgesi başlatır ve bir`DocumentBuilder` içerik eklemeyi kolaylaştırmak için.

## Adım 2: Belgenize İçerik Ekleyin

Sonra, belgenize biraz metin ekleyin. Burada, Bidi metin işlemeyi göstermek için farklı dillerde metin ekleyeceğiz.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Burada, önce standart bir İngilizce cümle ekliyoruz. Ardından, İbranice ve Arapça yazılmış olan sonraki metin için Bidi metin biçimlendirmesini etkinleştiriyoruz. Bu, çift yönlü metnin nasıl dahil edileceğini gösterir.

## Adım 3: Bidi İşaretleri için Kaydetme Seçeneklerini Yapılandırın

 Bidi işaretlerinin belgeye doğru şekilde kaydedildiğinden emin olmak için,`TxtSaveOptions` ve etkinleştirin`AddBidiMarks` seçenek.

```csharp
// Bidi işaretleri ekle
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 Bu adımda, bir örnek oluşturuyoruz`TxtSaveOptions` ve ayarla`AddBidiMarks`mülk`true`Bu, belgenin metin dosyası olarak kaydedilmesi sırasında Bidi işaretlerinin dahil edilmesini sağlar.

## Çözüm

Word belgelerinize Bidi işaretleri eklemek, farklı metin yönlerine sahip dilleri içeren çok dilli içeriklerle uğraşırken önemli bir adım olabilir. Aspose.Words for .NET ile bu süreç basit ve etkilidir. Yukarıda belirtilen adımları izleyerek, belgelerinizin Bidi metnini doğru şekilde temsil etmesini sağlayabilir, okunabilirliği ve doğruluğu artırabilirsiniz.

## SSS

### Bidi işaretleri nedir ve neden önemlidir?
Bidi işaretleri, belgelerdeki metnin yönünü kontrol etmek için kullanılan özel karakterlerdir. Arapça ve İbranice gibi sağdan sola okunan dilleri düzgün bir şekilde görüntülemek için gereklidirler.

### Diğer metin yönü sorunlarını çözmek için Aspose.Words for .NET'i kullanabilir miyim?
Evet, Aspose.Words for .NET, sağdan sola ve soldan sağa diller de dahil olmak üzere çeşitli metin yönü ve biçimlendirme ihtiyaçları için kapsamlı destek sağlar.

### Bidi biçimlendirmesini yalnızca belgenin belirli bölümlerine uygulamak mümkün müdür?
Evet, Bidi biçimlendirmesini ihtiyaç duyduğunuzda belgenizin belirli paragraflarına veya bölümlerine uygulayabilirsiniz.

### Bidi işaretli dokümanı hangi formatlarda kaydedebilirim?
Verilen örnekte, belge bir metin dosyası olarak kaydedilir. Ancak, Aspose.Words ayrıca Bidi işaretlerini korurken belgeleri çeşitli biçimlerde kaydetmeyi destekler.

### Aspose.Words for .NET hakkında daha fazla bilgiyi nerede bulabilirim?
 Aspose.Words for .NET hakkında daha fazla bilgi edinmek için şuraya tıklayabilirsiniz:[Aspose Belgeleri](https://reference.aspose.com/words/net/) ve erişim[Destek Forumu](https://forum.aspose.com/c/words/8) ek yardım için.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
