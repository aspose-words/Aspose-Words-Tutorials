---
category: general
date: 2026-10-23
description: Μάθετε πώς να εισάγετε έλλειψη και πώς να προσθέσετε σχήμα ορθογωνίου
  στο Word χρησιμοποιώντας το Aspose.Words. Περιλαμβάνει τη μετακίνηση του δρομέα
  στο σχήμα και πώς να δημιουργήσετε ομαδικό σχήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: el
lastmod: 2026-10-23
og_description: Πώς να εισάγετε ελλειπτικό σχήμα και πώς να προσθέσετε σχήμα ορθογωνίου
  στο Word με το Aspose.Words. Ακολουθήστε τον οδηγό βήμα‑βήμα για να μετακινήσετε
  τον κέρσορα στο σχήμα και να δημιουργήσετε ομαδικό σχήμα.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Πώς να εισάγετε σχήματα έλλειψης και ορθογωνίου σε μια ομαδική μορφή του
  Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να εισάγετε σχήματα έλλειψης και ορθογώνιου σε ένα ομαδικό σχήμα με το
  Aspose.Words
url: /el/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισαγάγετε σχήματα ellipse και rectangle μέσα σε ένα ομαδικό σχήμα με Aspose.Words

Αν χρειάζεστε να μάθετε **πώς να εισαγάγετε ellipse** σε ένα έγγραφο Word προγραμματιστικά, αυτός ο οδηγός δείχνει τη πλήρη διαδικασία. Θα δείτε επίσης **πώς να προσθέσετε rectangle** σχήμα, θα μάθετε να **μετακινείτε τον κέρσορα στο σχήμα**, και θα ανακαλύψετε **πώς να δημιουργήσετε group shape** που περιέχει πολλαπλά αντικείμενα σχεδίασης.

Η αυτοματοποίηση του Word συχνά απαιτεί ακριβή τοποθέτηση αντικειμένων σχεδίασης. Στο τέλος αυτού του tutorial μπορείτε να δημιουργήσετε ένα αρχείο `.docx` που περιέχει ένα ομαδοποιημένο rectangle και ellipse, έτοιμο για περαιτέρω στυλιζάρισμα ή εξαγωγή. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words for .NET και ένα περιβάλλον ανάπτυξης .NET.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη.
* Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`) προστέθηκε στο έργο σας.
* Βασικές γνώσεις σύνταξης C# και Visual Studio (ή οποιοδήποτε IDE).

Αυτές οι απαιτήσεις εξασφαλίζουν ότι ο κώδικας μεταγλωττίζεται χωρίς πρόσθετη διαμόρφωση.

## Πώς να δημιουργήσετε group shape στο Word

Ένα group shape λειτουργεί ως κοντέινερ που σας επιτρέπει να μετακινείτε, περιστρέφετε ή μορφοποιείτε πολλά σχήματα ως μία ενιαία μονάδα. Ο παρακάτω κώδικας δημιουργεί ένα group με συγκεκριμένο μέγεθος (300 × 200 points) και προετοιμάζει το έγγραφο για περαιτέρω λειτουργίες σχεδίασης.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Γιατί είναι σημαντικό αυτό το βήμα*: Το group shape ορίζει ένα τοπικό σύστημα συντεταγμένων. Όλα τα σχήματα που προστίθενται μετά τη μετακίνηση του κέρσορα στο group θα τοποθετηθούν σε σχέση με το αρχικό σημείο του group, καθιστώντας τους υπολογισμούς διάταξης απλούς.

## Πώς να προσθέσετε rectangle shape στο Word

Τώρα που υπάρχει το group, μπορείτε να **εισάγετε rectangle shape** μέσα σε αυτό. Το rectangle θα λειτουργήσει ως φόντο ή οπτικό placeholder για άλλο περιεχόμενο.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Εξήγηση*: `MoveTo(group)` ενημερώνει τον builder ότι το ενεργό σημείο εισαγωγής είναι το group shape. Χωρίς τη μετακίνηση του κέρσορα, το `InsertShape` θα προσθέσει το rectangle στο κύριο σώμα του εγγράφου αντί στο group.

## Πώς να εισαγάγετε ellipse

Με το rectangle στη θέση του, μπορείτε τώρα να δείξετε **πώς να εισαγάγετε ellipse**. Το ellipse θα κεντραριστεί μέσα στο ίδιο group, επικαλύπτοντας το rectangle αν το επιθυμείτε.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Γιατί πρέπει να μετακινηθεί ο κέρσορας*: Κάθε κλήση στο `InsertShape` σέβεται την τρέχουσα θέση του κέρσορα. Η επανάκληση του `MoveTo(group)` εγγυάται ότι το ellipse είναι επίσης παιδί του group, διατηρώντας την προγραμματισμένη ιεραρχία.

## Μετακινήστε τον κέρσορα στο σχήμα πριν την εισαγωγή πρόσθετων αντικειμένων

Αν χρειαστεί να προσθέσετε περισσότερα σχήματα αργότερα, πάντα **μετακινήστε τον κέρσορα στο σχήμα** πριν από κάθε εισαγωγή. Αυτό το μοτίβο αποτρέπει τυχαία τοποθέτηση εκτός του group.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Συμβουλή*: Η επαναχρησιμοποίηση του `MoveTo(group)` είναι φθηνή και βελτιώνει την αναγνωσιμότητα του κώδικα. Επίσης, κάνει τη μελλοντική συντήρηση πιο εύκολη επειδή το πλαίσιο εισαγωγής είναι σαφές.

## Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Το παράδειγμα αποθηκεύει το αρχείο ως `GroupShape.docx` σε έναν φάκελο που καθορίζετε.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Όταν ανοίξετε το αποθηκευμένο αρχείο στο Microsoft Word, θα δείτε ένα ενιαίο group που περιέχει ένα rectangle και ένα ellipse, και τα δύο σωστά τοποθετημένα.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο `.docx` με όνομα `GroupShape.docx`.
* Μέσα στο έγγραφο, ένα ομαδοποιημένο αντικείμενο σχεδίασης μεγέθους 300 × 200 points.
* Μέσα στο group:
  * Ένα rectangle (100 × 50 points) τοποθετημένο στο αρχικό σημείο του group.
  * Ένα ellipse (80 × 80 points) που επικαλύπτει το rectangle.
  * Οποιαδήποτε πρόσθετα σχήματα προσθέσατε μετά τη μετακίνηση του κέρσορα.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Προτεινόμενη προσέγγιση |
|-----------|----------------------|
| **Διαφορετικά μεγέθη μονάδων** | Το Aspose.Words χρησιμοποιεί points (1 pt = 1/72 in). Μετατρέψτε εκατοστά ή ίντσες σε points πριν καλέσετε το `InsertShape`. |
| **Περιστροφή σχημάτων μέσα στο group** | Μετά την εισαγωγή ενός σχήματος, ανακτήστε το αντικείμενο `ShapeBase` και ορίστε `ShapeBase.RotationAngle`. |
| **Προσθήκη κειμένου μέσα σε σχήμα** | Χρησιμοποιήστε `ShapeBase.AppendChild(new Paragraph(document))` και στη συνέχεια προσθέστε ένα `Run` με το επιθυμητό κείμενο. |
| **Αποθήκευση σε PDF αντί για DOCX** | Καλέστε `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – η ιεραρχία του group διατηρείται στην έξοδο PDF. |

Αυτές οι παραλλαγές δείχνουν ότι η ίδια λογική **πώς να εισαγάγετε ellipse** μπορεί να προσαρμοστεί σε πολλές πραγματικές περιπτώσεις.

## Επαγγελματικές συμβουλές

* **Επαναχρησιμοποιήστε το ίδιο αντικείμενο `DocumentBuilder`** – μειώνει το φορτίο μνήμης και διατηρεί την κατάσταση του εγγράφου συνεπή.
* **Επικυρώστε τις διαστάσεις του σχήματος** – εξαιρετικά μεγάλα πλάτη ή ύψη μπορεί να προκαλέσουν προβλήματα απόδοσης σε παλαιότερες εκδόσεις του Word.
* **Ομαδοποιήστε πριν το στυλ** – η εφαρμογή χρωμάτων γεμίσματος ή στυλ γραμμής στο group μετά την προσθήκη όλων των παιδιών εξασφαλίζει ομοιόμορφη εμφάνιση.

## Συμπέρασμα

Τώρα καταλαβαίνετε **πώς να εισαγάγετε ellipse** και **πώς να προσθέσετε rectangle** σχήμα μέσα σε ένα ομαδοποιημένο κοντέινερ σε έγγραφο Word χρησιμοποιώντας Aspose.Words. Με τη συνεχή **μετακίνηση του κέρσορα στο σχήμα** πριν από κάθε εισαγωγή, διατηρείτε μια καθαρή ιεραρχία και αποφεύγετε τυχαία τοποθέτηση. Το πλήρες παράδειγμα μεταγλωττίζεται, εκτελείται και παράγει ένα ομαδοποιημένο σχήμα που μπορεί να προσαρμοστεί περαιτέρω ή να εξαχθεί.

Έτοιμοι να εξερευνήσετε περισσότερα; Δοκιμάστε να συνδυάσετε αυτήν την τεχνική με **πώς να δημιουργήσετε group shape** για σύνθετα διαγράμματα, ή πειραματιστείτε με **insert rectangle shape word** μαζί με πλαίσια κειμένου για δημιουργία πλούσιων αναφορών. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε rectangle shape και group shapes σε Word με Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Πώς να δημιουργήσετε κενό έγγραφο Word και να προσθέσετε κρυφό ellipse shape σε C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Πώς να δημιουργήσετε group shape docx και να προσθέσετε διαδραστικούς ελέγχους σε C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}