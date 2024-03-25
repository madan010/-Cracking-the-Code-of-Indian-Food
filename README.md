# Cracking the Code of Indian Food

This project aims to analyze the nutritional content of 528 key Indian foods using the IFCT (Indian Food Composition Tables) data. By uncovering hidden gems within these foods, to gain insights into their health benefits and cultural significance.

Indian cuisine is incredibly diverse, influenced by regional variations, social practices, and cultural norms. Understanding the nutritional aspects of these foods can help us make informed dietary choices and appreciate the richness of Indian culinary traditions.

The Data: 
===
The IFCT 2017 dataset, published by the National Institute of Nutrition in Hyderabad, provides detailed nutritional information for 528 essential Indian foods. It covers 151 nutrients, including bioactive compounds.

The [IFCT data](https://vikaspedia.in/health/nutrition/nutritive-value-of-foods/indian-food-composition-tables).
The Indian Food Composition Tables, 2017 provides nutritional information on 151 discrete food components for 528 key foods.

# Summary of Data Cleaning.
- Orignal Data Shape : 542 Rows x 421 columns
- Selected only the major Nutrients for data analysis - data Shape After (542 Rows x 16 Columns)
- Cleaning Column Names(removed ";" from the column names; Using `.str.split` & method chaining to select the dezired column name.
- Renamed the Columns - Using `.rename` method.
- Check for Null values in cell. `.isnull().sum()`
- Simplified the 4 food types to 2 food types (Veg & Non Veg) by creatig **dictionary** and using `replace` method to assign food type to the respective categoriy according to the dictionary.
-  Simplified Food Name Column by Creating new Column "Food Description" from Food Name column using `str.split()`
- Renamed cereals & Millets as either Cereals or Milltes next to respective food name to impove the data analysis by creating cereal dictionary and millets dictonary and replacing the food group respectively using `np.where` & `isin()` Methods.
# Summary of Data Analysis.
## Summarizing the data- no. of food in each group
- ![No of Food](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Distribution%20of%20Food%20Groups.png)
- The IFCT has more than 90 Fish varieties nutritional data. The foods have been divided to 19 food groups.
- I used the `value_counts()` method to get the count in each food group. I then chained the `plot()` method to visualize the distribution. I passed `‘bar’` to the `kind` parameter to create a bar chart.
- ## Summerizing Nutritional Data.
-  ![Nutritional Data](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Average_Nutrient_Content_in_Different_Food_Groups1.png)
- The chart clearly illustrates that animal-based diets are abundant in proteins and fats, while plant-based diets predominantly consist of carbohydrates. Furthermore, it underscores the versatility of plant-based foods in terms of their nutritional composition.  
