---
title: Aspose.Words for .NET ব্যবহার করে Word ডকুমেন্টে অ্যালাইনড HTML সন্নিবেশ করুন
weight: 210
limit:
description: Aspose.Words for .NET ব্যবহার করে বাম, কেন্দ্র, অথবা ডান অ্যালাইনমেন্ট সহ র' HTML কীভাবে একটি Word ডকুমেন্টে সন্নিবেশ করা যায় শিখুন।
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET ব্যবহার করে Word ডকুমেন্টে অ্যালাইনড HTML সন্নিবেশ করুন
এই ইন্টারেক্টিভ টিউটোরিয়ালটি Aspose.Words for .NET ব্যবহার করে কীভাবে র' HTML-কে একটি Word ডকুমেন্টে এম্বেড করা যায় এবং তার অ্যালাইনমেন্ট—বাম, কেন্দ্র, অথবা ডান—নিয়ন্ত্রণ করা যায় তা দেখায়। Document এবং DocumentBuilder ব্যবহার করে, আপনি একটি HTML স্ট্রিং সন্নিবেশ করতে পারেন এবং কয়েকটি কোড লাইনে কাঙ্ক্ষিত প্যারাগ্রাফ অ্যালাইনমেন্ট প্রয়োগ করতে পারেন। যখন আপনাকে HTML ফরম্যাটিং সংরক্ষণ করতে হয় এবং কন্টেন্টটি আপনার ডকুমেন্টের মধ্যে সঠিকভাবে স্থাপন করতে হয়, তখন এই উদাহরণটি আদর্শ।

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

**Q: যদি DocumentBuilder.InsertHtml-এ পাস করা HTML স্ট্রিংয়ে এমন ট্যাগ থাকে যা Aspose.Words সমর্থন করে না, যেমন <script> বা <iframe>, তাহলে কী হয়?**
A: অসামর্থ্য ট্যাগগুলি উপেক্ষা করা হয়; Aspose.Words শুধুমাত্র যে HTML সাবসেটটি রেন্ডার করতে পারে তা পার্স করে, তাই <script>, <iframe> এবং অনুরূপ উপাদানগুলি সরিয়ে ফেলা হয়, আর বাকি বিষয়বস্তু সন্নিবেশ করা হয়।

**Q: InsertHtml ব্যবহার করার সময় ইনলাইন CSS স্টাইল (যেমন <span style=\"color:red;\">) সংরক্ষিত থাকবে কি?**
A: হ্যাঁ, InsertHtml রঙ, ফন্ট‑সাইজ এবং ব্যাকগ্রাউন্ডের মতো অনেক ইনলাইন CSS প্রপার্টি সম্মান করে এবং সেগুলিকে সংশ্লিষ্ট Word ফরম্যাটিংয়ে রূপান্তরিত করে।

**Q: InsertHtml কি স্বয়ংক্রিয়ভাবে <div> বা <h1> এর মতো ব্লক‑লেভেল উপাদানগুলির জন্য একটি নতুন প্যারাগ্রাফ তৈরি করে?**
A: ব্লক‑লেভেল উপাদানগুলি Word প্যারাগ্রাফে ম্যাপ করা হয়, তাই প্রতিটি <div>, <p>, <h1> ইত্যাদি ডকুমেন্টে একটি আলাদা প্যারাগ্রাফ হয়ে যায়।

**Q: আমি কীভাবে একটি বিদ্যমান ডকুমেন্টের শুরুতে নয়, নির্দিষ্ট স্থানে HTML সন্নিবেশ করতে পারি?**
A: InsertHtml কল করার আগে DocumentBuilder কার্সারকে কাঙ্ক্ষিত নোডে সরান (যেমন builder.MoveToDocumentEnd() অথবা builder.MoveToParagraph(index)); HTML বর্তমান কার্সার অবস্থানে সন্নিবেশ হবে।

**Q: যদি ডকুমেন্টে ইতিমধ্যে টেক্সট থাকে, তাহলে InsertHtml কল করা কি বিদ্যমান কন্টেন্ট ওভাররাইট করবে?**
A: না, InsertHtml পার্স করা HTML-কে builder-এর বর্তমান অবস্থানে সন্নিবেশ করে এবং বিদ্যমান নোডগুলি মুছে ফেলে না, যদি না আপনি স্পষ্টভাবে কার্সারকে সেই নোডে সরিয়ে নেন বা পূর্বে সেগুলি মুছে ফেলেন।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}