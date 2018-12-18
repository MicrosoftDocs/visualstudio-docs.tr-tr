---
title: Sınıf Tasarımcısında Visual C++ Yapılandırmaları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 79b4adcfbcacc8cf342b5fc4183ae4fe27431b09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864777"
---
# <a name="visual-c-structures-in-class-designer"></a>Sınıf tasarımcısında Visual C++ yapılandırmaları

**Sınıf Tasarımcısı** anahtar sözcüğü ile bildirilen C++ yapıları destekleyen `struct`. Bir örneği verilmiştir:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Kullanma hakkında daha fazla bilgi için `struct` yazın, bkz: [yapı](/cpp/cpp/struct-cpp).

Sınıf diyagramında C++ yapı şeklinde görünür ve etiketi dışında sınıf şeklinin gibi çalışır **yapı** ve yuvarlak köşeler yerine dörtgen köşelerine sahiptir.

|Kod öğesi|Sınıf Tasarımcısı görünümü|
|------------------| - |
|`struct StructureName {};`|**StructureName**<br /><br /> Yapı|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual C++ Kodu ile Çalışma](working-with-visual-cpp-code.md)
- [Sınıflar ve Yapılar](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)