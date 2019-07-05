# Обертка для работы с агентами Битрикс

За основу был взять функционал для работы с агентами из console-jedi

## Установка

```bash
composer require webpractik/agent
```

## Примеры

##### Регистрация агента
Проверяет, существует ли в БД агент. Если нет, то регистрирует его.

```php
use Webpractik\Agent\AgentTask;
use Vendor\Module\TestAgent;
use Bitrix\Main\Type\DateTime;

AgentTask::build()
    ->setClass(TestAgent::class)
    ->setCallChain(
        ['execute' => [$params]]
    )
    ->setModule('vendor.module')
    ->setExecutionTime(DateTime::createFromTimestamp(time() + 60)) // optional
    ->setUserId(1) // optional
    ->create();
```

#### Пример метода

```php
namespace Vendor\Module;

class TestAgent
{
    use AgentTrait;

    public function execute()
    {
        // some code

        return $this->getAgentName(['execute' => []]); // метод обязательно должен вернуть имя агента
    }
}

``` 
