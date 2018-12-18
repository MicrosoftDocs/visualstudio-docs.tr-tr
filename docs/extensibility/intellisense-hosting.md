---
title: IntelliSense barındırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28fc8ca212574c054add28e69a409fde4f58308a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638840"
---
# <a name="intellisense-hosting"></a>IntelliSense barındırma
Visual Studio IntelliSense barındırma sağlar. Sağlar barındırma IntellSense Visual Studio metin düzenleyicisi tarafından barındırılmadığında kod için IntelliSense sağlar.  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense barındırma kullanımı  
 Visual Studio'da tamamlama kümesi ve bir metin arabelleği erişimi olan herhangi bir kod IntelliSense windows yerden edinebilirsiniz kullanıcı arabiriminde (UI). Bazı örnek senaryolar bu tamamlanmasında olduğu **Watch** penceresi ya da bir kesme noktası Özellikler penceresinin koşul alanında.  
  
### <a name="implementation-interfaces"></a>Uygulama arabirimleri  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 IntelliSense açılır pencereleri barındıran herhangi bir UI bileşeni desteklemelidir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimi. Hisse varsayılan çekirdek düzenleyici metin görünümünü içerir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> geçerli IntelliSense işlevselliği korumak için uygulama arabirimi. Çoğunlukla, yöntemlerinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> ne bir alt kümesi üzerinde gerçekleştirilir temsil arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi. Alt IntelliSense UI işleme, giriş işaretini ve seçim düzenlemesi ve basit metin değiştirme işlevselliği içerir. Ayrıca, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimi, ayrı IntelliSense "konu" ve "içerik" böylece doğrudan bağlamları için kullanılan metin arabelleği yok konular için IntelliSense sağlanabilir sağlar.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimi sağlayıcısı uygulanmalı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> konak ne tür bir IntelliSense özellikleri belirlemek bir istemci etkinleştirme yöntemi destekler.  
  
 Tanımlanan konak bayrakları [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), aşağıda özetlenmiştir.  
  
|IntelliSense konak bayrağı|Açıklama|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Bağlamı arabelleğine bu bayrağı anlamına gelir ayarlama salt okunur ve düzenleme yalnızca konu metnini içinde gerçekleşir.|  
|IHF_NOSEPERATESUBJECT|Bu bayrak anlamına gelir, orada ayrı IntelliSense konu yok ayardır. Konu bağlamı arabelleğinde gibi geleneksel var. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense sistem.|  
|IHF_SINGLELINESUBJECT|Konu olmayan bu bayrağı ayarlamak bir tek satırlı düzenleme özelliği, gibi birden çok satırlı **Watch** penceresi.|  
|IHF_FORCECOMMITTOCONTEXT|Bu bayrağı ayarlarsanız ve bağlamı arabelleğine güncelleştirilmelidir konağı yok sayılacak bağlamı arabelleğine salt okunur bayrağı ve devam etmek için düzenlemeleri etkinleştirir.|  
|IHF_OVERTYPE|(Konu veya bağlam) düzenleme, üzerine yazma modunda yapılmalıdır.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit ve IVsIntellisenseHost.AfterCompletorCommit  
 Bu geri çağırma yöntemleri önce ve sonra metin ön işleme ve son işlemi etkinleştirmek için taahhüt tamamlama penceresini tarafından çağrılır.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Tümleşik geliştirme ortamı (IDE) tarafından kullanılan standart tamamlama penceresini birlikte oluşturulabilir sürümü arabirimidir. Tüm <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> arabirimi hızlı bir şekilde uygulayabilirsiniz IntelliSense bu completor arabirimini kullanarak.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop>