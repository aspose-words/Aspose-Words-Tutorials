---
title: Προσθήκη Κόκκινου Διαγώνιου Υδατογραφήματος Κειμένου σε Έγγραφα Word με χρήση του Aspose.Words για .NET
weight: 110
limit:
description: Εφαρμόστε αυτόματα ένα κόκκινο διαγώνιο υδατογράφημα κειμένου σε κάθε αρχείο Word που δημιουργείται σε μια παρτίδα χρησιμοποιώντας το Aspose.Words για .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Εφαρμόστε αυτόματα ένα κόκκινο διαγώνιο υδατογράφημα κειμένου σε κάθε
    αρχείο Word που δημιουργείται σε μια παρτίδα χρησιμοποιώντας το Aspose.Words για
    .NET.
  headline: Προσθήκη Κόκκινου Διαγώνιου Υδατογραφήματος Κειμένου σε Έγγραφα Word με
    χρήση του Aspose.Words για .NET
  type: TechArticle
- description: Εφαρμόστε αυτόματα ένα κόκκινο διαγώνιο υδατογράφημα κειμένου σε κάθε
    αρχείο Word που δημιουργείται σε μια παρτίδα χρησιμοποιώντας το Aspose.Words για
    .NET.
  name: Προσθήκη Κόκκινου Διαγώνιου Υδατογραφήματος Κειμένου σε Έγγραφα Word με χρήση
    του Aspose.Words για .NET
  steps:
  - name: Δημιουργήστε το φάκελο \"GeneratedReports\" όπου θα αποθηκευτούν τα αρχεία
      εξόδου.
    text: Δημιουργήστε το φάκελο \"GeneratedReports\" όπου θα αποθηκευτούν τα αρχεία
      εξόδου.
  - name: Ξεκινήστε έναν βρόχο που θα δημιουργήσει τρία ξεχωριστά έγγραφα.
    text: Ξεκινήστε έναν βρόχο που θα δημιουργήσει τρία ξεχωριστά έγγραφα.
  - name: Δημιουργήστε ένα νέο κενό αντικείμενο εγγράφου Word.
    text: Δημιουργήστε ένα νέο κενό αντικείμενο εγγράφου Word.
  - name: Χρησιμοποιήστε το DocumentBuilder για να γράψετε μια γραμμή τίτλου και μια
      περιγραφή στο έγγραφο.
    text: Χρησιμοποιήστε το DocumentBuilder για να γράψετε μια γραμμή τίτλου και μια
      περιγραφή στο έγγραφο.
  - name: Ορίστε την εμφάνιση του υδατογραφήματος, συμπεριλαμβανομένης της γραμματοσειράς,
      του μεγέθους, του χρώματος και της διαγώνιας διάταξης.
    text: Ορίστε την εμφάνιση του υδατογραφήματος, συμπεριλαμβανομένης της γραμματοσειράς,
      του μεγέθους, του χρώματος και της διαγώνιας διάταξης.
  - name: Εφαρμόστε το ρυθμισμένο κόκκινο διαγώνιο υδατογράφημα με το κείμενο \"PROTECTED\"
      στο έγγραφο.
    text: Εφαρμόστε το ρυθμισμένο κόκκινο διαγώνιο υδατογράφημα με το κείμενο \"PROTECTED\"
      στο έγγραφο.
  - name: Αποθηκεύστε το υδατογραφημένο έγγραφο στο φάκελο \"GeneratedReports\" με
      ένα μοναδικό όνομα αρχείου.
    text: Αποθηκεύστε το υδατογραφημένο έγγραφο στο φάκελο \"GeneratedReports\" με
      ένα μοναδικό όνομα αρχείου.
  - name: Κλείστε τον βρόχο μετά την επεξεργασία του τρέχοντος εγγράφου.
    text: Κλείστε τον βρόχο μετά την επεξεργασία του τρέχοντος εγγράφου.
  type: HowTo
- questions:
  - answer: Το IsSemitrasparent καθορίζει αν το υδατογράφημα αποδίδεται με μερική
      διαφάνεια· ορίζοντάς το σε **true**, το κείμενο γίνεται ημιδιαφανές ώστε το
      υποκείμενο περιεχόμενο να παραμένει πιο ευανάγνωστο.
    question: Τι ελέγχει η επιλογή **IsSemitrasparent** και ποιο είναι το αποτέλεσμα
      του ορισμού της σε **true**;
  - answer: Ναι—ορίστε την ιδιότητα **Layout** σε **WatermarkLayout.Horizontal** στο
      **TextWatermarkOptions** πριν καλέσετε το **document.Watermark.SetText**.
    question: Μπορώ να αλλάξω τον προσανατολισμό του υδατογραφήματος σε οριζόντιο
      αντί για διαγώνιο;
  - answer: Το απόσπασμα δημιουργεί ένα νέο αντικείμενο **Document**, αλλά μπορείτε
      να ανοίξετε οποιοδήποτε υπάρχον αρχείο (π.χ., `new Document(\"Existing.docx\")`)
      και στη συνέχεια να καλέσετε το **document.Watermark.SetText** για να εφαρμόσετε
      το ίδιο υδατογράφημα.
    question: Αυτός ο κώδικας θα προσθέσει υδατογράφημα σε υπάρχον αρχείο Word ή μόνο
      σε νεοδημιουργημένα έγγραφα;
  - answer: Αναθέστε ένα προσαρμοσμένο χρώμα με **Color.FromArgb(red, green, blue)**
      στην ιδιότητα **Color** του **TextWatermarkOptions**, π.χ., `Color = Color.FromArgb(128,
      0, 128)` για μοβ.
    question: Πώς μπορώ να χρησιμοποιήσω προσαρμοσμένο χρώμα RGB για το υδατογράφημα
      αντί του προκαθορισμένου **Color.Red**;
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Προσθήκη Κόκκινου Διαγώνιου Υδατογραφήματος Κειμένου σε Έγγραφα Word
og_description: Δείτε πώς να εφαρμόζετε αυτόματα ένα κόκκινο διαγώνιο υδατογράφημα σε κάθε έγγραφο Word σε μια παρτίδα με το Aspose.Words.
og_image_alt: Οδηγός που δείχνει πώς να προσθέσετε ένα κόκκινο διαγώνιο υδατογράφημα κειμένου σε έγγραφα Word χρησιμοποιώντας το Aspose.Words για .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Κόκκινου Διαγώνιου Υδατογραφήματος Κειμένου σε Έγγραφα Word με χρήση του Aspose.Words για .NET
Αυτό το σεμινάριο δείχνει πώς να ενσωματώσετε αυτόματα ένα κόκκινο διαγώνιο υδατογράφημα κειμένου σε κάθε έγγραφο Word που δημιουργείται κατά τη διάρκεια μιας παρτίδας δημιουργίας αναφορών. Χρησιμοποιώντας τις κλάσεις Document και DocumentBuilder του Aspose.Words για .NET, το υδατογράφημα εφαρμόζεται προγραμματιστικά καθώς παράγονται τα αρχεία, εξασφαλίζοντας ότι κάθε έγγραφο φέρει το ίδιο branding ή την ειδοποίηση εμπιστευτικότητας χωρίς χειροκίνητη παρέμβαση.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Τι ελέγχει η επιλογή **IsSemitrasparent** και ποιο είναι το αποτέλεσμα του ορισμού της σε **true**;**  
A: Το IsSemitrasparent καθορίζει αν το υδατογράφημα αποδίδεται με μερική διαφάνεια· ορίζοντάς το σε **true**, το κείμενο γίνεται ημιδιαφανές ώστε το υποκείμενο περιεχόμενο να παραμένει πιο ευανάγνωστο.

**Q: Μπορώ να αλλάξω τον προσανατολισμό του υδατογραφήματος σε οριζόντιο αντί για διαγώνιο;**  
A: Ναι—ορίστε την ιδιότητα **Layout** σε **WatermarkLayout.Horizontal** στο **TextWatermarkOptions** πριν καλέσετε το **document.Watermark.SetText**.

**Q: Αυτός ο κώδικας θα προσθέσει υδατογράφημα σε υπάρχον αρχείο Word ή μόνο σε νεοδημιουργημένα έγγραφα;**  
A: Το απόσπασμα δημιουργεί ένα νέο αντικείμενο **Document**, αλλά μπορείτε να ανοίξετε οποιοδήποτε υπάρχον αρχείο (π.χ., `new Document(\"Existing.docx\")`) και στη συνέχεια να καλέσετε το **document.Watermark.SetText** για να εφαρμόσετε το ίδιο υδατογράφημα.

**Q: Πώς μπορώ να χρησιμοποιήσω προσαρμοσμένο χρώμα RGB για το υδατογράφημα αντί του προκαθορισμένου **Color.Red**;**  
A: Αναθέστε ένα προσαρμοσμένο χρώμα με **Color.FromArgb(red, green, blue)** στην ιδιότητα **Color** του **TextWatermarkOptions**, π.χ., `Color = Color.FromArgb(128, 0, 128)` για μοβ.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}