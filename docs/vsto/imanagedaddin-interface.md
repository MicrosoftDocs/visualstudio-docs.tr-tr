---
title: IManagedAddin arabirimi
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ddede8542cda7499a9781c19a6baf1c58acfd125
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839550"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin arabirimi
  Uygulama yükleyen bir bileşen oluşturmak için Imanagedaddin arabirimi VSTO eklentileri yönetilen. Bu arabirim 2007 Microsoft Office sistemi eklendi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Imanagedaddin arabirimi tarafından tanımlanan yöntemler aşağıdaki tabloda listelenmiştir.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Microsoft Office çağırılır uygulama yönetilen bir VSTO eklentisi yükler.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Yalnızca Microsoft Office önce çağırılır, yönetilen bir VSTO eklentisi uygulamasını kaldırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 2007 Microsoft Office sistemi ile başlayarak, Microsoft Office uygulamaları, Office, VSTO eklentileri yükünü dengeleyebilmek için Imanagedaddin arabirimi kullanın. Kendi VSTO eklentisi yükleyici oluşturmak için Imanagedaddin arabirimi uygulayabilir ve çalışma zamanı için VSTO VSTO eklentisi yükleyicisini kullanmak yerine eklentileri, yönetilen (*VSTOLoader.dll*) ve [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Daha fazla bilgi için [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Yönetilen eklentiler yüklenen nasıl  
 Aşağıdaki adımlar, bir uygulama başladığında gerçekleşir:  
  
1. Uygulama, aşağıdaki kayıt defteri anahtarı altında girişleri arayarak VSTO eklentileri bulur:  
  
    **HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<uygulama adı >* \Addins\\**  
  
    Bu kayıt defteri anahtarı altında her girişin bir VSTO eklentisinin benzersiz kimliğidir. Genellikle, VSTO eklenti derlemesinin adını budur.  
  
2. Uygulama arayan bir `Manifest` her VSTO eklentisi için giriş altındaki girişi.  
  
    Yönetilen VSTO eklentileri depolayabileceğiniz bir bildirimde tam yolunu `Manifest` altında girdisi **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<uygulama adı >_ \Addins\\  _\<eklenti kimliği >_**. VSTO eklentisi yükünü dengeleyebilmek için kullanılan bilgileri sağlayan bir dosya (genellikle, bir XML dosyası) bildirimidir.  
  
3. Uygulama bulursa bir `Manifest` girişi, uygulama yönetilen bir VSTO eklentisi yükleyici bileşeni yüklemek çalışır. Imanagedaddin arabirimi uygulayan bir COM nesnesi oluşturmak deneyerek uygulamanın bunu yapar.  
  
    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Bir VSTO eklentisi yükleyici bileşeni içerir (*VSTOLoader.dll*), veya uygulama tarafından kendi Imanagedaddin arabirimi oluşturabilirsiniz.  
  
4. Uygulama çağrıları [IManagedAddin::Load](../vsto/imanagedaddin-load.md) yöntemi ve değerini geçişlerinde `Manifest` girişi.  
  
5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) yöntemi VSTO VSTO yüklenmekte eklentisi için uygulama etki alanı ve güvenlik ilkesi yapılandırma gibi eklentiyi yüklemek için gerekli görevleri gerçekleştirir.  
  
   Tarafından yönetilen bulmak ve yüklemek için Microsoft Office uygulamalarını kullanmaktadır anahtarlar VSTO eklentileri için kayıt hakkında daha fazla bilgi için bkz: [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Imanagedaddin uygulamak için kılavuz  
 Imanagedaddin uygularsanız, uygulama aşağıdaki CLSID içeren DLL kaydetmeniz gerekir:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office uygulamaları, bu CLSID Imanagedaddin uygulayan COM nesne oluşturmak için kullanın.  
  
> [!CAUTION]  
>  Bu CLSID tarafından da kullanılan *VSTOLoader.dll* içinde [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Bu nedenle, kendi VSTO eklentisi yükleyici ve çalışma zamanı bileşeni oluşturma Imanagedaddin kullanırsanız, VSTO dayanan eklentileri çalıştıran bilgisayarlara bileşeniniz dağıtamazsınız [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yönetilmeyen API Başvurusu &#40;Visual Studio'da Office geliştirme&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  