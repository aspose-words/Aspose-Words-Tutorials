---
title: افزودن فیلد فرم چک‌باکس به یک سند Word با Aspose.Words for .NET
weight: 210
limit:
description: بیاموزید چگونه به‌صورت برنامه‌نویسی یک فیلد فرم چک‌باکس را به یک سند Word جدید با استفاده از Aspose.Words for .NET اضافه کنید و فایل را ذخیره کنید.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# افزودن فیلد فرم چک‌باکس به یک سند Word با Aspose.Words
این آموزش نشان می‌دهد چگونه یک سند Word تازه ایجاد کنید و از DocumentBuilder در Aspose.Words for .NET برای وارد کردن یک فیلد فرم چک‌باکس استفاده کنید. با دنبال کردن مراحل، کد دقیق مورد نیاز برای افزودن عنصر تعاملی و سپس ذخیره سند در یک فایل را خواهید دید. این یک روش سریع برای ساخت برنامه‌نویسی فایل‌های Word با فرم ساده است.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: آرگومان چهارم (0) در InsertCheckBox چه معنایی دارد؟**
A: این مقدار اندازهٔ بصری چک‌باکس را بر حسب پوینت تعیین می‌کند؛ مقدار 0 به Aspose.Words می‌گوید از اندازهٔ پیش‌فرض استفاده کند.

**Q: آیا می‌توانم بیش از یک چک‌باکس با همان نام وارد کنم؟**
A: خیر – هر نام فیلد فرم باید یکتا باشد؛ تلاش برای وارد کردن چک‌باکس دیگری با نام "CheckBox" منجر به پرتاب ArgumentException می‌شود.

**Q: چگونه می‌توانم یک چک‌باکس را به یک سند موجود اضافه کنم نه به یک سند جدید؟**
A: ابتدا سند را بارگذاری کنید (مثلاً `Document doc = new Document("Existing.docx");`) سپس برای آن سند یک DocumentBuilder ایجاد کنید و `InsertCheckBox` را در موقعیت دلخواه مکان‌نما فراخوانی کنید.

**Q: چگونه می‌توانم وضعیت چک‌باکس وارد شده را پس از ذخیره سند بخوانم؟**
A: فیلد فرم را با استفاده از `doc.Range.FormFields["CheckBox"]` دریافت کنید و ویژگی `Checked` آن را بررسی کنید تا ببینید آیا علامت‌خورده بوده است یا نه.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}