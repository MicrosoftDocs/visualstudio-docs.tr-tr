---
title: Bir kaynak denetimi VSPackage'ı oluşturma | Microsoft Docs
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
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e85c25f1a5d935d36466e922659b5c2021b4c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779040"
---
# <a name="creating-a-source-control-vspackage"></a>Kaynak Denetimi VSPackage’ı Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belge mimarisine genel bakış ile tümleşik kaynak denetimi paketi bağlantılarını içerir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], uygulanacak arabirimleri ve tüketilmesi Hizmetleri tarafından tanımlanan API ve basit bir kaynağı gösteren bir örnek paket uygulama denetimi.  
  
 Bir kaynak denetimi VSPackage'ı ile kapsamlı tümleştirme yolu ile tümleştirmek kaynak denetimi için oluşturabileceğiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Varsayılan kaynak denetimi tarafından barındırılan UI atlamak için paketi etkinleştirir. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], proje sistemi kaynak denetimi isteklerine yanıt vermek ve etkileşim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bileşenleri gibi **Çözüm Gezgini**. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Güçlendirir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] iş ortakları ile tümleştirilebilir bir VSPackage'ı oluşturmak için bir mekanizma [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hizmet modelini kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Kaynak Denetimi Eklentisi Kaynak denetimi uygulamak için daha gelişmiş bir alternatifidir kaynak denetim paketi anlatılmaktadır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Mimari](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Bir diyagramını sunar ve kaynak denetimi paket bileşenlerinin açıklar.  
  
 [Özellikler](../../extensibility/internals/source-control-vspackage-features.md)  
 Bir kaynak denetim paketi çeşitli özelliklerini açıklar.  
  
 [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Bir kaynak denetim paketi için derin tümleştirme uygulamalıdır VSPackage'ı yapısını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 İçinde kaynak denetimi işlevlerini sağlar. kaynak denetimi eklentisi oluşturma anlatılmaktadır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetimi kullanıcı arabirimini (UI).  
  
 [Kaynak Denetimi](../../extensibility/internals/source-control.md)  
 Tümleşik bir özelliği olarak kaynak denetimi uygulama seçenekleri ele alınmaktadır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

