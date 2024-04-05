# The Diskmag Project

This project is focused on collecting all possible data about the disk magazines (diskmags).
In this repository you will find the datasets containing the collected information on diskmags from various internet sources. 
The data set `mw_import_magazines.csv` contains the merged data from all these sources. 
Now we will explain how to obtain and organize the data for this project.

We also invite you to visit our project site: [diskmags.de](https://diskmags.de/index.php?title=Main_Page)

## 1. Data collection

During data collection, the metadata for each found magazine will be extracted and stored in 
a **JSON** or **CSV** file.
Ideally, the script language *Python* and the corresponding libraries such as 
[Scrapy](https://scrapy.org/), [Selenium](https://www.selenium.dev/) or [Beautiful Soup](https://beautiful-soup-4.readthedocs.io/en/latest/) can be used.
Basically, you can decide yourself what kind of data models you want to create for 
collecting and storing your data.

### 1.1 Source

If you have found the page where the topic "Diskmags" is dealt with, you must first 
determine whether you can extract the metadata there.
Once you have found that the necessary information is there, think about how you 
can collect this data. If you want to automate this process, you can look at the structure 
of the page with **[devtools](https://en.wikipedia.org/wiki/Web_development_tools)**.
Note the HTML elements that are of interest to you and copy the paths to each of these elements. 
Usually these are the XPATH expressions.

Currently, data is collected from the following resources:

**a) Web:**
* Demozoo: [https://demozoo.org](https://demozoo.org/)
* Internet Archive: [https://archive.org](https://archive.org/)
* Kultboy: [https://www.kultboy.com](https://www.kultboy.com/index.php?)
* Pouët: [https://www.pouet.net](https://www.pouet.net/)
* The C-64 Scene Database (CSDB): [https://csdb.dk](https://csdb.dk/)
* ZX Press: [https://zxpress.ru](https://zxpress.ru/)

**b) Books:**
* Volko, Claus-Dieter (2013). *Enzyklopädie der Diskmags*, ISBN: 3656295387 

### 1.2 Scrape the data

Now you can start collecting data. If you do not want to collect the data manually, you can use the libraries 
mentioned above. Write the code in which the information is extracted from the HTML elements you have 
noted. You have to extract some of the following metadata:
* `title`
* `platform`
* `origin/country`
* `language`
* `publication date`
* `link`
* `download link`

Save this data in a JSON or CSV file. You can rely on the files in the repository to choose 
the appropriate data model. Then you can upload your file to this repository, 
name these files as follows: `diskmags_[sourcename].[fileformat]`.

## 2. Data merging

During the data merging process, you will update the main dataset with the information 
you have collected. You can do this manually, otherwise you can automate this process.
The file `mw_import_magazines.csv` has the following structure:

| Title | Magazine[Language] | Magazine[Origin] | Magazine[Start date] | Magazine[End date]  | Magazine[Systems] | Magazine[Issues] |
|-------|--------------------|------------------|----------------------|---------------------|-------------------|------------------|

### 2.1 Case 1: Data are already present in the dataset

If you have collected the information on the diskmag that is already present in this record, 
you need to update the corresponding row. If this diskmag has the same name but a different 
platform (row `Magazine[Systems]`), then it is most likely a completely different diskmag.

### 2.2 Case 2: Data are not present in the dataset

If the diskmags you have found are not present in the dataset, you have to  create a new entry in the 
dataset for each of these diskmags. Make sure that the issues of the same magazine are added as one entry. 

### 2.3 Final steps

Once you have finished the data merging, you need to sort the dataset alphabetically by title (row `Title`). 
To avoid the misunderstandings with upper and lower case, do the case-insensitive sort.
Upload the updated file to this repository. In the description of the commit, you have to explain what you have done.

## Mediawiki
The Structure for the mediawiki: 
![image](https://github.com/zpd-digital-editions/Diskmags/assets/24278823/8a4fc78c-75b0-4988-8786-1b7929a1f9c4)

The correlated data will be published here soon.
