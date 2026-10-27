---
category: general
date: 2026-10-23
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word και να εισάγετε έναν
  έλεγχο περιεχομένου απλού κειμένου (SDT) με σύμβολο κράτησης θέσης χρησιμοποιώντας
  C#. Περιλαμβάνει κώδικα βήμα‑προς‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert control
- plain text content control
- how to add sdt
- add placeholder to tag
language: el
lastmod: 2026-10-23
og_description: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε έναν έλεγχο περιεχομένου
  απλού κειμένου (SDT) με σύμβολο κράτησης θέσης χρησιμοποιώντας C#. Ακολουθήστε το
  πλήρες, εκτελέσιμο παράδειγμα.
og_image_alt: Screenshot showing a blank Word document with a highlighted plain text
  content control
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε έναν έλεγχο περιεχομένου
  απλού κειμένου – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create a blank Word document and insert a plain text content
    control (SDT) with a placeholder using C#. Includes step‑by‑step code.
  headline: How to create blank Word document with a plain text content control in
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- ContentControl
- WordAutomation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word με έναν έλεγχο περιεχομένου απλού
  κειμένου σε C#
url: /el/java/document-manipulation/how-to-create-blank-word-document-with-a-plain-text-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word με έλεγχο περιεχομένου απλού κειμένου σε C#

Αν χρειάζεστε να **δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Χρησιμοποιώντας το Aspose.Words για .NET μπορείτε να ξεκινήσετε με ένα κενό αρχείο, να εισάγετε ένα StructuredDocumentTag (SDT) απλού κειμένου, να του δώσετε έναν τίτλο και να προσθέσετε ένα χρήσιμο placeholder—όλα σε λίγες γραμμές C#.

Το σεμινάριο καλύπτει κάθε βήμα που χρειάζεστε, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση του τελικού `.docx`. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 (ή νεότερο) εγκατεστημένο.  
* Μια αναφορά στο πακέτο NuGet **Aspose.Words**.  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code.

Δεν απαιτούνται πρόσθετες βιβλιοθήκες.

## Πώς να δημιουργήσετε κενό έγγραφο Word και να προσθέσετε έλεγχο περιεχομένου απλού κειμένου

Το πρώτο σημαντικό έργο είναι η δημιουργία ενός **κενού εγγράφου Word**. Αυτό σας παρέχει έναν καθαρό καμβά στον οποίο μπορείτε αργότερα να **εισάγετε στοιχεία ελέγχου**.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί λειτουργεί αυτό*: `Document()` δημιουργεί μια αναπαράσταση σε μνήμη ενός αρχείου Word χωρίς σελίδες. `DocumentBuilder` είναι η βοηθητική κλάση που σας επιτρέπει να προσθέτετε παραγράφους, πίνακες και ελέγχους περιεχομένου.

## Πώς να εισάγετε έλεγχο χρησιμοποιώντας το DocumentBuilder

Τώρα που το έγγραφο υπάρχει, μπορείτε να **εισάγετε αντικείμενα ελέγχου** απευθείας στο σημείο όπου βρίσκεται ο κέρσορας. Για έλεγχο περιεχομένου απλού κειμένου, χρησιμοποιήστε το `InsertStructuredDocumentTag`.

```csharp
// Step 2: Insert a plain‑text StructuredDocumentTag (SDT) inline
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
```

*Εξήγηση*:  
* `StructuredDocumentTagType.PlainText` λέει στο Aspose.Words να δημιουργήσει έναν **έλεγχο περιεχομένου απλού κειμένου**.  
* `MarkupLevel.Inline` τοποθετεί τον έλεγχο μέσα στην τρέχουσα παράγραφο, κάνοντάς τον να συμπεριφέρεται όπως το κανονικό κείμενο.

## Πώς να προσθέσετε τίτλο SDT και κείμενο placeholder

Ένας καλά ονομασμένος έλεγχος είναι πιο εύκολο να εντοπιστεί αργότερα, ειδικά όταν χρειάζεται να δεσμεύσετε δεδομένα ή να εκτελέσετε επικύρωση. Το βήμα **προσθήκη placeholder στην ετικέτα** βελτιώνει επίσης την εμπειρία του χρήστη.

```csharp
// Step 3: Give the SDT a meaningful title (used for identification)
sdt.Title = "CustomerName";

// Step 4: Add placeholder text so the user knows what to enter
sdt.AppendChild(new Run(doc, "Enter name here"));
```

*Γιατί είναι σημαντικό*:  
* Η ιδιότητα `Title` είναι μεταδεδομένα που μπορείτε να ερωτήσετε με `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
* Το placeholder (`Run` με “Enter name here”) εμφανίζεται αχνό (γκρι) στο Word, προτρέποντας τον τελικό χρήστη να το αντικαταστήσει.

## Πώς να αποθηκεύσετε το έγγραφο με το SDT

Τέλος, αποθηκεύστε το αρχείο στο δίσκο. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική με τον τρέχοντα φάκελο της εφαρμογής σας.

```csharp
// Step 5: Save the document with the SDT to a file
doc.Save("SDTExample.docx");
```

Όταν ανοίξετε το **SDTExample.docx** στο Microsoft Word, θα δείτε μια μόνο γραμμή που περιέχει ένα αχνό placeholder μέσα σε ένα πλαίσιο με περίγραμμα—ακριβώς τον **έλεγχο περιεχομένου απλού κειμένου** που δημιουργήσατε.

### Αναμενόμενο αποτέλεσμα

| Τοποθεσία | Οπτική ένδειξη |
|-----------|----------------|
| Μέσα στην πρώτη παράγραφο | Ένα ορθογώνιο πλαίσιο με την ετικέτα “Enter name here” (placeholder) |

Μπορείτε να πληκτρολογήσετε ένα όνομα απευθείας στο πλαίσιο· το Word θα θεωρήσει το εισαχθέν κείμενο ως περιεχόμενο του SDT.

## Προσθήκη πολλαπλών ελέγχων (προαιρετικό)

Αν χρειάζεστε περισσότερους από έναν **έλεγχο περιεχομένου απλού κειμένου**, επαναλάβετε τα βήματα 2‑4 με μια νέα θέση `DocumentBuilder`. Για παράδειγμα, για να προσθέσετε ένα πεδίο διεύθυνσης:

```csharp
builder.Writeln(); // Move to a new paragraph
StructuredDocumentTag addressSdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
addressSdt.Title = "CustomerAddress";
addressSdt.AppendChild(new Run(doc, "Enter address here"));
```

*Συμβουλή*: Χρησιμοποιήστε το `builder.Writeln()` για να ξεκινήσετε μια νέα παράγραφο πριν εισάγετε άλλο SDT, διατηρώντας τη διάταξη τακτική.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Το κείμενο placeholder εξαφανίζεται μετά την αποθήκευση | Το SDT δημιουργήθηκε με `MarkupLevel.Block` αντί για `Inline` | Χρησιμοποιήστε `MarkupLevel.Inline` για inline placeholders |
| Ο τίτλος δεν είναι αναζητήσιμος | Ο τίτλος δεν ορίστηκε ποτέ ή ορίστηκε μετά την αποθήκευση | Ορίστε `sdt.Title` **πριν** καλέσετε `doc.Save()` |
| Το έγγραφο εμφανίζεται κενό στο Word | Δεν προστέθηκε περιεχόμενο μετά τη δημιουργία του εγγράφου | Βεβαιωθείτε ότι προσθέτετε τουλάχιστον μια παράγραφο ή έλεγχο πριν την αποθήκευση |

## Επαγγελματική συμβουλή: Επαναχρησιμοποίηση του αποσπάσματος σε βοηθητική μέθοδο

Η περιτύλιξη της λογικής την καθιστά επαναχρησιμοποιήσιμη σε διάφορα έργα:

```csharp
public static Document CreateDocumentWithPlainTextControl(string title, string placeholder)
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);

    StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
    sdt.Title = title;
    sdt.AppendChild(new Run(doc, placeholder));

    return doc;
}

// Usage
Document myDoc = CreateDocumentWithPlainTextControl("OrderNumber", "Enter order #");
myDoc.Save("OrderForm.docx");
```

*Γιατί βοηθά*: Η μέθοδος απομονώνει τη λογική **δημιουργίας κενών εγγράφων Word**, επιτρέποντάς σας να δημιουργήσετε πολλαπλά πρότυπα με διαφορετικούς τίτλους και placeholders χωρίς να διπλασιάζετε κώδικα.

## Επόμενα βήματα

Τώρα που γνωρίζετε **πώς να εισάγετε έλεγχο** και **πώς να προσθέσετε placeholder στην ετικέτα**, μπορείτε να εξερευνήσετε:

* Σύνδεση SDT με προσαρμοσμένα XML μέρη (`doc.CustomXmlParts`) – χρήσιμο για πρότυπα που βασίζονται σε δεδομένα.  
* Μετατροπή του εγγράφου σε PDF διατηρώντας τους ελέγχους περιεχομένου.  
* Χρήση άλλων τιμών `StructuredDocumentTagType` όπως `Date`, `ComboBox` ή `CheckBox` για πιο πλούσιες φόρμες.

Κάθε ένα από αυτά τα θέματα βασίζεται στο βασικό μοτίβο που παρουσιάστηκε εδώ.

---

**Σύνοψη**

Αυτό το σεμινάριο σας οδήγησε στη δημιουργία ενός **κενού εγγράφου Word**, στην εισαγωγή ενός **ελέγχου περιεχομένου απλού κειμένου**, στην ανάθεση τίτλου και στην προσθήκη ενός χρήσιμου placeholder. Το πλήρες, εκτελέσιμο παράδειγμα μπορεί να αντιγραφεί σε οποιοδήποτε έργο .NET, και η προαιρετική βοηθητική μέθοδος δείχνει πώς να κλιμακώσετε την προσέγγιση. Με αυτή τη βάση είστε έτοιμοι να δημιουργήσετε σύνθετες φόρμες και πρότυπα βασισμένα σε Word σε C#.

---

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω σεμινάρια καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία νέου εγγράφου Word και εισαγωγή ελέγχου περιεχομένου σε C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη ελέγχου περιεχομένου και placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Πώς να προσθέσετε έλεγχο περιεχομένου και να δημιουργήσετε έγγραφο Word με Aspose – Πλήρες](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}