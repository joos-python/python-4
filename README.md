### Домашнее задание «Коллекции данных.Словари.Множества»

### Задание 1
Дан список с визитами по городам и странам. Напишите код, который возвращает отфильтрованный список geo_logs, содержащий только визиты из России."

```
geo_logs = [
    {'visit1': ['Москва', 'Россия']},
    {'visit2': ['Дели', 'Индия']},
    {'visit3': ['Владимир', 'Россия']},
    {'visit4': ['Лиссабон', 'Португалия']},
    {'visit5': ['Париж', 'Франция']},
    {'visit6': ['Лиссабон', 'Португалия']},
    {'visit7': ['Тула', 'Россия']},
    {'visit8': ['Тула', 'Россия']},
    {'visit9': ['Курск', 'Россия']},
    {'visit10': ['Архангельск', 'Россия']}
]
```

### Решение

```python
geo_logs_sorted = []
for visit in geo_logs:
  for key, item in visit.items():
    if item[1] == "Россия":
      geo_logs_sorted.append(visit)

print(geo_logs_sorted)
```
!!!
```python
for visit in geo_logs:
    value = list(visit.values())[0][1]
    if value == 'Россия':
        print(visit)
```

### Задание 2
Выведите на экран все уникальные гео-ID из значений словаря ids.
Т.е. список вида [213, 15, 54, 119, 98, 35]
```
ids = {'user1': [213, 213, 213, 15, 213],
       'user2': [54, 54, 119, 119, 119],
       'user3': [213, 98, 98, 35]}
```
### Решение

```python
unique_ids = set()
for key, item in ids.items():
  for value in item:
    unique_ids.add(value)

print(unique_ids)
```
!!!
```python
my_set = set()
for geo_ids in ids.values():
    my_set |= set(geo_ids)
print(list(my_set))
```
### Задание 3
Дан список поисковых запросов. Получить распределение количества слов в них. Т.е. поисковых запросов из одного - слова 5%, из двух - 7%, из трех - 3% и т.д.
```
queries = [
    'смотреть сериалы онлайн',
    'новости спорта',
    'афиша кино',
    'курс доллара',
    'сериалы этим летом',
    'курс по питону',
    'сериалы про спорт'
    ]
```

### Решение

```python
queries_len = len(queries)
count = 1

while len(queries) != 0:
  sum_words = 0
  for value in queries:
    if len(value.split(" ")) == count:
      sum_words += 1
      queries[queries.index(value)] = ' '
  while ' ' in queries:
    queries.remove(' ')
  print(count, " word(s) = ", round(sum_words*100/queries_len), "%")
  count = count + 1
```
!!!
```python
number_words = [len(query.split()) for query in queries]
result = dict.fromkeys(set(number_words), 0)
for count_word in result:
    result[count_word] = number_words.count(count_word)
for word in result.items():
    print(f'Запросов с {word[0]} словами(словом) -  {round((word[1] * 100 / len(queries)), 2)}%')
```

### Задание 4
Дана статистика рекламных каналов по объемам продаж.
Напишите скрипт, который возвращает название канала с максимальным объемом.
Т.е. в данном примере скрипт должен возвращать 'yandex'.
```
stats = {'facebook': 55, 'yandex': 120, 'vk': 115, 'google': 99, 'email': 42, 'ok': 98}
```

### Решение

```python
max_volume = 0
best_kanal = ' '
for kanal, volume in stats.items():
  if volume > max_volume:
    best_kanal = kanal
    max_volume = volume
print(best_kanal)
```
!!!
```python
new_stats = sorted(stats.items(), key=lambda x: x[1], reverse=True)
print(new_stats[0][0])
```

### Задание 5
*Напишите код для преобразования произвольного списка вида ['2018-01-01', 'yandex', 'cpc', 100] (он может быть любой длины) в словарь {'2018-01-01': {'yandex': {'cpc': 100}}}


!!!
```python
lst = ['2018-01-01', 'yandex', 'cpc', 100]
lst = list(reversed(lst))
new_dict = lst[0]
for e in lst[1:]:
    new_dict = {e: new_dict}

print(new_dict)
```

