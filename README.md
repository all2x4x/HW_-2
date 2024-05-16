# Переводим код в one hot вид.
## Первоначальный код
```python
import random
lst = ['robot'] * 10
lst += ['human'] * 10
random.shuffle(lst)
data = pd.DataFrame({'whoAmI':lst})
data.head()
```
 
 ## Конечный код
# Исходные данные
import random
lst = ['robot'] * 10
lst += ['human'] * 10
random.shuffle(lst)
data = pd.DataFrame({'whoAmI':lst})

# Создание one-hot encoding
categories = data['whoAmI'].unique()
one_hot_encoded = pd.DataFrame(0, index=data.index, columns=categories)

for category in categories:
    one_hot_encoded[category] = (data['whoAmI'] == category).astype(int)

# Соединение one-hot encoding с исходными данными
data = pd.concat([data, one_hot_encoded], axis=1)
data.drop('whoAmI', axis=1, inplace=True)  # Удалить исходный столбец 'whoAmI'

data.head()
 ```