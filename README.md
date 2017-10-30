MySQL Python - manageDB
===========

## Описание
**manageDB** подключается к MySQL и использует такие запросы, как SELECT (одно и несколько условий), INSERT, UPDATE, DELETE простым и быстрым способом.


## Применение
Чтобы начать использовать manageDB, вам необходимо инициализировать
инициализировать класс используя 4 необходимых параметров: `host`, `user`, `password`, `database`

```
connect_mysql = MysqlPython('host.ip.address', 'user', 'password', 'database')
```
    
#### SELECT с одним условием
Если вы хотите получать информацию из одной таблицы и использовать одно условие, вы можете
использовать функцию SELECT где аргумент args предназначен для ссылки на столбцы, которые вам нужно получить.

```
conditional_query = "id = %s"
result = connect_mysql.select("table", conditional_query, "morning", "upload", id = "245919343")
```

**Результат:**
	Функция возвращает список или пустой список в случае отсутствия ничего.

---
    
#### SELECT с несколькими условиями
Если вам нужно получить информацию с более чем одним условием, вы можете использовать функцию
`select_advanced` , где столбцы, которые вам нужно получить, ссылаются на `args` а на условные обозначения указаны `tuples`.

```
sql_query = 'SELECT C.cylinder FROM car C WHERE C.car_make = %s AND C.car_model = %s'
result = connect_mysql.select_advanced(sql_query, ('car_make', 'nissan'), ('car_model', 'altima'))
```

**Результат:**
	Функция возвращает список или пустой список в случае отсутствия ничего.

---
    
#### SELECT с несколькими условиями
Если вам нужно получить информацию с более чем одним условием, вы можете использовать функцию
`select_advanced` , где столбцы, которые вам нужно получить, ссылаются на `args` а на условные обозначения указаны `tuples`.

```
sql_query = 'SELECT C.cylinder FROM car C WHERE C.car_make = %s AND C.car_model = %s'
result = connect_mysql.select_advanced(sql_query, ('car_make', 'nissan'), ('car_model', 'altima'))
```

**Результат:**
	Функция возвращает список или пустой список в случае отсутствия ничего.

---

#### INSERT - вставка данных
Вставка данных интуитивно понятна, мы будем ссылаться на столбец и значения

```
result = connect_msyql.insert('table', car_make = 'ford' ,car_model = 'escort', car_year = '2005')
```

**Результат:**
	Функция возвращает последний идентификатор строки.

---

#### UPDATE - обновление данных
Для обновления данных требуется только таблица, условный запрос и укажите столбцы, которые вы хотите обновить

```
conditional_query = 'car_make = %s'
result = connect_mysql.update('table', conditional_query, 'nissan', car_model='escort', car_year='2005')
```

**Результат:**
	Функция возвращает количество обновленных строк.

---

#### UPDATE - удаление данных
Удалить данные очень просто, как вставка, просто укажите столбец как условие и таблицу.

```
conditional_query = 'id = %s'
result = connect_mysql.delete('table', conditional_query, 'nissan')
```

**Результат:**
	Функция возвращает количество удаленных строк.

## Требования

PyMySQL