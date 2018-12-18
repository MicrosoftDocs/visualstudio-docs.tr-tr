---
title: Otomasyon modeline katkıda bulunma | Microsoft Docs
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
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53a669ed6f1ddaa9c2274371439828da24b92789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726970"
---
# <a name="contributing-to-the-automation-model"></a>Otomasyon Modeline Katkıda Bulunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio ortamı özelleştirmek için Otomasyon arabirimlerini sunmaktadır. Otomasyon modeli, Visual Studio eklentileri ve uzantıları oluşturmak son kullanıcıların sağlayan nesne modelidir.  
  
 Ayrıca, sizin için uygun Otomasyon modeline katkıda bulunmak için bir VSPackage geliştirici olarak; Bunu yaparak, eklentiler oluşturup, VSPackage içinde kullanıldığında genellikle model tutarlı bir kullanıcı deneyimi sağlamak için VSPackage son kullanıcıları etkinleştirme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Böylece fikirlerinizi otomasyon modeli, VSPackage için izler, VSPackage tasarlarken son kullanıcı deneyimi tutarlı hale getirmek için bir dizi izleyebilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)  
 Otomasyon modeli, ortak bir ortam, ana özelliklerini denetleyen nesnelerin ilgili gruplar olarak tanımlar. Bu nesne kümesini Otomasyon modelinin bir diyagramda Resimli.  
  
 [VSPackage’lar için Otomasyon Sağlama](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Otomasyon, VSPackage için sağlamak için başlıca iki yolu ele alınmaktadır.  
  
 [Proje Nesnelerini Kullanıma Sunma](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage özgü nesneler oluşturmak için adım adım yönergeler sağlar.  
  
 [Proje Modelleme](../../extensibility/internals/project-modeling.md)  
 Otomasyon için yeni proje türünüzü oluşturmak için gerekli olan standart proje nesnelerini açıklar ve proje Otomasyon aşağıdaki yol göstermektedir. Bu konu, ayrıca listelerini bildirimleri ve uygulama için sınıflar sağlar.  
  
 [Olayları Gösterme](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Otomasyon modeliniz için olaylar oluşturmak için adım adım yönergeler sağlar.  
  
 [Seçenekler Sayfaları için Otomasyon Desteği](../../extensibility/internals/automation-support-for-options-pages.md)  
 Özel bir VSPackage özelliklerini desteklemek için Otomasyon nesnesini döndürmeyi açıklar **seçenekleri** iletişim kutusunda **aracı** genişleterek menü `DTE.Properties` nesne.  
  
 [Kod için Otomasyon Sağlama](../../extensibility/internals/providing-automation-for-code.md)  
 Kodunuz için bir otomasyon modeli oluşturma gerekli olmadığını açıklar. Ancak, kod modelleri ayrıntılı bilgileri sağlar. Bu konuda bir bağlantı sağlanır.  
  
 [Nasıl Yapılır: Windows için Otomasyon Sağlama](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Otomasyon sağlama hakkında fikir Otomasyon nesneleri bir penceresinde kullanılabilir hale getirmek istediğiniz ve ortam hazır Otomasyon nesnesi zaten sağlamaz olduğu açıklanmaktadır. Araç pencereleri ve belge pencereleri için Otomasyon açıklanır.  
  
 [Otomasyon Modelini Kullanma](../../extensibility/internals/using-the-automation-model.md)  
 Bir Otomasyon tüketici ilk proje Otomasyon nesneleri nasıl alacağını gösteren iki kod örneği sağlar.  
  
 [Yapılandırma ve SelectedItem Nesneleri için Otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Otomasyon için yapılandırma seçeneklerini ve seçili öğeler için Otomasyon hakkında bilgi sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 VSPackage DTE Otomasyon nesne modeli içerisinde nasıl katıldığı gösteren bir kod örneği sağlanmıştır. Seçili açıklamalar parametreleri ve dönüş değerleri listelenmektedir.  
  
## <a name="related-sections"></a>İlgili Bölümler

