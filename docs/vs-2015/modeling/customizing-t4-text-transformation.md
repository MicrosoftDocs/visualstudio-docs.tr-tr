---
title: T4 metin dönüştürmeyi özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dc44c1de2e0a590b73916a8496a7fe5cae7cb07e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200245"
---
# <a name="customizing-t4-text-transformation"></a>T4 Metin Dönüştürmeyi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonları, bir özelliği olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program kodu veya bir dönüştürme işlemiyle diğer metin dosyaları oluşturmak kullanabilirsiniz. Kullanarak [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], metin şablonu yönerge işlemcisini veya metin şablonu ana bilgisayarı'nı özelleştirerek varsayılan şablonu dönüştürme süreci genişletebilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Metin Şablonu Dönüştürme Süreci](../modeling/the-text-template-transformation-process.md)  
 Metin dönüştürmenin nasıl çalıştığını açıklar ve şablonu ana bilgisayarı ve yönerge işlemcilerine rolünü açıklar.  
  
 [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Yönerge işlemcisini yönergeleri, şablonunuzda gibi işler `<#@template#>.` şablon derlenirken çalışır ve derlemeleri ve diğer kaynakları yükleyebilirsiniz. Ayrıca, çalışma zamanında kaynakları yükleyecek kod da ekleyebilirsiniz. Yönerge işlemciniz tanımlayarak şablonlarınızı karmaşıklığını azaltabilir.  
  
 [Bir VS Uzantısında Metin Dönüştürmeyi Çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Yazıyorsanız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı gibi bir menü komutu veya olay işleyicisi, uzantınızı metin şablonu oluşturma hizmetini herhangi bir metin şablonu dönüştürme için kullanabilirsiniz. Oturum nesnesi kullanarak şablona parametre verileri aktarmak ve değerleri şablon içinde almak `<#@parameter#>` yönergesi.  
  
 [Bir Özel Konak kullanarak Metin Şablonlarını İşleme](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Metin şablonunun kod yürütüldüğünde, ana dış dosyaları ve uygulama durumunu erişim sağlar. Örneğin, metin dönüştürmeleri çalıştığı konak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm Gezgini'ne erişim sağlayabilir. Ayrıca hatalar hata iletisi penceresinde görüntüler. Farklı bir bağlamda metin dönüştürmeleri çalıştırmak istiyorsanız, bu bağlamda kullanılamayan hizmetlerine erişim sağlayan kendi ana tanımlayabilirsiniz.  
  
 Yazıyorsanız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı, kendi ana bilgisayarınızı yazmak yerine metin dönüştürme hizmetini kullanmayı düşünün. Daha fazla bilgi için [bir VS uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Başvuru  
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)  
  
 Metin şablonu yönergeleri ve denetim blokları söz dizimi sağlar.



