---
title: Yalıtılmış kabuk uygulamaları dağıtma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27228131c1e955a394e666ac05f0ddd68c879be0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758785"
---
# <a name="distributing-isolated-shell-applications"></a>Yalıtılmış kabuk uygulamaları dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalıtılmış Kabuk uygulaması oluşturmak için Visual Studio ve Visual Studio SDK'yı yüklemeniz gerekir. Diğer kullanıcıları veya müşterileri makinelere uygulamayı dağıtmak için yalıtılmış Kabuk için özel bir yeniden dağıtılabilir paketini içermelidir.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Yalıtılmış kabuk uygulamaları dağıtmak için Önkoşullar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|Visual Studio SDK|Geliştirme ve test uzantıları için SDK'sı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. SDK, Visual Studio yalıtılmış Kabuğu kendi örneğini oluşturmak için de kullanabilirsiniz.<br /><br /> Visual Studio SDK'sı için önkoşuldur.|  
|Microsoft Visual Studio yalıtılmış Kabuğu yeniden dağıtılabilir|Yeniden dağıtılabilir Visual Studio bir araç ortamınızı oluşturduğunuzda, Kurulum programınıza ekleyin yalıtılmış Kabuk. Yalıtılmış Kabuk yeniden dağıtılabilir paket, .NET Framework 4.5 içerir.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Uygulama için bir yükleme programı oluşturma  
 Bir özel yükleme programı için tümleşik veya yalıtılmış Kabuk uygulaması oluşturmanız gerekir. Daha fazla bilgi için [bir yalıtılmış Kabuk Uygulaması Yükleme](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Uygulama güncelleştirmeleri için izin verme  
 Uygulamanızı, Microsoft Güncelleştirmeleri veya şirketinizin güncelleştirmeleri güncelleştirileceğini olasılığını için yükleme programınızı izin vermeniz gerekir. Güncelleştirmeleri hakkında daha fazla bilgi için bkz. [yalıtılmış kabuk uygulamaları için hizmet verme yönergeleri](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

