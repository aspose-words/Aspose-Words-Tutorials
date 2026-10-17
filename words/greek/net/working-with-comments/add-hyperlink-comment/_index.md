---
title: Προσθήκη Hyperlink Comment και εξαγωγή ως PDF Annotation χρησιμοποιώντας Aspose.Words for .NET
weight: 110
limit:
description: Μάθετε πώς να προσθέσετε ένα hyperlink comment σε ένα αρχείο Word και να το εξάγετε ως PDF annotation με Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Μάθετε πώς να προσθέσετε ένα hyperlink comment σε ένα αρχείο Word και
    να το εξάγετε ως PDF annotation με Aspose.Words for .NET.
  headline: Προσθήκη Hyperlink Comment και εξαγωγή ως PDF Annotation χρησιμοποιώντας
    Aspose.Words for .NET
  type: TechArticle
- description: Μάθετε πώς να προσθέσετε ένα hyperlink comment σε ένα αρχείο Word και
    να το εξάγετε ως PDF annotation με Aspose.Words for .NET.
  name: Προσθήκη Hyperlink Comment και εξαγωγή ως PDF Annotation χρησιμοποιώντας Aspose.Words
    for .NET
  steps:
  - name: Δημιουργήστε ένα νέο κενό αντικείμενο Document και ένα DocumentBuilder για
      να εργαστείτε με αυτό.
    text: Δημιουργήστε ένα νέο κενό αντικείμενο Document και ένα DocumentBuilder για
      να εργαστείτε με αυτό.
  - name: Γράψτε μια γραμμή ορατού κειμένου που θα φιλοξενήσει το επερχόμενο σχόλιο.
    text: Γράψτε μια γραμμή ορατού κειμένου που θα φιλοξενήσει το επερχόμενο σχόλιο.
  - name: Δημιουργήστε ένα Comment που έχει συγγραφέα Jane Doe και συνδέστε το με
      την πρώτη παράγραφο του εγγράφου.
    text: Δημιουργήστε ένα Comment που έχει συγγραφέα Jane Doe και συνδέστε το με
      την πρώτη παράγραφο του εγγράφου.
  - name: Μέσα στο comment, προσθέστε μια παράγραφο και εισάγετε έναν μπλε, υπογραμμισμένο
      σύνδεσμο προς τον ιστότοπο Aspose.Words Library.
    text: Μέσα στο comment, προσθέστε μια παράγραφο και εισάγετε έναν μπλε, υπογραμμισμένο
      σύνδεσμο προς τον ιστότοπο Aspose.Words Library.
  - name: Διαμορφώστε το έγγραφο ώστε να αποδίδει τα comments ως σημειώσεις PDF και
      ανανεώστε τη διάταξη.
    text: Διαμορφώστε το έγγραφο ώστε να αποδίδει τα comments ως σημειώσεις PDF και
      ανανεώστε τη διάταξη.
  - name: Δημιουργήστε έναν φάκελο "Output" στον τρέχοντα κατάλογο για να αποθηκεύσετε
      το παραγόμενο PDF.
    text: Δημιουργήστε έναν φάκελο "Output" στον τρέχοντα κατάλογο για να αποθηκεύσετε
      το παραγόμενο PDF.
  - name: Αποθηκεύστε το προετοιμασμένο έγγραφο ως αρχείο PDF χρησιμοποιώντας PdfSaveOptions.
    text: Αποθηκεύστε το προετοιμασμένο έγγραφο ως αρχείο PDF χρησιμοποιώντας PdfSaveOptions.
  - name: Ελέγξτε ότι το αρχείο PDF υπάρχει και περιέχει δεδομένα, στη συνέχεια εμφανίστε
      το αποτέλεσμα στην κονσόλα.
    text: Ελέγξτε ότι το αρχείο PDF υπάρχει και περιέχει δεδομένα, στη συνέχεια εμφανίστε
      το αποτέλεσμα στην κονσόλα.
  type: HowTo
- questions:
  - answer: Το τρίτο όρισμα της `InsertHyperlink` καθορίζει αν ο σύνδεσμος θα αντιμετωπιστεί
      ως πεδίο· ορίζοντας το σε `false` εισάγει έναν απλό σύνδεσμο που λειτουργεί
      στη PDF annotation χωρίς να χρειάζεται κώδικας πεδίου.
    question: Τι ελέγχει το τρίτο όρισμα (`false`) στη μέθοδο `InsertHyperlink`;
  - answer: Ορίστε το `myDocument.LayoutOptions.CommentDisplayMode` σε `CommentDisplayMode.ShowInBalloons`
      πριν καλέσετε το `Save`; το PDF θα περιέχει τότε το comment ως κανονικό comment
      Word αντί για annotation.
    question: Πώς μπορώ να κάνω το comment να εμφανίζεται ως μπαλόνι στο έγγραφο Word
      αντί για PDF annotation;
  - answer: Ναι—κάθε `Comment` που προσθέτετε σε μια παράγραφο μπορεί να περιέχει
      τη δική του κλήση `InsertHyperlink`, και όλοι οι σύνδεσμοι θα διατηρηθούν ως
      ξεχωριστές PDF annotations όταν αποθηκευτεί το έγγραφο.
    question: Αν προσθέσω περισσότερα από ένα comment, θα λειτουργεί κάθε σύνδεσμος
      στο εξαγόμενο PDF;
  - answer: Ανοίξτε το παραγόμενο PDF, εντοπίστε την annotation του comment (συνήθως
      εμφανίζεται ως εικονίδιο σημείωσης), κάντε κλικ σε αυτήν για να εμφανιστεί το
      κείμενο του comment και, στη συνέχεια, κάντε κλικ στον μπλε υπογραμμισμένο σύνδεσμο·
      θα πρέπει να ανοίξει το URL προορισμού σε έναν φυλλομετρητή.
    question: Πώς μπορώ να επαληθεύσω ότι ο σύνδεσμος μέσα στο comment λειτουργεί
      πραγματικά μετά τη δημιουργία του PDF;
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Εισαγωγή Hyperlink Comment & Εξαγωγή σε PDF
og_description: Μάθετε πώς να ενσωματώσετε έναν κλικ‑σύνδεσμο σε ένα comment Word και να τον μετατρέψετε σε PDF annotation.
og_image_alt: Οδηγός που δείχνει πώς να προσθέσετε ένα comment με κλικ‑σύνδεσμο σε ένα έγγραφο Word και να το εξάγετε ως PDF annotation χρησιμοποιώντας Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Hyperlink Comment και εξαγωγή ως PDF Annotation χρησιμοποιώντας Aspose.Words
Σε αυτόν τον οδηγό θα δείτε πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε ένα comment που περιέχει έναν κλικ‑σύνδεσμο προς έναν εξωτερικό ιστότοπο, να διαμορφώσετε αυτό το comment ώστε να εμφανίζεται ως σημείωση PDF, να εξάγετε το έγγραφο σε PDF και να επαληθεύσετε το παραγόμενο αρχείο PDF. Ο κώδικας βήμα‑βήμα σας επιτρέπει να προσθέσετε πλούσια, ενεργοποιημένα με συνδέσμους comments και να τα διατηρήσετε κατά τη μετατροπή σε PDF, καθιστώντας εύκολο το μοίρασμα διαδραστικών σημειώσεων με τους αναγνώστες.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Τι ελέγχει το τρίτο όρισμα (`false`) στη μέθοδο `InsertHyperlink`;**  
A: Το τρίτο όρισμα της `InsertHyperlink` καθορίζει αν ο σύνδεσμος θα αντιμετωπιστεί ως πεδίο· ορίζοντας το σε `false` εισάγει έναν απλό σύνδεσμο που λειτουργεί στη PDF annotation χωρίς να χρειάζεται κώδικας πεδίου.

**Q: Πώς μπορώ να κάνω το comment να εμφανίζεται ως μπαλόνι στο έγγραφο Word αντί για PDF annotation;**  
A: Ορίστε το `myDocument.LayoutOptions.CommentDisplayMode` σε `CommentDisplayMode.ShowInBalloons` πριν καλέσετε το `Save`; το PDF θα περιέχει τότε το comment ως κανονικό comment Word αντί για annotation.

**Q: Αν προσθέσω περισσότερα από ένα comment, θα λειτουργεί κάθε σύνδεσμος στο εξαγόμενο PDF;**  
A: Ναι—κάθε `Comment` που προσθέτετε σε μια παράγραφο μπορεί να περιέχει τη δική του κλήση `InsertHyperlink`, και όλοι οι σύνδεσμοι θα διατηρηθούν ως ξεχωριστές PDF annotations όταν αποθηκευτεί το έγγραφο.

**Q: Πώς μπορώ να επαληθεύσω ότι ο σύνδεσμος μέσα στο comment λειτουργεί πραγματικά μετά τη δημιουργία του PDF;**  
A: Ανοίξτε το παραγόμενο PDF, εντοπίστε την annotation του comment (συνήθως εμφανίζεται ως εικονίδιο σημείωσης), κάντε κλικ σε αυτήν για να εμφανιστεί το κείμενο του comment και, στη συνέχεια, κάντε κλικ στον μπλε υπογραμμισμένο σύνδεσμο· θα πρέπει να ανοίξει το URL προορισμού σε έναν φυλλομετρητή.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}