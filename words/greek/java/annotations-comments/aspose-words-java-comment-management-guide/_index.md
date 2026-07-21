---
date: '2026-07-21'
description: Μάθετε πώς να χρησιμοποιήσετε το Aspose.Words για Java για να προσθέτετε,
  εκτυπώνετε, αφαιρείτε και να σημειώνετε τα σχόλια ως ολοκληρωμένα, καθώς και να
  ανακτάτε χρονικές σφραγίδες UTC σε έγγραφα Word.
keywords:
- how to use aspose
- add comment java
- print word comments
- Aspose.Words Java
- comment management
lastmod: '2026-07-21'
og_description: Ανακαλύψτε πώς να χρησιμοποιήσετε το Aspose.Words Java για να προσθέτετε,
  εκτυπώνετε, αφαιρείτε και να σημειώνετε τα σχόλια ως ολοκληρωμένα, και να ανακτάτε
  χρονικές σφραγίδες UTC σε έγγραφα Word.
og_image_alt: 'Developer guide: Manage Word comments with Aspose.Words Java'
og_title: Πώς να χρησιμοποιήσετε το Aspose.Words Java για διαχείριση σχολίων
schemas:
- author: Aspose
  dateModified: '2026-07-21'
  description: Learn how to use Aspose.Words for Java to add, print, remove, and mark
    comments as done, plus retrieve UTC timestamps in Word documents.
  headline: How to Use Aspose.Words Java for Comment Management
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a library that enables developers to create,
      edit, convert, and render Word documents programmatically without requiring
      Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: A temporary license or free trial works for development and testing; a
      full license is required for production deployments.
    question: Do I need a license to run the examples?
  - answer: Yes—load the document with the appropriate password, then use the same
      comment APIs once the file is opened.
    question: Can I add comments to password‑protected documents?
  - answer: The library handles comments in all Word formats (DOC, DOCX, DOCM, DOT,
      DOTX, DOTM) and preserves them when converting to PDF, HTML, or images.
    question: How many comment formats does Aspose.Words support?
  - answer: Practically, you can manage thousands of comments; performance depends
      on document size and available memory.
    question: Is there a limit to the number of comments I can process?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
- add comment java
- print word comments
title: Πώς να χρησιμοποιήσετε το Aspose.Words Java για διαχείριση σχολίων
url: /el/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να χρησιμοποιήσετε το Aspose.Words Java για Διαχείριση Σχολίων

Η διαχείριση σχολίων σε ένα έγγραφο Word προγραμματιστικά μπορεί να μοιάζει με πλοήγηση σε λαβύρινθο, ειδικά όταν πρέπει να προσθέσετε απαντήσεις, να επιλύσετε ζητήματα ή να παρακολουθήσετε πότε δόθηκε η ανατροφοδότηση. **Πώς να χρησιμοποιήσετε το Aspose** κάνει αυτό απλό: η βιβλιοθήκη Aspose.Words for Java παρέχει ένα καθαρό API που σας επιτρέπει να προσθέτετε, εκτυπώνετε, αφαιρείτε και να σημειώνετε σχόλια ως ολοκληρωμένα, καθώς και να λαμβάνετε ακριβείς χρονικές σημάνσεις UTC. Σε αυτόν τον οδηγό θα περάσουμε από κάθε δυνατότητα βήμα‑βήμα, ώστε να ενσωματώσετε ισχυρή διαχείριση σχολίων στις εφαρμογές Java σας.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τα σχόλια Word σε Java;** Aspose.Words for Java.
- **Μπορώ να προσθέσω μια απάντηση σε ένα σχόλιο;** Ναι – use `Comment.getReplies().add(...)`.
- **Πώς εκτυπώνω όλα τα σχόλια;** Iterate `doc.getComments()` and output each comment’s text.
- **Είναι δυνατόν να σημειώσετε ένα σχόλιο ως ολοκληρωμένο;** Set `Comment.setDone(true)`.
- **Πώς μπορώ να λάβω το χρονικό σήμα UTC ενός σχολίου;** Call `Comment.getDateTime().toInstant()`.

## Τι είναι το “how to use aspose”;
**“how to use aspose”** αναφέρεται στα πρακτικά βήματα που ακολουθούν οι προγραμματιστές για την ενσωμάτωση των βιβλιοθηκών Aspose—όπως το Aspose.Words for Java—στον κώδικά τους για εργασίες διαχείρισης εγγράφων. Ακολουθώντας τα παρακάτω παραδείγματα, θα δείτε ακριβώς πώς να αξιοποιήσετε το API για τη διαχείριση σχολίων.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για διαχείριση σχολίων;
Το Aspose.Words υποστηρίζει **35+** μορφές εισόδου και εξόδου—συμπεριλαμβανομένων των DOCX, PDF, HTML και ODT—και μπορεί να επεξεργαστεί έγγραφα **500‑σελίδων** σε λιγότερο από **3 δευτερόλεπτα** σε τυπικό εξοπλισμό διακομιστή, όλα χωρίς την ανάγκη του Microsoft Word. Αυτή η απόδοση, σε συνδυασμό με ένα πλούσιο API σχολίων, εξαλείφει την ανάγκη για χειροκίνητη ανάλυση XML ή εξωτερικά εργαλεία.

## Προαπαιτούμενα
- Java Development Kit (JDK 8 ή νεότερο) εγκατεστημένο.
- Ένα IDE όπως IntelliJ IDEA ή Eclipse.
- Maven ή Gradle για διαχείριση εξαρτήσεων.
- Ένα έγκυρο άδεια Aspose.Words (διατίθεται δωρεάν δοκιμή).

### Ρύθμιση του Aspose.Words για Java
Συμπεριλάβετε τη βιβλιοθήκη στο έργο σας:

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### Απόκτηση Άδειας
Το Aspose.Words είναι εμπορικό προϊόν, αλλά μπορείτε να ξεκινήσετε με δωρεάν δοκιμή ή να ζητήσετε προσωρινή άδεια για πλήρη πρόσβαση στις δυνατότητες. Επισκεφθείτε τη [σελίδα αγοράς](https://purchase.aspose.com/buy) για να εξερευνήσετε τις επιλογές αδειοδότησης.

## Πώς να προσθέσετε ένα σχόλιο με απάντηση χρησιμοποιώντας το Aspose.Words για Java;
Για να εισάγετε ένα σχόλιο και μια επακόλουθη απάντηση, πρώτα φορτώστε ή δημιουργήστε ένα `Document`, στη συνέχεια χρησιμοποιήστε ένα `DocumentBuilder` για να τοποθετήσετε τον κέρσορα στο σημείο όπου πρέπει να εμφανιστεί το σχόλιο. Δημιουργήστε ένα αντικείμενο `Comment` με πληροφορίες συγγραφέα και κείμενο, προσθέστε το στο έγγραφο και, τέλος, συνδέστε μια απάντηση `Comment` στο αρχικό σχόλιο. Αυτή η ακολουθία εξασφαλίζει ότι η ανατροφοδότηση αποθηκεύεται ιεραρχικά μέσα στο αρχείο.

Η κλάση `Document` αντιπροσωπεύει ένα έγγραφο Word που έχει φορτωθεί στη μνήμη.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

## Πώς να εκτυπώσετε όλα τα σχόλια και τις απαντήσεις τους σε ένα έγγραφο Word;
Για να εμφανίσετε κάθε σχόλιο μαζί με τις ένθετες απαντήσεις του, φορτώστε το στοχευόμενο έγγραφο και επαναλάβετε τη `CommentCollection`. Για κάθε σχόλιο πρώτου επιπέδου, εμφανίστε τον συγγραφέα, το κείμενο και την ημερομηνία δημιουργίας, στη συνέχεια επαναλάβετε τη συλλογή `Replies` για να εκτυπώσετε τις λεπτομέρειες κάθε απάντησης. Αυτή η προσέγγιση παρέχει μια πλήρη, αναγνώσιμη προβολή όλων των σχολίων που υπάρχουν στο αρχείο.

Η κλάση `Document` αντιπροσωπεύει ένα έγγραφο Word που έχει φορτωθεί στη μνήμη.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

## Πώς να αφαιρέσετε απαντήσεις σχολίων στο Aspose.Words για Java;
Για να διαγράψετε απαντήσεις σχολίων, πρώτα αποκτήστε το γονικό αντικείμενο `Comment` από τη συλλογή σχολίων του εγγράφου. Μπορείτε είτε να εκκαθαρίσετε ολόκληρη τη λίστα `Replies` για να αφαιρέσετε όλη την ένθετη ανατροφοδότηση, είτε να στοχεύσετε μια συγκεκριμένη απάντηση με βάση το δείκτη της και να καλέσετε τη μέθοδο `remove`. Αυτός ο καθαρισμός βοηθά το έγγραφο να παραμείνει συνοπτικό μετά την ανασκόπηση.

Η κλάση `Document` αντιπροσωπεύει ένα έγγραφο Word που έχει φορτωθεί στη μνήμη.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

## Πώς να σημειώσετε ένα σχόλιο ως ολοκληρωμένο σε ένα έγγραφο Word;
Το να σημειώσετε ένα σχόλιο ως ολοκληρωμένο υποδηλώνει ότι το ζήτημα έχει αντιμετωπιστεί. Ανακτήστε το επιθυμητό `Comment` από το έγγραφο, στη συνέχεια καλέστε τη μέθοδο `setDone(true)`. Μόλις επισημανθεί, το σχόλιο θα εμφανίζεται με οπτικό δείκτη σε υποστηριζόμενους προβολείς, επιτρέποντας στους αξιολογητές να εντοπίζουν γρήγορα τα επιλυμένα στοιχεία.

Η κλάση `Document` αντιπροσωπεύει ένα έγγραφο Word που έχει φορτωθεί στη μνήμη.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

## Πώς να λάβετε την ημερομηνία και ώρα UTC από ένα σχόλιο;
Κάθε σχόλιο αποθηκεύει την ακριβή στιγμή δημιουργίας του. Μετά τη φόρτωση του εγγράφου, αποκτήστε το αντικείμενο `Comment` και καλέστε τη μέθοδο `getDateTime()`, η οποία επιστρέφει μια τιμή `DateTime`. Μετατρέψτε αυτή την τιμή σε UTC χρησιμοποιώντας `toInstant()` για να λάβετε ένα χρονικό σήμα ανεξάρτητο από τη ζώνη ώρας, κατάλληλο για καταγραφή ή σκοπούς ελέγχου.

Η κλάση `Document` αντιπροσωπεύει ένα έγγραφο Word που έχει φορτωθεί στη μνήμη.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

## Πρακτικές Εφαρμογές
Η κατανόηση και η αξιοποίηση αυτών των λειτουργιών διαχείρισης σχολίων μπορεί να βελτιώσει δραστικά τις ροές εργασίας εγγράφων:

- **Συνεργατική Επεξεργασία:** Οι ομάδες μπορούν να αφήνουν σχόλια σε νήμα χωρίς να βγουν από το αρχείο Word.
- **Αυτοματοποίηση Ανασκόπησης Εγγράφων:** Εξαγωγή σχολίων σε CSV ή ενσωμάτωση με συστήματα παρακολούθησης ζητημάτων.
- **Έλεγχος & Συμμόρφωση:** Τα χρονικά σήματα UTC παρέχουν αμετάβλητο αρχείο της στιγμής που δόθηκαν τα σχόλια.

Αυτές οι δυνατότητες ενσωματώνονται ομαλά με πλατφόρμες διαχείρισης περιεχομένου, αυτοματοποιημένες γραμμές αναφοράς ή προσαρμοσμένα εργαλεία ανασκόπησης.

## Σκέψεις για την Απόδοση
Όταν διαχειρίζεστε μεγάλα αρχεία Word (εκατοντάδες σελίδες) κρατήστε αυτές τις συμβουλές στο μυαλό:

- Επεξεργαστείτε τα σχόλια σε παρτίδες αντί να φορτώνετε ολόκληρο το δέντρο σχολίων ταυτόχρονα.
- Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` για πολλαπλές λειτουργίες ώστε να μειώσετε την κατανάλωση μνήμης.
- Αναβαθμίστε στην πιο πρόσφατη έκδοση του Aspose.Words για να επωφεληθείτε από βελτιώσεις απόδοσης και διορθώσεις σφαλμάτων.

## Συμπέρασμα
Τώρα γνωρίζετε **πώς να χρησιμοποιήσετε το Aspose.Words Java** για να προσθέτετε, εκτυπώνετε, αφαιρείτε, επιλύετε και να προσθέτετε χρονικά σήματα σε σχόλια σε έγγραφα Word. Ενσωματώστε αυτά τα πρότυπα στις εφαρμογές σας για να βελτιώσετε τη συνεργασία και να διατηρήσετε ένα σαφές αρχείο ελέγχου.

**Επόμενα βήματα:**  
- Δοκιμάστε το φιλτράρισμα σχολίων ανά συγγραφέα ή ημερομηνία.  
- Συνδυάστε τη διαχείριση σχολίων με χαρακτηριστικά προστασίας εγγράφων για ασφαλείς κύκλους ανασκόπησης.  

Έτοιμοι να εφαρμόσετε αυτές τις τεχνικές στην παραγωγή; Ξεκινήστε τον κώδικα σήμερα και δείτε τη διαδικασία ανασκόπησης εγγράφων σας να γίνει πολύ πιο αποδοτική.

## Συχνές Ερωτήσεις

**Q: Τι είναι το Aspose.Words for Java;**  
A: Το Aspose.Words for Java είναι μια βιβλιοθήκη που επιτρέπει στους προγραμματιστές να δημιουργούν, επεξεργάζονται, μετατρέπουν και αποδίδουν έγγραφα Word προγραμματιστικά χωρίς την ανάγκη του Microsoft Word.

**Q: Χρειάζομαι άδεια για να εκτελέσω τα παραδείγματα;**  
A: Μια προσωρινή άδεια ή δωρεάν δοκιμή λειτουργεί για ανάπτυξη και δοκιμές· απαιτείται πλήρης άδεια για παραγωγικές εγκαταστάσεις.

**Q: Μπορώ να προσθέσω σχόλια σε έγγραφα προστατευμένα με κωδικό;**  
A: Ναι—φορτώστε το έγγραφο με τον κατάλληλο κωδικό, στη συνέχεια χρησιμοποιήστε τα ίδια API σχολίων αφού το αρχείο ανοίξει.

**Q: Πόσες μορφές σχολίων υποστηρίζει το Aspose.Words;**  
A: Η βιβλιοθήκη διαχειρίζεται σχόλια σε όλες τις μορφές Word (DOC, DOCX, DOCM, DOT, DOTX, DOTM) και τα διατηρεί κατά τη μετατροπή σε PDF, HTML ή εικόνες.

**Q: Υπάρχει όριο στον αριθμό των σχολίων που μπορώ να επεξεργαστώ;**  
A: Πρακτικά, μπορείτε να διαχειριστείτε χιλιάδες σχόλια· η απόδοση εξαρτάται από το μέγεθος του εγγράφου και τη διαθέσιμη μνήμη.

**Τελευταία Ενημέρωση:** 2026-07-21  
**Δοκιμή Με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose

```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```

```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## Σχετικά Μαθήματα

- [Κατακτήστε το Aspose.Words για Java: Πώς να Εισάγετε και να Διαχειριστείτε Σελιδοδείκτες σε Έγγραφα Word](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [Παρακολούθηση Αλλαγών σε Έγγραφα Word με Aspose.Words Java: Πλήρης Οδηγός για Αναθεωρήσεις Εγγράφων](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Πλήρης Οδηγός για Επεξεργασία Εγγράφων Word](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}