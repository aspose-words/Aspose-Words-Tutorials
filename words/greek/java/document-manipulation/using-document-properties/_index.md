---
date: 2026-01-16
description: Μάθετε πώς να μετατρέπετε ίντσες σε πόντους, να διαβάζετε τα μεταδεδομένα
  εγγράφου Java, να προσθέτετε προσαρμοσμένες ιδιότητες Java και να ορίζετε περιθώρια
  σελίδας Java με το Aspose.Words for Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Μετατροπή ιντσών σε πόντους – Χρήση ιδιοτήτων εγγράφου στο Aspose.Words για
  Java
url: /el/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή ίντσων σε σημεία – Χρήση ιδιοτήτων εγγράφου στο Aspose.Words for Java

## Quick Answers
- **Πώς μετατρέπω ίντσες σε σημεία;** Χρησιμοποιήστε `ConvertUtil.inchToPoint(value)` από το Aspose.Words.
- **Μπορώ να διαβάσω μεταδεδομένα εγγράφου σε Java;** Ναι – καλέστε `doc.getBuiltInDocumentProperties()` ή `doc.getCustomDocumentProperties()`.
- **Πώς προσθέτω προσαρμοσμένη ιδιότητα σε Java;** Χρησιμοποιήστε `doc.getCustomDocumentProperties().add(name, value)`.
- **Ποια μέθοδος ορίζει τα περιθώρια σε σημεία;** `PageSetup.setTopMargin`, `setBottomMargin`, κ.λπ., δέχονται τιμές σε σημεία.
- **Υποστηρίζεται η σύνδεση σε σελιδοδείκτη;** Ναι – χρησιμοποιήστε `addLinkToContent` στη συλλογή προσαρμοσμένων ιδιοτήτων.

## Introduction to Document Properties

Οι ιδιότητες εγγράφου είναι ένα ζωτικό μέρος κάθε αρχείου Word. Αποθηκεύουν πληροφορίες όπως τίτλος, συγγραφέας, θέμα, λέξεις‑κλειδιά και τυχόν προσαρμοσμένα μεταδεδομένα που χρειάζεστε για επεξεργασία downstream. Στο Aspose.Words for Java μπορείτε να χειριστείτε τόσο ενσωματωμένες όσο και προσαρμοσμένες ιδιότητες εγγράφου, και μπορείτε επίσης να ελέγχετε λεπτομέρειες διάταξης όπως τα περιθώρια μετατρέποντας μονάδες μέτρησης (π.χ., **convert inches to points**).

## What is “convert inches to points”?

Στο Word, οι μετρήσεις διάταξης εκφράζονται σε σημεία (1 σημείο = 1/72 ίντσας). Η μετατροπή ίντσων σε σημεία σας επιτρέπει να ορίζετε περιθώρια, εσοχές και διαστήματα χρησιμοποιώντας γνωστές αυτοκρατορικές μονάδες, ενώ το API εργάζεται εσωτερικά με σημεία.

## Why manage document metadata in Java?

Η ενσωμάτωση μεταδεδομένων διευκολύνει την αναζήτηση, την κατηγοριοποίηση και την αυτοματοποίηση των ροών εργασίας. Για παράδειγμα, μπορείτε να επισημάνετε μια σύμβαση με μια σημαία “Authorized” ή να αποθηκεύσετε έναν αριθμό αναθεώρησης για τα αρχεία ελέγχου. Η ανάγνωση και η εγγραφή αυτών των πληροφοριών προγραμματιστικά εξασφαλίζει συνέπεια σε μεγάλες παρτίδες εγγράφων.

## Prerequisites
- Java 17+ (ή συμβατό JDK)
- Βιβλιοθήκη Aspose.Words for Java προστιθέμενη στο έργο σας (Maven/Gradle)
- Ένα δείγμα αρχείου `.docx` (π.χ., `Properties.docx`) τοποθετημένο σε προσβάσιμο κατάλογο

## Step‑by‑Step Guide

### Enumerating Built‑in Document Properties
Ακολουθεί ένα απλό τεστ που ανοίγει ένα έγγραφο και εκτυπώνει όλες τις ενσωματωμένες ιδιότητες όπως Τίτλος, Συγγραφέας και Λέξεις‑Κλειδιά.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Συμβουλή:** Χρησιμοποιήστε αυτό το απόσπασμα για να επαληθεύσετε ότι τα μεταδεδομένα σας γράφτηκαν σωστά στα προηγούμενα βήματα.

### Adding Custom Document Properties (add custom properties java)
Οι προσαρμοσμένες ιδιότητες σας επιτρέπουν να αποθηκεύετε οποιονδήποτε τύπο δεδομένων χρειάζεστε—boolean, string, date, number κ.λπ.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Γιατί είναι σημαντικό:** Η προσθήκη μιας σημαίας όπως **Authorized** μπορεί να καθοδηγήσει ροές έγκρισης downstream χωρίς να τροποποιήσει το περιεχόμενο του εγγράφου.

### Removing a Custom Property
Εάν μια ιδιότητα δεν χρειάζεται πλέον, μπορείτε να τη διαγράψετε καθαρά.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configuring a Link to Content (bookmark linking)
Μπορείτε να δημιουργήσετε έναν σελιδοδείκτη και στη συνέχεια να προσθέσετε μια προσαρμοσμένη ιδιότητα που δείχνει σε αυτόν τον σελιδοδείκτη, ενεργοποιώντας δυναμικές διασταυρούμενες αναφορές.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Converting Between Measurement Units (set page margins java)
Εδώ όπου η κύρια λέξη‑κλειδί λάμπει. Ορίζουμε τα περιθώρια σε ίντσες, έπειτα **convert inches to points** χρησιμοποιώντας το `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Σημείωση:** Το `ConvertUtil` παρέχει επίσης `pointToInch`, `mmToPoint`, κ.λπ., για ευέλικτο χειρισμό διάταξης.

### Using Control Characters (read document metadata java)
Οι χαρακτήρες ελέγχου σας βοηθούν να καθαρίσετε τα ροές κειμένου. Αυτό το παράδειγμα αντικαθιστά μια επιστροφή καρτέλας (`\r`) με τη σειρά αλλαγής γραμμής των Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Common Issues & Solutions

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Τα περιθώρια φαίνονται λανθασμένα μετά τη μετατροπή | Χρήση λανθασμένης μονάδας (π.χ., cm αντί για ίντσες) | Επαληθεύστε ότι καλείτε `ConvertUtil.inchToPoint` για τιμές σε ίντσες |
| Η προσαρμοσμένη ιδιότητα δεν εμφανίζεται | Η ιδιότητα προστέθηκε μετά την αποθήκευση του εγγράφου | Καλέστε `doc.save(...)` μετά την προσθήκη ιδιοτήτων |
| Ο σύνδεσμος σελιδοδείκτη σπασμένος | Λάθος ονομασία σελιδοδείκτη | Βεβαιωθείτε ότι το όνομα του σελιδοδείκτη ταιριάζει ακριβώς στο `addLinkToContent` |

## FAQ's

### How do I access built-in document properties?

Για να αποκτήσετε πρόσβαση στις ενσωματωμένες ιδιότητες εγγράφου στο Aspose.Words for Java, μπορείτε να χρησιμοποιήσετε τη μέθοδο `getBuiltInDocumentProperties` στο αντικείμενο `Document`. Αυτή η μέθοδος επιστρέφει μια συλλογή ενσωματωμένων ιδιοτήτων που μπορείτε να διατρέξετε.

### Can I add custom document properties to a document?

Ναι, μπορείτε να προσθέσετε προσαρμοσμένες ιδιότητες εγγράφου σε ένα έγγραφο χρησιμοποιώντας τη συλλογή `CustomDocumentProperties`. Μπορείτε να ορίσετε προσαρμοσμένες ιδιότητες με διάφορους τύπους δεδομένων, συμπεριλαμβανομένων strings, booleans, dates και numeric values.

### How can I remove a specific custom document property?

Για να αφαιρέσετε μια συγκεκριμένη προσαρμοσμένη ιδιότητα εγγράφου, μπορείτε να χρησιμοποιήσετε τη μέθοδο `remove` στη συλλογή `CustomDocumentProperties`, περνώντας το όνομα της ιδιότητας που θέλετε να αφαιρέσετε ως παράμετρο.

### What is the purpose of linking to content within a document?

Η σύνδεση σε περιεχόμενο μέσα σε ένα έγγραφο σας επιτρέπει να δημιουργήσετε δυναμικές αναφορές σε συγκεκριμένα τμήματα του εγγράφου. Αυτό μπορεί να είναι χρήσιμο για τη δημιουργία διαδραστικών εγγράφων ή διασταυρούμενων αναφορών μεταξύ ενοτήτων.

### How can I convert between different measurement units in Aspose.Words for Java?

Μπορείτε να μετατρέψετε μεταξύ διαφορετικών μονάδων μέτρησης στο Aspose.Words for Java χρησιμοποιώντας την κλάση `ConvertUtil`. Παρέχει μεθόδους για μετατροπή μονάδων όπως ίντσες σε σημεία, σημεία σε εκατοστά κ.λπ.

## Frequently Asked Questions

**Q: Πώς διαβάζω μεταδεδομένα εγγράφου Java χωρίς να φορτώσω ολόκληρο το αρχείο;**  
A: Χρησιμοποιήστε το `DocumentInfo` για να ανακτήσετε τις βασικές ιδιότητες χωρίς να φορτώσετε πλήρως το περιεχόμενο του εγγράφου.

**Q: Μπορώ να ορίσω προγραμματιστικά τα περιθώρια σελίδας Java για υπάρχοντα έγγραφα;**  
A: Ναι—ανοίξτε το έγγραφο, τροποποιήστε τα περιθώρια `PageSetup` (μετατρέψτε ίντσες σε σημεία αν χρειάζεται) και αποθηκεύστε.

**Q: Είναι δυνατόν να εξάγετε προσαρμοσμένες ιδιότητες σε μεταδεδομένα PDF;**  
A: Κατά την αποθήκευση σε PDF, το Aspose.Words αντιστοιχίζει αυτόματα τις προσαρμοσμένες ιδιότητες εγγράφου σε προσαρμοσμένα μεταδεδομένα PDF.

**Q: Επηρεάζουν οι χαρακτήρες ελέγχου τη μετατροπή σε PDF;**  
A: Διατηρούνται κατά τη μετατροπή· ωστόσο, ίσως θέλετε να ομαλοποιήσετε τα τέλη γραμμής για συνέπεια.

**Q: Ποια έκδοση του Aspose.Words απαιτείται για το `ConvertUtil`;**  
A: Το `ConvertUtil` είναι διαθέσιμο από το Aspose.Words 16.5· οποιαδήποτε πρόσφατη έκδοση το υποστηρίζει.

## Conclusion

Με την εξοικείωση με **convert inches to points**, την ανάγνωση μεταδεδομένων εγγράφου Java και την προσθήκη προσαρμοσμένων ιδιοτήτων Java, αποκτάτε πλήρη έλεγχο τόσο της οπτικής διάταξης όσο και των κρυφών δεδομένων των αρχείων Word σας. Αυτές οι δυνατότητες σας επιτρέπουν να δημιουργήσετε αυτοματοποιημένες αγωγές εγγράφων, να επιβάλετε συμμόρφωση και να δημιουργήσετε πλούσια μορφοποιημένες αναφορές—όλα με το Aspose.Words for Java.

---

**Τελευταία ενημέρωση:** 2026-01-16  
**Δοκιμή με:** Aspose.Words for Java 24.11  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}