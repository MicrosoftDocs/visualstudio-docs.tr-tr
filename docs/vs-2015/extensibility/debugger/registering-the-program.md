---
title: Program kaydetme | Microsoft Docs
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
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e26e15e17e69e8bf182d23161cb17ddbd5de0035
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797110"
---
# <a name="registering-the-program"></a>Program Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı bir bağlantı noktası aldıktan sonra tarafından temsil edilen bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi, ayıklanacak programın etkinleştirmenin sonraki adımı olan bağlantı noktası ile kaydetmek için. Kaydedildikten sonra program aşağıdaki yollardan birini kullanarak hata ayıklama için kullanılabilir:  
  
-   Çalışan bir uygulamanın hata ayıklama tam denetim kazanmak hata ayıklayıcı sağlayan ekleme, işlemi.  
  
-   Yalnızca hata ayıklama sonrasında-aslında bir hata ayıklayıcı bağımsız olarak çalışan bir programın hata ayıklama için izin veren zamanında (JIT). Çalışma zamanı mimari bir hataya yakalar, hata ayıklayıcı önce işletim sistemine bildirilir veya çalışma zamanı ortamı bellek ve hataya neden olan program kaynaklarını serbest bırakır.  
  
## <a name="registering-procedure"></a>Yordam kaydedilemedi  
  
#### <a name="to-register-your-program"></a>Programınızı kaydetmek için  
  
1.  Çağrı [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) bağlantı noktası tarafından uygulanan yöntem.  
  
     `IDebugPortNotify2::AddProgramNode` bir işaretçi gerektiren bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi.  
  
     Genellikle, bir program, işletim sistemi ya da çalışma zamanı ortamı yüklediğinde, program düğümü oluşturur. Hata ayıklama altyapısı (DE) programı yüklemek için sorulursa DE oluşturur ve program düğüm kaydeder.  
  
     Aşağıdaki örnek, program başlatma ve bağlantı noktası ile kayıt hata ayıklama altyapısı gösterir.  
  
    > [!NOTE]
    >  Bu, başlatın ve işlemi sürdürme tek yolu değildir; Bu, bir bağlantı noktası ile bir program kaydetme çoğunlukla bir örnektir.  
  
    ```cpp#  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı noktası alma](../../extensibility/debugger/getting-a-port.md)   
 [Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

