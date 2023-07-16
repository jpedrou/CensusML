# <img width="48" height="48" src="https://img.icons8.com/color/48/goal--v1.png" alt="goal--v1"/> Purpose Of This Work 
- Choose a database and apply the steps of a Machine Learning Project. My problem is for: **Classification**.

- Propose 4 solutions to the problem and at the end inform the most efficient one:
  - [x] a) Choose a Machine Learning model and apply it without use feature selection or dimensionality reduction. Simply apply the model and find the value of R2(for Regression) or 
    Accuracy (for Classification).
  - [x] b) Use the PCA or LDA technique for dimensionality reduction and apply the Same Machine Learning model used in letter a.
  - [x] c) Use a Feature Selection technique and apply the same Machine Learning model used in the letter a.
  - [x] d) Use the Pycaret library to solve the problem.

## Tools
<img width="48" height="48" src="https://img.icons8.com/color/48/python--v1.png" alt="python--v1"/> <img width="48" height="48" src="https://img.icons8.com/color/48/google-colab.png" alt="google-colab"/>

## OBS
**If you are seeing the code here in GitHub some graphics may not be displayed, because some ones are dynamic. You can open it in the Google Colab.**
 
## Exploratory Data Analysis (EDA)
### Data 
It's a Extraction from the 1994 Census database wich was done by Barry Becker.
**For more data details click [here](https://archive.ics.uci.edu/ml/datasets/adult)**.

> The **goal** is predict whether income exceeds $50K/yr based on census data. Also known as "Census Income" dataset.

> The metric chose to evaluate the models performance was **Accuracy**

Some analyzes were made to verify inconsistent data, missing data and graphical visualizations to understand and discover what were the relationships between the attributes, so that it would be possible to choose a model that could be satisfactory for the case. All of this analyzes can be checked in the project file.
## Model Choice
After doing the EDA I opted for the DecisionTreClassifier Model, because as the data is large this model can be more specific and more accurate than the probably table models, rule models and maybe more accurate than the instanced-based ones. Basically, the model I chose works by making, as the name suggests, a Decision Tree, where it will find the best correlations between the most important attributes. Also a good choice would be the RandomForestClassifier, wich is an updated DecisionTree model.

![decision](https://github.com/jpedrou/CensusML/assets/127536464/3ad4bcaf-068c-4eb2-b232-d746845b615a)

**Decision Tree example.**

## Experiments
### 1° Default DecisionTreeClassifier
- Default Model
- Without find the best parameters
- No Scaling
  
I used this model like this to see how good it would be without looking for the best parameters and had a regular Accuracy result **(0.8082)**.

### 2° DecisionTreeClassifier With Dimensionality Reduction Technique
- LDA; totally dependent of the class(es)

As I used LabelEncoder and OneHotEncoder to transform categorical features into numeric ones, the data got too many columns. For that, I thought that using LDA ( dimension reduction technique), which often has better results than PCA would be a good method. But, as my meta class only had two features LDA greatly reducted the data, wich can caused some correlations lost. For that, the Accuracy was not so good **(0.7836)**. 


### 3° DecisionTreeClassifier With Features Selection
- Low Variance
  
In this experience I tried to improve the model selecting the best attributes using the **Low Variance** method. It removes all features whose variance doesn’t meet some threshold. By default, it removes all zero-variance features, i.e. features that have the same value in all samples. At this point, I've got a good Accuracy **(0.8157)**.

### 4° Using Pycaret
- CatBoostClassifier <img align='right' width=340 src='https://github.com/jpedrou/CensusML/assets/127536464/4a0e380d-1579-406c-8063-3360d81a4686'>

It's a powerfull Python AutoML library, which is very used to find the base model to not lose much time finding manually the ideal model. I just passed the default parameters and already had an awesome result **(0.8746)**.

**If you want to see more of the library click [here](https://pycaret.org/).**

## <img width="28" height="28" src="https://img.icons8.com/color/48/goodnotes.png" alt="goodnotes"/> Conclusion 
The best model was with pycaret library, just with the default configs:
- **CatBoostClassifier (0.8746)**

CatBoost is one of the most powerfull classification models in this moment, basically it have the same learning principles of DecisionTree, but with new updates and parameters. It is a recent model.
