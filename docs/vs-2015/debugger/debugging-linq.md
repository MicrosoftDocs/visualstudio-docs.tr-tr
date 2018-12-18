---
title: LINQ hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 081c97bffc062bf2bbc9d24feed13e5e512b8c74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755605"
---
# <a name="debugging-linq"></a>LINQ'de Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik hata ayıklama dilini destekler, bazı kısıtlamalarla (LINQ) kodunda sorgulayın. Hata ayıklama özelliklerinin çoğu LINQ deyimleriyle Adımlama, kesme noktaları ayarlama ve sonuçları hata ayıklayıcı pencerelerinde görüntüleme dahil olmak üzere çalışın. Bu konu LINQ hata ayıklamanın önemli sınırlamalarını açıklar.  
  
##  <a name="BKMK_ViewingLINQResults"></a> LINQ sonuçlarını görüntüleme  
 DataTips, izleme penceresi ve QuickWatch iletişim kutusunu kullanarak, bir LINQ ifadesini sonucunu görüntüleyebilirsiniz. Bir kaynak penceresi kullandığınızda, kaynak penceresinde bir sorgunun işaretçisini duraklatabilirsiniz ve bir DataTip görünür. Bir LINQ değişkenini kopyalayıp İzle penceresine veya QuickWatch iletişim kutusuna yapıştırın.  
  
 LINQ içinde bir sorgu oluşturulduğunda veya bildirildiğinde ancak sorgu kullanılmadıysa değerlendirilmez. Bu nedenle sorgu değerlendirilene kadar bir değeri yok. Sorgu oluşturmaya ve değerlendirmeye tam bir açıklaması için bkz [(C#) LINQ sorgularına giriş](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) veya [bilgisayarınızı ilk LINQ sorgusu yazma](http://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Bir sorgunun sonucu görüntülemek için hata ayıklayıcı sorguyu değerlendirmelidir. Hata ayıklayıcıda LINQ Sorgu sonucu görüntülediğinizde oluşan bu örtülü değerlendirme, düşünmeniz gereken bazı etkilere sahiptir:  
  
-   Her değerlendirme sorgusunun zaman alır. Sonuç düğümlerinin genişletilmesi zaman alır. Bazı sorgular için yinelenen değerlendirme belirgin bir performans düşüşüyle sonuçlanabilir.  
  
-   Bir sorgunun değerlendirilmesi verilerin değerinde veya programınızın durumunu yapılan değişiklikler etkilere neden olabilir. Tüm sorguların yan etkisi yoktur. Bir sorgu yan etkileri olmadan güvenli bir şekilde değerlendirilebilir olup olmadığını belirlemek için sorguyu uygulayan kodu anlamanız gerekir.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Adımlama ve LINQ  
 LINQ kodunu ayıklarken Adımlama hakkında bilmeniz gereken belirli davranış farkları vardır.  
  
### <a name="linq-to-sql"></a>LINQ - SQL  
 İçinde bir LINQ to SQL sorgularında koşul kodu hata ayıklayıcının denetimi dışında ' dir. Bu nedenle, doğrulama koduna geçemezsiniz. Bir ifade ağacına derleyen herhangi bir sorgu hata ayıklayıcının denetimi dışında kod oluşturur.  
  
### <a name="stepping-in-visual-basic"></a>Visual Basic'de Adımlama  
 Bir Visual Basic programını adımladığınızda ve hata ayıklayıcı bir sorgu bildirimiyle karşılaştığında bildirime girmez ancak bildirimin tamamını tek bir deyim olarak vurgular. Bu davranış, sorgu çağrılana kadar değerlendirilmediğinden oluşur. Daha fazla bilgi için [Visual Basic'te LINQ'e giriş](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Aşağıdaki örnek kodda gezinirseniz, hata ayıklayıcı sorgu bildirimini veya sorgu oluşturmayı tek bir deyim olarak vurgular.  
  
```  
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
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Koşul kodu adlı yeni bir işleve taşıyabilirsiniz `IsEven`:  
  
```  
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
 Düzenle ve devam et, LINQ sorgularında yapılan değişiklikleri desteklemez. Ekleme, kaldırma veya hata ayıklama oturumu sırasında bir LINQ ifadesini değiştirin, bildiren değişikliğin Düzenle ve devam et tarafından desteklenmez bir iletişim kutusu görünür. Bu noktada, ya değişiklikleri geri almak veya hata ayıklama oturumunu durdurmak ve düzenlenen kodla yeni bir oturumu yeniden başlatabilirsiniz.  
  
 Ayrıca, Düzenle ve devam et, türü veya bir LINQ deyiminde kullanılan bir değişkenin değerini değiştirmeyi desteklemez. Yine, ya değişiklikleri geri almak veya durdurabilir ve hata ayıklama oturumunu yeniden başlatın.  
  
 C# ' ta, Düzenle ve devam et LINQ sorgusu içeren bir yöntem herhangi bir kod kullanamazsınız.  
  
 Visual Basic'te, LINQ olmayan kodda bile LINQ sorgusu içeren bir yöntem üzerinde Düzenle ve devam et kullanabilirsiniz. Ekleyebilir veya LINQ deyiminden önce kod değişiklikleri LINQ sorgusunun satır numarasını etkilese kaldırın. Visual Basic hata ayıklama deneyimi için LINQ olmayan kodda, LINQ öncesi olduğu gibi aynı kalır. Değiştirme, ekleme veya değişiklikleri uygulamak için hata ayıklamayı durdurmak istemediğiniz sürece LINQ sorgusu, ancak kaldırma olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL hata ayıklama](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Yan etkiler ve ifadeler](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Özel durumları hata ayıklayıcısı ile yönetme](../debugger/managing-exceptions-with-the-debugger.md)   
 [LINQ sorguları (C#) giriş](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Visual Basic'de LINQ'e giriş](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)



