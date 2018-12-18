---
title: Otomasyon modeline katkıda bulunma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d56b446914ae7345ccb0d393db8f17fc7f82c47
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513191"
---
# <a name="contribute-to-the-automation-model"></a>Otomasyon modeline katkıda bulunma
Visual Studio ortamı özelleştirmek için Otomasyon arabirimlerini sunmaktadır. Otomasyon modeli, Visual Studio eklentileri ve uzantıları oluşturmak son kullanıcıların sağlayan nesne modelidir.  
  
 Ayrıca, sizin için uygun Otomasyon modeline katkıda bulunmak için bir VSPackage geliştirici olarak; Bunu yaparak, eklentiler oluşturup, VSPackage içinde kullanıldığında genellikle model tutarlı bir kullanıcı deneyimi sağlamak için VSPackage son kullanıcıları etkinleştirme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Böylece fikirlerinizi otomasyon modeli, VSPackage için izler, VSPackage tasarlarken son kullanıcı deneyimi tutarlı hale getirmek için bir dizi izleyebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Otomasyon modeline genel bakış](../../extensibility/internals/automation-model-overview.md)  
 Otomasyon modeli, ortak bir ortam, ana özelliklerini denetleyen nesnelerin ilgili gruplar olarak tanımlar. Bu nesne kümesini Otomasyon modelinin bir diyagramda Resimli.  
  
 [Vspackage'lar için Otomasyon sağlar](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Otomasyon, VSPackage için sağlamak için başlıca iki yolu ele alınmaktadır.  
  
 [Proje nesnelerini kullanıma sunma](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage özgü nesneler oluşturmak için adım adım yönergeler sağlar.  
  
 [Proje Modelleme](../../extensibility/internals/project-modeling.md)  
 Otomasyon için yeni proje türünüzü oluşturmak için gerekli olan standart proje nesnelerini açıklar ve proje Otomasyon aşağıdaki yol göstermektedir. Bu konu, ayrıca listelerini bildirimleri ve uygulama için sınıflar sağlar.  
  
 [Olayları kullanıma sunma](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Otomasyon modeliniz için olaylar oluşturmak için adım adım yönergeler sağlar.  
  
 [Seçenekler sayfaları için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)  
 Özel bir VSPackage özelliklerini desteklemek için Otomasyon nesnesini döndürmeyi açıklar **seçenekleri** iletişim kutusunda **aracı** genişleterek menü `DTE.Properties` nesne.  
  
 [Kod için Otomasyon sağlar](../../extensibility/internals/providing-automation-for-code.md)  
 Kodunuz için bir otomasyon modeli oluşturma gerekli olmadığını açıklar. Ancak, kod modelleri ayrıntılı bilgileri sağlar. Bu konuda bir bağlantı sağlanır.  
  
 [Nasıl yapılır: Windows için Otomasyon sağlar](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Otomasyon sağlama hakkında fikir Otomasyon nesneleri bir penceresinde kullanılabilir hale getirmek istediğiniz ve ortam hazır Otomasyon nesnesi zaten sağlamaz olduğu açıklanmaktadır. Araç pencereleri ve belge pencereleri için Otomasyon açıklanır.  
  
 [Otomasyon modeli kullanın](../../extensibility/internals/using-the-automation-model.md)  
 Bir Otomasyon tüketici ilk proje Otomasyon nesneleri nasıl alacağını gösteren iki kod örneği sağlar.  
  
 [Yapılandırma ve SelectedItem nesneleri için Otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Yapılandırma ve SelectedItems nesneleri için Otomasyon hakkında bilgi sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 VSPackage DTE Otomasyon nesne modeli içerisinde nasıl katıldığı gösteren bir kod örneği sağlanmıştır. Seçili açıklamalar parametreleri ve dönüş değerleri listelenmektedir.  
  
