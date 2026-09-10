---
title: درج HTML هم‌راستا در سند Word با استفاده از Aspose.Words for .NET
weight: 210
limit:
description: یاد بگیرید چگونه HTML خام را با تراز چپ، مرکز یا راست در یک سند Word با استفاده از Aspose.Words for .NET وارد کنید.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# درج HTML هم‌راستا در سند Word با استفاده از Aspose.Words
این آموزش تعاملی نشان می‌دهد چگونه HTML خام را در یک سند Word جاسازی کنید در حالی که تراز آن را—چپ، مرکز یا راست—با استفاده از Aspose.Words for .NET کنترل می‌کنید. با بهره‌گیری از Document و DocumentBuilder می‌توانید یک رشته HTML را وارد کرده و تراز پاراگراف مورد نظر را تنها در چند خط کد اعمال کنید. این مثال زمانی که نیاز به حفظ قالب‌بندی HTML و قرار دادن دقیق محتوا در داخل سند دارید، ایده‌آل است.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: اگر رشته HTML که به DocumentBuilder.InsertHtml پاس داده می‌شود شامل برچسب‌هایی باشد که Aspose.Words پشتیبانی نمی‌کند، مانند <script> یا <iframe>، چه اتفاقی می‌افتد؟**
A: برچسب‌های پشتیبانی‌نشده نادیده گرفته می‌شوند؛ Aspose.Words فقط زیرمجموعه‌ای از HTML را که می‌تواند رندر کند تجزیه می‌کند، بنابراین <script>، <iframe> و عناصر مشابه حذف می‌شوند در حالی که بقیه محتوا درج می‌شود.

**Q: آیا استایل‌های CSS درون‌خطی (مثلاً <span style=\"color:red;\">) هنگام استفاده از InsertHtml حفظ می‌شوند؟**
A: بله، InsertHtml بسیاری از ویژگی‌های CSS درون‌خطی مانند color، font‑size و background را رعایت می‌کند و آن‌ها را به قالب‌بندی متناظر در Word تبدیل می‌نماید.

**Q: آیا InsertHtml به‌طور خودکار برای عناصر بلوکی مانند <div> یا <h1> یک پاراگراف جدید ایجاد می‌کند؟**
A: عناصر بلوکی به پاراگراف‌های Word نگاشت می‌شوند، بنابراین هر <div>، <p>، <h1> و غیره به یک پاراگراف جداگانه در سند تبدیل می‌شود.

**Q: چگونه می‌توانم HTML را در موقعیت خاصی از یک سند موجود وارد کنم به‌جای ابتدای سند؟**
A: قبل از فراخوانی InsertHtml، مکان‌نما (cursor) DocumentBuilder را به گره مورد نظر منتقل کنید (مثلاً builder.MoveToDocumentEnd() یا builder.MoveToParagraph(index))؛ HTML در موقعیت فعلی مکان‌نما درج خواهد شد.

**Q: اگر سند قبلاً شامل متن باشد، آیا فراخوانی InsertHtml محتوای موجود را بازنویسی می‌کند؟**
A: خیر، InsertHtml HTML تجزیه‌شده را در موقعیت فعلی builder وارد می‌کند بدون اینکه نودهای موجود را حذف کند، مگر این‌که پیش از آن به‌صورت صریح مکان‌نما را به آن نودها منتقل کنید یا آن‌ها را حذف کنید.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}