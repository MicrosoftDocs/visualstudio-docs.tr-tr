---
title: Kod parçacıkları Visual C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 213f4299ac71c08118563a008abe065f2c02423e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655398"
---
# <a name="visual-c-code-snippets"></a>Visual C++ Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, C++ kod dosyalarınıza yaygın olarak kullanılan kodu eklemek için kod parçacıklarını kullanabilirsiniz. Genel olarak, kod parçacıklarını C# ile aynı şekilde kullanabilirsiniz, ancak varsayılan kod parçacıkları kümesi farklıdır.

 Kodunuzda belirli bir konuma (ekleme) bir kod parçacığı ekleyebilir veya seçili bir kodu kod parçacığı ile çevreleyin.

## <a name="inserting-a-code-snippet"></a>Kod parçacığı ekleme
 Bir kod parçacığı eklemek için bir C++ kod dosyası (. cpp veya. h) açın, dosyanın içinde herhangi bir yere tıklayın ve aşağıdakilerden birini yapın:

- Bağlam menüsünü almak için sağ tıklayın ve **kod parçacığı Ekle** ' yi seçin.

- **Düzenle/IntelliSense** menüsünde **kod parçacığı Ekle** ' yi seçin.

- Kısayol tuşlarını kullanın: **CTRL + K + X**

  **#İf**başlayan seçeneklerin bir listesini görmeniz gerekir. **#İf**' yi seçtiğinizde, dosyaya aşağıdaki kodun eklendiğini görmeniz gerekir:

```cpp
#if 0

#endif // 0
```

 Daha sonra 0 değerini doğru koşulla değiştirebilirsiniz.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Seçilen kodu çevrelemek için bir kod parçacığı kullanma
 Seçilen kodu çevrelemek için bir kod parçacığı kullanmak için bir satır (veya birden çok satır) seçin ve aşağıdakilerden birini yapın:

1. Bağlam menüsünü almak için sağ tıklayın ve şununla **Çevrele** ' yi seçin

2. **Düzenle/IntelliSense** menüsünde **Şununla Çevrele** ' yi seçin

3. Kısayol tuşlarını kullanın: **CTRL + K + S**

   **#İf**seçin. Şuna benzer bir şey görmeniz gerekir:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

 Daha sonra 0 değerini doğru koşulla değiştirebilirsiniz.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ kod parçacıklarının tamamen bir listesini nerede bulabilirim?
 C++ kod parçacıklarının tüm listesini **kod parçacıkları Yöneticisi** ' ne giderek ( **Araçlar** menüsünde) ve **dili** **Visual C++** olarak ayarlayarak bulabilirsiniz. Aşağıdaki pencerede **Visual C++**' ı genişletin. Tüm C++ kod parçacıklarının adlarını alfabetik sırada görmeniz gerekir.

 Çoğu kod parçacıklarının adı kendi kendine açıklayıcıdır, ancak bazı adlar kafa karıştırıcı olabilir.

## <a name="class-vs-classi"></a>Sınıf ve classı karşılaştırması
 **Sınıf** parçacığı, uygun varsayılan Oluşturucu ve yıkıcısıyla MyClass adlı bir sınıfın tanımını sağlar; burada Oluşturucu ve yıkıcının tanımlarının sınıfın dışında bulunduğu bir değer:

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

 Classı kod parçacığı, MyClass adlı bir sınıfın tanımını da sağlar, ancak varsayılan Oluşturucu ve yıkıcısı sınıf tanımı içinde tanımlanmıştır:

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

## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Vs. ForEach vs. öğrencilerinize vs rfor için
 Farklı türlerde döngüler sağlayan kod parçacıkları için dört farklı vardır.

 **For** kod parçacığında, `for` koşulun bir nesnenin uzunluğuna (içindeki) göre kullanıldığı bir döngü sağlar `size_t` :

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

 **Foreach** parçacığı, `for each` bir koleksiyonun üyeleri üzerinde yineleme yapan bir döngü sağlar:

```cpp
for each (object var in collection_to_loop)
{

}
```

 **Öğrencilerinize** kod parçacığı, `for` koşulun bir nesnenin uzunluğuna (tamsayı cinsinden) dayanmakta olduğu ters bir döngü sağlar:

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

 **Rfor** kod parçacığı, [Aralık tabanlı](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) bir for döngüsü (bağlantı) sağlar:

```cpp
for (auto& i : v)
{

}
```

## <a name="the-destructor-snippet-"></a>Yıkıcı parçacığı (~)
 Yıkıcı parçacığı ( **~** ) farklı bağlamlarda farklı davranışlar gösterir. Bu kod parçacığını bir sınıfın içine eklerseniz, bu sınıf için bir yıkıcı sağlar. Örneğin, aşağıdaki kod verildiğinde:

```cpp
class SomeClass {

};
```

 Yıkıcı parçacığı eklerseniz, SomeClass için bir yıkıcı sağlar:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

 Yıkıcı parçacığı bir sınıfın dışında eklemeye çalışırsanız, yer tutucu adına sahip bir yıkıcı sağlar:

```cpp
~TypeNamePlaceholder()
{

```
