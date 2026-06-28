Cleaning Log

This document summarizes all the data cleaning, validation, and transformation steps I performed on the retail orders dataset to get it ready for analysis and dashboard building.
Issues Identified
Inconsistent text formatting in several columns
Extra leading and trailing spaces
Mixed uppercase and lowercase text
Missing values in Region, Ship Mode, and Discount columns
Exact duplicate records
Duplicate Order IDs that needed checking
Invalid shipping records (Ship Date before Order Date)
Missing discount values
Inconsistent Order Status and Payment Status entries
Sales and Profit fields that required validation
Cleaning Actions Performed
Kept the original dataset untouched and created a separate cleaned version
Removed extra spaces using TRIM
Standardized text using PROPER, UPPER, and Find & Replace
Standardized values for Region, Category, Sub-Category, Ship Mode, Payment Status, and Order Status
Filled missing Region values with “Unknown”
Filled missing Ship Mode values with “Unknown”
Replaced missing Discount values with 0 (where it made business sense)
Removed exact duplicate records
Flagged duplicate Order IDs for further review
Standardized date formats for Order Date and Ship Date
Flagged records where Ship Date was earlier than Order Date
Added several useful calculated columns:
Cleaned Discount
Calculated Sales
Calculated Profit
Profit Margin
Shipping Delay Days
Order Month & Year
Data Quality Flag
Business Rules Applied
Missing Region → replaced with “Unknown”
Missing Ship Mode → replaced with “Unknown”
Missing Discount → set to 0 only when other sales fields were valid
Negative discounts → marked as invalid
Failed payments and Cancelled orders → excluded from completed sales analysis
Refunded orders → summarized separately
Records with Ship Date before Order Date → flagged as invalid
Duplicate Handling
Removed exact duplicate rows completely
Kept duplicate Order IDs but flagged them for manual review (in case they had conflicting information)
Assumptions
Blank Discount values mean “no discount” when the rest of the sales data looks valid
“Unknown” values for Region and Ship Mode are acceptable for now and can be corrected later
Sales and profit calculations are based on Quantity × Unit Price × Cleaned Discount
Records Summary
Original Records: 932
Exact Duplicates Removed: 20
Final Clean Records: 912
Limitations
Validation was done only on the data we received
Records flagged as invalid still need review by the business team
We assume the source data from the operational system is mostly complete, except for the quality issues we found