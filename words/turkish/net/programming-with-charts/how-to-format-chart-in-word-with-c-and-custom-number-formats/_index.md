---
category: general
date: 2026-10-13
description: C# kullanarak Word’de bir grafiği, eksenlerine para birimi gibi özel
  bir sayı formatı uygulayarak nasıl biçimlendireceğiniz. Adım adım kod örneği dahil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: tr
lastmod: 2026-10-13
og_description: C# ile Word’de grafik biçimlendirme, grafik eksenlerine özel bir sayı
  formatı uygulamanızı sağlar; böylece değerler para birimi, yüzde ya da ihtiyacınız
  olan herhangi bir desen olarak görünür. Adım adım kılavuzu izleyin.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: C# ile Word’te grafik nasıl biçimlendirilir – özel sayı formatları
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: C# ve özel sayı formatlarıyla Word’de grafiği nasıl biçimlendirilir
url: /tr/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de Grafik Nasıl Biçimlendirilir C# ve Özel Sayı Formatlarıyla

Word'de grafik biçimlendirme, verileri profesyonel bir şekilde sunmanız gerektiğinde yaygın bir gereksinimdir. Bu rehber, **Aspose.Words for .NET** kullanarak bir grafiğin eksenine özel bir sayı formatı uygulamanın nasıl yapılacağını gösterir, böylece değerler tam olarak beklediğiniz gibi görünür.

Bir DOCX dosyasını nasıl yükleyeceğinizi, ilk grafiği nasıl bulacağınızı, mevcut formatı nasıl okuyacağınızı ve ardından iki ondalık basamaklı para birimi gibi yeni bir desen nasıl ayarlayacağınızı öğreneceksiniz. Eğitim ayrıca ek seriler için grafik eksen formatını nasıl değiştireceğinizi ve gerektiğinde formatı nasıl sıfırlayacağınızı da kapsar.

## Önkoşullar

* .NET 6.0 veya daha yeni bir sürüm yüklü  
* Visual Studio 2022 (veya .NET'i destekleyen herhangi bir IDE) projesi  
* **Aspose.Words for .NET** NuGet paketi (`Aspose.Words`)  
* En az bir grafik içeren bir Word belgesi (`input.docx`)

Paketi aşağıdaki komutla ekleyebilirsiniz:

```bash
dotnet add package Aspose.Words
```

## Aspose.Words Kullanarak Word'de Grafik Nasıl Biçimlendirilir

Aşağıdaki tam program, **grafik** eksen değerlerini biçimlendirmek için gereken tüm adımları gösterir. Dosyayı `Program.cs` olarak kaydedin ve komut satırından ya da IDE'nizden çalıştırın.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Her Adımın Açıklaması

| Adım | Neden Önemli | Ana kod |
|------|----------------|----------|
| **Belgeyi Yükle** | Word dosyasıyla çalışmak için bir `Document` nesnesine ihtiyacınız var. | `new Document("input.docx")` |
| **Grafiği Al** | `Chart` nesneleri `Shape` düğümleri olarak depolanır; tip dönüşümü, grafik‑özel API'leri kullanmanıza olanak tanır. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **X‑değerlerine Eriş** | Eksen biçimlendirmesi, bir veri serisinin değer koleksiyonuna uygulanır. | `chart.ChartData.Series[0].XValues` |
| **Mevcut Formatı Oku** | Mevcut `FormatCode`'u bilmek, onu değiştirip değiştirmeyeceğinize karar vermenize yardımcı olur. | `xValues.FormatCode` |
| **Özel Format Ayarla** | `FormatCode` özelliği, para birimi, yüzde, tarih vb. gibi Excel uyumlu herhangi bir deseni kabul eder. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Belgeyi Kaydet** | Değişiklikleri kalıcı hale getirmek, yeni eksen formatını DOCX dosyasına yazar. | `doc.Save("output_formatted.docx")` |

Programı çalıştırmak `output_formatted.docx` dosyasını üretir. Word'de açtığınızda, grafiğin X‑eksen değerlerinin **$1,234.00**, **$2,345.00**, … şeklinde, düz sayılar yerine görüntülendiğini göreceksiniz.

## Grafik Eksenine Özel Sayı Formatı Uygulama

Y‑eksenine veya ek serilere **özel sayı formatı uygulamanız** gerekiyorsa, süreç aynı—sadece farklı bir koleksiyona hedefleyin:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro ipucu:** Biçim dizesi içinde çift tırnak kullanarak literal karakterler ekleyin (ör. para birimi için `"$"`). Yukarıda gösterildiği gibi tırnakları kaçırın.

## Özel sayı formatı kelimesi – Word'ün yerel ayarını yönetme

Word, sayı formatlarını yorumlarken belgenin yerel ayarına saygı gösterir. Belge ABD dışı bir yerel ayar kullanıyorsa, biçim dizesini ayarlamanız gerekebilir:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Almanca dil ayarlarına sahip bir belgede formatı test etmek, değerlerin **€ 1.234,00** olarak göründüğünü doğrular.

## Grafik Özelliklerini Programlı Olarak Nasıl Ayarlarsınız

Eksen biçimlendirmesinin ötesinde, genellikle **grafik** başlıkları, lejandları veya veri etiketlerini ayarlamak istersiniz. İşte ekseni biçimlendirdikten sonra bir grafik başlığı ayarlamayı gösteren hızlı bir kod parçacığı:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Bunu özel sayı formatı ile birleştirerek, raporlamaya hazır, tamamen işlenmiş bir grafik elde edersiniz.

## Kullanıcı Girişine Göre Grafik Eksen Formatını Dinamik Olarak Değiştirme

Gerçek dünyadaki uygulamalarda, kullanıcıların çalışma zamanında bir format seçmesine izin verebilirsiniz. Aşağıdaki yöntem, biçimlendirme mantığını kapsüller:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

`SetAxisFormat(chart, 0, "\"$\"#,##0.00")` çağırarak para birimi, `SetAxisFormat(chart, 0, "0%")` çağırarak yüzde formatı kullanabilirsiniz. Bu yaklaşım, ana kodunuzu temiz tutar ve gelecekteki genişletmelere destek verir.

## Kenar Durumları ve Yaygın Tuzaklar

| Durum | Dikkat Edilmesi Gereken | Önerilen Çözüm |
|-----------|-------------------|---------------|
| Belge **grafik içermiyor** | `GetChild` `null` döndürür, bu da tip dönüşüm hatasına neden olur. | Tip dönüşümünden önce `null` kontrol edin (örneğe bakın). |
| Aynı belgede birden fazla grafik | Kod her zaman ilk grafiği alır (`index 0`). | `doc.GetChildNodes(NodeType.Shape, true)` üzerinden döngü yapın ve `ShapeType.Chart` ile filtreleyin. |
| Seriler **X‑değerleri olmadan** (ör. pasta grafikleri) | `XValues`'a erişmek `ArgumentOutOfRangeException` hatası atabilir. | Biçimlendirmeden önce `Series[i].XValues`'ın boş olmadığını doğrulayın. |
| Yerel ayar uyumsuzluğu | Para birimi simgesi yanlış görünebilir. | `xValues.FormatCode`'u uygun yerel ayar sembolleriyle açıkça ayarlayın. |

## Beklenen Çıktı

Örnek programı çalıştırdıktan sonra **output_formatted.docx** dosyasını açın. Grafiğin X‑ekseninde, seçilen özel formatta sayılar görüntülenmelidir. Para birimi örneği için, eksen etiketleri şu şekilde görünür:

```
$1,000.00
$2,000.00
$3,000.00
```

Yüzde formatını Y‑değerlerine uyguladıysanız, Y‑eksen etiketleri şu şekilde görünür:

```
10%
20%
30%
```

## Sonuç

Bu eğitim, C# ile Word'de **grafiği nasıl biçimlendireceğinizi** gösterdi; eksen değerlerine **özel bir sayı formatı uygulayarak**. Artık para birimi, yüzde veya başka herhangi bir sayısal desen ayarlamak için yeniden kullanılabilir bir deseniniz ve yerel ayarları, birden fazla seriyi ve dinamik kullanıcı girişini yönetmek için rehberiniz var.

Sonraki adımda, `ChartRenderer` kullanarak **grafik** başlıklarını, veri etiketlerini ayarlamayı veya grafiği bir görüntü olarak dışa aktarmayı keşfedebilirsiniz. Bu konular, burada ele alınan kavramların üzerine doğrudan inşa edilir ve tamamen otomatik raporlama çözümleri oluşturmanıza yardımcı olur.

---

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki eğitimler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalı tam çalışan kod örnekleri içerir.

- [Grafikte Eksen İçin Sayı Formatı](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Grafikte Veri Etiketi Sayısını Biçimlendir](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Word Çizgi Grafiklerinde İkincil X‑Eksenini Biçimlendir ve Görüntü Birimlerini Binlere Ayarla Aspose.Words for .NET Kullanarak](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}