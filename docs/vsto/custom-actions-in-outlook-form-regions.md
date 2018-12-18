---
title: Outlook form bölgelerindeki özel eylemler
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e2ad8e1c3b55d479cb031fe920e3027dbc1788c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671072"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook form bölgelerindeki özel eylemler
  Bir Microsoft Office Outlook öğesine yanıt vermesine olanak sağlayan bir düğme eylemleri görüntüler. Örneğin, bir posta öğesine yanıt vermek için kullanıcılar'ı tıklatın **yanıt**, **Tümünü Yanıtla**, veya **İleri** eylem düğmeleri. Bu eylemlerin her biri yeni bir posta öğesi oluşturur ve öğenin alan özgün öğeden bilgileri kullanarak doldurur.  
  
 Outlook öğesine herhangi bir türden açan özel bir eylem oluşturabilirsiniz. Örneğin, yeni bir randevu veya görev öğesi açan özel bir eylem ekleyebilirsiniz. Yeni öğe alanlarını doldurmak için özel kod kullanma ya da özel bir eylemin özelliklerini ayarlayın. Özel Eylemler görünür **özel eylemler** öğenin açık bir Outlook Inspector penceresinde açılır.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Özel Eylemler için form bölgesi ekleme  
 Form bölgesine özel bir eylem eklemek için **özel eylemler** iletişim kutusu. Açabileceğiniz **özel eylemler** iletişim kutusunda **Çözüm Gezgini** genişleterek **bildirim** düğümünün seçerek **CustomActions**özelliği ve ardından üç nokta düğmesini (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips")).  
  
 Kullanabileceğiniz **özel eylemler** belirtmek için iletişim kutusunda bir *hedef form*. Kullanıcı özel eylemin çalıştırdığı zaman görüntülenen formdaki bir hedef biçimidir.  
  
 Ayrıca **özel eylemler** iletişim kutusu bilgilerini özgün öğeden hedef formda görünmesini nasıl istediğinizi belirtin.  
  
 Aşağıdaki tablo, kullanılabilen özellikleri tanımlar **özel eylemler** iletişim kutusu.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**AddressLike**|Hedef form nasıl ele alınacağını belirtir.|  
|**Gövde**|Özgün öğe gövdesi hedef formun nasıl eklenir belirtir.|  
|**Etkin**|Özel eylemin etkin olup olmadığını gösterir. Bu özellik ayarlanırsa **false**, özel eylemdeki devre dışı bırakıldı.|  
|**Yöntemi**|Özel eylem çalıştırıldığında kullanılabilir yanıtının türünü belirtir. Özel eylem form gönderme, formu açın veya bunlar göndermek veya formunu açmak isteyip istemediğinizi sorar.|  
|**Ad**|Bu özel eylem kodda başvurmak için kullanabileceğiniz iç adını belirtir.|  
|**ShowOnRibbon**|Özel eylem özgün öğesinin şeridinde görüntülenip görüntülenmeyeceğini gösterir.|  
|**SubjectPrefix**|Hedef form konu satırı başında eklenen metni belirtir.|  
|**TargetForm**|Hedef form ileti sınıfı adını belirtir. Örneğin **IPM. Görev** görev formu açın.|  
|**Başlık**|Özel eylem düğmesinin etiketi belirtir.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Çalışma zamanında bir özel eylem özelleştirme  
 Kod kullanarak özel bir eylem için davranış da ekleyebilirsiniz. Örneğin, e-posta alıcılarının adlarını alır ve yeni bir randevu öğesi katılanlar olarak bu adları eklediği kod ekleyebilirsiniz. Bunu yapmak için işleme [özel](/office/vba/api/Outlook.MailItem.CustomAction) olayı [MailItem Nesnesi](/office/vba/api/Outlook.MailItem).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  