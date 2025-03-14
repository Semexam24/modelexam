# modelexam

#1
Define a function to calculate EMI using the given formula for a loan amount.
SOLUTION:
Define Function: 
      def calculate _emi(amount, duration, rate, down_payment =0); 
try:  
      n = duration *12 
      r = rate /(12*100) 
      loan_amount = amount – down_payment 
      emi=loan_amount *r* ((1 + r)**n/((1 +r)**n-1)) 
      return emi 
except: 
      print(“Error: Please check your input values.”) 
Assign Values: 
      emi = calculate_emi(amount=100000, duration=5,rate=8)  
Print Values: 
      print(“EMI:”,emi);


#2
Give 2 Working Example for the following functions.  
function1 = np.append 
function2 = np.average 
SOLUTION:
Library: 
      import numpy as np 
Define Function: 
      new_arr = np.append(arr, 4) 
      avg = np.average(arr)  
Assign Values: 
      arr = np.array([1, 2, 3]) 
      arr = np.array([10, 20, 30, 40])  
Print Values: 
      print(new_arr)   
      print(avg)

      
#3
Demonstrate dot function using *, sum and np.dot () with an example. 
SOLUTION 
Library: 
      import numpy as np 
Define Function: 
      dot_product_1 = sum(A * B) 
      dot_product_2 = np.sum(A * B) 
      dot_product_3 = np.dot(A, B) 
Assign Values: 
       A = np.array([1, 2, 3]) 
       B = np.array([4, 5, 6]) 
Print Values: 
      print(dot_product_1) 
      print(dot_product_2) 
      print(dot_product_3)


#4
Use ‘italy-covid-daywise.csv ' data set for the following Questions:
4a: What are the total number of reported cases and deaths related to Covid-19 in Italy? 
SOLUTION:
import pandas as pd 
covid_df = pd.read_csv('D:/python basic 1/italy-covid-daywise.csv') 
total_cases = covid_df['new_cases'].sum() 
total_deaths = covid_df['new_deaths'].sum() 
print("Total reported cases:", total_cases) 
print("Total reported deaths:", total_deaths) 
 
4b: What is the overall death rate (ratio of reported deaths to reported cases)? 
SOLUTION: 
death_rate = total_deaths/total_cases 
print("Overall death rate:", death_rate) 
 
4c: What is the overall number of tests conducted? A total of 935310 tests were conducted 
before daily test numbers were reported. 
SOLUTION: 
initial_tests = 935310 
total_tests = initial_tests + covid_df.new_tests.sum() 
total_tests 

4d: convert the date from object datatype to date and include day, month, weekday and year as separate field
SOLUTION: 
covid_df['date'] = pd.to_datetime(covid_df['date']) 
covid_df['Day'] = covid_df["date"].dt.day 
covid_df["Month"] = covid_df['date'].dt.month 
covid_df['Weekday'] = covid_df['date'].dt.weekday 
covid_df['Year'] = covid_df['date'].dt.year 
print(covid_df[['date', 'Day', 'Month', 'Weekday', 'Year']].head()) 
 
4e: Find month wise case & death count 
SOLUTION: 
month_wise_cases = covid_df.groupby(['Month'])['new_cases'].sum() 
month_wise_deaths = covid_df.groupby(['Month'])['new_deaths'].sum() 
print("Month wise case count:\n", month_wise_cases) 
print("Month wise death count:\n", month_wise_deaths)


#5
Use ‘countries.csv&#39; data set for the following Questions 
5a: How many countries does the data frame contain? 
SOLUTION: 
countries_df = pd.read_csv('countries.csv') 
countries_df.shape[0] 
 
5b: How many continents does the data frame contain 
SOLUTION: 
countries_df['continent'].unique() 
 
5c: What is the total population of all the countries listed in this dataset? 
SOLUTION: 
total_population = countries_df['population'].sum() 
print('The total population is {:,}'.format(int(total_population))) 
 
5d: What is the overall life expectancy across in the world? 
SOLUTION: 
overall_life = countries_df["life_expectancy"].mean() 
print("The overall average life expectancy is:", overall_life) 
 
5e: Create a data frame containing 10 countries with the highest population. 
SOLUTION: 
most_populous_df 
countries_df.sort_values('population'.ascending False) 
most_populous_df.head(10) 
 
5f: Add a new column in countries_df to record the overall GDP per country (product of population &amp; per capita GDP). 
SOLUTION: 
countries_df['gdp'] = countries_df["po; ulation"]/countries_df["gdp_per_capita"] 
countries_df['gdp']


#6
Perform the following using covid-countries-data.csv 
Count the number of countries for which the total_tests data is missing. 
SOLUTION: 
covid_data_df = pd.read_csv('covid-countries-data.csv') 
total_tests_missing = covid_data_df['total_tests'].isna().sum() 
print("The data for total tests is missing for {} countries.".format(int(total_tests_missing)))


#7
Merge the two data frames ‘countries.csv' & covid-countries-data.csv named combined_df, and perform the following 
7a: Add columns tests_per_million, cases_per_million, deaths_per_million into combined_df. 
SOLUTION: 
combined_df=countries_df.merge(covid_data_df, on='location', how='inner') 
print(combined_df.head())combined_df['tests_per_million'] = combined_df['total_tests'] * 1e6 
/ combined_df['population'] 
combined_df['cases_per_million']=combined_df['total_cases']*1e6/ 
combined_df['population'] 
combined_df['deaths_per_million']=combined_df['total_deaths']*1e6/ 
combined_df['population'] 
combined_df 
 
7b: Create a dataframe with 10 countires that have highest number of tests per million people. 
SOLUTION: 
highest_tests_df " 
combined_df.sort_values('tests_per_million ascending False) head(10) 
highest_tests_df 
 
7c: Create a dataframe with 10 countires that have highest number of positive cases per million people. 
SOLUTION: 
highest_cases_df= 
combined_df.sort_values('cases_per_million'.ascending=False).head(10) 
highest_cases_df 
                  
7d: Create a dataframe with 10 countires that have highest number of deaths cases per million people? 
SOLUTION: 
highest_cases_df=combined_df.sort_values('deaths_per_million',ascending=False). 
head(10) 
highest cases df 
    
7e: Count number of countries that feature in both the lists of "highest number of tests per million" and "highest number of cases per million". 
SOLUTION:
merged_df pd.merge(highest_tests_df, highest_cases_df. on 'location') 
num_countries merged_df['location'].nunique() 
print("Number of countries that feature in both lists:", num_countries)


#8
Merge the two data frames ‘countries.csv’ & covid-countries-data.csv named combined_df, and find the result of following. 
Count number of countries that feature in both the lists "20 countries with lowest GDP per capita" and "20 countries with the lowest number of hospital beds per thousand 
population". Only consider countries with a population higher than 10 million while creating the list. 
SOLUTION: 
population = set(countries_df.location[countries_df['population']>10000000]) 
lowest_gdp_set = set((countries_df.sort_values('gdp_per_capita', 
ascending=True).head(20)).location) 
lowest_gdp_set


#9
Plot Line chart with following characteristics Line Style dotted and Line-color should be red X label name = x,  Y label name = y 
Add title as Example plot Add a circle marker. Line marker color as red Line width should be 3 
SOLUTION: 
x = [1, 2, 3, 4, 5] 
y = [1.5, 4, 7, 4, 2]  # Ensure y has the same length as x 
plt.plot(x, label="x", linestyle='-', marker='o', color='b', linewidth=2) 
plt.plot(x, y, 'o--r', linewidth=3, markersize=8, label="y") 
plt.xlabel('X') 
plt.ylabel('Y') 
plt.title("Sample Plot") 
plt.legend() 
plt.show()


#10
Use a proper plot to know the relationship between the variables sepal_length and petal_length according to the spices from the iris data. Comment on your result. 
SOLUTION: 
flowers_df = sns.load_dataset("iris") 
sns.scatterplot(x=flowers_df.petal_length,  
y=flowers_df.sepal_length,  
hue=flowers_df.species); 


#11
Visualizing the multidimensional relationships among the variable in a dataset "tips" according to the variable "time" 
SOLUTION: 
tips_df = sns.load_dataset("tips"); 
sns.pairplot(tips_df, hue='time');


#12
Write code to produce the below plot (Hint: Use sns.relplot) 
SOLUTION:
tips_df = sns.load_dataset('tips')  # If using built-in Seaborn dataset 
sns.relplot(x='total_bill', y='tip', hue='day', data=tips_df) 
plt.show()


#13
Produce the plot below with your code by using the dataset named 'titanic' which is available in Seaborn dataset, 
Include Legend,  Set ci parameter as 99 
SOLUTION: 
titanic = sns.load_dataset('titanic') 
sns.barplot(x='sex', y='survived', hue='class', data=titanic, ci=95) 
Show the plot 
plt.show()
