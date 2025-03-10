---
title: Word Dosyasından Active XControl Özelliklerini Oku
linktitle: Word Dosyasından Active XControl Özelliklerini Oku
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word dosyalarından ActiveX denetim özelliklerinin nasıl okunacağını adım adım bir kılavuzda öğrenin. Belge otomasyon becerilerinizi geliştirin.
weight: 10
url: /tr/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word Dosyasından Active XControl Özelliklerini Oku

## giriiş

Günümüzün dijital çağında, otomasyon üretkenliği artırmanın anahtarıdır. ActiveX denetimleri içeren Word belgeleriyle çalışıyorsanız, çeşitli amaçlar için özelliklerini okumanız gerekebilir. Onay kutuları ve düğmeler gibi ActiveX denetimleri önemli verileri tutabilir. .NET için Aspose.Words'ü kullanarak, bu verileri programatik olarak verimli bir şekilde çıkarabilir ve işleyebilirsiniz.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET Kütüphanesi: Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. Visual Studio veya herhangi bir C# IDE: Kodunuzu yazmak ve çalıştırmak için.
3. ActiveX denetimleri içeren bir Word belgesi: Örneğin, "ActiveX denetimleri.docx".
4. Temel C# bilgisi: Takip edebilmek için C# programlamaya aşinalık gereklidir.

## Ad Alanlarını İçe Aktar

Öncelikle Aspose.Words for .NET ile çalışmak için gerekli ad alanlarını içe aktaralım.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Adım 1: Word Belgesini Yükleyin

Başlamak için ActiveX denetimlerini içeren Word belgesini yüklemeniz gerekir.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Adım 2: Özellikleri Tutmak İçin Bir Dize Başlatın

Daha sonra ActiveX denetimlerinin özelliklerini depolamak için boş bir dize başlatın.

```csharp
string properties = "";
```

## Adım 3: Belgedeki Şekiller Arasında Yineleme Yapın

ActiveX denetimlerini bulmak için belgedeki tüm şekilleri yinelememiz gerekiyor.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // ActiveX denetimini işle
    }
}
```

## Adım 4: ActiveX Denetimlerinden Özellikleri Çıkarın

Döngü içinde, kontrolün Forms2OleControl olup olmadığını kontrol edin. Eğer öyleyse, onu dönüştürün ve özelliklerini çıkarın.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Adım 5: Toplam ActiveX Denetimlerini Say

Tüm şekilleri yineledikten sonra bulunan toplam ActiveX denetimlerinin sayısını sayın.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Adım 6: Özellikleri Görüntüle

Son olarak çıkarılan özellikleri konsola yazdırın.

```csharp
Console.WriteLine("\n" + properties);
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir Word belgesinden ActiveX denetim özelliklerini okumayı başarıyla öğrendiniz. Bu eğitim, bir belgeyi yüklemeyi, şekiller arasında yinelemeyi ve ActiveX denetimlerinden özellikleri çıkarmayı kapsıyordu. Bu adımları izleyerek, Word belgelerinizden önemli verilerin çıkarılmasını otomatikleştirebilir ve iş akışı verimliliğinizi artırabilirsiniz.

## SSS

### Word belgelerindeki ActiveX denetimleri nelerdir?
ActiveX denetimleri, formlar oluşturmak ve görevleri otomatikleştirmek için kullanılan onay kutuları, düğmeler ve metin alanları gibi Word belgelerine yerleştirilmiş etkileşimli nesnelerdir.

### Aspose.Words for .NET kullanarak ActiveX denetimlerinin özelliklerini değiştirebilir miyim?
Evet, Aspose.Words for .NET, ActiveX denetimlerinin özelliklerini program aracılığıyla değiştirmenize olanak tanır.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
 Aspose.Words for .NET ücretsiz deneme sunuyor ancak devam eden kullanım için bir lisans satın almanız gerekecek. Ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/).

### Aspose.Words for .NET'i C# dışındaki diğer .NET dilleriyle birlikte kullanabilir miyim?
Evet, Aspose.Words for .NET, VB.NET ve F# dahil olmak üzere herhangi bir .NET diliyle kullanılabilir.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
 Ayrıntılı dokümanları bulabilirsiniz[Burada](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
