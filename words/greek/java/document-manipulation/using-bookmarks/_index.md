---
date: 2026-01-11
description: Μάθετε πώς να εμφανίζετε και να κρύβετε σελιδοδείκτες και να δημιουργείτε
  σελιδοδείκτες Java χρησιμοποιώντας το Aspose.Words for Java για αποτελεσματική πλοήγηση
  και διαχείριση εγγράφων.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Εμφάνιση/Απόκρυψη Σελιδοδεικτών με το Aspose.Words για Java
url: /el/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εμφάνιση/Απόκρυψη Σελιδοδεικτών με Aspose.Words for Java

## Εισαγωγή στη Χρήση Σελιδοδεικτών στο Aspose.Words for Java

Οι σελιδοδείκτες είναι μια ισχυρή δυνατότητα στο Aspose.Words for Java που σας επιτρέπει να **create bookmark java**, να μεταβείτε σε συγκεκριμένο περιεχόμενο και ακόμη να **show hide bookmarks** όταν χρειάζεται να δημιουργήσετε διαφορετικές εκδόσεις εγγράφου. Σε αυτόν τον οδηγό βήμα‑βήμα θα περάσουμε από τη δημιουργία, την πρόσβαση, την ενημέρωση, την αντιγραφή και την εναλλαγή της ορατότητας των σελιδοδεικτών, παρέχοντάς σας πλήρη έλεγχο πάνω στην επεξεργασία εγγράφων.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο κύριος σκοπός των σελιδοδεικτών;** Σημειώνουν και επιτρέπουν την ανάκτηση συγκεκριμένων τμημάτων ενός εγγράφου.  
- **Μπορώ να κρύψω τα σύμβολα των σελιδοδεικτών στην τελική έξοδο;** Ναι—χρησιμοποιήστε το show/hide API για να εναλλάξετε την ορατότητά τους.  
- **Πώς δημιουργώ έναν σελιδοδείκτη μέσα σε κελί πίνακα;** Ξεκινήστε και τερματίστε τον σελιδοδείκτη με `DocumentBuilder` ενώ ο κέρσορας βρίσκεται μέσα στο κελί.  
- **Μπορεί να αντιγραφεί το κείμενο με σελιδοδείκτη σε άλλο έγγραφο;** Απόλυτα—χρησιμοποιήστε το `NodeImporter` για να διατηρήσετε τη μορφοποίηση.  
- **Ποια έκδοση του Aspose.Words απαιτείται;** Οποιαδήποτε πρόσφατη έκδοση· ο κώδικας λειτουργεί με την τελευταία έκδοση 2026.

## Τι είναι η «εμφάνιση/απόκρυψη σελιδοδεικτών»;

Η δυνατότητα **show hide bookmarks** σας επιτρέπει προγραμματιστικά να εμφανίζετε ή να κρύβετε τα σύμβολα των σελιδοδεικτών στο αποθηκευμένο έγγραφο. Αυτό είναι χρήσιμο όταν θέλετε να δημιουργήσετε καθαρή έξοδο για τους τελικούς χρήστες, ενώ διατηρείτε τα δεδομένα των σελιδοδεικτών για εσωτερική επεξεργασία.

## Γιατί να χρησιμοποιήσετε σελιδοδείκτες στην αυτοματοποίηση εγγράφων Java;

- **Αποτελεσματική πλοήγηση** – Μεταβείτε άμεσα σε ενότητες χωρίς να σαρώσετε ολόκληρο το αρχείο.  
- **Δυναμική δημιουργία περιεχομένου** – Εισάγετε, αντικαταστήστε ή αφαιρέστε κείμενο συνδεδεμένο με έναν σελιδοδείκτη.  
- **Υπό όρους ορατότητα** – Εμφανίστε ή κρύψτε τα σύμβολα των σελιδοδεικτών ανάλογα με τις προτιμήσεις του χρήστη ή τη μορφή εξόδου.  
- **Επαναχρησιμοποίηση** – Αντιγράψτε τμήματα με σελιδοδείκτη μεταξύ εγγράφων διατηρώντας τα στυλ.

## Προαπαιτούμενα
- Java Development Kit (JDK) 8 ή νεότερο.  
- Βιβλιοθήκη Aspose.Words for Java προστεθειμένη στο έργο σας (Maven/Gradle ή JAR).  
- Βασική εξοικείωση με τις κλάσεις `Document` και `DocumentBuilder`.

## Οδηγός Βήμα‑βήμα

### Βήμα 1: Δημιουργία Σελιδοδείκτη (create bookmark java)

Για να προσθέσετε έναν σελιδοδείκτη, ξεκινάτε, γράφετε το περιεχόμενο και στη συνέχεια τερματίζετε. Αυτό το παράδειγμα δημιουργεί έναν απλό σελιδοδείκτη με όνομα **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Βήμα 2: Πρόσβαση σε Σελιδοδείκτες (access bookmarks java)

Οι σελιδοδείκτες μπορούν να ανακτηθούν είτε με το μηδενικό‑βασισμένο δείκτη τους είτε με το όνομα. Ο κώδικας παρακάτω δείχνει και τις δύο προσεγγίσεις.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Βήμα 3: Ενημέρωση Δεδομένων Σελιδοδείκτη (update bookmark text)

Μπορείτε να μετονομάσετε έναν σελιδοδείκτη ή να αντικαταστήσετε το κείμενο του. Αυτό είναι χρήσιμο όταν το υποκείμενο έγγραφο αλλάζει.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Βήμα 4: Εργασία με Κείμενο με Σελιδοδείκτη (copy bookmarked text)

Η αντιγραφή ενός τμήματος με σελιδοδείκτη σε άλλο έγγραφο διατηρώντας τη μορφοποίηση είναι απλή με το `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Βήμα 5: Εμφάνιση και Απόκρυψη Σελιδοδεικτών (show hide bookmarks)

Το παρακάτω απόσπασμα δείχνει πώς να κρύψετε τα σύμβολα ενός σελιδοδείκτη στο αποθηκευμένο αρχείο. Περάστε `false` για απόκρυψη, `true` για εμφάνιση.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Βήμα 6: Αποπλοκή Σελιδοδεικτών Σειράς (bookmark table cell)

Όταν οι σελιδοδείκτες καλύπτουν σειρές πίνακα, μπορεί να μπλέξουν. Οι βοηθητικές μεθόδους παρακάτω τα αποπλέκουν και σας επιτρέπουν να διαγράψετε μια συγκεκριμένη σειρά με βάση τον σελιδοδείκτη της.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Κοινά Προβλήματα και Λύσεις

| Πρόβλημα | Λύση |
|----------|------|
| **Ο σελιδοδείκτης δεν βρέθηκε** | Επαληθεύστε ότι το όνομα του σελιδοδείκτη ταιριάζει ακριβώς (διάκριση πεζών/κεφαλαίων) και ότι το έγγραφο αποθηκεύτηκε μετά τη δημιουργία. |
| **Το αντιγραμμένο κείμενο χάνει τη μορφοποίηση** | Χρησιμοποιήστε `ImportFormatMode.KEEP_SOURCE_FORMATTING` με το `NodeImporter` όπως φαίνεται στο Βήμα 4. |
| **Η εμφάνιση/απόκρυψη δεν επηρεάζει την έξοδο** | Βεβαιωθείτε ότι καλείτε το `showHideBookmarkedContent` **πριν** αποθηκεύσετε το έγγραφο. |
| **Ο σελιδοδείκτης μέσα σε κελί πίνακα αγνοείται** | Τοποθετήστε τις κλήσεις start/end ενώ ο κέρσορας του builder βρίσκεται μέσα στο επιθυμητό κελί. |

## Συχνές Ερωτήσεις

**Ε: Πώς δημιουργώ έναν σελιδοδείκτη σε κελί πίνακα;**  
Α: Χρησιμοποιήστε το `DocumentBuilder` για να μετακινήσετε τον κέρσορα στο επιθυμητό κελί, στη συνέχεια καλέστε `startBookmark` και `endBookmark` γύρω από το περιεχόμενο του κελιού.

**Ε: Μπορώ να αντιγράψω έναν σελιδοδείκτη σε άλλο έγγραφο;**  
Α: Ναι—χρησιμοποιήστε την κλάση `NodeImporter` (δείτε το Βήμα 4) για να εισάγετε τον κόμβο με σελιδοδείκτη διατηρώντας την αρχική μορφοποίηση.

**Ε: Πώς μπορώ να διαγράψω μια γραμμή με βάση τον σελιδοδείκτη της;**  
Α: Πρώτα εντοπίστε τη γραμμή που περιέχει τον σελιδοδείκτη, στη συνέχεια καλέστε `remove` στον κόμβο της γραμμής (όπως επιδεικνύεται στο Βήμα 6).

**Ε: Ποιες είναι μερικές κοινές περιπτώσεις χρήσης των σελιδοδεικτών;**  
Α: Δημιουργία πίνακα περιεχομένων, εξαγωγή συγκεκριμένων ενοτήτων για αναφορές και αυτοματοποίηση συναρμολόγησης εγγράφων βάσει επιλογών χρήστη.

**Ε: Πού μπορώ να βρω περισσότερες πληροφορίες για το Aspose.Words for Java;**  
Α: Για λεπτομερή τεκμηρίωση και λήψεις, επισκεφθείτε [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Τελευταία ενημέρωση:** 2026-01-11  
**Δοκιμή με:** Aspose.Words for Java 24.11 (2026)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}