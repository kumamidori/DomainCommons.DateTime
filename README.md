# [WIP] Dommain Commons "DateTime" 

# Installation

```
$ composer require kumamidori/domain-commons-datetime
```

# Features

## DateTime basics

### Date and Time

- Date
- DateTime
- MonthDay
- Year
- YearMonth
- HourMin
- AgeRange

### Period

- Duration
- Period
- Term

#### Traversable

- DailyTrait / DailyIteratableInterface
- MonthlyTrait / MonthlyIteratableInterface

You can define a domain specific period as follows:

```php
namespace MyDomain;

use PHPMentors\DomainCommons\DateTime\Date;
use PHPMentors\DomainCommons\DateTime\Period\DailyIteratableInterface;
use PHPMentors\DomainCommons\DateTime\Period\DailyTrait;

class DailyPeriod extends Period implements DailyIteratableInterface
{
    use DailyTrait;

    public function __construct(Date $start, Date $end)
    {
        parent::__construct($start, $end);
        $this->it = $this->iterate(); // this line enables iterator
    }
}
```

You can iterate this period by date using standard `foreach` statement as follows:

```
use PHPMentors\DomainCommons\DateTime\Date;
use MyDomain\DailyPeriod;

$period = new DailyPeriod(new Date('2015-04-12'), new Date('2015-06-30'));

$count = 0;
foreach ($period as $one) {
    echo $one->format('m/d') . PHP_EOL;
}
```

### Utility

- Clock

# Copyright

Copyright (c) 2015 GOTO Hidenori, 2015 KUBO Atsuhiro, All rights reserved.

# License

[The BSD 2-Clause License](http://opensource.org/licenses/BSD-2-Clause)
