#### Credit Bill Generator:
Requirements:
- Use monthly Credit card Bills.
- Read the data from the pdf file.
- Populate the data to excel(Sheet Name: pdf_1).
- If there are 2 pdfs then create 2 excel sheets in the same file, one like above and another as sheet name: pdf_2.
- Write a logic that if there is 2nd pdf then bot will run for both the pdf's or bot has do the same thing for 1st pdf.
- Run Macro
	- If there is no 2nd pdf, do the same macro in 1sheet and for that create another macro.( 1st macro for - if there is 1 pdf, 2nd Macro for - if there are 2pdfs)
	- Convert the populated data to table(you can do one after another in same excel but different sheet)
	- Check the date of data in the table. Take the data of that month.
	- Keep the data with similar name in the one below another.
	- After both the data populated in the excel, create 3rd sheet (Sheet Name: Date_Credit Bill)-
		- In that sheet add all the contents in the data in a single table 
	- Populate the output(Addition of all data) at last of the table.
- In message box show the output value.
Note:
- If there is no 2nd pdf we don't need to create 2 sheets.
- Create a string and manually enter the file name and path, if there is 2nd file create string, assign the filename and value to the string. if there is no 2nd file leave the 2nd string empty and create a condition for it.
- Create a 2module(for 2pdfs & 1pdf) that works same as macro using automation anywhere actions(Only if possible).