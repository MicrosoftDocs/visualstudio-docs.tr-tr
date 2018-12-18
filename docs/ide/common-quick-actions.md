---
title: Yaygın Hızlı Eylemler
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c6eaa3b776e7a4c4e90795265f94af2d0df994b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894020"
---
# <a name="common-quick-actions"></a>Yaygın Hızlı Eylemler

Bu konudaki bölümler bazı yaygın listesinde **hızlı Eylemler** hem C# ve Visual Basic kodu için geçerli. Bu eylemler *kod düzeltme* derleyici Tanılama veya yerleşik [.NET derleyici platformu Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) Visual Studio'da.

## <a name="actions-that-fix-errors"></a>Hataları düzeltme eylemleri

Hızlı Eylemler Bu bölümde, bir derleme başarısız olmasına neden olan kodu hataları düzeltin. Bir kod satırının bir hatayı düzeltmek hızlı Eylemler kullanılabilir olduğunda simge kenar boşluğunda görüntülenir veya kırmızı dalgalı çizgi altında bulunan kırmızı bir 'x' ile bir ampul olduğu.

![Hızlı Eylemler hata simgesi ve menüsü](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Doğru yanlış yazılmış sembol veya anahtar sözcüğü

Bir tür veya Visual Studio'da anahtar sözcüğü yanlışlıkla yazarsanız, bu hızlı işlem otomatik olarak bunu sizin için düzeltir. Ampul menüsü bu öğeleri görürsünüz **"değişiklik '*yanlış word*'to'*düzeltmek word*'**. Örneğin:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Hata Kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS0103, BC30002 | C# ve Visual Basic | Visual Studio 2015 Güncelleştirme 2 |

### <a name="resolve-git-merge-conflict"></a>Git birleştirme çakışması çözümleme

Bu hızlı Eylemler git birleştirme çakışması çözümlemek etkinleştirdiğiniz tarafından "Sürüyor bir değişiklik", çakışan kod ve işaretçiler kaldırır.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Hata Kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 |

## <a name="actions-that-remove-unnecessary-code"></a>Gereksiz kodu Kaldır eylemleri

### <a name="remove-unnecessary-usingsimports"></a>Gereksiz using deyimlerini/içeri aktarmaları Kaldır

**Kaldırma gereksiz kullanımları/Imports** hızlı eylem kaldırır kullanılmayan `using` ve `Import` deyimleri geçerli dosya için. Bu öğeyi seçin, kullanılmayan ad alanı içeri aktarmaları kaldırılır.

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unnecessary-cast"></a>Gereksiz tür dönüştürmeyi Kaldır

Bir tür dönüştürme gerektirmeyen başka bir tür türüne, **gereksiz tür dönüştürmeyi Kaldır** gereksiz tür dönüştürmeyi hızlı eylem öğeyi kaldırır.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# ve Visual Basic | Visual Studio 2015 RTW |

### <a name="remove-unused-variables"></a>Kullanılmayan değişkenler Kaldır

Bu hızlı eylem bildirildi ancak hiç kullanılmadı değişkenleri kodunuzda kaldırmanızı sağlar.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 |

### <a name="remove-type-from-default-value-expression"></a>Varsayılan değer ifadesinden türünü Kaldır

Bu hızlı eylem değer türünün bir varsayılan değer ifadesinden kaldırır ve kullandığı [varsayılan sabit değer](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) zaman derleyici tanım Çıkarsama ifadenin türü.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1 + | Visual Studio 2017 sürüm 15.3 |

## <a name="actions-that-add-missing-code"></a>Eksik kod ekleme eylemleri

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Türler için using deyimlerini/içeri aktarmalar başvuru bütünleştirilmiş kodları, NuGet paketlerini veya çözümünüzdeki diğer türleri Ekle

Çözümünüzdeki diğer projelere bulunan türleri kullanarak görüntüler hızlı eylem otomatik olarak diğer gelen etkinleştirilmesi gerekir ancak **Araçlar > Seçenekler > C#** veya **temel > Gelişmiş** sekmesinde:

- Reference bütünleştirilmiş kodlarında türler için using deyimlerini/içeri aktarmalar Öner
- NuGet paketlerinde türler için using deyimlerini/içeri aktarmalar Öner

Bir tür, şu anda değil alınır, ancak bir başvuru bütünleştirilmiş kodu veya NuGet paketi mevcut bir ad alanında kullanırsanız, etkin olduğunda, using/Import deyimi oluşturulur.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS0103, BC30451 | C# ve Visual Basic| Visual Studio 2015 Güncelleştirme 2 |

### <a name="add-missing-casesdefault-caseboth"></a>Eksik durumları/varsayılan durumda/hem Ekle

Oluştururken bir `switch` C# ' ta, ifade veya `Select Case` deyimi Visual Basic'de büyük/küçük harf öğeleri, varsayılan case deyimi ya da her ikisini de otomatik olarak eklemek için bir kod eylemi kullanabilirsiniz.

Aşağıdaki sabit göz önünde bulundurun ve boş `switch` veya `Select Case` deyimi:

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Kullanarak **hem de ekleme** hızlı eylem eksik durumda doldurur ve varsayılan durumda ekler:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 |

### <a name="add-null-checks-for-parameters"></a>Parametre için null denetimleri Ekle

Bu hızlı işlem onay bir parametre null olup olmadığını bildirmek için kodunuzda eklemenize olanak tanır.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 |

### <a name="add-argument-name"></a>Bağımsız değişken adını Ekle

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 |

### <a name="add-braces"></a>Küme ayracı Ekle

Hızlı Eylem Ekle küme ayraçları sarmalar küme ayraçları tek satır etrafında `if` deyimleri.

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 RTW |

### <a name="add-and-order-modifiers"></a>Ekleme ve sipariş değiştiriciler

Bu hızlı Eylemler, değiştirici mevcut sıralamak ve eksik erişilebilirlik değiştiricileri Ekle olanak tanıyarak düzenlemenize yardımcı.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 |
| IDE0040 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 |

## <a name="code-transformations"></a>Kod dönüşümleri

### <a name="convert-if-construct-to-switch"></a>'İf' yapısı 'geçiş yapmak için ' Dönüştür

Bu hızlı eylem dönüştürmenize olanak sağlayan bir **if-then-else** oluşturmak için bir **geçiş** oluşturun.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 |

### <a name="convert-to-interpolated-string"></a>Enterpolasyonlu dizeye Dönüştür

[İlişkilendirilmiş dizeler](/dotnet/csharp/language-reference/keywords/interpolated-strings) dizeleri gömülü değişkenleri, benzer şekilde ifade etmek için kolay bir yoludur **[String.Format](/dotnet/api/system.string.format#overloads)** yöntemi.  Bu hızlı eylem birleştirilmiş ya da kullanarak dizeleri olduğu durumları algılar **String.Format**, kullanım için bir aradeğerlendirme dizesinde değiştirir.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# 6.0 + ve Visual Basic 14 + | Visual Studio 2017 RTW |

### <a name="use-object-initializers"></a>Nesne başlatıcıları kullanın

Bu hızlı eylem kullanmanızı sağlayan [nesne başlatıcılarda](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) yapıcıyı ve ek atama deyimleri satırları sahip olmak yerine.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# ve Visual Basic | Visual Studio 2017 RTW |

### <a name="use-collection-initializers"></a>Koleksiyon başlatıcıları kullanın

Bu hızlı eylem kullanmanıza olanak tanıyan [koleksiyon başlatıcıları](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) birden çok çağrı yerine `Add` sınıfınızın yöntemi.

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# ve Visual Basic | Visual Studio 2017 RTW |

### <a name="convert-auto-property-to-full-property"></a>Otomatik özellik tam özelliğe Dönüştür

Bu hızlı eylemi otomatik özellik tam özelliğe Dönüştür olanak tanır ve bunun tersi de geçerlidir.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Geçerli diller | Desteklenen sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic | Visual Studio 2017 sürüm 15.5 |

### <a name="convert-block-body-to-expression-bodied-member"></a>İfade gövdeli üyesi için blok gövdesi Dönüştür

Bu hızlı eylem yöntemleri, Oluşturucular, işleçler, özellikler, dizin oluşturucular ve erişimciler için ifade gövdeli üyeler blok gövdeleri dönüştürmek sağlar.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0 VE ÜZERİ | Visual Studio 2017 RTW |

### <a name="convert-anonymous-function-to-local-function"></a>Anonim işlev yerel işleve dönüştürme

Bu hızlı eylem yerel işlevlerini anonim işlevler dönüştürür.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>'ReferenceEquals', 'null olduğu için' Dönüştür

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0 + | Visual Studio 2017 sürüm 15.5 |

Bu hızlı eylem kullanımını öneren [desen eşleştirme](/dotnet/csharp/pattern-matching) yerine ```ReferenceEquals``` kodlama düzenini, mümkün olduğunda.

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0 + | Visual Studio 2017 sürüm 15.5 |

### <a name="introduce-pattern-matching"></a>Desen eşleştirme Ekle

Bu hızlı eylem kullanımını öneren [desen eşleştirme](/dotnet/csharp/pattern-matching) yayınları ve C# null denetimleri.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0 + | Visual Studio 2017 RTW |
| IDE0019 | C# 7.0 + | Visual Studio 2017 RTW |

### <a name="change-base-for-numeric-literals"></a>Sayısal değişmez değerleri değiştirme temeli

Bu hızlı eylem bir sayısal sabit değer temel bir sayısal sistemden dönüştürmenize olanak sağlar. Örneğin, onaltılık veya ikili biçimi bir sayıyı değiştirebilirsiniz.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0 + ve Visual Basic 14 + | Visual Studio 2017 sürüm 15.3 |

### <a name="insert-digit-separators-into-literals"></a>Rakam ayırıcıları değişmez değerleri Ekle

Bu hızlı eylem ayırıcı karakter değişmez değerlere eklemenize olanak tanır.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0 + ve Visual Basic 14 + | Visual Studio 2017 sürüm 15.3 |

### <a name="use-explicit-tuple-names"></a>Açık demet adları kullanın

Bu hızlı eylem burada açık demet adını kullanılabilir Item1 Item2, vb. yerine alanları belirler.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0 + ve Visual Basic 15 + | Visual Studio 2017 RTW |

### <a name="use-inferred-names"></a>Çıkarsanan adlar kullanın

Bu hızlı eylem anonim türde üye adları çıkarılan kullanmak için kodu Basitleştirilmiş zaman işaret eder veya demetlerde öğe adları.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 v. 15.5 |
| IDE0037 | C# 7.1 + | Visual Studio 2017 v. 15.5 |

### <a name="deconstruct-tuple-declaration"></a>Tanımlama grubu bildirimini Ayrıştır

Bu hızlı eylem ayrıştırma demet değişken bildirimlerini etkinleştirir.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| Tanılama kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0 + | Visual Studio 2017 v. 15.5 |

### <a name="make-method-synchronous"></a>Yöntem zaman uyumlu yapın

Kullanırken `async` veya `Async` anahtar sözcüğü bir yöntem, bu, bu yöntem içinde beklenen `await` veya `Await` anahtar sözcüğü de kullanılır. Bu durumda değilse, ancak hızlı eylem kaldırarak yöntem zaman uyumlu yaptığı görünür `async` veya `Async` anahtar sözcüğü ve dönüş türünü değiştirme. Kullanım **yöntem zaman uyumlu hale getirin** hızlı Eylemler menüsünden seçeneği.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| Hata Kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS1998, BC42356 | C# ve Visual Basic | Visual Studio 2015 Güncelleştirme 2 |

### <a name="make-method-asynchronous"></a>Zaman uyumsuz yöntem yapın

Kullanırken `await` veya `Await` anahtar sözcüğü bir yöntem içinde bu yöntem ile işaretlenmiş beklenmektedir `async` veya `Async` anahtar sözcüğü. Ancak, bu durumda değilse, hızlı bir eylem, zaman uyumsuz hale getirdiğini görüntülenir. Kullanım **yöntemi/işlev zaman uyumsuz hale getirin** hızlı Eylemler menüsünden seçeneği.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Hata Kimliği | Geçerli diller | Desteklenen sürüm |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# ve Visual Basic | Visual Studio 2017 |

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
