# C#에서 정수 및 부동 소수점 숫자를 사용하는 방법

## 목차
- [C#에서 정수 및 부동 소수점 숫자를 사용하는 방법](#c에서-정수-및-부동-소수점-숫자를-사용하는-방법)
  - [목차](#목차)
  - [정수 계산 살펴보기](#정수-계산-살펴보기)
  - [연산 순서 알아보기](#연산-순서-알아보기)
  - [정수 전체 자릿수 및 한도 살펴보기](#정수-전체-자릿수-및-한도-살펴보기)
  - [double 형식 작업](#double-형식-작업)
    - [과제](#과제)
  - [10진 형식으로 작업](#10진-형식으로-작업)
    - [과제](#과제-1)
  - [출처](#출처)

---
## 정수 계산 살펴보기

numbers-quickstart라는 디렉터리를 만듭니다. 현재 디렉터리로 만들고 다음 명령을 실행합니다.

```bash
dotnet new console -n NumbersInCSharp -o .
```

```
!중요!

.NET 6 용 C# 템플릿은 ‘최상위 문’을 사용합니다. .NET 6으로 이미 업그레이드한 경우 애플리케이션이 이 문서의 코드와 일치하지 않을 수 있습니다. 자세한 내용은 최상위 문을 생성하는 새 C# 템플릿을 참조하세요.

.NET 6 SDK는 다음 SDK를 사용하는 프로젝트에 대한 암시적global using 지시문 집합도 추가합니다.

Microsoft.NET.Sdk
Microsoft.NET.Sdk.Web
Microsoft.NET.Sdk.Worker

이러한 암시적 global using 지시문에는 해당 프로젝트 형식의 가장 일반적인 네임스페이스가 포함됩니다.

자세한 내용은 암시적 using 지시문 문서를 참조하세요.
```

원하는 편집기에서 Program.cs를 열고 파일의 콘텐츠를 다음 코드로 바꿉니다.

```C#
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

명령 창에 dotnet run을 입력하여 이 코드를 실행합니다.

정수를 사용하는 기본 수학 연산 중 하나를 살펴봤습니다. int 형식은 정수(0, 양의 정수 또는 음의 정수)를 나타냅니다. 더하기의 경우 + 기호를 사용합니다. 정수에 대해 다른 일반적인 수학 연산은 다음과 같습니다.

 - 빼기의 경우 -
 - 곱하기의 경우 *
 - 나누기의 경우 /

다른 연산을 살펴보세요. c의 값을 쓰는 줄 뒤에 다음 줄을 추가합니다.

```C#
// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

명령 창에 dotnet run을 입력하여 이 코드를 실행합니다.

원하는 경우 동일한 줄에서 여러 수학 연산을 작성하여 실험할 수도 있습니다. 예를 들어 c = a + b - 12 * 17;을 사용해 보세요. 변수와 상수를 혼합해서 사용할 수 있습니다.

```
팁

C# (또는 다른 프로그래밍 언어)를 살펴보면서 코드를 작성할 때 실수를 하게 될 것입니다. 컴파일러는 그러한 오류를 찾아 사용자에게 보고합니다. 출력에 오류 메시지가 포함되어 있으면 예제 코드와 창의 코드를 자세히 살펴보고 수정 사항을 확인하세요. 이 연습은 C# 코드의 구조를 학습하는 데 도움이 됩니다.
```

첫 번째 단계를 완료했습니다. 다음 섹션을 시작하기 전에 현재 코드를 별도의 메서드로 이동합니다. 메서드는 함께 그룹화되고 이름이 지정된 일련의 문입니다. 메서드 이름 뒤에 ()를 써서 메서드를 호출합니다. 코드를 메서드로 구성하면 새 예제 작업을 쉽게 시작할 수 있습니다. 작업을 마치면 코드가 다음과 같이 됩니다.

```C#
WorkWithIntegers();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}
```

줄 WorkWithIntegers();는 메서드를 호출합니다. 다음 코드는 메서드를 선언하고 정의합니다.

---
## 연산 순서 알아보기

WorkingWithIntegers()에 대한 호출을 주석으로 처리합니다. 그러면 이 섹션에서 작업할 때 출력이 덜 복잡해집니다.

```C#
//WorkWithIntegers();
```

//는 C#에서 주석을 시작합니다. 주석은 소스 코드에 유지하되 코드로 실행하지는 않으려는 모든 텍스트입니다. 컴파일러는 주석에서 실행 코드를 생성하지 않습니다. WorkWithIntegers()는 메서드이므로 한 줄만 주석으로 처리해야 합니다.

C# 언어는 수학에서 배운 규칙과 일치하는 규칙으로 여러 가지 수학 연산의 우선 순위를 정의합니다. 곱하기와 나누기는 더하기와 빼기보다 우선 순위가 높습니다. 다음 코드를 WorkWithIntegers() 호출 뒤에 추가하고 dotnet run을 실행하여 살펴봅니다.

```C#
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
```

출력에서는 곱하기가 수행된 후 더하기가 수행되었음을 보여 줍니다.

먼저 수행하려는 연산 주위에 괄호를 추가하여 다른 연산 순서를 적용할 수 있습니다. 다음 줄을 추가하고 다시 실행합니다.

```C#
d = (a + b) * c;
Console.WriteLine(d);
```

여러 다른 연산을 결합하여 자세히 살펴보세요. 다음과 같은 줄을 추가합니다. dotnet run을 다시 시도해 봅니다.

```C#
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

정수에 대해 흥미로운 동작을 이미 알고 있을 수 있습니다. 정수 나누기는 결과에 소수 또는 소수 부분이 포함될 것으로 예상되는 경우에도 항상 정수 결과를 생성합니다.

이러한 동작을 본 적이 없다면 다음 코드를 시도해 보세요.

```C#
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

dotnet run을 다시 입력하여 결과를 확인합니다.

넘어가기 전에 이 섹션에서 작성한 모든 코드를 새 메서드에 배치해 보겠습니다. 이러한 새 메서드의 이름을 OrderPrecedence라고 하겠습니다. 코드는 다음과 비슷합니다.

```C#
// WorkWithIntegers();
OrderPrecedence();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
    int c = a + b;
    Console.WriteLine(c);


    // subtraction
    c = a - b;
    Console.WriteLine(c);

    // multiplication
    c = a * b;
    Console.WriteLine(c);

    // division
    c = a / b;
    Console.WriteLine(c);
}

void OrderPrecedence()
{
    int a = 5;
    int b = 4;
    int c = 2;
    int d = a + b * c;
    Console.WriteLine(d);

    d = (a + b) * c;
    Console.WriteLine(d);

    d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
    Console.WriteLine(d);

    int e = 7;
    int f = 4;
    int g = 3;
    int h = (e + f) / g;
    Console.WriteLine(h);
}
```

---
## 정수 전체 자릿수 및 한도 살펴보기

마지막 샘플에서는 정수 나누기가 결과를 자르는 것을 보여 줍니다. modulo 연산자(% 문자)를 사용하여 나머지를 얻을 수 있습니다. OrderPrecedence() 메서드 호출 뒤에 다음 코드를 시도합니다.

```C#
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# 정수 형식은 한 가지 다른 면에서 수학의 정수와 다릅니다. 즉 int 형식에는 최소 한도와 최대 한도가 있습니다. 이 코드를 추가하여 해당 한도를 확인합니다.

```C#
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

계산이 해당 한도를 초과하는 값을 생성하는 경우 언더플로 또는 오버플로 조건이 발생합니다. 답은 한 한도에서 다른 한도로 래핑하는 것으로 나타납니다. 다음 두 줄을 추가하여 예제를 확인합니다.

```C#
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

답은 최소 (음의) 정수와 아주 가깝습니다. min + 2와 같습니다. 더하기 연산은 정수에 대해 허용된 값을 오버플로했습니다. 오버플로가 가능한 가장 큰 정수에서 가장 작은 정수로 “래핑”하기 때문에 답은 아주 큰 음수입니다.

int 형식이 요구 사항을 충족하지 않을 때 사용하는 여러 한도와 전체 자릿수가 있는 다른 숫자 형식이 있습니다. 다음으로 다른 형식을 살펴보겠습니다. 다음 섹션이 시작하기 전에 이 섹션에서 작성한 코드를 별도의 메서드로 옮깁니다. 이 EventHandler의 이름을 TestLimits로 지정합니다.

---
## double 형식 작업

double 숫자 형식은 배정밀도 부동 소수점 수를 나타냅니다. 이러한 용어는 생소할 수 있습니다. 부동 소수점 수는 아주 크거나 작은 정수가 아닌 수를 나타낼 때 유용합니다. 배정밀도는 값을 저장하는 데 사용되는 이진 자릿수를 설명하는 상대 용어입니다. 배정밀도 숫자의 이진 자릿수는 단정밀도의 두 배입니다. 최신 컴퓨터에서는 단정밀도 숫자보다 배정밀도를 더 많이 사용합니다. 단정밀도 숫자는 float 키워드를 사용하여 선언됩니다. 지금 살펴보세요. 다음 코드를 추가하고 결과를 확인합니다.

```C#
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

답에 몫의 소수 부분이 포함되어 있습니다. double을 사용하여 약간 더 복잡한 식을 사용해 보세요.

```C#
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

double 값의 범위는 정수 값보다 훨씬 큽니다. 지금까지 작성한 코드 아래에 다음 코드를 사용해 봅니다.

```C#
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

이 값은 과학적 표기법으로 인쇄됩니다. E의 왼쪽에 있는 숫자는 유효 숫자입니다. 오른쪽의 숫자는 지수이며 10의 배수입니다. 수학의 10진수 숫자와 마찬가지로, C#에서 double에는 반올림 오류가 발생할 수 있습니다. 다음 코드를 사용해 보세요.

```C#
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

유한한 횟수를 반복하는 것은 과 1/3정확히 동일하지 않다는 것을 알고 0.3 있습니다.

### 과제

double 형식을 사용하여 큰 숫자, 작은 숫자, 곱하기 및 나누기로 다른 계산을 수행해 보세요. 더 복잡한 계산을 수행해 보세요. 과제를 하느라 약간의 시간을 보낸 후 작성한 코드를 새 메서드에 배치합니다. 이러한 새 메서드의 이름을 WorkWithDoubles로 지정합니다.

---
## 10진 형식으로 작업

C#의 기본적인 숫자 형식인 정수 형식과 double 형식을 살펴봤습니다. 학습할 또 다른 형식이 있습니다. 바로 decimal 형식입니다. decimal 형식은 범위가 작지만 double보다 전체 자릿수가 큽니다. 이 형식에 대해 살펴보겠습니다.

```C#
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

범위가 double 형식보다 작습니다. 다음 코드를 사용하여 소수점이 있는 더 큰 전체 자릿수를 확인할 수 있습니다.

```C#
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

숫자의 M 접미사는 상수가 decimal 형식을 사용해야 함을 나타내는 방법입니다. 형식을 지정하지 않으면 컴파일러는 double 형식으로 간주합니다.

```
참고

문자 M은 double 키워드와 decimal 키워드 사이에서 가장 시각적으로 고유한 문자로 선택되었습니다.
```

소수점 형식을 사용하는 수학에는 소수점 오른쪽에 더 많은 숫자가 있습니다.

### 과제

이제 여러 가지 숫자 형식을 살펴봤으므로 반지름이 2.50센티미터인 원의 면적을 계산하는 코드를 작성하세요. 원의 면적은 반지름 제곱 곱하기 PI입니다. 힌트: .NET에는 PI의 상수가 포함되어 있습니다. 즉 해당 값에 사용할 수 있는 Math.PI입니다. System.Math 네임스페이스에 선언된 모든 상수와 마찬가지로 Math.PI는 double 값입니다. 이러한 이유로 이 과제에는 decimal 값 대신 double을 사용해야 합니다.

---
## 출처
[C# 설명서>시작하기>자습서>C#에서 정수 및 부동 소수점 숫자를 사용하는 방법](https://learn.microsoft.com/ko-kr/dotnet/csharp/tour-of-csharp/tutorials/numbers-in-csharp-local)