### 
### Архитектура приложения состоит из 5 микросервисов:
- user-service - обрабатывает запросы пользователей
- event-service - обрабатывает запросы событий
- request-service обрабатывает заявками пользователей на участие в событиях
- comment-service - обрабатывает комментарии пользователей
- interaction-api - связывает все модули с помощью DTO, ENUM, Exception и Feign-клиентов

Все запросы идут через gateway-server.

### API для взаимодействия сервисов:
#### User-service
- Получение всех пользователей: **GET/admin/users**
- Поиск пользователя по id: **GET/admin/users/{userId}**
- Проверка пользователя: **GET/admin/{userId}**
#### Event-service:
- Поиск события по id: **GET/events/{id}**
- Добавление события: **POST/users/{userId}/events**
- Обновление заявок на участие: **PATCH/admin/events/{eventId}**
- Проверка на существование события: **GET/admin/events/{id}**
#### Request-service:
- Получение всех заявок: **GET/users/{userId}/requests**
- Добавление заявки: **POST/users/{userId}/requests**
- Отклонение заявки: **PATCH/users/{userId}/requests/{requestId}/cancel**
- Поиск всех заявок по id события: **GET/requests/event/{eventId}**
- Поиск подтвержденных заявок по id события: **GET/requests/event/confirmed/{eventId}**
- Обновление статуса заявки: **PATCH/requests/status/{id}**
#### Comment-service
1. Получение всех комментариев по id события: **GET/comments/{eventId}**
2. Создание комментария: **POST/users/{userId}/comments**
3. Обновление комментария: **PATCH/users/{userId}/comments/{commentId}**
4. Удаление комментария: **DELETE/users/{userId}/comments/{commentId}**
#### Stats-server
1. Получение статистики: **GET/stats**
2. Сохранение статистики: **POST/hit**
