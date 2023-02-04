# Redis - Использование

### Очереди

> Есть два типа очередей FIFO (первым пришёл первым ушёл) и LIFO (последним пришёл первым ушёл)

> Процесс который занимается получением задачи из очереди называется consumer



##### Отправить задачу в очередь

```php
public function pushToQueue(string $queueName, $payload)
{
    $this->getRedis()->rawCommand('RPUSH', $queueName, serialize($payload));
}
```



### Laravel

https://github.com/russsiq/laravel-docs-ru/blob/9.x/docs/redis.md

```php
Laravel предлагает удобный интерфейс для команд publish и subscribe Redis. Эти команды Redis позволяют вам прослушивать сообщения на указанном «канале». Вы можете публиковать сообщения в канал из другого приложения или даже с использованием другого языка программирования, что позволяет легко взаимодействовать между приложениями и процессами.

Во-первых, давайте настроим слушатель каналов с помощью метода subscribe. Мы поместим вызов этого метода в команду Artisan, поскольку вызов метода subscribe запускает длительный процесс:

<?php

namespace App\Console\Commands;

use Illuminate\Console\Command;
use Illuminate\Support\Facades\Redis;

class RedisSubscribe extends Command
{
    /**
     * Имя и сигнатура консольной команды.
     *
     * @var string
     */
    protected $signature = 'redis:subscribe';

    /**
     * Описание консольной команды.
     *
     * @var string
     */
    protected $description = 'Subscribe to a Redis channel';

    /**
     * Выполнить консольную команду.
     *
     * @return mixed
     */
    public function handle()
    {
        Redis::subscribe(['test-channel'], function ($message) {
            echo $message;
        });
    }
}
Теперь мы можем публиковать сообщения в канале с помощью метода publish:

use Illuminate\Support\Facades\Redis;

Route::get('/publish', function () {
    // ...

    Redis::publish('test-channel', json_encode([
        'name' => 'Adam Wathan'
    ]));
});
```

