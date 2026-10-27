---
title: Δημιουργήστε διαγώνιο υδατογράφημα κειμένου με προσαρμοσμένη γραμματοσειρά σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
weight: 210
limit:
description: Κώδικας βήμα‑βήμα για την προσθήκη διαγώνιου υδατογραφήματος κειμένου με προσαρμοσμένη γραμματοσειρά σε αρχείο Word .docx χρησιμοποιώντας το Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Κώδικας βήμα‑βήμα για την προσθήκη διαγώνιου υδατογραφήματος κειμένου
    με προσαρμοσμένη γραμματοσειρά σε αρχείο Word .docx χρησιμοποιώντας το Aspose.Words
    for .NET.
  headline: Δημιουργήστε διαγώνιο υδατογράφημα κειμένου με προσαρμοσμένη γραμματοσειρά
    σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
  type: TechArticle
- description: Κώδικας βήμα‑βήμα για την προσθήκη διαγώνιου υδατογραφήματος κειμένου
    με προσαρμοσμένη γραμματοσειρά σε αρχείο Word .docx χρησιμοποιώντας το Aspose.Words
    for .NET.
  name: Δημιουργήστε διαγώνιο υδατογράφημα κειμένου με προσαρμοσμένη γραμματοσειρά
    σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
  steps:
  - name: Δημιουργήστε ένα νέο κενό αντικείμενο εγγράφου Word με όνομα `document`.
    text: Δημιουργήστε ένα νέο κενό αντικείμενο εγγράφου Word με όνομα `document`.
  - name: Διαμορφώστε το `watermarkSettings` με γραμματοσειρά Arial 48 pt σε γκρι
      χρώμα, διαγώνια διάταξη και αδιαφανή απόδοση.
    text: Διαμορφώστε το `watermarkSettings` με γραμματοσειρά Arial 48 pt σε γκρι
      χρώμα, διαγώνια διάταξη και αδιαφανή απόδοση.
  - name: Εφαρμόστε το υδατογράφημα κειμένου "Private" στο `document` χρησιμοποιώντας
      τις προηγουμένως ορισμένες ρυθμίσεις.
    text: Εφαρμόστε το υδατογράφημα κειμένου "Private" στο `document` χρησιμοποιώντας
      τις προηγουμένως ορισμένες ρυθμίσεις.
  - name: Ορίστε τη διαδρομή αρχείου όπου θα αποθηκευτεί το έγγραφο με υδατογράφημα.
    text: Ορίστε τη διαδρομή αρχείου όπου θα αποθηκευτεί το έγγραφο με υδατογράφημα.
  - name: Αποθηκεύστε το τροποποιημένο `document` στην καθορισμένη διαδρομή ως αρχείο
      .docx.
    text: Αποθηκεύστε το τροποποιημένο `document` στην καθορισμένη διαδρομή ως αρχείο
      .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` καθορίζει αν το υδατογράφημα αποδίδεται με μερική
      διαφάνεια· ορίζοντάς το σε `false` το υδατογράφημα γίνεται πλήρως αδιαφανές,
      ενώ το `true` εφαρμόζει το προεπιλεγμένο ημιδιαφανές εφέ.'
    question: Τι ελέγχει η σημαία **IsSemitrasparent** στο `TextWatermarkOptions`;
  - answer: Ναι—ορίστε την ιδιότητα `Layout` σε `WatermarkLayout.Horizontal` (ή άλλη
      τιμή enum) πριν καλέσετε το `document.Watermark.SetText`.
    question: Μπορώ να αλλάξω τον προσανατολισμό του υδατογραφήματος σε οριζόντιο
      αντί για διαγώνιο;
  - answer: Το Word θα επιστρέψει στην προεπιλεγμένη γραμματοσειρά του για το υδατογράφημα,
      έτσι το κείμενο θα εμφανίζεται αλλά μπορεί να φαίνεται διαφορετικό από το προτιθέμενο
      στυλ.
    question: Τι συμβαίνει αν η καθορισμένη `FontFamily` (π.χ., "Arial") δεν είναι
      εγκατεστημένη στον προορισμό;
  - answer: Φορτώστε το υπάρχον αρχείο με `Document document = new Document("Existing.docx");`
      στη συνέχεια διαμορφώστε το `TextWatermarkOptions` και καλέστε το `document.Watermark.SetText`
      όπως φαίνεται.
    question: Είναι δυνατόν να προσθέσετε υδατογράφημα σε υπάρχον αρχείο `.docx` αντί
      να δημιουργήσετε νέο;
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Προσθήκη διαγώνιου υδατογραφήματος κειμένου με προσαρμοσμένη γραμματοσειρά
og_description: Μάθετε πώς να ενσωματώσετε ένα κεκλιμένο υδατογράφημα κειμένου με τη δική σας γραμματοσειρά σε αρχείο Word σε λίγα λεπτά.
og_image_alt: Οδηγός που δείχνει πώς να προσθέσετε διαγώνιο υδατογράφημα κειμένου με προσαρμοσμένη γραμματοσειρά σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε διαγώνιο υδατογράφημα κειμένου με προσαρμοσμένη γραμματοσειρά σε έγγραφο Word χρησιμοποιώντας το Aspose.Words
Αυτό το σεμινάριο σας καθοδηγεί στη δημιουργία ενός νέου εγγράφου Word, στη διαμόρφωση ενός διαγώνιου υδατογραφήματος κειμένου με τις επιλεγμένες ρυθμίσεις γραμματοσειράς, στην εφαρμογή του μέσω του API Document.Watermark.SetText και στην αποθήκευση του αποτελέσματος ως αρχείο .docx. Στο τέλος θα έχετε ένα επαγγελματικά υδατογραφημένο έγγραφο που προβάλλει το εμπορικό σήμα ή την ιδιοκτησία σας. Ο κώδικας βήμα‑βήμα είναι έτοιμος για αντιγραφή σε οποιοδήποτε έργο .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Τι ελέγχει η σημαία **IsSemitrasparent** στο `TextWatermarkOptions`;**  
A: `IsSemitrasparent` καθορίζει αν το υδατογράφημα αποδίδεται με μερική διαφάνεια· ορίζοντάς το σε `false` το υδατογράφημα γίνεται πλήρως αδιαφανές, ενώ το `true` εφαρμόζει το προεπιλεγμένο ημιδιαφανές εφέ.

**Q: Μπορώ να αλλάξω τον προσανατολισμό του υδατογραφήματος σε οριζόντιο αντί για διαγώνιο;**  
A: Ναι—ορίστε την ιδιότητα `Layout` σε `WatermarkLayout.Horizontal` (ή άλλη τιμή enum) πριν καλέσετε το `document.Watermark.SetText`.

**Q: Τι συμβαίνει αν η καθορισμένη `FontFamily` (π.χ., "Arial") δεν είναι εγκατεστημένη στον προορισμό;**  
A: Το Word θα επιστρέψει στην προεπιλεγμένη γραμματοσειρά του για το υδατογράφημα, έτσι το κείμενο θα εμφανίζεται αλλά μπορεί να φαίνεται διαφορετικό από το προτιθέμενο στυλ.

**Q: Είναι δυνατόν να προσθέσετε υδατογράφημα σε υπάρχον αρχείο `.docx` αντί να δημιουργήσετε νέο;**  
A: Φορτώστε το υπάρχον αρχείο με `Document document = new Document("Existing.docx");` στη συνέχεια διαμορφώστε το `TextWatermarkOptions` και καλέστε το `document.Watermark.SetText` όπως φαίνεται.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}