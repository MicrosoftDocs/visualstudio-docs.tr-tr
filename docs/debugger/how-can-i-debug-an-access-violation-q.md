---
title: Bir C++ erişim ihlali hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6f463f4e14e5be90422f73b299cb927a54fcfcef
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067268"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Nasıl bir C++ erişim ihlali hata Ayıklayabilirim?
## <a name="problem-description"></a>Sorun açıklaması  
 Kendi programımı bir erişim ihlali üretir. Bu sorunu nasıl ayıklayabilirim?  
  
## <a name="solution"></a>Çözüm  
 Birden çok işaretçi başvuru kod satırında bir erişim ihlali alırsanız, hangi işaretçi erişim ihlaline neden olduğunu bulmak zor olabilir. Visual Studio 2015 güncelleştirme 1'de başlayarak, özel durum iletişim kutusunda artık açıkça erişim ihlaline neden işaretçi adları.  
  
 Örneğin, aşağıdaki kodu göz önünde bulundurulduğunda, bir erişim ihlali almanız gerekir:  
  
```C++  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
        ClassC* C;  
        ClassB() {  
                C = new ClassC();  
        }  
     void printHello() {  
                cout << "hello world";  
        }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
      ClassA() {  
                B = nullptr;  
        }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
      A->B->printHello();  
}  
```  
  
 Visual Studio 2015 güncelleştirme 1'de bu kodu çalıştırırsanız, aşağıdaki özel durum iletişim kutusunu görmeniz gerekir:  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 İşaretçi erişim ihlaline neden neden belirleyemiyorsa, soruna işaretçi doğru şekilde atandığını emin olmak için kod boyunca izleme.  Bir parametre olarak geçirilir, doğru geçirilir ve yanlışlıkla oluşturma olmayan emin bir [yüzeysel kopya](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Ardından değerlerini istemeden yere programda veri kesme noktası işaretçisi, başka bir yerde programda değiştirilen olmadığından emin olmak için söz konusu oluşturarak değiştirilmekte olan değil olduğunu doğrulayın. Veri kesme noktaları hakkında daha fazla bilgi için bkz: veri kesme noktası bölümünde [kullanılarak kesme noktaları](../debugger/using-breakpoints.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)