---
title: 'Nasıl yapılır: PolicyActivity kural kümesi (eski) oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7ab49957d830bf558a9dddf55cdc5e8c2f3f75d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194629"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Nasıl yapılır: PolicyActivity kural kümesi (eski) oluşturma
Bu konu eski kullanılarak ayarlanan ilke etkinlik kuralının nasıl oluşturulacağını açıklar [!INCLUDE[wfd1](../includes/wfd1-md.md)] hedefleyen [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Sürüklenen sonra bir **ilke** etkinlik öğesinden **araç kutusu** iş akışı tasarım yüzeyine, mevcut bir kuralı seçin veya yeni bir kural kümesini oluşturmak isteyeceksiniz [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) etkinlik. Mevcut bir kuralı ayarlamak için seçtiğiniz [seçin kuralı Ayarla iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md) ve kullanarak kural kümeleri oluşturma [kural kümesi Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Açabileceğiniz [kural kümesi Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) doğrudan çift tıklatarak iletişim kutusunu bir [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) iş akışı tasarım yüzeyinde etkinlik.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Seçmek veya PolicyActivity etkinliği için bir kural oluşturmak için  
  
1.  Sağ [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)ve ardından **özellikleri** açmak için **özellikleri** penceresi.  
  
2.  Tıklayın **RuleSetReference** özelliği.  
  
3.  Aşağıdakilerden birini yapın:  
  
    -   Tıklayın **RuleSetReference** üç nokta **[...]** seçip kümesinde mevcut bir kuralı [seçin kuralı Ayarla iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Ardından 10. adıma gidin.  
  
         veya  
  
    -   Bir kural kümesi için bir ad yazın. Tıklayın **RuleSetReference** üç nokta **[...]** ve ardından **Düzenle** içinde [seçin kuralı Ayarla iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         veya  
  
    -   Bir kural kümesi için bir ad yazın. Genişletin **RuleSetReference** özelliği ve üç noktayı seçin **[...]**  içinde **RuleSet tanımı** özelliği.  
  
         [Kural kümesi Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) açılır.  
  
4.  İçinde [kural kümesi Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), tıklayın **Kuralı Ekle** kural kümesine yeni bir kural eklemek için.  
  
5.  Girin **adı**, **öncelik**, ve **yeniden değerlendirme** özellikleri veya varsayılan değerleri koruyun.  
  
6.  Metni girin **koşul**.  
  
7.  Metni girin **ardından Eylemler** ve **başka eylemler**.  
  
8.  Tıklayın **Kuralı Ekle** yeniden başka bir kural eklemek için.  
  
9. İşiniz bittiğinde **Tamam**'a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Select kuralı Ayarla iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Kural kümesi Düzenleyicisi iletişim kutusu (eski)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [İlke etkinliği kullanma](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Eski İş Akışı Etkinlikleri ](../workflow-designer/legacy-workflow-activities.md)