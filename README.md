**Дипломный проект по профессии "Тестировщик"**

Дипломный проект - автоматизация тестирования комплексного сервиса, взаимодействующего с СУБД и API банка.

**Документация** 

[План автоматизации](https://github.com/GodIrina/Diploma-qa/blob/master/docs/Plan.md)

[Отчетные документы по итогам тестирования](https://github.com/GodIrina/Diploma-qa/blob/master/docs/Report.md)

[Отчетные документы по итогам автоматизации](https://github.com/GodIrina/Diploma-qa/blob/master/docs/Summary.md)

**Описание приложения: бизнес часть** 

Приложение представляет собой веб-сервис, по покупке тура.

![](service.png)

Приложение предлагает купить тур по определённой цене с помощью двух способов:

Обычная оплата по дебетовой карте
Уникальная технология: выдача кредита по данным банковской карты
Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

сервису платежей (далее - Payment Gate)
кредитному сервису (далее - Credit Gate)

**Предварительные условия для запуска автотестов**

1. Для запуска проекта и тестов на локальном компьютере потребуются установленные Git, JDK 11, IntelliJ IDEA, Docker
2. Запустить Docker Desktop
3. Склонировать репозиторий на локальный компьютер командой в Git:
    git clone https://github.com/GodIrina/Diploma-qa
4. Запустить IntelliJ IDEA и открыть проект

**Запуск контейнеров**

1. Запустить необходимые базы данных (MySQL и PostgreSQL). Параметры для запуска хранятся в файле docker-compose.yml. Для запуска необходимо ввести в терминале команду:
   docker-compose up

2. В новой вкладке терминала ввести команду в зависимости от базы данных:

   java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar ./artifacts/aqa-shop.jar (для базы данных MySQL);

   java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar ./artifacts/aqa-shop.jar (для базы данных PostgreSQL);

3. Проверить доступность приложения в браузере по адресу: http://localhost:8080/
4. В новой вкладке терминала запустить автотесты командой:

   ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app" (для базы данных MySQL);

   ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app" (для базы данных PostgreSQL);

5. Для запуска и просмотра отчетов по результатам тестирования, с помощью "Allure", выполнить команду:

   ./gradlew allureServe

