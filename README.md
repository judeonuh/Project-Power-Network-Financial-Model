# Power Network Excel Financial Model
___

![Power_image](power_image.jpg)  

---

### Description
This project builds a scalable Excel financial model for a power distribution company, automating 5-year fixed charge calculations across multiple network regions and customer bands, eliminating manual rebuilds when onboarding new regions. 

---

### Table of Contents  
- [Description](#description)
- [Skills Demonstrated](#skills-demonstrated)
- [Data Sources](#data-sources)
- [Usage Instructions](#usage-instructions)
- [Data Cleaning and Preprocessing](#data-cleaning-and-preprocessing)
- [Data Analysis and Discussion](#data-analysis-and-discussion)
- [Replicating Model](#replicating-model)
- [Further Improvements](#further-improvements)

---

### Skills Demonstrated  
- VLOOKUP
- IFERROR
- Power Query
- Data Cleaning
- Financial Modelling

---

### Data Sources
Datasets for this project were obtained from a Power company, and files were named according to the regions within their power network. All datasets can be found [here](financial_data_sheets)

---

### Data Cleaning and Preprocessing
On the financial model...
- Data was cleaned using the 'trim' function to remove trailing whitespaces; 'iferror' to assign values (0 for numerical columns or "-" for text columns ) to empty cells that may return '#N/A' errors.
- To get the names of customers on the "Name" column for each sheet, link/extract this from their respective data sheets.
> [!Warning]
> On your Excel sheet, ensure the number format for the "Name" column is set to "General"
- Using the VLOOKUP function, extract the Residual Charging Bands of each customer from their respective data sheets.
- Populate the Import Fixed Charges (IFC) for each customer from 2020 to 2024 using the VLOOKUP function.
> [!WARNING]
> For quick retrieval of the IFC: After using VLOOKUP for the first IFC column, say 2020_IFC, copy the formula for this column into the next column, say 2021_IFC. Next, navigate to the formula bar on this column and change the year accordingly - in this case, from 2020/21 to 2021/22.
> Repeat the same for every column. This way, the model allows you to extract any customer's IFC for any year by just editing the year on the formula bar.
- Calculate the Annual Fixed Charge (AFC) (in £) for each customer by dividing IFC (this is in pence) by 100 and multiplying by 365 or 366 (for a leap year)
- Calculate the Year-on-Year percentage change on AFC using the formular "(current year AFC/ previous year AFC)-1"
- Summarise data using a pivot table and a chart

---

### Usage Instructions
- Data analysis was performed on Microsoft Excel. Download and install MS Excel on your machine. If you have not already, this software can be downloaded [here](https://www.microsoft.com/en-gb/microsoft-365/excel?ef_id=_k_7f6ebb9ae2b216bcec3edc83309dd670_k_&OCID=AIDcmmp20rgnjr_SEM__k_7f6ebb9ae2b216bcec3edc83309dd670_k_&msclkid=7f6ebb9ae2b216bcec3edc83309dd670).
- Ensure all data files are located in the same directory and maintain a consistent naming pattern for all files.
> [!WARNING]
> Saving files on an online platform (e.g. OneDrive) could cause any link in the file to load more slowly, throwing up warning alerts. So, preferably, save files on the desktop or the "C Drive"

---

### Data Analysis and Discussion


---

### Replicating Model
To replicate this model for any new Network/region of customers...
- Create a copy of your model and rename this copy as the new Network/region
- Delete all the records presently on the new sheet EXCEPT the first 5 records.
- Select any cell from the above 5 records and change the links to your new data sheet. By doing this, the model automatically extracts data from the new linked data sheet without the need to rewrite formulas again. To edit/change links...
  -  Select a non-empty cell
  -  Go to the "Data" Tab, click on "Edit Links".
  -  From the opened dialogue box, select the new data sheet you want and click on "Change Source".
  -  Click "Close" when finished.
  -  Select all records and fill downwards
- Refresh any Pivot table connected to your data
> [!CAUTION]
> It is recommended to break all links before exporting or sharing your model with others, for security reasons.
> Go to "Data" Tab, click on "Edit Links", select all links and click "Break link".
> NOTE: Broken links can not be undone!
___
