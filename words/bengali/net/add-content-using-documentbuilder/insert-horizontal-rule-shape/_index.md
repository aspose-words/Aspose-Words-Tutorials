---
title: Aspose.Words for .NET ব্যবহার করে Word ডকুমেন্টে Horizontal Rule Shape সন্নিবেশ করুন।
weight: 110
limit:
description: Aspose.Words for .NET দিয়ে Word ডকুমেন্টে horizontal rule শেপ সন্নিবেশ করার ধাপে ধাপে গাইড।
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET ব্যবহার করে Word ডকুমেন্টে Horizontal Rule Shape সন্নিবেশ করুন।
Aspose.Words for .NET ব্যবহার করে কীভাবে একটি Word ডকুমেন্টে horizontal rule শেপ সন্নিবেশ করা যায় তা শিখুন। এই টিউটোরিয়ালটি আপনাকে নতুন ডকুমেন্ট তৈরি করা, একটি টেক্সট লাইন যোগ করা, DocumentBuilder দিয়ে একটি horizontal rule শেপ স্থাপন করা এবং ফাইলটি সংরক্ষণ করার মাধ্যমে গাইড করে। horizontal rule আপনার কন্টেন্টের জন্য একটি সহজ ভিজ্যুয়াল সেপারেটর প্রদান করে।

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: আমি কি DocumentBuilder.InsertHorizontalRule() দিয়ে সন্নিবেশ করা horizontal rule এর চেহারা (রঙ, পুরুত্ব) পরিবর্তন করতে পারি?**
A: InsertHorizontalRule ডিফল্ট ফরম্যাটিং সহ একটি বিল্ট‑ইন horizontal line শেপ তৈরি করে; এর চেহারা পরিবর্তন করতে আপনাকে সন্নিবেশ করা Shape অবজেক্ট (builder.CurrentParagraph.LastChild) পুনরুদ্ধার করে তার LineFormat প্রপার্টি সমন্বয় করতে হবে।

**Q: যদি আমি একটি প্যারাগ্রাফের পরে যা ইতিমধ্যে লাইন ব্রেক দিয়ে শেষ হয়েছে, InsertHorizontalRule() কল করি, তাহলে কী হয়?**
A: এই মেথডটি রুলটি একটি আলাদা প্যারাগ্রাফ হিসেবে সন্নিবেশ করে, তাই পূর্বের লাইন ব্রেক কেবল রুলের আগে একটি খালি প্যারাগ্রাফ তৈরি করে; রুলটি এখনও নিজস্ব লাইনে প্রদর্শিত হবে।

**Q: DocumentBuilder ব্যবহার করে একই ডকুমেন্টে একাধিক horizontal rule সন্নিবেশ করা সম্ভব কি?**
A: হ্যাঁ, builder.InsertHorizontalRule() প্রতিটি কল বর্তমান কর্সর অবস্থানে একটি নতুন horizontal rule শেপ যোগ করে, যা ডকুমেন্ট জুড়ে একাধিক রুলের অনুমতি দেয়।

**Q: DOCX ছাড়া PDF এর মতো অন্যান্য ফরম্যাটে ডকুমেন্ট সংরক্ষণ করার সময় InsertHorizontalRule() কাজ করে কি?**
A: horizontal rule ডকুমেন্ট মডেলে একটি শেপ হিসেবে সংরক্ষিত হয়, তাই আপনি যখন PDF, XPS বা অন্যান্য সমর্থিত ফরম্যাটে সংরক্ষণ করেন, রুলটি আউটপুটে সঠিকভাবে রেন্ডার হয়।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}