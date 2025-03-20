## Стратегия разработки интернет-магазина

Как QA-инженер моя основная задача — обеспечить качество продукта, выявить дефекты на ранних стадиях и минимизировать риски, влияющие на пользователя и бизнес-показатели.
Тестирование будет проводиться согласно этапам на пирамиде тестирования: 
**1)** **Анализ требований** - создание документации с функциональными и нефункциональными требованиями.
**2)** **Проектирование** - разработка архитектуры, создание БД, прототив интерфейса.
**3)** **Разработка** - бекенд (функционал управления) + фронтенд (визуал).
**4)** **Тестирование**
   - 4.1. **Модульное тестирование** - тестирование отдельных компонентов и модулей.
   - 4.2. **Интеграционное тестирование** - тесты взаимодействий модулей.
   - 4.3. **Системное тестирование** - тесты системы на различных устройствах.
   - 4.4. **Регрессионное тестирование** - тесты после корректив.
   - 4.5. **Нагрузочное тестирование** - тесты на определения нагрузки по тест-сценарию через автоматизацию (условно 10, 100, 1000, 10000 пользователей одновременно).
**5)** **Развёртывание** - размещение магазина на сервере, проведение финальных тестов перед перед запуском, обеспечение бесперебойной работы.
**7)** **Эксплуатация**. По мере эксплуатации следить за технической поддержкой, отслеживать баги, решать их и тестировать.
  
### Этап 1: Анализ требований (подготовка), проектирование(неделя 1)
На данном этапе создаём документацию и тест-кейсы на основе требований, в документации будут описаны основной функционал, желаемый интерфейс, архитектура системы, схемы взаимодействий между компонентами, а также технические особенности. Это включает в себя детальное описание базы данных, используемых технологий и инструментов, а также план тестирования и критерии.
Одновременно с этим занимаемся процессом проектирвоания: в нём детально описывается алгоритм работы того или иного модуля.



На основе документации я буду подготавливать план тестирования и составлять тест-кейсы:
**1)** **Ручное тестирование** - здесь я буду указывать какие модули следует тестировать руками, в зависимости от её сложности. Составлю список, например: корзина(проверка логики, редактирование корзины), проверка оплаты(проверка на успешность платежа, нестандартные действия, по типу закрытия страницы на этапе оплаты), проверка на XSS уязвимости.
**2)** **Автоматическое тестирование** - для автоматического тестирования буду использовать библиотеки PyTest, requests, Bahave, Selenium для Python. Напишу основные шаблоны для тестирования пользовательского интерфейса, производительности и безопасности.
**3)** **Тест-кейсы** - документ, который описывает порядок действий тестирования, входные данные и ожидаемый результат.
**Пример тест-кейса:** 
1. **TEST-CASE №N**
2. **Название**: название тестируемого модуля.
3. **Описание**: описание модуля.
4. **Предисловия**: условия, которые необходимы перед началом тестирования.
5. **Шаги выполнения**: порядок действий, необходимый во время тестирования.
6. **Ожидаемый результат**: результат того или иного модуля в зависимости от требований.
7. **Статус**: успешно/неудачно.

-- 1/12

### Этап 2: Тестирование альфа-версии (недели 2-3)
После выхода первой альфа-версии интернет-магазина необходимо заниматься модульным и интеграционным тестированием. Здесь необходимо выявить критичные ошибки, например: утечка данных, логические ошибки при взаимодействии с модулями. 
На этом этапе я буду заниматься ручным тестированием, лично буду убеждаться в работоспособности или неработоспособности какого-либа модуля, составлять баг-репорты на основе тест-кейсов.
**Пример баг-репорта:**
   - 1) BUG-REPORT №N.
   - 2) Название: название модуля, выдавший ошибку.
   - 3) Описание: описание ошибки.
   - 4) Шаги выполенния: подробное описание шагов, которые надо выполнить для воспроизведения ошибки.
   - 5) Ожидаемый результат: результат который должен получиться
   - 6) Фактический результат: результат который получился.
   - 7) Статус: исправлено/не исправлено.

-- 3/12

### Этап 3: Функциональное тестирование (недели 5-8)
На этом этапе предполагается, что базовый функционал магазина исправно работает, дальше проверяем работу всех сценариев: поиск товаров, добавление в корзину, оформление заказа, выбор доставки и платежной системы.
Здесь я буду применять автоматизированное тестирование с помощью PyTest на взаимодействие пользователя с корзиной. Для более сложных модулей буду использовать ручное, необходимо будет проверить корректность всех данных на основе документации. Так же буду составлять баг-репорты по необходимости.
Займусь кросс-браузерным тестированием, системным тестированием на мобильных устройствах, проверка пользовательского интерфейса. Выполняется тестирование безопасности, включая SQL-инъекции, XSS-атаки, проверку работы SSL-сертификатов.

### Этап 4: Нагрузочное тестирование (недели 9-12)
После внесения исправлений и добавления новых возможностей проводим регрессионное тестирование, чтобы убедиться в отсутствии побочных эффектов. На этом этапе выполняем следующие действия:
**Нагрузочное тестирование** - создаются сценарии высокого трафика (10-10000 пользователей одновременно), в случае необходимости проводится работа по оптимизации.

### Этап 5: Финальное тестирование перед релизом (недели 13-14)
Перед выпуском проводим финальную проверка всего функционала.
**UX тестирование** - уделяется внимание интуитивности и удобству пользовательского интерфейса.
**Контрольная проверка безопасности** - проверка на наличие уязвимостей (SQL-инъекции, XSS-атаки).

### Этап 6: Пост-релизная поддержка (месяц после выпуска)
После релиза продолжается мониторинг системы, анализ качества, работа с пользовательскими отзывами и устранение критических дефектов. Дорабатываем автоматизированные тесты, запускаем стресс-тесты и анализируем лог-файлы для выявления потенциальных проблем.



## ОСНОВЫ БАЗЫ ДАННЫХ

### Задание 1.
```sql
CREATE DATABASE university
    WITH
    OWNER = postgres
    ENCODING = 'UTF8'
    LC_COLLATE = 'ru'
    LC_CTYPE = 'ru'
    LOCALE_PROVIDER = 'libc'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
```
### Задание 2.

```sql
DROP TABLE IF EXISTS Exams CASCADE;
DROP TABLE IF EXISTS Courses CASCADE;
DROP TABLE IF EXISTS Students CASCADE;	



CREATE TABLE Students (
    s_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    start_year INT
);

CREATE TABLE Courses (
    c_no SERIAL PRIMARY KEY,
    title VARCHAR(100) NOT NULL UNIQUE,
    hours INT
);

CREATE TABLE Exams (
    s_id INT REFERENCES Students(s_id) ON DELETE CASCADE,
    c_no INT REFERENCES Courses(c_no) ON DELETE CASCADE,
    score INT,
    PRIMARY KEY (s_id, c_no)
);
```

### Задание 3. 
```sql
INSERT INTO Students (name, start_year) VALUES 
('Иван Иванов', 2021),
('Мария Петрова', 2020),
('Алексей Сидоров', 2019),
('Сергей Кузнецов', 2022),
('Ольга Смирнова', 2023);

INSERT INTO Courses (title, hours) VALUES 
('Математика', 120),
('Физика', 100),
('Информатика', 100);


INSERT INTO Exams (s_id, c_no, score) VALUES 
(1, 1, 85),
(1, 2, 90),
(2, 1, 78),
(3, 3, 88), 
(3, 2, 75);  
```

### Задание 4. Несдавшие.
```sql
SELECT s_id, name 
FROM Students 
WHERE s_id NOT IN (SELECT s_id FROM Exams);
```
### Задание 5. Сдавшие
```sql
SELECT s_id, name, COUNT(*) AS exam_count 
FROM Students 
JOIN Exams USING (s_id) 
GROUP BY s_id, name;
```

### Задание 6. Средний балл по экзамену.
```sql
SELECT 
    c.title, 
    ROUND(AVG(e.score), 2) AS avg_score
FROM Courses c
JOIN Exams e ON c.c_no = e.c_no
GROUP BY c.title
ORDER BY avg_score DESC;
```
