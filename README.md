# Data-engineer

Написать API и встроить в него модель. В модуле необходимо реализовать:
* запись "сырых" данных в БД на выбор (использование Redis, PostgreSQL приветствуется)
* расчет необходимых параметров 
* запись рассчитанных значений параметров
* вызов натренированной модели по заявке

API на входе должен принимать номер заявки. Ответ модуля должен включать в себя номер заявки, для которой проводился расчет и скоринговый балл модели для заявки - mdl.predict_proba(X)[:, 1]
Files

**Данные для использования в задании:**   
[raw_dataset.csv](https://github.com/cashupukraine/Data-engineer/blob/master/raw_data.csv) - данные для расчета входных параметров для модели.   
[test_model.pkl](https://github.com/cashupukraine/Data-engineer/blob/master/test_model.pkl) - файл с натренированной моделью
 
**Данные для самопроверки:**   
[final_dataset.csv](https://github.com/cashupukraine/Data-engineer/blob/master/final_dataset.csv) - входных данные после преобразований применения необходимых преобразований
[model_results.csv](https://github.com/cashupukraine/Data-engineer/blob/master/model_results.csv) - ответы модели по заявкам
 
**Features**
**Входные данные для модели:**   
* application_id - номер заявки
* amount - преобразованные значения поля amount из “сырого” датасета с использованием функции numpy.log()
* prev_amount -преобразованные значения поля prev_amount из “сырого” датасета с использованием функции numpy.log()
* diff_dates_in_days - разница между значениями полей start_date и finish_date из “сырого” датасета 
* free_amount - преобразованная разница между значениями полей earned и spendings из “сырого” датасета с использованием функции numpy.log() 

Все отсутствующие значения в датасете (значения типа NoneType) заменяются нулем. Значения остальных полей соответствуют значениям полей в “сыром” датасете (файл [raw_dataset.csv](https://github.com/cashupukraine/Data-engineer/blob/master/raw_data.csv))

Использование Docker для выполнения задания, написание unit тестов и реализация безопасного доступа к API (ограниченный доступ через headers etc.) приветствуется. 
