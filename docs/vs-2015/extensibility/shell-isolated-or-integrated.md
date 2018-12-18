---
title: Shell (yalıtılmış veya tümleşik) | Microsoft Docs
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
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 856e32d4569e5dcb73e783d0a6b66e186fbb1848
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755876"
---
# <a name="shell-isolated-or-integrated"></a>Shell (yalıtılmış veya tümleşik)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tümleşik veya yalıtılmış modda, kendi Visual Studio tabanlı bir uygulama oluşturabilirsiniz. Tümleşik modda, uygulamanıza ek olarak birçok Visual Studio özelliği kullanılabilir. Yalıtılmış modda, dağıtmak için kendi uzantınızla birlikte Visual Studio özelliklerinin bir alt kümesi seçin.  
  
## <a name="integrated-mode"></a>Tümleşik modu  
 Tümleşik modu, kullanıcılarınızın özel araçlarınız ile birlikte standart bir Visual Studio özelliklerini kullanmayı sağlar. Yazılım geliştirme araçları ve programlama dilleri öncelikle barındırma tümleştirilmiş Kabuk yöneliktir.  
  
 Herhangi bir sürümünü aynı bilgisayara yüklü Visual Studio ile tümleştirilmiş Kabuk otomatik olarak oluşturulan özel araçlar birleştirin. Visual Studio zaten yüklü değilse, Visual Studio tümleşik Kabuk yeniden dağıtılabilir sürümü sağlayabilirsiniz.  
  
 Visual Studio tümleşik Kabuk yeniden dağıtılabilir sürümünü programlama dilleri ve ilgili proje sistemlerini destekleyen özellikleri içermez.  
  
> [!NOTE]
>  Visual Studio shell tümleşik modu, Visual Studio Express sürümleri hariç tüm sürümleri ile birlikte yüklenebilir.  
  
 Daha fazla bilgi için [Visual Studio Kabuğu (tümleşik)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Yalıtılmış modu  
 Yalıtılmış modda, yan yana çalıştırma özel araçlar oluşturmanıza olanak tanır, Visual Studio'nun diğer sürümleriyle birlikte. Öncelikle standart tüm Visual Studio özelliklere bağlı olarak Visual Studio hizmetler olmadan erişebileceği araçları için tasarlanmıştır. Visual Studio yalıtılmış Kabuğu oluşturulan uygulamalar görünümünü özelleştirebilirsiniz. Kolayca, görüntülenecek birlikte uygulamanızı istemediğiniz menü komut gruplarını ve özellikleri devre dışı bırakabilirsiniz.  
  
 Daha fazla bilgi için [Visual Studio yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Tümleşik veya yalıtılmış Kabuk uygulaması dağıtma  
 Tümleşik veya yalıtılmış Kabuk uygulamanızı dağıtmak için uygulamanız, bir özel tümleşik veya yalıtılmış Kabuk yeniden dağıtılabilir ve bir yükleme programı eklemeniz gerekir. Dağıtım ve yükleme hakkında daha fazla bilgi için bkz: [yalıtılmış kabuk uygulamaları dağıtma](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  [Son kullanıcı lisans sözleşmesi (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) Kabukları Visual Studio tümleşik ve yalıtılmış bir bölüm veri toplamayı içerir (**bölüm 3. Veri**).  Bu, kullanıcıların uygulamanıza yapı tümleşik veya yalıtılmış Kabuk yazılım ya da Microsoft tarafından toplanabilir müşteri kullanım verilerini açıklar. Daha fazla bilgi için [Microsoft Visual Studio ürün ailesi gizlilik bildirimi](https://www.visualstudio.com/en-us/dn948229).  
> 
>  Uygulamanızı müşterilerinizin ayrı kullanım verilerini toplamak, uygun dikkat edin, Topla, uygulamanızın kullanıcılara sağlamanız gerekir.  Visual Studio Yazılım Geliştirme Seti lisans göre uygulamanızın bir parçası olarak yalıtılmış veya tümleşik Kabuk yazılım dağıttığınızda aşağıdakilerden birini içermelidir:  
> 
> - Uygulama lisansı bir parçası olarak son kullanıcı lisans sözleşmesi  
>   -   Visual Studio koruyan koşulları kabul etmeniz müşterilerinizin gerektiren kendi EULA'yı tümleşik veya kabuk yazılım için Microsoft son kullanıcı lisans koşullarını olarak yalıtılmış Kabuk en azından  
  
## <a name="additional-resources"></a>Ek Kaynaklar  
 Yeniden dağıtılabilir paketleri hakkında daha fazla bilgi için bkz: [Visual Studio genişletilebilirlik indirmeleri](http://go.microsoft.com/fwlink/?LinkID=119298) Web sitesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)

