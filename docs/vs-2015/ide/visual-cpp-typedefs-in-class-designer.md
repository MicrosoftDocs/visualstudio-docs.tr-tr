---
title: Sınıf tasarımcısında Visual C++ Typedefs | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ba65af46589e01aa5473b5757124ed184da2197
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230236"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Typedefs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TypeDef deyimleri, bir ad ve temel alınan türü arasında bir yöneltme bir veya daha fazla katmanı oluşturun. Sınıf Tasarımcısı anahtar sözcüğü ile bildirilen C++ typedef türleri destekleyen `typedef`, örneğin:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
 Ardından bu tür bir örneği bildirmek için de kullanabilirsiniz:  
  
 `COORD OriginPoint;`  
  
 Sınıf Tasarımcısı, adı olmadan bir typedef bildirebilirsiniz, ancak belirttiğiniz etiket adı kullanmaz; Bu, sınıf görünümü oluşturan adı kullanacaksınız. Örneğin, aşağıdaki bildirimi geçerlidir, ancak adlı bir nesne sınıf görünümü ve Sınıf Tasarımcısı içinde göründüğü **__unnamed**:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```  
  
 Kullanma hakkında daha fazla bilgi için `typedef` yazın, bkz: [(NOTINBUILD) typedef tanımlayıcısı](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1).  
  
 Bir C++ typedef şekli typedef içinde belirtilen tür şeklini sahiptir. Örneğin, kaynak bildirirse `typedef class`, şeklin köşe ve etiket yuvarlanmış **sınıfı**. İçin `typedef struct`, Şekil köşeler ve etikete sahiptir **yapı**.  
  
 Bunların içinde bildirilen iç içe geçmiş tür tanımları, sınıfları ve yapıları olabilir; Bu nedenle, sınıf ve yapı şekilleri iç içe geçmiş typedef bildirimleri iç içe geçmiş şekillere gösterebilirsiniz.  
  
 TypeDef şekilleri Destek **ilişkilendirmesi olarak göster** ve **koleksiyon ilişkilendirmesi olarak göster** bağlam menüsü komutları.  
  
 Sınıf Tasarımcısı'nı destekleyen typdef türlerin bazı örnekleri şunlardır:  
  
 `typedef type name`  
  
 *adı* : *türü*  
  
 typedef  
  
 Bağlama türü için bir ilişkilendirme çizgisi çizen *adı*, mümkünse.  
  
 `typedef void (*func)(int)`  
  
 `func: void (*)(int)`  
  
 typedef  
  
 İşlev işaretçileri için TypeDef. Hiçbir ilişkilendirme çizgisi çizilir.  
  
 Bir işlev işaretçisi kaynak türü ise, Sınıf Tasarımcısı bir tür tanımı görüntülemez.  
  
```  
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
 `MyInt: int`  
  
 typedef  
  
 `A`  
  
 örneği  
  
 Kaynak türü şekilden hedef türü şekle işaret eden bir ilişkilendirme çizgisi çizer.  
  
 `Class B {};`  
  
 `typedef B MyB;`  
  
 `B`  
  
 örneği  
  
 `MyB : B`  
  
 typedef  
  
 Typedef şekle sağ tıklayıp tıklayarak **ilişkilendirme olarak göster** typedef veya sınıf görüntüler ve **diğer adını** satır birleştirme (bir ilişkilendirme çizgisi için benzer) iki şekil.  
  
 `typedef B MyB;`  
  
 `typedef MyB A;`  
  
 `MyBar : Bar`  
  
 typedef  
  
 Yukarıdakiyle aynı.  
  
```  
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
 `B`  
  
 örneği  
  
 `MyB : B`  
  
 typedef  
  
 `A`  
  
 örneği  
  
 `MyB` iç içe geçmiş tür tanımı şekildir.  
  
 `#include <vector>`  
  
 `...`  
  
 `using namespace std;`  
  
 `...`  
  
 `typedef vector<int> MyIntVect;`  
  
 `vector<T>`Sınıfı  
  
 `MyIntVect : vector<int>`  
  
 typedef  
  
 `class B {};`  
  
 `typedef B MyB;`  
  
 `class A : MyB {};`  
  
 `MyB : B`  
  
 typedef  
  
 B -&GT;  
  
 `B`  
  
 `A`  
  
 örneği  
  
 MyB ->  
  
 Sınıf Tasarımcısı, bağlam menüsü komutu kullanarak bu tür bir ilişki görüntüleme desteklemez.  
  
 `#include <vector>`  
  
 `Typedef MyIntVect std::vector<int>;`  
  
 `Class MyVect : MyIntVect {};`  
  
 `std::vector<T>`  
  
 örneği  
  
 `MyIntVect : std::vector<int>`  
  
 typedef  
  
 `MyVect`  
  
 örneği  
  
 MyIntVect ->  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual C++ kodu (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-visual-cpp-code-class-designer.md)   
 [(NOTINBUILD) typedef tanımlayıcısı](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)



