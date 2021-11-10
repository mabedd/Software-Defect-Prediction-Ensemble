<img src='https://d3v77cxrhim28u.cloudfront.net/wp-content/uploads/2018/11/bg_img_1.png'>

# Software Defect Prediction using Ensemble Learning on Selected Features
<h2><strong><italic>Research Paper Implementation</italic></strong></h2>
A comprehensive implementation of the paper <a href='https://www.sciencedirect.com/science/article/abs/pii/S0950584914001591'>Software defect prediction using ensemble learning on selected features.</a>

The paper was presented by <strong><a href='https://www.linkedin.com/in/dr-lahouari-ghouti/'>Dr.Lahouari Ghouti</a></strong> at Prince Sultan Univserity in the Software Analytics course (SE480).

The implementation was benchmarked on the <a href='https://figshare.com/articles/dataset/Software_Defect_Prediction_Dataset/13536506/1'>Ant 1.7</a> public dataset for software metrics. According to the paper this particular dataset achieved the highest performance with the proposed APE.

# Table of contents
- [Software Defect Prediction using Ensemble Learning on Selected Features](#software-defect-prediction-using-ensemble-learning-on-selected-features)
- [Table of contents](#table-of-contents)
- [Approach](#approach)
  - [Used Models](#used-models)
  - [Feature Selection](#feature-selection)
    - [Sequential Forward Selection](#sequential-forward-selection)
  - [Training Pipeline](#training-pipeline)
  - [Solve Class Imbalance](#solve-class-imbalance)
  - [Individual Results](#individual-results)
  - [Average Probability Estimator](#average-probability-estimator)
- [Ensembles Comparison](#ensembles-comparison)
- [Contribute](#contribute)

<a id="approach"></a>
# Approach

The approach for this implementation was to follow mostly all research paper details in order to come up with a comprehensive implementation for the paper covering almost all aspects such as Feature Selection, Stratified K Fold CV, and other presented techniques.

The paper presented an AI system that helps in Software Defect Prediction by applying <strong><em>Heterogeneous Ensemble</em></strong>.
<img src='https://d3i71xaburhd42.cloudfront.net/e2600cbc04da3284b61ef72223403f1dca3d2a98/3-Figure1-1.png'></img>

Heterogeneous Ensemble is a ML technique in which several models trained on the same dataset. These models can differ in the learning algorithm, hyperparameters, or could be the same. After training the <strong>Voting Classifier</strong> will contain all trained models in order to apply voting.

The voting was done based on models weights which is <strong>Weighted Average Ensemble</strong> which means that models that have more weights on the data will eventually be involved more in the voting.

<a id="used-models"></a>
## Used Models
The paper proposed using 7 models for building the voting system. As the paper states 7 was the optimal number of models for this solution as using more models will negatively impact the performance. Also, to avoid voting conflicts, the number of used models should be odd number to avoid conflicts situations.

The used models were the following:

```sh
SVC(probability=True)
MultinomialNB()
BernoulliNB()
RandomForestClassifier()
GradientBoostingClassifier()
SGDClassifier(loss='log')
LogisticRegression()
```

Several <strong>Hyperparameters</strong> tuning was done using <code>GridSearchCV</code> to achieve the best performing model with the corresponding <strong>Hyperparameters</strong>.

<a id="feature-selection"></a>
## Feature Selection
As the paper title states, Feature Selection was done to increase preformance and get rid of unnecessary features. The paper comapred between different selection approaches such as Fisher, Chi, and Greedy. Based on the results Greedy method reported the best results and showed that a very few number of feautres contributes to the output. 

For applying Feature Selection, the following implementation used <code>MLXTEND</code> library which comes with ready made functions for applying several Feature Selection approaches depending on the use case.

<a id="sequential-forward-selection"></a>
### Sequential Forward Selection
The following is an example of the <strong>Sequential Forward Selection</strong> that was applied taken from <code>MLXTEND</code> <a href='http://rasbt.github.io/mlxtend/user_guide/feature_selection/SequentialFeatureSelector/'>documentation</a>.
```sh
from mlxtend.feature_selection import SequentialFeatureSelector as SFS

sfs1 = SFS(knn, 
           k_features=3, 
           forward=True, 
           floating=False, 
           verbose=2,
           scoring='accuracy',
           cv=0)

sfs1 = sfs1.fit(X, y)
```
<a id='training-pipeline'></a>
## Training Pipeline
In order to make things easier and reusable, the implementation built a training pipeline for each classifier putting the processing and tuning steps in that pipeline. 
The pipeline consisted of:
* Feature Selection
* Feature Scaling
* Training

After that the pipeline was inserted into a <code>GridSearchCV</code> for applying <strong>Hyperparameters Tuning</strong>

```sh
  # Data will be scaled with Standard Scaler first
  scaler = StandardScaler()

  # Feature selection will be applied with 10 - 15 features
  sfs = SFS(estimator=LogisticRegression(max_iter = 3500), 
            k_features=10,
            forward=True, 
            floating=False, 
            scoring='accuracy',
            cv=2)

  # Logisitc Regression classifier is trained
  clf = LogisticRegression()
```
```sh
  steps = [
      ('sfs', sfs), 
      ('scaler', scaler), 
      ('clf', clf)
  ]

  pipeline = Pipeline(steps)

  # Hyperparameters for GridSearch CV

  param_range_fl = [1.0, 0.5]

  grid_params_lr = [{
          'clf__penalty': ['l1', 'l2'],
          'clf__C': param_range_fl,
          'clf__solver': ['liblinear'],
          'sfs__k_features': [10, 15]
  }] 
```
<a id='solve-class-imbalance'></a>
## Solve Class Imbalance
One of the main problems that was presented in this dataset was that there is a huge visible class imbalance in the dataset. The difference between the two classes was more than 80% which will eventually cause a huge overfitting for the models regardless of the used algorithm.

There are mainly two solutions presented for this issue. Both solutions were tested and one of them overcomed the other.
  * <strong>Synthetic Minority Oversampling Technique (SMOTE)</strong>
    
    This technique works by applying data resampling. Either by generating synthetic data for the underwhelming class <code>Oversampling</code> or discarding some records from the overwhelming class <code>Undersampling</code>. This technique resulted in a significant improvement in modles performance but there was a much better solution.

  * <strong>Stratified K Fold Cross Validation</strong>

    Implementing the concept of stratified sampling in cross-validation ensures the training and test sets have the same proportion of the feature of interest as in the original dataset. Doing this with the target variable ensures that the cross-validation result is a close approximation of generalization error. This technique resulted in a better performance and discarded the need of either creating synthetic data or removing data. 

<a class='individual-results'></a>    
## Individual Results
Before creating the <code>(Average Probability Estimator) APE</code> voting system, each model was trained in previous individually and saved.
The following table summerizes each model performance metrics:
<center>
  <table>
    <tr>
      <th>Model</th>
      <th>Overall Test Accuracy</th>
    </tr>
    <tr>
      <td>Logisitc Regression</td>
      <td>%82.66</td>
    </tr>
    <tr>
      <td>Bernouli Naive Bayes</td>
      <td>%77.70</td>
    </tr>
    <tr>
      <td>Gradient Boost</td>
      <td>%82.35</td>
    </tr>
      <tr>
      <td>Multinomial Naive Bayes</td>
      <td>%77.98</td>
    </tr>
      <tr>
      <td>Random Forest</td>
      <td>%80.66</td>
    </tr>
      <tr>
      <td>Stochastic Gradient Descent</td>
      <td>%82.41</td>
    </tr>
      <tr>
      <td>Support Vector Machines - SVC</td>
      <td>%81.20</td>
    </tr>
  </table>
</center>

<a class='average-probability-estimator'></a>    
## Average Probability Estimator
The weighted voting method assigns various weights to the classifiers based on specific criteria and takes a vote of the classifiers based on the weight. In this work, the weight of each classifier would be chosen based on the performance accuracy of the classifier based on the testing set. 

A weighted ensemble is an extension of a model averaging ensemble where the contribution of each member to the final prediction is weighted by the performance of the model.

First all models were loaded and evaluated on the Test set in order to get their weights and apply the <strong>Weighted Ensemble</strong> based on them.
```sh
  # load models with pickle
  bnb = pickle.load(open('models/bnb.sav', 'rb'))
  gb = pickle.load(open('models/gb.sav', 'rb'))
  lr = pickle.load(open('models/lr.sav', 'rb'))
  mnb = pickle.load(open('models/mnb.sav', 'rb'))
  rf = pickle.load(open('models/rf.sav', 'rb'))
  svc = pickle.load(open('models/svc.sav', 'rb'))
  sgd = pickle.load(open('models/sgd.sav', 'rb'))

  # dump them into a list
  def get_models():
      models = list()
      
      models.append(('bnb', bnb))
      models.append(('gb', gb))
      models.append(('lr', lr))
      models.append(('mnb', mnb))
      models.append(('rf', rf))
      models.append(('sgd', sgd))
      models.append(('svc', svc))
      
      return models
```
```sh
  # evaluate each base model
  def evaluate_models(models, X_test, y_test):
      # fit and evaluate the models
      scores = list()
      for name, model in models:
          # predict the test set
          yhat = model.predict(X_test)
          # find the accuracy
          acc = accuracy_score(y_test, yhat)
          # store the performance
          scores.append(acc)
          # report model performance
      return scores

  # get models
  models = get_models()

  # get models weights
  scores = evaluate_models(models, X_test, y_test)
```
The <code>scores</code> variable contains all models performance on the test set which will play a key part in the voting later on.

After that <code>VotingClassifier</code> was implemented which estimators were the trained models previously and weights were the scores evaluated previously as well.

```sh
from sklearn.ensemble import VotingClassifier

ensemble = VotingClassifier(estimators = models, voting = 'soft', weights = scores)
```

<a id='ensemble-comparison'></a>
# Ensembles Comparison

The aim of this paper was to develop an AI system that helps in Software Defect Prediction by applying advanced techniques in order to come up with the best performance. The paper also compared between several ensemble models which are <code>W-SVM</code> and <code>RandomForest</code>. 
<center>
  <table>
    <tr>
      <th>Ensemble Model</th>
      <th>Test Accuracy</th>
    </tr>
    <tr>
      <td>APE (proposed)</td>
      <td>%82.81</td>
    </tr>
    <tr>
      <td>Random Forest</td>
      <td>%81.20</td>
    </tr>
    <tr>
      <td>Weighted Support Vector Machines</td>
      <td>%72.89</td>
    </tr>
  </table>
</center>

<a id='contribute'></a>
# Contribute
The paper was presented by <strong><a href='https://www.linkedin.com/in/dr-lahouari-ghouti/'>Dr. Lahouari Ghouti</a></strong> Associate Professor in Computer Science at Prince Sultan University. Dr. Lahouari presented the paper to his students in the course Software Analytics (SE480) and the paper was implemented by one of his students <strong><a href='https://www.linkedin.com/in/mohammed-abed-itil%C2%AE-b9a60186/'>Mohammed Abed</a></strong> later on.
 