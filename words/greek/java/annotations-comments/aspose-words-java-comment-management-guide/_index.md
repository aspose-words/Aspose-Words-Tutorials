---
date: '2026-08-10'
description: Μάθετε πώς να προσθέσετε comment java με το Aspose.Words για Java. Οδηγός
  βήμα‑βήμα για τη δημιουργία, απάντηση, εκτύπωση, αφαίρεση και σήμανση των comments
  ως ολοκληρωμένα, καθώς και την ανάκτηση των UTC timestamps.
keywords:
- how to add comment java
- comment management Java
- Aspose.Words comments
lastmod: '2026-08-10'
og_description: Μάθετε πώς να προσθέσετε comment java με το Aspose.Words για Java.
  Οδηγός βήμα‑βήμα για τη δημιουργία, απάντηση, εκτύπωση, αφαίρεση και σήμανση των
  comments ως ολοκληρωμένα, καθώς και την ανάκτηση των UTC timestamps.
og_image_alt: Guide showing how to add comment java with Aspose.Words in Word documents
og_title: Πώς να προσθέσετε comment java χρησιμοποιώντας το Aspose.Words για έγγραφα
  Word
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add comment java with Aspose.Words for Java. Step‑by‑step
    guide to create, reply to, print, remove, and mark comments as done, plus retrieve
    UTC timestamps.
  headline: How to add comment java using Aspose.Words for Word docs
  type: TechArticle
- questions:
  - answer: No. The trial works for development only; a full license is required for
      production deployments.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes. Load a protected file by passing the password to the `Document` constructor.
    question: Does the library support password‑protected documents?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, with full feature
      parity across versions.
    question: Which Java versions are compatible?
  - answer: Comment enumeration runs in linear time; a 1,000‑page document processes
      in under 2 seconds on a typical 4‑core server.
    question: How does comment performance scale with document size?
  - answer: Absolutely. Iterate the `CommentCollection` and write each comment’s properties
      to CSV, JSON, or XML as needed.
    question: Can I export comments to a separate file?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java document processing
title: Πώς να προσθέσετε comment java χρησιμοποιώντας το Aspose.Words για έγγραφα
  Word
url: /el/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε σχόλιο java χρησιμοποιώντας το Aspose.Words για έγγραφα Word

## Εισαγωγή
Η προσθήκη σχολίων προγραμματιστικά σε ένα έγγραφο Word μπορεί να βελτιώσει τη συνεργασία, την ανασκόπηση κώδικα ή τη δημιουργία αυτόματων αναφορών. Σε αυτό το tutorial θα μάθετε **πώς να προσθέσετε σχόλιο java** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words, καλύπτοντας τη δημιουργία, τις απαντήσεις, την εκτύπωση, την αφαίρεση, την επισήμανση ως ολοκληρωμένο και την εξαγωγή χρονικών σημάνσεων UTC. Στο τέλος θα μπορείτε να ενσωματώσετε πλούσια ανατροφοδότηση απευθείας στα έγγραφά σας χωρίς χειροκίνητη παρέμβαση.

## Γρήγορες απαντήσεις
- **Ποιο είναι το πρώτο βήμα;** Φορτώστε το αρχείο Word με `new Document("input.docx")`.  
- **Μπορώ να απαντήσω σε ένα σχόλιο;** Ναι—δημιουργήστε ένα αντικείμενο `Comment` και καλέστε `comment.getReplies().add(reply)`.  
- **Πώς σημαδεύω ένα σχόλιο ως ολοκληρωμένο;** Ορίστε `comment.setDone(true)` για να το επισημάνετε ως επιλυμένο.  
- **Είναι διαθέσιμος ο χρόνος UTC;** Κάθε σχόλιο αποθηκεύει `getDateTime()` σε UTC, το οποίο μπορείτε να διαβάσετε απευθείας.  
- **Χρειάζομαι άδεια;** Η δοκιμαστική έκδοση λειτουργεί για ανάπτυξη· μια πλήρης άδεια αφαιρεί τους περιορισμούς αξιολόγησης.

## Τι είναι η προσθήκη σχολίου Java;
`how to add comment java` αναφέρεται στη διαδικασία προγραμματιστικής εισαγωγής ενός σχολίου σε ένα έγγραφο Microsoft Word χρησιμοποιώντας κώδικα Java και το API Aspose.Words. Αυτή η λειτουργία επιτρέπει αυτοματοποιημένους βρόχους ανατροφοδότησης σε ροές εργασίας που βασίζονται σε έγγραφα.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για διαχείριση σχολίων;
Το Aspose.Words υποστηρίζει **35+ μορφές εισόδου και εξόδου** και μπορεί να διαχειριστεί έγγραφα που υπερβαίνουν τις **500 σελίδες** διατηρώντας τη χρήση μνήμης κάτω από **100 MB** σε έναν τυπικό διακομιστή. Το API σχολίων λειτουργεί χωρίς εγκατεστημένο το Microsoft Word, παρέχοντάς σας πλήρη έλεγχο σε περιβάλλοντα χωρίς γραφικό περιβάλλον και μειώνοντας το κόστος αδειοδότησης έως και **70 %** σε σύγκριση με την αυτοματοποίηση του Office.

## Προαπαιτούμενα
- Java Development Kit (JDK) 17 ή νεότερο εγκατεστημένο.  
- Ένα IDE όπως το IntelliJ IDEA ή το Eclipse.  
- Maven ή Gradle για διαχείριση εξαρτήσεων.  
- Ένα έγκυρο άδεια Aspose.Words for Java (δοκιμαστική ή πλήρης).

### Ρύθμιση του Aspose.Words για Java
Το Aspose.Words παρέχεται ως ένα ενιαίο JAR. Προσθέστε την εξάρτηση που ταιριάζει με το εργαλείο κατασκευής σας.

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

#### Απόκτηση άδειας
Το Aspose.Words είναι εμπορικό προϊόν· μπορείτε να ξεκινήσετε με μια δωρεάν δοκιμή ή να ζητήσετε προσωρινή άδεια για πλήρη πρόσβαση σε λειτουργίες. Επισκεφθείτε τη [σελίδα αγοράς](https://purchase.aspose.com/buy) για να εξερευνήσετε τις επιλογές αδειοδότησης.

## Πώς να προσθέσετε ένα σχόλιο σε Java χρησιμοποιώντας το Aspose.Words;
Φορτώστε το έγγραφό σας, δημιουργήστε ένα αντικείμενο `Comment` και συνδέστε το με ένα `Paragraph`. Αυτό το μοτίβο δύο βημάτων εισάγει ένα σχόλιο στην επιθυμητή θέση και αποτελεί τη βάση για όλες τις επόμενες λειτουργίες. Καθορίζοντας τον συγγραφέα, το κείμενο και τη χρονική σήμανση, μπορείτε άμεσα να παρέχετε συμφραζόμενα στους αξιολογητές, και το σχόλιο γίνεται μέρος της δομής του εγγράφου.

Η κλάση `Document` είναι το κορυφαίο αντικείμενο του Aspose.Words που αντιπροσωπεύει ένα μοναδικό αρχείο Word στη μνήμη. Μετά τη δημιουργία, όλες οι λειτουργίες ανάγνωσης και εγγραφής περνούν μέσω αυτού του αντικειμένου.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

Στη συνέχεια, δημιουργείτε το ίδιο το σχόλιο. Η κλάση `Comment` αποθηκεύει πληροφορίες συγγραφέα, κειμένου και χρονικής σήμανσης.  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Τέλος, προσθέστε μια απάντηση χρησιμοποιώντας τη συλλογή `Replies` του σχολίου. Το αντικείμενο `Comment` παρακολουθεί αυτόματα την ιεραρχία των απαντήσεων.  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## Πώς να εκτυπώσετε όλα τα σχόλια και τις απαντήσεις τους;
Επανάληψη στη `CommentCollection` του εγγράφου και έξοδο του κειμένου, του συγγραφέα και της χρονικής σήμανσης UTC κάθε σχολίου. Οι απαντήσεις είναι ενσωματωμένες μέσα σε κάθε σχόλιο, επιτρέποντάς σας να εμφανίσετε ολόκληρο το νήμα συζήτησης. Με την επαναληπτική διαπέραση της συλλογής μπορείτε να διατηρήσετε την ιεραρχία, να μορφοποιήσετε την έξοδο για αρχεία καταγραφής ή UI, και προαιρετικά να φιλτράρετε ανά συγγραφέα ή ημερομηνία.  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

Χρησιμοποιήστε έναν απλό βρόχο για να διασχίσετε τη συλλογή και να εκτυπώσετε τις λεπτομέρειες.  
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

## Πώς να αφαιρέσετε τις απαντήσεις σχολίων;
Μπορείτε να διαγράψετε μια συγκεκριμένη απάντηση ή να καθαρίσετε όλες τις απαντήσεις από ένα σχόλιο. Η αφαίρεση των απαντήσεων βοηθά το έγγραφο να παραμείνει καθαρό μετά την ενσωμάτωση της ανατροφοδότησης. Χρησιμοποιήστε τη μέθοδο `getReplies().remove(index)` για στοχευμένη αφαίρεση ή καλέστε `clear()` για να εκκαθαρίσετε ολόκληρη τη λίστα απαντήσεων, εξασφαλίζοντας ότι δεν παραμένει ορφανή συζήτηση.  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

Καλέστε `comment.getReplies().clear()` ή αφαιρέστε μεμονωμένες απαντήσεις με δείκτη.  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## Πώς να σημαδέψετε ένα σχόλιο ως ολοκληρωμένο;
Ορισμός της σημαίας `Done` ενός σχολίου υποδηλώνει ότι το ζήτημα έχει επιλυθεί. Αυτό το οπτικό σήμα είναι χρήσιμο για τους αξιολογητές και τα εργαλεία επεξεργασίας. Όταν κληθεί `setDone(true)`, το Word εμφανίζει ένα σημάδι ελέγχου δίπλα στο σχόλιο, και μπορείτε αργότερα να ελέγξετε τη σημαία για να δημιουργήσετε αναφορές των εκκρεμών στοιχείων.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

Εφαρμόστε τη σημαία αφού έχετε αντιμετωπίσει το περιεχόμενο του σχολίου.  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## Πώς να λάβετε την ημερομηνία και ώρα UTC από ένα σχόλιο;
Κάθε σχόλιο αποθηκεύει την ώρα δημιουργίας του σε UTC, προσβάσιμη μέσω `getDateTime()`. Αυτή η χρονική σήμανση είναι απαραίτητη για τα αρχεία ελέγχου και τον έλεγχο εκδόσεων. Το επιστρεφόμενο αντικείμενο `DateTime` μπορεί να μορφοποιηθεί χρησιμοποιώντας πρότυπα ISO‑8601, επιτρέποντάς σας να καταγράψετε ακριβείς στιγμές ανατροφοδότησης και να συγχρονίσετε τα δεδομένα σχολίων σε κατανεμημένα συστήματα.  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

Μπορείτε να μορφοποιήσετε τη χρονική σήμανση ως ISO‑8601 για εύκολη καταγραφή.  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## Πρακτικές εφαρμογές
Η κατανόηση αυτών των API σας επιτρέπει να δημιουργήσετε ισχυρές λύσεις για:
- **Πλατφόρμες συνεργατικής επεξεργασίας** – ενσωματώστε βρόχους ανατροφοδότησης απευθείας σε παραγόμενες αναφορές.  
- **Αυτοματοποιημένες γραμμές ελέγχου** – σημαδέψτε, επιλύστε και ελέγξτε σχόλια χωρίς ανθρώπινη παρέμβαση.  
- **Τεκμηρίωση συμμόρφωσης** – καταγράψτε τις χρονικές σήμανσεις των αξιολογητών για ρυθμιστικούς ελέγχους.

## Παρατηρήσεις απόδοσης
Κατά την επεξεργασία μεγάλων αρχείων (500 + σελίδες), ακολουθήστε τις καλύτερες πρακτικές:
- Επεξεργαστείτε τα σχόλια σε παρτίδες για να αποφύγετε τη φόρτωση ολόκληρης της συλλογής στη μνήμη.  
- Χρησιμοποιήστε `Document.optimizeResources()` για να μειώσετε το μέγεθος του εγγράφου πριν την αποθήκευση.  
- Διατηρήστε το Aspose.Words ενημερωμένο· η έκδοση 24.12 εισήγαγε βελτίωση ταχύτητας κατά 30 % για την απαρίθμηση σχολίων.

## Συμπέρασμα
Τώρα διαθέτετε ένα πλήρες σύνολο εργαλείων για **πώς να προσθέσετε σχόλιο java** με το Aspose.Words: δημιουργία σχολίων, απαντήσεις, εκτύπωση, αφαίρεση, επισήμανση ως ολοκληρωμένο και εξαγωγή χρονικών σημάνσεων UTC. Ενσωματώστε αυτά τα αποσπάσματα στις υπάρχουσες υπηρεσίες Java σας για να αυτοματοποιήσετε την ανατροφοδότηση, να επιβάλετε πολιτικές ελέγχου και να διατηρήσετε ένα καθαρό αρχείο ελέγχου.

**Επόμενα βήματα**
- Πειραματιστείτε με το φιλτράρισμα σχολίων ανά συγγραφέα ή ημερομηνία.  
- Συνδυάστε τη διαχείριση σχολίων με το API “track changes” του Aspose.Words για πλήρη έλεγχο αναθεώρησης.  
- Εξερευνήστε την εξαγωγή δεδομένων σχολίων σε JSON για αναλύσεις downstream.

## Συχνές ερωτήσεις

**Q: Μπορώ να χρησιμοποιήσω το Aspose.Words χωρίς άδεια σε παραγωγή;**  
A: Όχι. Η δοκιμαστική έκδοση λειτουργεί μόνο για ανάπτυξη· απαιτείται πλήρης άδεια για παραγωγικές εγκαταστάσεις.

**Q: Υποστηρίζει η βιβλιοθήκη έγγραφα με προστασία κωδικού;**  
A: Ναι. Φορτώστε ένα προστατευμένο αρχείο περνώντας τον κωδικό στο κατασκευαστή `Document`.

**Q: Ποιες εκδόσεις Java είναι συμβατές;**  
A: Το Aspose.Words for Java υποστηρίζει JDK 8 έως JDK 21, με πλήρη ισοδυναμία λειτουργιών σε όλες τις εκδόσεις.

**Q: Πώς κλιμακώνεται η απόδοση των σχολίων με το μέγεθος του εγγράφου;**  
A: Η απαρίθμηση σχολίων εκτελείται σε γραμμικό χρόνο· ένα έγγραφο 1.000 σελίδων επεξεργάζεται σε κάτω από 2 δευτερόλεπτα σε τυπικό διακομιστή 4 πυρήνων.

**Q: Μπορώ να εξάγω τα σχόλια σε ξεχωριστό αρχείο;**  
A: Απόλυτα. Επανάλαβε τη `CommentCollection` και γράψε τις ιδιότητες κάθε σχολίου σε CSV, JSON ή XML όπως απαιτείται.

---

**Τελευταία ενημέρωση:** 2026-08-10  
**Δοκιμή με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< blocks/products/products-backtop-button >}}

## Σχετικά μαθήματα

- [Κατακτήστε τις Σημειώσεις & Σχόλια με τα Μαθήματα Aspose.Words για Java](/words/java/annotations-comments/)
- [Παρακολούθηση Αλλαγών σε Έγγραφα Word χρησιμοποιώντας Aspose.Words Java: Ολοκληρωμένος Οδηγός για Αναθεωρήσεις Εγγράφων](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java: Πλήρης Οδηγός για Επεξεργασία Εγγράφων Word](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}