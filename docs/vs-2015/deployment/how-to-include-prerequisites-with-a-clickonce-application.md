---
title: 'Nasıl yapılır: ClickOnce uygulamasına Önkoşullar dahil etme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1a58e305b1214a6b8d710ef08126d241f381a051
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212205"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulamasına Önkoşullar Dahil Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Önkoşul yazılımı dağıtmadan önce bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması gerekir indirmeniz olan yükleme paketlerini geliştirme bilgisayarınıza bu Önkoşullar. Ne zaman bir uygulamayı yayımlamak ve seçin **Uygulamamla aynı konumdan önkoşulları karşıdan**, eğer yükleyici paketleri olmayan bir hata meydana gelir **paketleri** klasör.  
  
> [!NOTE]
>  .NET Framework için bir yükleyici paket eklemek için bkz [geliştiriciler için .NET Framework Dağıtım Kılavuzu](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> Package.xml kullanarak bir yükleyici paket eklemek için  
  
1.  Dosya Gezgini'nde Aç **paketleri** klasör.  
  
     Varsayılan olarak, C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages 32-bit sistem üzerinde ve C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages 64-bit sistemde yoludur.  
  
2.  Eklemek istediğiniz ön koşul için klasörü açın ve ardından'ın yüklü sürümü için dil klasörü açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (örneğin, **tr** İngilizce).  
  
3.  Not Defteri'nde açın **Package.xml** dosya.  
  
4.  Bulun **adı** öğesini içeren **http://go.microsoft.com/fwlink**ve URL'yi kopyalayın. Dahil **LinkId** bölümü.  
  
    > [!NOTE]
    >  Hayır ise **adı** ögesinin **http://go.microsoft.com/fwlink**açın **Product.xml** bulun ve ön koşul için kök klasöründeki dosya **fwlink** dize.  
  
    > [!IMPORTANT]
    >  Bazı ön koşullar (örneğin, 32-bit veya 64-bit sistemler için) birden çok yükleme paketine sahiptirler. Birden çok **adı** öğeleri içeren **fwlink**, bunların her biri için kalan adımları yinelemeniz gerekir.  
  
5.  Tarayıcınızın adres çubuğuna URL'yi yapıştırın ve ardından, çalıştırmanız veya kaydetmeniz istendiğinde **Kaydet**.  
  
     Bu adım, yükleyici dosyasını bilgisayarınıza yükler.  
  
6.  Dosyayı ön koşul için kök klasörüne kopyalayın.  
  
     Örneğin, Windows Installer 4.5 ön koşulları için dosyayı \Packages\WindowsInstaller4_5 klasörüne kopyalayın.  
  
     Şimdi, yükleyici paketi uygulamanız ile dağıtabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)



