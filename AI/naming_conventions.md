# Правила именования для ИИ

**Основное правило:** Всегда следуй приведенным ниже соглашениям об именовании для всех создаваемых и изменяемых файлов и сущностей.

| Сущность | Правило | Пример |
| :--- | :--- | :--- |
| **Controller** | Единственное число, суффикс `Controller`. | `ArticleController` |
| **Route** | Множественное число для ресурсов. | `articles/1` |
| **Route Name** | `snake_case`, группировка через точку. | `users.show_active` |
| **Model** | Единственное число, `PascalCase`. | `User` |
| **hasOne/belongsTo Relation** | Единственное число, `camelCase`. | `articleComment` |
| **hasMany/belongsToMany Relation** | Множественное число, `camelCase`. | `articleComments` |
| **Table** | Множественное число, `snake_case`. | `article_comments` |
| **Pivot Table** | Имена моделей в ед.ч., `snake_case`, алфавитный порядок. | `article_user` |
| **Table Column** | `snake_case`, без имени таблицы. | `meta_title` |
| **Foreign Key** | Имя модели в ед.ч. + `_id`. | `article_id` |
| **Primary Key** | Всегда `id`. | `id` |
| **Migration** | `YYYY_MM_DD_HHMMSS_action_in_table_name`. | `2023_01_01_000000_create_articles_table` |
| **Method** | `camelCase`. | `getAll` |
| **Variable** | `camelCase`. | `$articlesWithAuthor` |
| **Collection Variable** | Описательное, множественное число. | `$activeUsers` |
| **Object Variable** | Описательное, единственное число. | `$activeUser` |
| **View File** | `kebab-case`. | `show-filtered.blade.php` |
| **Interface** | Суффикс `Interface`. | `AuthenticationInterface` |
| **Trait** | Суффикс `Trait`. | `NotifiableTrait` |
| **Enum** | Единственное число, `PascalCase`. | `UserType` |
| **Form Request** | `PascalCase`, суффикс `Request`. | `UpdateUserRequest` |

---

## Дополнительные правила

*   **Правило:** Имена должны быть осмысленными и раскрывать намерение.
    *   **Пример:** ✅ `$currentUser` / ❌ `$usr`, `$data`
*   **Правило:** Методы должны быть глаголами (`getCustomer`), классы — существительными (`Customer`).
*   **Правило:** Булевы переменные и методы должны начинаться с `is`, `has`, `can`.
    *   **Пример:** ✅ `canDeletePost()` / ❌ `permission()`
*   **Правило:** Для числовых переменных, где это применимо, указывай единицы измерения.
    *   **Пример:** ✅ `$timeoutInSeconds = 100;`
*   **Правило:** Избегай "магических" строк и чисел. Используй константы классов или файлы конфигурации.
    *   **Пример:** ✅ `if ($article->status === Article::STATUS_PUBLISHED)` / ❌ `if ($article->status === 2)`
