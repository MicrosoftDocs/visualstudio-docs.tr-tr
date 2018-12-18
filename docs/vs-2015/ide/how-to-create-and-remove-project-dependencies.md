---
title: 'Nasıl yapılır: Proje bağımlılıklarını oluşturma ve kaldırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cc63ef7159b0f11b3d170e0b4123f337ba413d65
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823846"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Nasıl Yapılır: Proje Bağımlılıklarını Oluşturma ve Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden çok proje içeren bir çözüm derlerken, belirli projeleri ilk oluşturulacak, diğer projeleri tarafından kullanılan kodu oluşturmak için gerekli olabilir. Bir proje başka bir proje tarafından oluşturulan yürütülebilir kodu kullanırken, kodu oluşturan proje kodu kullanan projenin proje bağımlılık olarak adlandırılır. Bu bağımlılık ilişkiler tanımlanabilir **proje bağımlılıkları** iletişim kutusu.  
  
### <a name="to-assign-dependencies-to-projects"></a>Bağımlılıkları projelerine atamak için  
  
1. Çözüm Gezgini'nde bir proje seçin.  
  
2. Üzerinde **proje** menüsünde seçin **proje bağımlılıkları**.  
  
    **Proje bağımlılıkları** iletişim kutusu açılır.  
  
   > [!NOTE]
   >  **Proje bağımlılıkları** seçeneği, yalnızca kullanılabilir birden fazla proje içeren bir çözümde.  
  
3. Üzerinde **bağımlılıkları** sekmesinde, bir proje seçin **proje** açılan menüsü.  
  
4. İçinde **bağlıdır** alanında, bu proje önce oluşturmanız gerekir, başka bir projeye ait onay kutusunu seçin.  
  
   Proje bağımlılıkları oluşturmadan önce çözümünüzü birden fazla proje oluşmalıdır.  
  
### <a name="to-remove-dependencies-from-projects"></a>Proje bağımlılıkları kaldırmak için  
  
1.  Çözüm Gezgini'nde bir proje seçin.  
  
2.  Üzerinde **proje** menüsünde seçin **proje bağımlılıkları**.  
  
     **Proje bağımlılıkları** iletişim kutusu açılır.  
  
    > [!NOTE]
    >  **Proje bağımlılıkları** seçeneği, yalnızca kullanılabilir birden fazla proje içeren bir çözümde.  
  
3.  Üzerinde **bağımlılıkları** sekmesinde, bir proje seçin **proje** açılan menüsü.  
  
4.  İçinde **bağlıdır** alan, bu projenin bağımlılıklarıdır artık herhangi bir projeyi yanındaki onay kutularını temizleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Projeleri ve Visual Studio çözümleri oluşturma ve temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)   
 [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)   
 [NIB nasıl yapılır: Proje özelliklerini ve yapılandırma ayarlarını değiştirme](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)



