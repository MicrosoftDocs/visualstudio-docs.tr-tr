---
title: Betik hata ayıklamasında sınırlamalar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c85f990d08a41bd4b4ee25190d0c5b6bd99d340
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058028"
---
# <a name="limitations-on-script-debugging"></a>Betik Hata Ayıklamasında Sınırlamalar
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bu konudaki sınırlamalar istemci tarafı komut dosyası hata ayıklamayı destekler.  
  
## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Kesme noktası eşleme istemci tarafı komut dosyası ile ilgili bir sınırlama  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir istemci-tarafı dosyaya çalışma zamanında dönüştürülen bir sunucu tarafı ASPX veya HTML dosyasında bir kesme noktası ayarlamanıza olanak tanır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istemci-tarafı dosyasında, aşağıdaki sınırlamalara tabi karşılık gelen bir kesme noktası için sunucu tarafı dosyasından bir kesme noktası eşler:  
  
-   Kesme noktalarını ayarlayın, içinde `<script>` engeller. Satır içi komut dosyasında kesme noktaları veya `<% %>` blokları eşlenemez.  
  
-   Sayfa için tarayıcı URL'si sayfa adı içermelidir. Örneğin, http://microsoft.com/default.apsx. Kesme noktası eşleme yapılamıyor tanıması bir adresinden yeniden yönlendirme gibi http://microsoft.com varsayılan sayfası.  
  
-   Kesme noktası ayarlama sayfası veya bu sayfa tarafından dahil başka bir dosyaya, bir ASPX denetim (ascx) dosyası değil, tarayıcı URL'sinde belirtilen sayfası ana. Kesme noktaları dahil sayfalarında ayarlamak eşlenemez.  
  
-   Kesme noktaları kümesinde `<script defer=true>` blokları eşlenemez.  
  
-   Kesme noktaları ayarlayın `<script id="">` blokları, kesme noktası eşleme yoksayar `id` özniteliği.  
  
## <a name="breakpoint-mapping-and-duplicate-lines"></a>Kesme noktası eşleme ve yinelenen satırları  
 Sunucu tarafı ve istemci tarafı komut dosyasında karşılık gelen konumu bulmak için her satırda kod kesme noktası eşleme algoritması inceler. Algoritma, her satırın benzersiz olduğunu varsayar. İki veya daha fazla satır aynı kodu içerir ve bu yinelenen satırlar birinde bir kesme noktası belirleyerek, kesme noktası eşleme algoritması istemci-tarafı dosyasında yanlış yinelenen seçebilirsiniz. Bunu önlemek için kesme burada ayarladığınız satır için bir açıklama ekleyin. Örneğin:  
  
```csharp
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```
