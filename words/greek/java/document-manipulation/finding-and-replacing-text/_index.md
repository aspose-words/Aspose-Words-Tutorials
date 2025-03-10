---
title: Εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java
linktitle: Εύρεση και αντικατάσταση κειμένου
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να βρίσκετε και να αντικαθιστάτε κείμενο σε έγγραφα του Word με το Aspose.Words για Java. Οδηγός βήμα προς βήμα με παραδείγματα κώδικα. Βελτιώστε τις δεξιότητες χειρισμού εγγράφων Java.
weight: 15
url: /el/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java


## Εισαγωγή στην εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java

Το Aspose.Words for Java είναι ένα ισχυρό Java API που σας επιτρέπει να εργάζεστε με έγγραφα του Word μέσω προγραμματισμού. Μία από τις κοινές εργασίες όταν ασχολούμαστε με έγγραφα του Word είναι η εύρεση και η αντικατάσταση κειμένου. Είτε θέλετε να ενημερώσετε τα σύμβολα κράτησης θέσης σε πρότυπα είτε να εκτελέσετε πιο σύνθετους χειρισμούς κειμένου, το Aspose.Words για Java μπορεί να σας βοηθήσει να επιτύχετε τους στόχους σας αποτελεσματικά.

## Προαπαιτούμενα

Πριν βουτήξουμε στις λεπτομέρειες της εύρεσης και αντικατάστασης κειμένου, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Περιβάλλον Ανάπτυξης Java
- Aspose.Words για βιβλιοθήκη Java
- Ένα δείγμα εγγράφου του Word για εργασία

 Μπορείτε να κάνετε λήψη της βιβλιοθήκης Aspose.Words for Java από[εδώ](https://releases.aspose.com/words/java/).

## Εύρεση και αντικατάσταση απλού κειμένου

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε ένα DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Εύρεση και αντικατάσταση κειμένου
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

 Σε αυτό το παράδειγμα, φορτώνουμε ένα έγγραφο του Word, δημιουργούμε ένα`DocumentBuilder` και χρησιμοποιήστε το`replace` μέθοδος εύρεσης και αντικατάστασης του "παλιού κειμένου" με "νέου κειμένου" εντός του εγγράφου.

## Χρήση κανονικών εκφράσεων

Οι κανονικές εκφράσεις παρέχουν ισχυρές δυνατότητες αντιστοίχισης προτύπων για αναζήτηση και αντικατάσταση κειμένου. Το Aspose.Words για Java υποστηρίζει τυπικές εκφράσεις για πιο προηγμένες λειτουργίες εύρεσης και αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε ένα DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Χρησιμοποιήστε κανονικές εκφράσεις για εύρεση και αντικατάσταση κειμένου
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε ένα τυπικό μοτίβο έκφρασης για να βρούμε και να αντικαταστήσουμε κείμενο μέσα στο έγγραφο.

## Παράβλεψη κειμένου εντός πεδίων

Μπορείτε να διαμορφώσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα στα πεδία κατά την εκτέλεση λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε τα IgnoreFields σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό είναι χρήσιμο όταν θέλετε να εξαιρέσετε το κείμενο μέσα σε πεδία, όπως πεδία συγχώνευσης, από την αντικατάσταση.

## Παράβλεψη κειμένου στο εσωτερικό Διαγραφή αναθεωρήσεων

Μπορείτε να διαμορφώσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα στις αναθεωρήσεις διαγραφής κατά τις λειτουργίες εύρεσης και αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε το IgnoreDeleted σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να αποκλείσετε την αντικατάσταση κειμένου που έχει επισημανθεί για διαγραφή στις παρακολουθούμενες αλλαγές.

## Παράβλεψη κειμένου μέσα στις αναθεωρήσεις εισαγωγής

Μπορείτε να διαμορφώσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα στις αναθεωρήσεις εισαγωγής κατά τη διάρκεια λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε το IgnoreInserted σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εξαιρέσετε από την αντικατάσταση κείμενο που έχει επισημανθεί ότι έχει εισαχθεί στις παρακολουθούμενες αλλαγές.

## Αντικατάσταση κειμένου με HTML

Μπορείτε να χρησιμοποιήσετε το Aspose.Words για Java για να αντικαταστήσετε κείμενο με περιεχόμενο HTML.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions με μια προσαρμοσμένη αντικατάσταση επανάκλησης
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

 Σε αυτό το παράδειγμα, χρησιμοποιούμε μια προσαρμογή`ReplaceWithHtmlEvaluator` αντικατάσταση κειμένου με περιεχόμενο HTML.

## Αντικατάσταση κειμένου σε κεφαλίδες και υποσέλιδα

Μπορείτε να βρείτε και να αντικαταστήσετε κείμενο στις κεφαλίδες και τα υποσέλιδα του εγγράφου του Word.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Αποκτήστε τη συλλογή κεφαλίδων και υποσέλιδων
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Επιλέξτε τον τύπο κεφαλίδας ή υποσέλιδου στον οποίο θέλετε να αντικαταστήσετε το κείμενο (π.χ. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Δημιουργήστε μια παρουσία FindReplaceOptions και εφαρμόστε την στην περιοχή του υποσέλιδου
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να πραγματοποιείτε αντικαταστάσεις κειμένου ειδικά σε κεφαλίδες και υποσέλιδα.

## Εμφάνιση αλλαγών για παραγγελίες κεφαλίδας και υποσέλιδου

Μπορείτε να χρησιμοποιήσετε το Aspose.Words για να εμφανίσετε αλλαγές για παραγγελίες κεφαλίδας και υποσέλιδου στο έγγραφό σας.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Αποκτήστε την πρώτη ενότητα
Section firstPageSection = doc.getFirstSection();

//Δημιουργήστε μια παρουσία FindReplaceOptions και εφαρμόστε την στην περιοχή του εγγράφου
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Αντικαταστήστε το κείμενο που επηρεάζει τις παραγγελίες κεφαλίδων και υποσέλιδων
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να οπτικοποιήσετε τις αλλαγές που σχετίζονται με τις παραγγελίες κεφαλίδας και υποσέλιδου στο έγγραφό σας.

## Αντικατάσταση κειμένου με πεδία

Μπορείτε να αντικαταστήσετε κείμενο με πεδία χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε μια προσαρμοσμένη αντικατάσταση επανάκλησης για πεδία
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

 Σε αυτό το παράδειγμα, αντικαθιστούμε κείμενο με πεδία και καθορίζουμε τον τύπο του πεδίου (π.χ.`FieldType.FIELD_MERGE_FIELD`).

## Αντικατάσταση με αξιολογητή

Μπορείτε να χρησιμοποιήσετε έναν προσαρμοσμένο αξιολογητή για να προσδιορίσετε δυναμικά το κείμενο αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε μια προσαρμοσμένη αντικατάσταση επανάκλησης
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε έναν προσαρμοσμένο αξιολογητή (`MyReplaceEvaluator`) για αντικατάσταση κειμένου.

## Αντικατάσταση με Regex

Το Aspose.Words για Java σάς επιτρέπει να αντικαταστήσετε κείμενο χρησιμοποιώντας κανονικές εκφράσεις.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Χρησιμοποιήστε κανονικές εκφράσεις για εύρεση και αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε ένα τυπικό μοτίβο έκφρασης για να βρούμε και να αντικαταστήσουμε κείμενο μέσα στο έγγραφο.

## Αναγνώριση και αντικαταστάσεις εντός προτύπων αντικατάστασης

Μπορείτε να αναγνωρίσετε και να κάνετε αντικαταστάσεις σε μοτίβα αντικατάστασης χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions με το UseSubstitutions να έχει οριστεί σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου με μοτίβο
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να πραγματοποιείτε αντικαταστάσεις εντός των μοτίβων αντικατάστασης για πιο προχωρημένες αντικαταστάσεις.

## Αντικατάσταση με String

Μπορείτε να αντικαταστήσετε το κείμενο με μια απλή συμβολοσειρά χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Αντικαταστήστε το κείμενο με μια συμβολοσειρά
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, αντικαθιστούμε το "text-to-replace" με το "new-string" μέσα στο έγγραφο.

## Χρήση παραγγελιών παλαιού τύπου

Μπορείτε να χρησιμοποιήσετε εντολή παλαιού τύπου κατά την εκτέλεση εργασιών εύρεσης και αντικατάστασης.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε το UseLegacyOrder σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Χρησιμοποιήστε επιλογές κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να χρησιμοποιείτε παραγγελίες παλαιού τύπου για λειτουργίες εύρεσης και αντικατάστασης.

## Αντικατάσταση κειμένου σε πίνακα

Μπορείτε να βρείτε και να αντικαταστήσετε κείμενο μέσα σε πίνακες στο έγγραφο του Word.

```java
// Φορτώστε το έγγραφο
Document doc = new Document("your-document.docx");

// Λάβετε έναν συγκεκριμένο πίνακα (π.χ. τον πρώτο πίνακα)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Χρησιμοποιήστε το FindReplaceOptions για να αντικαταστήσετε το κείμενο στον πίνακα
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Αποθηκεύστε το τροποποιημένο έγγραφο
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να πραγματοποιείτε αντικαταστάσεις κειμένου ειδικά μέσα σε πίνακες.

## Σύναψη

Το Aspose.Words για Java παρέχει ολοκληρωμένες δυνατότητες εύρεσης και αντικατάστασης κειμένου σε έγγραφα του Word. Είτε χρειάζεται να εκτελέσετε απλές αντικαταστάσεις κειμένου είτε πιο προηγμένες λειτουργίες χρησιμοποιώντας κανονικές εκφράσεις, χειρισμούς πεδίου ή προσαρμοσμένους αξιολογητές, το Aspose.Words για Java σας καλύπτει. Φροντίστε να εξερευνήσετε την εκτενή τεκμηρίωση και τα παραδείγματα που παρέχονται από την Aspose για να αξιοποιήσετε πλήρως τις δυνατότητες αυτής της πανίσχυρης βιβλιοθήκης Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να κατεβάσω το Aspose.Words για Java;

 Μπορείτε να κατεβάσετε το Aspose.Words για Java από τον ιστότοπο επισκεπτόμενοι[αυτόν τον σύνδεσμο](https://releases.aspose.com/words/java/).

### Μπορώ να χρησιμοποιήσω τυπικές εκφράσεις για αντικατάσταση κειμένου;

Ναι, μπορείτε να χρησιμοποιήσετε κανονικές εκφράσεις για αντικατάσταση κειμένου στο Aspose.Words για Java. Αυτό σας επιτρέπει να εκτελείτε πιο προηγμένες και ευέλικτες λειτουργίες εύρεσης και αντικατάστασης.

### Πώς μπορώ να αγνοήσω το κείμενο μέσα στα πεδία κατά την αντικατάσταση;

Για να αγνοήσετε το κείμενο μέσα στα πεδία κατά την αντικατάσταση, μπορείτε να ορίσετε το`IgnoreFields` ιδιοκτησία του`FindReplaceOptions` να`true`. Αυτό διασφαλίζει ότι το κείμενο εντός πεδίων, όπως τα πεδία συγχώνευσης, εξαιρείται από την αντικατάσταση.

### Μπορώ να αντικαταστήσω το κείμενο μέσα στις κεφαλίδες και τα υποσέλιδα;

 Ναι, μπορείτε να αντικαταστήσετε κείμενο μέσα στις κεφαλίδες και τα υποσέλιδα του εγγράφου του Word. Απλώς αποκτήστε πρόσβαση στην κατάλληλη κεφαλίδα ή υποσέλιδο και χρησιμοποιήστε το`replace` μέθοδο με την επιθυμητή`FindReplaceOptions`.

### Σε τι χρησιμεύει η επιλογή UseLegacyOrder;

 Ο`UseLegacyOrder` επιλογή σε`FindReplaceOptions` σας επιτρέπει να χρησιμοποιείτε παραγγελίες παλαιού τύπου όταν εκτελείτε λειτουργίες εύρεσης και αντικατάστασης. Αυτό μπορεί να είναι χρήσιμο σε ορισμένα σενάρια όπου είναι επιθυμητή η συμπεριφορά παραγγελιών παλαιού τύπου.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
