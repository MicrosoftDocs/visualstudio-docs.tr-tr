---
title: 'Nasıl yapılır: sınıfı kısmi sınıflara (Sınıf Tasarımcısı) bölme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6ae389e3bfe32e2e040da5bef3f41a51ff69555d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245485"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Nasıl Yapılır: Sınıfı Kısmi Sınıflara Bölme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanarak bir sınıf veya yapı çeşitli bildirimler arasında bildirimi bölebilirsiniz `Partial` Visual Basic'teki veya `partial` anahtar sözcüğü Visual C#. İstediğiniz sayıda farklı kaynak dosyaları veya bir kaynak dosyasında istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz. Ancak, tüm bildirimler aynı derleme ve aynı ad olmalıdır.  
  
 Kısmi sınıflar çeşitli durumlarda yararlı olur. Örneğin, bir sınıf içinde birden fazla dosya ayırma büyük projeleri üzerinde çalışıyorsanız, aynı anda üzerinde çalışmak birden fazla Programcı sağlar. Visual Studio oluşturan kod ile çalışırken, sınıf kaynak dosyasını yeniden oluşturmak zorunda kalmadan değiştirebilirsiniz. (Visual Studio oluşturan kod örnekleri Windows Formları ve Web hizmeti sarmalayıcı kodu içerir.) Bu nedenle, otomatik olarak oluşturulan sınıfları oluşturan Visual Studio dosyayı değiştirmek zorunda kalmadan kullanan kodu oluşturabilirsiniz.  
  
 Kısmi yöntemler iki tür vardır. Visual C# içinde bildirme ve uygulama çağrılır; Visual Basic'te, bunlara bildirimini ve uygulamasını verilir.  
  
 Sınıf Tasarımcısı, kısmi sınıflar ve yöntemler destekler. Tür şeklini sınıf diyagramı içinde kısmi sınıfın tek bildirimde konumunu ifade eder. Kısmi sınıf birden çok dosyalarında tanımlandıysa, Sınıf Tasarımcısı, ayarlayarak kullanacağı bildirimi konumu belirtebilirsiniz **yeni üye konumu** özelliğinde **özellikleri** penceresi. Sınıf şeklinin çift tıkladığınızda, diğer bir deyişle, Sınıf Tasarımcısı tarafından tanımlanmış sınıf bildirimi içeren kaynak dosyayı gider **yeni üye konumu** özelliği. Sınıf şeklinin içinde kısmi bir yöntemi çift tıkladığınızda, Sınıf Tasarımcısı için kısmi yöntem bildiriminde gider. Ayrıca, **özellikleri** penceresinde **dosya adı** özelliği bildirimi konuma başvuruyor. Kısmi sınıflar için **dosya adı** bildirimini ve uygulamasını bu sınıfın kodu içeren dosyaları listeler. Ancak, kısmi yöntemler için **dosya adı** kısmi yöntem bildirimi içeren dosyanın listeler.  
  
 Aşağıdaki örnekler sınıfının tanımını bölme `Employee` alanına iki bildirimler, her biri farklı bir yordam tanımlar. İki kısmi tanım örneklerde, bir kaynak dosyasında veya iki farklı kaynak dosyalar olabilir.  
  
> [!NOTE]
>  Visual Basic, Visual Studio ayırmak için kısmi sınıf tanımları kullanır: kullanıcı tarafından yazılan koddan oluşturulan kod. Kod ayrı kaynak dosyalarıyla ayrılır. Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar `Form`. Bu denetimler oluşturulan kodda değiştirmeniz gerekir.  
  
 Visual Basic'te kısmi türleri hakkında daha fazla bilgi için bkz. [kısmi](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).  
  
## <a name="example"></a>Örnek  
 Visual Basic'te bir sınıf tanımı bölmek için kullanın `Partial` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## <a name="example"></a>Örnek  
 Bir sınıf tanımı Visual C# ' ta bölmek için kullanın `partial` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi.  
  
```csharp  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kısmi sınıflar ve yöntemler](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1)   
 [partial (tür)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)   
 [partial (yöntem) (C# Başvurusu)](http://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137)   
 [Partial](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)



