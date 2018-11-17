# Coding style

This is the basic gist of this coding style

```php
<?php declare(strict_types=1);

namespace App\Model;

class Person implements \App\Model\Entity
{

    public const GENDER_MALE = 0,
        GENDER_FEMALE = 1;

    /**
     * @var string
     */
    private $name;

    /**
     * @var \App\Model\Task[]
     */
    private $tasks;

    public function __construct(string $name)
    {
        if (strlen($name) <= 3) {
            throw new \App\Exception\NotLongEnough($name);
        }
        $this->name = $name;
    }

    /**
     * @return \App\Model\Task[]
     */
    public function getTasks(): array
    {
        return $this->tasks;
    }

    public function addTask(Task $task): void
    {
        $this->tasks[] = $task;
    }

    public function getName(): string
    {
        return $this->name;
    }

}

```