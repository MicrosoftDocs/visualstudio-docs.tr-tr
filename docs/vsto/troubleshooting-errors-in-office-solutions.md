---
title: Office çözümleri hatalarında sorun giderme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bcc5600f38e2d53244d972e4c4c7094182bfa48c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672957"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office çözümleri hatalarında sorun giderme
  Visual Studio'da Office çözümleri geliştirirken, aşağıdaki görevleri gerçekleştirirken sorunlarla karşılaşabilirsiniz:  
  
-   [Projeleri oluşturma ve yükseltme](#creating)  
  
-   [Tasarımcıları](#designers)  
  
-   [Kod yazma](#code)  
  
-   [Projeler derleme](#building)  
  
-   [Proje hata ayıklama](#debugging)  
  
##  <a name="creating"></a> Projeleri oluşturma ve yükseltme  
 Office projeleri oluşturduğunuzda veya açtığınızda şu hatalarla karşılaşabilirsiniz.  
  
### <a name="the-project-cannot-be-created"></a>Proje oluşturulamıyor  
 Bir Office projesi oluşturun veya açın çalışıldı, ancak Visual Studio nedenini belirlemek için yeterli bilgiye sahip olmayan bir hata oluştu. Visual Studio çıkmak ve yeniden başlatmayı projenizi kapatmayı deneyin.  
  
 Belge düzeyi projesi oluşturmaya çalışıyorsanız, Yeni projedeki belge aynı ada sahip başka bir belge zaten Excel veya Word'ün açık olduğundan emin mümkündür. Diğer tüm örnekleri Excel veya Word kapalı olduğundan emin olun.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Varolan bir projeden bir belge temel alan yeni bir proje oluşturduğunuzda, denetim özelliklerini kaybolur  
 Mevcut bir projeyi bir belgeden dayalı yeni bir Office projesi oluşturursanız, belge üzerinde olan herhangi bir denetim özelliklerini yeni projeye kopyalanmaz. Önceden var olan tüm denetimler için özellikleri el ile sıfırlamanız gerekir. Alternatif olarak, yeni bir proje oluşturmak yerine var olan projenin bir kopyasını oluşturarak veya yeni çözümde (Tasarımcı) varolan proje yükleme ve kopyalama ve yapıştırma denetimleri var olan denetim özellikleri koruyabilir Yeni belge belgesi.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Mevcut bir çalışma kitabını temel alan bir Excel çalışma kitabı projesi oluştururken hatalar  
 Mevcut bir çalışma kitabını temel alan yeni bir Excel çalışma kitabı projesi oluşturursanız, şu hatalarla birlikte görebilirsiniz.  
  
 Excel: "Gizlilik Uyarı: Bu belge makroları, ActiveX denetimleri, XML genişletme paketi bilgileri ve Web bileşenleri içerir. Bu belge denetçisi tarafından kaldırılan kişisel bilgiler içerebilir."  
  
 Visual Studio'dan: "Düzgün yüklenemedi Tasarımcısı."  
  
 Bu hatalar, belge Inspector'ı kullanarak kendi kişisel bilgilerine sahip bir çalışma kitabını temel alan bir proje oluşturmak deneyin ortaya çıkabilir. Bu hatadan kaçınmak için proje oluşturmadan önce aşağıdaki adımları gerçekleştirin.  
  
1.  Çalışma kitabını Excel'de açın.  
  
2.  Excel'de, Güven Merkezi'ni açın.  
  
3.  Üzerinde **Gizlilik Seçenekleri** sekmesini Temizle **kaydederken dosya özelliklerinden kişisel bilgileri Kaldır** onay kutusu.  
  
4.  Çalışma kitabını kaydedin ve Excel'i kapatın.  
  
### <a name="cannot-open-a-project-after-migration"></a>Bir proje, geçişten sonra açılamıyor  
 Bir Office çözüm Microsoft Office 2010'a geçirildikten sonra yalnızca 2007 Microsoft Office sistemi yüklü bir geliştirme bilgisayarında proje açılamıyor. Aşağıdaki hatayla karşılaşabilirsiniz.  
  
 "Çözümdeki bir veya daha fazla proje doğru şekilde yüklenmedi. Lütfen ayrıntılar için çıkış penceresine bakın."  
  
 "Bu proje türüyle ilişkili uygulama bu bilgisayarda yüklü olmadığından Proje oluşturulamıyor. Bu proje türüyle ilişkilendirilen Microsoft Office uygulamasını yüklemeniz gerekir."  
  
 Bu sorunu gidermek için Düzenle *.vbproj* veya *.csproj* dosya. Bir sözcük projesi için HostPackage HostPackage ile "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". Bir Excel projesi için HostPackage HostPackage ile "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" = "{825100CF-0BA7-47ea-A084-DCF3308DAF74}". Bir Outlook projesi için HostPackage HostPackage ile "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" = "{20A848B8-E01F-4801-962E-25DB0FF57389}".  
  
 Alternatif olarak, geçirilen projeleri yalnızca geliştirme bilgisayarlarda yüklü Microsoft Office 2010 ile açıldığından emin olun.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Windows Forms denetimleri içeren yükseltilen Office 2003 belge düzeyi projeler hataları  
 Microsoft Office 2003 belge düzeyi projesi yükseltme ve belge Windows Forms denetimlerini içeriyorsa, yükseltilen proje derleme veya çalışma zamanı hataları olabilir. Projeyi yükseltmeden önce bu sorunu önlemek için Visual Studio 2005 araçları Office Second Edition Runtime geliştirme bilgisayarına yükleyin. Çalışma zamanının bu sürümü Microsoft Download Center yeniden dağıtılabilir paket olarak kullanılabilir [için Microsoft Visual Studio 2005 araçları Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Projenizi yükseltmeyi tamamladığınızda, başka bir Office çözümü tarafından kullanılmadığından, Visual Studio 2005 araçları Office Second Edition Runtime Geliştirme bilgisayarınızdan kaldırabilirsiniz.  
  
##  <a name="designers"></a> Tasarımcıları  
 Belge, çalışma kitabı veya çalışma sayfasını tasarımcıda belge düzeyi projeler ile çalışırken hatalarla karşılaşabilirsiniz.  
  
### <a name="designer-failed-to-load-correctly"></a>Tasarımcı düzgün yüklenemedi  
 Visual Studio, aşağıdaki durumlarda Tasarımcı açılamıyor:  
  
-   Excel veya Word'den zaten açık olan ve kalıcı bir iletişim kutusu görüntüleniyor. Tasarımcısını açmak için Excel veya Word'den kalıcı bir iletişim kutusu açmak ve açık kalıcı iletişim kutularını kapatmak sahip olup olmadığını denetleyin. Açık hiçbir kalıcı iletişim kutuları varsa, önce Excel gereken başka bir eylem olabilir veya Word yanıt verir.  
  
-   Proje şu anda hata ayıklama yapılıyor. Tasarımcı açmak için durdurmak veya hata ayıklamasını bitirdiğinizde.  
  
-   Bir Excel VSTO geliştirme bilgisayarında yüklü eklenti Excel başlatıldığında bir iletişim kutusu görüntülüyor. Bir Excel belge düzeyi projesi oluşturmak için önce VSTO eklentisi devre dışı bırakmanız gerekir.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Siyah Dikdörtgenler belge veya çalışma sayfasındaki denetimleri görünür  
 Denetimleri bir belge veya çalışma grubu, Visual Studio artık denetimleri tanır. Gruplandırılmış denetimleri erişilemez **özellikleri** penceresi ve belge veya çalışma sayfası üzerinde siyah dikdörtgenler olarak görünür. İşlevselliğini geri yüklemek için Denetim grubunu gerekir.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Word şablonu denetimleri, Visual Studio'da görünür değildir.  
 Visual Studio tasarımcıda bir Word şablonu açın, şablonda ayarlarına uygun olarak metin olmayan denetimler görünür olmayabilir. Visual Studio içindeki Word şablonları açılır olmasıdır **Normal** görünümü. Denetimleri görüntülemek için tıklayın **görünümü** menüsünde **Microsoft Office Word görünümü** ve ardından **düzeni**.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Küçük Resim Ekle komutu Visual Studio Tasarımcısı'nda hiçbir şey yapılmaz  
 Excel veya Word Visual Studio tasarımcıda açık olduğunda, tıklayarak **küçük resim** düğmesini **çizimler** Şerit sekmesinde açılmaz **küçük resim** görev bölmesi. Küçük resim eklemek için çalışma kitabı veya ana proje klasöründe belgenin bir kopyasını açın (olan kopyalamayacak *\bin* klasör) Visual Studio dışında küçük resim ekleyin ve ardından çalışma kitabını veya belgeyi kaydedin.  
  
##  <a name="code"></a> Kod yazma  
 Office projelerinde kod yazdığınızda, şu hatalarla karşılaşabilirsiniz.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Office nesne bazı olayları C# kullanırken erişilemez  
 Bazı durumlarda, bir Office birincil birlikte çalışma derlemesi (PIA), bir Visual C# projesinde türü örneği belirli bir olay erişmeyi denediğinizde aşağıdaki gibi bir derleyici hatası görebilirsiniz.  
  
 "'Microsoft.Office.Interop.Excel._Application.NewWorkbook' ve 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook' arasında belirsizlik var"  
  
 Bu hata, başka bir özellik veya yöntem nesnesinin aynı ada sahip bir olay erişmeye çalıştığınız anlamına gelir. Olay erişmek için nesnenin türüne kendi *olay arabirimi*.  
  
 Olayları olan office PIA türleri uygulayan iki arabirim: tüm özellikleri ve yöntemleri ile bir çekirdek arabirimi ve nesne tarafından sunulan olaylar içeren bir olay arabirimi. Bu olay arabirimleri adlandırma kuralı kullanmak *objectname*olayları*n*_olay, gibi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> ve <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Bir nesne bulmayı beklediğinize olaya erişemiyorsanız, kendi olay arabirimi nesnesine dönüştürün.  
  
 Örneğin, <xref:Microsoft.Office.Interop.Excel.Application> nesneler sahip bir <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> olay ve <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> özelliği. İşlenecek <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> olay cast <xref:Microsoft.Office.Interop.Excel.Application> için <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> arabirimi. Aşağıdaki kod örneği, Excel için belge düzeyi projede bunun nasıl yapılacağını gösterir.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Office PIA'ların arabirimlerde olay hakkında daha fazla bilgi için bkz. [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış](/previous-versions/office/office-12//ms247299(v=office.12)).  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>Olamaz Office PIA başvurusu sınıfları projelerinde hedefleyen [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], bir Office PIA'içinde tanımlanan bir sınıfa başvuruyor kod, varsayılan olarak derlenmez. PIA'ların sınıflarda adlandırma kuralı kullanmak *objectname*gibi sınıf <xref:Microsoft.Office.Interop.Word.DocumentClass> ve <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Örneğin, Word VSTO eklenti projesindeki aşağıdaki kod derlemeyecektir.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Bu kod, aşağıdaki derleme hataları oluşur:  
  
- Visual Basic: "derlemesi yok PIA modunu kullanarak bağlandığında başvuru 'belge sınıfı' sınıfına izin verilmiyor."  
  
- Visual C#: "'Microsoft.Office.Interop.Word.DocumentClass' katıştırılmış birlikte çalışma türü. Uygulanabilir arabirimi kullanın."  
  
  Bu hatayı gidermek için bunun yerine karşılık gelen arabirimi başvurmak için kodu değiştirin. Örneğin, başvurusu yerine bir <xref:Microsoft.Office.Interop.Word.DocumentClass> nesne, örneği başvuru <xref:Microsoft.Office.Interop.Word.Document> bunun yerine arabirimi.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]otomatik olarak varsayılan olarak Office PIA'ların gelen tüm birlikte çalışma türlerini katıştır. Gömülü birlikte çalışma türleri bu özellik yalnızca olmayan sınıflar arabirimleri ile çalıştığı için bu derleme hatası oluşur. Arabirimleri ve Office PIA'ların sınıfları hakkında daha fazla bilgi için bkz. [sınıflar ve arabirimler Office birincil birlikte çalışma derlemelerindeki genel bakış](http://go.microsoft.com/fwlink/?LinkId=189592). Office projelerinde gömülü birlikte çalışma türleri özelliği hakkında daha fazla bilgi için bkz. [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Office sınıflarına başvurular tanınmıyor  
 Örneğin uygulama, bazı sınıf adları gibi birden çok ad alanları olan <xref:Microsoft.Office.Interop.Word> ve <xref:System.Windows.Forms>. Bu nedenle, **içeri aktarmalar**/**kullanarak** niteleyici sabiti, bir toplu deyimini üst proje şablonları içerir:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 Bu kullanımı **içeri aktarmalar**/**kullanarak** örneğin Office Word veya Excel niteleyicisi sınıflarıyla başvuruları ayırt gerektirir:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 Örneğin bir nitelenmemiş bildirimi kullanıyorsanız hataları alırsınız:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 Word veya Excel ad alanı içe aktardıktan ve içindeki tüm sınıflar erişiminiz olsa bile, tam ad alanı belirsizliğini kaldırmak için Word ve Excel ile tüm türleri nitelemeniz gerekir.  
  
##  <a name="building"></a> Projeler derleme  
 Office projeleri oluşturduğunuzda şu hatalarla karşılaşabilirsiniz.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Sınırlı izinler ile bir belge temel alan bir belge düzeyi projesi derlenemiyor  
 Belge sınırlı izinlere sahip değilse visual Studio belge düzeyi projeler derlenemez. Projenizi içeren sınırlı izinlere sahip bir belge, proje derlenmez ve aşağıdaki iletisinde alırsınız **hata listesi** penceresi.  
  
 "Özelleştirme eklenemedi."  
  
 Sınırlı izinlere sahip bir belge dahil etmek istiyorsanız, geliştirme ve Çözümü derleyin Kısıtlamasız bir belge kullanın. Daha sonra Çözümü yayımladıktan sonra kısıtlı izinler yayımlama konumu belgede uygulanır.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange denetimi silindikten sonra derleme hataları oluşur.  
 Silerseniz bir <xref:Microsoft.Office.Tools.Excel.NamedRange> etkin çalışma tasarımcısında, otomatik olarak oluşturulan kodu olmayan bir çalışma denetiminden projenizden kaldırılmayabilir ve derleyici hataları oluşabilir. Kod kaldırıldığından emin olmak için her zaman içeren çalışma seçmelisiniz <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim silmeden önce etkin çalışma yapmak için denetim. Denetim sildiğinizde otomatik olarak oluşturulan kod silinmez, kod çalışma etkinleştirme ve böylece çalışma değiştirilmiş olarak işaretlemek bir değişiklik yapılarak silmek Tasarımcı neden olabilir. Projeyi yeniden kod kaldırılır.  
  
##  <a name="debugging"></a> Proje hata ayıklama  
 Office projelerinde hata ayıklaması yaparken şu hatalarla karşılaşabilirsiniz.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Yayımlama ve bir çözüm geliştirme bilgisayarına yüklemeniz kaldırmak için istem görüntülendiğinde  
 Office çözümünü hata ayıklaması yaparken, aşağıdaki hatayı görebilirsiniz.  
  
 "Başka bir sürümü yüklü olan ve bu konumdan yükseltilemez özelleştirme yüklenemez."  
  
 Bu hata, önceden yayımlanmış ve Office çözümleri geliştirme bilgisayarınızda yüklü olduğunu gösterir. Çözüme hata ayıklaması önce bir iletinin görüntülenmesini engellemek için çözüm bilgisayarda yüklü programlar listesinde kaldırın. Alternatif olarak, yayımlanan çözümünün yüklenmesi test etmek için geliştirme bilgisayarınızda başka bir kullanıcı hesabı oluşturabilirsiniz.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>UNC ağ konumlarında oluşturulan belge düzeyi projeler Visual Studio'dan çalıştırma  
 Excel veya bir UNC ağ konumunda Word için belge düzeyi projesi oluşturursanız, güvenilen konumlar listesine Excel veya Word belgesinin konumunu eklemeniz gerekir. Aksi takdirde, çalıştırmak veya Visual Studio'da proje hatalarını ayıklamaya çalıştığınızda, özelleştirme yüklenmez. Güvenilen konumları hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>İş parçacığı hata ayıklama sonrasında doğru durdurulmaz  
 Visual Studio'da Office projeleri program düzgün kapatmak hata ayıklayıcıyı etkinleştiren adlandırma bir iş parçacığı izleyin. İş parçacıkları çözümünüzde oluşturursanız, bu iş parçacığı hata ayıklamayı durdurduğunuzda düzgün şekilde işlendiğinden emin olmak için VSTA_ önekiyle her bir iş parçacığı adlandırmanız gerekir. Örneğin, ayarlayabilirsiniz `Name` ağ olayını bekler bir iş parçacığının özelliğini **VSTA_NetworkListener**.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Çalıştıramaz veya herhangi bir Office çözümü geliştirme bilgisayarında hata ayıklama  
 Çalıştırın veya geliştirme bilgisayarınızda bir Office projesi geliştirmek, aşağıdaki hata iletisini görebilirsiniz.  
  
 "Uygulama etki alanı oluşturulamadı çünkü özelleştirme yüklenemedi."  
  
 Visual Studio Fusion, .NET Framework derleme yükleyicisi derlemeleri Office çözümlerini yüklemeden önce önbelleğe almak için kullanır. Visual Studio Fusion önbelleğe yazabilirsiniz ve tekrar deneyin emin olun. Daha fazla bilgi için [gölge kopyalama derlemeleri](/dotnet/framework/app-domains/shadow-copy-assemblies).  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Düzenle ve devam et kullandıktan sonra bir belge düzeyi projede hata ayıklamayı durdurma hatası  
 Kullanırsanız **Düzenle** ve **devam** proje kesme modundayken, Excel veya Word için belge düzeyi projede kod için değişiklik yapmak için aşağıdaki hata iletisini içeren bir iletişim kutusu görebilirsiniz, ardından hata ayıklayıcıyı durdurun.  
  
 "Geçerli durumunda işlem sonlandırılıyor kaybı verileri ve sistem kararsızlığı gibi istenmeyen sonuçlara neden olabilir."  
  
 Tıkladığınız olup **Evet** veya **Hayır** iletişim kutusunda, Visual Studio, Excel veya Word'den işlemi sonlandırır ve hata ayıklayıcıyı durdurur. Bu iletişim kutusu görüntülenmeden projenin hata ayıklamasını durdurmak için Excel veya Word doğrudan yerine Visual Studio hata ayıklayıcının durdurulması çıkın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)   
 [Office çözüm güvenliğinde sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)   
 [Office çözümü dağıtımında sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)  
  
  