---
title: Eski Durum makinesi iş akışı Tasarımcısı'nı kullanarak | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 30eaf026d0558538c51b4cbda313e051348a5120
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231692"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Eski Durum Makinesi İş Akışı Tasarımcısını Kullanma
Oluştururken yeni bir Durum makinesi iş akışı projesi [!INCLUDE[vs2010](../includes/vs2010-md.md)] ya da hedefleyen [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], ya da kullanmayı da tercih edebilirsiniz **Durum makinesi iş akışı konsol uygulaması** veya  **Durum makinesi iş akışı Kitaplığı** eski proje şablonu. Bu durum makine proje şablonlarından birini seçerseniz, durum makine Tasarımcı eski iş akışı Tasarımcısı kullanıcı arabirimi olarak sunulur. Eski Durum makinesi proje şablonları hakkında daha fazla bilgi için bkz: [nasıl yapılır: oluşturma Durum makinesi iş akışı konsol uygulamaları (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) ve [nasıl yapılır: Durum makinesi iş akışı kitaplığı (eski)oluşturma](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Bir Durum makinesi iş akışı durumlarının bir kümesinden oluşur. Bir durum başlangıç durumu gösterilir. Her durum, belirli bir etkinlik kümesi alabilir. Etkinliğe göre başka bir duruma geçiş yapılabilir. Durum makinesi iş akışı, bir son duruma sahip olabilir. Son duruma geçiş yapıldığında, iş akışı tamamlanır.  
  
## <a name="state-machine-designer-views"></a>Durum makinesi Tasarımcı görünümleri  
 Durum makine Tasarımcısı etkinlikleri serbestçe tasarım yüzeyinde taşınabildiğinden, yani serbest biçimli bir tasarımcı olur. İki görünüm durumu makine Tasarımcı vardır: *durumu* görünümü ve *olay temelli* görünümü.  
  
 Durum görünümü, durum etkinlikleri ve bir durum etkinlik içinde bulunan olay temelli etkinlikleri gösterir. Bu görünümde, bir durumdan diğerine geçişleri genişleten olay denetimli etkinliğinden bir durumda başka bir duruma çizgilerle gösterilir. Geçişleri çizgi çizerek kendiniz de oluşturabilirsiniz. Geçiş çizmek için olay temelli etkinliği seçin ve etkinlik tutamaçları birini seçin ve sürükleyin. Bu eylem, bir çizgi çizer. Bu satırın ardından durumları arasında geçiş gösteren hedef durum, bağlı olduğu.  
  
 Olay görünümü temelli erişmek için olay temelli bir etkinliği çift tıklatın. Sıralı iş akışı Tasarımcısı gibi görünen tasarımcıyı olur. Tasarımcı üstünde gezinti çubuğunda görüntülenen olay temelli bir etkinlik kadar etkinlikleri hiyerarşisini gösterir. Durum görünümüne görüntülenen hiyerarşideki herhangi bir öğeyi tıklatarak gidebilirsiniz. Bir geçişi bir durumdan diğerine durum görünümünde çizmişseniz ve olay görünümü, etkinliğin temelli görüntülüyorsanız kümesi durum etkinlik olay temelli etkinliğine sizin için eklenir. Küme durumu etkinlik özelliklerini değiştirirseniz durum görünümünde yansıtılır.  
  
## <a name="state-machine-workflow-activities"></a>Durum makinesi iş akışı etkinlikleri  
 Aşağıdaki tabloda, bir Durum makinesi iş akışı Tasarımcısı'nda kullanılan anahtar etkinliklerini açıklar.  
  
|Araç adı|Etkinlik|Açıklama|  
|------------------|--------------|-----------------|  
|**State**|[Buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Bir durum makinesindeki bir durumu temsil eder; Ek içeren **buraya StateActivity** etkinlikler. Daha fazla bilgi için [buraya StateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Yeni bir durum geçiş belirtir. Daha fazla bilgi için [SetStateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Bir durum girildiğinde yürütür; diğer etkinlikleri içerebilir. Daha fazla bilgi için [StateInitialization etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|İçerilen etkinlikleri ayrılırken yürütür bir [buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinlik. Daha fazla bilgi için [StateFinalizationActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Çalıştırmaya başlamak için dış bir olaya kullanan durumları için kullanılır. **EventDrivenActivity** etkinlik uygulayan bir etkinlik içermelidir [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) ilk alt etkinlik olarak arabirimi. Daha fazla bilgi için [EventDrivenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Bir Durum makinesi iş akışı ana bileşeninde [buraya StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinlik. Bir Durum makinesi iş akışı çeşitli noktalarında yakalanan olayları gibi farklı durumları olaylarla ilişkili görevleri işlemek için girilir. İş akışı yaşam süresi boyunca, iş akışı bırakın ve birkaç farklı durumları girin. Bu durumları kullanarak birbirine [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) etkinlik.  
  
 Yeni bir sürüklediğinizde **buraya StateActivity** iş akışı tasarım yüzeyine sürükleyin, eklediğiniz [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), veya ek **buraya StateActivity** alt etkinlik olarak etkinlikler.  
  
> [!CAUTION]
>  İş akışları oluşturmak için Durum makinesi iş akışı Tasarımcısı'nı kullandığınızda tasarlama konusunda iş akışının yapı izleme **belge anahattı** Görünümü penceresi. Durum makinesi iş akışı içinde yapısını görünümünü **belge anahattı** Görünüm penceresi etkinlikler iş akışı işaretleme dosyasının, mantıksal düzenini yansıtır. Tasarım yüzeyinde göründükleri gibi fiziksel düzenini iş akışı etkinlikleri iş akışı işaretleme dosyasının etkinliklerin mantıksal düzenini yansıtma değil.  
>   
>  Açmak için **belge anahattı** penceresi, **görünümü** menüsünde **diğer Windows**ve ardından **belge anahattı**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Durum makinesi iş akışı konsol uygulamaları oluşturma (eski)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Nasıl yapılır: bir Durum makinesi iş akışı kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Durum makinesi iş akışları](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Buraya StateActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65083)   
 [StateInitializationActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65006)   
 [StateFinalizationActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65008)   
 [SetStateActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65082)   
 [EventDrivenActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65068)