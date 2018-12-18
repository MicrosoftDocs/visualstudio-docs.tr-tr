---
title: Sınıf Tasarımcısında Visual C++ Sınıfları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2ff2b6660b7ef7530d3a37d251904fa54b5ce0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856203"
---
# <a name="visual-c-classes-in-class-designer"></a>Sınıf tasarımcısında Visual C++ sınıfları

**Sınıf Tasarımcısı** C++ sınıflarını destekler ve Visual Basic aynı şekilde yerel C++ sınıfları görselleştiren ve C# C++ sınıfları birden çok devralma ilişkisi olabilir dışında şekiller, sınıf. Daha fazla alanlar ve yöntemler sınıfında göstermek veya alanından tasarruf etmek için daraltılabilir sınıf şeklinin genişletebilirsiniz.

> [!NOTE]
> **Sınıf Tasarımcısı** birleşimler (bellek tahsis sınıfı özel bir tür olduğundan yalnızca Birliği'nin en büyük veri üyesi için gereken miktar) desteklemez.

## <a name="simple-inheritance"></a>Basit devralma

Birden fazla sınıf bir sınıf diyagramına sürükleyin ve sınıfların sınıf devralma ilişkisi olan bir ok bunları birbirine bağlar. Yönde taban sınıfının ok işaret eder. Aşağıdaki sınıflar, bir sınıf diyagramında görüntülendiğinde, örneğin, bir ok, B'den y: için işaret eden bağlanır

```cpp
class A {};
class B : A {};
```

Ayrıca yalnızca Sınıf B sınıf diyagramına sürükleyin, sınıf şeklinin B için sağ tıklayın ve ardından **temel sınıfları Göster**. Bu, onun temel sınıfından görüntüler: A.

## <a name="multiple-inheritance"></a>Çoklu devralma

**Sınıf Tasarımcısı** birden çok sınıf devralma ilişkilerinin görsel öğeyi destekler. *Birden çok devralma* türetilmiş bir sınıf birden fazla temel sınıfın özniteliklerine sahip olduğunda kullanılır. Birden çok devralma bir örneği verilmiştir:

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Birden fazla sınıf sınıf diyagramına sürükleyin ve sınıfları birden çok sınıf devralma ilişkisi, bir ok bunları birbirine bağlar. Temel sınıflar yönünde ok işaret eder.

Sınıf şeklinin sağ tıklatıp **temel sınıfları Göster** seçilen sınıf için temel sınıflarını görüntüler.

> [!NOTE]
> **Türetilmiş sınıfları Göster** komutu, C++ kodu için desteklenmiyor. Türetilen sınıfların giderek görüntüleyebilirsiniz **sınıf görünümü**türü düğümü genişletme, genişletme **türetilen türler** alt ve sonra bu türleri sınıf diyagramına sürükleyebilir sürükleyerek.

Birden çok sınıf devralma hakkında daha fazla bilgi için bkz: [birden çok devralma](https://msdn.microsoft.com/library/6td5yws2.aspx) ve [birden çok temel sınıflar](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Soyut sınıflar

**Sınıf Tasarımcısı** destekler soyut sınıflar (aynı zamanda "soyut temel sınıflar" olarak adlandırılır). Bu, hiçbir zaman örneği ancak kendisinden başka sınıflar türetilip sınıflardır. Bu belgedeki "Birden çok devralma" bir örnek kullanarak örneği `Bird` sınıfına aşağıdaki gibi ayrı nesneleri:

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Ancak, örneklemek istediğinize değil `Swimmer` ayrı ayrı nesneler olarak sınıf. Yalnızca diğer tür hayvan sınıfı, örneğin, türetmeniz planladığınız `Penguin`, `Whale`, ve `Fish`. Bu durumda, bildirirsiniz `Swimmer` sınıfı soyut bir temel sınıf olarak.

Bir sınıfı soyut olarak bildirmek için kullanabileceğiniz `abstract` anahtar sözcüğü. Özet olarak işaretlenmiş veya soyut bir sınıf, dahil edilen üyeleri sanal ve soyut sınıftan türeyen sınıflar tarafından uygulanmalıdır.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

En az bir saf sanal işlevi dahil ederek bir sınıfı soyut olarak da bildirebilirsiniz:

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Bir sınıf diyagramında sınıf adı bu bildirimleri görüntülediğinizde `Swimmer` ve kendi saf sanal işlevi `swim` italik gösterimi ile birlikte bir soyut sınıf şeklinde görüntülenen **soyut sınıf**. Bir noktalı çizgi kenarlığını olması dışında soyut sınıf tür şeklini, normal bir sınıfın aynı olduğuna dikkat edin.

Soyut bir temel sınıftan türetilmiş bir sınıf, taban sınıftaki her saf sanal işlevi geçersiz kılmanız gerekir veya türetilmiş bir sınıf örneği oluşturulamıyor. Bu nedenle, örneğin, türetirseniz bir `Fish` gelen sınıfı `Swimmer` sınıfı `Fish` geçersiz kılmanız gerekir `swim` yöntemi:

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Bu kod bir sınıf diyagramında görüntülediğinizde **Sınıf Tasarımcısı** bir devralma satırından çizer `Fish` için `Swimmer`.

## <a name="anonymous-classes"></a>Anonim sınıflar

**Sınıf Tasarımcısı** anonim sınıflarını destekler. *Anonim sınıf türleri* sınıfları bir tanımlayıcı olarak bildirilir. Bunlar bir oluşturucu veya yıkıcı olamaz, İşlevler için bağımsız değişken olarak geçirilemez ve işlevlerden dönüş değerleri döndürülemez. Anonim bir sınıf, bir sınıf adı aşağıdaki örnekte olduğu gibi bir typedef adı değiştirmek için kullanabilirsiniz:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Yapılar, anonim olarak da olabilir. **Sınıf Tasarımcısı** ilgili türünü görüntüler gibi aynı yapıları ve anonim sınıflarını görüntüler. Bildirme ve anonim sınıfları ve yapıları görüntüle ancak **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. Bu, sınıf görünümü oluşturan adı kullanacaksınız. Sınıf veya yapı, Sınıf Görünümü'nde görünür ve **Sınıf Tasarımcısı** adlı bir öğe olarak **__unnamed**.

Anonim sınıflar hakkında daha fazla bilgi için bkz. [anonim sınıf türleri](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Şablon sınıfları

**Sınıf Tasarımcısı** şablon sınıfının görselleştirme destekler. İç içe geçmiş bildirimleri desteklenir. Aşağıdaki tabloda, bazı tipik bildirimlerini gösterir.


| Kod öğesi | Sınıf Tasarımcısı görünümü |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Şablon sınıfı |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon sınıfı |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Şablon sınıfı |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Şablon sınıfı |

Aşağıdaki tabloda, kısmi özelleştirme bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon sınıfı|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon sınıfı|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda, kısmi özelleştirmede devralma bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon sınıfı<br /><br /> `B`<br /><br /> örneği<br /><br /> (nokta sınıfı için)<br /><br /> `C`<br /><br /> örneği<br /><br /> (nokta sınıfı için)|

Aşağıdaki tabloda, şablon işlevleri kısmi özelleştirmede bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> FUNC\<T, U > (+ 1 aşırı yükleme)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon sınıfı<br /><br /> (B altında bir sınıf içinde barındırılan **iç içe türler**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> örneği<br /><br /> C ->\<int ><br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda, şablon devralma bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> örneği<br /><br /> B -&GT;<br /><br /> `C<int>`<br /><br /> örneği<br /><br /> (B altında C sınıfı içinde barındırılan **iç içe türler**)<br /><br /> `C<T>`<br /><br /> Şablon sınıfı|

Aşağıdaki tabloda, kurallı özel sınıfın bağlantı bazı örnekler gösterilmektedir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> örneği<br /><br /> C ->\<int ><br /><br /> `C<int>`<br /><br /> örneği<br /><br /> `C<T>`<br /><br /> Şablon sınıfı<br /><br /> `D`<br /><br /> örneği<br /><br /> C ->\<kayan noktalı sayı >|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Min \<T >|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [Anonim Sınıf Türleri](/cpp/cpp/anonymous-class-types)
- [Birden çok devralma](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [Birden Çok Taban Sınıfı](/cpp/cpp/multiple-base-classes)
- [Şablonlar](/cpp/cpp/templates-cpp)