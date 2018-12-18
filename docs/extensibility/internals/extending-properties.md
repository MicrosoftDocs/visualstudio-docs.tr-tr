---
title: Özellikleri genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77b5861dd084098e561f3642b5738dd0279d4b52
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512115"
---
# <a name="extend-properties"></a>Özellikleri genişletme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Özellikleri** penceresi COM ve COM + bileşenleri için bir evrensel özellik tarayıcısı ve tüm destekler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ürünleri. **Özellikleri** penceresinde çalışır `ITypeInfo` bilgi ve herhangi bir tümleşik geliştirme ortamı (IDE) penceresinde şu anda seçili nesne için tasarım zamanı özellikleri listelemek için COM + meta verileri yazın.  
  
 **Özellikleri** tuşuna basarak açılan penceresinde **F4** klavye veya seçerek **Özellikler penceresi** üzerinde **görünümü** menüsünde, bağımsız yapılandırma, tasarım zamanı özelliklerini ve seçilen nesnelerin olaylarını görüntüleyin ve düzenleyin için kullanılır. Bağımlı yapılandırma özellikleri, çözümler ve projeler, ile ilişkili görüntülenir [özellik sayfaları](../../extensibility/internals/property-pages.md). Daha fazla bilgi için [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Özellikler penceresine genel bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Özellik penceresi  
  
 Bu bölümde bireysel alanları için ilgili ayrıntılı bilgiyi **özellikleri** penceresi ve uygulamanız gereken arabirimleri ve pencereyi doldurmak için çağrı.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Özellikler penceresine genel bakış](../../extensibility/internals/properties-window-overview.md)  
 Amacını açıklar **özellikleri** penceresi araç penceresi ve belge penceresi.  
  
 [Şablon İlkesi ve Özellikler penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Bir proje kuruluş şablon projesinde nasıl bulunur ve kurumsal şablon proje ilkesini zorunlu kılabilir nasıl ele alınmaktadır.  
  
 [Özellikler penceresi alanları ve arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Hangi bilgilerin görüntülenen belirleyen seçimi temel açıklar **özellikleri** penceresi.  
  
 [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md)  
 Amacını açıklayan **özellikleri** penceresi nesne listesi açıklayan bu listeden farklı bir nesne bir arama tetiklendiğinde nasıl ortamı yeni bir nesne seçili bilgisi verilir.  
  
 [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md)  
 Görüntülenen varsayılan dört düğme amacını **özellikleri** penceresi araç çubuğu.  
  
 [Özellikler görüntü Kılavuzu](../../extensibility/internals/properties-display-grid.md)  
 Özellik adlarını ve özellik değerlerini alanları kılavuzda burada bulunan açıklar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Proje türleri](../../extensibility/internals/project-types.md)  
 Proje yapı taşları olarak ele alınmaktadır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)  
 Nasıl kullanabileceğinizi açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürekli olarak test etme ve bunları derleme sırasında hata ayıklama uygulamaları için platform.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Açıklar `IDispatch` arabirimi, ilk erişmek ve nesnenin özellikleri ve yöntemleri hakkında bilgi almak için geç bağlanan bir mekanizma sunarak Otomasyonu desteklemek için tasarlanmıştır.  
  
 [Uygulama ayarlarını yönetme (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Özellik değerleri uygulamanın derlenmiş kodu yerine bir dış yapılandırma dosyasında depolanır, böylece uygulamanız yapılandırmanıza imkan sağlayan uygulama ayarları genel bir bakış sağlar.  
  
 [Projeler ve çözümler](../../ide/solutions-and-projects-in-visual-studio.md)  
 Açıklayan nasıl [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başvuruları, veri bağlantıları, klasörleri ve geliştirme çalışmalarınızı çözümler ve projeler aracılığıyla gerektirdiği dosyaları gibi öğeleri yönetir.  
  
 [Visual Studio'nun diğer bölümlerini genişletme](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geri kalanını eşleşen kullanıcı Arabirimi öğeleri oluşturmak için Sertifika Hizmetleri'ni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].