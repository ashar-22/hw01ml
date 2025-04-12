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

◌ model_experiment.csv - ხდეbა მონაცემების დამუშავება, შემდეგი მათი დატრენინგება და საბოლოოდ დალოგვა MlFlow-ზე. 

◌ model_inference.csv -  ხდება MLflow-ზე დალოგილი მოდელის ჩამოტვირთვა და მისი მეშვეობით პროგნოზირება სატესტო მონაცემებზე.

◌ submission.csv: - შეიცავს პროგნოზებს ტესტ სეტისთვის, რომელიც ატვირთულია Kaggle-ზე.

# Feature Engineering

◌ Categorical ცვლადების შეცვლა: ენკოდირებულ იქნა OneHotEncoder-ის საშუალებით.

◌ ცარიელი მნიშვნელობების შეცვლა: ისინი, რომლებიც ეკუთვნოდა Numerical ტიპის სვეტებს, შევცვალე მათი საშუალოთი, ხოლო Categorical ტიპის - სვეტში ყველაზე ხშირი 
მნიშვნელობით.

◌ Scaling: Numerical ტიპის ინფორმაციები სტანდარტიზებულ იქნა StandardScaler-ის საშუალებით, რათა დაგვეყვანა საერთო scale-ზე.

