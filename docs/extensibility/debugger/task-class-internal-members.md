---
title: Görev sınıfı - dahili üyeler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9e9bbf6bbf42b8008850b540a59fa2b5d75b199
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276770"
---
# <a name="task-class---internal-members"></a>Görev sınıfı - dahili üyeler
Bu makalede iç üyelerine <xref:System.Threading.Tasks.Task?displayProperty=fullName> yardımcı sınıf, bir özel hata ayıklayıcı uygulama. Bu sınıf hakkında genel bilgi için bkz: <xref:System.Threading.Tasks.Task> başvurusu makalesinde.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (içinde *mscorlib.dll*)  
  
 Bu iç üyeleri .NET Framework'ten erişemediği için aşağıdaki söz dizimini ortak Ara dil (CIL) sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
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
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Çalışma durumuna ulaştı önce görev iptal veya görev, iptal Onaylandı ve özel durum tamamlandı gösterir.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Görevin çalıştığı gösterir.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Görev işlenmeyen bir özel durum nedeniyle tamamlandığını gösterir.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Görev Yürütme başarıyla tamamlandığını gösterir.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Görev tamamlandı, temsilciyi çalıştırıyor ve örtük olarak eklenen alt görevlerin tamamlanmasını bekliyor gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bunlar girişinin işaretlemek için aşağıdaki iç yöntemler bir hata ayıklayıcısı altyapısı kullanışlıdır <xref:System.Threading.Tasks.Task> kod yürütme:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework için paralel uzantı dahili bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)