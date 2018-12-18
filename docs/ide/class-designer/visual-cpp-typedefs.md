---
title: Sınıf Tasarımcısında Visual C++ Typedefs
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb831422df42a246a5d5c23ccdd480bce47a0e6
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958340"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Sınıf tasarımcısında Visual C++ typedefs

[TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) deyimleri yöneltme bir ad ve temel alınan türü arasında bir veya daha fazla katmanı oluşturun. **Sınıf Tasarımcısı** anahtar sözcüğüyle bildirilen C++ typedef türlerini destekler `typedef`, örneğin:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Ardından bu tür bir örneği bildirmek için de kullanabilirsiniz:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Sınıf ve yapı şekiller

İçinde **Sınıf Tasarımcısı**, Şekil typedef belirtilen türde bir C++ typedef sahiptir. Kaynak bildirirse `typedef class`, Şekil köşeleri ve etiket yuvarlanmış **sınıfı**. İçin `typedef struct`, Şekil kare köşeleri ve etiket sahip **yapısı**.

Sınıfları ve yapıları bunların içinde bildirilen iç içe geçmiş tür tanımları sahip olabilir. İçinde **Sınıf Tasarımcısı**, sınıf ve yapısı şekiller olarak içe şekillerin iç içe geçmiş typedef bildirimleri gösterebilir.

TypeDef şekilleri Destek **Göster ilişkilendirmesi olarak** ve **Göster koleksiyon ilişkilendirmesini** bağlam menüsünde komutları.

### <a name="class-typedef-example"></a>Sınıf typedef örneği

```cpp
class B {};
typedef B MyB;
```

![Sınıf tasarımcısında C++ sınıfı typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Yapı typedef örneği

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Sınıf tasarımcısında C++ yapısı typedef](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Adlandırılmamış tür tanımları

Bir ad olmadan bir typedef bildirebilir rağmen **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. **Sınıf Tasarımcısı** adını kullanır, **sınıf görünümü** oluşturur. Örneğin, aşağıdaki bildirimi geçerlidir, ancak görünür **sınıf görünümü** ve **Sınıf Tasarımcısı** adlı bir nesne olarak **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Sınıf Tasarımcısı** kaynak türü, bir işlev işaretçisi olan tür tanımları görüntülenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ kodu ile çalışma](working-with-visual-cpp-code.md)
- [Tür tanımları](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)