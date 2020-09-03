---
title: Sınıf Tasarımcısı 'de C++ Typedefs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590702"
---
# <a name="c-typedefs-in-class-designer"></a>Sınıf Tasarımcısı 'de C++ tür tanımları

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) deyimleri, bir ad ve temel alınan türü arasında bir veya daha fazla yöneltme katmanı oluşturur. **Sınıf Tasarımcısı** , anahtar sözcüğüyle belirtilen C++ typedef türlerini destekler `typedef` , örneğin:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Daha sonra bu türü bir örnek bildirmek için kullanabilirsiniz:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Sınıf ve yapı şekilleri

**Sınıf Tasarımcısı**, C++ typedef, typedef içinde belirtilen türde bir şekle sahiptir. Kaynak bildirirse `typedef class` , şekil yuvarlak köşeler ve Label **sınıfına**sahiptir. İçin `typedef struct` , şeklinin kare köşeleri ve Label **yapısı**vardır.

Sınıfların ve yapıların içinde bildirildiği iç içe tür tanımları olabilir. **Sınıf Tasarımcısı**, sınıf ve yapı şekilleri iç içe geçmiş bir typedef bildirimini iç içe geçmiş şekiller olarak gösterebilir.

TypeDef şekilleri, sağ tıklama menüsünde (bağlam menüsü) **ilişki olarak göster** ve **koleksiyon ilişkilendirme olarak göster** komutlarını destekler.

### <a name="class-typedef-example"></a>Sınıf typedef örneği

```cpp
class B {};
typedef B MyB;
```

![Sınıf Tasarımcısı 'de C++ sınıfı typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Struct typedef örneği

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Sınıf Tasarımcısı 'de C++ yapısı typedef](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Adlandırılmamış tür tanımları

Bir typedef adı olmadan bildirebilseniz de **Sınıf Tasarımcısı** belirttiğiniz etiket adını kullanmaz. **Sınıf Tasarımcısı** , **sınıf görünümü** oluşturduğu adı kullanır. Örneğin, aşağıdaki bildirim geçerlidir, ancak **sınıf görünümü** ve **Sınıf Tasarımcısı** **__unnamed**adlı bir nesne olarak görünür:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Sınıf Tasarımcısı** , kaynak türü bir işlev işaretçisi olan tür tanımları öğesini görüntülemez.

## <a name="see-also"></a>Ayrıca bkz.

- [C++ koduyla çalışma](working-with-visual-cpp-code.md)
- [Tür tanımları](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
