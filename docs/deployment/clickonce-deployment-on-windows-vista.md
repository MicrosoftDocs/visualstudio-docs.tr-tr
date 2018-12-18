---
title: Windows Vista'da ClickOnce dağıtımı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0389665349ae9c39a0f820bc047af6cc4db2b683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867539"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista'da ClickOnce dağıtımı

Visual Studio'da uygulamaları oluşturma, Windows Vista kullanıcı hesabı denetimi (UAC) normalde gömülü bir bildirim üretir uygulamanın yürütülebilir dosyasına ikili olarak XML verilerinde kodlanmış.  ClickOnce ve Registration-Free COM uygulamaları dış bildiriminde gerektirdiğinden, Visual Studio bu projelerin bir gömülü bildirimi yerine UAC verileri içeren bir dosya oluşturur. ClickOnce ve Registration-Free COM dağıtımları için Visual Studio bilgileri adlı bir dosyadan kullanır *app.manifest* dış UAC bildirim bilgilerini oluşturmak için. Diğer tüm durumlarda için Visual Studio UAC veri uygulamanın yürütülebilir dosyasına katıştırır. 

Visual Studio, bildirim oluşturmak üzere aşağıdaki seçenekleri sağlar:  
  
- Gömülü bir bildirim kullanın. UAC veri uygulamanın yürütülebilir dosyasına katıştırma ve normal bir kullanıcı olarak çalıştırın.  
  
   (ClickOnce kullanmadığınız sürece) varsayılan ayar budur. Bu ayar, Visual Studio çalıştığı her zamanki şekilde Windows Vista'da destekler, hem iç hem de dış nesil kullanarak bildirim `AsInvoker`.  
  
- Harici bildirim kullanın. Harici bir bildirim oluşturmak *app.manifest*.  
  
   Bu bilgileri kullanarak yalnızca dış bildirimi oluşturur *app.manifest*. ClickOnce veya Registration-Free COM kullanılarak bir uygulama yayımladığınızda, Visual Studio ekler *app.manifest* projeye sağ tıklatın ve ardından bu seçeneği ekler.  
  
- Hiçbir bildirim kullanın. Bir bildirim olmadan uygulamayı oluşturun.  
  
   Bu yaklaşım olarak da bilinir, *sanallaştırma*. Visual Studio'nun önceki sürümlerindeki mevcut uygulamalarla uyumluluk için bu seçeneği kullanın.  
  
  Yeni özellikler kullanılabilir **uygulama** sayfası Proje Tasarımcısı (Visual C# projeleri yalnızca için) ve MSBuild proje dosyası biçimi.  
  
  Visual Studio IDE içinde UAC bildirim üretme yapılandırma yöntemi proje türü (Visual C# veya Visual Basic) bağlı olarak farklılık gösterir.  
  
  * Bildirim oluşturmak üzere Visual C# projelerini yapılandırma hakkında daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  * Visual Basic projeleri için bildirim oluşturma yapılandırma hakkında daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Kullanıcı izinleri ve Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)