---
title: Kaynak denetimi VSPackage'ı mimarisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8a6b4c1e36f092bce89c57a2ead07a9e1a96a0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884140"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
Kaynak denetimi kullanan bir VSPackage Hizmetleri paketidir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] özelliklere sahip IDE sunar. Buna karşılık, bir kaynak denetimi paket, kaynak denetimi hizmetini işlevselliği sağlar. Ayrıca, bir kaynak denetimi daha verimli bir alternatif bir kaynak denetimi eklentisi kaynak denetimine tümleştirmek için daha pakettir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API uygulayan katı bir sözleşme'ne bağlıdır. Örneğin, bu eklenti varsayılan değiştirilemiyor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcı arabirimi (UI). Ayrıca, kaynak denetimi eklentisi API kendi kaynak denetimi modeli uygulamak bir eklenti etkinleştirmez. Bir kaynak denetimi paket ancak, bu sınırlamalardan hem de ortadan kaldırır. Kaynak denetimi paket kaynak denetim deneyimi üzerinde tam denetime sahip bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcı. Ayrıca, kendi kaynak denetimi modeli ve mantıksal bir kaynak denetimi paketini kullanabilir ve tüm kaynak denetimi ile ilgili kullanıcı arabirimleri tanımlayabilirsiniz.  
  
## <a name="source-control-package-components"></a>Kaynak denetimi paket bileşenleri  
 Mimari diyagramında gösterildiği bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi saplama adlı bir kaynak denetimi paketi ile tümleşen bir VSPackage bileşendir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Kaynak denetimi saplama aşağıdaki görevleri gerçekleştirir.  
  
- Kaynak denetimi paketi kaydı için gerekli olan ortak bir kullanıcı Arabirimi sağlar.  
  
- Bir kaynak denetimi paketi yükler.  
  
- Bir kaynak denetimi paketi etkin/etkin değil olarak ayarlar.  
  
  Kaynak denetimi saplama kaynak denetimi paket için etkin hizmet arar ve o paket için tüm gelen hizmet çağrıları IDE'den yönlendirir.  
  
  Özel bir kaynak denetimi, paket kaynak denetimi bağdaştırıcısı paketi olan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlar. Bu paket, kaynak denetimi kaynak denetimi eklentisi API tabanlı eklentileri desteklemek için merkezi bir bileşendir. Kaynak Denetimi Eklentisi eklenti etkin olduğunda, kaynak denetimi saplama olaylarına kaynak denetimi bağdaştırıcısı paketi gönderir. Buna karşılık, kaynak denetimi bağdaştırıcısı paketi kaynak denetimi eklentisi ile kaynak denetimi eklentisi API kullanarak iletişim kurar ve bir varsayılan, tüm kaynak denetimi eklentileri için ortak olan kullanıcı Arabirimi sağlar.  
  
  Kaynak denetimi paket paketi etkin olduğunda, diğer taraftan, kaynak denetimi saplama doğrudan paket ile birlikte kullanarak iletişim kurar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Source-Control paket arabirimleri. Kaynak denetimi paketin, kendi kaynak denetimi UI barındırmak için sorumludur.  
  
  ![Kaynak Denetim Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  Bir kaynak denetimi paketin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim kodu veya bir API tümleştirmesi için sağlamaz. Bu bölümünde açıklanan yaklaşımı Karşıtlık [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md) kaynak denetimi eklentisi sahip olduğu işlevleri ve geri aramalar katı bir dizi uygulamak.  
  
  Herhangi bir VSPackage gibi bir kaynak denetimi kullanılarak oluşturulan bir COM nesnesi bir pakettir `CoCreateInstance`. VSPackage'ı kendisi için kullanılabilir hale getirir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulayarak IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Bir örneği oluşturulduğunda bir VSPackage'ı site işaretçi alır ve bir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> kullanılabilir hizmetler ve arabirimler IDE içindeki VSPackage erişim sağlayan bir arabirimi.  
  
  Bir kaynak denetimi VSPackage'ı tabanlı paketi yazma kaynak denetimi eklentisi API tabanlı yazma değerinden daha gelişmiş programlama uzmanlık gerektiren eklenti.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)