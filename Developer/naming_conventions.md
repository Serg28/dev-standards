# Соглашения об именовании

Этот документ описывает ключевые принципы и стандарты именования, принятые в нашем проекте. Соблюдение этих правил помогает сделать код более читаемым, предсказуемым и лёгким для поддержки.

## Фундаментальные принципы

### 1. Язык и однозначность

*   **Используйте только английский язык.** Никакого транслита.
    *   ✅ **Правильно:** `$user`, `$order`
    *   ❌ **Неправильно:** `$polzovatel`, `$zakaz`

*   **Соблюдайте грамматику английского языка.**
    *   ✅ **Правильно:** `$horizontalAlignment`
    *   ❌ **Неправильно:** `$alignmentHorizontal`

*   **Имена должны быть произносимыми и доступными для поиска.** Избегайте аббревиатур, которые невозможно произнести, и однобуквенных переменных вне локальных циклов.
    *   ✅ **Правильно:** `$mailingList`, `const MAX_LOGIN_ATTEMPTS`
    *   ❌ **Неправильно:** `$mList`, `const ATTEMPTS = 5`

*   **Не допускайте шуток в коде.** Имена вроде `$holyHandGrenade` неуместны в профессиональной разработке.

### 2. Точность и осмысленность

*   **Имя должно строго соответствовать тому, что делает сущность.**
    *   ✅ **Правильно:** `Validator`, `HtmlEncoder`
    *   ❌ **Неправильно:** `Manager`, `Processor` (слишком общие)

*   **Избегайте "шумных" и неоднозначных слов,** таких как `Data`, `Info`, `Object`.
    *   ✅ **Правильно:** `Customer`, `Address`
    *   ❌ **Неправильно:** `CustomerData`, `AddressInfo`

*   **Используйте технические термины, отражающие паттерны проектирования.**
    *   ✅ **Правильно:** `CustomerBuilder`, `OrderFactory`, `PaymentStrategy`
    *   ❌ **Неправильно:** `MakeCustomer`, `CreateOrder` (если это классы, а не методы)

*   **Используйте симметричные пары** для противоположных операций.
    *   ✅ **Правильно:** `begin/end`, `first/last`, `min/max`, `lock/unlock`, `increment/decrement`

### 3. Структура и читаемость

*   **Классы — существительные, методы — глаголы.**
    *   ✅ **Правильно:** `class Order`, `public function send()`
    *   ❌ **Неправильно:** `class Send`, `public function order()`

*   **Булевы значения должны читаться как вопрос (предикат).**
    *   ✅ **Правильно:** `isEnabled`, `hasPermissions`, `canDeletePost()`
    *   ❌ **Неправильно:** `getPermissions()`, `checkDelete()`

*   **Код должен читаться как проза.** Старайтесь, чтобы вызовы методов и условия были максимально естественными для чтения.
    *   ✅ **Правильно:** `if ($cart->hasItems()) { ... }`
    *   ❌ **Неправильно:** `if ($cart->checkIfItemsExist()) { ... }`

*   **Длина имени зависит от области видимости.** Чем шире область видимости, тем более описательным должно быть имя.
    *   ✅ **Локальный цикл:** `foreach ($users as $u) { ... }`
    *   ✅ **Метод:** `public function getUserById(int $userId): User`
    *   ✅ **Свойство класса:** `private User $authenticatedUser;`

### 3. Придерживайтесь контекста

Имена должны быть понятны в том контексте, где они используются.

*   **Используйте один термин для одного понятия.** Не называйте одно и то же действие `fetch`, `retrieve` и `get` в разных частях кода. Выберите что-то одно.
*   **Не добавляйте избыточный контекст.** Если класс называется `Order`, не нужно называть его свойства `orderId` или `orderDate`. Просто `id` и `date` будет достаточно. Контекст уже задан классом.

## Практические рекомендации

### Переменные

*   **Формат:** `camelCase`
*   **Для булевых значений** используйте префиксы `is`, `has`, `can`.
    *   `$isActive`, `$hasErrors`, `$canDelete`
*   **Для коллекций** используйте множественное число.
    *   `$users`, `$orders`
*   **Указывайте единицы измерения**, если это применимо.
    *   ✅ **Правильно:** `$timeoutInSeconds`, `$memoryLimitInMb`
    *   ❌ **Неправильно:** `$timeout`, `$limit`

### Функции и методы

*   **Формат:** `camelCase`
*   Имя должно описывать **действие** и, при необходимости, **результат**.
    *   `formatPhoneNumber()`
    *   `calculateTotalPrice()`
*   **Геттеры и сеттеры** должны начинаться с `get` и `set`.
    *   `getName()`, `setName(string $name)`

### Классы и интерфейсы

*   **Формат:** `PascalCase`
*   **Интерфейсы** должны иметь суффикс `Interface`.
    *   `PayableInterface`, `UserRepositoryInterface`
*   **Абстрактные классы** могут иметь префикс `Abstract`.
    *   `AbstractController`
*   **Трейты** должны иметь суффикс `Trait`.
    *   `NotifiableTrait`

### Cоглашения об именовании в Laravel

Всегда следуйте официальным и общепринятым cоглашениям об именовании в Laravel.

| Что | Как | ✅ Правильно | ❌ Неправильно |
| :--- | :--- | :--- | :--- |
| **Контроллер** | единственное число | `ArticleController` | `ArticlesController` |
| **Роут** | множественное число | `articles/1` | `article/1` |
| **Именование роутов** | snake_case | `users.show_active` | `users.show-active` |
| **Модель** | единственное число | `User` | `Users` |
| **Отношения** (`hasOne`, `belongsTo`) | единственное число | `articleComment` | `articleComments`, `article_comment` |
| **Отношения** (`hasMany`, `belongsToMany`) | множественное число | `articleComments` | `articleComment`, `article_comments` |
| **Таблица** | множественное число | `article_comments` | `article_comment`, `ArticleComment` |
| **Сводная таблица** | имена моделей в единственном числе в алфавитном порядке | `article_user` | `user_article`, `articles_users` |
| **Поле в таблице** | snake_case без имени модели | `meta_title` | `metaTitle`, `article_meta_title` |
| **Внешний ключ** | имя модели в единственном числе с суффиксом `_id` | `article_id` | `ArticleId`, `id_article`, `articles_id` |
| **Первичный ключ** | - | `id` | `custom_id` |
| **Миграция** | - | `2017_01_01_000000_create_articles_table` | `2017_01_01_000000_articles` |
| **Метод** | camelCase | `getAll` | `get_all` |
| **Метод в ресурсном контроллере** | [стандартные](https://laravel.com/docs/master/controllers#resource-controllers) | `store` | `saveArticle` |
| **Переменная** | camelCase | `$articlesWithAuthor` | `$articles_with_author` |
| **Коллекция** | описательное, множественное число | `$activeUsers` | `$active`, `$data` |
| **Объект** | описательное, единственное число | `$activeUser` | `$users`, `$obj` |
| **Свойство в конфиге** | snake_case | `users.max_articles` | `users.max-articles` |
| **Представление (View)** | kebab-case | `show-filtered.blade.php` | `showFiltered.blade.php` |
| **Конфиг** | snake_case | `app/config/stripe.php` | `app/config/Stripe.php` |
| **Контракт (интерфейс)** | cуществительное или прилагательное | `AuthenticationInterface` | `Authenticatable`, `IAuthentication` |
| **Трейт** | прилагательное | `Notifiable` | `Notification` |
| **Enum** | единственное число | `UserType` | `UserTypes` |
| **Form Request** | `PascalCase` | `UpdateUserRequest` | `UserFormRequest`, `UserRequest` |
| **Действие (Action)** | единственное число | `ProcessPodcast` | `ProcessPodcastAction` |
| **Исключение** | единственное число | `ModelNotFoundException` | `ModelNotFound` |
