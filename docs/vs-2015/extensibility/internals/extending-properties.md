---
title: Özellikleri genişletme | Microsoft Docs
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
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 919b5a08f003d6e6c320edef4c1321af35f17388
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777883"
---
# <a name="extending-properties"></a>Özellikleri Genişletme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Özellikleri** penceresi COM ve COM + bileşenleri için bir evrensel özellik tarayıcısı ve tüm destekler [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ürünleri. **Özellikleri** penceresinde çalışır `ITypeInfo` bilgi ve herhangi bir tümleşik geliştirme ortamı (IDE) penceresinde şu anda seçili nesne için tasarım zamanı özellikleri listelemek için COM + meta verileri yazın.  
  
 **Özellikleri** klavyedeki F4 veya seçtiğinizde açılan penceresinde **Özellikler penceresi** üzerinde **görünümü** menüsünde, görüntülemek ve düzenlemek için kullanılır bağımsız yapılandırma, tasarım zamanı özellikleri ve seçili nesnelerin olayları. Bağımlı yapılandırma özellikleri, çözümler ve projeler, ile ilişkili görüntülenir [özellik sayfaları](../../extensibility/internals/property-pages.md). Daha fazla bilgi için [NIB: Proje özelliklerini](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md), ve [projelerinde NIB: öğesi Yönetimi](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Özellikler penceresine genel bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Özellik penceresi  
  
 Bu bölümde bireysel alanları için ilgili ayrıntılı bilgiyi **özellikleri** penceresi ve uygulamanız gereken arabirimleri ve pencereyi doldurmak için çağrı.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özellikler Penceresine Genel Bakış](../../extensibility/internals/properties-window-overview.md)  
 Amacını açıklar **özellikleri** penceresi araç penceresi ve belge penceresi.  
  
 [Şablon İlkesi ve Özellikler Penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Bir proje kuruluş şablon projesinde nasıl bulunur ve kurumsal şablon proje ilkesini zorunlu kılabilir nasıl ele alınmaktadır.  
  
 [Özellikler Penceresi Alanları ve Arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Hangi bilgilerin görüntülenen belirleyen seçimi temel açıklar **özellikleri** penceresi.  
  
 [Özellikler Penceresi Nesne Listesi](../../extensibility/internals/properties-window-object-list.md)  
 Amacını açıklayan **özellikleri** penceresi nesne listesi açıklayan bu listeden farklı bir nesne bir arama tetiklendiğinde nasıl ortamı yeni bir nesne seçili bilgisi verilir.  
  
 [Özellikler Penceresi Düğmeleri](../../extensibility/internals/properties-window-buttons.md)  
 Görüntülenen varsayılan dört düğme amacını **özellikleri** penceresi araç çubuğu.  
  
 [Özellikler Görüntü Kılavuzu](../../extensibility/internals/properties-display-grid.md)  
 Özellik adlarını ve özellik değerlerini alanları kılavuzda burada bulunan açıklar.  
  
 [İzleme özelliği pencere seçimi ile tanışın](../../misc/announcing-property-window-selection-tracking.md)  
 İzleme seçimi açıklar **özellikleri** penceresi.  
  
 [Alt özellikleri olan özellikleri gizleme](../../misc/hiding-properties-that-have-child-properties.md)  
 Alt özellikleri uygulayarak sahip özellikler Gizle açıklanmaktadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> arabirimi.  
  
 [Özel Özellikler penceresinde sağlama](../../misc/providing-a-custom-properties-window.md)  
 Kendi özellik tarayıcısı sağlama adımlarını ayrıntılı şekilde açıklar.  
  
 [Özellikler penceresinden alan tanımlarını alma](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Seçili özellik alanı için ilgili bilgileri görüntüler Açıklama alanını nerede bulunacağı açıklanır.  
  
 [Özellikler penceresindeki özellik değerlerini güncelleştiriliyor](../../misc/updating-property-values-in-the-properties-window.md)  
 Tutmak için iki yol gösteren adım adım yönergeler sağlar **özellikleri** penceresi özellik değeri değişiklikleri ile eşitlenir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Proje yapı taşları olarak ele alınmaktadır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)  
 Nasıl kullanabileceğinizi açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sürekli olarak test etme ve bunları derleme sırasında hata ayıklama uygulamaları için Platform.  
  
 [HTML belge özellikleri, özellik penceresi](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Özellikler penceresini doğrudan HTML belgesi düzenlemek için yönergeler sağlar ve bir HTML belgesi Özellikler penceresindeki alanları gerçekleşen bir tablo sağlar.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Açıklar `IDispatch` arabirimi, ilk erişmek ve nesnenin özellikleri ve yöntemleri hakkında bilgi almak için geç bağlanan bir mekanizma sunarak Otomasyonu desteklemek için tasarlanmıştır.  
  
 [NIB: Giriş Dinamik Özellikler (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Özellik değerleri uygulamanın derlenmiş kodu yerine bir dış yapılandırma dosyasında depolanır, böylece uygulamanız yapılandırmanıza imkan sağlayan dinamik özellikleri genel bir bakış sağlar.  
  
 [NIB: Proje olarak kapsayıcılar](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Proje rolünü mantıksal olarak yönetmek, derleme ve hata ayıklama uygulamanızı oluşturan öğeler için bir çözüm içindeki bir kapsayıcı olarak açıklar.  
  
 [NIB: Proje Özellikleri](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Projenin tamamı projeye Uygula denetim özellikleri ve ayrıca belirli proje derleme yapılandırmaları için sınırlı özellikleri olanak tanıyan ayarlar nasıl yönettiğini açıklanmaktadır.  
  
 [Çözümler ve Projeler](../../ide/solutions-and-projects-in-visual-studio.md)  
 Açıklayan nasıl [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] başvuruları, veri bağlantıları, klasörleri ve geliştirme çalışmalarınızı çözümler ve projeler aracılığıyla gerektirdiği dosyaları gibi öğeleri yönetir.  
  
 [Visual Studio’nun Diğer Bölümlerini Genişletme](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] geri kalanını eşleşen kullanıcı Arabirimi öğeleri oluşturmak için Sertifika Hizmetleri'ni [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

