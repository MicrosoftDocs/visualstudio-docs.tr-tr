---
title: VBA ve belge düzeyi özelleştirmelerini birleştirme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2243a3e03ed84325523f62d77ae3cc6d20f83bbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878082"
---
# <a name="combine-vba-and-document-level-customizations"></a>VBA ve belge düzeyi özelleştirmelerini birleştirme
  Visual Basic for Applications (VBA) kodu Microsoft Office Word veya Microsoft Office Excel için belge düzeyi özelleştirmesinde parçası olan bir belgeyi kullanabilirsiniz. Özelleştirme bütünleştirilmiş koddan belgedeki VBA kodu çağırabilir veya özelleştirme derlemede kod çağırmak için belgedeki VBA kodu etkinleştirmek için projenizi yapılandırabilirsiniz.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesinde VBA kodunun davranışı  
 Projenizi Visual Studio'da açtığınızda, belge tasarım modunda açılır. VBA kodu çalıştırmadan kod ve belge üzerinde çalışabilmesi için belge tasarım modunda olduğunda VBA kodu çalışmaz.  
  
 Çözümü çalıştırdığınızda, olay işleyicileri VBA hem de özelleştirme bütünleştirilmiş kodu belgede başlatılan olaylara yerden devam edebiliyorduk ve iki kod çalıştırın. Önceden, hangi kod diğerinden önce çalışacak belirlenemiyor; Bu, tek tek her durumda test sürecinde belirlemelisiniz. İki kod değil dikkatli bir şekilde denetlenen ve test, beklenmeyen sonuçlar alabilirsiniz.  
  
## <a name="call-vba-code-from-the-customization-assembly"></a>Özelleştirme bütünleştirilmiş koddan VBA kodu çağırma  
 Word belgelerinde makroları çağırabilir ve Excel çalışma kitaplarını makrolar ve İşlevler çağırabilir. Bunu yapmak için aşağıdaki yöntemlerden birini kullanın:  
  
- Sözcük için arama <xref:Microsoft.Office.Interop.Word._Application.Run%2A>yöntemi <xref:Microsoft.Office.Interop.Word.Application> sınıfı.  
  
- Excel için çağrı <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> yöntemi <xref:Microsoft.Office.Interop.Excel.Application> sınıfı.  
  
  Her bir yöntemin ilk parametre makro veya çağırmak istediğiniz işlevin adını tanımlar ve diğer isteğe bağlı parametreler makrosu veya işleve geçirilecek parametreler belirtin. İlk parametre, Word ve Excel için farklı biçimlerde olabilir:  
  
- Word için ilk parametre şablonunu, modül ve makro adı herhangi bir birleşimi olabilir bir dizedir. Belge adı belirtirseniz, kodunuzu yalnızca makroları geçerli bağlamla ilgili belgelerde çalıştırabilirsiniz; herhangi bir belgedeki yalnızca hiçbir makrosu.  
  
- Excel için ilk parametre makro adını belirten bir dize olabilir bir <xref:Microsoft.Office.Interop.Excel.Range> işlevi olduğu veya bir kayıt kimliği için kayıtlı bir DLL (XLL) işlev gösterir. Bir dize geçirirseniz, dize etkin sayfa bağlamında değerlendirilir.  
  
  Aşağıdaki kod örneğinde adlı bir makro çağrısı gösterilmiştir `MyMacro` bir Excel için belge düzeyi projesi. Bu örnek olduğunu varsayar `MyMacro` tanımlanan `Sheet1`.  
  
```vb  
Globals.Sheet1.Application.Run("MyMacro")  
```  
  
```csharp  
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,  
    missing, missing, missing, missing, missing, missing, missing,   
    missing, missing, missing, missing, missing, missing);  
```  
  
> [!NOTE]  
>  Genel kullanma hakkında bilgi için `missing` Visual C#, isteğe bağlı parametreler yerine değişken bkz [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="call-code-in-document-level-customizations-from-vba"></a>Belge düzeyi özelleştirmelerdeki VBA'dan Kod Çağırma  
 Visual Basic for Applications (VBA) kod belgedeki özelleştirme derlemede kod çağırabilmek Word veya Excel için belge düzeyi projesi yapılandırabilirsiniz. Aşağıdaki senaryolarda kullanışlıdır:  
  
- Belge düzeyi özelleştirmesinde aynı belge ile ilişkilendirilen özellikleri kullanarak mevcut bir belgedeki VBA kodunu genişletme istiyorsunuz.  
  
- Geliştirme Hizmetleri belge düzeyi özelleştirmesinde kullanılabilir son kullanıcılar, hizmetler, belgedeki VBA kodu yazarak erişebilir yapmak istiyorsunuz.  
  
  Visual Studio'da Office geliştirme araçları, VSTO eklentileri için benzer bir özellik sağlar. Bir VSTO eklentisi geliştiriyorsanız, kod içinde VSTO eklenti diğer Microsoft Office Çözümlerinden çağırabilirsiniz. Daha fazla bilgi için [çağrı kod VSTO eklentileri diğer Office Çözümlerinden](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
> [!NOTE]  
>  Bu özellik Word şablonu projelerinde kullanılamaz. Yalnızca Word belgesi, Excel çalışma kitabı veya Excel şablon projelerinde kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 VBA kodunu özelleştirme bütünleştirilmiş kod içine çağırmak için etkinleştirmeden önce projenize aşağıdaki gereksinimleri karşılaması gerekir:  
  
-   Belge aşağıdaki dosya adı uzantıları birine sahip olmalıdır:  
  
    -   Word: *.docm* veya *.doc*  
  
    -   Excel: *.xlsm*, *.xltm*, *.xls*, veya *.xlt*  
  
-   Belge zaten VBA kodunun olduğu bir VBA projesi içermesi gerekir.  
  
-   Belgedeki VBA kodu kullanıcı makroları istemeden çalışmaya izin verilmesi gerekir. Office proje konumunu Word veya Excel için Güven Merkezi ayarlarında güvenilen konumlar listesine ekleyerek çalıştırılacak VBA kodu güvenebilir.  
  
-   Office proje için VBA bırakıyorsunuz bir veya daha fazla genel üyeleri içeren en az bir ortak sınıf içermelidir.  
  
     Yöntemler, özellikler ve olaylar VBA kullanıma sunabilirsiniz. Bir konak Item sınıfı, kullanıma sınıfı olabilir (gibi `ThisDocument` Word için veya `ThisWorkbook` ve `Sheet1` Excel için) veya projenize tanımlayan başka bir sınıf. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğelerini ve denetimlerine genel bakış için ana bilgisayar](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>VBA kodunu özelleştirme bütünleştirilmiş kod içine çağırmak için etkinleştirme  
 Belgedeki VBA kodu özelleştirme derlemeye üyeleri getirebilir iki farklı yolu vardır:  
  
- Bir konak öğesi sınıfında üyeleri ortaya koyabileceğiniz bir [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA projesi. Bunu yapmak için ayarlanmış **EnableVbaCallers** konak öğesi özelliği **True** içinde **özellikleri** penceresi sırasında (diğer bir deyişle, belge, çalışma sayfası veya çalışma kitabı) konak öğesi Tasarımcıda açık. Visual Studio otomatik olarak tüm sınıf üyelerini çağırmak VBA kodunu etkinleştirmek için gerekli işlemleri gerçekleştirir.  
  
- Visual C# projesinde herhangi bir genel sınıf üyeleri getirebilir ya da konak olmayan üyeler sınıfta öğesi bir [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] VBA projesi. Bu seçenek, hangi sınıflar için VBA kullanıma seçme özgürlüğü sağlar, ancak ayrıca daha fazla el ile yapılacak adımlar gerektirir.  
  
   Bunu yapmak için aşağıdaki temel adımları gerçekleştirmeniz gerekir:  
  
  1.  Vystavit sınıfı  
  
  2.  Geçersiz kılma **GetAutomationObject** gösterme sınıfının bir örneğini dönmek için projenizdeki ana bilgisayar öğesi sınıfının yöntemi.  
  
  3.  Ayarlama **ReferenceAssemblyFromVbaProject** projede herhangi bir ana bilgisayar öğesi sınıf özelliği **True**. Bu özelleştirme bütünleştirilmiş kodun tür kitaplığını derlemeye gömer ve belgedeki VBA projesine tür kitaplığına bir başvuru ekler.  
  
  Ayrıntılı yönergeler için bkz. [nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) ve [nasıl yapılır: kodu Visual c VBA kullanımına sunma&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).  
  
  **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özellikleri yalnızca **özellikleri** penceresi; tasarım zamanında çalışma zamanında kullanılamaz . Özelliklerini görüntülemek için bir ana öğe Tasarımcısı'nı açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Visual Studio bu özellikleri ayarladığınızda gerçekleştiren belirli görevler hakkında daha fazla bilgi için bkz. [konak öğesi özellikleri tarafından gerçekleştirilen görevler](#PropertyTasks).  
  
> [!NOTE]  
>  Çalışma kitabı veya belge VBA kodu zaten içermiyor veya belgedeki VBA kodu çalıştırmak için güvenilir değilse, ayarlarken bir hata iletisi alırsınız **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject**  özelliğini **True**. Bu durum, Visual Studio, bu durumda belgedeki VBA projesine değiştirilemiyor çünkü.  
  
## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Üyelerinin VBA kodu özelleştirme bütünleştirilmiş kod içine çağırmak için kullanın.  
 VBA kodunu özelleştirme bütünleştirilmiş kod içine çağırmak için etkinleştirmek için projenizi yapılandırdıktan sonra Visual Studio aşağıdaki üyeleri belgedeki VBA projesine ekler:  
  
- Tüm projeler için Visual Studio adlı bir genel yöntem ekler `GetManagedClass`.  
  
- İçin [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] bir konak üyeleri ortaya projeleri öğe sınıfı kullanarak **EnableVbaCallers** özelliği, Visual Studio ayrıca adlı bir özellik ekler `CallVSTOAssembly` için `ThisDocument`, `ThisWorkbook`, `Sheet1`, `Sheet2`, veya `Sheet3` VBA projesinde modülü.  
  
  Kullanabileceğiniz `CallVSTOAssembly` özelliği veya `GetManagedClass` genel projesinde kodu VBA maruz sınıf üyelerine erişmek için yöntemi.  
  
> [!NOTE]  
>  Geliştirdiğinizde ve dağıttığınızda, çözümünüzün vardır belge birkaç farklı kopyalarını burada VBA kodu ekleyebilirsiniz. Daha fazla bilgi için [kod belgeye VBA ekleme yönergeleri](#Guidelines).  
  
### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Visual Basic projesinde CallVSTOAssembly özelliğini kullanın  
 Kullanım `CallVSTOAssembly` konak öğesi sınıfına eklenen genel üyeleri erişmek için özelliği. Örneğin, aşağıdaki VBA makrosu adında bir yöntemi çağıran `MyVSTOMethod` içinde tanımlanan `Sheet1` bir Excel çalışma kitabı projesi sınıfta.  
  
```vb
Sub MyMacro()  
    Sheet1.CallVSTOAssembly.MyVSTOMethod()  
End Sub  
```  
  
 Bu özelliği kullanmaktan özelleştirme bütünleştirilmiş kodu çağırmak için daha kullanışlı bir yoldur `GetManagedClass` doğrudan yöntemi. `CallVSTOAssembly` ana bilgisayarı temsil eden bir nesne için VBA ortaya çıkardığınız Item sınıfı döndürür. Yöntem parametreleri döndürülen nesne ve üyeler Intellisense'te görünür.  
  
 `CallVSTOAssembly` Özelliği, aşağıdaki koda benzer bir bildirime sahiptir. Bu kod, sunduğunuz varsayar `Sheet1` konak adlı bir Excel çalışma kitabı projesi öğesi sınıfını `ExcelWorkbook1` VBA.  
  
```vb 
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1  
    Set CallVSTOAssembly = GetManagedClass(Me)  
End Property  
```  
  
### <a name="use-the-getmanagedclass-method"></a>GetManagedClass yöntemi kullanın  
 Genel kullanılacak `GetManagedClass` kılacağınızı içeren ana öğesi sınıf VBA nesnesindeki karşılık gelen geçişine yöntemi **GetAutomationObject** yöntemi. Ardından, döndürülen nesne VBA için kullanıma sunulan sınıfa erişmek için kullanın.  
  
 Örneğin, aşağıdaki VBA makrosu adında bir yöntemi çağıran `MyVSTOMethod` içinde tanımlanan `Sheet1` konak adlı bir Excel çalışma kitabı projesi öğesi sınıfını `ExcelWorkbook1`.  
  
```vb
Sub CallVSTOMethod  
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1  
    Set VSTOSheet1 = GetManagedClass(Sheet1)  
    VSTOSheet1.MyVSTOMethod  
End Sub  
```  
  
 `GetManagedClass` Yöntemi aşağıdaki bildirime sahiptir.  
  
```vb
GetManagedClass(pdispInteropObject Object) As Object  
```  
  
 Bu yöntem, kullanıma sunulan sınıf VBA için temsil eden bir nesne döndürür. Yöntem parametreleri döndürülen nesne ve üyeler Intellisense'te görünür.  
  
##  <a name="Guidelines"></a> VBA kodunu belgeye ekleme yönergeleri  
 Belge düzeyi özelleştirmesi çağrı yapan VBA kodu eklemek belgenin birkaç farklı kopyalarını vardır.  
  
 Geliştirin ve çözümünüzü test etme gibi hata ayıklarken veya projeyi Visual Studio'da (diğer bir deyişle, yapı çıkış klasöründe belge) çalıştırın, açılır belgedeki VBA kodu yazabilirsiniz. Ancak, Visual Studio yapı çıkış klasöründe belge ana proje klasöründen belgenin bir kopyasını değiştirir çünkü bu belgeye eklediğiniz VBA kodlar projeyi sonraki açışınızda üzerine yazılır.  
  
 Hata ayıklama veya çözüm çalıştırırken belgeye eklediğiniz VBA kodu kaydetmek istiyorsanız, proje klasöründeki belgesine VBA kodu kopyalayın. Yapı işlemi hakkında daha fazla bilgi için bkz. [office çözümleri derleme](../vsto/building-office-solutions.md).  
  
 Çözümünüzü dağıtmak hazırsanız VBA kodu ekleyebileceğiniz üç ana belge konum vardır.  
  
### <a name="in-the-project-folder-on-the-development-computer"></a>Geliştirme bilgisayarında proje klasöründe  
 Bu konum, belgedeki VBA kodu hem özelleştirme kod üzerinde tam denetime sahip uygundur. Belge geliştirme bilgisayarında olduğundan özelleştirme kodu değiştirirseniz kolayca VBA kodu değiştirebilirsiniz. Derleme, hata ayıklama ve çözümünüzü yayımlamak için bu belgenin kopyasını eklediğiniz VBA kodu belgede kalır.  
  
 Tasarımcıda açık durumdayken VBA kodunu belgeye eklenemiyor. Belgeyi tasarımcıda kapatın ve sonra belgeyi doğrudan Word veya Excel'de açın.  
  
> [!CAUTION]  
>  Belge açıldığında çalıştırılan VBA kodu eklerseniz, nadir durumlarda bu kodu belge bozuk veya tasarımcıda açılmasını engelle.  
  
### <a name="in-the-publish-or-installation-folder"></a>Yayımlama ya da yükleme klasöründe  
 Bazı durumlarda, VBA kodunu belgeye yayımlama ya da yükleme klasöründeki eklemek uygun olabilir. Örneğin, VBA kodu yazılır ve Visual Studio yüklü olmayan bir bilgisayara farklı bir geliştirici tarafından test varsa bu seçeneği belirleyebilirsiniz.  
  
 Kullanıcıların çözümü yayımlama klasöründen doğrudan yüklerseniz, çözümü her yayımladığınızda VBA kodunu belgeye eklemeniz gerekir. Visual Studio çözümü yayımladığınızda, yayımlama konumu belgede üzerine yazar.  
  
 Kullanıcıların çözümü yayımlama klasöründen farklı bir yükleme klasöründen yüklerseniz, çözümü her yayımladığınızda VBA kodunu belgeye ekleme önleyebilirsiniz. Yayımlama güncelleştirme yükleme klasörüne yayımlama klasöründen taşınacak hazır olduğunda, tüm dosyaları belge dışında yükleme klasörüne kopyalayın.  
  
### <a name="on-the-end-user-computer"></a>Son kullanıcı bilgisayarda  
 Son kullanıcılar için belge düzeyi özelleştirmesinde sağladığınız Hizmetleri çağıran VBA geliştiriciler varsa, bunları kullanarak nasıl kodunuzun söyleyebilirsiniz `CallVSTOAssembly` özelliği veya `GetManagedClass` belge kopyalarını yöntemi. Güncelleştirmeler çözümü yayımladığınızda, son kullanıcı bilgisayarında belgedeki VBA kodu yazılmaz, belge değiştirilmez çünkü güncelleştirmeleri yayımlayabilir.  
  
##  <a name="PropertyTasks"></a> Ana bilgisayar öğesi özellikleri tarafından gerçekleştirilen görevleri  
 Kullanırken **EnableVbaCallers** ve **ReferenceAssemblyFromVbaProject** özellikleri, Visual Studio farklı görevler kümesini gerçekleştirir.  
  
### <a name="enablevbacallers"></a>EnableVbaCallers  
 Ayarladığınızda **EnableVbaCallers** konak öğesi özelliği **True** Visual Basic projesinde, Visual Studio aşağıdaki görevleri gerçekleştirir:  
  
1. Ekler <xref:Microsoft.VisualBasic.ComClassAttribute> ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> öznitelikleri için konak öğesi sınıfı.  
  
2. Onu geçersiz kılar **GetAutomationObject** konak öğesi sınıfının yöntemi.  
  
3. Bu ayarlar **ReferenceAssemblyFromVbaProject** konak öğesi özelliği **True**.  
  
   Ayarladığınızda **EnableVbaCallers** özelliğini yeniden **False**, Visual Studio aşağıdaki görevleri gerçekleştirir:  
  
4. Kaldırır <xref:Microsoft.VisualBasic.ComClassAttribute> ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliklerini `ThisDocument` sınıfı.  
  
5. Kaldırır **GetAutomationObject** konak öğesi sınıfından yöntemi.  
  
   > [!NOTE]  
   >  Visual Studio otomatik olarak ayarlamazsa **ReferenceAssemblyFromVbaProject** özelliğini yeniden **False**. Bu özelliği ayarlamak **False** kullanarak el ile **özellikleri** penceresi.  
  
### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject  
 Zaman **ReferenceAssemblyFromVbaProject** özelliği herhangi bir Visual Basic veya Visual C# projesinde ana öğesinin **True**, Visual Studio aşağıdaki görevleri gerçekleştirir:  
  
1. Bu özelleştirme derlemesi için bir tür kitaplığı üretir ve tür kitaplığını derlemeye gömer.  
  
2. Belgedeki VBA projesinde aşağıdaki tür kitaplıkları için bir başvuru ekler:  
  
   -   Derlemenizi özelleştirme için tür kitaplığı.  
  
   -   Office yürütme altyapısı 9.0 tür kitaplığı için Microsoft Visual Studio Araçları. Bu tür kitaplığı dahil [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
   Zaman **ReferenceAssemblyFromVbaProject** ayarlanırsa geri **False**, Visual Studio aşağıdaki görevleri gerçekleştirir:  
  
3. Belgedeki VBA projesine tür kitaplığı başvurularını kaldırır.  
  
4. Gömülü tür kitaplığını bütünleştirilmiş koddan kaldırır.  
  
## <a name="troubleshoot"></a>Sorun giderme
 Aşağıdaki tabloda, bazı yaygın hatalar ve hataları düzeltmek için önerileri listeler.  
  
|Hata|Öneri|  
|-----------|----------------|  
|Ayarlandıktan sonra **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliği, bir hata iletisi durumları belge bir VBA projesi içermiyor veya erişmek için izniniz yok Belgedeki VBA projesine.|En az bir VBA makrosu projedeki belge içeren, VBA projesi çalıştırmak için yeterli güvene sahip ve VBA projesinde bir parola ile korunmayan emin olun.|  
|Ayarlandıktan sonra **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliği, bir hata iletisi durumları <xref:System.Runtime.InteropServices.GuidAttribute> bildirimi eksik veya bozuk.|Emin <xref:System.Runtime.InteropServices.GuidAttribute> bildirimi bulunan *AssemblyInfo.cs* veya *AssemblyInfo.vb* proje dosyasında ve bu öznitelik için geçerli bir GUID olarak ayarlanır.|  
|Ayarlandıktan sonra **EnableVbaCallers** veya **ReferenceAssemblyFromVbaProject** özelliği, bir hata iletisi durumları tarafından belirtilen sürüm numarası <xref:System.Reflection.AssemblyVersionAttribute> geçerli değil.|Emin <xref:System.Reflection.AssemblyVersionAttribute> bildiriminde *AssemblyInfo.cs* veya *AssemblyInfo.vb* projenizdeki dosya için geçerli derleme sürüm numarası ayarlayın. Geçerli derleme sürüm numaraları hakkında daha fazla bilgi için bkz: <xref:System.Reflection.AssemblyVersionAttribute> sınıfı.|  
|Özelleştirme bütünleştirilmiş koda çağrı yapan VBA kodu özelleştirme bütünleştirilmiş kodu yeniden adlandırdıktan sonra durur.|Sonra VBA kodunu sunmadan özelleştirme derlemenin adını değiştirirseniz, belgedeki VBA projesine özelleştirme derlemenizi arasındaki bağlantı bozuk. Bu sorunu gidermek için değiştirme **ReferenceFromVbaAssembly** projenize özelliğinde **False** ve ardından yeniden **True**ve ardından eski derlemenin tüm başvurularını Değiştir VBA kodu adı ile yeni bir derleme adı.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Visual Basic projesinde kodu VBA kullanımına sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Nasıl yapılır: kodu Visual c VBA kullanımına sunma&#35; proje](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [İzlenecek yol: kod Visual Basic projesinde VBA'dan çağırın](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [İzlenecek yol: Visual c VBA'dan Kod Çağırma&#35; proje](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio'da karşılaştırılan VBA ve Office çözümleri](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)   
 [Belge düzeyi özelleştirmelerini programlama](../vsto/programming-document-level-customizations.md)  
  
  