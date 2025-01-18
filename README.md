# **C. elegans Gene Analysis 2024**

## **Project Overview**
This project investigates the *C. elegans* gene `sra-4` (Serpentine Receptor A), which has an unknown function. The study aims to determine its potential biological role and its relationship with human proteins. By leveraging computational tools and Hidden Markov Models (HMMs), the analysis reveals critical insights into the gene’s conserved domains, potential human orthologs, and its implications as a drug target.

---

## **Key Highlights**
- **Gene Analyzed**: `sra-4` (*C. elegans*).
- **Techniques Applied**: Comparative analysis using BLAST and HMMER.
- **Outcomes**:
  - Identified conserved regions and domains.
  - Found connections to human orthologs through HMM profile matching.
  - Proposed potential biological roles and drug target implications.

---

## **Tools and Technologies**
### **Software**:
- **BLAST**: Sequence comparison and alignment tool.
- **HMMER**: Profile Hidden Markov Models for protein analysis.

### **Datasets**:
- Protein sequence for `sra-4` downloaded from [UniProt](https://www.uniprot.org/) (ID: Q09206).
- Human genome data from [NCBI](https://www.ncbi.nlm.nih.gov/).

---

## **Getting Started**

### **Prerequisites**
1. **Install BLAST**:
   - Download and install BLAST+ from the [NCBI website](https://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download).
2. **Install HMMER**:
   - Follow the installation guide on [HMMER’s website](http://hmmer.org/).

### **Data Preparation**
1. **Sequence Retrieval**:
   - Download the `sra-4` sequence in FASTA format from UniProt.
   - Obtain comparison datasets such as human protein sequences from NCBI.
2. **File Structure**:
   - Organize files as follows:
     ```
     C-elegans_Gene_Analysis_2024/
      ├── README.md
      ├── HMM/
      │   ├── Viterbi.py
      │   ├── Islands.py
      │   ├── chr_22.txt
      │   └── alignments/ 
      ├── BLAST/
      │   ├── blast_results.txt
      │   ├── sra-4.fasta
      └── Analysis/
         ├── results_summary.md
         ├── diagrams/
         └── raw_data/
     ```

---

## **Steps to Run the Analysis**

### **1. BLAST Analysis**
- Use `blastp` to compare the `sra-4` sequence with the non-redundant (nr) protein database.
- Example command:
  ```bash
  blastp -query BLAST/sra-4.fasta -db nr -out BLAST/blast_results.txt -evalue 0.01 -max_target_seqs 10
  ```
- Record significant hits and note any human orthologs with low E-values (<0.01).

### **2. HMMER Analysis**
- Use `phmmer` to detect conserved domains and motifs.
- Example steps:
  1. Search for the `sra-4` sequence against Pfam using `hmmscan`.
  2. Retrieve significant matches (E-value <0.01).
  3. Download alignments in Stockholm format and process them.
- Use `hmmsearch` to query the profile HMM against a human protein database:
  ```bash
  hmmsearch --tblout HMMER/hmm_results.txt alignments/your_alignment.sto
  ```

### **3. Viterbi and HMM Simulations**
- Modify and run `Viterbi.py` for state sequence predictions.
- Analyze emitted sequences and probabilities to understand transitions.

---

## **Results and Findings**
- **BLAST Results**:
  - No direct human orthologs identified with significant similarity.
  - Matches primarily included *C. elegans* genes and closely related species.
- **HMMER Results**:
  - Identified family: **7TM_GPCR_Sra** (Serpentine type 7TM GPCR chemoreceptor Sra).
  - Representative alignment: 308 proteins in Pfam family.
  - Significant match: **Prostaglandin E2 receptor EP2 subtype** (human gene).
- **Functional Insights**:
  - Sra-4 functions as a sensory receptor in *C. elegans*, likely involved in chemotaxis and signal transduction.
  - Its human ortholog, Prostaglandin E2 receptor, plays a role in inflammation and signal transduction.

---

## **Conclusion**
This project highlights the utility of computational tools like BLAST and HMMER for functional annotation and comparative genomics. The identification of a human ortholog for the *C. elegans* `sra-4` gene emphasizes the evolutionary conservation of sensory receptors and their potential as drug targets.

---

## **References**
1. [BLAST Documentation](https://blast.ncbi.nlm.nih.gov/Blast.cgi)
2. [HMMER User Guide](http://hmmer.org/)
3. [UniProt Protein Database](https://www.uniprot.org/)
4. [Pfam Database](https://pfam.xfam.org/)
5. [NCBI Database](https://www.ncbi.nlm.nih.gov/)
