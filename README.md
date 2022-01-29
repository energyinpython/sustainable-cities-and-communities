# DARIA-for-sustainability-assessment
Here is a step-by-step guide of using Python software for obtaining an overall aggregate ranking of European countries evaluated towards sustainability using **Data vaRIability based Assessment (DARIA)**. It is a newly developed method that integrates MCDA methods with measuring rankings' variability and direction of variability in investigated periods of time. 
1. ***Prepare dataset***. Load data downloaded as CSV files from Eurostat with **eurostat_reader**.
If something is laborious and tedious, we automatize it! Need EUROSTAT data, but the differences in the available tables require a lot of manual shifts? It takes much time, besides it is easy to make a mistake. This script **(eurostat_reader.py)** is intended to handle pre-prepared tables taken from CSV files from EUROSTAT (sample data including Sustainable Development Indicators are available at https://ec.europa.eu/eurostat/web/sdi/main-tables). We focus on the **_SDG11_** indicator. Just prepare easily and quickly tables as shown in examples provided in DATASET, specify the years and countries you are interested in and run this script. This way, you will quickly, easily, and pleasantly prepare your data from EUROSTAT and, most importantly, without the risk of errors. Results for all selected years are demonstrated in sample CSV file in **eurostat_reader/output_all**. Then, you can use **eurostat_dataset_creator** for preparing datasets in CSV files for selected years. Missing data for particular years are automatically completed with data from the most recent year for which these data are available. Dataset for each year is saved in a separate CSV file named, for example, **data_2019.csv** for 2019. The CSV files for each year are the appropriate files for the next step, which is MCDA evaluation. 

***Please note:*** 

If certain data is missing for a criterion for a given year, insert manually (Ctrl+C, Ctrl+V) the data for that criterion from the available last year by inserting the selected column in the CSV file. For example, there is no data for C3 for the year 2019, so insert column C3 from the file data_2018.csv in the file data_2019.csv 

2. ***MCDA evaluation following years***. Evaluate the alternatives using **mcda_methods** containing the three MCDA methods TOPSIS, VIKOR and COMET and the supporting methods in additions.py. 
3. ***Calculate rankings correlation***. Calculate the correlations between the rankings provided by each MCDA method using **correlations**, which displays a correlation matrix with Pearson correlation coefficient values. 
4. ***Results visualization***. Visualize country rankings in a nice looking radar chart form using **radar_charts**. 
5. ***DARIA method***. Now you can determine the variability of the criteria and the alternatives' efficiency values and update the last efficiency value with its variability over the years studied. Methods in the **_DARIA class_** provided in the daria file located in the **daria** directory in this repository are indented for performing these procedures. 
6. ***Determination of criteria performance variability***. Determine the values and directions of the variability of the criteria for each country in subsequent years analysed using the Gini coefficient by **variability_criteria** using **_gini** and **_direction_criteria** methods provided by **_DARIA_** class included in **daria** directory. Criteria variability can be determined by the **_gini** method in the same way as the efficiencies variability due to the identical algorithm. However, the **_gini_criteria** method is also included in the DARIA class to better explain its algorithm with the typical determinations for criteria variability. Both methods work the same and produce identical results. 
7. ***Determination of alternatives efficiency variability***. Determine the values and directions of the variability of rankings for each country in subsequent years analysed using the Gini coefficient by **variability_scores** using **_gini** and **_direction** methods provided by **_DARIA_** class included in **daria** directory.
8. ***Updating the last efficiency by its variability***. Get the final overall countries' ranking, taking into account the results of the rankings and their variability over the entire time studied using **final_results** using **_update_efficiency** method provided by **_DARIA_** class included in **daria** directory. 

**_Instructions for launching this software:_**

To use the software, you need to install Python version >= 3.0 by downloading a version suitable for your OS from [Python downloads](https://www.python.org/downloads/) from the Downloads section.
Then install the required Python packages by typing the following commands in the console. For example, if you use **pip**, you can install them as follows:
```
pip install numpy
pip install pandas
pip install matplotlib
pip install scipy
pip install seaborn
```
To run the software, download the repository and run files with extensions .py in your favourite IDE (integrated development environment) or open source code editor, for example [Visual Studio Code](https://code.visualstudio.com/download) with the ability to execute and edit the source code. The authors of this software use the latest version of [Visual Studio Code](https://code.visualstudio.com/download) on Windows and Python 3.8.6 (64-bit).
