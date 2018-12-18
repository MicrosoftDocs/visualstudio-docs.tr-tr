---
title: Görev sınıfı - dahili üyeler | Microsoft Docs
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
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92ddc4b00f9d8eb37893e1db7ae44802e04e9c46
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764825"
---
# <a name="task-class---internal-members"></a>Görev Sınıfı - Dahili Üyeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu konu, iç üyelerini açıklar <xref:System.Threading.Tasks.Task?displayProperty=fullName> yardımcı sınıf, bir özel hata ayıklayıcı uygulama. Bu sınıf hakkında genel bilgi için bkz: <xref:System.Threading.Tasks.Task> başvuru konusu.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll içinde)  
  
 Bu iç üyeleri .NET Framework'ten erişemediği için aşağıdaki söz dizimini ortak Ara dil (CIL) sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="methods"></a>Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion Metodu](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Ayarlar veya TASK_STATE_WAIT_COMPLETION_NOTIFICATION durumu bit temizler.|  
|[NotifyDebuggerOfWaitCompletion Metodu](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Hata ayıklayıcı tarafından bir kesme noktası hedefi olarak kullanılan yer tutucu yöntemi.|  
  
### <a name="fields"></a>Alanlar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|İçindeki yürütülecek kodu temsil eden temsilcinin <xref:System.Threading.Tasks.Task> nesne.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Ek özellikleri depolar <xref:System.Threading.Tasks.Task> nesne.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Destek alanı <xref:System.Threading.Tasks.Task?displayProperty=fullName> üst özellik.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Geçerli durumuyla ilgili bilgileri depolayan <xref:System.Threading.Tasks.Task> nesne.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Eylem tarafından kullanılan verileri temsil eden nesne.|  
|[m_taskıd](../../extensibility/debugger/m-taskid-field.md)|Destek alanı <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> özelliği.|  
|[s_taskıdcounter](../../extensibility/debugger/s-taskidcounter-field.md)|Sonraki kullanılabilir tanımlayıcısı bir <xref:System.Threading.Tasks.Task> nesne.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Çalışma durumuna ulaştı önce görev iptal edildi veya görev, iptal onaylanır ve özel durum tamamlandı gösterir.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Görevin çalıştığı gösterir.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Görev işlenmeyen bir özel durum nedeniyle tamamlandığını gösterir.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Görev Yürütme başarıyla tamamlandığını gösterir.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Görev, temsilci yürütülmesi tamamlandı ve örtük olarak eklenen alt görevlerin tamamlanmasını beklediğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bunlar girişinin işaretlemek için aşağıdaki iç yöntemler bir hata ayıklayıcısı altyapısı kullanışlıdır <xref:System.Threading.Tasks.Task> kod yürütme:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework için Paralel Uzantı Dahili Bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

