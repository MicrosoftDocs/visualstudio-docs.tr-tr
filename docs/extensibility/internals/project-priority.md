---
title: Proje önceliği | Microsoft Docs
description: Visual Studio IDE 'nin kullandığı öncelik şeması, öğe birden fazla projenin üyesiyse bir öğeyi açmak için en iyi projeyi tespit edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac0556e63b25f0f2a0df399cb23d5e2e9473008
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899647"
---
# <a name="project-priority"></a>Proje Önceliği
Proje öğesi genellikle çözümdeki yalnızca bir projenin üyesidir. Bu nedenle, IDE, öğeyi açmak için hangi projenin kullanıldığını kolayca belirleyebilir. Ancak, bir öğe birden fazla projenin üyesiyse, IDE, öğeyi açmak için en iyi projeyi belirlemede bir öncelik şeması kullanır.

 Aşağıdaki listede, proje öncelik şeması gösterilmektedir:

- IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> belgenin o projenin bir üyesi olup olmadığını anlamak için çözümdeki her proje için yöntemini çağırır.

- Belge projenin üyesiyse proje, projenin işleme göre atadığı bir öncelik ile yanıt verir. Örneğin, bir dil projesi kendi dil kaynak dosyaları için yüksek öncelikli olarak yanıt verir, ancak yapı sürecinin bir parçası olarak kullanılmayan tanınmayan bir dosya türü için daha düşük bir önceliğe sahip olur.

- Bir belge için özel, projeye özgü düzenleyiciler ve tasarımcılar sağlayan projeler de yüksek öncelikli bir öncelik alır.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Sabit listesi belge önceliği değerlerini sağlar.

- En yüksek önceliğe sahip projeye belgeyi açmak için bağlam verilir. İki proje eşit öncelik değeri getirse, etkin proje tercih edilir. Çözümdeki bir proje belgeyi açabiliyorsa yanıt verirse, IDE belgeyi çeşitli dosyalar projesine koyar. Daha fazla bilgi için bkz. [çeşitli dosyalar projesi](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çeşitli Dosyalar Projesi](../../extensibility/internals/miscellaneous-files-project.md)
- [Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
