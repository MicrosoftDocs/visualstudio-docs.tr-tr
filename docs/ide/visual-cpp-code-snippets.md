---
title: Visual C++ kod parçacıkları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: f119f3b2bc438eacfaaa722bd57fb440aa303052
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948934"
---
# <a name="visual-c-code-snippets"></a>Visual C++ kod parçacıkları

Visual Studio'da kod parçacıkları, kod sık kullanılan C++ kod dosyalarınızı eklemek için kullanabilirsiniz. Genel olarak, çok aynı şekilde olduğu gibi C# kod parçacıkları kullanabilirsiniz, ancak varsayılan kod parçacıkları kümesini farklıdır.

Bir kod parçacığı belirli bir konumda kodunuza (ekleme) ekleyin veya bir kod parçacığı ile seçilen kod çevreleyen.

## <a name="insert-a-code-snippet"></a>Kod parçacığı Ekle

Kod parçacığını eklemek için bir C++ kod dosyasını açın (*.cpp* veya *.h*) içindeki dosyanın bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsü alma ve seçmek için sağ tıklama **kod parçacığı Ekle**

- İçinde **Düzenle / IntelliSense** menüsünde **kod parçacığı Ekle**

- Kısayol tuşlarını kullanın: **Ctrl**+**K**+**X**

Sürümünden itibaren seçenekleri listesini görmelisiniz **#if**. Seçtiğinizde, **#if**, dosyaya eklenen aşağıdaki kodu görmeniz gerekir:

```cpp
#if 0

#endif // 0
```

Daha sonra değiştirebilirsiniz **0** doğru koşulu.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Seçili kod kapsamak için kod parçacığını kullanın.

Seçili kod kapsamak için kod parçacığı kullanmak için bir satır (veya birden fazla satır) seçin ve aşağıdakilerden birini yapın:

- Bağlam menüsü almak için sağ tıklatın ve seçin **Surround With**

- Gelen **Düzenle** > **IntelliSense** menüsünde **Surround With**

- Klavyeyi kullanarak, tuşuna basın: **Ctrl**+**K**+**S**

Seçin **#if**. Bunun gibi bir şey görmeniz gerekir:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

0 ile doğru koşul daha sonra değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ kod parçacıkları tam bir listesini nerede bulabilirim?

Sayfasına gidip C++ kod parçacıkları tam listesini bulabilirsiniz **kod parçacıkları Yöneticisi** (üzerinde **Araçları** menüsü) ve ayarı **dil** için **Visual C++** . Penceresinde **Visual C++**. Alfabetik sırada tüm C++ kod parçacıkları adını görmeniz gerekir.

Çoğu kod parçacıkları adlarını anlamı kolayca anlaşılır ancak bazı adları kafa karıştırıcı.

## <a name="class-vs-classi"></a>Classi sınıfı

**Sınıfı** kod parçacığı sağlar adlı bir sınıf tanımı `MyClass`uygun varsayılan oluşturucu ve yıkıcı, oluşturucu ve yıkıcı tanımlarını sınıfı dışında bulunduğu yeri:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

**Classi** kod parçacığı da adlı bir sınıf tanımı sağlar `MyClass`, ancak varsayılan oluşturucu ve yıkıcı sınıf tanımının içinde tanımlanır:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>için forr vs rfor karşılaştırması

Vardır üç farklı **için** farklı sağlayan kod parçacıkları, `for` döngüleri.

**Rfor** kod parçacığı sağlayan bir [aralık tabanlı](/cpp/cpp/range-based-for-statement-cpp) for döngüsü (bağlantı). Tento konstruktor je dizin tabanlı üzerinden tercih edilen `for` döngüleri.

```cpp
for (auto& i : v)
{

}
```

**İçin** kod parçacığı sağlayan bir `for` Döngü koşulu uzunluğuna dayalıdır (içinde `size_t`) bir nesnenin.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Forr** kod parçacığı sağlar ters `for` Döngü koşulu uzunluğu nesnenin üzerinde (tamsayı) dayanır.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı kod parçacığını (~)

Yıkıcı kod parçacığını (**~**) farklı bağlamda farklı bir davranış gösterir. Bu kod parçacığı bir sınıf içinde eklerseniz, o sınıf için yok edici sağlar. Örneğin, aşağıdaki kod verilen:

```cpp
class SomeClass {

};
```

Yıkıcı kod parçacığını eklemek, bir yok edici için sağladığı `SomeClass`:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Sınıf dışındaki yok Edicisi parçacığı eklemeye çalışırsanız, bir yer tutucu adıyla bir yok edici sağlar:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)