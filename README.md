# M0BusinessDataAnalysis_ThiernoB
## Executive summary:
Using Excel and Python, I found out that 3 crops (Corn, rice, wheat) cultivated in different districts in india don't have the same productivity.
After identifing the Productivity index of each crop in its specific district, I made a list that display all the the districts that have at least one crop with a productivity index inferior to 0.5. This leads me to recommand a relocation of the areas cultivated to the best efficient crop in the district.
## Business problem:
Three(3) crops(corn, rice, wheat) are cultivated in the districts of different states in India. The production shows that certain crops are more efficient in terms of productivity than others within the same district . Those performing crops might benefit more area of production in their specific district at the expense of the less efficient ones. What are the target districts that could benefit from a relocation of cultivated areas to maximize local production ?
## Data lifecycle and summarize tasks:
<img width="570" alt="Screenshot 2025-05-07 at 10 52 17 AM" src="https://github.com/user-attachments/assets/e519b0a9-75cd-4f8e-8a11-5fef24ac0720" />

### How does the data lifecycle apply to my business problem:
Since this project is first of all for academic purposes, it is important for me to apply my learning in terms of data lifecycle. Therefore, I followed the cycle above to do my analysis.
#### Business problem:
In Agriculture, especially in crop production, the three fundamentals elements are the plant, the soil and the environment. In this project, I focused on the soil and showcase the importance of managing the area of production. This is crucial in order to optize crop production especially in today's world where we are increasingly whitnessing a decline in agricultural production areas due to a constant increase in the world population. My business problem defined above should help solving this problem in that specific region.
#### Data collection:
I collected data that allign with my business problem. here is the source of my data: "https://www.kaggle.com/datasets/vineetkukreti/indian-agriculture-dataset"
#### Data processing:
I processed the data by cleaning it:
-  1- I retrieved only the information i need : State,district,year,crop,production,area,yield.
*  2- filtered the data by year to have the data from year 2000 to 2017
-  3- displayed the data in a long selection format in a new sheet to unpivot the collunn for an efficient use of the pivot table.
*  4- used a pivot table to have the data based on district(rows). 
-  5- copy the pivot table and paste it as statique data in a new sheet for flexible changes and analysis.
#### Data analysis:
I analysed the data by doing calculations:
-  1- I converted the yield form kg/ha to Tons/ha
*  2- I calculated the total sum of production by district, the sum of area by district and the sum of average yield by district. formulas= sum(production corn,production rice, production wheat)...
-  3- I then calculated the production shared for each crop in the district in percentage. Formula= production crop/production total (%); production rice/ production total (%); same for wheat
*  4- I calculated the area shared for each crop by district. with the same methodoloy for the prooduction (in %)
-  5- I finally calculated the productivity index PI which is the efficiency of a crop. "how good is the production based on its used area". If PI>1,excellent PI, if PI=1, good PI, if PI<1, poor PI. The formula is: prouction shared/area shared. In this study, I targeted the districts with very poor PI, which is why i set my comparison to 0.5
    In this section , since some values of the area shared(%) is very low,close to 0.00%, it means it has an insignificant shared area. Therefore, I used a formula to return 1 whenever the denominator (shared area % ) is 0 to avoid #div/0 error. final formula= If(area<>0,production/area,1).
*  6- I opened excel file with the pandas library and opened the sheet called final data.
-  7- with pandas python i was able to find the districts that I targeted(comments in python.ipynb). I especially used a function that I called filter_low_PI, which returned me all the districts with at least one crop having a productivity index lower than 0.5.
  <img width="1155" alt="Screenshot 2025-05-20 at 3 40 57 PM" src="https://github.com/user-attachments/assets/1bf13fb6-44c7-4211-9ad3-b6618b7e6491" />
 In summary, I first found the PI of each crop in each district using excel; then with python, I filtered the data to have only my targeted districts that respond to my criteria: PI<0,05.

#### Data presentation:
in this section, I used the plot() function in pandas to display an horizontal bar chart in order to show the inequality of the crop efficiencies for a sample of my targeted districts.

<img width="1153" alt="Screenshot 2025-05-20 at 3 55 20 PM" src="https://github.com/user-attachments/assets/65afa3f4-e925-4861-ae49-59e46a9958d5" />

<img width="654" alt="Screenshot 2025-05-07 at 2 57 44 PM" src="https://github.com/user-attachments/assets/e93cd5dd-2ba4-403c-a991-72f50f1b3ecc" />

This bar plot is a good example of a data presentation as it shows the inequality of the productivity index of crops in a district.
we can have a story around it and make suggestions to maximize the local production.


## Data type:
My dataset contains mostly numeric quantitative data as it's all about production in tons , yield in tons/ha or area in ha.
The type is also continuous as we can take it as a range.

## Conclusion:
As I went through this analysis, I recommend using the district target and find the best combination corn rice wheat in these regions in order to optimize the uses of the areas and improve the total production.
This analysis using only the production might not give an efficient result because the 3 crops can't have the same weight in the exact same area of production. so their yield are not comparable.The best thing to do would be to use a new parameter <price> as comparison. the revenue generated by the yield would be a better parameter to calculate the productivity index.

