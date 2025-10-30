# -DSA2040A_Load_-Irakoze-aaron-_-515

Aaron Irakoze RuharO

DSA2040A – Lab 5: LOAD PHASE

#Load & Verification

#recommended pacakges for loading phase 
-pandas - for data manipulation and analysis for the excel files (trnasformed_full.xlsx and transformed_incremental.xlsx)
-sqlite3 - for interacting with the SQLite database
-pathlib - for handling file paths

##Format Used
The *SQLite* format was used for the Load phase.  
Both transformed Excel files — 'transformed_full.xlsx' and 'transformed_incremental.xlsx' — were loaded into a database file named `full_data.db, stored in the 'loaded/' folder.

Option 1:
Use sqlite was chosen because it:
- Is lightweight and portable  
- Works directly with Pandas through '.to_sql()' 
- Supports SQL queries for verification and analysis  


#Issues Faced and How They Were Solved

During the Load phase, number of challenges were encountered and resolved to ensure successful database creation and validation:

1. File Format Mismatch  
   - Issue: The transformed datasets were initially saved as ".csv" files, but the loading script used "pd.read_excel()".  
   - Solution:Both datasets were converted to ".xlsx" format and the file paths in the script were updated to match. This allowed pandas to read the files correctly without errors.

2. Missing Folder Error  
   - Issue: When saving the SQLite database, the "loaded/" directory did not exist, leading to a *“No such file or directory”* error.  
   - Solution: The command "Path("loaded").mkdir(exist_ok=True)" was added to automatically create the folder before saving the database file.

3. Datatype Inconsistencies  
   - Issue: Some numeric columns (e.g., prices, quantities) appeared as object (text) types after being read from Excel.  
   - Solution: Column data types were inspected using ".dtypes", and the schema was validated again after loading to ensure that all columns matched their intended data types.

4. low Loading Process 
   - Issue: Writing the full dataset (over 300,000 rows) into SQLite using ".to_sql()" took longer than expected.  
   - Solution: Allowed the process to complete fully and then verified the record counts using SQL queries to confirm that all data was loaded successfully.

5. Verification Display Issue  
   - Issue: The SQLite file ("full_data.db") could not be viewed directly in VS Code.  
   - Solution: Installed the "QLite Viewer" extension in VS Code to visually inspect and confirm that the first 10 rows were loaded correctly into the database tables.

*After resolving these issues, the loading phase ran successfully, and both datasets ("full_data" and "incremental_data") were correctly inserted into the SQLite database for analysis.*
