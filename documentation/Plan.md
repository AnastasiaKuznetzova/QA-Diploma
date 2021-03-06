**План автоматизации**

**Объект тестирования:**

Веб-сервис оплаты путешествия двумя способами:

- дебетовой картой
- выдачей кредита по реквизитам банковской карты

**Валидные данные тестовых карт:**

- Номер карты APPROVED: 4444 4444 4444 4441
- Номер карты DECLINED: 4444 4444 4444 4442
- Месяц: двузначное число в диапазоне 01...12
- Год: больше текущего на два, в формате двузначного числа
- Владелец: Имя и Фамилия латиницей
- CVC: Трёхзначное число в диапазоне 000...999
 
**Перечень автоматизируемых сценариев:**

**1. Позитивные сценарии**

   **1.1 Заполнение валидными данными Payment Gate с картой APPROVED:**

- Нажать кнопку “Купить”
- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ Сообщение “Успешно. Операция одобрена Банком.”

**1.2 Заполнение валидными данными Credit Gate с картой APPROVED:**

- Нажать кнопку “Купить в кредит”
- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ Сообщение “Успешно. Операция одобрена Банком.”

**1.3 Заполнение валидными данными Payment Gate с картой DECLINED:**

- Нажать кнопку “Купить”
- В поле “номер карты” ввести: 4444 4444 4444 4442
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ Сообщение “Ошибка! Банк отказал в проведении операции”

**1.4 Заполнение валидными данными Credit Gate с картой DECLINED:**

- Нажать кнопку “Купить в кредит”
- В поле “номер карты” ввести: 4444 4444 4444 4442
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ Сообщение “Ошибка! Банк отказал в проведении операции”

**2. Работа с полем “Номер карты” для Payment Gate и Credit Gate**

   Сначала проверяется поле по кнопке “Купить”, далее по кнопке “Купить в кредит”

**2.1 Номер карты пустой**

- Поле “номер карты” оставить не заполненным
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “номер карты” появляется сообщение “Неверный формат”, заявка не отправляется.

**2.2 Номер карты из одинаковых цифр**

- В поле “номер карты” ввести: 9999 9999 9999 9999
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ Сообщение “Ошибка! Банк отказал в проведении операции”

**2.3 Номер карты заполнен не полностью**

- В поле “номер карты” ввести: 9999 9999 9999 99
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “номер карты” появляется сообщение “Неверный формат”, заявка не отправляется.

**3. Работа с полем “Месяц” для Payment Gate и Credit Gate**

   Сначала проверяется поле по кнопке “Купить”, далее по кнопке “Купить в кредит”

**3.1 Заполнение поля невалидным значением**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 16
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “месяц” появляется сообщение “Неверно указан срок действия карты”, заявка не отправляется.

**3.2 Заполнение поля однозначным числом**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 2
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “месяц” появляется сообщение “Неверный формат”, заявка не отправляется.

**3.3 Поле оставить пустым**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- Поле "Месяц" оставить не заполненным
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “месяц” появляется сообщение “Неверный формат”, заявка не отправляется.

**3.4 Заполнение поля нулевым значением**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 00
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “месяц” появляется сообщение “Неверный формат”, заявка не отправляется.

**4. Работа с полем “Год” для Payment Gate и Credit Gate**

   Сначала проверяется поле по кнопке “Купить”, далее по кнопке “Купить в кредит”

**4.1 Заполнение поля прошедшей датой**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 08
- В поле "Год" ввести: 18
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “год” появляется сообщение “Истёк срок действия карты”, заявка не отправляется.

**4.2 Заполнение поля однозначным числом**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 2
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “месяц” появляется сообщение “Неверный формат”, заявка не отправляется.

**4.3 Поле оставить пустым**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- Поле "Год" оставить пустым
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “год” появляется сообщение “Неверный формат”, заявка не отправляется.

**4.4 Заполнение поля невалидным значением**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 32
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “год” появляется сообщение “Неверно указан срок действия карты”, заявка не отправляется.

**5. Работа с полем “Владелец” для Payment Gate и Credit Gate**

   Сначала проверяется поле по кнопке “Купить”, далее по кнопке “Купить в кредит”

**5.1 Заполнение поля невалидным значением (не указав фамилию)**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “Владелец” появляется сообщение “Неверный формат”, заявка не отправляется.

**5.2 Заполнение поля кириллицей**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Алексей Петров
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “Владелец” появляется сообщение “Неверный формат”, заявка не отправляется.

**5.3 Поле оставить пустым**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- Поле "Владелец" оставить пустым
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “Владелец” появляется сообщение “Поле обязательно для заполнения”, заявка не отправляется.

**5.4 Заполнение поля невалидным значением (цифрами)**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: 2104
- В поле "CVC/CVV" ввести: 999
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “Владелец” появляется сообщение “Неверный формат”, заявка не отправляется.

**6. Работа с полем “CVC/CVV” для Payment Gate и Credit Gate**

   Сначала проверяется поле по кнопке “Купить”, далее по кнопке “Купить в кредит”

**6.1 Заполнение поля невалидным значением (не полностью)**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- В поле "CVC/CVV" ввести: 99
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “CVC/CVV” появляется сообщение “Неверный формат”, заявка не отправляется

**6.2 Поле оставить пустым**

- В поле “номер карты” ввести: 4444 4444 4444 4441
- В поле "Месяц" ввести: 09
- В поле "Год" ввести: 23
- В поле "Владелец" ввести: Alex Petrov
- Поле "CVC/CVV" оставить пустым
- Нажать кнопку "Продолжить"

_Ожидаемый результат:_ под полем “CVC/CVV” появляется сообщение “Неверный формат”, заявка не отправляется.

**Перечень используемых инструментов:**
1. IntelliJ IDE, Gradle для написания авто тестов
2. Docker для развертывания сервера SQL и запуска симулятора данных на Node.js
3. Selenide для взаимодействия с web элементами на странице
4. Google Chrome для работы с web формой
5. Java - для написания автотестов
6. Git, Github - для хранения кода
7. Junit 5 для работы с annotations и assertions
8. Allure для отчета по автотестам
9. Appveyor для непрерывной интеграции CI

**Перечень и описание возможных рисков при автоматизации:**
- Отсутствие документации на приложение: поведение приложение придётся изучать в режиме он-лайн.
- Сложности при подключении к БД с различными СУБД: ошибки авторизации, ошибки настройки коннектора.
- Изучение особенностей подключения и обмена с банковскими сервисами: ранее не пробовал настраивать взаимодействие по REST API.
- Возможная неработоспособность элементов веб-формы или особый формат заполнения: может потребоваться время на подбор способа заполнения формы и подготовку тестовых данных.

**Интервальная оценка с учётом рисков (в часах)**
- Разработка плана тестирования - 8 часов;
- Подготовка необходимых инструментов, написание кода автотестов - 64 часа;
- Подготовка отчетной документации, баг-репортов - 12 часов;
- Запас в виде 24 часов на непредвиденные обстоятельства.


**План сдачи работ:**
- Готовность автотестов - 14 рабочих дней после утверждения плана и разрешения вопросов;
- Результат работы автотестов - документы по итогам тестирования (отчет по итогам тестирования + баг-репорты) - 3 рабочих дня ;
- Подготовка отчёта по автоматизации - 3 рабочих для после проведения всех работ.