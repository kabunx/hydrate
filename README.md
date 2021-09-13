## hydrate

### 注解处理字段映射问题

属性会通过定义的数据类型，自动转换

#### 版本

```
php: ^8.0
```

## 如何安装

```shell
$ composer require kabunx/hydrate -vvv
```

## 定义Entity

```php
<?php
declare(strict_types=1);

namespace App\Entities;

use Carbon\Carbon;
use Kabunx\Hydrate\Annotations\Source;
use Kabunx\Hydrate\Entity;
use Kabunx\Hydrate\Source;

/**
 * Class UserEntity
 * @package App\Entities
 */
class UserEntity extends Entity
{

    /**
     * @var string
     */
    public string $name = '';

    public string $email = '';

    /**
     * @var int
     */
    public int $gender = 0;

    /**
     * @var string
     */
    public string $birthday = '';

    /**
     * @var string
     */
    public Carbon $createdAt = '';

    /**
     * @var string
     */
     #[Source("modifiedAt")]
    public Carbon $updatedAt = '';


    /**
     * @param string $value
     * @return int
     */
    public function setGender(string $value): int
    {
        return $value == 'm' ? 0 : 1;
    }
}
```

### 使用

```php
<?php
use App\Entities\UserEntity;

$users = [
    'id' => 1,
    'name' => 'test01',
    'email' => 'test01@sp.local',
    'gender' => 'm',
    'birthday' => '2000-10-01',
    'createdAt' => '2021-07-23',
    'modifiedAt' => '2021-07-23 12:05:10'
];

UserEntity::instance($users);

```

### 输出为

```shell

```
