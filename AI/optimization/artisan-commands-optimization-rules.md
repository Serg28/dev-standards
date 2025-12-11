# Задача: оптимизировать все Artisan-команды Laravel проекта, исключив создание тяжёлых зависимостей в конструкторах.

## Требования:

 - Просканируй все классы в app/Console/Commands.
 - Определи "тяжёлые" зависимости:

   - API-клиенты (PromApi, NovaPoshtaApi2 и т.п.)
   - HTTP-клиенты (Guzzle, Http::class)
   - Сервисы изображений (GD, Imagick, свои обёртки)
   - Blade compiler, FilesystemManager, QueueManager, Redis, Elasticsearch
   - Любые классы с тяжёлыми конструкторами

- Убери все такие зависимости из конструкторов команд.
- Перенеси их инициализацию в handle() через app() / resolve().
- Лёгкие зависимости (репозитории, мелкие сервисы) оставляй.
- Не менять логику команд, только место создания сервисов.
- Не изменять публичные методы и интерфейсы классов.

Пример:

Было:
```php
public function __construct(NovaPoshtaApi2 $np)
{
parent::__construct();
$this->np = $np;
}
```

Стало:

```php
public function __construct()
{
    parent::__construct();
}

public function handle()
{
    $np = app(NovaPoshtaApi2::class);
}
```

Выполни этот рефакторинг для всех команд проекта.
