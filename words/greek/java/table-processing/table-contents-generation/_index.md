---
title: Πίνακας περιεχομένων Δημιουργία
linktitle: Πίνακας περιεχομένων Δημιουργία
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να δημιουργείτε δυναμικό πίνακα περιεχομένων χρησιμοποιώντας το Aspose.Words για Java. Κύρια δημιουργία TOC με βήμα προς βήμα καθοδήγηση και παραδείγματα πηγαίου κώδικα.
weight: 14
url: /el/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πίνακας περιεχομένων Δημιουργία

## Εισαγωγή

Δυσκολευτήκατε ποτέ να δημιουργήσετε έναν δυναμικό και επαγγελματικό Πίνακα Περιεχομένων (TOC) στα έγγραφά σας στο Word; Μην ψάχνετε άλλο! Με το Aspose.Words για Java, μπορείτε να αυτοματοποιήσετε ολόκληρη τη διαδικασία, εξοικονομώντας χρόνο και διασφαλίζοντας την ακρίβεια. Είτε δημιουργείτε μια ολοκληρωμένη έκθεση είτε μια ακαδημαϊκή εργασία, αυτό το σεμινάριο θα σας καθοδηγήσει στη δημιουργία ενός TOC μέσω προγραμματισμού με Java. Είστε έτοιμοι να βουτήξετε; Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν ξεκινήσουμε την κωδικοποίηση, βεβαιωθείτε ότι έχετε τα εξής:

1.  Java Development Kit (JDK): Εγκατεστημένο στο σύστημά σας. Μπορείτε να το κατεβάσετε από[Ο ιστότοπος της Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words for Java Library: Κάντε λήψη της πιο πρόσφατης έκδοσης από το[σελίδα έκδοσης](https://releases.aspose.com/words/java/).
3. Ενσωματωμένο περιβάλλον ανάπτυξης (IDE): Όπως το IntelliJ IDEA, το Eclipse ή το NetBeans.
4.  Aspose Temporary License: Για να αποφύγετε περιορισμούς αξιολόγησης, αποκτήστε α[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/).

## Εισαγωγή πακέτων

Για να χρησιμοποιήσετε αποτελεσματικά το Aspose.Words για Java, βεβαιωθείτε ότι εισάγετε τις απαιτούμενες κλάσεις. Εδώ είναι οι εισαγωγές:

```java
import com.aspose.words.*;
```

Ακολουθήστε αυτά τα βήματα για να δημιουργήσετε ένα δυναμικό TOC στο έγγραφο του Word.

## Βήμα 1: Αρχικοποιήστε το Document και το DocumentBuilder

 Το πρώτο βήμα είναι να δημιουργήσετε ένα νέο έγγραφο και να χρησιμοποιήσετε το`DocumentBuilder` τάξη για να το χειραγωγήσουν.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Αντιπροσωπεύει το έγγραφο του Word.
- `DocumentBuilder`: Μια βοηθητική κλάση που επιτρέπει τον εύκολο χειρισμό του εγγράφου.

## Βήμα 2: Εισαγάγετε τον Πίνακα Περιεχομένων

Τώρα, ας εισαγάγουμε το TOC στην αρχή του εγγράφου.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Εισάγει ένα πεδίο TOC. Οι παράμετροι καθορίζουν:
  - `\o "1-3"`: Συμπεριλάβετε επικεφαλίδες των επιπέδων 1 έως 3.
  - `\h`: Δημιουργήστε υπερσυνδέσμους καταχωρήσεων.
  - `\z`: Καταργήστε αριθμούς σελίδων για έγγραφα web.
  - `\u`: Διατήρηση στυλ για υπερσυνδέσμους.
- `insertBreak`: Προσθέτει μια αλλαγή σελίδας μετά το TOC.

## Βήμα 3: Προσθέστε επικεφαλίδες για να συμπληρώσετε το TOC

Για να συμπληρώσετε το TOC, πρέπει να προσθέσετε παραγράφους με στυλ επικεφαλίδων.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Ορίζει το στυλ της παραγράφου σε ένα συγκεκριμένο επίπεδο επικεφαλίδας (π.χ.`HEADING_1`, `HEADING_2`).
- `writeln`: Προσθέτει κείμενο στο έγγραφο με το καθορισμένο στυλ.

## Βήμα 4: Προσθέστε ένθετες επικεφαλίδες

Για να δείξετε τα επίπεδα TOC, συμπεριλάβετε ένθετες επικεφαλίδες.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Προσθέστε επικεφαλίδες βαθύτερων επιπέδων για να εμφανίσετε την ιεραρχία στο TOC.

## Βήμα 5: Ενημερώστε τα πεδία TOC

Το πεδίο TOC πρέπει να ενημερωθεί για να εμφανίζονται οι πιο πρόσφατες επικεφαλίδες.


```java
doc.updateFields();
```

- `updateFields`: Ανανεώνει όλα τα πεδία του εγγράφου, διασφαλίζοντας ότι το TOC αντικατοπτρίζει τις επικεφαλίδες που προστέθηκαν.

## Βήμα 6: Αποθηκεύστε το έγγραφο

Τέλος, αποθηκεύστε το έγγραφο στην επιθυμητή μορφή.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Εξάγει το έγγραφο σε a`.docx` αρχείο. Μπορείτε να καθορίσετε άλλες μορφές όπως`.pdf` ή`.txt` αν χρειαστεί.

## Σύναψη

Συγχαρητήρια! Δημιουργήσατε με επιτυχία έναν δυναμικό πίνακα περιεχομένων σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για Java. Με λίγες μόνο γραμμές κώδικα, έχετε αυτοματοποιήσει μια εργασία που διαφορετικά θα μπορούσε να διαρκέσει ώρες. Λοιπόν, τι ακολουθεί; Δοκιμάστε να πειραματιστείτε με διαφορετικά στυλ και μορφές επικεφαλίδων για να προσαρμόσετε το TOC σας στις συγκεκριμένες ανάγκες.

## Συχνές ερωτήσεις

### Μπορώ να προσαρμόσω περαιτέρω τη μορφή TOC;
Απολύτως! Μπορείτε να προσαρμόσετε τις παραμέτρους TOC, όπως τη συμπερίληψη αριθμών σελίδων, τη στοίχιση κειμένου ή τη χρήση προσαρμοσμένων στυλ επικεφαλίδων.

### Είναι υποχρεωτική η άδεια χρήσης για το Aspose.Words για Java;
 Ναι, απαιτείται άδεια για πλήρη λειτουργικότητα. Μπορείτε να ξεκινήσετε με α[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/).

### Μπορώ να δημιουργήσω ένα TOC για ένα υπάρχον έγγραφο;
 Ναί! Φορτώστε το έγγραφο σε α`Document` και ακολουθήστε τα ίδια βήματα για να εισαγάγετε και να ενημερώσετε το TOC.

### Λειτουργεί αυτό για εξαγωγές PDF;
 Ναι, το TOC θα εμφανιστεί στο PDF εάν αποθηκεύσετε το έγγραφο`.pdf` σχήμα και διάταξις βιβλίου.

### Πού μπορώ να βρω περισσότερα έγγραφα;
 Ελέγξτε το[Aspose.Words για τεκμηρίωση Java](https://reference.aspose.com/words/java/) για περισσότερα παραδείγματα και λεπτομέρειες.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
