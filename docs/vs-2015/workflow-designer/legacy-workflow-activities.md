---
title: Eski iş akışı etkinlikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205424"
---
# <a name="legacy-workflow-activities"></a>Eski İş Akışı Etkinlikleri
[!INCLUDE[wf](../includes/wf-md.md)] Varsayılan işlevler sağlayan denetim akışı koşulları, olay işleme, durum yönetimi ve iletişim için uygulamalar ve hizmetler ile etkinlik kümesini içerir. İş akışları tasarlarken tarafından sağlanan sistem tarafından sağlanan etkinlikler kullanabileceğiniz [!INCLUDE[wfd1](../includes/wfd1-md.md)], veya özel etkinliklerinizi oluşturabilirsiniz.  
  
 Aşağıdaki tabloda [!INCLUDE[wf2](../includes/wf2-md.md)] framework kullanıma hazır etkinlik kümesi. Çok sayıda, ancak tüm, bu etkinlikler erişilebilir etkinlik tasarımcıları tarafından temsil edilen **araç kutusu** , [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Bir etkinlik oluşturmak için kendi Tasarımcısından sürükleyin **araç kutusu** ve tasarım yüzeyine bırakın.  
  
|Etkinlik|Açıklama|  
|--------------|-----------------|  
|[Parametr CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|İle kullanılan **HandleExternalEventActivity** etkinliği için girdi ve çıktı iletişim ile yerel bir hizmet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Parametr CallExternalMethodActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[Aktivity Typu](http://go.microsoft.com/fwlink?LinkID=65050)|Tüm bileşik etkinliğin alt işiniz önce iptal bileşik bir etkinlik için temizleme mantığı içeren kullanılacak yürütülüyor. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CancellationHandlerActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Akışınız için Visual Basic veya C# kod eklemenize olanak tanır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CodeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Bir üst öğesi dengelenebilir sürümünü [öğeler SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableSequenceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Bir üst öğesi dengelenebilir sürümünü **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableTransactionScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Geri almak için veya bir hata oluştuğunda zaten iş akışı tarafından gerçekleştirilen işlemleri için dengelemek için kodunu çağırmasını sağlar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Tamamlanan TransactionScopeActivity etkinliğe yönelik maaş gerçekleştiren bir veya daha fazla etkinlikler için sarmalayıcı [!INCLUDE[crdefault](../includes/crdefault-md.md)] [CompensationHandlerActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Geçerli bir koşula göre alt etkinlikleri yürütür [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) etkinlik kendisini ve her alt için ayrı ayrı uygular koşullara bağlı. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ConditionedActivityGroup etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65028)|İş akışınızı bir zaman aşımı aralığına dayalı gecikme oluşturmanıza olanak sağlar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventDrivenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Belirtilen bir olay meydana geldiğinde yürütülen bir veya daha fazla etkinlikleri sarmalar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventDrivenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Bir etkinlik olayları ilişkilendirmek için bir çerçeve sunar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlersActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Kendi ana alt etkinlik ile concurrently yürütür bir [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlingScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Belirttiğiniz türü özel bir durumu işlemek için kullanılır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlerActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Alt etkinlik türünün sıralı bir listesi olan birleşik bir etkinlik temsil [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlersActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|İle birlikte kullanılan [parametr CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) etkinliği için girdi ve çıktı iletişim ile yerel bir hizmet. [!INCLUDE[crdefault](../includes/crdefault-md.md)][HandleExternalEventActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Her dala koşul test eder ve ilk dal için eşittir koşulu üzerinde etkinlikleri gerçekleştiren **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Bir dalı temsil eden bir [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Öğeye etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Bir Web hizmetini çağırmak, iş akışını etkinleştirir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWebServiceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Başka bir iş akışı çağırmak, iş akışını etkinleştirir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWorkflowActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Yalnızca içeren bir birleşik etkinlik [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) alt etkinlikler. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ListenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|İki veya daha fazla alt zamanlamak için bir yol sağlar **öğeler SequenceActivity** aynı anda işleme için etkinlik dalları. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ParallelActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Kural koleksiyonunu temsil etmek için bu seçeneği kullanın. Bir kural koşulları ve sonuçta elde edilen Eylemler oluşur. [!INCLUDE[crdefault](../includes/crdefault-md.md)][PolicyActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Birden çok örneğini tek bir alt etkinlik oluşturur. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ReplicatorActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[Öğeler SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Birden çok etkinlik sıralı yürütme için bir arada bağlamak için basit bir yol sağlar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Öğeler SequenceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Yeni bir durum geçiş belirtir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SetStateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[Buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Bir Durum makinesi iş akışı bir durumda temsil eder. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Buraya StateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Kullanılan bir [buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) ayrılırken yürütülen alt etkinlikler için kapsayıcı olarak etkinlik **buraya StateActivity** etkinlik. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateFinalizationActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Kullanılan bir [buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) girerken yürütülen alt etkinlikler için kapsayıcı olarak etkinlik **buraya StateActivity** etkinlik. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateInitializationActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Özel dikkat gerektiren bazı hata koşulu durumunda müdahale etkinleştirmek için iş akışı işlemini askıya alır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SuspendActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|İçerilen etkinlikleri eşitlenmiş bir etki alanında sıralı olarak yürütür. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SynchronizationScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Hemen bir hata koşulu olması durumunda iş akışınızın işlemi sona olanak tanır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][TerminateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|İşlem meta verileri için bir iş akışı kapsamında oluşturulan iş özel durumu yakalamanızı sağlar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ThrowActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|İşlemler ve özel durum işleme için bir çerçeve sunar. Daha fazla bilgi için [TransactionScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Bir Web hizmeti hata oluşumunu modeli sağlar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceFaultActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Bir Web hizmetinden veri alır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceInputActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Bir iş akışı için yapılan bir Web hizmeti isteğine yanıt verir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceOutputActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Bir koşul yerine getirilene kadar döngü, iş akışını etkinleştirir. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WhileActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] özel etkinlikler oluşturmak nasıl [özel etkinlikler geliştirmeyi](http://go.microsoft.com/fwlink?LinkID=65023) ve [eski etkinlik Tasarımcısını kullanarak](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Etkinlik Görünümleri (Eski)](../workflow-designer/activity-views-legacy.md)  
 Etkinliklerin farklı tasarım görünümler açıklanır.  
  
 [Nasıl Yapılır: Araç Kutusuna Etkinlik Ekleme (Eski)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Araç kutusuna etkinlik ekleme işlemi gösterilmektedir.  
  
 [Nasıl Yapılır: Bildirime Dayanan Kural Koşulu Oluşturma (Eski)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Bildirime dayanan Kural koşulu oluşturma adımları gösterilmektedir.  
  
 [Nasıl Yapılır: PolicyActivity Kural Kümesi Oluşturma (Eski)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 PolicyActivity kural kümesi oluşturma adımları gösterilmektedir.  
  
 [Nasıl Yapılır: WCF Bütünleştirme İşlemi Gerçekleştirme (Eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Uygulamak için bu adımları gösteren bir [!INCLUDE[indigo2](../includes/indigo2-md.md)] sözleşme işlemi.  
  
 [Nasıl Yapılır: WCF Bütünleştirme İşlemi Çağırma (Eski)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Çağrılacak adımları gösteren bir [!INCLUDE[indigo2](../includes/indigo2-md.md)] sözleşme işlemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Workflow Foundation etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65005)   
 [İş akışları geliştirme](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Geliştirme iş akışı etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65023)