---
title: Aspose.Words for .NET kullanarak Word belgesinde Döndürülmüş Metin Tablosu oluşturun
weight: 110
limit:
description: Aspose.Words for .NET kullanarak sabit sütun genişliklerine, döndürülmüş metne, kesin satır yüksekliğine ve doldurulmuş hücrelere sahip bir Word tablosu oluşturmayı öğrenin.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aspose.Words for .NET kullanarak sabit sütun genişliklerine, döndürülmüş
    metne, kesin satır yüksekliğine ve doldurulmuş hücrelere sahip bir Word tablosu
    oluşturmayı öğrenin.
  headline: Aspose.Words for .NET kullanarak Word belgesinde Döndürülmüş Metin Tablosu
    oluşturun
  type: TechArticle
- description: Aspose.Words for .NET kullanarak sabit sütun genişliklerine, döndürülmüş
    metne, kesin satır yüksekliğine ve doldurulmuş hücrelere sahip bir Word tablosu
    oluşturmayı öğrenin.
  name: Aspose.Words for .NET kullanarak Word belgesinde Döndürülmüş Metin Tablosu
    oluşturun
  steps:
  - name: Tabloyu oluşturmak için kullanılacak yeni bir Document ve bir DocumentBuilder
      örneği oluşturun.
    text: Tabloyu oluşturmak için kullanılacak yeni bir Document ve bir DocumentBuilder
      örneği oluşturun.
  - name: Yeni bir tablo başlatın, ilk hücreyi ekleyin ve sütun genişliklerini otomatik
      ayarlamayı önleyecek şekilde sabitleyin.
    text: Yeni bir tablo başlatın, ilk hücreyi ekleyin ve sütun genişliklerini otomatik
      ayarlamayı önleyecek şekilde sabitleyin.
  - name: Mevcut hücredeki içeriği dikey olarak ortalayın ve birinci satırın birinci
      hücresinin metnini yazın.
    text: Mevcut hücredeki içeriği dikey olarak ortalayın ve birinci satırın birinci
      hücresinin metnini yazın.
  - name: Birinci satırın ikinci hücresini ekleyin ve metnini yazın.
    text: Birinci satırın ikinci hücresini ekleyin ve metnini yazın.
  - name: Birinci satırı kapatın, düzenini tamamlayın.
    text: Birinci satırı kapatın, düzenini tamamlayın.
  - name: İkinci satırın ilk hücresini başlatın, satır yüksekliğini tam olarak 100
      puan olarak ayarlayın, metni yukarı doğru döndürün ve hücrenin metnini yazın.
    text: İkinci satırın ilk hücresini başlatın, satır yüksekliğini tam olarak 100
      puan olarak ayarlayın, metni yukarı doğru döndürün ve hücrenin metnini yazın.
  - name: İkinci satırın ikinci hücresini ekleyin, metnini aşağı doğru döndürün ve
      hücrenin metnini yazın.
    text: İkinci satırın ikinci hücresini ekleyin, metnini aşağı doğru döndürün ve
      hücrenin metnini yazın.
  - name: İkinci satırı kapatın, tablonun ikinci satırını tamamlayın.
    text: İkinci satırı kapatın, tablonun ikinci satırını tamamlayın.
  - name: Tablo oluşturmayı sonlandırın, tablo yapısını sabitleyin.
    text: Tablo oluşturmayı sonlandırın, tablo yapısını sabitleyin.
  - name: Tamamlanan belgeyi bir .docx dosyasına kaydedin.
    text: Tamamlanan belgeyi bir .docx dosyasına kaydedin.
  type: HowTo
- questions:
  - answer: Sütun genişliklerini sabitledikten sonra, bir sonraki hücreyi eklemeden
      önce `builder.CellFormat.Width = <valueInPoints>;` kullanarak her hücreye bir
      genişlik atayın; tablo bu kesin genişlikleri koruyacaktır.
    question: '`table.AutoFit(AutoFitBehavior.FixedColumnWidths)` çağrısından sonra
      belirli sütun genişliklerini nasıl ayarlarım?'
  - answer: '`builder.CellFormat.VerticalAlignment` hücre düzeyinde bir ayardır, bu
      yüzden ikinci satırdaki hücreler için (ör. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) içeriklerini yazmadan önce tekrar ayarlamanız
      gerekir.'
    question: Dikey hizalama neden yalnızca birinci satırı etkiliyor ve ikinci satırı
      etkilemiyor?
  - answer: Evet—her `builder.EndRow();` çağrısından önce `builder.RowFormat.Height`
      ve `builder.RowFormat.HeightRule = HeightRule.Exactly` ayarlayın; bir sonraki
      satır farklı bir yükseklik değerine sahip olabilir.
    question: Her satıra farklı bir kesin yükseklik verebilir miyim, eğer verebilirsem
      nasıl?
  - answer: Bir sonraki hücreye yazmadan önce `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      atayarak yönlendirmeyi sıfırlayın.
    question: '`TextOrientation.Upward` veya `Downward` kullandıktan sonra metin yönlendirmesini
      varsayılanına nasıl geri döndürürüm?'
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Aspose.Words ile Word'de Döndürülmüş Metin Tablosu oluşturun
og_description: Dikey olarak döndürülmüş metin ve tam satır yüksekliğine sahip sabit genişlikte bir tablo oluşturmak için adım adım kod.
og_image_alt: Aspose.Words for .NET kullanılarak oluşturulmuş, sabit sütun genişliklerine, hücrelerde döndürülmüş metne ve tanımlı satır yüksekliğine sahip bir tablo içeren Word belgesinin ekran görüntüsü
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word belgesinde Döndürülmüş Metin Tablosu oluşturun
Bu öğreticide, sabit genişlikte sütunlara, tam yüksekliğe sahip satırlara ve hücre metni dikey olarak döndürülmüş bir tablo ekleyerek bir Word belgesi oluşturmayı gösterir. Dikey hizalamayı ayarlamayı, metin yönlendirmesini uygulamayı, her hücreyi içerikle doldurmayı ve sonunda belgeyi kaydetmeyi—tümü Aspose.Words for .NET ile öğreneceksiniz.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` çağrısından sonra belirli sütun genişliklerini nasıl ayarlarım?**  
A: Sütun genişliklerini sabitledikten sonra, bir sonraki hücreyi eklemeden önce `builder.CellFormat.Width = <valueInPoints>;` kullanarak her hücreye bir genişlik atayın; tablo bu kesin genişlikleri koruyacaktır.

**Q: Dikey hizalama neden yalnızca birinci satırı etkiliyor ve ikinci satırı etkilemiyor?**  
A: `builder.CellFormat.VerticalAlignment` hücre düzeyinde bir ayardır, bu yüzden ikinci satırdaki hücreler için (ör. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) içeriklerini yazmadan önce tekrar ayarlamanız gerekir.

**Q: Her satıra farklı bir kesin yükseklik verebilir miyim, eğer verebilirsem nasıl?**  
A: Evet—her `builder.EndRow();` çağrısından önce `builder.RowFormat.Height` ve `builder.RowFormat.HeightRule = HeightRule.Exactly` ayarlayın; bir sonraki satır farklı bir yükseklik değerine sahip olabilir.

**Q: `TextOrientation.Upward` veya `Downward` kullandıktan sonra metin yönlendirmesini varsayılanına nasıl geri döndürürüm?**  
A: Bir sonraki hücreye yazmadan önce `builder.CellFormat.Orientation = TextOrientation.Horizontal;` atayarak yönlendirmeyi sıfırlayın.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}