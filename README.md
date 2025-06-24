This repository will hold the publicly released anonymized logs and scripts for DOI 10.1145/3478432.3499123

### Update on June 17, 2025
- Specified column names in the cleaned datasets. The raw logs(`final-time.tsv`, `midterm-time.tsv`) were left unmodified.
  - `curr_time`: Elapsed time in milliseconds  
  - `id`: Student ID  
  - `question`: Question identifier in the format `q<category_number>_<question_number>`  
  - `score`: Student's score on the specific question at the current timestamp  

#### Time-Related Cleaning
1. `clean_time_final.tsv` and `clean_time_mid.tsv`
   Contain the cleaned time-related datasets for the final and midterm exams, respectively.  
   Each included student ID has only valid (non-negative) `curr_time` entries and a complete set of questions.

> The `.tsv` files below contain discarded entries from the original dataset during the cleaning process:
2. `corrupted_time_final.tsv` and `corrupted_time_mid.tsv`
   Contain all log entries for any student ID with at least one negative `curr_time` value.  
   These entries were excluded under the assumption that negative timestamps indicate a corrupted log.
3. `incomplete_time_final.tsv` and `incomplete_time_mid.tsv`  
   Contain all log entries for student IDs who viewed fewer or more than the number of questions assigned in the exam:
   - 7 questions for the midterm  
   - 8 questions for the final  
   These logs were excluded based on the assumption that a valid student log should include exactly all assigned questions for the midterm/final.

---

#### Non-Time-Related Cleaning
1. `clean_non_time_final.tsv` and `clean_non_time_mid.tsv`  
   Contain the cleaned non-time-related datasets for the final and midterm exams, respectively.  
   Each included student ID has a complete set of questions.
   These files may contain entries with negative `curr_time` values, as time was not a criterion for this cleaning.

> The `.tsv` files below contain discarded entries from the original dataset during the cleaning process:
2. `incomplete_non_time_final.tsv` and `incomplete_non_time_mid.tsv`  
   Contain all log entries for student IDs who viewed fewer or more than the number of questions assigned in the exam:
   - 7 questions for the midterm  
   - 8 questions for the final  
   These logs were excluded under the assumption that a valid student log should include exactly all assigned questions for the midterm/final.
