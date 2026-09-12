---
category: general
date: 2026-09-11
description: Η λειτουργία συγχώνευσης αλληλογραφίας του Aspose σας επιτρέπει να φορτώσετε
  ένα πρότυπο Word και να το γεμίσετε με δεδομένα, αυτοματοποιώντας τη δημιουργία
  εγγράφων για τη δημιουργία εξατομικευμένων επιστολών.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: el
lastmod: 2026-09-11
og_description: Η συγχώνευση αλληλογραφίας του Aspose σας επιτρέπει να φορτώνετε πρότυπο
  Word και να το συμπληρώνετε, βελτιστοποιώντας τη δημιουργία εγγράφων ώστε να μπορείτε
  να δημιουργείτε εξατομικευμένες επιστολές γρήγορα.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Συγχώνευση αλληλογραφίας Aspose: Συμπλήρωση προτύπου Word σε λίγα λεπτά'
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
title: Πώς να εκτελέσετε συγχώνευση αλληλογραφίας Aspose για να συμπληρώσετε ένα πρότυπο
  Word
url: /el/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εκτελέσετε mail merge με Aspose για να συμπληρώσετε ένα πρότυπο Word

Αν χρειάζεστε **mail merge aspose** για να δημιουργήσετε μια παρτίδα εξατομικευμένων επιστολών, αυτός ο οδηγός σας δείχνει ακριβώς πώς να φορτώσετε ένα πρότυπο Word, να το συμπληρώσετε με δεδομένα και να αυτοματοποιήσετε τη δημιουργία εγγράφων με λίγες γραμμές C#. Είτε χτίζετε ένα σύστημα αποστολής αλληλογραφίας είτε ένα εργαλείο αναφορών, το πλήρες παράδειγμα παρακάτω σας επιτρέπει να δημιουργήσετε εξατομικευμένες επιστολές χωρίς να γράψετε καμία χειροκίνητη λογική συγχώνευσης.

Θα μάθετε πώς να **φορτώσετε πρότυπο word**, να χρησιμοποιήσετε την low‑code κλάση `MailMerger` και να **συμπληρώσετε πρότυπο word** με μια ανώνυμη πηγή δεδομένων. Στο τέλος του tutorial θα έχετε μια έτοιμη για εκτέλεση εφαρμογή console που παράγει ένα συγχωνευμένο έγγραφο Word που μπορείτε να στείλετε μέσω email, να εκτυπώσετε ή να αρχειοθετήσετε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Ένα έγκυρο license του Aspose.Words for .NET (ή ένα δωρεάν κλειδί αξιολόγησης)  
* Το πακέτο NuGet `Aspose.Words` (έκδοση 23.10 ή νεότερη) εγκατεστημένο στο project σας  
* Ένα αρχείο Word (`MailMergeTemplate.docx`) που περιέχει placeholders MERGEFIELD όπως **«Name»** και **«Age»**  

Μπορείτε να δημιουργήσετε το πρότυπο στο Microsoft Word εισάγοντας *Insert → Quick Parts → Field → MergeField* και ονομάζοντας τα πεδία ακριβώς όπως τα ονόματα των ιδιοτήτων στην πηγή δεδομένων σας.

## Βήμα 1 – Προετοιμάστε την πηγή δεδομένων για το mail merge

Η low‑code συγχώνευση λειτουργεί με οποιαδήποτε συλλογή που είναι enumerable. Σε αυτό το παράδειγμα χρησιμοποιούμε έναν πίνακα ανώνυμων αντικειμένων, αλλά θα μπορούσατε επίσης να περάσετε ένα `DataTable`, μια λίστα POCO ή δεδομένα που διαβάζονται από βάση δεδομένων.

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

**Γιατί είναι σημαντικό:**  
Το όνομα της ιδιότητας κάθε αντικειμένου (`Name`, `Age`) πρέπει να ταιριάζει με ένα MERGEFIELD στο πρότυπο. Η κλάση `MailMerger` αντιστοιχίζει αυτόματα τις ιδιότητες στα πεδία, εξαλείφοντας την ανάγκη για χειροκίνητα γεγονότα `FieldMerging`.

## Βήμα 2 – Φορτώστε το πρότυπο Word που περιέχει MERGEFIELDs

Η φόρτωση του προτύπου είναι απλή με την κλάση `Document`. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική με τον κατάλογο εργασίας του εκτελέσιμου.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Συμβουλή:**  
Αν εκτελείτε τον κώδικα από το Visual Studio, ορίστε *Copy to Output Directory* για το αρχείο προτύπου σε **Copy always**. Αυτό εξασφαλίζει ότι το αρχείο είναι διαθέσιμο όταν εκτελείται το μεταγλωττισμένο binary.

## Βήμα 3 – Δημιουργήστε μια παρουσία MailMerger δεσμευμένη στο πρότυπο

Η κλάση `MailMerger` βρίσκεται στο namespace `Aspose.Words.LowCode` και παρέχει μία μέθοδο `Execute` που δέχεται την πηγή δεδομένων.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Γιατί να χρησιμοποιήσετε το MailMerger;**  
`MailMerger` αφαιρεί το boiler‑plate των κλήσεων `MailMerge.Execute`, διαχειρίζεται τον εντοπισμό πεδίων, τη δέσμευση δεδομένων και την κλωνοποίηση εγγράφου εσωτερικά. Αυτό καθιστά τον κώδικα ιδανικό για σενάρια **automate document generation** όπου θέλετε μια καθαρή, low‑code λύση.

## Βήμα 4 – Εκτελέστε τη low‑code συγχώνευση χρησιμοποιώντας τα προετοιμασμένα δεδομένα

Καλώντας το `Execute` επιστρέφει ένα νέο `Document` που περιέχει

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Rename Word Merge Fields with Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}