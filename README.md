🧹 WiseWaste MIS Automation Engine & Data Cleaner
A robust, production-ready Python automation engine designed to transform raw, unformatted Wise Waste Management Information System (MIS) exports—specifically Inward, Outward, and Production—into cleaned, formula-injected, Zoho CRM-compatible Excel workbooks ready for operations and analytics.

📑 Overview & Operational Context
Operating real-world waste management facilities involves handling raw MIS exports from different collection points, material recovery facilities (MRFs), and processing centers. These raw exports present several data challenges:

Unformatted / Missing Parent Rows: Multi-material dispatches or receipts leave parent metadata fields (Inward Code, Outward Code, Vehicle Number, Customer, Shift, Process-Equipment) blank on line items 2, 3, etc.

Zoho CRM Hyperlink Compatibility Issues: Raw image and document links arrive as embedded =HYPERLINK("...", "...") Excel formulas. Importing these into Zoho CRM or databases causes URL corruption (e.g., https://cdn.../=HYPERLINK(...)). This engine sanitizes them into clean, un-wrapped CDN links ([https://cdn.wisewaste.in/](https://cdn.wisewaste.in/)...).

Missing Excel Calculation Formulas: Net values, accepted quantities, and rejection percentages are either missing or exported as static numbers rather than dynamic, audit-ready formulas.

Mixed Production Equipment Workflow: Production logs combine multiple processing lines (Sorting, Bagging, Bailing, Shredding) into a single raw sheet, requiring automated segregation into distinct operational tabs.

wisewaste-data-engine/
├── inward_cleaner.py       # Standalone Inward MIS cleaning & formula injection script
├── outward_cleaner.py      # Standalone Outward MIS cleaning & formula injection script
├── production_cleaner.py   # Production MIS cleaning & multi-process sheet splitter
└── README.md               # Comprehensive architecture & operational documentation

Method A: Running via Google Colab (Recommended)
Create a Colab Notebook:

Go to Google Colab.

Click on File > New Notebook.

Paste the Code:

Copy the code from either inward_cleaner.py, outward_cleaner.py, or production_cleaner.py.

Paste it into a code cell in your Colab notebook.

Execute the Cell:

Press Shift + Enter or click the Play button on the left of the cell.

Upload Your File:

When prompted with: 📂 Please upload your file (.xlsx or .csv):

Automatic Download:

The script will clean the parent rows, inject the formulas, generate clean Zoho-compatible URLs, save the workbook, and automatically trigger your browser download for the resulting cleaned file (Inward_Zoho_Ready.xlsx, Outward_Zoho_Ready.xlsx, or Production_Processed_MultiSheet.xlsx).
