---
title: ParallelForEach&lt;T&gt; etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: eb97ba6abb40c34d03e612c346e2c721719024de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216404"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; etkinlik Tasarımcısı
<xref:System.Activities.Statements.ParallelForEach%601> Etkinlik bir koleksiyon öğelerini numaralandırır ve bir katıştırılmış deyim koleksiyonundaki her öğe için olan aynı iş parçacığında zaman uyumsuz olarak paralel olarak yürütür. Bu akış denetimi etkinliği yerine kullanın <xref:System.Activities.Statements.Sequence> boşta gitmek için bu etkinliği alt etkinliklerini bekleniyorsa etkinlik.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> Etkinliğinde bir <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> içeren bir kullanıcı tarafından belirtilen özelliğe [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifade. <xref:System.Activities.Statements.ParallelForEach%601> Her dal tamamlandıktan sonra bu özellik etkinlik değerlendirir. Değerlendirilirse **true**, ardından <xref:System.Activities.Statements.ParallelForEach%601> etkinliği tamamlandıktan diğer dalları çalıştırmadan. Varsa <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> için değerlendirilmiyor **true**, ardından <xref:System.Activities.Statements.ParallelForEach%601> etkinliği tamamlandıktan tüm alt etkinliklerinin tamamladıktan sonra.  
  
## <a name="the-parallelforeacht-activity"></a>ParallelForEach\<T > etkinliği  
 <xref:System.Activities.Statements.ParallelForEach%601> değerleri ve zamanlamaları numaralandırır <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> numaralandırır üzerinde her değeri. Yalnızca zamanlar <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Nasıl gövdesini yürütür bağlıdır <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> boşta gider.  
  
 Varsa <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> değil Git zamanlanmış etkinlikleri bir yığın işlenir, çünkü boş bir ters sırada yürütür, son zamanlanan etkinlikten önce yürütür. Örneğin, bir koleksiyonu varsa {1,2,3,4}içinde <xref:System.Activities.Statements.ParallelForEach%601> ve bir **WriteLine** değerin yazılmasına yarar gövdesi olarak. 4, 3, 2, 1 konsolda yazdırılabilir vardır. Bunun nedeni, **WriteLine** bunu 4 sonra boşta geçmez **WriteLine** etkinlikleri zamanlanmış, yığın davranışını kullanarak yürütülen (ilk giren son çıkar).  
  
 Ancak etkinlikler varsa <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> , gidip gibi boş bir <xref:System.ServiceModel.Activities.Receive> etkinlik veya <xref:System.Activities.Statements.Delay> etkinlik. Sonra bunların tamamlanmasını beklemenize gerek yoktur. <xref:System.Activities.Statements.ParallelForEach%601> sonraki giden gövdesi aktivitesi ve onu yürütmek deneyin. Bu etkinlik, boşta kalırsa <xref:System.Activities.Statements.ParallelForEach%601> yeniden sonraki gövdesi faaliyete taşır.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach kullanarak\<T > etkinlik Tasarımcısı  
 **ParallelForEach\<T >** etkinlik Tasarımcısı bulunabilir **akış denetimi** kategorisi **araç kutusu**, hangi erişilen tıklayarak **Araç kutusu** sol tarafındaki sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.)  
  
 **ParallelForEach\<T >** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] etkinlik tasarımcıları normal olarak yerleştirilen her yerde yüzey için Örneğin, içini bir **dizisi** etkinlik Tasarımcısı. İçine bırakmadan sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)], oluşturduğu bir <xref:System.Activities.Statements.ParallelForEach%601> içeren varsayılan olarak, etkinlik bir <xref:System.Activities.Activity.DisplayName%2A> , **ParallelForEach\<Int32 >.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > İş Akışı Tasarımcısı özellikleri  
 Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.ParallelForEach%601> etkinlik özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik Tasarımcısı kolay görünen adını belirtir. Varsayılan değer **ParallelForEach\<Int32 >**. Değer, isteğe bağlı olarak düzenlenebilir **özellikleri** kılavuz veya doğrudan etkinlik Tasarımcısı başlığı.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Koleksiyondaki her öğe için çalıştırılacak etkinlik. Eklemek için <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> etkinlik, etkinlik araç kutusundan bir bırakma **gövdesi** kutusuna **ParallelForEach\<T >** etkinlik Tasarımcısı ile "Etkinliği buraya bırakın" İpucu metni.|  
|**TypeArgument**|Doğru|Öğelerin türünü <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> genel parametre tarafından belirtilen koleksiyon *T*. Varsayılan olarak, **TypeArgument** ayarlanır **Int32**. ' % S'tür T içinde değiştirmek için **ParallelForEach\<T >** etkinlik Tasarımcısı değiştirin **TypeArgument** özellik kılavuzunda birleşik giriş kutusu.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Doğru|Üzerinden yinelemek için öğeleri koleksiyonu. Ayarlanacak <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesinde **değerleri** kutusuna **ForEach\<T >** ipucu metnini "VB ifadesi gir" veya içinde kutusunda etkinlik Tasarımcısı **Değerleri** kutusuna **özellikleri** penceresi.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Her yineleme tamamlandıktan sonra değerlendirilir. Bekleyen true sonra zamanlanmış olarak değerlendirir, yinelemeler iptal edilir. Bu özellik ayarlanmamışsa, tüm zamanlanmış deyimleri işlem tamamlanana kadar yürütün.|  
  
 Varsayılan olarak, döngü yineleyici öğesi olarak adlandırılır. Yineleyici değişkeni adını değiştirebilirsiniz **ForEach** kutusunda **ParallelForEach\<T >** etkinlik Tasarımcısı. Döngü yineleyici alt ifadelerde kullanılabilir <xref:System.Activities.Statements.ParallelForEach%601> etkinlik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizisi](../workflow-designer/sequence-activity-designer.md)   
 [Paralel](../workflow-designer/parallel-activity-designer.md)   
 [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)