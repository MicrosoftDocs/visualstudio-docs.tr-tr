---
title: Bağlantı noktası alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39aa81216ad3b6e98162c68136734589b008873b
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645087"
---
# <a name="get-a-port"></a>Bir bağlantı noktası alma
Bir bağlantı noktası işlemleri çalıştırdığınız bir makine bağlantısını temsil eder. Bu makineyi, yerel veya uzak bir makinede olabilir (büyük olasılıkla çalışan Windows tabanlı olmayan bir işletim sistemi; bkz [bağlantı noktaları](../../extensibility/debugger/ports.md) daha fazla bilgi için).  
  
 Bir bağlantı noktası tarafından temsil edilen [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi. Bağlantı noktasına bağlı bir makinede çalışan işlemler hakkında bilgi almak için kullanılır.  
  
 Hata ayıklama altyapısı, program düğümleri bağlantı noktası ile kaydetmek için ve bilgi işlem isteklerini karşılamak için bir bağlantı noktasına erişmesi gerekir. Örneğin, hata ayıklama altyapısı uyguluyorsa [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirim uygulamasını [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) yöntemi için gereken işlem bağlantı noktası isteyin döndürülecek bilgileri.  
  
 Visual Studio hata ayıklama altyapısı için gereken bağlantı noktasını sağlar ve bu bağlantı noktasına bağlantı noktası sağlayıcısı alır. Bir program için bağlıysa ('nden ya da hata ayıklayıcısı içinde veya bir özel durum nedeniyle oluşturuldu, Just-in-Time [JIT] iletişim kutusunda, tetikler), kullanıcının Aktarım (bağlantı noktası sağlayıcısı için başka bir ad), tercih ettiğiniz verilir. Aksi takdirde, kullanıcı hata ayıklayıcı programın başlarsa, proje sistemi kullanılacak bağlantı noktası sağlayıcısı belirtir. Visual Studio tarafından temsil edilen bağlantı noktası sağlayıcısı ya da bir olay başlatır bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi ve yeni bir bağlantı noktasını çağırarak ister [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) ile bir [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) arabirimi. Bu bağlantı noktasını daha sonra bir form içinde hata ayıklama altyapısı veya başka bir aktarılır.  
  
## <a name="example"></a>Örnek  
 Bu kod parçasını sağlanan bağlantı noktası kullanma işlemini gösterir [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) program düğümünde kaydedilecek [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Bu kavramı için doğrudan ilgili parametreleri açıklık için atlandı.  
  
> [!NOTE]
>  Bu örneği başlatın ve işlemi sürdürmek için bağlantı noktası kullanır ve varsayar [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) arabirimi, bağlantı noktası üzerinde uygulanır. Olmadığı göre Hayır bu görevleri gerçekleştirmek için tek yol budur ve bağlantı noktası bile dışında programın için ilişkili olabilir değil, mümkündür [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) verilen.  
  
```cpp  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Program kaydetme](../../extensibility/debugger/registering-the-program.md)   
 [Bir program görüntüde hata ayıklamayı etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Bağlantı noktası sağlayıcıları](../../extensibility/debugger/port-suppliers.md)   
 [Bağlantı Noktaları](../../extensibility/debugger/ports.md)