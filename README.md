# Doctrine TinyInt

Add list of type for doctrine (metapackage)

## Installation:

```shell
composer require gollumsf/doctrine-type
```

## Configuration:

```yaml
doctrine:
    dbal:
        types:
            tinyint:  GollumSF\Doctrine\TinyInt # Add TINYINT type
            array_pipe:  GollumSF\Doctrine\ArrayPipe # Add array pipe transformer [ 'VAL1', 'VAL2' ] => 'VAL1|VAL2'
            enum:  GollumSF\Doctrine\ArrayPipe # Add ENUM type
```

## Usage:


```php
namespace App\Entity;

use GollumSF\Enum\Enum;
use Doctrine\ORM\Mapping as ORM;

class MyEnum extends Enum {
	const VALUE1 = 'VALUE1';
	const VALUE2 = 'VALUE2';
	const VALUE3 = 'VALUE3';
}

/**
 * @ORM\Table()
 */
class Entity {
	
	/**
	 * @ORM\Column(type="tinyint")
	 * @var int
	 */
	private $tinyint;
	
	/**
	 * @ORM\Column(type="array_pipe")
	 * @var int
	 */
	private $arrayPipe = [
		'ROLE_EXAMPLE', 'ROLE_USER', 'ROLE_ADMIN'
	];
	// Storage data in database with value: ROLE_EXAMPLE|ROLE_USER|ROLE_ADMIN
	
	/**
	 * @ORM\Column(type="enum", options={"enum"=MyEnum::class})
	 * @var int
	 */
	private $enum;
	
	/////////
	// ... //
	/////////
	
}
```

## Single packages:

 - https://github.com/GollumSF/doctrine-tinyint
 - https://github.com/GollumSF/doctrine-arraypipe
 - https://github.com/GollumSF/doctrine-enum