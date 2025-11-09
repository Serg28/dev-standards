# Правила именования кода для ИИ

## Общие принципы

* **Правило:** Имя должно отражать назначение сущности. Не допускаются бессмысленные или шутливые названия.
* **Правило:** Все имена — только на английском языке.
* **Правило:** Грамматика должна соответствовать английской структуре. Пример: `horizontalAlignment`, а не `alignmentHorizontal`.
* **Правило:** Избегать дезинформирующих имён. Имя должно точно отражать действие или назначение.
* **Правило:** Имена должны быть легко читаемыми и произносимыми.

## Классы

* **Формат:** PascalCase
* **Тип слова:** Существительное.
* **Правило:** Имя класса описывает объект или сущность.
* **Пример:** ✅ `Customer`, `InvoiceParser` / ❌ `CustomerData`, `DataHandler`
* **Правило:** Если применяется паттерн проектирования, указывать его в названии.

    * Пример: `CustomerBuilder`, `OrderFactory`

## Методы и функции

* **Формат:** camelCase
* **Тип слова:** Глагол.
* **Правило:** Имя описывает действие.
* **Пример:** ✅ `getCustomer()`, `calculateTotal()` / ❌ `customerGet()`, `emailSending()`
* **Булевы методы:** начинать с `is`, `has`, `can`, `should`.

    * Пример: ✅ `isActive()`, `canDelete()` / ❌ `deleteFlag()`, `permission()`

## Переменные и свойства

* **Формат:** camelCase
* **Правило:** Имя отражает содержимое переменной.
* **Правило:** Длина имени зависит от области видимости. Чем шире область — тем информативнее имя.
* **Пример:** ✅ `$totalAmount`, `$userEmail` / ❌ `$a`, `$temp`
* **Правило:** Использовать симметричные пары: `min/max`, `begin/end`, `locked/unlocked`.

## Константы

* **Формат:** UPPER_SNAKE_CASE
* **Правило:** Имя отражает фиксированное значение.
* **Пример:** ✅ `MAX_ATTEMPTS`, `DEFAULT_TIMEOUT` / ❌ `MaxAttempts`, `defaultTimeout`

## Точность и контекст

* **Правило:** Для численных значений всегда указывайте единицы измерения в имени.
    * **Пример:** ✅ `$requestTimeoutInSeconds`, `$memoryLimitInMegabytes` / ❌ `$timeout`, `$limit`
* **Правило:** Для сложных или неоднозначных значений (например, деньги, проценты) использовать объекты-значения (Value Objects) вместо примитивных типов.
    * **Пример:** ✅ `Percentage::fromFloat(0.5)` / ❌ `$percentage = 50`
* **Правило:** Отдавать предпочтение длинным и описательным именам, а не коротким и загадочным. Имя должно полностью раскрывать суть переменной.

## Laravel Naming Conventions

**Rule:** Adhere strictly to the following Laravel naming conventions.

| Item | Convention | ✅ Correct | ❌ Incorrect |
| :--- | :--- | :--- | :--- |
| **Controller** | Singular | `ArticleController` | `ArticlesController` |
| **Route** | Plural | `articles/1` | `article/1` |
| **Route Name** | snake_case | `users.show_active` | `users.show-active` |
| **Model** | Singular | `User` | `Users` |
| **Relation (hasOne, belongsTo)** | Singular | `articleComment` | `articleComments`, `article_comment` |
| **Relation (hasMany, belongsToMany)** | Plural | `articleComments` | `articleComment`, `article_comments` |
| **Table** | Plural | `article_comments` | `article_comment`, `ArticleComment` |
| **Pivot Table** | Singular, alphabetical model names | `article_user` | `user_article`, `articles_users` |
| **Table Column** | snake_case, no model name | `meta_title` | `metaTitle`, `article_meta_title` |
| **Foreign Key** | Singular model name + `_id` | `article_id` | `ArticleId`, `id_article`, `articles_id` |
| **Primary Key** | - | `id` | `custom_id` |
| **Migration** | - | `2017_01_01_000000_create_articles_table` | `2017_01_01_000000_articles` |
| **Method** | camelCase | `getAll` | `get_all` |
| **Variable** | camelCase | `$articlesWithAuthor` | `$articles_with_author` |
| **Collection** | Descriptive, plural | `$activeUsers` | `$active`, `$data` |
| **Object** | Descriptive, singular | `$activeUser` | `$users`, `$obj` |
| **Config Property** | snake_case | `users.max_articles` | `users.max-articles` |
| **View** | kebab-case | `show-filtered.blade.php` | `showFiltered.blade.php` |
| **Config File** | snake_case | `config/stripe.php` | `config/Stripe.php` |
| **Interface** | Noun or Adjective | `AuthenticationInterface` | `Authenticatable`, `IAuthentication` |
| **Trait** | Adjective | `Notifiable` | `Notification` |
| **Enum** | Singular | `UserType` | `UserTypes` |
| **Form Request** | PascalCase | `UpdateUserRequest` | `UserFormRequest`, `UserRequest` |
| **Action** | Singular | `ProcessPodcast` | `ProcessPodcastAction` |
| **Exception** | Singular | `ModelNotFoundException` | `ModelNotFound` |

## Читаемость

* **Правило:** Код должен читаться как естественная фраза.
* **Пример:** ✅ `if ($list->contains($item))` / ❌ `if ($list->isContained($item))`

## Сокращения

* **Правило:** Не использовать непонятные аббревиатуры.
* **Исключения:** допустимы `id`, `url`, `db`.
* **Пример:** ✅ `userId`, `createdAt` / ❌ `usr`, `crAt`

## Итог

* Все имена должны быть осмысленными, краткими и точными.
* Соблюдать единый стиль именования во всём проекте.
* Имена должны быть самодокументирующими.
