---
title: Kodlama kuralı ayarlarına EditorConfig için .NET
ms.date: 06/14/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: kuhlenh
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a54a3d6b967e7652c25e24922d7bd3b49141cc17
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769747"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>Kodlama kuralı ayarlarına EditorConfig için .NET

Visual Studio 2017'de tanımlayabilir ve tutarlı bir kod stili korumak, birlikte kod temeli bir [EditorConfig](../ide/create-portable-custom-editor-options.md) dosya. EditorConfig içeren birkaç temel özellikleri biçimlendirme gibi `indent_style` ve `indent_size`. Visual Studio'da .NET kodlama kuralları ayarları bir EditorConfig dosyasını kullanarak da yapılandırılabilir. EditorConfig dosyaları etkinleştirme veya devre dışı bağımsız .NET kodlama kuralları ve önem derecesi zorunlu kuralı istediğiniz ölçüde yapılandırmak için izin verin. EditorConfig temelinizde tutarlılığı zorlamak için nasıl kullanılacağı hakkında daha fazla bilgi edinmek için [oluşturma taşınabilir özel düzenleyici seçenekleri](../ide/create-portable-custom-editor-options.md).

Bu makalenin sonuna bakın bir [örnek .editorconfig dosyasındaki](#example-editorconfig-file).

## <a name="convention-categories"></a>Kural kategorileri

Üç desteklenen .NET kodlama kuralı kategorisi vardır:

- [Dil kod stilleri](#language-code-styles)

   C# veya Visual Basic Dil ilişkin kurallardır. Örneğin, etrafında kullanarak kuralları belirtebilirsiniz `var` veya açık olduğunda türleri değişkenleri tanımlayan veya ifade gövdeli üyeler belgelemeyi.

- [Biçimlendirme kuralları](#formatting-conventions)

   Okunmalarını kolaylaştırmak için kodunuzun yapısı ve düzeni kurallardır. Örneğin, denetim blokları Allman küme ayraçları veya alanları belgelemeyi çevresinde kuralları belirtebilirsiniz.

- [Adlandırma kuralları](../ide/editorconfig-naming-conventions.md)

   İlgili kod öğelerini adlandırma kuralları. Örneğin, belirtebilirsiniz `async` yöntemleri "Async" bitmelidir.

## <a name="language-code-styles"></a>Dil kod stilleri

Dil kod stili için kuralları aşağıdaki biçime sahiptir:

`options_name = false|true : none|silent|suggestion|warning|error`

Her dil kodu stil kuralı belirtmeli **true** (Bu stil tercih et) veya **false** (Bu stil tercih değil) ve bir **önem derecesi**. Önem derecesi için o stilin zorlama düzeyini belirtir.

Olası önem derecesi değerlerini ve bunların etkileri aşağıdaki tabloda listelenmektedir:

Önem Derecesi | Efekt
:------- | ------
`none` | Bu kural ihlal edildiğinde herhangi bir şey kullanıcıya göstermez. Kod oluşturma özellikleri kodu bu stilde, ancak oluşturma. İle kurallar `none` önem derecesi hiçbir zaman görünür **hızlı Eylemler ve yeniden düzenlemeler** menüsü. Çoğu durumda, bu "yoksayıldı" veya "devre dışı" olarak kabul edilir.
`silent` (Ayrıca `refactoring` Visual Studio 2017 sürüm 15,8) | Bu kural ihlal edildiğinde herhangi bir şey kullanıcıya göstermez. Kod oluşturma özellikleri kodu bu stilde, ancak oluşturma. İle kurallar `silent` önem derecesi temizleme katılmak yanı sıra görünür **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
`suggestion` | Bu stil kuralı ihlal edildiğinde kullanıcıya öneri olarak gösterir. Öneriler, ilk iki karakter altındaki gri üç nokta olarak görünür.
`warning` | Bu stil kuralı ihlal edildiğinde bir derleyici uyarısı gösterir.
`error` | Bu stil kuralı ihlal edildiğinde bir derleyici hatası gösterir.

Aşağıdaki listede verilen dil kod stili ayarları gösterilmektedir:

- .NET kod stili ayarları
    - ["This." ve "Me." niteleyicileri](#this_and_me)
        - DotNet\_stili\_nitelik\_for_field
        - DotNet\_stili\_nitelik\_for_property
        - DotNet\_stili\_nitelik\_for_method
        - DotNet\_stili\_nitelik\_for_event
    - [Dil anahtar sözcükleri framework yerine tür başvurularını adlarını yazın](#language_keywords)
        - DotNet\_stili\_önceden tanımlanmış\_türü\_için\_Yereller\_parameters_members
        - DotNet\_stili\_önceden tanımlanmış\_türü\_için\_member_access
    - [Değiştiricisi tercihleri](#normalize_modifiers)
        - DotNet\_stili\_gerektiren\_accessibility_modifiers
        - CSharp\_tercih edilen\_modifier_order
        - görsel\_temel\_tercih edilen\_modifier_order
        - DotNet\_stili\_salt okunur\_alan
    - [Parantez tercihleri](#parentheses)
        - DotNet\_stili\_parantez\_içinde\_aritmetik\_ikili\_işleçleri
        - DotNet\_stili\_parantez\_içinde\_diğer\_ikili\_işleçleri
        - DotNet\_stili\_parantez\_içinde\_diğer\_işleçleri
        - DotNet\_stili\_parantez\_içinde\_ilişkisel\_ikili\_işleçleri
    - [İfade düzeyi tercihleri](#expression_level)
        - DotNet\_stili\_object_initializer
        - DotNet\_stili\_collection_initializer
        - DotNet\_stili\_açık\_tuple_names
        - DotNet\_stili\_tercih\_çıkarılan\_tuple_names
        - DotNet\_stili\_tercih\_çıkarılan\_anonim\_türü\_member_names
        - DotNet\_stili\_tercih\_otomatik\_özellikleri
        - DotNet\_stili\_tercih\_olduğu\_null\_denetleyin\_üzerinden\_başvuru\_eşitlik\_yöntemi
        - DotNet\_stili\_tercih\_koşullu\_ifade\_üzerinden\_atama
        - DotNet\_stili\_tercih\_koşullu\_ifade\_üzerinden\_döndürür
    - ["Null" Tercihler denetleniyor](#null_checking)
        - DotNet\_stili\_coalesce_expression
        - DotNet\_stili\_null_propagation
- C# kod stili ayarları
    - [Örtük ve açık türleri](#implicit-and-explicit-types)
        - CSharp\_stili\_var\_için\_yerleşik\_in_types
        - CSharp\_stili\_var\_olduğunda\_türü\_is_apparent
        - CSharp\_stili\_var_elsewhere
    - [İfade gövdeli üyeler](#expression_bodied_members)
        - csharp\_style\_expression\_bodied_methods
        - CSharp\_stili\_ifade\_bodied_constructors
        - CSharp\_stili\_ifade\_bodied_operators
        - CSharp\_stili\_ifade\_bodied_properties
        - CSharp\_stili\_ifade\_bodied_indexers
        - CSharp\_stili\_ifade\_bodied_accessors
    - [Desen eşleştirme](#pattern_matching)
        - CSharp\_stili\_deseni\_eşleşen\_üzerinden\_olduğu\_ile\_cast_check
        - CSharp\_stili\_deseni\_eşleşen\_üzerinden\_olarak\_ile\_null_check
    - [Satır içi değişken bildirimi](#inlined_variable_declarations)
        - CSharp\_stili\_satır içine alınmış\_variable_declaration
    - [İfade düzeyi tercihleri](#expression_level_csharp)
        - csharp\_prefer\_simple\_default_expression
        - CSharp\_stili\_deconstructed\_variable_declaration
        - CSharp\_stili\_deseni\_yerel\_üzerinden\_anonymous_function
    - ["Null" Tercihler denetleniyor](#null_checking_csharp)
        - csharp\_style\_throw_expression
        - CSharp\_stili\_koşullu\_delegate_call
    - [Kod bloğu tercihleri](#code_block)
        - CSharp\_prefer_braces

### <a name="net-code-style-settings"></a>.NET kod stili ayarları

Stil kurallarını Bu bölümde, hem C# ve Visual Basic için geçerlidir. Tercih ettiğiniz programlama dilini kod örnekleri görmek için açılan menü seçin **dil** tarayıcı pencerenizin sağ üst köşesindeki menü.

#### <a name="this_and_me"></a>"This." ve "Me." niteleyicileri

Bu stil kuralı (kimlikleri IDE0003 ve IDE0009 kural) alanlar, özellikler, yöntemler veya olayları için uygulanabilir. Değerini **true** anlamına gelir, kod simge ile başlayan tercih `this.` C# veya `Me.` Visual Basic'te. Değerini **false** anlamına gelir, kod öğesi tercih _değil_ başında için `this.` veya `Me.`.

Kural adı, geçerli programlama dilleri ve varsayılan değerleri aşağıdaki tabloda gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan değer |
| ----------- | -------------------- | ----------------------|
| dotnet_style_qualification_for_field | C# ve Visual Basic | false: yok |
| dotnet_style_qualification_for_property | C# ve Visual Basic | false: yok |
| dotnet_style_qualification_for_method | C# ve Visual Basic | false: yok |
| dotnet_style_qualification_for_event | C# ve Visual Basic | false: yok |

**DotNet\_stili\_nitelik\_for_field**

- Bu kural ayarlandığında **true**, ile başlayan alanlar tercih `this.` C# veya `Me.` Visual Basic'te.
- Bu kural ayarlandığında **false**, alanlar tercih _değil_ başında için `this.` veya `Me.`.

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

**DotNet\_stili\_nitelik\_for_property**

- Bu kural ayarlandığında **true**, başında için özellikleri tercih et `this.` C# veya `Me.` Visual Basic'te.
- Bu kural ayarlandığında **false**, özellikleri tercih et _değil_ başında için `this.` veya `Me.`.

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

**DotNet\_stili\_nitelik\_for_method**

- Bu kural ayarlandığında **true**, tercih ettiğiniz yöntemleri ile başlayan `this.` C# veya `Me.` Visual Basic'te.
- Bu kural ayarlandığında **false**, tercih ettiğiniz yöntemleri _değil_ başında için `this.` veya `Me.`.

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

**DotNet\_stili\_nitelik\_for_event**

- Bu kural ayarlandığında **true**, olayları ile başlayan tercih `this.` C# veya `Me.` Visual Basic'te.
- Bu kural ayarlandığında **false**, olayları tercih _değil_ başında için `this.` veya `Me.`.

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="language_keywords"></a>Dil anahtar sözcükleri framework yerine tür başvurularını adlarını yazın

Bu stil kuralı, yerel değişkenler, yöntem parametreleri ve sınıf üyeleri veya üye erişimi ifadeleri yazmak için ayrı bir kural olarak uygulanabilir. Değerini **true** anlamına gelir, tercih ettiğiniz dil anahtar sözcüğü (örneğin, `int` veya `Integer`) tür adı yerine (örneğin, `Int32`) bunları temsil etmek için bir anahtar sözcük sahip türleri. Değerini **false** anlamına gelir, tercih ettiğiniz dil anahtar sözcüğü yerine tür adı.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli programlama dilleri ve varsayılan değerleri gösterir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan |
| --------- | ------- | -------------------- | ----------------------|
| dotnet_style_predefined_type_for_locals_parameters_members | IDE0012 ve IDE0014 | C# ve Visual Basic | TRUE: yok |
| dotnet_style_predefined_type_for_member_access | IDE0013 ve IDE0015 | C# ve Visual Basic | TRUE: yok |

**DotNet\_stili\_önceden tanımlanmış\_türü\_için\_Yereller\_parameters_members**

- Bu kural ayarlandığında **true**, tercih ettiğiniz dil anahtar sözcüğü yerel değişkenler, yöntem parametreleri ve sınıf üyeleri, bunları temsil etmek için bir anahtar sözcüğüne sahip türler için tür adı yerine.
- Bu kural ayarlandığında **false**türü adını yerel değişkenler, yöntem parametreleri ve sınıf üyeleri, dil anahtar sözcüğü yerine.

Kod örnekleri:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

**DotNet\_stili\_önceden tanımlanmış\_türü\_için\_member_access**

- Bu kural ayarlandığında **true**, bunları temsil etmek için bir anahtar sözcüğüne sahip türler için tür adı yerine üye erişimi ifadeleri için dil anahtar kelimesi'tercih et.
- Bu kural ayarlandığında **false**, dil anahtar sözcüğü yerine üye erişimi ifadeleri için tür adını tercih et.

Kod örnekleri:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="normalize_modifiers"></a>Değiştiricisi tercihleri

Bu bölümdeki Stil kurallarının değiştiricisi tercihleri, erişilebilirlik değiştiricileri gerektiren, istenen değiştiricisi sıralama düzenini belirten ve salt okunur değiştiricisi gerektirme dahil olmak üzere uğraşmak.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli programlama dilleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| dotnet_style_require_accessibility_modifiers | IDE0040 | C# ve Visual Basic | for_non_interface_members:none | 15.5 |
| csharp_preferred_modifier_order | IDE0036 | C# | Genel, özel, korumalı, dahili, statik ve extern, yeni, virtual, abstract, korumalı, geçersiz kılma, salt okunur, güvenli, geçici, zaman uyumsuz: yok | 15.5 |
| visual_basic_preferred_modifier_order | IDE0036 | Visual Basic | Kısmi, varsayılan, özel, korumalı, genel, arkadaş NotOverridable, geçersiz kılınabilir, MustOverride, aşırı yüklemeler, geçersiz kılmalar, MustInherit, NotInheritable, statik, paylaşılan, gölgeler, salt okunur, WriteOnly, boyutu, Const, WithEvents, daraltma, özel, genişletme Zaman uyumsuz: yok | 15.5 |
| dotnet_style_readonly_field | IDE0044 | C# ve Visual Basic | TRUE: öneri | 15.7 |

**DotNet\_stili\_gerektiren\_accessibility_modifiers**

Bu kural kabul etmediği bir **true** veya **false** değeri; bunun yerine aşağıdaki tablodan bir değer olarak kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| Her zaman | Erişilebilirlik değiştiricileri belirtilmesi tercih et |
| için\_olmayan\_interface_members | Genel arabirim üyeleri hariç bildirilmesi için erişilebilirlik değiştiricileri tercih eder. Bu, aynı **her zaman** ve C# varsayılan arabirim yöntemleri eklerse, gelecekteki sağlama için eklendi. |
| hiçbir zaman | Erişilebilirlik değiştiricileri belirtilmesi tercih ediyorsunuz |

Kod örnekleri:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

**csharp_preferred_modifier_order**

- Bu kural değiştiriciler listesine ayarlandığında, belirtilen sıralama tercih eder.
- Bu kural dosyasından atlandığında, değiştirici sırasını tercih ediyorsunuz.

Kod örnekleri:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

**visual_basic_preferred_modifier_order**

- Bu kural değiştiriciler listesine ayarlandığında, belirtilen sıralama tercih eder.
- Bu kural dosyasından atlandığında, değiştirici sırasını tercih ediyorsunuz.

Kod örnekleri:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

**dotnet_style_readonly_field**

- Bu kural ayarlandığında **true**, alanları ile işaretlenmelidir tercih `readonly` (C#) veya `ReadOnly` yalnızca satır içi hiç olmadığı kadar atandığı veya bir oluşturucu içinde olması durumunda (Visual Basic).
- Bu kural ayarlandığında **false**, tercih yok olup alanları ile işaretlenmelidir üzerinden belirtin `readonly` (C#) veya `ReadOnly` (Visual Basic).

Kod örnekleri:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="parentheses"></a>Parantez tercihleri

Bu bölümdeki Stil kurallarının parantez tercihleri, parantez aritmetik, ilişkisel, için ve diğer ikili işleçler kullanımı dahil olmak üzere uğraşmak.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli programlama dilleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_parentheses_in_arithmetic_binary_operators | IDE0047 | C# ve Visual Basic | always_for_clarity: yok | 15,8 |
| dotnet_style_parentheses_in_relational_binary_operators | IDE0047 | C# ve Visual Basic | always_for_clarity: yok | 15,8 |
| dotnet_style_parentheses_in_other_binary_operators | IDE0047 | C# ve Visual Basic | always_for_clarity: yok | 15,8 |
| dotnet_style_parentheses_in_other_operators | IDE0047 | C# ve Visual Basic | never_if_unnecessary: yok | 15,8 |

**DotNet\_stili\_parantez\_içinde\_aritmetik\_binary_operators**

- Bu kural ayarlandığında **always_for_clarity**, aritmetik işleç açıklamak için parantezler tercih (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) öncelik.
- Bu kural ayarlandığında **never_if_unnecessary**, aritmetik, parantez almamayı tercih işleci (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) öncelik belirgin.

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

**DotNet\_stili\_parantez\_içinde\_ilişkisel\_binary_operators**

- Bu kural ayarlandığında **always_for_clarity**, ilişkisel işleç açıklamak için parantezler tercih (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) öncelik.
- Bu kural ayarlandığında **never_if_unnecessary**, ilişkisel olduğunda parantezler almamayı tercih işleci (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) öncelik belirgin.

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

**DotNet\_stili\_parantez\_içinde\_diğer\_binary_operators**

- Bu kural ayarlandığında **always_for_clarity**, tercih ettiğiniz diğer ikili işleç açıklamak için parantezler (`&&`, `||`, `??`) öncelik.
- Bu kural ayarlandığında **never_if_unnecessary**, parantez almamayı tercih, diğer ikili işleç (`&&`, `||`, `??`) öncelik belirgin.

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

**DotNet\_stili\_parantez\_içinde\_other_operators**

- Bu kural ayarlandığında **always_for_clarity**, İşleç önceliği netleştirmek için parantez tercih edin.
- Bu kural ayarlandığında **never_if_unnecessary**, İşleç önceliği belirgin olduğunda parantezler almamayı tercih ediyorsunuz.

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:none
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:none
```

#### <a name="expression_level"></a>İfade düzeyi tercihleri

Stil nesne başlatıcıları, koleksiyon başlatıcıları, açık veya çıkarsanan demet adları, kullanımı dahil olmak üzere bu bölümü endişe ifade düzeyi tercihlerinde kuralları ve anonim türler sonuçlandı.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli programlama dilleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_object_initializer | IDE0017 | C# ve Visual Basic | TRUE: öneri | İlk yayın |
| dotnet_style_collection_initializer | IDE0028 | C# ve Visual Basic | TRUE: öneri | İlk yayın |
| dotnet_style_explicit_tuple_names | IDE0033 | C# 7.0 + ve Visual Basic 15 + | TRUE: öneri | İlk yayın |
| dotnet_style_prefer_inferred_tuple_names | IDE0037 | C# 7.1 + ve Visual Basic 15 + | TRUE: öneri | 15.6 |
| dotnet_style_prefer_inferred_anonymous_type_member_names | IDE0037 | C# ve Visual Basic | TRUE: öneri | 15.6 |
| dotnet_style_prefer_auto_properties | IDE0032 | C# ve Visual Basic | TRUE: yok | 15.7 |
| dotnet_style_prefer_is_null_check_over_reference_equality_method | IDE0041 | C# ve Visual Basic | TRUE: öneri | 15.7 |
| dotnet_style_prefer_conditional_expression_over_assignment | IDE0045 | C# ve Visual Basic | TRUE: yok | 15,8 |
| dotnet_style_prefer_conditional_expression_over_return | IDE0046 | C# ve Visual Basic | TRUE: yok | 15,8 |

**DotNet\_stili\_object_initializer**

- Bu kural ayarlandığında **true**, mümkün olduğunda, nesne başlatıcıları kullanarak başlatılacak nesneleri tercih edin.
- Bu kural ayarlandığında **false**, nesnelere tercih *değil* olması nesne başlatıcıları kullanılarak başlatılır.

Kod örnekleri:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

**DotNet\_stili\_collection_initializer**

- Bu kural ayarlandığında **true**, mümkün olduğunda koleksiyon başlatıcıları kullanarak başlatılması için koleksiyonları tercih et.
- Bu kural ayarlandığında **false**, koleksiyonlara tercih *değil* olması koleksiyon başlatıcıları kullanılarak başlatılır.

Kod örnekleri:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

**DotNet\_stili\_açık\_tuple_names**

- Bu kural ayarlandığında **true**, demet adları ItemX özellikleri tercih et.
- Bu kural ayarlandığında **false**, demet adları ItemX özellikleri tercih et.

Kod örnekleri:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

**DotNet\_stili\_tercih\_çıkarılan\_tuple_names**

- Bu kural ayarlandığında **true**, gösterilen demet öğesi adlarını tercih et.
- Bu kural ayarlandığında **false**, açık demet öğesi adlarını tercih et.

Kod örnekleri:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

**DotNet\_stili\_tercih\_çıkarılan\_anonim\_türü\_member_names**

- Bu kural ayarlandığında **true**, gösterilen anonim tip üye adlarını tercih et.
- Bu kural ayarlandığında **false**, açık anonim tip üye adlarını tercih et.

Kod örnekleri:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

**DotNet\_stili\_tercih\_otomatik\_özellikleri**

- Bu kural ayarlandığında **true**, autoproperties üzerinden özel yedekleme alanlarla özellikleri tercih et.
- Bu kural ayarlandığında **false**, autoproperties özel yedekleme alanlarla özellikleri tercih et.

Kod örnekleri:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

**DotNet\_stili\_tercih\_olduğu\_null\_denetleyin\_üzerinden\_başvuru\_eşitlik\_yöntemi**

- Bu kural ayarlandığında **true**, null denetimi ile desen eşleştirme nesnenin üzerine kullanmayı tercih. ReferenceEquals.
- Bu kural ayarlandığında **false**, nesne tercih edin. Null denetimi ile desen eşleştirme üzerinden ReferenceEquals.

Kod örnekleri:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```



**DotNet\_stili\_tercih\_koşullu\_ifade\_over_assignment**

- Bu kural ayarlandığında **true**, Üçlü koşullu atamaları bir if-else deyimi tercih.
- Bu kural ayarlandığında **false**, Üçlü koşullu bir if-else deyimi atamaları tercih.

Kod örnekleri:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

**DotNet\_stili\_tercih\_koşullu\_ifade\_over_return**

- Bu kural ayarlandığında **true**, Üçlü koşullu bir if-else deyimi kullanmak için dönüş deyimleri tercih edin.
- Bu kural ayarlandığında **false**, Üçlü koşullu bir if-else deyimi kullanılacak dönüş deyimleri tercih et.

Kod örnekleri:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:none
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
```

#### <a name="null_checking"></a>Null denetimi tercihleri

Bu bölümdeki Stil kurallarının null denetimi tercihleri ilgilendiriyor.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli programlama dilleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---- |
| dotnet_style_coalesce_expression | IDE0029 | C# ve Visual Basic | TRUE: öneri | İlk yayın |
| dotnet_style_null_propagation | IDE0031 | C# 6.0 + ve Visual Basic 14 + | TRUE: öneri | İlk yayın |

**DotNet\_stili\_coalesce_expression**

- Bu kural ayarlandığında **true**, denetimi Üçlü işleç null birleşim ifadelerini tercih edin.
- Bu kural ayarlandığında **false**, Üçlü işleç için null birleşim ifadelerini denetimi tercih edin.

Kod örnekleri:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

**DotNet\_stili\_null_propagation**

- Bu kural ayarlandığında **true**, mümkün olduğunda null koşullu işleci kullanmayı tercih eder.
- Bu kural ayarlandığında **false**, Üçlü null denetimi mümkün olduğunda kullanmayı tercih eder.

Kod örnekleri:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

Bu kurallar, görünebilir bir *.editorconfig* aşağıdaki gibi:

```EditorConfig
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

### <a name="c-code-style-settings"></a>C# kod stili ayarları

Bu bölümdeki stil kuralları yalnızca C# için geçerlidir.

#### <a name="implicit-and-explicit-types"></a>Örtük ve açık türleri

Bu bölümdeki Stil kurallarının (kimlikleri IDE0007 ve IDE0008 kural) kullanımını ilgilendiriyor [var](/dotnet/csharp/language-reference/keywords/var) anahtar sözcüğü Değişken bildiriminde bir açık tür yerine. Bu kural türü belirgin olduğunda yerleşik türler ve diğer yerlerde için ayrı olarak uygulanabilir.

Kural adı, geçerli programlama dilleri ve varsayılan değerleri aşağıdaki tabloda gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan |
| ----------- | -------------------- | ----------------------|
| csharp_style_var_for_built_in_types | C# | TRUE: yok |
| csharp_style_var_when_type_is_apparent | C# | TRUE: yok |
| csharp_style_var_elsewhere | C# | TRUE: yok |

**CSharp\_stili\_var\_için\_yerleşik\_in_types**

- Bu kural ayarlandığında **true**, tercih ettiğiniz `var` değişkenler gibi yerleşik sistem türleriyle bildirmek için kullanılan `int`.
- Bu kural ayarlandığında **false**, üzerinden açık türü tercih et `var` gibi yerleşik sistem türleriyle değişkenleri bildirmeyi `int`.

Kod örnekleri:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

**CSharp\_stili\_var\_olduğunda\_türü\_is_apparent**

- Bu kural ayarlandığında **true**, tercih ettiğiniz `var` zaman türü zaten belirtilen bir bildirimi ifadesinin sağ tarafta.
- Bu kural ayarlandığında **false**, üzerinden açık türü tercih et `var` zaman türü zaten belirtilen bir bildirimi ifadesinin sağ tarafta.

Kod örnekleri:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

**CSharp\_stili\_var_elsewhere**

- Bu kural ayarlandığında **true**, tercih ettiğiniz `var` tüm durumlarda açık tür üzerinden başka bir kod stili kural tarafından geçersiz kılınmadığı sürece.
- Bu kural ayarlandığında **false**, üzerinden açık türü tercih et `var` tüm durumlarda, başka bir kod stili kural tarafından geçersiz kılınmadığı sürece.

Kod örnekleri:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="expression_bodied_members"></a>İfade gövdeli üyeler

Bu bölümdeki Stil kurallarının kullanımını ilgilendiriyor [ifade gövdeli üyeler](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) zaman tek bir ifadeye oluşur mantığı. Bu kural, yöntemleri, Oluşturucular, işleçler, özellikler, dizin oluşturucular ve erişimcileri için uygulanabilir.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli dil sürümleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_style_expression_bodied_methods | IDE0022 | C# 6.0 VE ÜZERİ | false: yok | 15.3 |
| csharp_style_expression_bodied_constructors | IDE0021 | C# 7.0 + | false: yok | 15.3 |
| csharp_style_expression_bodied_operators | IDE0023 ve IDE0024 | C# 7.0 + | false: yok | 15.3 |
| csharp_style_expression_bodied_properties | IDE0025 | C# 7.0 + | TRUE: yok | 15.3 |
| csharp_style_expression_bodied_indexers | IDE0026 | C# 7.0 + | TRUE: yok | 15.3 |
| csharp_style_expression_bodied_accessors | IDE0027 | C# 7.0 + | TRUE: yok | 15.3 |

**CSharp\_stili\_ifade\_bodied_methods**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | İfade gövdeli üyeler yöntemlerine tercih et |
| when_on_single_line | Bunlar tek bir satırda ne zaman metotlar için ifade gövdeli üyeler tercih et |
| false | Metotlar için blok gövdeleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

**CSharp\_stili\_ifade\_bodied_constructors**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | Oluşturucular için ifade gövdeli üyeler tercih et |
| when_on_single_line | Bunlar tek bir satırda ne zaman oluşturucular için ifade gövdeli üyeler tercih et |
| false | Oluşturucular için blok gövdeleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

**CSharp\_stili\_ifade\_bodied_operators**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | İfade gövdeli üyeler işleçleri tercih et |
| when_on_single_line | Bunlar tek bir satırda ne zaman işleçler için ifade gövdeli üyeler tercih et |
| false | İşleçler için blok gövdeleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

**CSharp\_stili\_ifade\_bodied_properties**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | İfade gövdeli üyeler özellikleri tercih et |
| when_on_single_line | Bunlar tek bir satırda ne zaman ifade gövdeli üyeler özellikleri tercih et |
| false | Blok gövdeleri özellikleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

**CSharp\_stili\_ifade\_bodied_indexers**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | Dizin oluşturucular için ifade gövdeli üyeler tercih et |
| when_on_single_line | Uygulanırsa, tek bir satırda olur, dizin oluşturucular için ifade gövdeli üyeler tercih et |
| false | Dizin oluşturucular için blok gövdeleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

**CSharp\_stili\_ifade\_bodied_accessors**

Bu kural, aşağıdaki tablodaki değerlerden kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| true | Erişimciler için ifade gövdeli üyeler tercih et |
| when_on_single_line | Bunlar tek bir satırda ne zaman erişimciler için ifade gövdeli üyeler tercih et |
| false | Erişimciler için blok gövdeleri tercih et |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
```

#### <a name="pattern_matching"></a>Desen eşleştirme

Bu bölümdeki Stil kurallarının kullanımını ilgilendiriyor [desen eşleştirme](/dotnet/csharp/pattern-matching) C#.

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli dil sürümleri ve varsayılan değerleri gösterir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_pattern_matching_over_is_with_cast_check | IDE0020 | C# 7.0 + | TRUE: öneri |
| csharp_style_pattern_matching_over_as_with_null_check | IDE0019 | C# 7.0 + | TRUE: öneri |

**CSharp\_stili\_deseni\_eşleşen\_üzerinden\_olduğu\_ile\_cast_check**

- Bu kural ayarlandığında **true**, yerine desen eşleştirme tercih `is` tür atamaları ifadelerle.
- Bu kural ayarlandığında **false**, tercih ettiğiniz `is` ifadelerle desen eşleştirme yerine tür atamaları.

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

**CSharp\_stili\_deseni\_eşleşen\_üzerinden\_olarak\_ile\_null_check**

- Bu kural ayarlandığında **true**, yerine desen eşleştirme tercih `as` sorun belirli bir tür olup olmadığını belirlemek için null denetimlerinin ifadelerle.
- Bu kural ayarlandığında **false**, tercih ettiğiniz `as` sorun belirli bir tür olup olmadığını belirlemek için desen eşleştirme yerine null denetimleri içeren ifadeler.

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="inlined_variable_declarations"></a>Satır içi değişken bildirimi

Bu stil kuralı endişeleriniz mi `out` veya satır içi değişkenler bildirilir. C# 7'de başlayarak, şunları yapabilirsiniz [bağımsız değişken listesinde bir yöntem çağrısının dışına çıkan bir değişkeni bildirmek](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), yerine ayrı bir değişken bildirimi.

Kural adı, kural kimliği, geçerli dil sürümleri ve varsayılan değerleri aşağıdaki tabloda gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan |
| --------- | -------- | -------------------- | ----------------------|
| csharp_style_inlined_variable_declaration | IDE0018 | C# 7.0 + | TRUE: öneri |

**CSharp\_stili\_satır içine alınmış\_variable_declaration**

- Bu kural ayarlandığında **true**, tercih ettiğiniz `out` değişkenler mümkün olduğunda, bir yöntem çağrısının bağımsız değişken listesindeki, satır içi olarak.
- Bu kural ayarlandığında **false**, tercih ettiğiniz `out` yöntem çağrısından önce bildirilmesi için değişkenleri.

Kod örnekleri:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

#### <a name="expression_level_csharp"></a>İfade düzeyi tercihleri

Stil kurallarının bu bölümdeki ifade düzeyi tercihleri, kullanımı dahil olmak üzere uğraşmak [varsayılan ifadeleri](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference), ayrıştırılmış değişkenleri ve anonim işlevler üzerinde yerel işlevler.

Aşağıdaki tabloda, kural adı, kural kimliği, geçerli dil sürümleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_simple_default_expression | IDE0034 | C# 7.1 + | TRUE: öneri | 15.3 |
| csharp_style_deconstructed_variable_declaration | IDE0042 | C# 7.0 + | TRUE: öneri | 15.5 |
| csharp_style_pattern_local_over_anonymous_function | IDE0039 | C# 7.0 + | TRUE: öneri | 15.5 |

**csharp\_prefer\_simple\_default_expression**

Bu stil kuralı kullanarak ilgiliyse [ `default` değişmez değer için varsayılan değer ifadeleri](/dotnet/csharp/programming-guide/statements-expressions-operators/default-value-expressions#default-literal-and-type-inference) zaman derleyici tanım Çıkarsama ifadenin türü.

- Bu kural ayarlandığında **true**, tercih ettiğiniz `default` üzerinden `default(T)`.
- Bu kural ayarlandığında **false**, tercih ettiğiniz `default(T)` üzerinden `default`.

Kod örnekleri:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

**CSharp\_stili\_deconstructed\_variable_declaration**

- Bu kural ayarlandığında **true**, ayrıştırılmış değişken bildirimini tercih et.
- Bu kural ayarlandığında **false**, değişken bildirimlerinde ayrıştırma tercih ediyorsunuz.

Kod örnekleri:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

**CSharp\_stili\_deseni\_yerel\_üzerinden\_anonymous_function**

- Bu kural ayarlandığında **true**, yerel işlevler üzerinde anonim işlevler tercih edin.
- Bu kural ayarlandığında **false**, anonim işlevler yerel işlevler üzerinde tercih edin.

Kod örnekleri:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
```

#### <a name="null_checking_csharp"></a>"Null" Tercihler denetleniyor

Bu kuralları önemli etrafında sözdizimi stil `null` kullanma dahil olmak üzere, denetimi `throw` ifadeleri veya `throw` ifadeleri ve null denetimi gerçekleştirmek veya koşullu birleşim işleci kullanmayı (`?.`) bir çağrılırken[lambda ifadesi](/dotnet/csharp/lambda-expressions).

Aşağıdaki tabloda, kuralı adları, kural kimliklerini, geçerli dil sürümleri ve varsayılan değerleri gösterir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan |
| --------- | ------- | -------------------- | ----------------------|
| csharp_style_throw_expression | IDE0016 | C# 7.0 + | TRUE: öneri |
| csharp_style_conditional_delegate_call | IDE0041 | C# 6.0 VE ÜZERİ | TRUE: öneri |

**csharp\_style\_throw_expression**

- Bu kural ayarlandığında **true**, kullanmayı tercih `throw` ifadeler yerine `throw` deyimleri.
- Bu kural ayarlandığında **false**, kullanmayı tercih `throw` yerine deyimleri `throw` ifadeler.

Kod örnekleri:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

**CSharp\_stili\_koşullu\_delegate_call**

- Bu kural ayarlandığında **true**, koşullu birleşim işleci kullanmayı tercih eder (`?.`) bir lambda ifadesi çağrılırken null gerçekleştirmek yerine kontrol edin.
- Bu kural ayarlandığında **false**, koşullu birleşim işleci kullanmak yerine, bir lambda ifadesi çağırmadan önce bir null denetimi gerçekleştirmek tercih ettiğiniz (`?.`).

Kod örnekleri:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="code_block"></a>Kod bloğu tercihleri

Bu stil kuralı kaşlı ayraçlar kullanımı ile ilgilidir `{ }` kod blokları kapsamak için.

Aşağıdaki tabloda, kural adı, kural kimliği, geçerli dil sürümleri, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Kural Kimliği | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| --------- | ------- | -------------------- | ----------------------| ---------------- |
| csharp_prefer_braces | IDE0011 | C# | TRUE: yok | 15.3 |

**CSharp\_tercih\_küme ayraçları**

- Bu kural ayarlandığında **true**, küme ayraçları için bir kod satırı bile tercih et.
- Bu kural ayarlandığında **false**, izin verilen herhangi bir küme ayracı tercih.

Kod örnekleri:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:none
```

## <a name="formatting-conventions"></a>Biçimlendirme kuralları

Biçimlendirme kurallarını kurallarının çoğu, aşağıdaki biçime sahiptir:

`rule_name = false|true`

Seçeneklerinden birini belirtin **true** (Bu stil tercih et) veya **false** (Bu stil tercih ediyorsunuz). Bir önem derecesi belirtmeyin. Bazı kurallar, true veya false yerine ne zaman ve nereye kuralı uygulamak açıklamak için diğer değerleri belirtin.

Aşağıdaki liste, Visual Studio'da kullanılabilen biçimlendirme kuralı kuralları gösterir:

- .NET biçimlendirme ayarları
    - [Using'leri düzenleme](#usings)
        - dotnet_sort_system_directives_first
- C# biçimlendirme ayarları
    - [Yeni satır seçenekleri](#newline)
        - csharp_new_line_before_open_brace
        - csharp_new_line_before_else
        - csharp_new_line_before_catch
        - csharp_new_line_before_finally
        - csharp_new_line_before_members_in_object_initializers
        - csharp_new_line_before_members_in_anonymous_types
        - csharp_new_line_between_query_expression_clauses
    - [Girintileme seçenekleri](#indent)
        - csharp_indent_case_contents
        - csharp_indent_switch_labels
        - csharp_indent_labels
    - [Aralık Seçenekleri](#spacing)
        - csharp_space_after_cast
        - csharp_space_after_keywords_in_control_flow_statements
        - csharp_space_between_method_declaration_parameter_list_parentheses
        - csharp_space_between_method_call_parameter_list_parentheses
        - csharp_space_between_parentheses
        - csharp_space_before_colon_in_inheritance_clause
        - csharp_space_after_colon_in_inheritance_clause
        - csharp_space_around_binary_operators
        - csharp_space_between_method_declaration_empty_parameter_list_parentheses
        - csharp_space_between_method_call_name_and_opening_parenthesis
        - csharp_space_between_method_call_empty_parameter_list_parentheses
    - [Kaydırma seçenekleri](#wrapping)
        - csharp_preserve_single_line_statements
        - csharp_preserve_single_line_blocks

### <a name="net-formatting-settings"></a>.NET biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları, C# ve Visual Basic için geçerlidir.

#### <a name="usings"></a>Using'leri düzenleme

Biçimlendirme bu kural ile ilgili diğer yönergeleri kullanarak System.* yerleşimini işlemiyle ilgili yönergeleri kullanarak.

Aşağıdaki tabloda, kural adı, geçerli diller, varsayılan değer ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| ----------- | -------------------- | ----------------------| ---------------- |
| dotnet_sort_system_directives_first | C# ve Visual Basic | true | 15.3 |

**DotNet\_sıralama\_sistem\_directives_first**

- Bu kural ayarlandığında **true**, System.* using yönergelerini alfabetik olarak sıralamak ve bunları diğer kullanımları önce yerleştirin.
- Bu kural ayarlandığında **false**, önce diğer yönergeleri kullanarak System.* yerleştirmeyin yönergeleri kullanarak.

Kod örnekleri:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# .NET formatting settings:
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
```

### <a name="c-formatting-settings"></a>C# biçimlendirme ayarları

Yalnızca C# kodu için bu bölümdeki biçimlendirme kurallarını uygulayın.

#### <a name="newline"></a>Yeni satır seçenekleri

Bu biçimlendirme kurallarını kod biçimlendirmek için yeni satırlar kullanımını ilgilendiriyor.

Aşağıdaki tabloda "Yeni satıra" kuralı adları gösterir. geçerli diller, varsayılan değerler ve öncelikle Visual Studio sürümü desteklenir:

| Kural adı | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_new_line_before_open_brace | C# | tüm | 15.3 |
| csharp_new_line_before_else | C# | true | 15.3 |
| csharp_new_line_before_catch | C# | true | 15.3 |
| csharp_new_line_before_finally | C# | true | 15.3 |
| csharp_new_line_before_members_in_object_initializers | C# | true | 15.3 |
| csharp_new_line_before_members_in_anonymous_types | C# | true | 15.3 |
| csharp_new_line_between_query_expression_clauses | C# | true | 15.3 |

**CSharp\_yeni\_satırı\_önce\_open_brace**

Bu kural, bir açık küme ayracı olup olmadığını işlemiyle ilgili `{` projeler yukarıdaki kodla aynı satırda veya yeni bir satıra yerleştirilmelidir. Bu kural için belirtmezseniz **true** veya **false**. Bunun yerine, belirttiğiniz **tüm**, **hiçbiri**, veya bir veya daha fazla öğe gibi kod **yöntemleri** veya **özellikleri**, bu kuralı ne zaman çalıştırılması tanımlamak için uygulanır. İzin verilen değerler tam listesini aşağıdaki tabloda gösterilmiştir:

| Değer | Açıklama
| ------------- |:-------------|
| erişimciler anonymous_methods, anonymous_types, control_blocks, olaylar, dizin oluşturucular, lambda ifadeleri, local_functions, yöntemleri, object_collection_array_initializers, özellikleri, türleri.<br>(Birden çok tür için Ayır ','). | Belirtilen kod öğelerini ("Allman" stil olarak da bilinir) için yeni bir satırdsa olacak şekilde küme ayraçları gerektirin |
| tüm | Tüm ifadeler ("Allman" stil) için yeni bir satırdsa olacak şekilde küme ayraçları gerektirin |
| yok | Küme ayraçları ("K & R") tüm ifadeler için aynı satırda olmasını gerektirin |

Kod örnekleri:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

**CSharp\_yeni\_satırı\_before_else**

- Bu kural ayarlandığında **true**, yerleştirin `else` yeni bir satıra deyimleri.
- Bu kural ayarlandığında **false**, yerleştirin `else` deyimleri aynı satırda.

Kod örnekleri:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

**CSharp\_yeni\_satırı\_before_catch**

- Bu kural ayarlandığında **true**, yerleştirin `catch` yeni bir satıra deyimleri.
- Bu kural ayarlandığında **false**, yerleştirin `catch` deyimleri aynı satırda.

Kod örnekleri:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

**CSharp\_yeni\_satırı\_before_finally**

- Bu kural ayarlandığında **true**, gerekli `finally` kapatma küme ayracından sonra yeni bir satıra olmasını deyimleri.
- Bu kural ayarlandığında **false**, gerekli `finally` kapanış küme ayracı ile aynı satırda olmasını deyimleri.

Kod örnekleri:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

**CSharp\_yeni\_satırı\_önce\_üyeleri\_içinde\_object_initializers**

- Bu kural ayarlandığında **true**, üyelerinin nesne başlatıcıları ayrı satırlarda olmasını gerektirir.
- Bu kural ayarlandığında **false**, aynı satırda bulunması için nesne başlatıcıları üyeleri gerektirir.

Kod örnekleri:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

**CSharp\_yeni\_satırı\_önce\_üyeleri\_içinde\_anonymous_types**

- Bu kural ayarlandığında **true**, ayrı satırlarda olmasını anonim türlerin üyelerini gerektirir.
- Bu kural ayarlandığında **false**, aynı satırda olmasını anonim türlerin üyelerini gerektirir.

Kod örnekleri:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

**csharp_new_line_between_query_expression_clauses**

- Bu kural ayarlandığında **true**, öğeleri sorgu ifadesi tümceleri ayrı satırlarda olmasını gerektirir.
- Bu kural ayarlandığında **false**, öğeleri sorgu ifadesi tümceleri aynı satırda olmasını gerektirir.

Kod örnekleri:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="indent"></a>Girintileme seçenekleri

Bu biçimlendirme kuralları biçimi koda girinti kullanımını ilgilendiriyor.

Aşağıdaki tabloda, kural adı, geçerli diller, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_indent_case_contents | C# | true | 15.3 |
| csharp_indent_switch_labels | C# | true | 15.3 |
| csharp_indent_labels | C# | no_change | 15.3 |

**CSharp\_girinti\_case_contents**

- Bu kural ayarlandığında **true**, girinti `switch` case içerikleri.
- Bu kural ayarlandığında **false**, değil Girintile `switch` case içerikleri.

Kod örnekleri:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**CSharp\_girinti\_switch_labels**

- Bu kural ayarlandığında **true**, girinti `switch` etiketler.
- Bu kural ayarlandığında **false**, değil Girintile `switch` etiketler.

Kod örnekleri:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

**CSharp\_indent_labels**

Bu kural kabul etmediği bir **true** veya **false** değeri; bunun yerine aşağıdaki tablodan bir değer olarak kabul eder:

| Değer | Açıklama |
| ----- |:----------- |
| flush_left | Etiketleri en soldaki sütuna yerleştirilir. |
| one_less_than_current | Etiketler tek tek geçerli bağlam için daha az girinti yerleştirilir |
| no_change | Etiketleri geçerli içerik olarak aynı girinti yer alır |

Kod örnekleri:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="spacing"></a>Aralık Seçenekleri

Bu biçimlendirme kuralları koduna boşluk karakterleri kullanımını ilgilendiriyor.

Aşağıdaki tabloda, kural adı, geçerli diller, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_space_after_cast | C# | false | 15.3 |
| csharp_space_after_keywords_in_control_flow_statements | C# | true | 15.3 |
| csharp_space_between_method_declaration_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_method_call_parameter_list_parentheses | C# | false | 15.3 |
| csharp_space_between_parentheses | C# | false | 15.3 |
| csharp_space_before_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_after_colon_in_inheritance_clause | C# | true | 15.7 |
| csharp_space_around_binary_operators | C# | before_and_after | 15.7 |
| csharp_space_between_method_declaration_empty_parameter_list_parentheses | C# | false | 15.7 |
| csharp_space_between_method_call_name_and_opening_parenthesis | C# | false | 15.7 |
| csharp_space_between_method_call_empty_parameter_list_parentheses | C# | false | 15.7 |

**CSharp\_alanı\_after_cast**

- Bu kural ayarlandığında **true**, atama ve değer arasında bir alan gerektirir.
- Bu kural ayarlandığında **false**, gerekli _hiçbir_ cast değeri arasındaki boşluk.

Kod örnekleri:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

**csharp_space_after_keywords_in_control_flow_statements**

- Bu kural ayarlandığında **true**, gibi bir alan sonra bir denetim akışı ifadesi bir anahtar sözcük gerektiren bir `for` döngü.
- Bu kural ayarlandığında **false**, gerekli _hiçbir_ gibi bir anahtar sözcüğü bir denetim akışı ifadesi içinde'sonra boşluk bir `for` döngü.

Kod örnekleri:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

**csharp_space_between_method_declaration_parameter_list_parentheses**

- Bu kural ayarlandığında **true**, açma parantezinden sonra ve bir yöntem bildiriminin parametre listesinin kapatma parantezinden önce bir boşluk karakteri yerleştirin.
- Bu kural ayarlandığında **false**, boşluk karakterleri açma parantezinden sonra ve kapatma parantezinden yöntemi bildirimi parametre listesini önce yerleştirmeyin.

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

**csharp_space_between_method_call_parameter_list_parentheses**

- Bu kural ayarlandığında **true**, açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce bir boşluk karakteri yerleştirin.
- Bu kural ayarlandığında **false**, boşluk karakterleri açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce yerleştirmeyin.

Kod örnekleri:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

**csharp_space_between_parentheses**

Bu kural, aşağıdaki tablodaki değerlerden bir veya daha fazla kabul eder:

| Değer | Açıklama |
| ----- |:------------|
| control_flow_statements | Denetim akış deyimlerindeki parantez arasında boşluk koyun |
| ifadeler | İfadelerin parantezler arasında boşluk koyun |
| type_casts | Tür atamaları parantezler arasında boşluk koyun |

Bu kural atlayın veya dışında bir değer kullanın, `control_flow_statements`, `expressions`, veya `type_casts`, ayar uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

**CSharp\_alanı\_önce\_iki nokta üst üste\_içinde\_inheritance_clause**

- Bu kural ayarlandığında **true**, iki nokta üst üste için tabanları veya bir tür bildiriminde arabirimleri önce bir alan gerektirir.
- Bu kural ayarlandığında **false**, gerekli _hiçbir_ için iki nokta üst üste tabanları veya bir tür bildiriminde arabirimleri önce boşluk.

Kod örnekleri:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

**CSharp\_alanı\_sonra\_iki nokta üst üste\_içinde\_inheritance_clause**

- Bu kural ayarlandığında **true**, iki nokta üst üste için tabanları veya bir tür bildiriminde arabirimleri sonra bir boşluk gerektirir.
- Bu kural ayarlandığında **false**, gerekli _hiçbir_ için iki nokta üst üste tabanları ya da bir tür bildiriminde arabirimleri sonra boşluk.

Kod örnekleri:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

**CSharp\_alanı\_etrafında\_binary_operators**

Bu kural aşağıdaki tablodan bir değer kabul eder:

| Değer | Açıklama |
| ----- |:------------|
| before_and_after | Önce ve ikili işleç sonra boşluk Ekle |
| yok | Önce ve sonra ikili işleç boşlukları Kaldır |
| yoksayma | İkili işleçler etrafındaki boşlukları yoksay |

Bu kural atlayın veya dışında bir değer kullanın, `before_and_after`, `none`, veya `ignore`, ayar uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

**csharp_space_between_method_declaration_empty_parameter_list_parentheses**

- Bu kural ayarlandığında **true**, yöntem bildiriminde için boş parametre listesi parantezlerinin içine boşluk ekleyin.
- Bu kural ayarlandığında **false**, yöntem bildiriminde için boş parametre listesi parantezlerinin içine boşluk kaldırın.

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_name_and_opening_parenthesis**

- Bu kural ayarlandığında **true**, yöntem çağrısı adı ve açma parantezi arasına boşluk ekleyin.
- Bu kural ayarlandığında **false**, yöntem çağrısı adı ve açma parantezi arasına boşluk kaldırın.

Kod örnekleri:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

**csharp_space_between_method_call_empty_parameter_list_parentheses**

- Bu kural ayarlandığında **true**, boş bağımsız değişken listesi parantezlerinin içine boşluk ekleyin.
- Bu kural ayarlandığında **false**, boş bağımsız değişken listesi parantezlerinin içine boşluk kaldırın.

Kod örnekleri:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
```

#### <a name="wrapping"></a>Kaydırma seçenekleri

Bu biçimlendirme kuralları ifadeleri ve kod blokları için ayrı satırlara karşı tek satır kullanımını ilgilendiriyor.

Aşağıdaki tabloda, kural adı, geçerli diller, varsayılan değerleri ve Visual Studio'nun desteklenen ilk sürüm gösterilmektedir:

| Kural adı | Geçerli diller | Visual Studio varsayılan | Visual Studio 2017 sürüm |
| ----------- | -------------------- | ----------------------| ---------------- |
| csharp_preserve_single_line_statements | C# | true | 15.3 |
| csharp_preserve_single_line_blocks | C# | true | 15.3 |

**csharp_preserve_single_line_statements**

- Bu kural ayarlandığında **true**, ifadeler ve üye bildirimlerini aynı satırda bırakın.
- Bu kural ayarlandığında **false**, ifadeler ve üye bildirimlerini farklı satırlarda bırakın.

Kod örnekleri:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

**csharp_preserve_single_line_blocks**

- Bu kural ayarlandığında **true**, kod bloğu tek satırda bırak.
- Bu kural ayarlandığında **false**, kod bloğu ayrı satırlarda bırakın.

Kod örnekleri:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

Örnek *.editorconfig* dosyası:

```EditorConfig
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

## <a name="example-editorconfig-file"></a>EditorConfig dosyası örneği

Başlamanıza yardımcı olmak için bir örnek aşağıdadır *.editorconfig* dosyasıyla varsayılan seçenekleri:

```EditorConfig
###############################
# Core EditorConfig Options   #
###############################

root = true

# All files
[*]
indent_style = space

# Code files
[*.{cs,csx,vb,vbx}]
indent_size = 4
insert_final_newline = true
charset = utf-8-bom

###############################
# .NET Coding Conventions     #
###############################

[*.{cs,vb}]
# Organize usings
dotnet_sort_system_directives_first = true

# this. preferences
dotnet_style_qualification_for_field = false:none
dotnet_style_qualification_for_property = false:none
dotnet_style_qualification_for_method = false:none
dotnet_style_qualification_for_event = false:none

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:none
dotnet_style_predefined_type_for_member_access = true:none

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:none
dotnet_style_readonly_field = true:suggestion

# Expression-level preferences
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent

###############################
# Naming Conventions          #
###############################

# Style Definitions
dotnet_naming_style.pascal_case_style.capitalization             = pascal_case

# Use PascalCase for constant fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.constant_fields_should_be_pascal_case.symbols  = constant_fields
dotnet_naming_rule.constant_fields_should_be_pascal_case.style    = pascal_case_style
dotnet_naming_symbols.constant_fields.applicable_kinds            = field
dotnet_naming_symbols.constant_fields.applicable_accessibilities  = *
dotnet_naming_symbols.constant_fields.required_modifiers          = const

###############################
# C# Code Style Rules         #
###############################

[*.cs]
# var preferences
csharp_style_var_for_built_in_types = true:none
csharp_style_var_when_type_is_apparent = true:none
csharp_style_var_elsewhere = true:none

# Expression-bodied members
csharp_style_expression_bodied_methods = false:none
csharp_style_expression_bodied_constructors = false:none
csharp_style_expression_bodied_operators = false:none
csharp_style_expression_bodied_properties = true:none
csharp_style_expression_bodied_indexers = true:none
csharp_style_expression_bodied_accessors = true:none

# Pattern-matching preferences
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion

# Null-checking preferences
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Expression-level preferences
csharp_prefer_braces = true:none
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion

###############################
# C# Formatting Rules         #
###############################

# New line preferences
csharp_new_line_before_open_brace = all
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left

# Space preferences
csharp_space_after_cast = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false

# Wrapping preferences
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true

##################################
# Visual Basic Code Style Rules  #
##################################

[*.vb]
# Modifier preferences
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
- [EditorConfig için .NET adlandırma kuralları](../ide/editorconfig-naming-conventions.md)
- [Taşınabilir özel düzenleyici seçenekleri oluşturma](../ide/create-portable-custom-editor-options.md)
- [.NET derleyici platformu'nın .editorconfig dosyasındaki](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
