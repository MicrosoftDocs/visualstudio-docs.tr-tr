---
title: VSTO eklentilerinde diğer Office Çözümlerinden kod arama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9290fcdd705f6f38b4b7e91e46d5b635f1e309ff
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248104"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>VSTO eklentilerinde diğer Office Çözümlerinden kod arama
  Bir nesne için diğer Microsoft Office çözümleri gibi diğer çözümlerle VSTO eklenti içinde kullanıma sunabilirsiniz. VSTO eklenti diğer çözümleri kullanmayı etkinleştirmek istediğiniz bir hizmet sağlar, bu yöntem kullanışlıdır. Bir Web hizmetinden Finansal veriler üzerinde hesaplamalar yapan Microsoft Office Excel için VSTO eklentisi varsa, örneğin, diğer çözümleri bu hesaplamalar zamanında Excel VSTO eklentisi içinde çağırarak gerçekleştirebilirsiniz.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Bu işlemde iki ana adım vardır:  
  
-   VSTO eklenti içinde bir nesne için diğer çözümleri kullanıma sunar.  
  
-   Başka bir çözümde, VSTO eklentisi ve nesnenin çağrı üyeleri tarafından kullanıma sunulan nesneye erişim.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Tür bir eklentide kod çağırabilir miyim çözümler  
 VSTO eklentisi çözümleri aşağıdaki türden bir nesne getirebilir:  
  
-   Visual Basic for Applications (VBA) kodu aynı uygulama işleminde, VSTO eklentisi olarak yüklenen belgedeki.  
  
-   Aynı uygulama işlemi, VSTO eklentisi olarak yüklenen belge düzeyinde özelleştirmeler.  
  
-   Visual Studio'da Office proje şablonları kullanılarak oluşturulan diğer VSTO Add-Ins.  
  
-   COM, VSTO eklentileri (diğer bir deyişle, VSTO uygulayan eklentileri <xref:Extensibility.IDTExtensibility2> doğrudan arabirim).  
  
-   VSTO eklenti değerinden farklı bir işlemde çalışan herhangi bir çözümü (Bu tür çözümler olarak da adlandırılır *işlem dışı istemciler*). Bunlar, bir Windows Forms veya konsol uygulaması ve VSTO farklı bir işlem içinde yüklenen eklentiler gibi bir Office uygulaması otomatikleştirmek uygulamaları içerir.  
  
## <a name="expose-objects-to-other-solutions"></a>Diğer çözümleri nesnelere kullanıma sunma  
 Diğer çözümler için VSTO eklenti, bir nesneyi göstermek için VSTO eklenti aşağıdaki adımları gerçekleştirin:  
  
1.  Diğer çözümler için kullanıma sunmak istediğiniz bir sınıf tanımlar.  
  
2.  Geçersiz kılma <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yönteminde `ThisAddIn` sınıfı. Diğer çözümler için kullanıma sunmak istediğiniz sınıfının bir örneğini döndürür.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Diğer çözümler için kullanıma sunmak istediğiniz sınıfı tanımlayın  
 En azından kullanıma sunmak istediğiniz sınıf ortak olmalıdır, olmalıdır <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliğini **true**, ve açığa çıkarmalıdır [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimi.  
  
 Kullanıma sunmak için önerilen yöntem [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimidir aşağıdaki adımları gerçekleştirmek için:  
  
1. Diğer çözümler için kullanıma sunmak istediğiniz üyeleri bildiren bir arabirim tanımlayın. Bu arabirim, VSTO eklenti projesinde tanımlayabilirsiniz. Ancak, sınıf VBA olmayan çözümler için kullanıma sunmak istiyorsanız VSTO eklenti arama çözümleri VSTO Eklenti projenizi başvurulmadan arabirimi başvurabilir, böylece bu arabirimi ayrı sınıf kitaplığı projesinde tanımlamak isteyebilirsiniz.  
  
2. Uygulama <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği bu arabirime ve bu öznitelik ayarlanan **true**.  
  
3. Bu arabirim uygulamak için kendi sınıfınızı değiştirin.  
  
4. Uygulama <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> öznitelik sınıfı ve bu öznitelik ayarlanan **hiçbiri** değerini <xref:System.Runtime.InteropServices.ClassInterfaceType> sabit listesi.  
  
5. Bu sınıf işlem dışı istemcilere kullanıma sunmak istiyorsanız aşağıdakileri yapmanız gerekebilir:  
  
   -   Türetin <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Daha fazla bilgi için [kullanıma sınıfları işlem dışı istemcilere](#outofproc).  
  
   -   Ayarlama **kaydetme COM birlikte çalışması için** arabirimi tanımladığınız projedeki özellik. Bu özellik yalnızca istemcilerin VSTO eklentisi çağırmak için erken bağlama kullanmasını etkinleştirmek istiyorsanız gereklidir.  
  
   Aşağıdaki kod örneğinde bir `AddInUtilities` sınıfıyla birlikte bir `ImportData` diğer çözümler tarafından çağrılabilen bir yöntem. Daha geniş bir anlatım bağlamında bu kodu görmek için bkz: [izlenecek yol: Bir VSTO eklenti VBA'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>VBA sınıfları gösterir  
 Yukarıda verilen adımları gerçekleştirdiğinizde, VBA kodu arabiriminde bildirdiğiniz yöntemleri çağırabilir. VBA kodu Sınıfınız içinde sınıfınıza temel sınıftan gibi edinir yöntemleri dahil olmak üzere diğer yöntemleri çağıramaz <xref:System.Object>.  
  
 Bunun yerine getirebilir [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ayarlayarak arabirimi <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği AutoDispatch veya AutoDual değerine <xref:System.Runtime.InteropServices.ClassInterfaceType> sabit listesi. Arabirimi kullanıma sunma, ayrı arabirim yöntemleri bildirmeniz gerekmez. Ancak, genel ve statik olmayan yöntemleri gibi temel sınıftan edinilen yöntemler de dahil olmak üzere sınıfınızda VBA kodu çağırabilir <xref:System.Object>. Ayrıca, erken bağlama kullanan işlem dışı istemciler sınıfınıza çağrılamıyor.  
  
###  <a name="outofproc"></a> İşlem dışı istemcilere sınıfları gösterir  
 VSTO eklenti işlem dışı istemcilere bir sınıfta kullanıma sunmak istiyorsanız, bu sınıftan türetilmelidir <xref:System.Runtime.InteropServices.StandardOleMarshalObject> işlem dışı istemciler VSTO eklentisi nesnenizin çağırabilirsiniz emin olmak için. Aksi takdirde, bir işlem dışı istemcisinde nesnenizin örneğini almaya çalışır beklenmedik şekilde başarısız olabilir.  
  
 Bu, tüm çağrıları nesne modelini bir Office uygulamasının ana kullanıcı Arabirimi iş parçacığında yapılması gerekir, ancak nesnenizin işlem dışı istemci çağrıları rastgele bir RPC (uzak yordam çağrısı) parçacığında ulaşır hatasıdır. .NET Framework'teki COM sıralama mekanizması iş parçacıkları geçiş yapmaz ve bunun yerine gelen RPC iş parçacığı ana UI iş parçacığı yerine nesnenize çağrısı hazırlamak çalışır. Nesnenizin türetildiği bir sınıf örneği olup olmadığını <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, nesnenizin gelen çağrıları otomatik olarak konak uygulamanın ana UI iş parçacığı ifşa edilen nesnenin oluşturulduğu, iş parçacığı için sıralanır.  
  
 Office çözümlerinde iş parçacığı kullanma hakkında daha fazla bilgi için bkz. [Office'te iş parçacığı desteği](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService yöntemi geçersiz kılın  
 Aşağıdaki kod örneğinde nasıl geçersiz kılınacağını gösterir <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> içinde `ThisAddIn` VSTO eklenti sınıfı. Örnek adlı bir sınıf tanımladığınız varsayar `AddInUtilities` diğer çözümlerde oluşturmak istediğiniz. Daha geniş bir anlatım bağlamında bu kodu görmek için bkz: [izlenecek yol: Bir VSTO eklenti VBA'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 VSTO Eklenti yüklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çağrıları <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> yöntemi. Çalışma zamanı döndürülen nesne COMAddIn.Object özelliğine atar. bir <xref:Microsoft.Office.Core.COMAddIn> VSTO eklenti temsil eden nesne. Bu <xref:Microsoft.Office.Core.COMAddIn> nesnedir başka bir Office çözümü ve Office otomatikleştiren çözümler için kullanılabilir.  
  
## <a name="access-objects-from-other-solutions"></a>Diğer çözümlerden nesnelere erişme  
 VSTO eklenti içinde oluşturulan nesnenin çağırmak için istemci çözümde aşağıdaki adımları gerçekleştirin:  
  
1. Alma <xref:Microsoft.Office.Core.COMAddIn> sunulan VSTO eklentisi temsil eden nesne. İstemciler tüm kullanılabilir VSTO eklentileri kullanarak erişim `Application.COMAddIns` Office uygulama konağının nesne modelinde bir özellik.  
  
2. COMAddIn.Object özelliğine erişmek <xref:Microsoft.Office.Core.COMAddIn> nesne. Bu özellik, VSTO eklentisi sunulan nesneyi döndürür.  
  
3. İfşa edilen nesnenin üyeleri çağırır.  
  
   VBA ve VBA olmayan istemciler için COMAddIn.Object özelliğinin dönüş değeri kullanma biçimini farklıdır. İşlem dışı istemciler için bir olası yarış durumu önlemek ek kod gereklidir.  
  
### <a name="access-objects-from-vba-solutions"></a>VBA çözümlerinden nesnelere erişme  
 Aşağıdaki kod örneği VBA VSTO eklentisi tarafından kullanıma sunulan bir yöntemi çağırmak için nasıl kullanılacağını gösterir. Bu VBA makrosu adında bir yöntemi çağıran `ImportData` bir VSTO adlı eklentisi içinde tanımlanan **ExcelImportData**. Daha geniş bir anlatım bağlamında bu kodu görmek için bkz: [izlenecek yol: Bir VSTO eklenti VBA'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>VBA olmayan çözümlerinden nesnelere erişme  
 VBA olmayan çözümünde, bunu uyguladığı arabirimin COMAddIn.Object özellik değerine dönüştürmeniz gerekir ve ardından arabirimi nesne üzerinde kullanıma sunulan yöntemleri çağırabilir. Aşağıdaki kod örneğinde nasıl çağrılacağını gösterir `ImportData` bir farklı VSTO Visual Studio'da Office geliştirme araçları kullanılarak oluşturulmuş eklenti yöntemi.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 COMAddIn.Object özelliğin değerini cast çalışırsanız, bu örnekte, `AddInUtilities` sınıfı yerine `IAddInUtilities` arabirimi, kod oluşturur bir <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)   
 [İzlenecek yol: Bir VSTO eklenti VBA'dan kod çağırma](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Genişletilebilirlik arabirimlerini kullanarak kullanıcı Arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  
