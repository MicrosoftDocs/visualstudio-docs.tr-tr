---
title: Özel Araçlar | Microsoft Docs
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
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793431"
---
# <a name="custom-tools"></a>Özel Araçlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Özel Araçlar* bir aracı bir projede bir öğe ile ilişkilendirmek ve dosyanın kaydedildiği zaman bu aracı sağlar. Bazı özel araçları, bazen olarak adlandırılan *tek dosya oluşturucular*, verilerden ve kod oluşturma çevirmenler uygulamak için sıkça kullanılır. Örneğin, tek dosya oluşturucular oluşturma [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] kaynak kodunun dışında .settings ve .resx dosyaları. Oluşturulan kaynak kod .settings ve .resx dosyalarındaki verileri kesin türü belirtilmiş erişmenizi sağlar. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] özel araçlar; proje türleri desteği [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje türleri yapın. Özel Araçlar kendi proje türleri de destekler.  
  
 Özel Araçlar, uygulama kayıtlı bileşenleridir `IVsSingleFileGenerator` arabirimi.  
  
 Özel araçlar ile ilişkili bir `ProjectItem` arabirimi nesnesi ve tasarımcılar ve düzenleyiciler gibi. Özel bir araç tarafından temsil edilen dosya alan bir `ProjectItem` olarak giriş ve dosya adı tarafından sağlanır, yeni bir dosya Yazar `DefaultExtension` yöntemi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Dosya Oluşturucular Ekleme](../../extensibility/internals/implementing-single-file-generators.md)  
 Nasıl kullanılacağını açıklar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> özel araç uygulamak için arabirim.  
  
 [Bir projenin varsayılan Namespace belirleme](../../misc/determining-the-default-namespace-of-a-project.md)  
 Kullanılan diline dayalı doğru ad alanını belirlemek açıklar.  
  
 [Tek Dosya Oluşturucuları Kaydetme](../../extensibility/internals/registering-single-file-generators.md)  
 Tüm kayıt defteri girdilerini açıklamaları için özel bir araç sağlar.  
  
 [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Nasıl proje sistemleri görsel tasarımcılar erişim üretilen sınıfları ve türleri için geçici taşınabilir yürütülebilir (PE) dosyaları desteği açıklanmaktadır.  
  
 [Proje Öğesinin Özelliğini Kalıcı Yapma](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Proje dosyasındaki bir kaynak dosyasının yazar gibi bir proje öğesi özelliği kalıcı hale getirmek gösterilmektedir.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Hakkında ayrıntılar sağlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, hangi dönüştüren tek bir giriş dosyası derlenmiş veya bir projeye eklenen bir tek çıkış dosyasına.  
  
 <xref:EnvDTE.ProjectItem>  
 Açıklar `ProjectItem` bir projedeki bir öğeyi temsil eden arabirim.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Hakkında ayrıntılar sağlar `DefaultExtension` yöntemi için çıkış dosyası adı verilen dosya adı uzantısını alır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Projeleri Genişletme](../../extensibility/extending-projects.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeler ve çözümler, kod dosyaları ve kaynak dosyalarını ve kaynak denetimi uygulamak nasıl düzenlemek için.

