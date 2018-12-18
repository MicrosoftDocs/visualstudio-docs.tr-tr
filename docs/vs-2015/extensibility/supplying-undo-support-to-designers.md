---
title: Geri alma tasarımcıları için destek sağlama | Microsoft Docs
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
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3043bf41c3420644bcf8d65a2d8bbde86eff6910
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778507"
---
# <a name="supplying-undo-support-to-designers"></a>Tasarımcılara Geri Alma Desteği Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tasarımcılar, düzenleyiciler gibi genellikle kullanıcılar, bir kod öğesi değiştirirken son değişikliklerini ters çevirebilirsiniz böylece geri alma işlemlerinin desteklemesi gerekir.  
  
 Visual Studio'da uygulanan çoğu tasarımcıları otomatik olarak ortamı tarafından sağlanan geri alma desteği vardır.  
  
 Tasarımcı için geri alma özelliğini desteklemek için gereken uygulamaları:  
  
- Soyut temel sınıf uygulayarak geri Yönetimi sağlayın. <xref:System.ComponentModel.Design.UndoEngine>  
  
- Kalıcılık sağlar ve CodeDOM desteği uygulayarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> ve <xref:System.ComponentModel.Design.IComponentChangeService> sınıfları.  
  
  Tasarımcılar kullanarak yazma hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], bkz: [tasarım zamanı desteğini genişletmek](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Varsayılan geri alma altyapısı tarafından sağlar:  
  
- Sağlama, Yönetim uygulamaları aracılığıyla geri <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> ve <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> sınıfları.  
  
- Kalıcılığı ve varsayılan aracılığıyla CodeDOM desteği sağlayan <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> ve <xref:System.ComponentModel.Design.IComponentChangeService> uygulamaları.  
  
## <a name="obtaining-undo-support-automatically"></a>Otomatik olarak geri alma desteği alma  
 Oluşturduğunuz herhangi bir tasarımcı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otomatik ve tam geri desteğine sahip ise, Tasarımcı:  
  
-   Kullanan bir <xref:System.Windows.Forms.Control> kullanıcı arabirimi için sınıf tabanlı.  
  
-   Standart CodeDOM tabanlı kod oluşturma ve ayrıştırma sistem kod oluşturma ve kalıcılığı için kullanır.  
  
     Visual Studio CodeDOM desteği ile çalışma hakkında daha fazla bilgi için bkz. [dinamik kaynak kodu oluşturma ve derleme](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Zaman açık Tasarımcı geri alma desteği  
 Tasarımcılar tarafından sağlanan dışındaki bir görünüm bağdaştırıcısı olarak adlandırılan bir grafik kullanıcı arabirimi kullanıyorlarsa kendi geri yönetim sağlaması gerekir <xref:System.Windows.Forms.Control>.  
  
 Buna örnek olarak bir ürün olan bir grafik tasarımı web tabanlı arabirimi oluşturmak olabilir yerine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] grafik arabirim tabanlı.  
  
 Bu gibi durumlarda, bu görünüm bağdaştırıcısı ile kaydetmek ihtiyacım var [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>ve açık geri alma yönetimi sağlayın.  
  
 Tasarımcılar ihtiyacınız olmayan kullanırsanız CodeDOM ve Kalıcılık desteği sağlamak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sağlanan kod oluşturma modeli <xref:System.CodeDom> ad alanı.  
  
## <a name="undo-support-features-of-the-designer"></a>Tasarımcı desteği özelliklerini al  
 Ortamı SDK'sı varsayılan uygulamaları sağlamak için gereken arabirimleri geri kullanmayan tasarımcılar tarafından kullanılabilmesi için destek sağlar <xref:System.Windows.Forms.Control> sınıfların kullanıcı arabirimlerini veya standart bir CodeDOM ve Kalıcılık modeli.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Sınıf türetilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> uygulaması kullanarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> sınıfı yönetmek için geri alma işlemleri.  
  
 Visual Studio Tasarımcı geri alma için aşağıdaki özellik sağlar:  
  
- Birden çok tasarımcılar arasında bağlantılı geri alma işlevselliği.  
  
- Bir tasarımcı içinde alt birimleri uygulayarak ebeveynleri ile çalışabilirler <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> üzerinde <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
  Ortamı SDK'sı CodeDOM ve Kalıcılık sağlanarak destek sağlar:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> bir uygulamaları olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  A <xref:System.ComponentModel.Design.IComponentChangeService> tarafından sağlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'' tasarım ana bilgisayar.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Geri alma desteği sağlamak için ortamı SDK özelliklerini kullanma  
 Geri alma desteği elde etmek için bir tasarımcı uygulayan bir nesne gerekir:  
  
- Örneği oluşturmak ve bir örneğini başlatır <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> geçerli bir sınıfla <xref:System.IServiceProvider> uygulaması.  
  
- Bu <xref:System.IServiceProvider> sınıfı aşağıdaki hizmetleri sağlar:  
  
  -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Tasarımcılar kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDOM serileştirme kullanmayı seçebilir <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> ile sağlanan [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] uygulaması olarak <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
       Bu durumda, <xref:System.IServiceProvider> sınıfı için sağlanan <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Oluşturucusu uygulaması bu nesne döndürmelidir <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> sınıfı.  
  
  -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Varsayılan değeri kullanmanın tasarımcıları <xref:System.ComponentModel.Design.DesignSurface> tarafından sağlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tasarım konak varsayılan bir uygulama olmasını garanti edilir <xref:System.ComponentModel.Design.IComponentChangeService> sınıfı.  
  
  Uygulama tasarımcıları bir <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> tabanlı geri alma mekanizması, değişiklikleri otomatik olarak izler:  
  
- Özellik değişiklikleri aracılığıyla yapılan <xref:System.ComponentModel.TypeDescriptor> nesne.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> kabul edilen geri alınamaz bir değişiklik olduğunda olayları el ile oluşturulur.  
  
- Tasarımcı değişikliği bağlamı içinde oluşturulmuş bir <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
- Açıkça kullanarak geri alma birimi uygulaması tarafından sağlanan standart geri alma birimi oluşturmak Tasarımcı seçer <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> veya Visual Studio özel uygulama <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, öğesinden türetildiğini <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ve aynı zamanda sağlayan bir Her iki uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Tasarım zamanı desteği sunma](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

