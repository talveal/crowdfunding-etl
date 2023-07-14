# Project 2: Group 7 Crowdfunding-ETL
## Team Members: Rehman Butt, Tatiana Alveal, Susan Abraham, & Crystal Burkhardt 

Option-1 being used as per requirements to utilize Pandas dictionaries.

For the ETL mini project, we worked in a team of four to practice building an ETL pipeline using Python, Pandas, and either Python dictionary methods or regular expressions to extract and transform the data. After we transformed the data, we created four CSV files and used the CSV file data to create a table schema. Finally, we uploaded the CSV file data into a Postgres database.

After creating the table schema, we successfully created the 4 required tables and able to load the data successfully from 4 files into the newly created tables in PGAdmin. Once the data is loaded, we ran the select statement to pull the data from each table and provided screenshots in a pdf file for results coming from all 4 queris. 

## Instructions
The instructions for this mini project are divided into the following subsections:

💠 Create the Category and Subcategory DataFrames <br>
💠 Create the Campaign DataFrame<br>
💠 Create the Contacts DataFrame<br>
💠 Create the Crowdfunding Database<br>
  
## Create the Category and Subcategory DataFrames
1. Extract and transform the crowdfunding.xlsx Excel data to create a category DataFrame that has the following columns:
💠 A "category_id" column that has entries going sequentially from "cat1" to "catn", where n is the number of unique categories<br>
💠 A "category" column that contains only the category titles<br>
💠 The following image shows this category DataFrame:<br>

<img width="190" alt="category_DataFrame" src="https://github.com/talveal/crowdfunding-etl/assets/128064003/4d354657-ad85-4541-a5ca-6c95fbfecbbd">

2. Export the category DataFrame as category.csv and save it to your GitHub repository.
3. Extract and transform the crowdfunding.xlsx Excel data to create a subcategory DataFrame that has the following columns:
💠 A "subcategory_id" column that has entries going sequentially from "subcat1" to "subcatn", where n is the number of unique subcategories<br>
💠 A "subcategory" column that contains only the subcategory titles<br>
💠 The following image shows this subcategory DataFrame:<br>
 
<img width="250" alt="subcategory_DataFrame" src="https://github.com/talveal/crowdfunding-etl/assets/128064003/0458790a-edda-4c4a-a718-58392604b547">

4. Export the subcategory DataFrame as subcategory.csv and save it to your GitHub repository.

## Create the Campaign DataFrame
1. Extract and transform the crowdfunding.xlsx Excel data to create a campaign DataFrame has the following columns:
💠 The "cf_id" column<br>
💠 The "contact_id" column<br>
💠 The "company_name" column<br>
💠 The "blurb" column, renamed to "description"<br>
💠 The "goal" column, converted to the float data type<br>
💠 The "pledged" column, converted to the float data type<br>
💠 The "outcome" column<br>
💠 The "backers_count" column<br>
💠 The "country" column<br>
💠 The "currency" column<br>
💠 The "launched_at" column, renamed to "launch_date" and with the UTC times converted to the datetime format<br>
💠 The "deadline" column, renamed to "end_date" and with the UTC times converted to the datetime format<br>
💠 The "category_id" column, with unique identification numbers matching those in the "category_id" column of the category DataFrame<br>
💠 The "subcategory_id" column, with the unique identification numbers matching those in the "subcategory_id" column of the subcategory DataFrame<br>
💠 The following image shows this campaign DataFrame:<br>

<img width="1074" alt="campaign_DataFrame" src="https://github.com/talveal/crowdfunding-etl/assets/128064003/c1862b79-6cd3-4b73-9d31-8f4fbcd643ad">

2. Export the campaign DataFrame as campaign.csv and save it to your GitHub repository.

## Create the Contacts DataFrame
1. Choose one of the following two options for extracting and transforming the data from the contacts.xlsx Excel data:
💠 Option 1: Use Python dictionary methods. NOTE: Our team chose to utilize this method. <br>
💠 Option 2: Use regular expressions.<br>

2. If you chose Option 1, complete the following steps:
💠 Import the contacts.xlsx file into a DataFrame.<br>
💠 Iterate through the DataFrame, converting each row to a dictionary.<br>
💠 Iterate through each dictionary, doing the following:<br>
💠 Extract the dictionary values from the keys by using a Python list comprehension.<br>
💠 Add the values for each row to a new list.<br>
💠 Create a new DataFrame that contains the extracted data.<br>
💠 Split each "name" column value into a first and last name, and place each in a new column.<br>
💠 Clean and export the DataFrame as contacts.csv and save it to your GitHub repository.<br>

3. If you chose Option 2, complete the following steps:
💠 Import the contacts.xlsx file into a DataFrame.<br>
💠 Extract the "contact_id", "name", and "email" columns by using regular expressions.<br>
💠 Create a new DataFrame with the extracted data.<br>
💠 Convert the "contact_id" column to the integer type.<br>
💠 Split each "name" column value into a first and a last name, and place each in a new column.<br>
💠 Clean and then export the DataFrame as contacts.csv and save it to your GitHub repository.<br>
  
4. Check that your final DataFrame resembles the one in the following image:

<img width="415" alt="contact_DataFrame_final" src="https://github.com/talveal/crowdfunding-etl/assets/128064003/40088274-c7c1-4b3c-aaee-1d737d481a86">

## Create the Crowdfunding Database
1. Inspect the four CSV files, and then sketch an ERD of the tables by using QuickDBDLinks to an external site..
2. Use the information from the ERD to create a table schema for each CSV file. Note: Remember to specify the data types, primary keys, foreign keys, and other constraints.
3. Save the database schema as a Postgres file named crowdfunding_db_schema.sql, and save it to your GitHub repository.
4. Create a new Postgres database, named crowdfunding_db.
5. Using the database schema, create the tables in the correct order to handle the foreign keys.
6. Verify the table creation by running a SELECT statement for each table.
7. Import each CSV file into its corresponding SQL table.
8. Verify that each table has the correct data by running a SELECT statement for each.

## Hints
💠 To split each "category & sub-category" column value into "category" and "subcategory" column values, use df[["new_column1","new_column2"]] = df["column"].str.split(). Make sure to pass the correct parameters to the split() function.<br>
💠 To get the unique category and subcategory values from the "category" and "subcategory" columns, create a NumPy array where the array length equals the number of unique categories and unique subcategories from each column. For information about how to do so, see numpy.arangeLinks to an external site. in the NumPy documentation.<br>
💠 To create the category and subcategory identification numbers, use a list comprehension to add the "cat" string or the "subcat" string to each number in the category or the subcategory array, respectively.<br>
💠 For more information about creating a new Pandas DataFrame, see the pandas.DataFrameLinks to an external site. in the Pandas documentation.<br>
💠 To convert the "goal" and "pledged" columns to the float data type, use the astype() method.<br>
💠 To convert the "launch_date" and "end_date" UTC times to the datetime format, see the Transform_Grocery_Orders_Solved.ipynb activity solution.<br>
💠 For more information about how to add the "category_id" and "subcategory_id" unique identification numbers to the campaign DataFrame, see the pandas.DataFrame.mergeLinks to an external site. in the Pandas documentation.<br>
