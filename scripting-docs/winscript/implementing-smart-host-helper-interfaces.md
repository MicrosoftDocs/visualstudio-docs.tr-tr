---
title: Akıllı konak yardımcı arabirimleri uygulama | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016e2a0641772992c9c3e6f423e105c42ae20ff1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909828"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Akıllı Konak Yardımcı Arabirimleri Uygulama
[Idebugdocumenthelper arabirimi](../winscript/reference/idebugdocumenthelper-interface.md) arabirimi akıllı barındırmak için gereken birçok arabirimler için uygulamaları sağladığından etkin hata ayıklama için bir akıllı ana bilgisayar oluşturma görevini büyük ölçüde basitleştirir.  
  
 Kullanarak akıllı bir konak olacak şekilde `IDebugDocumentHelper`, bir ana bilgisayar uygulaması yalnızca üç şey yapmanız gerekir:  
  
1. `CoCreate` İşlem Hata Ayıklama Yöneticisi ve kullanım [Iprocessdebugmanager arabirimi](../winscript/reference/iprocessdebugmanager-interface.md) hata ayıklanabilir uygulamaların listesi uygulamanıza eklemek için arabirim.  
  
2. Her komut dosyası için bir hata ayıklama belge Yardımcısı oluşturma kullanarak nesne [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) yöntemi. Belge adı, ana belge, metin ve komut dosyası blokları tanımlandığından emin olun.  
  
3. Uygulama [Iactivescriptsitedebug arabirimi](../winscript/reference/iactivescriptsitedebug-interface.md) arabirimi uygulayan nesneniz üzerinde [Iactivescriptsite](../winscript/reference/iactivescriptsite.md) (Bu, etkin komut dosyası için gerekli olan) arabirimi. Önemsiz yalnızca metottaki `IActiveScriptSiteDebug` arabirimi yalnızca yardımcıya atar.  
  
   İsteğe bağlı olarak, konak uygulayabilirsiniz [Idebugdocumenthost arabirimi](../winscript/reference/idebugdocumenthost-interface.md) söz dizimi renk, belge bağlam oluşturma ve genişletilmiş diğer işlevleri üzerinde ek denetim gerekiyorsa arabirim.  
  
   Akıllı konak yardımcı ana sınırlamasını içerikleri değiştirin veya (belgeler genişletebilirsiniz rağmen) eklendikten sonraki küçültme belge yalnızca işleyebilir ' dir. Birçok akıllı konakları için ancak sağladığı işlevsellik tam olarak ihtiyacınız olan şey olabilir.  
  
   Aşağıdaki bölümlerde, her adımda daha ayrıntılı açıklanmaktadır.  
  
## <a name="create-an-application-object"></a>Uygulama nesnesi oluşturun  
 Akıllı konak yardımcı kullanılmadan önce oluşturmak için gerekli bir [Idebugapplication arabirimi](../winscript/reference/idebugapplication-interface.md) uygulamanızı hata ayıklayıcısı temsil eden nesne.  
  
#### <a name="to-create-an-application-object"></a>Bir uygulama nesnesi oluşturmak için  
  
1.  İşlem hata ayıklama örneği Yöneticisi'ni kullanarak oluşturun `CoCreateInstance`.  
  
2.  Çağrı [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Kullanarak uygulamayı kümesinin adı [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Uygulama nesnesi kullanarak hata ayıklanabilir uygulamalar listesine eklemek [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Aşağıdaki kod işlem özetlenmektedir, ancak hata denetimi veya sağlam diğer programlama teknikleri içermez.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Idebugdocumenthelper kullanma  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>' % S'Yardımcısı (en az bir dizi adımdan) kullanmak için  
  
1.  Her ana belge için bir yardımcı kullanarak oluşturma [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Çağrı [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) Yardımcısı adı, belge öznitelikleri ve benzeri verir.  
  
3.  Çağrı [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) belge (veya belge kökü ise NULL) için üst Yardımcısı ile ağacında belgenin konumunu tanımlamak ve hata ayıklayıcı görünür hale getirmek için.  
  
4.  Çağrı [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) veya [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) belgenin metni tanımlamak için. (Bir tarayıcı durumunda olduğu gibi belge kademeli olarak yüklediyseniz bu birden çok kez çağrılabilir.)  
  
5.  Çağrı [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) her betik bloğu hem de ilişkili komut dosyası motorları aralıklarını tanımlamak için.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Iactivescriptsitedebug uygulama  
 Uygulamak için [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)belirtilen siteye karşılık gelen Yardımcısı alın ve sonra belirtilen kaynak bağlamı, aşağıdaki gibi kaydırın Başlangıç belgesini alın:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Ardından, belirli karakter kaydırma için yeni bir belge içeriği oluşturmak için yardımcıyı kullanın:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Uygulamak için [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), yalnızca çağrı `IDebugApplication::GetRootNode` (devralınan [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Uygulamak için [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), sadece dönüş `IDebugApplication` başlangıçta işlem hata ayıklama Yöneticisi'ni kullanarak oluşturduğunuz.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>İsteğe bağlı Idebugdocumenthost arabirimi  
 Ana bilgisayar uygulaması sağlayabilir [Idebugdocumenthost arabirimi](../winscript/reference/idebugdocumenthost-interface.md) kullanarak [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) yardımcı ek denetiminin kendilerinde olmasına. Konak arabirimi gerçekleştirmenize izin verir gereken önemli noktalar bazıları şunlardır:  
  
-   Metin ekleme [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) böylece ana karakterlerini hemen sağlamanız gerekmez. Karakterleri gerçekten gerektiğinde, yardımcı çağıracak [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) konaktaki.  
  
-   Yardımcısı tarafından sağlanan varsayılan söz dizimi renklendirmesi geçersiz kılar. Yardımcısı çağrıları [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) konak dönerseniz varsayılan uygulanması dönülüyor karakter, bir dizi renklendirme belirlemek için `E_NOTIMPL`.  
  
-   Belge bağlamı uygulama tarafından Yardımcısı tarafından oluşturulan bir kontrol eden bilinmeyen sağlayın [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Bu, varsayılan belge bağlamı uygulama işlevselliğini geçersiz kılmak konak sağlar.  
  
-   Bir yol adı dosya sistemindeki belge için sağlar. Bazı hata ayıklama kullanıcı arabirimleri düzenlemek ve değişiklikleri belgeye kaydetmek için kullanıcının izin vermek için bunu kullanın. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) Belge kaydedildikten sonra ana bilgisayara bildirmek için çağırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin Betik Hata Ayıklamaya Genel Bakış](../winscript/active-script-debugging-overview.md)