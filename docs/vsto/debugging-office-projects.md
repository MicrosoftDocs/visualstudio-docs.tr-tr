---
title: Office projelerinde hata ayıklama
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc1774e57fafadafc7087bb498e0b77a90e96d85
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676887"
---
# <a name="debug-office-projects"></a>Office projelerinde hata ayıklama
  Office projeleri aynı Microsoft kullanarak ayıklayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer için kullandığınız araçları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeleri. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcı, kesme noktaları yerleştirin ve değişkenleri görüntüleme olanağı gibi özellikleri **Yereller** penceresinde, Office projelerinde hata ayıklaması yaparken de kullanılabilir. Hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklama araçları, bkz: [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Hata ayıklamayı kolaylaştırmak için derleme ve hata ayıklama önce Office uygulamasının tüm örneklerini kapatın.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="start-and-stop-the-debugger"></a>Başlatma ve durdurma hata ayıklayıcı  
 Diğer hata ayıklama Başlat gibi bir Office projesi hata ayıklamaya başlayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeleri; Örneğin, basabilirsiniz **F5** anahtarı. Bir VSTO eklenti projesinde hata ayıklamaya başladığınızda, hedeflenen Office uygulaması için yeni bir işlem başlatıldı ve VSTO eklentisi yüklenir.  
  
 Belge düzeyi projesinde hata ayıklamaya başladığınızda, yeni bir Word veya Excel işlem belge veya çalışma kitabı açılır.  
  
 Hata ayıklayıcıyı durdurduğunuzda, hata ayıklayıcı uygulama işlemi beklenmedik şekilde sonlandırılırsa veya ayırmak için hata ayıklayıcıyı varsa ayırır. Sonlandırılan Office uygulama işleminde açılan tüm belgelerin ayrıca uyarı vermeden kapatılır ve kaydedilmemiş tüm değişiklikler kaybedilir. Bu, tüm belgelerin veya hata ayıklayıcı çalışırken, açılan çalışma kitaplarını içerebilir.  
  
 Genellikle, böylece Office uygulaması normal bir şekilde çıkabilirsiniz, hata ayıklayıcının durdurulması önce işlemden ayırmak iyidir. Hala bir açık belge veya çalışma sayfası hata ayıklayıcıyı durdurduktan sonra çalışmak istiyorsanız da işlemden önce ayırabilirsiniz.  
  
 Art arda Word için belge düzeyi özelleştirmesi ayıklıyorsanız, hata ayıklayıcının durdurulması ve aniden kapanmasına neden bozulmasını Normal şablon açabilir. Bu durumda, bozuk Normal şablon silebilmeniz için ve sözcük bir sonraki açışınızda otomatik olarak oluşturulacaktır. Ancak, Normal şablon içinde depolandı makroların yeniden oluşturulmaz.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Office 2013 veya Office 2016 kullanarak Office 2013 VSTO eklentilerinde hata ayıklama  
 Visual Studio 2015 kullanıyorsanız ve yüklü Office yan yana iki sürümü varsa, Visual Studio Office 2016 başlatır. Visual Studio, Visual Studio 2013 kullanıyorsanız, Office 2013 başlatır.  
  
 VSTO eklenti Office (2013 veya 2016) açık farklı bir sürümünü kullanarak hata ayıklamak istiyorsanız **Proje Tasarımcısı**hem de **hata ayıklama** sekmesini, **harici program Başlat**seçenek düğmesini. Ardından, uygun Office uygulama yürütülebilir dosyasının konumuna göz atın.  
  
## <a name="f10-and-f11-behavior"></a>F10 ve F11 davranışı  
 Office projesinde hata ayıklamaya başladığınızda **F10** ve **F11** olarak diğer Visual Basic veya C# projelerinde hata ayıklama başladığınızda aynı davranışa sahip değil. Visual Basic veya C# projelerinde, ana işlev hata ayıklayıcıyı durdurur; Office projelerinde, Visual Studio Office uygulamasının ana işlevini üzerinde denetime sahip değil. Ancak, hata ayıklama sırasında **F10** ve **F11** Visual Basic ve C# projeleri olduğu gibi aynı işlevlere sahip değilsiniz.  
  
## <a name="display-exceptions"></a>Özel durumları görüntüle  
 Yönetilen kod şekli nedeniyle etkileşim yönetilmeyen kod ile Visual Studio, Microsoft Office uygulamaları tarafından oluşturulan hataları görüntülemez. Örneğin, bir VSTO Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan eklentisi bir özel durum oluşturursa, Microsoft Office uygulamasının hata görüntülemeden devam eder. Bu hataları görmek için ortak dil çalışma zamanı özel durumları hata ayıklayıcının ayarlayın. Daha fazla bilgi için [özel durumları hata ayıklayıcısı ile yönetme](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Ortak dil çalışma zamanı özel durumları hata ayıklayıcının ayarlarsanız, tüm özel durumları hata ayıklayıcısına, projeniz için uygun olmayabilir işlediğiniz ve bazı çalışma zamanının kendisi, ilk şans özel durumlar da dahil olmak üzere, artık kesintiye uğrar. Hataları msosec bulunmamasını her projede görünür ancak yoksaymak güvenlidir. Çözümünüzü msosec özel durumları etkilemez.  
  
 Ayrıca **deneyin... Catch** yöntemlerinizi özel durumları yakalamak için ifadeleri.  
  
 Varsayılan olarak, Visual Studio değil görünen Just-ın-Time hata ayıklama hataları için Office projeleri ayrıca yapar; Ancak, oluşan hataları görebilmeniz için bu özelliği etkinleştirebilirsiniz. Daha fazla bilgi için [Just-ın-Time debugging in Visual Studio](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri  
 Varsa **başlatma eylemi** üzerinde **hata ayıklama** özellik sayfası ayarlandığında **başlangıç projesi**, Visual Studio kullanmayan komut satırı bağımsız değişkenleri proje hata ayıklama sırasında olsa bile başlatma seçenekleri gibi komut satırı bağımsız değişkenleri belirtildi. Hata ayıklamaya başladığınızda, komut satırı bağımsız değişkenleri kullanmak istiyorsanız, seçmelisiniz bir **başlatma eylemi** dışında **başlangıç projesi**.  
  
## <a name="source-control"></a>Kaynak denetimi  
 Hata ayıklama özellikleri kaynak denetimi altında birden çok kullanıcı arasında paylaşılan değil. Visual Basic ve C# projeleri, bir kullanıcıya özel dosyada hata ayıklama özelliklerini depolar (*ProjectName*. vbproj.user veya *ProjectName*. csproj.user), ve bu dosya kaynak denetimi altında değil. Her kullanıcı birden fazla kişi hata ayıklama, hata ayıklama özelliklerini el ile girmeniz gerekir.  
  
## <a name="debug-cached-datasets-in-a-document-level-project"></a>Önbelleğe alınmış veri kümeleri bir belge düzeyi projede hata ayıklama  
 Bir projeyi her derlediğinizde, veri kümesini boşaltılıp ve yeniden. Önbellekteki veri kümesini hata ayıklamak istiyorsanız, Visual Studio dışında belgeyi açın ve ardından hata ayıklayıcıyı iliştirmek gerekir.  
  
## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Hata ayıklama Word belgesi projeleri Word 97-2003 belgeye dayalı (* .doc) biçimi  
 Word 97-2003 belgesi üzerinde temel alan bir Word belgesi proje hata ayıklama (*/*.doc *) biçimi, proje klasörünü güvenilir bir klasör listesine eklemeniz gerekir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).  
  
## <a name="debug-disabled-add-ins"></a>Hata ayıklama devre dışı eklentileri  
 Microsoft Office uygulamaları, beklenmedik şekilde davranmasına VSTO Add-Ins devre dışı bırakabilirsiniz. Bir Microsoft Office uygulamasının VSTO Add-Ins sorunlu kod uygulama başladığında her zaman yüklenmesini önlemek için devre dışı bırakır. Ancak, bu da tipik olarak hata ayıklama sırasında beklenmeyen davranışlara neden kolaydır. VSTO eklentileri yeniden etkinleştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir VSTO devre dışı bırakılmış eklentiyi yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Microsoft Office uygulamaları için VSTO eklentileri için kullandığınız devre dışı bırakma iki tür vardır: devre dışı bırakma ve yazılım devre dışı bırakılıyor.  
  
### <a name="hard-disabling"></a>Sabit devre dışı bırakma  
 Sabit devre dışı bırakma, uygulama beklenmedik bir şekilde kapatmak VSTO eklentisi neden olduğunda oluşabilir. Hata ayıklayıcıyı, ayrıca geliştirme bilgisayarınızda oluşabilir <xref:Microsoft.Office.Tools.AddIn.Startup> olay işleyicisinde, VSTO eklentisi yürütülüyor. Bir VSTO eklentisi sabit devre dışı olduğunda görünür **devre dışı öğeler** uygulama listesinde.  
  
 Bir VSTO Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan eklentisi bir Office uygulaması sabit devre dışı bırakır, yalnızca VSTO hata nedeniyle eklenti uygulama devre dışı bırakır. Diğer VSTO, Office uygulamaları için Visual Studio'da Office geliştirme araçları kullanılarak oluşturulmuş eklentileri yüklemeye devam eder.  
  
### <a name="soft-disabling"></a>Geçici olarak devre dışı bırakma  
 Bir VSTO eklentisi beklenmedik bir şekilde kapatmak uygulamanın neden olmayan bir hata oluşturursa, geçici olarak devre dışı bırakma ortaya çıkabilir. Sırasında işlenmeyen bir özel durum oluşturursa, bir uygulama geçici bir VSTO eklentisi devre dışı bırakabilir <xref:Microsoft.Office.Tools.AddIn.Startup> olay işleyicisi yürütüyordur. Bir VSTO eklentisi geçici olarak devre dışı olduğunda görünür **etkin olmayan uygulama eklentileri** uygulama ve uygulama listesinde değerini değiştirir **LoadBehavior** kayıt defteri girdisi için VSTO eklentisi yüklenmemiş olduğunu belirtmek için. Hakkında daha fazla bilgi için **LoadBehavior** kayıt defteri girdisi bkz [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Olay Görüntüleyicisi'ni kullanarak yükleme hatalarını giderme  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Yüklediğinizde veya Office çözümlerini oluşan tüm özel durumlar için Olay Görüntüleyicisi'nde Windows iletileri yazar. Bu iletiler, yükleme ve dağıtım sorunlarını gidermek için kullanabilirsiniz.  
  
## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Günlük dosyası ve hata iletilerini kullanarak başlangıç hatalarını giderme  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Günlüğe başlatma sırasında oluşan tüm hataları dosya ya da bir ileti kutusunda her hata görünen yazabilirsiniz. Varsayılan olarak, bu seçenekler devre dışı bırakılmıştır. Ortam değişkenlerini oluşturarak seçenekleri etkinleştirebilirsiniz.  
  
 Her hata bir ileti kutusunda görüntülenecek adlı bir ortam değişkeni oluşturma `VSTO_SUPPRESSDISPLAYALERTS` ve 0 (sıfır) olarak ayarlayın. Ortam değişkenini silerek veya 1 (bir) olarak ayarlayarak iletileri gösterilmemesini sağlayabilirsiniz.  
  
 Hataları bir günlük dosyasına yazmak için adlandırılmış bir ortam değişkenine oluşturma `VSTO_LOGALERTS` ve (bir tane) 1 olarak ayarlayın. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Günlük dosyası için VSTO eklentisi dağıtım bildirimini içeren klasöre ya da belge veya özelleştirme ile ilişkili çalışma içeren klasörü oluşturur. Bu başarısız olursa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yerel günlük dosyasını oluşturur *% TEMP %* klasör. Uygulama düzeyinde VSTO eklentileri için varsayılan addır *Eklentisi adı*. vsto.log. Belge düzeyinde projeler için günlük dosyasının adıdır. *belge adı*. *Uzantı*.log ExcelWorkbook1.xlsx.log gibi. Günlük kaydı hataları durdurmak için ortam değişkenini silin veya 0 (sıfır) olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Nasıl yapılır: bir VSTO devre dışı bırakılmış eklentiyi yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [VSTO eklentilerini programlama](../vsto/programming-vsto-add-ins.md)  
  
  