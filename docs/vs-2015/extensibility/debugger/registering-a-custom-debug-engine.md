---
title: Hata ayıklama motoru özel bir kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ce7faf0ad538478d3291b48ac7306a39558663b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732644"
---
# <a name="registering-a-custom-debug-engine"></a>Özel Bir Hata Ayıklama Altyapısını Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı gereken kendisini COM kurallarına uygun bir sınıf üreteci kaydetmek yanı sıra Visual Studio kayıt defteri alt anahtarı Visual Studio ile kaydedin.  
  
> [!NOTE]
>  Hata ayıklama altyapısını kaydetme örneği bir parçası olarak oluşturulan TextInterpreter örneği bulunabilir [öğretici: bir hata ayıklama altyapısı kullanılarak ATL COM oluşturmaya](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>DLL sunucu işlemi  
 Genellikle, hata ayıklama altyapısı kendi DLL'de bir COM sunucusu olarak uygulanır. Başka bir deyişle, hata ayıklama altyapısı Visual Studio erişebilmeniz için önce COM ile kendi sınıf üreteci CLSID'si kaydetmelisiniz. Hata ayıklama altyapısı kendi Visual Studio ile kendisi herhangi bir özelliği (Aksi ölçümler olarak bilinen) oluşturmak için hata ayıklama kaydetmelisiniz sonra altyapısını destekler. Visual Studio kayıt defteri alt anahtarı'hata ayıklama altyapısı için yazılan ölçümler seçimi, hata ayıklama altyapısı destekler özelliklerine bağlıdır.  
  
 [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) yalnızca bir hata ayıklama altyapısı; kaydetmek gerekli kayıt defteri konumlarını açıklar aynı zamanda birçok kullanışlı işlevi ve oluşturan C++ geliştiricileri için bildirimleri içeren dbgmetric.lib kitaplığı açıklar daha kolay bir şekilde kayıt defterini düzenleme.  
  
### <a name="example"></a>Örnek  
 Nasıl kullanılacağını gösteren bir örnek (TextInterpreter örnekten) aşağıdadır `SetMetric` (dbgmetric.lib), Visual Studio ile hata ayıklama altyapısı kaydetmek için işlev. Geçirilen ölçümler de dbgmetric.lib içinde tanımlanır.  
  
> [!NOTE]
>  TextInterpreter temel hata ayıklama altyapısıdır; uygulamaz; ve bu nedenle kaydetme — diğer tüm özellikler. Daha eksiksiz bir hata ayıklama altyapısı tam bir listesi gerekir `SetMetric` çağrıları veya eşdeğeri, hata ayıklama altyapısı her bir özellik için bir tane destekler.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Öğretici: ATL COM kullanarak bir hata ayıklama altyapısı oluşturma](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)

