---
title: Hiyerarşiler
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
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2373909dbf218f24f148e0601d4dbb39cff1868
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061900"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio’da Hiyerarşiler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) proje olarak görüntüleyen bir *hiyerarşi*. IDE içinde bir hiyerarşi, her düğüme bir ilişkili özellikler kümesini sahip olduğu düğümlerinin ağacıdır. A *proje hiyerarşisi* proje öğelerini, öğeleri ilişkileri ve öğeleri ilişkili özellikler ve komutları tutan bir kapsayıcıdır.

 İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], hiyerarşi arabirimini kullanarak proje hiyerarşileri Yönet <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Arabirimi, proje öğeleri için çağırma standart komut işleyici yerine uygun hiyerarşisi penceresi komutları yönlendirir.

## <a name="project-hierarchies"></a>Proje hiyerarşiler
 Her proje hiyerarşisi, görüntüleyebileceği ve düzenleyebileceği öğeleri içerir. Bu öğeler, proje türüne göre değişiklik gösterir. Örneğin, bir veritabanı projesi veritabanı tabloları, veritabanı görünümlerini ve saklı yordamlarını içerebilir. Bir programlama dili proje Öte yandan, büyük olasılıkla kaynak dosyaları ve bit eşlemler ve iletişim kutuları için kaynak dosyaları içerir. Bir proje hiyerarşisi oluşturduğunuzda, bazı ek esneklik sağlayan hiyerarşileri yuvalanabilir.

 Yeni bir proje türü oluşturduğunuzda, proje türü içinde düzenlenebilir öğeleri tam kümesini denetler. Ancak, projeleri düzenleme desteği sahip oldukları olmayan öğeler içerebilir. Örneğin, Visual C++, HTML dosya türü için özelleştirilmiş bir düzenleyici sağlamaz olsa da Visual C++ projeleri HTML dosyaları içerebilir.

 Kalıcılık içerdikleri öğelerin hiyerarşileri Yönet. Uygulama hiyerarşisi hiyerarşi içinde öğelerin Kalıcılık etkileyen herhangi bir özel özellikler denetim gerekir. Örneğin, öğeleri deposundaki dosyaları yerine nesneleri temsil ediyorsa, hiyerarşi uygulama söz konusu nesnelerin Kalıcılık kontrol gerekir. IDE uyumlu kullanıcı girişi öğelerini kaydetmek için hiyerarşi yönlendirir, ancak IDE öğeleri kaydetmek için gereken tüm eylemleri denetlemez. Bunun yerine, denetiminde projesidir.

 Bir kullanıcı bir öğe bir düzenleyicide açıldığında, o öğe denetimleri hiyerarşi seçilir ve etkin olan hiyerarşi haline gelir. Seçili hiyerarşiyi bir öğeye hareket kullanılabilir komutları kümesini belirler. Bu şekilde kullanıcı odağı izleme, kullanıcının geçerli bağlam yansıtacak şekilde hiyerarşi sağlar.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje türleri](../../extensibility/internals/project-types.md) [seçim ve para birimi IDE'de](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK örnekleri](../../misc/vssdk-samples.md)
