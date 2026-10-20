---
category: general
date: 2026-02-15
description: Εξαγωγή Word σε Markdown σε Java χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να μετατρέπετε DOCX σε Markdown και να αποθηκεύετε τις εικόνες σε ξεχωριστό
  φάκελο με προσαρμοσμένο callback.
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- store images in separate folder
- aspose words markdown
- java document conversion
language: el
og_description: Εξαγωγή Word σε Markdown με το Aspose.Words. Αυτός ο οδηγός δείχνει
  πώς να μετατρέψετε DOCX σε Markdown και να αποθηκεύσετε τις εικόνες σε ξεχωριστό
  φάκελο.
og_title: Εξαγωγή Word σε Markdown – Πλήρης οδηγός Java
tags:
- Java
- Aspose.Words
- Markdown
- Image handling
title: Εξαγωγή Word σε Markdown – Πλήρης Οδηγός Java
url: /el/java/document-conversion-and-export/export-word-to-markdown-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εξαγωγή Word σε Markdown – Πλήρες Java Tutorial

Έχετε αναρωτηθεί ποτέ πώς να **εξάγετε Word σε Markdown** χωρίς να χάσετε τις ενσωματωμένες εικόνες; Δεν είστε οι μόνοι—οι προγραμματιστές ρωτούν συνεχώς, «Πώς να μετατρέψω DOCX σε Markdown διατηρώντας τις εικόνες οργανωμένες;» Τα καλά νέα είναι ότι το Aspose.Words for Java το κάνει παιχνιδάκι. Σε αυτό το tutorial θα περάσουμε από ένα έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο μετατρέπει ένα αρχείο `.docx` σε Markdown αλλά επίσης **αποθηκεύει τις εικόνες σε ξεχωριστό φάκελο** χρησιμοποιώντας μια προσαρμοσμένη callback.

Θα καλύψουμε όλα όσα χρειάζεστε: τις απαιτούμενες βιβλιοθήκες, κώδικα βήμα‑βήμα, γιατί κάθε γραμμή είναι σημαντική, και μια γρήγορη λίστα ελέγχου επαλήθευσης. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο μοτίβο που μπορείτε να ενσωματώσετε σε οποιοδήποτε Java project.

---

## Τι Θα Χρειαστείτε

| Προαπαιτούμενο | Γιατί είναι σημαντικό |
|----------------|------------------------|
| **Java 8+** | Το Aspose.Words απαιτεί τουλάχιστον JDK 8. |
| **Aspose.Words for Java** (τελευταία έκδοση) | Παρέχει `Document`, `MarkdownSaveOptions`, και το interface `IResourceSavingCallback`. |
| **A DOCX file** you want to convert | Το πηγαίο έγγραφο (`input.docx`). |
| **Write permission** on the output directories | Η βιβλιοθήκη θα γράψει το αρχείο Markdown και το φάκελο εικόνων. |

Προσθέστε την εξάρτηση Maven (ή κατεβάστε το JAR) πριν ξεκινήσετε:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version> <!-- check for the newest release -->
</dependency>
```

---

## Βήμα 1 – Φόρτωση του Πηγαίου Εγγράφου Word

Το πρώτο που κάνουμε είναι να δημιουργήσουμε μια παρουσία `Document` που δείχνει στο `.docx` μας. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη, δίνοντάς μας πρόσβαση στο περιεχόμενο, τα στυλ και τους ενσωματωμένους πόρους.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // Load the source .docx
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό:* Αν η διαδρομή του αρχείου είναι λανθασμένη, το Aspose ρίχνει `FileNotFoundException`. Η χρήση απόλυτης ή σωστά επιλυμένης σχετικής διαδρομής αποτρέπει αυτό το πρόβλημα.

---

## Βήμα 2 – Προετοιμασία των Επιλογών Αποθήκευσης Markdown

`MarkdownSaveOptions` μας επιτρέπει να ρυθμίσουμε τη συμπεριφορά της μετατροπής. Από προεπιλογή οι εικόνες αποθηκεύονται δίπλα στο αρχείο Markdown με γενικά ονόματα. Θα το παρακάμψουμε αργότερα, αλλά πρώτα χρειαζόμαστε ένα αντικείμενο επιλογών.

```java
        // Create options for Markdown export
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

*Σημείωση:* Μπορείτε επίσης να ορίσετε `mdOptions.setExportImages(true)` αν θέλετε να ελέγξετε την εξαγωγή εικόνων, αλλά η προεπιλογή είναι ήδη `true`.

---

## Βήμα 3 – Ορισμός Callback Αποθήκευσης Πόρων (Αποθήκευση Εικόνων σε Ξεχωριστό Φάκελο)

Εδώ βρίσκεται η καρδιά του tutorial. Υλοποιώντας το `IResourceSavingCallback` αποκτούμε πλήρη έλεγχο πάνω στο πού καταλήγει κάθε εικόνα. Η callback λαμβάνει ένα αντικείμενο `ResourceSavingArgs` για κάθε πόρο (εικόνες, γραμματοσειρές κ.λπ.) που το Aspose θέλει να γράψει.

```java
        // Customize image saving location
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                // Only intervene for image resources
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    // Build a unique filename based on document hash and original extension
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    // Store images in a dedicated folder
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Let Aspose handle other resource types (e.g., fonts) automatically
            }
        });
```

**Γιατί το κάνουμε αυτό:**  
- **Αποφυγή συγκρούσεων ονομάτων:** Δύο εικόνες με το ίδιο αρχικό όνομα λαμβάνουν διαφορετικά ονόματα αρχείων.  
- **Καθαρότερη δομή έργου:** Όλες οι εικόνες ζουν κάτω από `customImages/`, διατηρώντας τον φάκελο Markdown τακτοποιημένο.  
- **Προβλέψιμες URL:** Το Markdown θα αναφέρει `customImages/img_12345.png`, το οποίο μπορείτε αργότερα να ανεβάσετε σε CDN ή να ενσωματώσετε σε στατικό site.

---

## Βήμα 4 – Αποθήκευση του Εγγράφου ως Markdown

Τώρα λέμε στο Aspose να γράψει το αρχείο Markdown χρησιμοποιώντας τις επιλογές που μόλις διαμορφώσαμε. Η κλήση είναι συγχρονισμένη· όταν επιστρέψει, το αρχείο και οι εικόνες είναι ήδη στο δίσκο.

```java
        // Export to Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

Αν όλα πάνε ομαλά, θα βρείτε:

- `CustomMarkdown.md` που περιέχει το μετατρεπόμενο κείμενο με συνδέσμους εικόνων όπως `![](customImages/img_12345.png)`.  
- Όλα τα αρχεία εικόνων τοποθετημένα μέσα στο `YOUR_DIRECTORY/customImages/`.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται η πλήρης κλάση, έτοιμη για μεταγλώττιση. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο σύστημά σας.

```java
import com.aspose.words.*;

public class MarkdownExportDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source DOCX
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // 3️⃣ Hook into the resource‑saving pipeline
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceFileType() == ResourceFileType.IMAGE) {
                    String uniqueName = "img_" + doc.hashCode() + "." + args.getResourceFileExtension();
                    args.setResourceFileName(uniqueName);
                    args.setResourceFilePath("YOUR_DIRECTORY/customImages/" + uniqueName);
                }
                // Other resources (fonts, etc.) use default handling
            }
        });

        // 4️⃣ Save as Markdown
        doc.save("YOUR_DIRECTORY/CustomMarkdown.md", mdOptions);
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `CustomMarkdown.md` σε οποιονδήποτε επεξεργαστή κειμένου ή προβολέα Markdown. Θα πρέπει να δείτε κάτι όπως:

```markdown
# Sample Document

This is a paragraph from the original Word file.

![](customImages/img_123456789.png)

Another paragraph follows.
```

Το αρχείο εικόνας `img_123456789.png` θα βρίσκεται στον φάκελο `customImages` δίπλα στο αρχείο Markdown.

---

## Pro Συμβουλές & Συνηθισμένα Πιθανά Σφάλματα

- **Υπαρξία φακέλου:** Το Aspose **δεν** δημιουργεί αυτόματα τον φάκελο εικόνων προορισμού. Βεβαιωθείτε ότι το `customImages/` υπάρχει ή δημιουργήστε το προγραμματιστικά πριν την εξαγωγή.  
  ```java
  new java.io.File("YOUR_DIRECTORY/customImages").mkdirs();
  ```
- **Συγκρούσεις hash:** Η χρήση του `doc.hashCode()` είναι συνήθως ασφαλής, αλλά αν εκτελείτε τη μετατροπή πολλές φορές στο ίδιο έγγραφο μπορεί να προκύψουν διπλότυπα ονόματα. Προσθέστε χρονική σήμανση για επιπλέον μοναδικότητα:  
  ```java
  String uniqueName = "img_" + doc.hashCode() + "_" + System.currentTimeMillis() + "." + args.getResourceFileExtension();
  ```
- **Μεγάλα έγγραφα:** Για αρχεία DOCX με χιλιάδες εικόνες, σκεφτείτε να κάνετε streaming την έξοδο ή να αυξήσετε τη μνήμη JVM (`-Xmx2g`).  
- **Μορφές εικόνων:** Το Aspose διατηρεί την αρχική μορφή εικόνας (PNG, JPEG, κ.λπ.). Αν χρειάζεστε όλες τις εικόνες ως PNG, θα πρέπει να επεξεργαστείτε τον φάκελο μετά ή να χρησιμοποιήσετε τις API μετατροπής εικόνας του Aspose.

---

## Συχνές Ερωτήσεις

**Q: Λειτουργεί αυτό με αρχεία .doc ή μόνο με .docx;**  
A: Ναι. Το Aspose.Words ανιχνεύει αυτόματα τη μορφή, οπότε μπορείτε να κατευθύνετε `new Document("file.doc")` και η ίδια διαδικασία θα εκτελεστεί.

**Q: Τι γίνεται αν θέλω οι εικόνες να ενσωματωθούν ως base64 αντί για εξωτερικά αρχεία;**  
A: Ορίστε `mdOptions.setExportImagesAsBase64(true)`. Αυτό θα ενσωματώσει τα δεδομένα της εικόνας απευθείας στο αρχείο Markdown, αλλά χάνετε το πλεονέκτημα του ξεχωριστού φακέλου εικόνων.

**Q: Μπορώ να αλλάξω την επέκταση του αρχείου Markdown σε `.mdx` για έναν static‑site generator;**  
A: Απόλυτα. Το πρώτο όρισμα της μεθόδου `save` είναι απλώς ένα όνομα αρχείου, οπότε `doc.save("output.mdx", mdOptions);` λειτουργεί με τον ίδιο τρόπο.

---

## Συμπεράσματα

Μόλις **εξάγαμε Word σε Markdown** χρησιμοποιώντας το Aspose.Words, δείξαμε πώς να **μετατρέψουμε DOCX σε Markdown**, και παρουσιάσαμε έναν καθαρό τρόπο να **αποθηκεύσουμε τις εικόνες σε ξεχωριστό φάκελο**. Το μοτίβο—φόρτωση → ρύθμιση επιλογών → εισαγωγή callback → αποθήκευση—κλιμακώνεται σε οποιοδήποτε έργο που χρειάζεται αυτοματοποιημένη μετατροπή εγγράφων.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

- Ενσωματώστε αυτόν τον κώδικα σε ένα endpoint REST Spring Boot ώστε οι χρήστες να μπορούν να ανεβάσουν ένα DOCX και να λάβουν ένα έτοιμο‑για‑δημοσίευση πακέτο Markdown.  
- Συνδυάστε το με έναν static‑site generator (π.χ., Hugo) για αυτοματοποίηση των pipelines δημοσίευσης blog.  
- Αντικαταστήστε τη λογική αποθήκευσης εικόνων με αποθήκευση στο cloud (AWS S3, Azure Blob) ανεβάζοντας μέσα στην callback και ορίζοντας το σύνδεσμο Markdown στην δημόσια URL.

Έχετε περισσότερες ερωτήσεις; Αφήστε ένα σχόλιο, και καλή προγραμματιστική δουλειά!

![export word to markdown example](export_word_to_markdown.png "export word to markdown illustration")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}