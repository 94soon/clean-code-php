# Clean Code PHP - 한글판

## 목차

  1. [들어가며](#들어가며)
  2. [변수](#변수)
     * [의미있고 발음하기 쉬운 변수명을 사용하세요](#의미있고-발음하기-쉬운-변수명을-사용하세요)
     * [같은 타입의 변수에는 동일한 어휘를 사용하세요](#같은-타입의-변수에는-동일한-어휘를-사용하세요)
     * [찾기 쉬운 이름을 사용하세요 (part 1)](#찾기-쉬운-이름을-사용하세요-part-1)
     * [찾기 쉬운 이름을 사용하세요 (part 2)](#찾기-쉬운-이름을-사용하세요-part-2)
     * [설명적인 변수를 사용하세요](#설명적인-변수를-사용하세요)
     * [너무 깊은 중첩은 피하고 초기에 return 하세요 (part 1)](#너무-깊은-중첩은-피하고-초기에-return-하세요-part-1)
     * [너무 깊은 중첩은 피하고 초기에 return 하세요 (part 2)](#너무-깊은-중첩은-피하고-초기에-return-하세요-part-2)
     * [머릿속으로 짐작하게 하지 마세요](#머릿속으로-짐작하게-하지-마세요)
     * [불필요한 문맥을 덧붙이지 마세요](#불필요한-문맥을-덧붙이지-마세요)
     * [단락이나 조건문 대신 기본 인수를 사용하세요](#단락이나-조건문-대신-기본-인수를-사용하세요)
  3. [비교 연산자](#비교-연산자)
     * [동일 비교 연산자를 사용하세요](#동일-비교-연산자를-사용하세요)
  4. [함수](#함수)
     * [함수 인수 (2개 이하가 이상적)](#함수-인수-2개-이하가-이상적)
     * [함수는 한가지만 해야합니다](#함수는-한가지만-해야합니다)
     * [함수명은 어떤 일을 하는지 나타내야 합니다](#함수명은-어떤-일을-하는지-나타내야-합니다)
     * [함수는 추상화 레벨이 단 하나여야 합니다](#함수는-추상화-레벨이-단-하나여야-합니다)
     * [플래그를 함수의 매개변수로 사용하지 마세요](#플래그를-함수의-매개변수로-사용하지-마세요)
     * [부작용을 피하세요](#부작용을-피하세요)
     * [전역 함수를 사용하지 마세요](#전역-함수를-사용하지-마세요)
     * [싱글턴 패턴을 사용하지 마세요](#싱글턴-패턴을-사용하지-마세요)
     * [조건문은 캡슐화하세요](#조건문은-캡슐화하세요)
     * [부정 조건문을 피하세요](#부정-조건문을-피하세요)
     * [조건문을 피하세요](#조건문을-피하세요)
     * [타입 체킹을 피하세요 (part 1)](#타입-체킹을-피하세요-part-1)
     * [타입 체킹을 피하세요 (part 2)](#타입-체킹을-피하세요-part-2)
     * [불필요한 코드는 제거하세요](#불필요한-코드는-제거하세요)
  5. [객체와 자료구조](#객체와-자료구조)
     * [객체 캡슐화를 사용하세요](#객체-캡슐화를-사용하세요)
     * [객체가 private/protected 멤버를 갖게 하세요](#객체가-privateprotected-멤버를-갖게-하세요)
  6. [클래스](#클래스)
     * [상속보다는 컴포지션을 사용하세요](#상속보다는-컴포지션을-사용하세요)
     * [유창한 인터페이스를 피하세요](#유창한-인터페이스를-피하세요)
  7. [SOLID](#solid)
     * [단일 책임 원칙 (SRP)](#단일-책임-원칙-srp)
     * [개방/폐쇄 원칙 (OCP)](#개방폐쇄-원칙-ocp)
     * [리스코브 치환 원칙 (LSP)](#리스코브-치환-원칙-lsp)
     * [인터페이스 분리 원칙 (ISP)](#인터페이스-분리-원칙-isp)
     * [의존성 역전 원칙 (DIP)](#의존성-역전-원칙-dip)
  8. [반복하지 마세요 (DRY)](#반복하지-마세요-dry)
  9. [번역](#번역)

## 들어가며


Robert C. Martin의 책, 소프트웨어 엔지니어링의 교과서라고 불리는[*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) PHP 버전입니다.
이 문서는 스타일 가이드가 아닙니다. PHP로 읽기 쉽고 재사용 가능하며, 리팩토링이 쉬운 소프트웨어를 만들어내기 위한 안내서입니다.

문서의 모든 원칙을 엄격하게 지켜야 할 필요는 없습니다. 그리고 어떤 것들은 일반적으로 합의되지 못할 것입니다.
이 문서는 안내서일 뿐이고 그 이상이 될 순 없지만, 수년간 *Clean Code*의 저자들로부터 축적된 경험을 문서화 한 것입니다.

[clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript)에 영감을 받아 작성되었습니다.

여전히 PHP 5를 사용하는 개발자가 많겠지만, 문서의 예제 대부분은 PHP 7.1 이상의 버전에서만 작동합니다.

## 변수

### 의미있고 발음하기 쉬운 변수명을 사용하세요

**나쁜 예:**

```php
$ymdstr = $moment->format('y-m-d');
```

**좋은 예:**

```php
$currentDate = $moment->format('y-m-d');
```

**[⬆ 위로 가기](#목차)**

### 같은 타입의 변수에는 동일한 어휘를 사용하세요

**나쁜 예:**

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

**좋은 예:**

```php
getUser();
```

**[⬆ 위로 가기](#목차)**

### 찾기 쉬운 이름을 사용하세요 (part 1)

작성해야 할 코드보다 읽어야 할 코드가 더 많습니다. 우리가 작성해야 할 코드를 읽기 쉽고 찾기 쉽게 만드는 것은 중요합니다.
프로그램을 이해하기 쉽도록 변수명을 의미 있게 짓지 *않는*다면, 코드를 읽는 사람을 곤란하게 만드는 것입니다.
변수명을 찾기 쉽게 만드세요.


**나쁜 예:**

```php
// 도대체 448이 뭔 뜻이래요?
$result = $serializer->serialize($data, 448);
```

**좋은 예:**

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

### 찾기 쉬운 이름을 사용하세요 (part 2)

**나쁜 예:**

```php
// 4는 무슨 의미인가요?
if ($user->access & 4) {
    // ...
}
```

**좋은 예:**

```php
class User
{
    const ACCESS_READ = 1;
    const ACCESS_CREATE = 2;
    const ACCESS_UPDATE = 4;
    const ACCESS_DELETE = 8;
}

if ($user->access & User::ACCESS_UPDATE) {
    // do edit ...
}
```

**[⬆ 위로 가기](#목차)**

### 설명적인 변수를 사용하세요

**나쁜 예:**

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```

**나쁘진 않은 예:**

조금 낫군요. 하지만, 여전히 regex에 아주 많이 의존하고 있습니다.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

**좋은 예:**

naming subpattern을 사용해서 regex의 의존성을 줄입시다.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```

**[⬆ 위로 가기](#목차)**

### 너무 깊은 중첩은 피하고 초기에 return 하세요 (part 1)

너무 많은 if else 문은 코드를 따라가기 어렵게 만들 수 있습니다. 명료한 것이 암시하는 것보다 나아요.


**나쁜 예:**

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    } else {
        return false;
    }
}
```

**좋은 예:**

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = [
        'friday', 'saturday', 'sunday'
    ];

    return in_array(strtolower($day), $openingDays, true);
}
```

**[⬆ 위로 가기](#목차)**

### 너무 깊은 중첩은 피하고 초기에 return 하세요 (part 2)

**나쁜 예:**

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            } else {
                return 1;
            }
        } else {
            return 0;
        }
    } else {
        return 'Not supported';
    }
}
```

**좋은 예:**

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n > 50) {
        throw new \Exception('Not supported');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```

**[⬆ 위로 가기](#목차)**

### 머릿속으로 짐작하게 하지 마세요

우리의 코드를 읽는 사람이 변수가 어떤 의미인지 해석하게 하지 마세요.
명료한 것이 암시하는 것보다 좋아요.

**나쁜 예:**

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // 잠깐 $li가 뭐였죠?
    dispatch($li);
}
```

**좋은 예:**

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```

**[⬆ 위로 가기](#목차)**

### 불필요한 문맥을 덧붙이지 마세요

클래스/객체 명이 이미 말해주고 있다면, 변수명에 굳이 번복하지 마세요.

**나쁜 예:**

```php
class Car
{
    public $carMake;
    public $carModel;
    public $carColor;

    //...
}
```

**좋은 예:**

```php
class Car
{
    public $make;
    public $model;
    public $color;

    //...
}
```

**[⬆ 위로 가기](#목차)**

### 단락이나 조건문 대신 기본 인수를 사용하세요

**좋진 않은 예:**

아래 예제는 `$breweryName`이 `NULL`이 될 수 있으므로 좋지 않아요.

```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**나쁘진 않은 예:**

위의 예제보다 훨씬 이해하기 쉬워졌습니다. 하지만 변수의 값을 제어하는 게 낫겠습니다.

```php
function createMicrobrewery($name = null): void
{
    $breweryName = $name ?: 'Hipster Brew Co.';
    // ...
}
```

**좋은 예:**

[type hinting](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)을 사용해서 `$breweryName`이 `NULL`이 될 수 없음을 확신할 수 있습니다.

```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**[⬆ 위로 가기](#목차)**

## 비교 연산자

**[⬆ 위로 가기](#목차)**

### [동일 비교 연산자](http://php.net/manual/en/language.operators.comparison.php)를 사용하세요

**좋진 않은 예:**

```php
$a = '42';
$b = 42;
단순한 비교 연산자를 사용하면 string이 int로 변환 될 것입니다.

if( $a != $b ) {
   //이 표현식은 항상 건너 뛸 것입니다.
}

```
$a != $b는 false를 리턴하지만 사실은 true가 맞아요!
string '42'는 int 42와 다릅니다.

**좋은 예:**
동일 비교 연산자를 사용하면 자료형과 값을 비교합니다.
```php
if( $a !== $b ) {
    //이 표현식은 확인되었습니다.
}

```
$a !== $b는 true를 return 합니다.

**[⬆ 위로 가기](#목차)**


## 함수

### 함수 인수 (2개 이하가 이상적)

함수 매개변수의 개수를 제한하는 것은 엄청나게 중요합니다. 함수를 테스트하는 것을 더 쉽게 만들어 주기 때문이죠. 3개 이상의 매개변수는 테스트 조합을 폭발하게 합니다. 매개변수마다 서로 다른 수많은 케이스를 테스트해야 하기 때문입니다.

매개변수가 없는 것(0개)이 가장 이상적입니다. 1개에서 2개 정도는 괜찮습니다. 3개는 피해야 합니다. 매개변수가 3개를 넘어가면 통합되어야 합니다. 일반적으로, 매개변수가 2개 이상이라면 그 함수는 너무 많은 역할을 하는 것입니다. 그런 경우가 아니라면, 고수준의 객체는 대부분 하나의 매개변수로 충분할 것입니다.

**나쁜 예:**

```php
function createMenu(string $title, string $body, string $buttonText, bool $cancellable): void
{
    // ...
}
```

**좋은 예:**

```php
class MenuConfig
{
    public $title;
    public $body;
    public $buttonText;
    public $cancellable = false;
}

$config = new MenuConfig();
$config->title = 'Foo';
$config->body = 'Bar';
$config->buttonText = 'Baz';
$config->cancellable = true;

function createMenu(MenuConfig $config): void
{
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 함수는 한가지만 해야합니다

소프트웨어 엔지니어링에서 가장 중요한 규칙입니다. 함수가 1개 이상의 역할을 하게되면, 작성, 테스트, 추론하기가 어려워집니다.
함수를 단 하나의 행동으로 떼어낼 수 있다면, 코드는 쉽게 리팩토링 될 수 있으며 훨씬 더 깔끔하게 읽힐 것입니다.
이 문서에서 나머지는 다 갖다 버리고 이것만 지키신대도 웬만한 개발자 보다 앞서게 될 것 입니다.

**나쁜 예:**
```php
function emailClients(array $clients): void
{
    foreach ($clients as $client) {
        $clientRecord = $db->find($client);
        if ($clientRecord->isActive()) {
            email($client);
        }
    }
}
```

**좋은 예:**

```php
function emailClients(array $clients): void
{
    $activeClients = activeClients($clients);
    array_walk($activeClients, 'email');
}

function activeClients(array $clients): array
{
    return array_filter($clients, 'isClientActive');
}

function isClientActive(int $client): bool
{
    $clientRecord = $db->find($client);

    return $clientRecord->isActive();
}
```

**[⬆ 위로 가기](#목차)**

### 함수명은 어떤 일을 하는지 나타내야 합니다.

**나쁜 예:**

```php
class Email
{
    //...

    public function handle(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// 이게 뭘까요? 메세지를 위한 핸들? 지금 우리가 파일을 작성할건가요?
$message->handle();
```

**좋은 예:**

```php
class Email
{
    //...

    public function send(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// 분명하고 명백하군요
$message->send();
```

**[⬆ 위로 가기](#목차)**

### 함수는 추상화 레벨이 단 하나여야 합니다

추상화 레벨이 하나 이상이라면, 보통 우리의 함수는 너무 많은 일을 하고 있는 것입니다. 함수를 분리하면 재사용성을 높일 수 있고 테스트가 용이해집니다.

**나쁜 예:**

```php
function parseBetterJSAlternative(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    $ast = [];
    foreach ($tokens as $token) {
        // lex...
    }

    foreach ($ast as $node) {
        // parse...
    }
}
```

**여전히 나쁜 예:**

기능의 일부를 옮겼지만, `parseBetterJSAlternative()` 함수는 여전히 너무 복잡하고 테스트할 수 없습니다.

```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): array
{
    $ast = [];
    foreach ($tokens as $token) {
        $ast[] = /* ... */;
    }

    return $ast;
}

function parseBetterJSAlternative(string $code): void
{
    $tokens = tokenize($code);
    $ast = lexer($tokens);
    foreach ($ast as $node) {
        // parse...
    }
}
```

**좋은 예:**

가장 좋은 해결책은 `parseBetterJSAlternative()` 함수의 의존성을 제거하는 것 입니다.

```php
class Tokenizer
{
    public function tokenize(string $code): array
    {
        $regexes = [
            // ...
        ];

        $statements = explode(' ', $code);
        $tokens = [];
        foreach ($regexes as $regex) {
            foreach ($statements as $statement) {
                $tokens[] = /* ... */;
            }
        }

        return $tokens;
    }
}

class Lexer
{
    public function lexify(array $tokens): array
    {
        $ast = [];
        foreach ($tokens as $token) {
            $ast[] = /* ... */;
        }

        return $ast;
    }
}

class BetterJSAlternative
{
    private $tokenizer;
    private $lexer;

    public function __construct(Tokenizer $tokenizer, Lexer $lexer)
    {
        $this->tokenizer = $tokenizer;
        $this->lexer = $lexer;
    }

    public function parse(string $code): void
    {
        $tokens = $this->tokenizer->tokenize($code);
        $ast = $this->lexer->lexify($tokens);
        foreach ($ast as $node) {
            // parse...
        }
    }
}
```

**[⬆ 위로 가기](#목차)**

### 플래그를 함수의 매개변수로 사용하지 마세요

플래그를 사용하는 것은 함수가 한가지 이상의 일을 할 것이라 말하는 셈입니다. 함수는 한 가지 일을 해야 합니다.
만약 Boolean 값에 따라 서로 다른 코드를 사용해야 한다면 함수를 분리하세요.

**나쁜 예:**

```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/'.$name);
    } else {
        touch($name);
    }
}
```

**좋은 예:**

```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/'.$name);
}
```

**[⬆ 위로 가기](#목차)**

### 부작용을 피하세요

A function produces a side effect if it does anything other than take a value in and
return another value or values. A side effect could be writing to a file, modifying
some global variable, or accidentally wiring all your money to a stranger.

Now, you do need to have side effects in a program on occasion. Like the previous
example, you might need to write to a file. What you want to do is to centralize where
you are doing this. Don't have several functions and classes that write to a particular
file. Have one service that does it. One and only one.

The main point is to avoid common pitfalls like sharing state between objects without
any structure, using mutable data types that can be written to by anything, and not
centralizing where your side effects occur. If you can do this, you will be happier
than the vast majority of other programmers.

**나쁜 예:**

```php
// Global variable referenced by following function.
// If we had another function that used this name, now it'd be an array and it could break it.
$name = 'Ryan McDermott';

function splitIntoFirstAndLastName(): void
{
    global $name;

    $name = explode(' ', $name);
}

splitIntoFirstAndLastName();

var_dump($name); // ['Ryan', 'McDermott'];
```

**좋은 예:**

```php
function splitIntoFirstAndLastName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitIntoFirstAndLastName($name);

var_dump($name); // 'Ryan McDermott';
var_dump($newName); // ['Ryan', 'McDermott'];
```

**[⬆ 위로 가기](#목차)**

### 전역 함수를 사용하지 마세요

Polluting globals is a bad practice in many languages because you could clash with another
library and the user of your API would be none-the-wiser until they get an exception in
production. Let's think about an example: what if you wanted to have configuration array.
You could write global function like `config()`, but it could clash with another library
that tried to do the same thing.

**나쁜 예:**

```php
function config(): array
{
    return  [
        'foo' => 'bar',
    ]
}
```

**좋은 예:**

```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        return isset($this->configuration[$key]) ? $this->configuration[$key] : null;
    }
}
```

Load configuration and create instance of `Configuration` class

```php
$configuration = new Configuration([
    'foo' => 'bar',
]);
```

And now you must use instance of `Configuration` in your application.

**[⬆ 위로 가기](#목차)**

### 싱글턴 패턴을 사용하지 마세요

Singleton is an [anti-pattern](https://en.wikipedia.org/wiki/Singleton_pattern). Paraphrased from Brian Button:
 1. They are generally used as a **global instance**, why is that so bad? Because **you hide the dependencies** of your application in your code, instead of exposing them through the interfaces. Making something global to avoid passing it around is a [code smell](https://en.wikipedia.org/wiki/Code_smell).
 2. They violate the [단일 책임 원칙](#단일-책임-원칙-srp): by virtue of the fact that **they control their own creation and lifecycle**.
 3. They inherently cause code to be tightly [coupled](https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29). This makes faking them out under **test rather difficult** in many cases.
 4. They carry state around for the lifetime of the application. Another hit to testing since **you can end up with a situation where tests need to be ordered** which is a big no for unit tests. Why? Because each unit test should be independent from the other.

There is also very good thoughts by [Misko Hevery](http://misko.hevery.com/about/) about the [root of problem](http://misko.hevery.com/2008/08/25/root-cause-of-singletons/).

**나쁜 예:**

```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): DBConnection
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

**좋은 예:**

```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

     // ...
}
```

Create instance of `DBConnection` class and configure it with [DSN](http://php.net/manual/en/pdo.construct.php#refsect1-pdo.construct-parameters).

```php
$connection = new DBConnection($dsn);
```

And now you must use instance of `DBConnection` in your application.

**[⬆ 위로 가기](#목차)**

### 조건문은 캡슐화하세요

**나쁜 예:**

```php
if ($article->state === 'published') {
    // ...
}
```

**좋은 예:**

```php
if ($article->isPublished()) {
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 부정 조건문을 피하세요

**나쁜 예:**

```php
function isDOMNodeNotPresent(\DOMNode $node): bool
{
    // ...
}

if (!isDOMNodeNotPresent($node))
{
    // ...
}
```

**좋은 예:**

```php
function isDOMNodePresent(\DOMNode $node): bool
{
    // ...
}

if (isDOMNodePresent($node)) {
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 조건문을 피하세요

This seems like an impossible task. Upon first hearing this, most people say,
"how am I supposed to do anything without an `if` statement?" The answer is that
you can use polymorphism to achieve the same task in many cases. The second
question is usually, "well that's great but why would I want to do that?" The
answer is a previous clean code concept we learned: a function should only do
one thing. When you have classes and functions that have `if` statements, you
are telling your user that your function does more than one thing. Remember,
just do one thing.

**나쁜 예:**

```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

**좋은 예:**

```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```

**[⬆ 위로 가기](#목차)**

### 타입 체킹을 피하세요 (part 1)

PHP is untyped, which means your functions can take any type of argument.
Sometimes you are bitten by this freedom and it becomes tempting to do
type-checking in your functions. There are many ways to avoid having to do this.
The first thing to consider is consistent APIs.

**나쁜 예:**

```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedalTo(new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->driveTo(new Location('texas'));
    }
}
```

**좋은 예:**

```php
function travelToTexas(Traveler $vehicle): void
{
    $vehicle->travelTo(new Location('texas'));
}
```

**[⬆ 위로 가기](#목차)**

### 타입 체킹을 피하세요 (part 2)

If you are working with basic primitive values like strings, integers, and arrays,
and you use PHP 7+ and you can't use polymorphism but you still feel the need to
type-check, you should consider
[type declaration](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)
or strict mode. It provides you with static typing on top of standard PHP syntax.
The problem with manually type-checking is that doing it will require so much
extra verbiage that the faux "type-safety" you get doesn't make up for the lost
readability. Keep your PHP clean, write good tests, and have good code reviews.
Otherwise, do all of that but with PHP strict type declaration or strict mode.

**나쁜 예:**

```php
function combine($val1, $val2): int
{
    if (!is_numeric($val1) || !is_numeric($val2)) {
        throw new \Exception('Must be of type Number');
    }

    return $val1 + $val2;
}
```

**좋은 예:**

```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ 위로 가기](#목차)**

### 불필요한 코드는 제거하세요

Dead code is just as bad as duplicate code. There's no reason to keep it in
your codebase. If it's not being called, get rid of it! It will still be safe
in your version history if you still need it.

**나쁜 예:**

```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**좋은 예:**

```php
function requestModule(string $url): void
{
    // ...
}

$request = requestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**[⬆ 위로 가기](#목차)**


## 객체와 자료구조

### 객체 캡슐화를 사용하세요

In PHP you can set `public`, `protected` and `private` keywords for methods.
Using it, you can control properties modification on an object.

* When you want to do more beyond getting an object property, you don't have
to look up and change every accessor in your codebase.
* Makes adding validation simple when doing a `set`.
* Encapsulates the internal representation.
* Easy to add logging and error handling when getting and setting.
* Inheriting this class, you can override default functionality.
* You can lazy load your object's properties, let's say getting it from a
server.

Additionally, this is part of [Open/Closed](#개방폐쇄-원칙-ocp) principle.

**나쁜 예:**

```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->balance -= 100;
```

**좋은 예:**

```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
      $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Amount greater than available balance.');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->withdraw($shoesPrice);

// Get balance
$balance = $bankAccount->getBalance();
```

**[⬆ 위로 가기](#목차)**

### 객체가 private/protected 멤버를 갖게 하세요

* `public` methods and properties are most dangerous for changes, because some outside code may easily rely on them and you can't control what code relies on them. **Modifications in class are dangerous for all users of class.**
* `protected` modifier are as dangerous as public, because they are available in scope of any child class. This effectively means that difference between public and protected is only in access mechanism, but encapsulation guarantee remains the same. **Modifications in class are dangerous for all descendant classes.**
* `private` modifier guarantees that code is **dangerous to modify only in boundaries of single class** (you are safe for modifications and you won't have [Jenga effect](http://www.urbandictionary.com/define.php?term=Jengaphobia&defid=2494196)).

Therefore, use `private` by default and `public/protected` when you need to provide access for external classes.

For more informations you can read the [blog post](http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html) on this topic written by [Fabien Potencier](https://github.com/fabpot).

**나쁜 예:**

```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->name; // Employee name: John Doe
```

**좋은 예:**

```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->getName(); // Employee name: John Doe
```

**[⬆ 위로 가기](#목차)**

## 클래스

### 상속보다는 컴포지션을 사용하세요

As stated famously in [*Design Patterns*](https://en.wikipedia.org/wiki/Design_Patterns) by the Gang of Four,
you should prefer composition over inheritance where you can. There are lots of
good reasons to use inheritance and lots of good reasons to use composition.
The main point for this maxim is that if your mind instinctively goes for
inheritance, try to think if composition could model your problem better. In some
cases it can.

You might be wondering then, "when should I use inheritance?" It
depends on your problem at hand, but this is a decent list of when inheritance
makes more sense than composition:

1. Your inheritance represents an "is-a" relationship and not a "has-a"
relationship (Human->Animal vs. User->UserDetails).
2. You can reuse code from the base classes (Humans can move like all animals).
3. You want to make global changes to derived classes by changing a base class.
(Change the caloric expenditure of all animals when they move).

**나쁜 예:**

```php
class Employee
{
    private $name;
    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// Bad because Employees "have" tax data.
// EmployeeTaxData is not a type of Employee

class EmployeeTaxData extends Employee
{
    private $ssn;
    private $salary;

    public function __construct(string $name, string $email, string $ssn, string $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

**좋은 예:**

```php
class EmployeeTaxData
{
    private $ssn;
    private $salary;

    public function __construct(string $ssn, string $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee
{
    private $name;
    private $email;
    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(string $ssn, string $salary)
    {
        $this->taxData = new EmployeeTaxData($ssn, $salary);
    }

    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 유창한 인터페이스를 피하세요

A [Fluent interface](https://en.wikipedia.org/wiki/Fluent_interface) is an object
oriented API that aims to improve the readability of the source code by using
[Method chaining](https://en.wikipedia.org/wiki/Method_chaining).

While there can be some contexts, frequently builder objects, where this
pattern reduces the verbosity of the code (for example the [PHPUnit Mock Builder](https://phpunit.de/manual/current/en/test-doubles.html)
or the [Doctrine Query Builder](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html)),
more often it comes at some costs:

1. Breaks [Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_%28object-oriented_programming%29)
2. Breaks [Decorators](https://en.wikipedia.org/wiki/Decorator_pattern)
3. Is harder to [mock](https://en.wikipedia.org/wiki/Mock_object) in a test suite
4. Makes diffs of commits harder to read

For more informations you can read the full [blog post](https://ocramius.github.io/blog/fluent-interfaces-are-evil/)
on this topic written by [Marco Pivetta](https://github.com/Ocramius).

**나쁜 예:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): self
    {
        $this->make = $make;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
  ->setColor('pink')
  ->setMake('Ford')
  ->setModel('F-150')
  ->dump();
```

**좋은 예:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): void
    {
        $this->make = $make;
    }

    public function setModel(string $model): void
    {
        $this->model = $model;
    }

    public function setColor(string $color): void
    {
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car();
$car->setColor('pink');
$car->setMake('Ford');
$car->setModel('F-150');
$car->dump();
```

**[⬆ 위로 가기](#목차)**

## SOLID

**SOLID** is the mnemonic acronym introduced by Michael Feathers for the first five principles named by Robert Martin, which meant five basic principles of object-oriented programming and design.

 * [S: 단일 책임 원칙 (SRP)](#단일-책임-원칙-srp)
 * [O: 개방/폐쇄 원칙 (OCP)](#개방폐쇄-원칙-ocp)
 * [L: 리스코브 치환 원칙 (LSP)](#리스코브-치환-원칙-lsp)
 * [I: 인터페이스 분리 원칙 (ISP)](#인터페이스-분리-원칙-isp)
 * [D: 의존성 역전 원칙 (DIP)](#의존성-역전-원칙-dip)

### 단일 책임 원칙 (SRP)

As stated in Clean Code, "There should never be more than one reason for a class
to change". It's tempting to jam-pack a class with a lot of functionality, like
when you can only take one suitcase on your flight. The issue with this is
that your class won't be conceptually cohesive and it will give it many reasons
to change. Minimizing the amount of times you need to change a class is important.
It's important because if too much functionality is in one class and you modify a piece of it,
it can be difficult to understand how that will affect other dependent modules in
your codebase.

**나쁜 예:**

```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

**좋은 예:**

```php
class UserAuth
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings
{
    private $user;
    private $auth;

    public function __construct(User $user)
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```

**[⬆ 위로 가기](#목차)**

### 개방/폐쇄 원칙 (OCP)

As stated by Bertrand Meyer, "software entities (classes, modules, functions,
etc.) should be open for extension, but closed for modification." What does that
mean though? This principle basically states that you should allow users to
add new functionalities without changing existing code.

**나쁜 예:**

```php
abstract class Adapter
{
    protected $name;

    public function getName(): string
    {
        return $this->name;
    }
}

class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        $adapterName = $this->adapter->getName();

        if ($adapterName === 'ajaxAdapter') {
            return $this->makeAjaxCall($url);
        } elseif ($adapterName === 'httpNodeAdapter') {
            return $this->makeHttpCall($url);
        }
    }

    private function makeAjaxCall(string $url): Promise
    {
        // request and return promise
    }

    private function makeHttpCall(string $url): Promise
    {
        // request and return promise
    }
}
```

**좋은 예:**

```php
interface Adapter
{
    public function request(string $url): Promise;
}

class AjaxAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        return $this->adapter->request($url);
    }
}
```

**[⬆ 위로 가기](#목차)**

### 리스코브 치환 원칙 (LSP)

This is a scary term for a very simple concept. It's formally defined as "If S
is a subtype of T, then objects of type T may be replaced with objects of type S
(i.e., objects of type S may substitute objects of type T) without altering any
of the desirable properties of that program (correctness, task performed,
etc.)." That's an even scarier definition.

The best explanation for this is if you have a parent class and a child class,
then the base class and child class can be used interchangeably without getting
incorrect results. This might still be confusing, so let's take a look at the
classic Square-Rectangle example. Mathematically, a square is a rectangle, but
if you model it using the "is-a" relationship via inheritance, you quickly
get into trouble.

**나쁜 예:**

```php
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function render(int $area): void
    {
        // ...
    }

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $rectangle->setWidth(4);
        $rectangle->setHeight(5);
        $area = $rectangle->getArea(); // BAD: Will return 25 for Square. Should be 20.
        $rectangle->render($area);
    }
}

$rectangles = [new Rectangle(), new Rectangle(), new Square()];
renderLargeRectangles($rectangles);
```

**좋은 예:**

```php
abstract class Shape
{
    abstract public function getArea(): int;

    public function render(int $area): void
    {
        // ...
    }
}

class Rectangle extends Shape
{
    private $width;
    private $height;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Shape
{
    private $length;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return pow($this->length, 2);
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $area = $rectangle->getArea();
        $rectangle->render($area);
    }
}

$shapes = [new Rectangle(4, 5), new Rectangle(4, 5), new Square(5)];
renderLargeRectangles($shapes);
```

**[⬆ 위로 가기](#목차)**

### 인터페이스 분리 원칙 (ISP)

ISP states that "Clients should not be forced to depend upon interfaces that
they do not use."

A good example to look at that demonstrates this principle is for
classes that require large settings objects. Not requiring clients to setup
huge amounts of options is beneficial, because most of the time they won't need
all of the settings. Making them optional helps prevent having a "fat interface".

**나쁜 예:**

```php
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        // ...... eating in lunch break
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }

    public function eat(): void
    {
        //.... robot can't eat, but it must implement this method
    }
}
```

**좋은 예:**

Not every worker is an employee, but every employee is a worker.

```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        //.... eating in lunch break
    }
}

// robot can only work
class Robot implements Workable
{
    public function work(): void
    {
        // ....working
    }
}
```

**[⬆ 위로 가기](#목차)**

### 의존성 역전 원칙 (DIP)

This principle states two essential things:
1. High-level modules should not depend on low-level modules. Both should
depend on abstractions.
2. Abstractions should not depend upon details. Details should depend on
abstractions.

This can be hard to understand at first, but if you've worked with PHP frameworks (like Symfony), you've seen an implementation of this principle in the form of Dependency
Injection (DI). While they are not identical concepts, DIP keeps high-level
modules from knowing the details of its low-level modules and setting them up.
It can accomplish this through DI. A huge benefit of this is that it reduces
the coupling between modules. Coupling is a very bad development pattern because
it makes your code hard to refactor.

**나쁜 예:**

```php
class Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**좋은 예:**

```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**[⬆ 위로 가기](#목차)**

## 반복하지 마세요 (DRY)

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) 원칙을 지키도록 노력하세요.

중복코드를 피하고자 정말 최선을 다하세요. 중복된 코드는 나쁩니다. 만약 우리가 어떤 로직을 변경해야 할 때 고칠 곳이 한 곳 이상이라는 것을 뜻하기 때문이죠.

우리가 레스토랑을 운영하고 있다고 상상해보세요. 그리고 재고(토마토, 양파, 마늘, 양념 등등)를 기록하고 있다고요.
만약 우리가 이걸 기록하는 여러 개의 목록을 가지고 있다면, 토마토가 들어간 요리를 서빙할 때마다 모든 목록을 수정해야 할 겁니다.
만약 단 하나의 목록만 가지고 있다면, 수정할 곳은 단 한 곳뿐이겠지요!

종종 우리는 중복된 코드를 가집니다. 사소하게 다른 두어 개 때문인데, 많은 부분을 같이 공유하지만, 그 사소한 차이점이
거의 같은 일을 하는 두 개 이상의 서로 다른 함수를 만들어내게 합니다. 중복된 코드를 제거하는 것은 단 하나의 함수/모듈/클래스로 서로 다른 세트를 핸들 할 수 있는 추상화를 생성하는 것을 뜻합니다.

올바른 추상화를 갖는 것은 중요합니다. 그것이 [클래스](#클래스) 섹션에 있는 SOLID 원칙을 따라야 하는 이유입니다.
나쁜 추상화는 중복된 코드보다 나쁠 수 있습니다. 그러니 조심하세요!
지금껏 말했듯이, 좋은 추상화를 만들 수 있다면 그렇게 하세요!
같은 것을 반복 하지 마세요, 그렇지 않으면 하나를 바꾸려 할 때마다 여러 군데를 수정하고 있는 우리 자신을 발견하게 될 테니까요..

**나쁜 예:**

```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**좋은 예:**

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        $expectedSalary = $employee->calculateExpectedSalary();
        $experience = $employee->getExperience();
        $githubLink = $employee->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**아주 좋은 예:**

더 간결한 코드를 사용하는게 나은 것 같군요.

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([
            $employee->calculateExpectedSalary(),
            $employee->getExperience(),
            $employee->getGithubLink()
        ]);
    }
}
```

**[⬆ 위로 가기](#목차)**

## 번역

다른 언어로도 읽으실 수 있습니다.

* :cn: **중국어:**
   * [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
* :ru: **러시아어:**
   * [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
* :es: **스페인어:**
   * [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
* :brazil: **포르투갈어:**
   * [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
   * [jeanjar/clean-code-php](https://github.com/jeanjar/clean-code-php/tree/pt-br)
* :thailand: **태국어:**
   * [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
* :fr: **불어:**
   * [errorname/clean-code-php](https://github.com/errorname/clean-code-php)
* :ko: **한국어:**
  * [yujineeee/clean-code-php](https://github.com/yujineeee/clean-code-php)


**[⬆ 위로 가기](#목차)**
