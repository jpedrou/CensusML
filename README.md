# Purpose Of This Work
- Choose a database and apply the steps of a Machine Learning Project. My problem is for: **Classification**.

- Propose 4 solutions to the problem and at the end inform the most efficient one:
  - a) Choose a Machine Learning model and apply it without use feature selection or dimensionality reduction. Simply apply the model and find the value of R2(for Regression) or 
    Accuracy (for Classification).
  - b) Use the PCA or LDA technique for dimensionality reduction and apply the Same Machine Learning model used in letter a.
  - c) Use a Feature Selection technique and apply the same Machine Learning model used in the letter a.
  - d) Use the Pycaret library to solve the problem.
    
 **OBS: If you are seeing the code here in GitHub some graphics may not be displayed, because some ones are dynamic. You can open it in the Google Colab.**
# Exploratory Data Analysis (EDA)
## Data 
It's a Extraction from the 1994 Census database wich was done by Barry Becker.
For more data details check this link: https://archive.ics.uci.edu/ml/datasets/adult

> The **goal** is predict whether income exceeds $50K/yr based on census data. Also known as "Census Income" dataset.

> The metric chose to evaluate the models performance was **Accuracy**

Some analyzes were made to verify inconsistent data, missing data and graphical visualizations to understand and discover what were the relationships between the attributes, so that it would be possible to choose a model that could be satisfactory for the case. All of this analyzes can be checked in the project file.
# Model Choice
After making the EDA I opted for the DecisionTreClassifier Model, because as the data is big this model can be more specific and more accurate than the probably table models, rule models and maybe more accurate than the instanced-based ones. Basicaly, the model I chose works making, as the name suggers, a Decision Tree, where it will find the best correlations betwwens the more important attributes. I't would be a good choice too the RandomForestClassifier, wich is a DecisionTree model updated.

![decision](https://github.com/jpedrou/CensusML/assets/127536464/3ad4bcaf-068c-4eb2-b232-d746845b615a)

**Decision Tree example.**

# Experiments
## 1° Default DecisionTreeClassifier
- Default Model
- Without find the best parameters
- No Scaling
  
I used this model like this to see how good it would be without looking for the best parameters and had a regular Accuracy result **(0.8082)**.

## 2° DecisionTreeClassifier With Dimensionality Reduction Technique
- LDA; totally dependent of the class(es)

As I used LabelEncoder and OneHotEncoder to transform categorical features into numeric ones, the data got too many columns. For that, I thought that using LDA ( dimension reduction technique), which often has better results than PCA would be a good method. But, as my meta class only had two features LDA greatly reducted the data, wich can caused some correlations lost. For that, the Accuracy was not so good **(0.7836)**. 
