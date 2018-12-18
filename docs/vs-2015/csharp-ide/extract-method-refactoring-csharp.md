---
title: Ayıklama yöntemi yeniden düzenlemesi (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cc05da79676beed5fa698f11843a6b7485280e71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228066"
---
# <a name="extract-method-refactoring-c"></a>Ayıklama Yöntemi Yeniden Düzenlemesi (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extrahovat metodu** varolan bir üye kod parçasında yeni bir yöntem oluşturmak için kolay bir yol sağlayan bir yeniden düzenleme işlemi.  
  
 Kullanarak **yöntemi ayıklama**, koddan varolan bir üyesinin kod bloğunun seçimi çekip çıkararak yeni bir yöntem oluşturabilirsiniz. Yeni, ayıklanan yöntemi seçili kodu içerir ve varolan bir üye seçili kod yeni yönteme bir çağrı ile değiştirilir. Kodun bir parçasını kendi yönteme kapatma hızlı bir şekilde sağlar ve kod yeniden kullanımını ve daha iyi okunabilirlik için doğru bir şekilde yeniden düzenleyin.  
  
 **Extrahovat metodu** aşağıdaki faydaları sağlar:  
  
-   En iyi kodlama uygulamalarını teşvik etmektedir ayrık, yeniden kullanılabilir yöntemleri vurgulayarak.  
  
-   Kod iyi kuruluş aracılığıyla kendi kendine tanım teşvik eder.  
  
     Daha fazla bilgi edinin, açıklayıcı adlar kullanılan, üst düzey yöntemleri olduğunda açıklamaları dizisi ister.  
  
-   Geçersiz kılma basitleştirmek için yöntemleri dağıtımına oluşturulmasını önerir.  
  
-   Kod yinelemesinden azaltır.  
  
### <a name="to-use-extract-method"></a>Ayıklama yöntemi kullanmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `ExtractMethod`ve ardından `Program` ile aşağıdaki kod örneği.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Ayıklamak istediğiniz kod parçasını seçin:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Üzerinde **yeniden düzenleme** menüsünde tıklatın **yöntemi ayıklama**.  
  
     **Yöntemi ayıklama** iletişim kutusu görüntülenir.  
  
     Alternatif olarak, ayrıca CTRL + R klavye kısayolunu görüntülemek için M yazabilirsiniz **yöntemi ayıklama** iletişim kutusu.  
  
     Ayrıca seçili sağ tıklayabilirsiniz kod, işaret **yeniden düzenleyin**ve ardından **yöntemi ayıklama** görüntülenecek **yöntemi ayıklama** iletişim kutusu.  
  
4.  Yeni bir yöntem için bir ad belirtin `CircleArea`, **yeni yöntem adı** kutusu.  
  
     Yeni metot imzasını önizlemesini görüntüler altında **metot imzasını Önizle**.  
  
5.  **Tamam**'ı tıklatın.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanırken **yöntemi ayıklama** komutunu kaynak üye aynı sınıftaki aşağıdaki yeni yöntemi eklenir.  
  
## <a name="partial-types"></a>Kısmi türler  
 Sınıf kısmi bir türde ise **yöntemi ayıklama** kaynak üye hemen ardından yeni bir yöntem oluşturur. **Extrahovat metodu** örnek veri yeni metodu içindeki kod tarafından başvurulduğunda statik bir yöntem oluşturarak yeni metodun imzası belirler.  
  
## <a name="generic-type-parameters"></a>Genel Tür Parametreleri  
 Sınırlandırılmamış genel tür parametresi olan bir yönteme ayıkladığınızda, oluşturulan kod değil ekleyeceksiniz `ref` değiştiriciyi parametreye bir değer atanmadığı sürece. Ayıklanan Metoda başvuru türleri genel tür bağımsız değişkeni destekleyecek sonra el ile eklemelisiniz `ref` yöntem imzası parametre değiştiricisi.  
  
## <a name="anonymous-methods"></a>Anonim Yöntemler  
 Ardından Visual Studio bildirilen veya başvurulan anonim yöntemin dışında bir yerel değişken başvuru içeren bir anonim yöntem parçası genişletmeye çalışırsanız, olası anlamsal değişiklikler hakkında uyarır.  
  
 Değer, anonim bir yöntem, yerel bir değişken değerini kullandığında, anonim yöntemin yürütüldüğü şu anda elde edilir. Anonim bir yöntem başka bir yönteme ayıklandığında yerel değişkenin değeri ayıklanan Metoda yapılan çağrının anda elde edilir.  
  
 Aşağıdaki örnek bu anlamsal değişiklik gösterir. Bu kod, ardından yürütülürse **11** konsola yazdırılır. Kullanırsanız **yöntemi ayıklama** kendi yönteme kod açıklamaları işaretlenmiş kod bölgesi ayıklayın ve ardından yeniden düzenlenmiş kodu yürütmek için **10** konsola yazdırılır.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Bu durumu çözmek için sınıf anonim yöntem alanları kullanılan yerel değişkenler olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Düzenleme (C#)](../csharp-ide/refactoring-csharp.md)