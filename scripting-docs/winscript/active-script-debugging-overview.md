---
title: Etkin komut dosyası hata ayıklamaya genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8624c1405931edefe2e1e53e579ad28a7b238f1
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220228"
---
# <a name="active-script-debugging-overview"></a>Etkin Komut Dosyası Hata Ayıklamaya Genel Bakış
Etkin betik hata ayıklama arabirimleri, dilden bağımsız, konak nötr hata ayıklamaya izin verecek ve çok çeşitli geliştirme ortamlarında destekler.  
  
 ![Komut dosyası ana bilgisayarı işlemi](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Şekil 1  
  
 Bir dilden hata ayıklama ortamında herhangi bir programlama dili veya tüm dillere özel bilgisi olmadan programlama dillerinin bir karışımını destekler. Hata ayıklama ortamında, diller arası adımlama ve kesme noktaları da destekler. (Bu genel bakışta, öncelikle VBScript gibi dilleri komut desteği odaklanır ve [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Bir konak nötr hata ayıklayıcı, Internet Explorer veya özel bir ana bilgisayar gibi tüm etkin komut dosyası ana bilgisayarla otomatik olarak kullanılabilir. Konak, hangi hata ayıklayıcı kullanıcıya, belge ağacı içeriğine yapısını ve hata ayıklama belgelerin söz dizimi renklendirmesi sunan denetler. Bu, hataları ayıklanan kaynak kodu ana belge kapsamında gösterilmesini sağlar. Örneğin, Internet Explorer, bir HTML sayfasında bir betik gösterebilirsiniz.  
  
 Aşağıdaki alt bölümlerde, her anahtar bileşen etkin hata ayıklama ve ilişkili arabirimlerinden ele alınmıştır. Ancak, devam etmeden önce etkin hata ayıklama birkaç temel kavramları tanımlanmalıdır:  
  
 **Ana bilgisayar uygulaması**  
 Betik barındıran uygulama altyapıları ve kodlanabilir nesneler (veya "nesne modeli") sunmaktadır.  
  
 **Dil altyapısı**  
 Ayrıştırma, yürütme ve soyutlama belirli bir dil için hata ayıklama sağlayan bir bileşendir.  
  
 **hata ayıklayıcı IDE**  
 Konak uygulama ve dil altyapıları ile iletişim kurarak UI hata ayıklaması sağlayan uygulama.  
  
 **Makine Hata Ayıklama Yöneticisi** hata ayıklanabilir uygulama işlemlerinin bir kayıt defteri tutar bir bileşen.  
  
 **İşlem Hata Ayıklama Yöneticisi**  
 Belirli bir uygulama için hata ayıklanabilir belgelerinin ağaç tutan bir bileşeni, çalışan iş parçacıkları ve benzeri izler.  
  
 **Belge bağlamı**  
 Bir belge bağlamına ana belgenin bir kaynak kodu belirli bir aralıkta temsil eden bir soyutlamadır.  
  
 **Kod bağlamı**  
 Kod bağlamı çalışan kodu belirli bir konumda bir dil altyapısı (bir "sanal yönerge işaretçisi".) temsil eder.  
  
 **deyim bağlamı**  
 İfadeleri dil altyapısı tarafından değerlendirilebilir belirli bir içeriğe (örneğin, bir yığın çerçevesi).  
  
 **Nesne gözatma**  
 Bir nesnenin adı, türü, değer ve "izleme pencesine" uygulamak için uygun alt nesneleri yapılandırılmış, dilden bağımsız gösterimini kullanıcı Arabirimi.  
  
 Her anahtar etkin hata ayıklama bileşenleri ve bu arabirimler ayrıntılarını tarafından izlenen, karşılık gelen, ilişkili arabirim genel bir bakış aşağıdadır.  
  
## <a name="language-engine"></a>Dil altyapısı  
 Dil altyapısı sağlar:  
  
- Dil ayrıştırma ve yürütme.  
  
- Hata ayıklama desteği (kesme noktaları ve benzeri).  
  
- İfade değerlendirme.  
  
- Sözdizimi renklendirme.  
  
- Gözatma nesne.  
  
- Yığın numaralandırma ve ayrıştırma.  
  
  Aşağıda bir komut dosyası altyapısı hata ayıklama sağlamayı desteklemek için gereken arabirimleri, ifade değerlendirme ve nesne gözatma verilmiştir. Bu arabirimler, belge bağlamını ve altyapının kod bağlamları arasında eşleme ve ayrıca numaralandırma hata ayıklayıcı tarafından ifade değerlendirmesi yapmak için kullanıcı Arabirimi, yığın ve gözatma nesne için konak uygulama tarafından kullanılır.  
  
  [IActiveScriptDebug Arabirimi](../winscript/reference/iactivescriptdebug-interface.md)  
  Söz dizimi renklendirme ve kod bağlamı numaralandırma sağlar.  
  
  [IActiveScriptErrorDebug Arabirimi](../winscript/reference/iactivescripterrordebug-interface.md)  
  Bağlamları ve hatalar için yığın çerçevelerini verir belge.  
  
  [IActiveScriptSiteDebug Arabirimi](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Hata ayıklayıcı komut dosyası altyapısı bağlantısı sağlanan ana bilgisayar.  
  
  [IDebugCodeContext Arabirimi](../winscript/reference/idebugcodecontext-interface.md)  
  Bir sanal sağlar "yönerge işaretçisi" bir iş parçacığında.  
  
  [IEnumDebugCodeContexts Arabirimi](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Bir belge bağlamına karşılık gelen kod bağlamı numaralandırır.  
  
  [IDebugStackFrame Arabirimi](../winscript/reference/idebugstackframe-interface.md)  
  İş parçacığı yığınında bir mantıksal yığın çerçevesini temsil eder.  
  
  [IDebugExpressionContext Arabirimi](../winscript/reference/idebugexpressioncontext-interface.md)  
  İfadeleri değerlendirme bağlam sağlar.  
  
  [IDebugStackFrameSniffer Arabirimi](../winscript/reference/idebugstackframesniffer-interface.md)  
  Mantıksal yığın çerçevelerini numaralandırmak için bir yol sağlar.  
  
  [IDebugExpression Arabirimi](../winscript/reference/idebugexpression-interface.md)  
  Zaman uyumsuz olarak değerlendirilen bir ifade temsil eder.  
  
  [IDebugSyncOperation Arabirimi](../winscript/reference/idebugsyncoperation-interface.md)  
  Belirli bir engellenmiş iş parçacığı, iç içe geçmiş sırada gerçekleştirilmesi gereken işlem soyutlamak bir komut dosyası altyapısı sağlar.  
  
  [IDebugAsyncOperation Arabirimi](../winscript/reference/idebugasyncoperation-interface.md)  
  Bir zaman uyumlu hata ayıklama işlemi zaman uyumsuz erişim sağlar.  
  
  [IDebugAsyncOperationCallBack Arabirimi](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  İlerleme durumunu ilgili durum olayları sağlayan bir `IDebugAsyncOperation` arabirim değerlendirme.  
  
  [IEnumDebugExpressionContexts Arabirimi](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Bir koleksiyonu sıralar `IDebugExpressionContexts` nesneleri.  
  
  [IProvideExpressionContexts Arabirimi](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Belirli bir bileşen tarafından bilinen ifade bağlamları listelemek için bir yol sağlar.  
  
  [IDebugFormatter Arabirimi](../winscript/reference/idebugformatter-interface.md)  
  Bir dil veya değişken değerleri veya VARTYPE türler ile dizeler arasında dönüştürme özelleştirmek için IDE sağlar.  
  
  [IDebugStackFrameSnifferEx Arabirimi](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Mantıksal yığın çerçevesi için PDM numaralandırır.  
  
## <a name="hosts"></a>Konaklar  
 Ana bilgisayar:  
  
- Dil altyapıları barındırır.  
  
- Bir nesne modeli (betik oluşturulabilir nesne kümesi) sağlar.  
  
- Hata ayıklaması yapılabilir belge ağacının ve bunların içeriğini tanımlar.  
  
- Sanal uygulamalara betiklerini düzenler.  
  
  Konaklar iki tür vardır:  
  
- Yalnızca temel etkin komut dosyası yazma arabirimleri dumb konak destekler. Bu belge yapısı veya kuruluşlar üzerinde denetimi yoktur; Bu tamamen dil altyapıları için sağlanan betikleri tarafından belirlenir.  
  
- Bir akıllı ana bilgisayar, belge ağacı, belge içeriklerini ve söz dizimi renklendirmesi tanımlamanızı sağlayan daha büyük bir arabirimin destekler. Akıllı bir konak olacak şekilde bir konak için çok daha kolay hale sonraki alt bölümünde açıklanan yardımcı arabirimleri, bir dizi yoktur.  
  
### <a name="smart-host-helper-interfaces"></a>Akıllı konak yardımcı arabirimleri  
 `IDebugDocumentHelper` Yöntemleri bir ana bilgisayar tam karmaşıklığı (gücü) tam konak arabirimlerin işleme ve olmadan akıllı barındırma avantajlarını elde etmek için kullanabileceğiniz arabirimleri önemli ölçüde basitleştirilmiş bir dizi sağlar.  
  
 Bu arabirimler doğal olarak kullanılacak bir ana bilgisayar gerekli değildir. Ancak bu arabirimleri kullanarak, uygulama veya çok sayıda daha karmaşık arabirimleri kullanarak önleyebilirsiniz.  
  
 [IDebugDocumentHelper Arabirimi](../winscript/reference/idebugdocumenthelper-interface.md)  
 PDM tarafından uygulanan ve uygulamaları için akıllı barındırmak için gereken birçok arabirimler sağlar.  
  
 [IDebugDocumentHost Arabirimi](../winscript/reference/idebugdocumenthost-interface.md)  
 (İsteğe bağlı) söz dizimi renklendirme, hata ayıklayıcıya gibi ana bilgisayara özgü işlevleri kullanıma sunmak için ana bilgisayar tarafından uygulanır.  
  
 Daha fazla bilgi için [akıllı konak yardımcı arabirimleri uygulama](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Akıllı konak tam arabirimleri  
 Aşağıda tam bir akıllı ana bilgisayar uygulamak veya yardımcı arabirimleri kullanmıyorsa kullanan arabirimleri ayarlanır.  
  
 Ana bilgisayar tarafından uygulanan arabirimler:  
  
 [IDebugDocumentInfo Arabirimi](../winscript/reference/idebugdocumentinfo-interface.md)  
 Örneği değil veya bir belge hakkında bilgi sağlar.  
  
 [IDebugDocumentProvider Arabirimi](../winscript/reference/idebugdocumentprovider-interface.md)  
 İsteğe bağlı bir belge oluşturmak için gereken araçları sağlar.  
  
 [IDebugDocument Arabirimi](../winscript/reference/idebugdocument-interface.md)  
 Tüm hata ayıklama belgeler için temel arabirim.  
  
 [IDebugDocumentText Arabirimi](../winscript/reference/idebugdocumenttext-interface.md)  
 Hata ayıklama belge salt metin sürümüne erişim sağlar.  
  
 [IDebugDocumentTextAuthor Arabirimi](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Hata ayıklama belgesinin salt metin sürümünü düzenlenmesini sağlar.  
  
 [IDebugDocumentContext Arabirimi](../winscript/reference/idebugdocumentcontext-interface.md)  
 Hatası ayıklanmakta olan belgenin bir bölümünü soyut bir gösterimini sağlar.  
  
 Ana bilgisayar adına PDM tarafından uygulanan arabirimler:  
  
 [IDebugApplicationNode Arabirimi](../winscript/reference/idebugapplicationnode-interface.md)  
 İşlevselliğini genişletir `IDebugDocumentProvider` proje ağacı içinde bir bağlam sağlayarak arabirimi.  
  
## <a name="debugger-ide"></a>Hata ayıklayıcı IDE  
 Kullanıcı Arabirimi hata ayıklama dilden bağımsız bir ıde'dir. Şu olanakları sunar:  
  
- Belge görüntüleyiciler/düzenleyiciler.  
  
- Kesme noktası yönetimi.  
  
- İfade windows değerlendirme ve izleyin.  
  
- Yığın çerçeve göz atma.  
  
- Gözatma nesne/sınıfı.  
  
- Sanal uygulama yapısı göz atma.  
  
  Hata ayıklayıcı tarafından uygulanan arabirimler:  
  
  [IApplicationDebugger Arabirimi](../winscript/reference/iapplicationdebugger-interface.md)  
  Hata ayıklayıcı IDE oturumu tarafından kullanıma sunulan birincil arabirim.  
  
  [IApplicationDebuggerUI Arabirimi](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Dış bileşen hata ayıklayıcının kullanıcı arabirimini (UI) üzerinde daha fazla denetim sağlar.  
  
  [IDebugExpressionCallBack Arabirimi](../winscript/reference/idebugexpressioncallback-interface.md)  
  Durumu için olayları sağlar `IDebugExpression` değerlendirme ilerleme durumu.  
  
  [IDebugDocumentTextEvents Arabirimi](../winscript/reference/idebugdocumenttextevents-interface.md)  
  İlişkili metin belgeye yapılan değişiklikler belirten olayları sağlar.  
  
  [IDebugApplicationNodeEvents Arabirimi](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Olay arabirimi sağlayan `IDebugApplicationNode` arabirimi.  
  
### <a name="machine-debug-manager"></a>Makine Hata Ayıklama Yöneticisi  
 Makine Hata Ayıklama Yöneticisi, Bakım ve etkin sanal uygulamaların bir listesi sanal uygulamalar ve hata ayıklayıcılar arasında bağlantı noktası sağlar.  
  
 [IDebugSessionProvider Arabirimi](../winscript/reference/idebugsessionprovider-interface.md)  
 Hata ayıklama oturumu için çalışan bir uygulama oluşturur.  
  
 [IMachineDebugManager Arabirimi](../winscript/reference/imachinedebugmanager-interface.md)  
 Makine Hata Ayıklama Yöneticisi birincil arabirim.  
  
 [IMachineDebugManagerCookie Arabirimi](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Benzer şekilde `IMachineDebugManager` arabirimi, ancak bu arabirimi destekler hata ayıklama tanımlama bilgileri.  
  
 [IMachineDebugManagerEvents Arabirimi](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Sinyalleri çalışmasını değişiklikleri uygulama listesi Makine Hata Ayıklama Yöneticisi tarafından korunur.  
  
 [IEnumRemoteDebugApplications Arabirimi](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Bir makinede çalışan uygulamaları numaralandırır.  
  
### <a name="process-debug-manager"></a>İşlem Hata Ayıklama Yöneticisi  
 PDM şunları yapar:  
  
- Birden çok dil motorları, hata ayıklama eşitler.  
  
- Hata ayıklanabilir belge ağacı tutar.  
  
- Birleştirmeleri çerçeveler yığın.  
  
- Kesme noktaları ve dil altyapısı yelpazesini Adımlama düzenler.  
  
- İş parçacıkları izler.  
  
- Zaman uyumsuz işleme için bir hata ayıklayıcı iş parçacığını sürdürür.  
  
- Makine Hata Ayıklama Yöneticisi ve IDE hata ayıklayıcı ile iletişim kurar.  
  
  İşlem Hata Ayıklama Yöneticisi tarafından sağlanan arabirimleri aşağıda verilmiştir.  
  
  [IProcessDebugManager Arabirimi](../winscript/reference/iprocessdebugmanager-interface.md)  
  İşlem Hata Ayıklama Yöneticisi birincil arabirim. Bu arabirim, oluşturma, ekleme veya bir sanal uygulama bir işlemden kaldırma.  
  
  [IRemoteDebugApplication Arabirimi](../winscript/reference/iremotedebugapplication-interface.md)  
  Çalışan bir uygulamayı temsil eder.  
  
  [IDebugApplication Arabirimi](../winscript/reference/idebugapplication-interface.md)  
  Erişilemeyen hata ayıklama yöntemleri kullanmak için dil altyapıları ve konakları kullanımına sunar.  
  
  [IRemoteDebugApplicationThread Arabirimi](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Belirli bir uygulama içinde yürütme iş parçacığı temsil eder.  
  
  [IDebugApplicationThread Arabirimi](../winscript/reference/idebugapplicationthread-interface.md)  
  Dil altyapıları ve ana iş parçacığı eşitleme sağlamak ve iş parçacığına özgü, hata ayıklama durumunu bilgileri korumak için sağlar.  
  
  [IEnumRemoteDebugApplicationThreads Arabirimi](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Bir uygulamada çalışan iş parçacıkları numaralandırır.  
  
  [IDebugThreadCall Arabirimi](../winscript/reference/idebugthreadcall-interface.md)  
  Dağıtımları sıralanmış çağırır.  
  
  [IDebugApplicationNode Arabirimi](../winscript/reference/idebugapplicationnode-interface.md)  
  Hiyerarşideki bir belge için bir konum kullanır.  
  
  [IEnumDebugApplicationNodes Arabirimi](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Bir uygulama ile ilişkili bir düğümünün alt düğümleri numaralandırır.  
  
  [IEnumDebugStackFrames Arabirimi](../winscript/reference/ienumdebugstackframes-interface.md)  
  Yığın çerçevelerini motorlardan birleştirilmiş bir iş parçacığı, karşılık gelen sıralar.  
  
  [IDebugCookie Arabirimi](../winscript/reference/idebugcookie-interface.md)  
  Betik hata ayıklayıcıları içinde ayarlamak hata ayıklama tanımlama bilgisi sağlar.  
  
  [IDebugHelper Arabirimi](../winscript/reference/idebughelper-interface.md)  
  Nesne tarayıcı için bir üreteci ve komut dosyası motorları için basit bir bağlantı noktaları olarak görev yapar.  
  
  [ISimpleConnectionPoint Arabirimi](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Açıklayan ve kod altyapısı sayısı için bir bağlantı noktasında tetiklenen olayları numaralandırma için basit bir yol sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin Betik Hata Ayıklayıcı Arabirimleri](../winscript/reference/active-script-debugger-interfaces.md)
