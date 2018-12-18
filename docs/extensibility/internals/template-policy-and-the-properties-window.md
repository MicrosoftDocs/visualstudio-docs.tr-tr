---
title: Şablon İlkesi ve Özellikler penceresinde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cf24f6f769ea9344d2a7716856e3c84fdf122de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816332"
---
# <a name="template-policy-and-the-properties-window"></a>Şablon İlkesi ve Özellikler Penceresi
Bir proje içinde bir kuruluş şablonu projesi içerdiğinde, kuruluş şablon proje ilkesini zorunlu kılabilir. Şablon İlkesi özelliklerin varsayılan değerlerini ayarlamak, özellikleri Gizle, özellikleri ekleyin ve benzeri için kullanılan bir kısıtlama sistemi haline gelir.  
  
 Bilgilerin görüntülenmesini denetlemek için şablon İlkesi'ni kullanarak **özellikleri** penceredir uygulama öğesinden farklı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Şablon İlkesi çözüm veya proje düzeyinde nesne özellikleri kısıtlamak için kullanılabilse de bileşen düzeyinde nesne özellikleri işler. Diğer bir deyişle  
  
- Üzerinde yöntemleri uygulamak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ne görüntülenen belirlemek için **özellikleri** belirli nesneler için Pencere  
  
- Şablon İlkesi çözüm ve proje düzeyinde ne görüntülenen belirlemek için kullanın. **özellikleri** daha önce belirtilen nesneler için Pencere  
  
  Belirli özellikleri seçici olarak kısıtlamak için şablon İlkesi'ni kullanarak **özellikleri** belirtilen türde bir proje öğesi zaman penceresi içinde seçili **Çözüm Gezgini** tüm üyeleri için yararlı olabilir Geliştirme ekibi bir proje üzerinde çalışıyor. Örneğin, Şablon İlkesi'ni kullanarak, tüm bağlantı dizesi bilgilerini bir veritabanında Geliştiricileriniz için ayarlamanız ve bağlantı dizesini salt okunur hale getirin. Her geliştirici güvence altına almak için basit bir yol, veri erişimi için doğru yolu kullanır, bu şekilde, sağlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)