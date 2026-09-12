---
category: general
date: 2026-09-11
description: Mail merge aspose, bir Word şablonunu yüklemenizi ve verilerle doldurmanızı
  sağlar; belge oluşturmayı otomatikleştirerek kişiselleştirilmiş mektuplar oluşturur.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: tr
lastmod: 2026-09-11
og_description: Mail merge aspose, Word şablonunu yüklemenizi ve doldurmanızı sağlar,
  belge oluşturmayı kolaylaştırarak kişiselleştirilmiş mektupları hızlı bir şekilde
  oluşturmanızı sağlar.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail birleştirme aspose: Word şablonunu dakikalar içinde doldurun'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Aspose kullanarak posta birleştirme ile bir Word şablonunu doldurma
url: /tr/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose ile posta birleştirme (mail merge) yaparak Word şablonunu doldurma

Kişiselleştirilmiş mektupların toplu olarak oluşturulması için **mail merge aspose** yapmanız gerekiyorsa, bu kılavuz Word şablonunu nasıl yükleyeceğinizi, verilerle nasıl dolduracağınızı ve birkaç satır C# kodu ile belge oluşturmayı otomatikleştireceğinizi adım adım gösterir. İster bir posta sistemi ister bir raporlama aracı geliştirin, aşağıdaki tam örnek manuel birleştirme mantığı yazmadan kişiselleştirilmiş mektuplar oluşturmanızı sağlar.

**load word template**, düşük‑kodlu `MailMerger` sınıfını kullanma ve anonim bir veri kaynağıyla **populate word template** işlemlerini öğreneceksiniz. Eğitim sonunda, birleştirilmiş bir Word belgesi üreten, e‑posta gönderebileceğiniz, yazdırabileceğiniz veya arşivleyebileceğiniz hazır bir konsol uygulamanız olacak.

## Prerequisites

Başlamadan önce şunların yüklü olduğundan emin olun:

* .NET 6.0 SDK veya daha yeni bir sürüm  
* Geçerli bir Aspose.Words for .NET lisansı (veya ücretsiz deneme anahtarı)  
* Projenizde `Aspose.Words` NuGet paketi (versiyon 23.10 veya daha yenisi) yüklü  
* **«Name»** ve **«Age»** gibi MERGEFIELD yer tutucularını içeren bir Word dosyası (`MailMergeTemplate.docx`)  

Şablonu Microsoft Word’te *Insert → Quick Parts → Field → MergeField* yolunu izleyerek oluşturabilir ve alanları veri kaynağınızdaki özellik adlarıyla aynı şekilde adlandırabilirsiniz.

## Step 1 – Prepare the data source for the mail merge

Düşük‑kodlu birleştirme, herhangi bir enumerable koleksiyonla çalışır. Bu örnekte anonim nesnelerden oluşan bir dizi kullanıyoruz, ancak `DataTable`, POCO listesi veya bir veritabanından okunan verileri de geçirebilirsiniz.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Neden önemli:**  
Her nesnenin özellik adı (`Name`, `Age`) şablondaki bir MERGEFIELD ile aynı olmalıdır. `MailMerger` sınıfı özellikleri alanlara otomatik olarak eşler, manuel `FieldMerging` olaylarına gerek kalmaz.

## Step 2 – Load the Word template that contains MERGEFIELDs

Şablonu yüklemek `Document` sınıfı ile oldukça basittir. Yol mutlak ya da çalıştırılabilir dosyanın çalışma dizinine göre göreceli olabilir.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**İpucu:**  
Kodu Visual Studio’dan çalıştırıyorsanız, şablon dosyasının *Copy to Output Directory* özelliğini **Copy always** olarak ayarlayın. Böylece derlenmiş ikili çalıştırıldığında dosya her zaman bulunur.

## Step 3 – Create a MailMerger instance bound to the template

`MailMerger` sınıfı `Aspose.Words.LowCode` ad alanında bulunur ve veri kaynağını kabul eden tek bir `Execute` yöntemi sağlar.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**MailMerger neden kullanılmalı?**  
`MailMerger`, tekrarlayan `MailMerge.Execute` çağrılarını soyutlayarak alan algılama, veri bağlama ve belge kopyalama işlemlerini dahili olarak yönetir. Bu, **automate document generation** senaryoları için temiz, düşük‑kodlu bir çözüm sunar.

## Step 4 – Execute the low‑code merge using the prepared data

`Execute` metodunu çağırmak, içinde birleştirilmiş verilerin bulunduğu yeni bir `Document` döndürür.


## What Should You Learn Next?

Aşağıdaki eğitimler, bu kılavuzda gösterilen tekniklere dayanarak yakından ilgili konuları kapsar. Her kaynak, adım adım açıklamalar ve tam çalışan kod örnekleri içerir; böylece ek API özelliklerini öğrenebilir ve projelerinizde alternatif uygulama yaklaşımlarını keşfedebilirsiniz.

- [Rename Word Merge Fields with Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}