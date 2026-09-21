# C4-диаграмма контейнеров
## Веб-приложение для управления учебными материалами

Вставьте блок ниже как есть в файл `README.md` вашего репозитория — GitHub рендерит диаграммы Mermaid нативно, никакой картинки грузить не нужно.

```mermaid
C4Container
    title Диаграмма контейнеров — Веб-приложение для управления учебными материалами

    Person(student, "Студент", "Просмотр, поиск, скачивание материалов, избранное")
    Person(teacher, "Преподаватель", "Загрузка, редактирование, удаление материалов")
    Person(admin, "Администратор", "Управление пользователями, ролями, журналом событий")

    System_Boundary(webapp, "Веб-приложение для управления учебными материалами") {
        Container(frontend, "Frontend", "React / Vue, HTML5, CSS3", "Веб-интерфейс для трёх ролей пользователей, адаптивная вёрстка")
        Container(backend, "Backend", "Python, REST API, JWT", "Бизнес-логика, аутентификация и авторизация, обработка запросов")
        ContainerDb(database, "База данных", "PostgreSQL", "Пользователи, материалы, дисциплины, избранное, журнал событий")
        ContainerDb(filestorage, "Файловое хранилище", "File Storage", "Файлы материалов: PDF, DOCX, PPTX, XLSX, JPG, PNG")
    }

    System_Ext(emailSystem, "Почтовый сервер", "SMTP-сервер для восстановления пароля")
    System_Ext(externalSystem, "Внешняя информационная система", "Интеграция через REST API")

    Rel(student, frontend, "Использует", "HTTPS")
    Rel(teacher, frontend, "Использует", "HTTPS")
    Rel(admin, frontend, "Использует", "HTTPS")

    Rel(frontend, backend, "Запросы к API", "REST/JSON, HTTPS")
    Rel(backend, database, "Чтение/запись данных", "SQL")
    Rel(backend, filestorage, "Сохранение/получение файлов", "File I/O")
    Rel(backend, emailSystem, "Отправка писем восстановления пароля", "SMTP")
    Rel(externalSystem, backend, "Интеграция внешних систем", "REST API / HTTPS")

    UpdateLayoutConfig($c4ShapeInRow="2", $c4BoundaryInRow="1")
```
