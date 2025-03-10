---
title: Δημιουργία πίνακα περιεχομένων στο Aspose.Words για Java
linktitle: Δημιουργία πίνακα περιεχομένων
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να δημιουργείτε και να προσαρμόζετε τον Πίνακα Περιεχομένων (TOC) χρησιμοποιώντας το Aspose.Words για Java. Δημιουργήστε οργανωμένα και επαγγελματικά έγγραφα χωρίς κόπο.
weight: 21
url: /el/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία πίνακα περιεχομένων στο Aspose.Words για Java


## Εισαγωγή στη δημιουργία πίνακα περιεχομένων στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία δημιουργίας Πίνακα Περιεχομένων (TOC) χρησιμοποιώντας το Aspose.Words για Java. Το TOC είναι ένα κρίσιμο χαρακτηριστικό για τη δημιουργία οργανωμένων εγγράφων. Θα καλύψουμε πώς να προσαρμόσετε την εμφάνιση και τη διάταξη του TOC.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε εγκαταστήσει και ρυθμίσει το Aspose.Words for Java στο έργο σας Java.

## Βήμα 1: Δημιουργήστε ένα νέο έγγραφο

Αρχικά, ας δημιουργήσουμε ένα νέο έγγραφο για να εργαστούμε.

```java
Document doc = new Document();
```

## Βήμα 2: Προσαρμόστε τα στυλ TOC

Για να προσαρμόσετε την εμφάνιση του TOC σας, μπορείτε να τροποποιήσετε τα στυλ που σχετίζονται με αυτό. Σε αυτό το παράδειγμα, θα κάνουμε έντονες τις καταχωρήσεις TOC πρώτου επιπέδου.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Βήμα 3: Προσθέστε περιεχόμενο στο έγγραφό σας

Μπορείτε να προσθέσετε το περιεχόμενό σας στο έγγραφο. Αυτό το περιεχόμενο θα χρησιμοποιηθεί για τη δημιουργία του TOC.

## Βήμα 4: Δημιουργήστε το TOC

Για να δημιουργήσετε το TOC, εισαγάγετε ένα πεδίο TOC στην επιθυμητή θέση στο έγγραφό σας. Αυτό το πεδίο θα συμπληρωθεί αυτόματα με βάση τις επικεφαλίδες και τα στυλ στο έγγραφό σας.

```java
// Εισαγάγετε ένα πεδίο TOC στην επιθυμητή θέση στο έγγραφό σας.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Βήμα 5: Αποθηκεύστε το έγγραφο

Τέλος, αποθηκεύστε το έγγραφο με το TOC.

```java
doc.save("your_output_path_here");
```

## Προσαρμογή καρτελών στο TOC

Μπορείτε επίσης να προσαρμόσετε τις καρτέλες στο TOC σας για να ελέγξετε τη διάταξη των αριθμών σελίδων. Δείτε πώς μπορείτε να αλλάξετε τις στάσεις καρτελών:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Αποκτήστε την πρώτη καρτέλα που χρησιμοποιείται σε αυτήν την παράγραφο, η οποία ευθυγραμμίζει τους αριθμούς σελίδων.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Αφαιρέστε την παλιά καρτέλα.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Εισαγάγετε μια νέα καρτέλα σε μια τροποποιημένη θέση (π.χ. 50 μονάδες προς τα αριστερά).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Τώρα έχετε έναν προσαρμοσμένο Πίνακα περιεχομένων στο έγγραφό σας με προσαρμοσμένες στάσεις καρτελών για τη στοίχιση αριθμού σελίδας.


## Σύναψη

Σε αυτό το σεμινάριο, εξερευνήσαμε πώς να δημιουργήσετε έναν Πίνακα Περιεχομένων (TOC) χρησιμοποιώντας το Aspose.Words για Java, μια ισχυρή βιβλιοθήκη για εργασία με έγγραφα του Word. Ένα καλά δομημένο TOC είναι απαραίτητο για την οργάνωση και την πλοήγηση μεγάλων εγγράφων και το Aspose.Words παρέχει τα εργαλεία για τη δημιουργία και την προσαρμογή των TOC χωρίς κόπο.

## Συχνές ερωτήσεις

### Πώς μπορώ να αλλάξω τη μορφοποίηση των καταχωρήσεων TOC;

 Μπορείτε να τροποποιήσετε τα στυλ που σχετίζονται με τα επίπεδα TOC χρησιμοποιώντας`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, όπου X είναι το επίπεδο TOC.

### Πώς μπορώ να προσθέσω περισσότερα επίπεδα στο TOC μου;

Για να συμπεριλάβετε περισσότερα επίπεδα στο TOC σας, μπορείτε να τροποποιήσετε το πεδίο TOC και να καθορίσετε τον επιθυμητό αριθμό επιπέδων.

### Μπορώ να αλλάξω τις θέσεις τερματισμού καρτελών για συγκεκριμένες καταχωρήσεις TOC;

Ναι, όπως φαίνεται στο παραπάνω παράδειγμα κώδικα, μπορείτε να αλλάξετε τις θέσεις στοπ καρτελών για συγκεκριμένες καταχωρήσεις TOC επαναλαμβάνοντας τις παραγράφους και τροποποιώντας τις θέσεις καρτελών ανάλογα.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
