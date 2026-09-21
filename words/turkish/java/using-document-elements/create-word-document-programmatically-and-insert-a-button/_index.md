---
category: general
date: 2026-09-21
description: Word belgesini programlı olarak oluşturun ve DocumentBuilder kullanarak
  Word belgesini kaydet düğmesini, komut düğmesi kelimesini eklemeyi ve komut düğmesi
  başlığını ayarlamayı öğrenin.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: tr
lastmod: 2026-09-21
og_description: Aspose.Words ile programlı olarak Word belgesi oluşturun. Word belgesini
  kaydet düğmesi, komut düğmesi ekleme, komut düğmesi başlığını ayarlama ve etkileşimli
  formlar için DocumentBuilder kullanımını öğrenin.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Word belgesini programlı olarak oluştur ve bir düğme ekle
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Word belgesini programlı olarak oluştur ve bir düğme ekle
url: /tr/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programlı olarak Word belgesi oluşturma ve bir düğme ekleme

Programlı olarak **word belgesi oluşturmanız** gerektiğinde, Aspose.Words, CommandButton gibi etkileşimli denetimler eklemenizi sağlayan akıcı bir API sunar. Bu öğreticide ayrıca **DocumentBuilder nasıl kullanılır**, **word belgesi düğmesi nasıl kaydedilir** ve **komut düğmesi başlığı nasıl ayarlanır** açıklanıyor, böylece düğme .docx dosyası içinde tam olarak beklediğiniz gibi görünür.

Şunları öğreneceksiniz:

* `Document` ile boş bir belge başlatma.
* Belgeyi düzenlemek için `DocumentBuilder` ile çalışma.
* **CommandButton** ekleme (`insert command button word`).
* Düğmenin adını ve görünen başlığını ayarlama (`set command button caption`).
* Sonucu diske kaydetme (`save word document button`).

Adımlar, C# kullanan .NET geliştiricileri ve en yeni Aspose.Words for .NET (v24.10) için hazırlanmıştır. Aspose.Words dışındaki ek NuGet paketlerine ihtiyaç yoktur.

---

## Başlamadan Önce Gerekenler

| Gereklilik | Açıklama |
|------------|----------|
| Visual Studio 2022 (veya herhangi bir C# IDE) | Örnek kodu derlemek ve çalıştırmak için. |
| .NET 6.0 SDK veya daha yeni bir sürüm | Örneğin çalışma zamanını sağlar. |
| Aspose.Words for .NET (v24.10 veya daha yeni) | **Programlı olarak word belgesi oluşturmanıza** ve form denetimlerini yönetmenize olanak tanıyan kütüphane. |
| C# ve OOP kavramlarına temel aşinalık | Kod akışını anlamak için gereklidir. |

Aspose.Words’u NuGet üzerinden şu şekilde kurabilirsiniz:

```bash
dotnet add package Aspose.Words
```

---

## Programlı olarak word belgesi oluşturma

İlk adım, boş bir `Document` nesnesi oluşturmaktır. Bu nesne, tüm Word dosyasını bellekte temsil eder.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Programlı olarak belge oluşturmak, paragraf, tablo veya etkileşimli denetimler ekleyebileceğiniz temiz bir tuval sağlar.  

---

## DocumentBuilder nasıl kullanılır

`DocumentBuilder`, bir `Document` üzerinde düzenleme yapmanın temel sınıfıdır. Metin, resim ve form alanları eklemek için yöntemler sunar. Bu öğreticide bir CommandButton yerleştirmek için kullanıyoruz.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder, mevcut ekleme konumunu işaret eden dahili bir imleç tutar. Varsayılan olarak, ilk bölümün başında başlar; bu örnek için idealdir.

---

## Insert command button word

Aspose.Words, bir CommandButton’u ActiveX denetimi olarak ele alır. `InsertForms2OleControl` yöntemi, daha sonra bir düğme olarak yapılandıracağımız genel bir OLE denetimi oluşturur.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Bu noktada denetim belgede bulunur ancak türünü tanımlayana kadar görsel bir temsili yoktur.

---

## Set command button caption

Şimdi OLE denetimine CommandButton gibi davranmasını ve dostça bir etiket almasını söylüyoruz.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

**Komut düğmesi başlığını** ayarlamak çok önemlidir; çünkü Word bu metni düğme yüzeyinde gösterir. `SetCaption` çağrısını atlamanız durumunda düğme genel bir etiketle görünür.

---

## Save word document button

Son olarak belgeyi diske kalıcı olarak kaydedin. `Save` yöntemi, yeni eklenen düğmeyi de içeren tüm Word paketini bir .docx dosyasına yazar.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

`CommandButton.docx` dosyası artık **Submit** etiketiyle tam işlevsel bir düğme içerir. Kullanıcı Microsoft Word’de dosyayı açıp düğmeye tıkladığında, daha sonra VBA ile bağlayabileceğiniz varsayılan eylem tetiklenir.

---

## Tam çalışan örnek

Aşağıda, belge oluşturma aşamasından düğmeyi kaydetmeye kadar tüm iş akışını gösteren, kopyalayıp yapıştırıp çalıştırabileceğiniz tam program yer almaktadır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Beklenen sonuç**

* Belirttiğiniz yolda `CommandButton.docx` adlı bir dosya oluşturulur.
* Microsoft Word’de dosyayı açtığınızda ilk sayfada tek bir **Submit** düğmesi görülür.
* Düğme seçilebilir, yeniden boyutlandırılabilir veya Word’ün **Developer** sekmesinden bir makroya bağlanabilir.

---

## Yaygın sorular ve kenar‑durum yönetimi

| Soru | Cevap |
|------|-------|
| *Birden fazla düğmeye ihtiyacım olursa ne yapmalıyım?* | Farklı ad ve başlıklarla adım 3–6’yı tekrarlayın. Her düğmenin benzersiz bir `SetName` değeri olmalıdır. |
| *Düğmenin boyutunu ayarlayabilir miyim?* | Evet. Denetimi ekledikten sonra `OleFormat` nesnesi üzerinden `Width` ve `Height` özelliklerini değiştirebilirsiniz. |
| *Düğme tüm Word sürümlerinde çalışır mı?* | ActiveX denetimleri, Windows üzerindeki masaüstü Word sürümünde desteklenir. Word Online veya macOS’da görüntülenmez. |
| *Bir tıklama işleyicisi nasıl eklenir?* | Düğmenin adını (`btnSubmit`) referans alan bir VBA kodu yazmanız gerekir. VBA makrosu `doc.VbaProject` kullanılarak gömülebilir. |
| *Düğmeyi bir tablo hücresine eklemem gerekirse?* | `InsertForms2OleControl` çağırmadan önce builder’ın imlecini istenen hücreye (`builder.MoveTo(cell.FirstParagraph)`) taşıyın. |

---

## Pro ipuçları

* **Pro ipucu:** Her zaman `SetName` ile anlamlı bir ad verin. Bu, VBA otomasyonunu basitleştirir ve hata ayıklamayı kolaylaştırır.
* **Dikkat:** `SetControlType` çağrısını unutmayın. Bu çağrı olmadan OLE nesnesi, tıklanabilir bir düğme yerine genel bir yer tutucu olarak görünür.
* **Performans ipucu:** Döngü içinde çok sayıda belge üretiyorsanız, tek bir `DocumentBuilder` örneğini yeniden kullanın ve her eklemeden önce `builder.MoveToDocumentEnd()` çağırarak gereksiz imleç sıfırlamalarını önleyin.

---

## Sonraki adımlar

Artık **programlı olarak word belgesi oluşturmayı**, **command button word eklemeyi**, **komut düğmesi başlığını ayarlamayı** ve **word belgesi düğmesini kaydetmeyi** bildiğinize göre daha gelişmiş senaryoları keşfedebilirsiniz:

* Kullanıcı girişi için **TextFormField** denetimleri ekleyin.
* Düğmeleri **MacroButton** alanlarıyla birleştirerek VBA’yı doğrudan çalıştırın.
* **DocumentBuilder.InsertImage** kullanarak düğmelerinize simgeler yerleştirin.
* ASP.NET ile Word formları oluşturmak için bütünleştirin


## Bir Sonraki Öğrenmeniz Gerekenler


Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanız ve projelerinizde alternatif uygulama yaklaşımlarını keşfetmeniz için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Yeni Word Belgesi Oluştur](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Aspose.Words for .NET ile Word Belgesi Oluştur](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Aspose.Words ile Word Belgesine Satır İçi Görsel Ekle](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}