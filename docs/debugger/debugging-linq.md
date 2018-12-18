---
title: LINQ hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8511c3ac9efd79b712680bfe3f9d5611f3c5aa9c
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349432"
---
# <a name="debugging-linq"></a>LINQ'de Hata Ayıklama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tümleşik hata ayıklama dilini destekler, bazı kısıtlamalarla (LINQ) kodunda sorgulayın. Hata ayıklama özelliklerinin çoğu LINQ deyimleriyle Adımlama, kesme noktaları ayarlama ve sonuçları hata ayıklayıcı pencerelerinde görüntüleme dahil olmak üzere çalışın. Bu konu LINQ hata ayıklamanın önemli sınırlamalarını açıklar.  
  
##  <a name="BKMK_ViewingLINQResults"></a> LINQ sonuçlarını görüntüleme  
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak, bir LINQ ifadesini sonucunu görüntüleyebilirsiniz. Bir kaynak penceresi kullandığınızda, kaynak penceresinde bir sorgunun işaretçisini duraklatabilirsiniz ve bir DataTip görünür. Bir LINQ değişkenini kopyalayıp İzle penceresine veya QuickWatch iletişim kutusuna yapıştırın.  
  
 LINQ içinde bir sorgu oluşturulduğunda veya bildirildiğinde ancak sorgu kullanılmadıysa değerlendirilmez. Bu nedenle sorgu değerlendirilene kadar bir değeri yok. Sorgu oluşturmaya ve değerlendirmeye tam bir açıklaması için bkz [(C#) LINQ sorgularına giriş](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) veya [bilgisayarınızı ilk LINQ sorgusu yazma](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Bir sorgunun sonucu görüntülemek için hata ayıklayıcı sorguyu değerlendirmelidir. Hata ayıklayıcıda LINQ Sorgu sonucu görüntülediğinizde oluşan bu örtülü değerlendirme, düşünmeniz gereken bazı etkilere sahiptir:  
  
-   Her değerlendirme sorgusunun zaman alır. Sonuç düğümlerinin genişletilmesi zaman alır. Bazı sorgular için yinelenen değerlendirme belirgin bir performans düşüşüyle sonuçlanabilir.  
  
-   Bir sorgunun değerlendirilmesi verilerin değerinde veya programınızın durumunu yapılan değişiklikler etkilere neden olabilir. Tüm sorguların yan etkisi yoktur. Bir sorgu yan etkileri olmadan güvenli bir şekilde değerlendirilebilir olup olmadığını belirlemek için sorguyu uygulayan kodu anlamanız gerekir.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Adımlama ve LINQ  
 LINQ kodunu ayıklarken Adımlama hakkında bilmeniz gereken belirli davranış farkları vardır.  
  
### <a name="linq-to-sql"></a>LINQ - SQL  
 İçinde bir LINQ to SQL sorgularında koşul kodu hata ayıklayıcının denetimi dışında ' dir. Bu nedenle, doğrulama koduna geçemezsiniz. Bir ifade ağacına derleyen herhangi bir sorgu hata ayıklayıcının denetimi dışında kod oluşturur.  
  
### <a name="stepping-in-visual-basic"></a>Visual Basic'de Adımlama  
 Bir Visual Basic programını adımladığınızda ve hata ayıklayıcı bir sorgu bildirimiyle karşılaştığında bildirime girmez ancak bildirimin tamamını tek bir deyim olarak vurgular. Bu davranış, sorgu çağrılana kadar değerlendirilmediğinden oluşur. Daha fazla bilgi için [Visual Basic'te LINQ'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Aşağıdaki örnek kodda gezinirseniz, hata ayıklayıcı sorgu bildirimini veya sorgu oluşturmayı tek bir deyim olarak vurgular.  
  
```vb
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Yeniden adımladığınızda hata ayıklayıcısı vurgular `For Each cur In x`. İsteğe bağlı olarak sonraki adımında, işleve adımları `MyFunction`. Doğruluk sonra `MyFunction`, gezindikten `Console.WriteLine(cur.ToSting())`. Hata ayıklayıcı bu kodu değerlendirse bile herhangi bir noktada, sorgu bildirimindeki koşul kodu adım adım.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Koşulu Adımlamaya (Visual Basic) etkinleştirmek için bir işlevle değiştirme  
 Varsa, hata ayıklama amacıyla koşul kodu üzerinden adımlamak için koşulu orijinal koşul kodunu içeren bir işlev çağrısıyla değiştirebilirsiniz. Örneğin, bu kod olduğunu varsayalım:  
  
```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Koşul kodu adlı yeni bir işleve taşıyabilirsiniz `IsEven`:  
  
```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 Düzeltilmiş sorgu çağrıları işlev `IsEven` her geçişte `items`. Her öğenin belirtilen koşulu karşılayıp ve kodda adım adım olup olmadığını görmek için hata ayıklayıcı penceresini kullanabilirsiniz `IsEven`. Bu örnekteki koşul oldukça basittir. Ancak, hata ayıklama yapmanızı daha zor bir karşılaştırmanız varsa bu teknik çok kullanışlı olabilir.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Düzenle ve devam et LINQ için desteklenmiyor  
 Düzenle ve devam et, LINQ sorgularında kısıtlamalarla yapılan değişiklikleri destekler. Ayrıntılar için bkz [EnC desteklenen değişiklikleri](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>Ayrıca Bkz.

- [SQL hata ayıklama](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
- [LINQ sorguları (C#) giriş](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Visual Basic'de LINQ'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
