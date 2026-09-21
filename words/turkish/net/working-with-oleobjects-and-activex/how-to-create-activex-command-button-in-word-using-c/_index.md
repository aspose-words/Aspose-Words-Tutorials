---
category: general
date: 2026-09-21
description: Aspose.Words ve C# kullanarak bir Word belgesinde ActiveX komut düğmesi
  oluşturmayı öğrenin. Adım adım rehber, ekleme, konumlandırma ve kaydetmeyi kapsar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: tr
lastmod: 2026-09-21
og_description: C# ve Aspose.Words kullanarak bir Word belgesine ActiveX komut düğmesi
  oluşturun. Düğmeyi programlı olarak eklemek, konumlandırmak ve kaydetmek için bu
  kapsamlı öğreticiyi izleyin.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: C# ile Word’te bir ActiveX komut düğmesi oluşturma – tam rehber
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: C# kullanarak Word'de ActiveX komut düğmesi nasıl oluşturulur
url: /tr/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word'de C# Kullanarak ActiveX Komut Düğmesi Oluşturma

Bir Word dosyası içinde **ActiveX command button** oluşturmanız gerekiyorsa, bu rehber size tam adımları gösterir. Aspose.Words for .NET kullanarak düğmeyi tamamen C# kodundan ekleyebilir, konumlandırabilir ve yapılandırabilirsiniz.

ActiveX düğmesinin programatik eklenmesi, manuel UI çalışmalarını ortadan kaldırır ve formlar, raporlar veya etkileşimli şablonlar için otomatik belge oluşturmayı sağlar. Bu öğreticide **DocumentBuilder**, **InsertForms2OleControl** yöntemi ve ilgili özellikleri kullanarak tam işlevsel bir düğme oluşturmayı öğreneceksiniz.

## Gerekenler

* .NET 6.0 SDK veya daha yenisi (kod .NET Framework 4.7+ ile de çalışır)
* Aspose.Words for .NET (NuGet paketi `Aspose.Words`)
* Visual Studio 2022 veya VS Code gibi bir IDE
* C# ve Word belge kavramları hakkında temel bilgi

Ek bir Office kurulumu gerekli değildir çünkü Aspose.Words, Microsoft Word'den bağımsız çalışır.

## Adım 1: C# Projesini Kurma

Yeni bir konsol projesi oluşturun ve Aspose.Words paketini ekleyin.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` kütüphanesi, belgeyi manipüle etmek için kullanacağımız **DocumentBuilder** sınıfını sağlar.

## Adım 2: Belgeyi ve Builder'ı Başlatma

İlk kod bloğu boş bir belge ve bir `DocumentBuilder` örneği oluşturur. Bu nesne, tüm Word‑işleme işlemleri için giriş noktasıdır.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Neden önemli:** `DocumentBuilder` mevcut imleç konumunu korur, böylece sonraki eklemeler imleci yerleştirdiğiniz yerde görünür.

## Adım 3: ActiveX Komut Düğmesini Ekleme

**InsertForms2OleControl** yöntemi, istenen türde bir ActiveX kontrolü oluşturur. Burada bir `CommandButton` talep ediyor ve boyutunu puan cinsinden (200 × 30 pt) belirtiyoruz.

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Açıklama:**  
* `OleControlType.CommandButton`, Aspose.Words'e başka bir kontrol türü yerine bir düğme oluşturmasını söyler.  
* Yöntem, konumlandırma ve özellik alanlarını ortaya çıkaran bir `Forms2OleControl` nesnesi döndürür.

## Adım 4: Düğmeyi Konumlandırma ve Özelliklerini Ayarlama

Eklemeden sonra düğmeyi sayfadaki herhangi bir konuma taşıyabilir ve ona programatik bir ad ve görünen bir başlık verebilirsiniz.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Pro ipucu:** Koordinat sistemi sayfanın sol‑üst köşesinden başlar. Düğmeyi diğer form alanlarıyla hizalamak için `Left` ve `Top` değerlerini ayarlayın.

## Adım 5: Belgeyi Kaydetme

Son olarak belgeyi diske yazın. Dosya, Microsoft Word'de açıldığında etkileşimli hale gelen ActiveX düğmesini içerecek.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

`ActiveXCommandButton.docx` dosyasını Word'de açtığınızda, belirtilen konumda **Submit** etiketiyle bir düğme göreceksiniz. Word'de üzerine tıkladığınızda varsayılan komut‑düğmesi davranışı tetiklenir (daha sonra VBA veya Word eklentileriyle özelleştirebilirsiniz).

## Tam, Çalıştırılabilir Örnek

Tüm parçaları bir araya getirerek kopyalayıp yapıştırabileceğiniz ve çalıştırabileceğiniz bağımsız bir program elde edersiniz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Beklenen çıktı:** Konsol *“Document created successfully.”* mesajını yazdırır ve klasör artık `ActiveXCommandButton.docx` dosyasını içerir. Dosyayı Microsoft Word'de açtığınızda, sol kenar boşluğundan 100 pt, sayfanın üstünden 150 pt uzaklıkta konumlandırılmış tıklanabilir bir **Submit** düğmesi gösterilir.

## Yaygın Tuzaklar ve Nasıl Önlenir

| Sorun | Neden olur | Çözüm |
|-------|------------|------|
| Düğme sayfa dışına çıkıyor | `Left`/`Top` değerleri sayfa boyutlarını aşıyor | `doc.FirstSection.PageSetup.PageWidth` ve `PageHeight` kullanarak güvenli koordinatlar hesaplayın |
| Düğme Word'de görünmüyor | Belge, ActiveX kontrollerini kaldıran bir formatta kaydedildi (ör. `.txt`) | Her zaman `.docx` veya `.doc` olarak kaydedin |
| Çalışma zamanı hatası `ArgumentOutOfRangeException` | Genişlik veya yükseklik sıfır veya negatif olarak ayarlandı | `InsertForms2OleControl`'a geçirilen boyut argümanlarının pozitif sayılar olduğundan emin olun |

## Çözümü Genişletme

Düğmeyi `Enabled`, `Visible` gibi ek özellikler ayarlayarak veya VBA ile bir makro ekleyerek daha da özelleştirebilirsiniz. **Forms2OleControl** sınıfı ayrıca onay kutuları (`OleControlType.CheckBox`) veya açılır listeler (`OleControlType.ComboBox`) gibi diğer ActiveX kontrollerini eklemenize izin verir.

Bir döngü içinde birden fazla düğme oluşturmanız gerekiyorsa, ekleme mantığını bir yardımcı metoda kapsülleyin:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Sonuç

Artık C# ve Aspose.Words kullanarak bir Word belgesinde **ActiveX command button** oluşturmayı biliyorsunuz. Eğitim, projeyi kurmayı, düğmeyi `InsertForms2OleControl` ile eklemeyi, konumlandırmayı ve son dosyayı kaydetmeyi kapsadı. Bu temel sayesinde karmaşık formları otomatikleştirebilir, etkileşimli kontroller yerleştirebilir ve Word belgelerini daha büyük .NET çözümlerine entegre edebilirsiniz.

Sonra, **Aspose.Words ActiveX** form alanları, **C# DocumentBuilder** gelişmiş stil verme veya onay kutuları ve açılır listeler için **ActiveX control in Word** programatik ekleme gibi ilgili konuları keşfedin. Belirli düzen gereksinimlerinize uyacak şekilde farklı koordinatlar ve boyutlarla deneyler yapın. Kodlamanın tadını çıkarın!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu rehberde gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini öğrenmenize ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olmak için adım adım açıklamalar içeren tam çalışan kod örnekleri sunar.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}