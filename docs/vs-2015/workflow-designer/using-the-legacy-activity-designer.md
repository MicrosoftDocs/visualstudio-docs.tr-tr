---
title: Eski etkinlik Tasarımcısını kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a6c8aafe9eac26080bfbf57d06c7d512d1e1e62d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843437"
---
# <a name="using-the-legacy-activity-designer"></a>Eski Etkinlik Tasarımcısını Kullanma
Bu konuda, etkinlik Tasarımcısı içinde eski kullanmayı açıklar [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Eski Tasarımcı hedeflenirken kullanın [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Etkinlik Tasarımcısı özel etkinliklerinizi oluşturmanıza olanak sağlar.  
  
## <a name="creating-a-custom-activity"></a>Özel etkinlik oluşturma  
 Etkinlik Tasarımcısı'nı kullanarak özel bir etkinlik oluşturmak için aşağıdaki adımları izleyin:  
  
1. Üzerinde **proje** menüsünü tıklatın **etkinlik Ekle**.  
  
2. Seçin **etkinlik** veya **etkinlik (kod ayırma ile)** şablonu.  
  
   1.  Kullanım **etkinlik** etkinlik tanımı ve kullanıcı kodu aynı kod dosyasında olan etkinlik oluşturmak için şablon.  
  
   2.  Kullanım **etkinlik (kod ayırma ile)** bir etkinlik iş akışı biçimlendirmesi ve kullanıcı kodu ayrı bir kod dosyasında olarak ifade edilen etkinlik tanımı oluşturmak için şablon.  
  
3. Bir etkinlik adı yazın veya varsayılan adı bırakın ve ardından **Ekle**.  
  
   Yeni bir proje türünde oluşturarak özel etkinlikler kümesi oluşturabilirsiniz **iş akışı etkinlik Kitaplığı**. Bu proje türü hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir iş akışı etkinlik kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Bir etkinlik yapılandırma  
 Etkinlik Tasarımcısı etkin olsa da, aşağıdaki tabloda listelenen özellikleri yapılandırmak için özellik tarayıcısı kullanabilirsiniz.  
  
|Özellik|Açıklamalar|  
|--------------|--------------|  
|**Ad**|Etkinliğin adı.|  
|**Temel sınıf**|Etkinlik türetildiği temel sınıf. Varsayılan temel sınıf [öğeler SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). İçinde **özellikleri** penceresinde tıklayın **temel sınıf** üç nokta **[...]**  başka bir temel sınıfta seçilecek [göz atın ve bir .NET türünü seç iletişim kutusu (eski)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Açıklama**|Etkinlik kullanıcı tanımlı açıklaması.|  
|**Etkin**|Kümesine **True** Etkinlik yürütme ve doğrulamayı etkinleştirmek için varsayılan olarak. Kümesine **False** Etkinlik yürütme ve doğrulamayı devre dışı bırakmak için. Etkinlik yürütme ve doğrulama hakkında daha fazla bilgi için bkz. [geliştirme iş akışı etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Bağımlı etkinlikler ekleme  
 Çocuk etkinliklerinin tasarlarken etkinliğini araç kutusundan sürükleyebilirsiniz. Özellik tarayıcısı kullanarak her bir alt etkinlik daha sonra yapılandırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştirme iş akışı etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Özel etkinlik oluşturma](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Eski iş akışı etkinlikleri](../workflow-designer/legacy-workflow-activities.md)   
 [Özel etkinlikler örnekleri](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Nasıl yapılır: bir iş akışı etkinlik kitaplığı oluşturma (eski)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Eski İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-legacy-workflow-designer.md)