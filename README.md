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
- Cleaning Column Names(removed ";" from the column names; Using `.str.split` & method chaining `str[0]` to select the name occuring before ";".
- Renamed the Columns - Using `.rename` method.
- Check for Null values in cell. `.isnull().sum()`
- Simplified the 4 food types to 2 food types (Veg & Non Veg) by creatig **dictionary** and using `replace` method to assign food type to the respective categoriy according to the dictionary.
-  Simplified Food Name Column by Creating new Column "Food Description" from Food Name column using `str.split()`
- Renamed cereals & Millets as either Cereals or Milltes next to respective food name to impove the data analysis by creating cereal dictionary and millets dictonary and replacing the food group respectively using `np.where` & `isin()` Methods.
# Summary of Data Analysis.
## Summarizing the data- no. of food in each group
- ![No of Food](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Distribution%20of%20Food%20Groups.png)
- The IFCT has more than 90 Fish varieties nutritional data. The foods have been divided to 19 food groups.
> Here I used the `value_counts()` method to get the count in each food group. I then chained the `plot()` method to visualize the distribution. I passed `‘bar’` to the `kind` parameter to create a bar chart.
- ## Summerizing Nutritional Data.
-  ![Nutritional Data](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Average_Nutrient_Content_in_Different_Food_Groups3.png)
- The chart clearly illustrates that moisture makes most of the food. Animal-based diets are abundant in proteins and fats, while plant-based diets predominantly consist of carbohydrates and Dietry Fiber.
> this was done by creating a subset of the dataframe, grouped it by food categories, and calculated the mean of the nutritional components.
> I generated a stacked bar chart by setting the kind parameter to `bar` and the `stacked` parameter to `True`.
# Calories
## Food with most calories
- ![calories](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/high_calories.png)
- Walnut is the most calorie per 100g . Nuts are rich in energy followed by condiments. Chicken is the only animal based food in the list of top foods with highest energy.
> A subset of the data was created and sorted in descending order using `sort_values` and setting `ascending` parameter as `False`. This data was then used to plot a chart using the Seaborn library’s `sns.barplot` function, with the `hue` parameter set to represent different food groups.
- ![food group_calories](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Calories_foodsgroups.png)
- Nuts & oil Seeds, Millets, Cereals & legumes are rich source of energy.
> subset of the data was created using the `groupby` function, and the data from this subset was then visualized using the `plot` function.
# Moisture Content
- ![moisture_food_group](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/moisture_food_group1.png)
- Coconut water and toddy are the foods in miscellenaous food group.
- Apart from it vegetables are rich source of moisture followed by marine animal, Cereals , legumes and Nuts have lowest moisture content.
> A subset of the data was created using the `groupby` function, and the data from this subset was then visualized using the `sns.barplot` function. The mean moisture content was identified using the `mean()` function.
> A refrence line for mean moisture content of food was plotted using `plt.axvline`, and it was labeled using `plt.text`. Parameters for the location of the line, text location, and text contents were passed into these functions.
# Relationship between Energy and Moisture Content.
- ![energy_moisture](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Energy_moisture_scatter.png)
- On plotting a scatterplot between energy and moisture content we see that foods with high moisture content tend to have lower energy density than foods with low moisture content.
- We caninfer from it is that someone looking to lose weight might opt for foods with higher moisture content and lower energy density to feel full without consuming too many calories.
> Scatter plot using `sns.scatterplot` with `hue` paramater set to food groups.
> plotted Regression line in the plot using `sns.regplot`,  setting `scatter` parameter as `False`.
# Relationship between Energy and Protein.
- ![proein& Energy](https://github.com/madan010/-Cracking-the-Code-of-Indian-Food/blob/main/Energy_protein_scatter.png)
- The scatter plot above reveals that foods such as nuts, fruits, vegetables, millets, and pulses fall below the trend line. Conversely, animal-based foods like eggs, milk, and meat, with the exception of cereals, are positioned above the trend line.
- From the scatter plot, we can deduce that to obtain protein from foods situated above the trend line, one would need to consume a higher number of calories. On the other hand, foods located below the trend line offer a higher protein content with relatively fewer calories.
> Scatter plot using `sns.scatterplot` with `hue` paramater set to food groups.
> plotted Regression line in the plot using `sns.regplot`,  setting `scatter` parameter as `False`.
