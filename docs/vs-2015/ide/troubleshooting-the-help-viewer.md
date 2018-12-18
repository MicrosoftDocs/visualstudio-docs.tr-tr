---
title: Yardım Görüntüleyicisi'ni sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3497d46ed4c9c5a04d8f40cc3056ea282593884
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934242"
---
# <a name="troubleshooting-the-help-viewer"></a>Yardım Görüntüleyici'de Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda Yardım Görüntüleyici ile karşılaşabileceğiniz sorunlar açıklanmaktadır.  
  
## <a name="audio-doesnt-work"></a>Ses çalışmıyor.  
 Yardım Görüntüleyici, bir ses yürütücüsü içermez. Ses içeren içeriği indir ve seçtiğinizde herhangi işlem gerçekleşmediyse **Play**, bir ses yürütücüsü yükleyin.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Arama, Windows Server 2008, Windows Server 2008 SP1 veya Windows Server 2008 R2 ile çalışmaz.  
 Yardım Görüntüleyicisi'nde arama ve filtre özellikleri Windows Search hizmetinin yüklenmesi gerekir ve. Varsayılan olarak, bu hizmet Windows Server 2008, Windows Server 2008 Service Pack 1 (SP1) ve Windows Server 2008 R2'de kapalıdır.  
  
#### <a name="to-activate-windows-search-service"></a>Windows Search hizmetini etkinleştirmek için  
  
1.  Sunucu Yöneticisi'ni başlatın.  
  
2.  Sol gezinti bölmesinde **rolleri**.  
  
3.  Rollerin özeti bölmesinde **Rol Ekle**.  
  
4.  Dosya Hizmetleri rolünü seçin ve ardından **sonraki** düğmesi.  
  
5.  Windows Search rol hizmetini seçin.  
  
## <a name="additional-resources"></a>Ek Kaynaklar  
 Daha fazla bilgi edinin ve şu kaynakları kullanarak Yardım Görüntüleyici hakkında geri bildirim sağlayın:  
  
- Geri bildirim sağlamak için bkz: [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) Microsoft Web sitesi veya gönderme e-posta için [ hlpfdbk@microsoft.com ](mailto:hlpfdbk@microsoft.com).  
  
- Daha fazla bilgi için [Developer Documentation and Help System](http://go.microsoft.com/fwlink/?LinkId=232741) Forumu ve [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blogu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yardım Görüntüleyici 2.1 Yönetici Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=243985)



