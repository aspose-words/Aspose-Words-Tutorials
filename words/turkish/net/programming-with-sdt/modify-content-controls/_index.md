---
"description": "Aspose.Words for .NET kullanarak Word'de yapılandırılmış belge etiketlerini nasıl değiştireceğinizi öğrenin. Metni, açılır menüleri ve görselleri adım adım güncelleyin."
"linktitle": "İçerik Denetimlerini Değiştir"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "İçerik Denetimlerini Değiştir"
"url": "/tr/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# İçerik Denetimlerini Değiştir

## giriiş

Word belgeleriyle çalıştıysanız ve .NET için Aspose.Words kullanarak düz metin, açılır listeler veya resimler gibi yapılandırılmış içerik denetimlerini değiştirmeniz gerekiyorsa, doğru yerdesiniz! Yapılandırılmış Belge Etiketleri (SDT'ler), belge otomasyonunu daha kolay ve daha esnek hale getiren güçlü araçlardır. Bu eğitimde, bu SDT'leri ihtiyaçlarınıza uyacak şekilde nasıl değiştirebileceğinizi ele alacağız. İster metni güncelleyin, ister açılır seçimleri değiştirin veya resimleri değiştirin, bu kılavuz sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

İçerik kontrollerini değiştirmenin inceliklerine girmeden önce, aşağıdakilere sahip olduğunuzdan emin olun:

1. .NET için Aspose.Words Yüklendi: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Değilse, şunları yapabilirsiniz: [buradan indirin](https://releases.aspose.com/words/net/).

2. Temel C# Bilgisi: Bu eğitimde temel C# programlama kavramlarına aşina olduğunuzu varsayıyoruz.

3. .NET Geliştirme Ortamı: .NET uygulamalarını çalıştırmak için Visual Studio gibi bir IDE'niz olmalıdır.

4. Örnek Belge: Çeşitli SDT türlerini içeren bir örnek Word belgesi kullanacağız. Örnektekini kullanabilir veya kendinizinkini oluşturabilirsiniz.

5. Aspose Belgelerine Erişim: Daha ayrıntılı bilgi için şuraya bakın: [Aspose.Words belgeleri](https://reference.aspose.com/words/net/).

## Ad Alanlarını İçe Aktar

Aspose.Words ile çalışmaya başlamak için ilgili ad alanlarını C# projenize aktarmanız gerekir. Bunu şu şekilde yapabilirsiniz:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Bu ad alanları, Word belgelerinizdeki yapılandırılmış belge etiketlerini düzenlemek için gerekli sınıflara ve yöntemlere erişmenizi sağlayacaktır.

## Adım 1: Belge Yolunuzu Ayarlayın

Herhangi bir değişiklik yapmadan önce, belgenizin yolunu belirtmeniz gerekir. Değiştir `"YOUR DOCUMENT DIRECTORY"` Belgenizin saklandığı gerçek yol ile.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Adım 2: Yapılandırılmış Belge Etiketleri Arasında Döngü

SDT'leri değiştirmek için öncelikle belgedeki tüm SDT'leri dolaşmanız gerekir. Bu, şu şekilde yapılır: `GetChildNodes` türündeki tüm düğümleri alma yöntemi `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // SDT'leri türlerine göre değiştirin
}
```

## Adım 3: Düz Metin SDT'lerini Değiştirin

SDT düz metin türündeyse içeriğini değiştirebilirsiniz. Önce mevcut içeriği temizleyin, sonra yeni metin ekleyin.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Açıklama: Burada, `RemoveAllChildren()` SDT'nin mevcut içeriğini temizler. Daha sonra yeni bir içerik oluştururuz `Paragraph` Ve `Run` yeni metni eklemek için nesne.

## Adım 4: Açılır Liste SDT'lerini Değiştirin

Açılır liste SDT'leri için, seçili öğeyi şuraya erişerek değiştirebilirsiniz: `ListItems` koleksiyon. Burada, listedeki üçüncü öğeyi seçiyoruz.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Açıklama: Bu kod parçacığı, açılır listeden 2. dizindeki öğeyi (üçüncü öğe) seçer. Dizini ihtiyaçlarınıza göre ayarlayın.

## Adım 5: Resim SDT'lerini Değiştirin

Bir resim SDT'si içindeki bir resmi güncellemek için mevcut resmi yenisiyle değiştirebilirsiniz.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

Açıklama: Bu kod, şeklin bir resim içerip içermediğini kontrol eder ve ardından onu şu konumda bulunan yeni bir resimle değiştirir: `ImagesDir`.

## Adım 6: Değiştirilmiş Belgenizi Kaydedin

Gerekli tüm değişiklikleri yaptıktan sonra, orijinal belgenizi korumak için değiştirilen belgeyi yeni bir adla kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Açıklama: Bu, belgeyi yeni bir dosya adıyla kaydeder, böylece orijinalinden kolayca ayırt edebilirsiniz.

## Çözüm

Aspose.Words for .NET kullanarak bir Word belgesindeki içerik denetimlerini değiştirmek, ilgili adımları anladığınızda basittir. Metni güncelliyor, açılır seçimleri değiştiriyor veya görselleri değiştiriyor olun, Aspose.Words bu görevler için sağlam bir API sağlar. Bu öğreticiyi izleyerek belgenizin yapılandırılmış içerik denetimlerini etkili bir şekilde yönetebilir ve özelleştirebilir, belgelerinizi daha dinamik ve ihtiyaçlarınıza göre uyarlanmış hale getirebilirsiniz.

## SSS

1. Yapılandırılmış Belge Etiketi (SDT) Nedir?

SDT'ler, metin kutuları, açılır listeler veya resimler gibi belge içeriğini yönetmeye ve biçimlendirmeye yardımcı olan Word belgelerindeki öğelerdir.

2. SDT'ye yeni bir açılır liste öğesi nasıl ekleyebilirim?

Yeni bir öğe eklemek için şunu kullanın: `ListItems` özellik ve yeni bir tane ekle `SdtListItem` koleksiyona.

3. Bir belgeden SDT'leri kaldırmak için Aspose.Words'ü kullanabilir miyim?

Evet, belgenin düğümlerine erişip istediğiniz SDT'yi silerek SDT'leri kaldırabilirsiniz.

4. Diğer öğelerin içine yerleştirilmiş SDT'leri nasıl işlerim?

Kullanın `GetChildNodes` İç içe geçmiş SDT'lere erişmek için uygun parametrelere sahip yöntem.

5. Değiştirmem gereken SDT belgede görünmüyorsa ne yapmalıyım?

SDT'nin gizli veya korumalı olmadığından emin olun. Belge ayarlarını kontrol edin ve kodunuzun SDT türünü doğru şekilde hedeflediğinden emin olun.


### Aspose.Words for .NET kullanarak İçerik Denetimlerini Değiştirmek için örnek kaynak kodu 

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

İşte bu kadar! Aspose.Words for .NET kullanarak Word belgenizdeki farklı içerik denetimlerini başarıyla değiştirdiniz.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}