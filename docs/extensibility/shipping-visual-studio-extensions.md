---
title: Visual Studio uzantıları sevkiyat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c646ec2c5159e6c3551776761baa9328e3d62bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142766"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio uzantıları aktarma
Uzantınızı geliştirme bitirdikten sonra diğer makinelere yüklemeniz, arkadaşlarınız ve iş arkadaşlarınızla paylaşın veya Visual Studio Market'te yayımlayın. Bu bölümde biz yayımlama ve uzantınızı korumak için yapmanız gereken her şey açıklamaktadır: yayımlama, yerelleştirme ve güncelleştirme .vsix dosyalarıyla çalışma.  
  
## <a name="working-with-vsix-extensions"></a>VSIX uzantıları ile çalışma  
 Boş bir VSIX proje oluşturma ve farklı öğe şablonları ekleyerek VSIX uzantıları oluşturabilirsiniz. Daha fazla bilgi için bkz: [VSIX proje şablonu](../extensibility/vsix-project-template.md).  
  
 Proje şablonları paketini, şablonları, VSPackages, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenleri, öğe için VSIX biçimini kullanabilirsiniz **araç** denetimleri, derlemeler ve özel türler (buna dahildir özel başlangıç sayfaları). VSIX biçimi dosya tabanlı dağıtım kullanır. VSIX paketler hakkında daha fazla bilgi için bkz: [VSIX paketi anatomisi](../extensibility/anatomy-of-a-vsix-package.md).  
  
 VSIX biçimi kod parçacıkları yüklenmesini desteklemez. Genel Derleme Önbelleği (GAC) için veya sistem kayıt defterine yazılıyor gibi diğer bazı senaryolar da desteklemez. GAC veya yükleme kayıt defterinde yazmak gerekiyorsa, Windows Installer kullanmanız gerekir. Daha fazla bilgi için bkz: [hazırlama uzantıları için Windows Installer dağıtımı](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Visual Studio Market'te uzantınızı yayımlama  
 Yalnızca .vsix dosyasını posta ya da bir sunucu üzerinde koymaya tarafından uzantınızı diğer kişilere dağıtabilirsiniz. Ancak, kodunuzu çok kişilerin eline en iyi yolu, koymak için [Visual Studio Market'te](https://marketplace.visualstudio.com/vs). Visual Studio Market'te uzantıları aracılığıyla Visual Studio kullanıcılara kullanılabilir **Uzantılar ve güncelleştirmeler**. Daha fazla bilgi için bkz: [bulma ve Visual Studio uzantılarını kullanarak](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Bir uzantıyı Visual Studio Market'te yüklemeyi gösteren bir tam örnek için bkz: [izlenecek yol: Visual Studio uzantısı yayımlama](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Özel galerileri  
 Denetimleri, şablonlar ve Araçlar geliştirdikçe intranetinizdeki özel bir Galeriye göndererek bunları kuruluşunuz ile paylaşabilirsiniz. Daha fazla bilgi için bkz: [özel galerileri](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Uzantınızı yerelleştirme  
 Farklı yerel ayarlara uzantı yayımlamayı planlıyorsanız, bu yerelleştirme düşünmelisiniz. Ne ilgili açıklama için bkz: [yerelleştirme VSIX paket](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Güncelleştirme ve sürüm oluşturma uzantınızı  
 Uzantınızı yayımladıktan sonra var. gelen güncelleştirmek için gerektiğinde bir süre. Visual Studio Market'te yayımlanan uzantı güncelleştirmek nasıl öğrenmek için bkz: [nasıl yapılır: uzantı güncelleştirme](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Uzantınızın Visual Studio birden fazla sürümünü destekleyecek şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz: [Visual Studio, birden çok sürümleri destekleyen](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[VSIX Proje Şablonunu Kullanmaya Başlama](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX proje şablonu özel Proje şablonu yüklemek için nasıl kullanılacağını açıklar.|  
|[Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)|VSIX paketi bileşenlerini açıklar.|  
|[VSIX Proje Şablonu](../extensibility/vsix-project-template.md)|Paket ve uzantı yayımlama hakkında adım adım yönergeler sağlar.|  
|[VSIX Paketlerini Yerelleştirme](../extensibility/localizing-vsix-packages.md)|Yerelleştirilmiş metin extension.vsixlangpack dosyalarını kullanarak yükleme işlemini sağlamayı açıklar.|  
|[Nasıl yapılır: uzantı güncelleştir](../extensibility/how-to-update-a-visual-studio-extension.md)|Uzantı sisteminizdeki güncelleştirmek ve varolan bir Visual Studio uzantısı bir güncelleştirme dağıtın açıklar.|  
|[Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX dağıtım Paketlerine yönelik başvuruları eklemeyi açıklar.|  
|[Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Uzantınızı Windows Installer ile dağıtmak açıklanmaktadır.|  
|[VSIX Paketlerini İmzalama](../extensibility/signing-vsix-packages.md)|VSIX paket oturum açıklanmaktadır.|  
|[Özel Galeriler](../extensibility/private-galleries.md)|Uzantıları için özel galerileri oluşturma açıklanmaktadır.|  
|[Visual Studio'nun Birden Çok Sürümünü Destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Uzantı desteğine sahip birden fazla sürümünü Visual Studio gösterilmektedir.|
|[Visual Studio'yu Bulma](locating-visual-studio.md)|Özel uzantı dağıtımı için Visual Studio örneklerini bulmak açıklar.|
