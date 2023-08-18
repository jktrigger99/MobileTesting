## Charles Proxy Homework

## Ex_0: Сфокусироваться на перечисленных ниже запросах
```
Protocol: http
IP: 162.55.220.72
Port: 5005
```
На вкладке "Structure" в поле "Filter" добавляем адрес `162.55.220.72`

## Ex_1: EndPoint: /get_method
#### Task: подменить URL в Charles, чтобы в запросе ушло имя, которое вы вписали в Postman, а вернулось то, которое вы подставили в Charles (сделать и в Rewrite, и в BreakPoint)

1.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/get_method` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажок "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Response"
- Поменять значение поля "name" на любое другое и кликнуть "Execute"

1.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/get_method` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить правило: тип "Modify Query Param" (`Match` Name: name; `Replace` Name: name, Value: New_name) и кликнуть "ОК"
- Выполнить запрос

## Ex_2: EndPoint: /user_info_3
#### Task: Подменить body в Charles так, чтобы в запросе ушла salary, которую вы вписали в Postman, а в u_salary_1_5_year вернулась сумма меньше оригинальной из запроса (сделать и в Rewrite, и в BreakPoint)

2.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/user_info_3` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажок "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Response"
- Поменять значение поля "u_salary_1_5_year" на меньшее и кликнуть "Execute"

2.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/user_info_3` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить правило: тип "Body" (`Match` Value: "u_salary_1_5_year": 4000; `Replace` Value: "u_salary_1_5_year": 3999) и кликнуть "ОК"
- Выполнить запрос

## Ex_3: EndPoint: /object_info_1
#### Task: Подменить параметры запроса в Charles так, чтобы в Postman пришел ответ, где другое name, daily_food > weight из запроса, а daily_sleep < weight из запроса (сделать и в Rewrite, и в BreakPoint)

3.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/object_info_1` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажок "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Response"
- Поменять значение полей "name", "daily_food" и "daily_sleep" и кликнуть "Execute"

3.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/object_info_1` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить 3 правила типа "Body":
    - `Match` Value: "name": "Evgeny"; `Replace` Value: "name": "Phil"
    - `Match` Value: "daily_food": 0.792; `Replace` Value: "daily_food": 70
    - `Match` Value: "daily_sleep": 165.0; `Replace` Value: "daily_sleep": 50
- Выполнить запрос

## Ex_4: EndPoint: /object_info_3
#### Task: Сделать и в Rewrite, и в BreakPoint:
#### - Чтобы сервер вернул 500 код
#### - Чтобы сервер вернул 405 код

4.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/object_info_3` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажок "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Response"
- Поменять статус код `200 OK` на `500 Internal Server Error` и кликнуть "Execute"
- Снова выполнить запрос
- Поменять статус код `200 OK` на `405 Method Not Allowed` и кликнуть "Execute"

4.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/object_info_3` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить правило: тип "Response Status" (`Match` Value: 200 OK; `Replace` Value: 500 Internal Server Error) и кликнуть "ОК"
- Выполнить запрос
- Добавить правило: тип "Response Status" (`Match` Value: 200 OK; `Replace` Value: 405 Method Not Allowed) и кликнуть "ОК"
- Выполнить запрос (применяться будет то правило, которое находится в списке выше)

Также можно не просто подменить код ответа, но и сделать так, чтобы бэкэнд вернул нам данные ошибки:
- для получения 500 ошибки можно подменить название обязательного параметра "salary" на какое-нибудь другое
- для получения 405 ошибки можно подменить эндпоинт /object_info_3 на другой, который не принимает метод GET (например, /user_info_3)
 
## Ex_5: EndPoint: /object_info_4
#### Task: Сделать и в Rewrite, и в BreakPoint:
#### - Чтобы сервер вернул 405 код
#### - Подменить salary в request
#### - Подменить (salary * 2) в response

5.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/object_info_4` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажки "Request" и "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Request"
- Поменять значение поля "salary" и кликнуть "Execute"
- Выбрать вкладку "Edit Response"
- Поменять значение статус-кода  и поля "salary[1]" и кликнуть "Execute"

5.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/object_info_4` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить 3 правила:
    - тип "Modify Query Param" - `Match` Name: salary; `Replace` Name: salary, Value: 10000
    - тип "Response Status" - `Match` Value: 200 OK; `Replace` Value: 405 Method Not Allowed
    - тип "Body" - `Match` Value: 20000; `Replace` Value: 25000
- Выполнить запрос

## Ex_6: EndPoint: /user_info_2
#### Task: Сделать и в Rewrite, и в BreakPoint:
#### - Чтобы в Postman вернулся ответ, в котором qa_salary_after_1.5_year переименовано в qa_salary_after_1.5_month
#### - Чтобы qa_salary_after_3.5_years было меньше qa_salary_after_12_months в response

6.1 BreakPoint

- Выбрать Proxy -> Breakpoint Settings
- Поставить флажок "Enable Breakpoints" и кликнуть "Add"
- Вставить в поле "Host" адрес запроса `http://162.55.220.72:5005/user_info_2` и кликнуть на любом другом поле, чтобы запрос распарсился
- Поставить флажок "Response" и кликнуть "ОК"
- Выполнить запрос
- В появившемся окне Charles выбрать вкладку "Edit Response"
- Поменять название поля значение поля "qa_salary_after_1.5_year" на "qa_salary_after_1.5_month", а также уменьшить значение поля "qa_salary_after_3.5_years" и кликнуть "Execute"

6.2 Rewrite

- Выбрать Tools -> Rewrite
- Поставить флажок "Enable Rewrite" и кликнуть "Add"
- Добавить "Location": вставить в поле "Host" `http://162.55.220.72:5005/user_info_2` и кликнуть на любом другом поле, чтобы запрос распарсился
- Добавить 2 правила типа "Body":
    - `Match` Value: qa_salary_after_1.5_year; `Replace` Value: qa_salary_after_1.5_month
    - `Match` Value: 38000.0; `Replace` Value: 17000.0
- Выполнить запрос
