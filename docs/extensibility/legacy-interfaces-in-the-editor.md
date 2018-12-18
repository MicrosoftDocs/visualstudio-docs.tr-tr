---
title: Eski arabirimleri Düzenleyicisi'nde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5fdabadc1c3a0b5deda42aa268607e0f764e9b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849937"
---
# <a name="legacy-interfaces-in-the-editor"></a>Eski arabirimleri Düzenleyicisi
Visual Studio Düzenleyicisi eski arabirimlerden erişebilirsiniz. Visual Studio SDK'sı olarak da bilinen bağdaştırıcıları içerir *dolgular*, bu arabirimleri Düzenleyicisi ile etkileşim kurmak etkinleştirin. Bununla birlikte, yeni bir düzenleyici API kullanmak için eski kodunuzu güncelleştirmenizi öneririz. Kodunuzu daha iyi performans ve Windows Presentation Foundation (WPF) ve Yönetilen Genişletilebilirlik Çerçevesi (MEF) gibi yeni teknolojileri kullanabilirsiniz.  

## <a name="related-topics"></a>İlgili konular  

| Başlık | Açıklama |
| - | - |
| [Eski kod düzenleyicisine uyum](../extensibility/adapting-legacy-code-to-the-editor.md) | Kodunuzu yeni bir düzenleyici uyum açıklanmaktadır. |
| [Düzenleyici bağdaştırıcıları ile yeni veya değiştirilen davranışı](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | Düzenleyici bağdaştırıcıları davranışını Düzenleyicisi önceki sürümlerinde, farkı açıklar. |
| [Çekirdek Düzenleyicisi içinde](../extensibility/inside-the-core-editor.md) | Düzenleyicinin önceki sürümlerinden farklı bileşenlerini açıklar. |
| [Eski API'yi kullanarak çekirdek Düzenleyici örneği](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | Çekirdek Düzenleyici örneği oluşturmak için eski API'sini kullanmayı açıklar. |
| [Düzenleyici fabrikaları](../extensibility/editor-factories.md) | Düzenleyici fabrikaları eski API ile kullanmayı açıklar. |
| [Nasıl yapılır: Düzenleyici dosya türlerini kaydetme](../extensibility/how-to-register-editor-file-types.md) | Bir dosya adı uzantısı düzenleyiciniz için bağlantı açıklanmaktadır. |
| [İzlenecek yol: Düzenleyici çekirdek oluşturma ve bir düzenleyici dosya türünü kaydedin](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | Çekirdek düzenleyici oluşturma ve bir dosya adı uzantısı bağlantısına açıklanmaktadır. |
| [Nasıl yapılır: bağlam sağlamak için düzenleyicileri açma](../extensibility/how-to-provide-context-for-editors.md) | Bağlam düzenleyiciniz için sağlamayı açıklar. |
| [Dil Hizmetleri ve çekirdek Düzenleyicisi](../extensibility/language-services-and-the-core-editor.md) | Dil hizmeti ve düzenleyici arasındaki etkileşimler açıklanmaktadır. |
| [Erişim eski API'yi kullanarak metin arabelleği](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | Eski API'yi kullanarak metin arabelleğini erişimi açıklar. |
| [Eski API'yi kullanarak erişim erişimcisinde görünümü](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | Eski API'yi kullanarak metin görünümünü erişimi açıklar. |
| [Eski API'sini kullanarak kod windows özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | Kodu windows eski API'yi kullanarak özelleştirmek nasıl açıklar. |
| [Eski API'yi kullanarak erişim metin katmanları](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | Eski API'yi kullanarak metin farklı katmanlara erişimi açıklar. |
| [Metin işaretçileri eski API'si ile kullanma](../extensibility/using-text-markers-with-the-legacy-api.md) | Metin işaretçileri eski API'sini kullanarak ekleme işlemi açıklanmaktadır. |
| [Düzenleyici denetimleri ve menüler eski API'yi kullanarak özelleştirme](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | Düzenleyici denetimleri eski API'yi kullanarak özelleştirmek nasıl açıklar. |
| [Geri alma yönetmek ve eski API'yi kullanarak yineleme](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | Geri alma yönetmek ve eski API'yi kullanarak yineleme açıklanmaktadır. |
| [Nasıl yapılır: Bul uygulamak ve mekanizmasını değiştirin](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | Bul yönetmek ve eski API'yi kullanarak değiştirin açıklanmaktadır. |
| [Nasıl yapılır: dosya değişiklik bildirimlerini gösterme](../extensibility/how-to-suppress-file-change-notifications.md) | Eski API'yi kullanarak dosya değişiklik bildirimlerini bastır açıklanmaktadır. |
| [Özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md) | Özel düzenleyiciler ve tasarımcılar oluşturma açıklanır. |
| [Eski dil hizmeti geliştirme](../extensibility/internals/developing-a-legacy-language-service.md) | Özelleştirme olanağı sağlayan özellikleri ilgili belgelerin bağlantılarını sağlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dil hizmeti için destek ekleyerek çekirdek Düzenleyici. |
| [Yazı tipleri ve renkler kullan](../extensibility/using-fonts-and-colors.md) | Yazı tipleri ve renkler eski arabirimleri ile kullanmayı açıklar. |

