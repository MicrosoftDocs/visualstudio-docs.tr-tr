---
title: Proje Subtypes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91a16ad11f7089230138919519922d58f3cc472
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130681"
---
# <a name="project-subtypes"></a>Proje alt türleri
Proje subtypes özelleştirme veya proje sistemleri davranış flavor izin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Özelleştirmeleri içeren proje dosyasında ekleme veya öğeleri filtreleme ek verileri kaydetme **Yeni Öğe Ekle** iletişim kutusu, derlemeler nasıl hata ayıklaması ve dağıtılan, denetleme ve projeyi genişletme **özelliği Sayfaları** iletişim kutusu. VSPackages proje alt türleri COM birleştirme kullanarak uygular.  
  
> [!NOTE]
>  Visual C++ proje sistemi proje alt türleri desteklemez. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kendi SQL Server ve akıllı aygıt projeleri uygulamak için proje subtypes kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)  
 Proje subtypes kavramını açıklar.  
  
 [Proje Alt Türlerinin Başlatılma Sırası](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Programsal proje alt başlatma sırası tarafından açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortamı.  
  
 [Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Ayrıntılı açıklamalar için proje subtypes kullanarak en sık genişletilmiş yöntemleri ve özellikleri sağlar.  
  
 [MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Proje dosyası verilerde sürdürmek nasıl ve nasıl kullanılacağını açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> proje alt toplama düzeyleri arasında proje dosyasındaki verileri korumak için.  
  
 [Proje Özelliği Kullanıcı Arabirimi](../../extensibility/internals/project-property-user-interface.md)  
 Proje subtypes proje nasıl değiştirebileceğiniz anlatılmaktadır **özellik sayfaları** iletişim kutusu.  
  
 [Temel Projenin Nesne Modelini Genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Proje subtypes Otomasyon nesne modeli genişletmek için Otomasyon Extender'larının nasıl kullanabileceğiniz hakkında bilgi sağlar.  
  
 [Yeni Öğe Ekleme İletişim Kutusuna Katkıda Bulunma](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Öğeleri eklemeyi açıklar **Yeni Öğe Ekle** iletişim kutusu.  
  
 [Proje Dosyalarında Verileri Kaydetme](../../extensibility/saving-data-in-project-files.md)  
 Proje alt nasıl kaydedebilir ve yönetilen paket Framework (MPF) kullanarak proje dosyasında alt özgü verileri almak açıklanmaktadır.  
  
 [Özelleştirilmiş Dağıtım İşleme](../../extensibility/internals/handling-specialized-deployment.md)  
 Proje subtypes özel dağıtım davranışı uygulayarak nasıl sağlayabilir açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> arabirimi.  
  
 [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)  
 Ekleme ve özellik sayfaları Proje Tasarımcısı'nda kaldırma açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Proje Türleri](../../extensibility/internals/project-types.md)  
 Ayrıntılı konulara bağlantılar sağlanır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeleri.