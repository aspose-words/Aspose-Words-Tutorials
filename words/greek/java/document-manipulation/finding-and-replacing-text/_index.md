---
date: 2026-01-03
description: Μάθετε πώς να αντικαθιστάτε κείμενο με HTML σε έγγραφα Word χρησιμοποιώντας
  το Aspose.Words for Java. Οδηγός βήμα‑προς‑βήμα με παραδείγματα κώδικα, συμβουλές
  για αντικατάσταση κειμένου με regex σε Java και πολλά άλλα.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: Αντικατάσταση κειμένου με HTML χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# replace text with html in Aspose.Words for Java

## Introduction to Finding and Replacing Text in Aspose.Words for Java

Το Aspose.Words for Java είναι ένα ισχυρό Java API που σας επιτρέπει να χειρίζεστε έγγραφα Word προγραμματιστικά. Μία από τις πιο κοινές εργασίες είναι **replace text with html**, είτε ενημερώνετε placeholders σε ένα πρότυπο, είτε ενσωματώνετε στυλιζαρισμένο περιεχόμενο, είτε εκτελείτε μαζικές μετατροπές κειμένου. Σε αυτόν τον οδηγό θα δούμε πώς να αντικαταστήσετε κείμενο, πώς να χρησιμοποιήσετε regex replace text java, και ακόμη πώς να αντικαταστήσετε κείμενο σε headers—όλα ενώ διατηρείτε τον κώδικά σας καθαρό και αποδοτικό.

## Quick Answers
- **Ποια είναι η κύρια μέθοδος για replace text with html;** Χρησιμοποιήστε το `FindReplaceOptions` με ένα προσαρμοσμένο callback όπως το `ReplaceWithHtmlEvaluator`.  
- **Μπορώ να αγνοήσω τα fields κατά την αντικατάσταση;** Ναι – ορίστε `options.setIgnoreFields(true)`.  
- **Χρειάζομαι άδεια για παραγωγική χρήση;** Απαιτείται έγκυρη άδεια Aspose.Words για εμπορικές αναπτύξεις.  
- **Ποια έκδοση Java υποστηρίζεται;** Το Aspose.Words for Java λειτουργεί με Java 8 και νεότερες.  
- **Υποστηρίζεται το regex replace text java;** Απόλυτα – περάστε ένα αντικείμενο `Pattern` στη μέθοδο `replace`.  

## What is “replace text with html”?

Τι είναι το “replace text with html”;  
Η αντικατάσταση κειμένου με HTML σημαίνει την αντικατάσταση ενός placeholder απλού κειμένου με πλούσιο HTML markup (πίνακες, λίστες, στυλ) διατηρώντας τη δομή του περιβάλλοντος εγγράφου Word. Το Aspose.Words αναλύει το HTML και εισάγει τα αντίστοιχα αντικείμενα Word, παρέχοντάς σας πλήρη έλεγχο πάνω στην τελική διάταξη.

## Why use Aspose.Words for this task?

Γιατί να χρησιμοποιήσετε το Aspose.Words για αυτήν την εργασία;
- **Full Word fidelity** – η βιβλιοθήκη διατηρεί όλη τη μορφοποίηση, τα headers, footers και τις παρακολουθούμενες αλλαγές ανέπαφες.  
- **Built‑in regex support** – ιδανικό για σύνθετα μοτίβα αναζήτησης (`regex replace text java`).  
- **Fine‑grained control** – επιλογές όπως `IgnoreFields`, `IgnoreDeleted` και `UseLegacyOrder` σας επιτρέπουν να προσαρμόσετε τη λειτουργία στις ακριβείς ανάγκες σας.  
- **Cross‑platform** – λειτουργεί σε οποιοδήποτε OS που τρέχει Java.  

## Prerequisites

- Java Development Environment (JDK 8+)  
- Βιβλιοθήκη Aspose.Words for Java – κατεβάστε την από [εδώ](https://releases.aspose.com/words/java/).  
- Ένα δείγμα εγγράφου Word (`.docx`) για πειραματισμό.  

## Finding and Replacing Simple Text

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Αυτό το βασικό παράδειγμα δείχνει **πώς να αντικαταστήσετε κείμενο** χρησιμοποιώντας τη μέθοδο `replace`. Είναι η βάση για πιο προχωρημένα σενάρια.

## Using Regular Expressions (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Οι regular expressions σας παρέχουν ισχυρή αντιστοίχιση προτύπων, ιδανική για δυναμικά placeholders ή σύνθετα όρια λέξεων.

## Ignoring Text Inside Fields (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Ορίστε `IgnoreFields` για να διατηρήσετε τα merge fields, τους αριθμούς σελίδων ή άλλους κωδικούς πεδίων αμετάβλητους ενώ αντικαθιστάτε το περιβάλλον περιεχόμενο.

## Ignoring Text Inside Delete Revisions

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Αυτό αποτρέπει την τροποποίηση του κειμένου που έχει σημειωθεί για διαγραφή (tracked changes).

## Ignoring Text Inside Insert Revisions

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Χρήσιμο όταν θέλετε να διατηρήσετε το νεοεισαγμένο κείμενο αμετάβλητο κατά τη διάρκεια μιας μαζικής αντικατάστασης.

## Replacing Text with HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Εδώ **replace text with html** παρέχοντας έναν προσαρμοσμένο evaluator που αναλύει τη συμβολοσειρά HTML και εισάγει τους κατάλληλους κόμβους Word.

## Replacing Text in Headers and Footers (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Στοχευμένη αντικατάσταση μέσα σε headers ή footers εξασφαλίζει ότι η επωνυμία του εγγράφου σας παραμένει συνεπής.

## Showing Changes for Header and Footer Orders

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Αυτό το παράδειγμα καταγράφει αλλαγές, βοηθώντας σας να ελέγξετε τις τροποποιήσεις στην σειρά των headers/footers.

## Replacing Text with Fields

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Η ενσωμάτωση fields (π.χ., merge fields) σας επιτρέπει να δημιουργήσετε δυναμικά έγγραφα που μπορούν να συμπληρωθούν αργότερα.

## Replacing with an Evaluator

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Οι προσαρμοσμένοι evaluators σας δίνουν πλήρη προγραμματιστικό έλεγχο πάνω στο κείμενο αντικατάστασης.

## Replacing with Regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Ένας συνοπτικός τρόπος για την εκτέλεση αντικαταστάσεων βάσει προτύπων σε ολόκληρο το έγγραφο.

## Recognizing and Substitutions Within Replacement Patterns

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Ενεργοποιήστε το `UseSubstitutions` για να αναφέρετε ομάδες σύλληψης απευθείας στη συμβολοσειρά αντικατάστασης.

## Replacing with a String (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Η πιο απλή μορφή αντικατάστασης—ιδανική για στατικά placeholders.

## Using Legacy Order

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Η Legacy order μπορεί να είναι απαραίτητη όταν εργάζεστε με παλαιότερα έγγραφα που βασίζονται στην αρχική σειρά διάσχισης.

## Replacing Text in a Table

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Στοχευμένες αντικαταστάσεις μέσα σε πίνακες αποτρέπουν ανεπιθύμητες αλλαγές σε άλλα μέρη του εγγράφου.

## Common Issues and Solutions

- **HTML not rendering correctly** – Βεβαιωθείτε ότι το HTML είναι καλά δομημένο και περιλαμβάνει τις απαιτούμενες ετικέτες (π.χ., `<p>`, `<table>`).  
- **Regex not matching** – Θυμηθείτε να διαφύγετε τους ειδικούς χαρακτήρες και να χρησιμοποιήσετε `Pattern.CASE_INSENSITIVE` αν χρειάζεται.  
- **Fields being replaced unintentionally** – Ορίστε `options.setIgnoreFields(true)` για να τα προστατεύσετε.  
- **Performance on large documents** – Χρησιμοποιήστε `UseLegacyOrder` ή επεξεργαστείτε τις ενότητες ξεχωριστά για να μειώσετε το αποτύπωμα μνήμης.  

## Frequently Asked Questions

**Ε: Πώς μπορώ να κατεβάσω το Aspose.Words for Java;**  
Α: Μπορείτε να κατεβάσετε το Aspose.Words for Java από την ιστοσελίδα επισκεπτόμενοι [αυτόν τον σύνδεσμο](https://releases.aspose.com/words/java/).

**Ε: Μπορώ να χρησιμοποιήσω regular expressions για αντικατάσταση κειμένου;**  
Α: Ναι, μπορείτε να χρησιμοποιήσετε regular expressions για αντικατάσταση κειμένου στο Aspose.Words for Java. Αυτό σας επιτρέπει να εκτελείτε πιο προχωρημένες και ευέλικτες λειτουργίες εύρεσης και αντικατάστασης.

**Ε: Πώς μπορώ να αγνοήσω το κείμενο μέσα σε fields κατά την αντικατάσταση;**  
Α: Ορίστε την ιδιότητα `IgnoreFields` του `FindReplaceOptions` σε `true`. Αυτό εξαιρεί το περιεχόμενο των fields, όπως τα merge fields, από την αντικατάσταση.

**Ε: Είναι δυνατόν να αντικαταστήσω κείμενο μέσα σε headers και footers;**  
Α: Απόλυτα. Πρόσβαση στο επιθυμητό header ή footer μέσω `HeaderFooterCollection` και εφαρμογή της μεθόδου `replace` με τις κατάλληλες επιλογές.

**Ε: Τι κάνει η επιλογή `UseLegacyOrder`;**  
Α: `UseLegacyOrder` αναγκάζει τη μηχανή find/replace να διασχίζει τους κόμβους με την αρχική σειρά που χρησιμοποιούσαν οι παλαιότερες εκδόσεις του Aspose.Words, κάτι που μπορεί να είναι χρήσιμο για συμβατότητα με legacy έγγραφα.

**Τελευταία ενημέρωση:** 2026-01-03  
**Δοκιμάστηκε με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}