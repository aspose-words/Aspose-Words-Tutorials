---
category: general
date: 2026-06-24
description: Εκτελέστε έλεγχο γραμματικής σε ένα DOCX χρησιμοποιώντας Java. Μάθετε
  πώς να φορτώνετε docx με Java, να διαμορφώνετε ένα αυτο-φιλοξενούμενο LLM και να
  λαμβάνετε το διορθωμένο κείμενο σε λίγα εύκολα βήματα.
draft: false
keywords:
- run grammar check
- load docx java
- get revised text
- configure self hosted llm
language: el
og_description: Εκτελέστε έλεγχο γραμματικής σε αρχείο DOCX με Java. Αυτό το σεμινάριο
  δείχνει πώς να φορτώσετε DOCX με Java, να διαμορφώσετε ένα αυτο-φιλοξενούμενο LLM
  και να λάβετε γρήγορα το διορθωμένο κείμενο.
og_title: Εκτέλεση ελέγχου γραμματικής σε DOCX με Java – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Run grammar check on a DOCX using Java. Learn how to load docx java,
    configure self hosted llm and get revised text in a few easy steps.
  headline: Run Grammar Check on DOCX in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- AI
- Document Processing
title: Εκτέλεση ελέγχου γραμματικής σε DOCX με Java – Πλήρης οδηγός προγραμματισμού
url: /el/java/ai-machine-learning-integration/run-grammar-check-on-docx-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εκτέλεση ελέγχου γραμματικής σε DOCX με Java – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **εκτελέσετε έλεγχο γραμματικής** σε ένα έγγραφο Word από μια εφαρμογή Java, αλλά δεν ήξερες πώς να συνδέσεις ένα αυτο‑φιλοξενούμενο μεγάλο μοντέλο γλώσσας (LLM); Δεν είστε μόνοι. Σε πολλές επιχειρήσεις η πολιτική είναι να διατηρούν τις υπηρεσίες AI εντός των εγκαταστάσεων, πράγμα που σημαίνει ότι πρέπει να διαμορφώσετε το σημείο άκρου μόνοι σας και στη συνέχεια να τροφοδοτήσετε το κείμενο του εγγράφου για διόρθωση.

Σε αυτόν τον οδηγό θα περάσουμε από κάθε βήμα: από **load docx java** μέχρι **configure self hosted llm**, και τελικά **get revised text** μετά την εκτέλεση του ελέγχου γραμματικής. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

---

## Γιατί να εκτελείτε έλεγχο γραμματικής προγραμματιστικά

Πριν βουτήξουμε στον κώδικα, ας απαντήσουμε στο «γιατί». Η αυτοματοποιημένη διόρθωση γραμματικής μπορεί να:

* **Βελτιώστε την ποιότητα του περιεχομένου** για αυτόματα δημιουργημένες αναφορές, τιμολόγια ή προσχέδια email.  
* **Επιβάλετε οδηγίες στυλ** σε όλη την ομάδα χωρίς χειροκίνητη επιμέλεια.  
* **Εξοικονομήστε χρόνο** — αυτό που πήρε λεπτά ανά έγγραφο τώρα συμβαίνει σε χιλιοστά του δευτερολέπτου.

Και επειδή χρησιμοποιούμε ένα **self‑hosted LLM**, διατηρείτε τα δεδομένα μέσα στο τείχος προστασίας σας, παραμένετε σύμφωνοι με το GDPR ή το HIPAA, και αποφεύγετε δαπανηρές κλήσεις API σε υπηρεσίες τρίτων.

## Βήμα 1: Φόρτωση DOCX σε Java

Το πρώτο που χρειάζεστε είναι ένας τρόπος για να διαβάσετε ένα αρχείο `.docx`. Υπάρχουν διάφορες βιβλιοθήκες, αλλά για αυτό το tutorial θα χρησιμοποιήσουμε το **Aspose.Words for Java** επειδή προσφέρει ένα απλό API και λειτουργεί καλά με επεκτάσεις AI.

```java
import com.aspose.words.Document;
import java.nio.file.Paths;

/**
 * Loads a DOCX file from the given path.
 *
 * @param path absolute or relative path to the .docx file
 * @return Document object representing the Word file
 * @throws Exception if the file cannot be read
 */
public static Document loadDocx(String path) throws Exception {
    // Validate the file exists before attempting to load
    if (!Paths.get(path).toFile().exists()) {
        throw new IllegalArgumentException("File not found: " + path);
    }
    // Aspose.Words handles DOCX parsing internally
    return new Document(path);
}
```

**Γιατί είναι σημαντικό:**  
Η σωστή φόρτωση του εγγράφου εξασφαλίζει ότι όλο το κείμενο, οι υποσημειώσεις και οι πίνακες διατηρούνται. Αν παραλείψετε την επικύρωση, μπορεί να λάβετε ένα `FileNotFoundException` αργότερα, κάτι που μπορεί να προκαλέσει σύγχυση κατά τον εντοπισμό σφαλμάτων κλήσεων σχετικών με AI.

## Βήμα 2: Διαμόρφωση Self‑Hosted LLM

Τώρα λέμε στη βιβλιοθήκη ποιο μοντέλο AI να χρησιμοποιήσει. Η κλάση `AiOptions` (παρέχεται από το ίδιο SDK) σας επιτρέπει να δείξετε σε οποιοδήποτε συμβατό με OpenAI σημείο άκρου, όπως ένα τοπικά εκτελούμενο Llama ή ένα προσαρμοσμένο εκπαιδευμένο μοντέλο.

```java
import com.aspose.words.ai.AiOptions;
import com.aspose.words.ai.AiModelProvider;

/**
 * Prepares AI options for a self‑hosted LLM.
 *
 * @param endpoint URL of the local model server (e.g., http://my-llm.local/v1)
 * @param apiKey   Secret key for authentication; may be empty if not required
 * @return Configured AiOptions instance
 */
public static AiOptions configureSelfHostedLLM(String endpoint, String apiKey) {
    AiOptions options = new AiOptions();
    // Tell the SDK we are using a self‑hosted provider
    options.setModelProvider(AiModelProvider.SELF_HOSTED);
    options.setEndpoint(endpoint);
    // Some deployments require an API key; others don’t.
    if (apiKey != null && !apiKey.isBlank()) {
        options.setApiKey(apiKey);
    }
    return options;
}
```

**Γιατί είναι σημαντικό:**  
Η σκληρή κωδικοποίηση του σημείου άκρου ή η παράλειψη του καθορισμού του παρόχου θα κάνει το SDK να επιστρέφει στην προεπιλεγμένη υπηρεσία cloud, κάτι που αναιρεί τον σκοπό ενός σεναρίου **configure self hosted llm**. Πάντα ελέγχετε διπλά τη μορφή του URL (συμπεριλάβετε `http://` ή `https://`) και βεβαιωθείτε ότι ο διακομιστής είναι προσβάσιμος.

## Βήμα 3: Εκτέλεση ελέγχου γραμματικής και λήψη διορθωμένου κειμένου

Με το έγγραφο φορτωμένο και τις επιλογές AI έτοιμες, μπορούμε τελικά να **εκτελέσουμε έλεγχο γραμματικής**. Το SDK επιστρέφει ένα `GrammarCheckResult` που περιέχει τη διορθωμένη έκδοση του αρχικού κειμένου.

```java
import com.aspose.words.ai.GrammarCheckResult;

/**
 * Executes a grammar check on the given Document using the supplied AI options.
 *
 * @param doc     Document to be processed
 * @param aiOpts  Configured AI options pointing to the self‑hosted LLM
 * @return The revised text after grammar correction
 * @throws Exception if the AI service fails or returns an error
 */
public static String runGrammarCheck(Document doc, AiOptions aiOpts) throws Exception {
    // The checkGrammar method sends the document content to the LLM
    GrammarCheckResult result = doc.checkGrammar(aiOpts);
    // Extract the corrected text
    return result.getRevisedText();
}
```

**Γιατί είναι σημαντικό:**  
Η κλήση του `checkGrammar` ενεργοποιεί ένα αίτημα δικτύου προς το LLM σας. Εάν το μοντέλο δεν είναι λεπτορυθμισμένο για εργασίες γραμματικής, μπορεί να λάβετε παράξενες προτάσεις. Η δοκιμή με μια σύντομη παράγραφο πρώτα σας βοηθά να αξιολογήσετε την ποιότητα πριν την κλιμάκωση σε ολόκληρες αναφορές.

## Συνένωση όλων – Πλήρες Παράδειγμα Εργασίας

Παρακάτω υπάρχει ένα ελάχιστο, αυτόνομο πρόγραμμα Java που δείχνει ολόκληρη τη ροή. Επικολλήστε το σε ένα αρχείο με όνομα `GrammarChecker.java`, προσθέστε την εξάρτηση Aspose.Words Maven, και εκτελέστε το από τη γραμμή εντολών.

```java
// GrammarChecker.java
import com.aspose.words.Document;
import com.aspose.words.ai.AiOptions;
import com.aspose.words.ai.AiModelProvider;
import com.aspose.words.ai.GrammarCheckResult;

public class GrammarChecker {

    public static void main(String[] args) {
        try {
            // 1️⃣ Load the DOCX file
            Document doc = loadDocx("input.docx");

            // 2️⃣ Configure the self‑hosted LLM
            AiOptions aiOptions = configureSelfHostedLLM(
                    "http://my-llm.local/v1",   // endpoint
                    "my-secret-key"             // API key (if required)
            );

            // 3️⃣ Run the grammar check and retrieve revised text
            String revised = runGrammarCheck(doc, aiOptions);

            // 4️⃣ Display the revised text
            System.out.println("=== Revised Text ===");
            System.out.println(revised);
        } catch (Exception e) {
            System.err.println("Error during grammar check: " + e.getMessage());
            e.printStackTrace();
        }
    }

    // ----- Helper methods (see earlier sections) -----
    public static Document loadDocx(String path) throws Exception {
        if (!java.nio.file.Paths.get(path).toFile().exists()) {
            throw new IllegalArgumentException("File not found: " + path);
        }
        return new Document(path);
    }

    public static AiOptions configureSelfHostedLLM(String endpoint, String apiKey) {
        AiOptions options = new AiOptions();
        options.setModelProvider(AiModelProvider.SELF_HOSTED);
        options.setEndpoint(endpoint);
        if (apiKey != null && !apiKey.isBlank()) {
            options.setApiKey(apiKey);
        }
        return options;
    }

    public static String runGrammarCheck(Document doc, AiOptions aiOpts) throws Exception {
        GrammarCheckResult result = doc.checkGrammar(aiOpts);
        return result.getRevisedText();
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Αν το `input.docx` περιέχει την πρόταση:

```
She go to the market yesterday.
```

Η εκτέλεση του προγράμματος εκτυπώνει κάτι όπως:

```
=== Revised Text ===
She went to the market yesterday.
```

Η ακριβής διατύπωση μπορεί να διαφέρει ανάλογα με το πώς εκπαιδεύτηκε το **self hosted llm** σας, αλλά η γραμματική θα πρέπει να είναι διορθωμένη.

![Παράδειγμα εξόδου ελέγχου γραμματικής](https://example.com/images/grammar-check-output.png "Παράδειγμα εξόδου ελέγχου γραμματικής")

*Κείμενο alt εικόνας:* **run grammar check example output**

## Συνηθισμένα προβλήματα & Συμβουλές Pro

| Πρόβλημα | Γιατί συμβαίνει | Πώς να διορθώσετε / Αποφύγετε |
|------|----------------|--------------------|
| **FileNotFoundException** κατά τη φόρτωση του DOCX | Η διαδρομή είναι σχετική με τον τρέχοντα φάκελο εργασίας, όχι με τη θέση του αρχείου πηγής. | Χρησιμοποιήστε απόλυτη διαδρομή ή `Paths.get("").toAbsolutePath()` για εντοπισμό σφαλμάτων. |
| **Connection timeout** στο σημείο άκρου LLM | Ο αυτο‑φιλοξενούμενος διακομιστής είναι εκτός λειτουργίας ή μπλοκαρισμένος από τείχος προστασίας. | Επαληθεύστε το URL με `curl` ή έναν περιηγητή, και ανοίξτε τις απαιτούμενες θύρες (συνήθως 80/443). |
| **Κενό διορθωμένο κείμενο** | Το μοντέλο δεν είναι ρυθμισμένο για εργασίες γραμματικής· επιστρέφει την αρχική είσοδο. | Λεπτορυθμίστε το LLM σε σύνολο δεδομένων διόρθωσης γραμματικής ή μεταβείτε σε μοντέλο γνωστό για επεξεργασία (π.χ., `gpt‑4o‑mini` της OpenAI). |
| **Αυξημένη χρήση μνήμης σε μεγάλα έγγραφα** | Το Aspose φορτώνει ολόκληρο το DOCX στη μνήμη πριν το στείλει στο LLM. | Διαχωρίστε το έγγραφο σε ενότητες (`doc.getSections()`) και επεξεργαστείτε κάθε τμήμα ξεχωριστά. |
| **Διαρροή κλειδιού API** | Σκληρή κωδικοποίηση μυστικών σε έλεγχο πηγαίου κώδικα. | Αποθηκεύστε το κλειδί σε μεταβλητές περιβάλλοντος (`System.getenv("LLM_API_KEY")`) και διαβάστε το κατά την εκτέλεση. |

**Συμβουλή Pro:** Όταν ενσωματώνετε για πρώτη φορά ένα νέο LLM, ξεκινήστε με ένα μικρό δοκιμαστικό έγγραφο (μια παράγραφο). Με αυτόν τον τρόπο μπορείτε να εξετάσετε το JSON payload που στέλνει το Aspose και να διασφαλίσετε ότι η μορφή της απάντησης του μοντέλου ταιριάζει με αυτό που αναμένει το `GrammarCheckResult`.

## Επέκταση της Λύσης

Τώρα που μπορείτε να **run grammar check** και **get revised text**, σκεφτείτε τα επόμενα βήματα:

* **Batch processing** – Επανάληψη σε έναν φάκελο αρχείων DOCX και εγγραφή των διορθωμένων εκδόσεων σε φάκελο εξόδου.  
* **Integrate with a web service** – Εκθέστε ένα endpoint που δέχεται ανεβασμένα αρχεία DOCX, εκτελεί τον έλεγχο, και επιστρέφει το διορθωμένο κείμενο ως JSON.  
* **Add style enforcement** – Συνδυάστε το `checkGrammar` με το `checkSpelling` ή προσαρμοσμένους κανόνες regex για ορολογία ειδική της εταιρείας.  
* **Persist revisions** –  

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να εξάγετε κείμενο χρησιμοποιώντας το Aspose.Words για Java](/words/english/java/document-manipulation/extracting-content-from-documents/)
- [Πώς να δημιουργήσετε αρχείο απλού κειμένου με το Aspose.Words για Java](/words/english/java/document-loading-and-saving/saving-documents-as-text-files/)
- [Πώς να μετατρέψετε DOCX σε PNG με Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}