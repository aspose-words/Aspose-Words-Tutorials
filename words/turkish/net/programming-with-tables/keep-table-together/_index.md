---
"description": "Aspose.Words for .NET kullanarak Word belgelerinde tabloların sayfalar arasında dağılmasını nasıl önleyeceğinizi öğrenin. Profesyonel, okunabilir belgeler elde etmek için kılavuzumuzu izleyin."
"linktitle": "Masayı Bir Arada Tutun"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Masayı Bir Arada Tutun"
"url": "/tr/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masayı Bir Arada Tutun

## giriiş

Word belgenizdeki bir tablonun iki sayfaya bölündüğünü gördüğünüzde hiç hayal kırıklığına uğradınız mı? Sanki dikkatlice düzenlenmiş bilgileriniz aniden yarı yolda ara vermeye karar vermiş gibi! Tabloları tek bir sayfada bir arada tutmak okunabilirlik ve sunum için çok önemlidir. İster bir rapor, ister bir proje teklifi veya sadece kişisel bir belge için olsun, tabloların bölünmesi oldukça sarsıcı olabilir. Bizim için şanslıyız ki, .NET için Aspose.Words bu sorunu çözmek için akıllıca bir yola sahip. Bu eğitimde, tablolarınızı bozulmadan ve keskin bir şekilde tutmak için atmanız gereken adımları ele alacağız. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET - Eğer henüz yüklemediyseniz, şu adresten indirebilirsiniz: [Burada](https://releases.aspose.com/words/net/).
2. Tablo İçeren Bir Word Belgesi - Birden fazla sayfaya yayılan bir tablo içeren örnek bir belge üzerinde çalışacağız.
3. Temel C# Bilgisi - Bu eğitim, C# programlama konusunda temel bir anlayışa sahip olduğunuzu varsayar.

## Ad Alanlarını İçe Aktar

Öncelikle gerekli ad alanlarını içe aktaralım. Bu bize .NET için Aspose.Words'den ihtiyacımız olan sınıflara ve yöntemlere erişim sağlayacak.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

İşlemi kolay, sindirilebilir adımlara bölelim. Belgemizi yükleyerek başlayacağız ve tablonun bir arada kaldığı güncellenmiş belgeyi kaydederek bitireceğiz.

## Adım 1: Belgeyi Yükleyin

Bir Word belgesiyle çalışmak için öncelikle onu yüklememiz gerekir. `Document` Bunun için bir sınıf.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Adım 2: Tabloya Erişim

Sonra, bir arada tutmak istediğimiz tabloyu almamız gerekiyor. Belgedeki ilk tablo olduğunu varsayacağız.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Adım 3: Paragraflar için KeepWithNext'i ayarlayın

Tablonun sayfalar arasında dağılmasını önlemek için, `KeepWithNext` Tablodaki her paragraf için özellik, son satırdaki son paragraflar hariç.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Adım 4: Belgeyi Kaydedin

Son olarak güncellenen belgeyi kaydediyoruz. Bu, değişikliklerimizi uygulayacak ve tablonun tek sayfada bir arada kalmasını sağlayacaktır.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Çözüm

İşte karşınızda! Sadece birkaç satır kodla, Word belgelerinizdeki sayfalar arasında tablolarınızın bölünmesini önleyebilirsiniz. Bu basit ama etkili çözüm, tablolarınızın düzenli ve profesyonel kalmasını sağlayarak belgelerinizin okunabilirliğini artırır. .NET için Aspose.Words, bu tür biçimlendirme sorunlarıyla başa çıkmayı kolaylaştırır ve harika içerik oluşturmaya odaklanmanızı sağlar.

## SSS

### Bu yöntemi kullanarak birden fazla tabloyu bir arada tutabilir miyim?  
Evet, belgenizdeki her tabloda yineleme yaparak aynı mantığı birden fazla tabloya uygulayabilirsiniz.

### Ya tablom bir sayfaya sığmayacak kadar büyük olursa?  
Bir tablo tek bir sayfaya sığmayacak kadar büyükse, yine de sayfalara yayılacaktır. Bu yöntem, daha küçük tabloların bölünmeden sağlam kalmasını sağlar.

### Bunu bir belgedeki tüm tablolar için otomatikleştirmenin bir yolu var mı?  
Evet, belgenizdeki tüm tablolarda dolaşabilir ve `KeepWithNext` her paragrafa bir özellik.

### Aspose.Words for .NET için ücretli bir lisansa ihtiyacım var mı?  
Ücretsiz denemeye şuradan başlayabilirsiniz: [Burada](https://releases.aspose.com/), ancak tam işlevsellik için ücretli bir lisans önerilir.

### Tabloyu bir arada tutarken başka biçimlendirmeler uygulayabilir miyim?  
Kesinlikle! Tablonuzu tek bir sayfada bir arada kalmasını sağlayarak ihtiyacınıza göre biçimlendirebilirsiniz.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}