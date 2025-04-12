# hw01ml
# პროექტის სახელი

House Prices - Advanced Regression Techniques (Kaggle Competition)

# პროექტის მიმოხილვა

პროექტის მიზანია, შეძლოს სახლების ფასების პროგნოზირება ისეთ მონაცემებზე დაყრდნობით, როგორებიცაა: სახლის ფართობი, ოთახების რაოდენობა, რომელ წელს იყო აშენებული, რამდენად ხარისხიანი ექსტერიერი აქვს და ა.შ. ამ ინფორმაციის გამოყენებით უნდა შევძლოთ, რომ პროგნოზი გავაკეთოთ უნახავ მონაცემებზე და რაც შეიძლება უკეთ გამოვიცნოთ სახლების ფასები. 

## პრობლემის გადასაჭრელად გამოვიყენებ შემდეგ მიდგომებს:

◌ Feature Engineering: NaN ტიპის მნიშვნელობები შევცვალე იმის მიხედვით, თუ რა ტიპის კატეგორია იყო, numerical თუ categorical. 

◌ Model Training: დავტესტე რამდენიმე მოდელი - Linear Regression, Ridge, Random Forest და XGBoost.

◌ HyperParameter Tuning: GridSearchCV გამოვიყენე ყველა მოდელისთვის და გავაუმჯობესე RMSE-ს დახმარებით. 

◌ შეფასება: საბოლოოდ მოდელების მუშაობა შევაფასე RMSE-ზე დაყრდნობით, თუმცა ასევე დავაბეჭდინე ინფორმაცია MAE (Mean Absolute Error)-სა და R² (Coefficient of Determination)-ის შესახებ.

# რეპოზიტორიის სტრუქტურა

◌ model_experiment.csv - ხდეbა მონაცემების დამუშავება, შემდეგი მათი დატრენინგება და საბოლოოდ დალოგვა MLflow-ზე. 

◌ model_inference.csv -  ხდება MLflow-ზე დალოგილი მოდელის ჩამოტვირთვა და მისი მეშვეობით პროგნოზირება სატესტო მონაცემებზე.


# Feature Engineering

##კატეგორიული ცვლადების რიცხვითში გადაყვანა:

Categorical ცვლადების შეცვლა: ენკოდირებულ იქნა OneHotEncoder-ის საშუალებით.

ცარიელი მნიშვნელობების შეცვლა: ისინი, რომლებიც ეკუთვნოდა Numerical ტიპის სვეტებს, შევცვალე მათი საშუალოთი, ხოლო Categorical ტიპის - სვეტში ყველაზე ხშირი 
მნიშვნელობით.

Scaling: Numerical ტიპის ინფორმაციები სტანდარტიზებულ იქნა StandardScaler-ის საშუალებით, რათა დაგვეყვანა საერთო scale-ზე.

##Nan მნიშვნელობების დამუშავება:
 
მონაცემები გავასუფთავე იმ სვეტებისგან, რომლებიც დიდი რაოდენობით შეიცავდნენ NaN მნიშვნელობებს(>30%).

##Cleaning Methods

შევქმენი კლასი DropHighNanColumns, რომელიც შლიდა ისეთ სვეტებს, სადაც NaN მნიშვნელობები იყო 30%-ზე მეტი.

# Feature Selection

Preprocessing-ის დროს ამოირჩა ყველაზე მნიშვნვნელოვანი სვეტები, ხოლო ყველაზე უმნიშვნელო, მაგალითად, როგორიც არის "Id" თავიდანვე წავშალე.

#Training
მოდელები იყო დატრენინგებული მოცემულ ტრეინინგ დატასეტზე, სადაც ვიყენებდი ფაიფლაინს, რომელიც შეიცავდა preprocessing-ს, feature engineering-სა და model training-ს.
##გამოვიყენე შემდეგი მოდელები:

Linear Regression

Ridge Regression

Random Forest Regressor

XGBoost Regressor

##Hyperparameter Optimization Approach

GridSearchCV გამოვიყენე hyperparameter ოპტიმიზაციისათვის.პარამეტრების გრიდი იყო აღწერილი ყოველი მოდელისთვის და cross-validation იქნა ჩატარებული რომ დაგვედგინა საუკეთესო პარამეტრები.

##საუკეთესო მოდელის შერჩევის დასაბუთება
მრავალჯერ ჩავატარე ექსპერიმენტი და ყოველი ჩატარებისას, მიუხედავად იმისა, რომ ყველა მოდელი თითქმის თანაბარ შედეგს აბრუნებდა, XGBoost მოდელი იყო მათ შორის საუკეთესო. ამ მოდელს ვამჯობინებ ჩატარებული ექსპერიმენტის შედეგების საფუძველზე(RMSE). გატესტვისას linear regression მოდელში საშუალო მოდათი შევცვალე და უკეთესი შედეგი ვერ დადო. სხვა მოდელებისთვის კი შესაბამისი პარამეტრებისათვის რამდენიმე ვარიანტი დავტესტე და ამ შემთხვევაშიც თითქმის თანაბარი შედეგები მივიღე, ზოგჯერ linear-regression იმავენაირ შედეგს მაძლევდა, რასაც სხვა მოდელები. საბოლოოდ კი, მაინც შემიძლია ვთქვა, რომ მცირედი უპირატესობით ყოველთვის სჯობდა XGB: ყველაზე დაბალი RMSE, ყველაზე მაღალი R².

#MLflow Tracking

##MLflow ექსპერიმენტების ბმული

https://dagshub.com/ashar-22/hw01ml.mlflow/#/experiments/1?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D
https://dagshub.com/ashar-22/hw01ml.mlflow/#/experiments/0?searchFilter=attributes.user_id%20%3D%20'ashar-22'

##ჩაწერილი მეტრიკების აღწერა

◌ RMSE (log1p): Root Mean Squared Error სასურველ ცვლადზე ლოგარითმის მოდების შემდეგ.

◌ MAE (log1p): Mean Absolute Error ლოგარითმის მოდების შემდეგ.

◌ R² (log1p): R² ლოგარითმის მოდების შემდეგ.

###საუკეთესო მოდელის შედეგები
Metric Values:

mae - 0.09226510115111172
rmse - 0.13625557340876357
r2 - 0.900511853962483
