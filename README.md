# Mlops_1практика

## Создание инфраструктуры для простого проекта машинного обучения

## В данной работе проведены:
- настройка виртуальных машин
- создание конвеера для обработки данных
- обучение и оценка модели машинного обучения

Настроена связь между машинами (настройка виртуальных сетевых адаптеров):


Настроено обращение по именам машин:





Организация хранилища dvc на локальном сервере data_srv 

![Снимок экрана от 2023-10-08 16-14-19](https://github.com/Marakya/mlops_3/assets/113238801/54567f82-c71d-4e73-9ad0-dd9e5ac0876f)

![Снимок экрана от 2023-10-08 16-42-09](https://github.com/Marakya/mlops_3/assets/113238801/8bf3cb3c-faa3-4349-b72e-d6d543de2e2b)


Данные взяты с kaggle - Housing Price & Real Estate - 2023
https://www.kaggle.com/datasets/reenapinto/housing-price-and-real-estate-2023

Написаны три скрипта для обработки данных:

- get_features.py
- fill_na.py
- change_text_to_numeric.py

## Создание этапов (stage) и объединение их в единый конвейер 

![Снимок экрана от 2023-10-09 14-58-07](https://github.com/Marakya/mlops_3/assets/113238801/17fa2af5-14f0-41ae-8530-de7e5bdf0eb9)

![Снимок экрана от 2023-10-09 16-39-37](https://github.com/Marakya/mlops_3/assets/113238801/6e3ab7ad-f64a-4233-a969-ac4eb8161720)

Создание конвейера:

![Снимок экрана от 2023-10-09 16-40-22](https://github.com/Marakya/mlops_3/assets/113238801/73200500-69f6-458b-965d-011315604011)

Создан конвейер данных, который последовательно преобразует сырые данные. Сначала исходный файл выглядел так:

![image](https://github.com/Marakya/mlops_3/assets/113238801/6f0e1835-899d-4c16-adff-512371c7964e)

Затем мы оставили в нем только отдельные нужные нам признаки

![2023-10-09 (4)](https://github.com/Marakya/mlops_3/assets/113238801/dbbbe70a-5a9b-4eb3-8bd6-b9ea784a638b)

Признак -  содержит пропуски, заполним их средними значениями.

![2023-10-09 (5)](https://github.com/Marakya/mlops_3/assets/113238801/a87de661-2b7d-4bdf-bb80-30feaec95084)

Строковые значения признака-  заменены числовыми значениями.

![2023-10-09 (6)](https://github.com/Marakya/mlops_3/assets/113238801/2bf54d1f-f350-4e8a-a311-dd212387a95f)

В результате добавления в конвейер stage - train_test_split получаем два набора - train, test

![image](https://github.com/Marakya/mlops_3/assets/113238801/766d79ca-afc1-4b93-9ee7-5bb7568553ce)

![image](https://github.com/Marakya/mlops_3/assets/113238801/2b58a7ea-4783-4057-a2b1-7b8d79118f9e)

Также написаны скрипты по обучению и оценке модели, в результате после сборки конвейера dvc.yaml имеет вид:

![image](https://github.com/Marakya/mlops_3/assets/113238801/6d55a933-2543-4fad-87e7-7f9a85014d44)

После обучения модели, она сохраняется в папке models, а результаты её работы на новых данных в папке evaluate

![image](https://github.com/Marakya/mlops_3/assets/113238801/f39b2cca-49df-41b2-8921-6a5d94f1caae)

Эксперементируем с гиперпараметрами

![Снимок экрана от 2023-10-09 19-28-10](https://github.com/Marakya/mlops_3/assets/113238801/aed05959-b7fb-479f-a7fe-af3b27958ca0)

![Снимок экрана от 2023-10-10 11-08-30](https://github.com/Marakya/mlops_3/assets/113238801/223fcbef-b92f-4e13-b171-f1c2600546f3)

![Снимок экрана от 2023-10-09 19-17-34](https://github.com/Marakya/mlops_3/assets/113238801/f2adfbd4-6d28-40a0-8ed8-312f19a0cc00)

![Снимок экрана от 2023-10-09 19-28-39](https://github.com/Marakya/mlops_3/assets/113238801/405118d9-cf4e-4810-80bf-86633c4c91fe)



