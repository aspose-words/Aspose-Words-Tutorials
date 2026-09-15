---
category: general
date: 2026-09-14
description: Μάθετε πώς να εισάγετε ετικέτα, να προσθέτετε σχήματα, να δημιουργείτε
  ομάδα και να αποθηκεύετε το έγγραφο ως DOCX χρησιμοποιώντας το Aspose.Words σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: el
lastmod: 2026-09-14
og_description: Πώς να εισαγάγετε ετικέτα, να προσθέσετε σχήματα, να δημιουργήσετε
  ομάδα και να αποθηκεύσετε το έγγραφο ως DOCX χρησιμοποιώντας το Aspose.Words. Ακολουθήστε
  τον οδηγό βήμα‑βήμα.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Πώς να εισαγάγετε ετικέτα και να δημιουργήσετε ομαδοποιημένο σχήμα σε ένα
  DOCX με C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: Πώς να εισάγετε ετικέτα και να δημιουργήσετε ένα ομαδικό σχήμα σε ένα DOCX
url: /el/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισάγετε ετικέτα και να δημιουργήσετε μια ομαδική μορφή σε DOCX

Αν χρειάζεστε να γνωρίζετε **πώς να εισάγετε ετικέτα** κατά τη δημιουργία σύνθετης διάταξης, αυτός ο οδηγός σας παρουσιάζει μια πλήρη, εκτελέσιμη λύση. Θα δείτε πώς να προσθέτετε σχήματα, να δημιουργείτε μια ομάδα και τελικά **να αποθηκεύσετε το έγγραφο ως DOCX** με το Aspose.Words for .NET.

Η δημιουργία εγγράφων συχνά απαιτεί το συνδυασμό ετικετών κειμένου με γραφικά στοιχεία. Σε αυτό το tutorial θα μάθετε ακριβώς **πώς να εισάγετε ετικέτα**, πώς να **προσθέσετε σχήματα**, πώς να **δημιουργήσετε ομάδα**, και τον σωστό τρόπο **αποθήκευσης docx** ώστε το αρχείο να μπορεί να ανοιχθεί στο Word χωρίς απώλεια πιστότητας.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Βασική εξοικείωση με τη σύνταξη C#
- Ένα IDE όπως το Visual Studio ή το VS Code

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· το πλήρες παράδειγμα εκτελείται με μια μόνο αναφορά NuGet.

## Πώς να δημιουργήσετε ομάδα και να προσθέσετε σχήματα

Το πρώτο λογικό βήμα είναι η δημιουργία μιας **ομάδας** που θα περιέχει πολλαπλά σχήματα. Η ομαδοποίηση διατηρεί τα σχήματα μαζί όταν τα μετακινείτε ή τα περιστρέφετε αργότερα.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Γιατί είναι σημαντικό:**  
`GroupShape` λειτουργεί ως κοντέινερ. Όταν μετακινήσετε αργότερα την ομάδα, τόσο το ορθογώνιο όσο και η έλλειψη μετακινούνται μαζί, διατηρώντας τις σχετικές τους θέσεις. Αυτός είναι ο προτεινόμενος τρόπος διαχείρισης πολλαπλών γραφικών που ανήκουν στο ίδιο λογικό μπλοκ.

## Πώς να εισάγετε ετικέτα μέσα στο έγγραφο

Τώρα που η ομάδα είναι έτοιμη, μπορείτε να **εισάγετε ετικέτα** (ένα StructuredDocumentTag, γνωστό και ως SDT) αμέσως μετά την ομάδα. Η ετικέτα μπορεί να περιέχει απλό‑κείμενο, εμπλουτισμένο‑κείμενο ή ακόμη και επαναλαμβανόμενο περιεχόμενο.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Γιατί πρέπει να χρησιμοποιήσετε StructuredDocumentTag:**  
Ένα SDT παρέχει έναν σημασιολογικό δείκτη που το Word μπορεί να αναγνωρίσει για ελέγχους περιεχομένου, σύνδεση δεδομένων ή σενάρια συμπλήρωσης φορμών. Χρησιμοποιώντας το `InsertStructuredDocumentTag` εισάγετε ρητά **πώς να εισάγετε ετικέτα** με τρόπο που παραμένει μετά από επεξεργασία στο Microsoft Word.

## Πώς να αποθηκεύσετε docx και να επαληθεύσετε το αποτέλεσμα

Το τελικό βήμα είναι η διατήρηση του εγγράφου. Ο κώδικας παρακάτω δείχνει τον σωστό τρόπο **αποθήκευσης εγγράφου ως docx** και πού βρίσκεται το αρχείο εξόδου.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Όταν ανοίξετε το *GroupAndSDT.docx* στο Word, θα πρέπει να δείτε ένα ομαδοποιημένο γραφικό ορθογώνιο‑έλλειψη ακολουθούμενο από έναν έλεγχο περιεχομένου απλού κειμένου με τίτλο **MyTag** που περιέχει τη γραμμή “Content inside the SDT”.

### Αναμενόμενο αποτέλεσμα

- Μια ομάδα 200 × 200 σημείων τοποθετημένη στο (50, 50) της σελίδας.
- Μέσα στην ομάδα: ένα μπλε ορθογώνιο στα αριστερά και μια έλλειψη στα δεξιά (προεπιλεγμένα χρώματα).
- Ακριβώς κάτω από την ομάδα: ένας έλεγχος περιεχομένου με ετικέτα **MyTag** και το κείμενο “Content inside the SDT”.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using`, διαχείριση σφαλμάτων και σχόλια που εξηγούν κάθε βήμα.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Εκτελέστε το πρόγραμμα, μεταβείτε στην Επιφάνεια εργασίας σας και κάντε διπλό‑κλικ στο *GroupAndSDT.docx* για να επαληθεύσετε ότι η ομάδα και η ετικέτα εμφανίζονται όπως περιγράφεται.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να προσθέσω περισσότερα από δύο σχήματα στην ομάδα;** | Ναι. Καλέστε `groupShape.AppendChild(new Shape(...))` για κάθε επιπλέον σχήμα πριν την εισαγωγή της ομάδας. |
| **Τι γίνεται αν χρειάζομαι ετικέτα εμπλουτισμένου κειμένου αντί για απλό κείμενο;** | Χρησιμοποιήστε `StructuredDocumentTagType.RichText` στο `InsertStructuredDocumentTag`. |
| **Πώς αλλάζω το χρώμα του ορθογωνίου ή της έλλειψης;** | Ορίστε την ιδιότητα `FillColor` σε κάθε αντικείμενο `Shape`, π.χ., `shape.FillColor = Color.LightBlue;`. |
| **Μπορώ να περιστρέψω ολόκληρη την ομάδα;** | Ορίστε `groupShape.Rotation = 45;` (μοίρες) πριν την εισαγωγή του κόμβου. |
| **Πρέπει να καλέσω `Dispose()` σε κάποιο αντικείμενο;** | Το Aspose.Words διαχειρίζεται τις περισσότερες πηγές εσωτερικά· η διαγραφή του `Document` είναι προαιρετική σε μια κονσολική εφαρμογή μικρής διάρκειας. |

## Καλές πρακτικές για αποθήκευση αρχείων DOCX

- **Πάντα χρησιμοποιείτε απόλυτη διαδρομή** (ή καλά ορισμένη σχετική διαδρομή) όταν καλείτε `document.Save`. Αυτό αποτρέπει το σφάλμα “file not found” που μπορεί να εμφανιστεί με ασαφείς καταλόγους εργασίας.
- **Προτιμήστε τις υπερφορτώσεις `Save` που δέχονται ροή** εάν χρειάζεται να στείλετε το έγγραφο μέσω HTTP ή να το αποθηκεύσετε σε βάση δεδομένων.
- **Ορίστε τις `CompatibilityOptions`** εάν πρέπει να στοχεύσετε παλαιότερες εκδόσεις του Word (π.χ., Word 2003). Για τις περισσότερες σύγχρονες περιπτώσεις οι προεπιλεγμένες ρυθμίσεις λειτουργούν άψογα.

## Επόμενα βήματα

Τώρα που ξέρετε **πώς να εισάγετε ετικέτα**, πώς να **προσθέσετε σχήματα**, πώς να **δημιουργήσετε ομάδα** και πώς να **αποθηκεύσετε docx**, μπορείτε να εξερευνήσετε πιο προχωρημένα σενάρια:

- Συνδυάστε πολλαπλές ομάδες για τη δημιουργία σύνθετων διαγραμμάτων.
- Χρησιμοποιήστε `StructuredDocumentTag` για σύνδεση δεδομένων σε πρότυπα Word.
- Εξάγετε το ίδιο έγγραφο σε PDF (`document.Save("output.pdf")`) διατηρώντας τα ομαδοποιημένα γραφικά.
- Αυτοματοποιήστε τη συμπλήρωση φορμών προγραμματιστικά ορίζοντας το περιεχόμενο του SDT (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Πειραματιστείτε με διαφορετικές τιμές `ShapeType` (π.χ., `ShapeType.Polygon`, `ShapeType.Line`) για να δείτε πώς συμπεριφέρονται μέσα σε ένα `GroupShape`. Το ίδιο μοτίβο λειτουργεί για πίνακες, εικόνες ή οποιονδήποτε άλλο κόμβο θέλετε να διατηρήσετε μαζί.

---

**Σύνοψη:** Αυτό το tutorial έδειξε **πώς να εισάγετε ετικέτα** μέσα σε μια ομαδοποιημένη μορφή, πώς να **προσθέσετε σχήματα**, πώς να **δημιουργήσετε ομάδα** και τη σωστή μέθοδο **αποθήκευσης εγγράφου ως docx** χρησιμοποιώντας το Aspose.Words for .NET. Τώρα έχετε μια ισχυρή βάση για τη δημιουργία πλούσιων, διαδραστικών αρχείων DOCX προγραμματιστικά.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Πώς να αποθηκεύσετε Markdown από DOCX – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Πώς να ανακτήσετε DOCX – Πλήρης οδηγός με χρήση Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [Πώς να ελέγξετε τη γραμματική σε DOCX με Aspose.Words – χρήση gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}