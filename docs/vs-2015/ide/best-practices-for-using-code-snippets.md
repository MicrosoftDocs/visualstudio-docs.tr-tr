---
title: Kod parçacıkları için en iyi uygulamalar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1dad7bd7ccddf3645abb11dc55afcdf2e7cce7ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919916"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod Parçacıkları İçin En İyi Uygulamalar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacığı kodda bir şey yalnızca en basit yol gösterir. Çoğu uygulama için kod uygulaması uyacak şekilde değiştirilmesi gerekir.  
  
## <a name="handling-exceptions"></a>Özel Durumları İşleme  
 Genellikle, kod parçacığı deneyin... Catch blokları catch ve tüm özel durumları rethrow. Bu, projeniz için doğru seçim olmayabilir. Her özel durum için yanıt birkaç yolu vardır. Örnekler için bkz [nasıl yapılır: bir özel durum try/catch kullanarak (C# programlama Kılavuzu) işleme](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) ve [deneyin... Catch... Finally deyimini](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).  
  
## <a name="file-locations"></a>Dosya konumları  
 Dosya konumları uygulamanıza uyum, aşağıdakiler hakkında düşünün:  
  
-   Erişilebilir bir konumda bulunuyor. Uygulama dosyaları ile dosyaları depolama çalışmayabilir şekilde kullanıcılar bilgisayar, Program dosyaları klasörüne erişimi olmayabilir.  
  
-   Güvenli bir konumda bulunuyor. Dosya depolama kök klasöründe (C:\\) güvenli değildir. Uygulama verileri için \Application veri klasörü öneririz. Bireysel kullanıcı verileri için uygulama \My Belgeler klasöründe her kullanıcı için bir dosya oluşturabilirsiniz.  
  
-   Geçerli bir dosya adı kullanıyor. Kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> geçersiz dosya adları olasılığını azaltmak için denetimleri. Bir dosya kullanıcının seçtiği zaman ve kodunuzu dosyasını yöneten zaman arasında dosya silinebilir dikkat edin. Ayrıca, kullanıcı dosyaya yazmak için gerekli izinlere sahip.  
  
## <a name="security"></a>Güvenlik  
 Nasıl bir kod parçacığı güvenlidir, kaynak kodunda kullanıldığı ve kodda olduğunda nasıl değiştirilir bağlıdır. Aşağıdaki liste, dikkate alınması gereken alanların birkaçını içerir.  
  
- Dosya ve veritabanı erişimi  
  
- Kod erişimi güvenliği  
  
- Kaynakları koruma (olay günlükleri, kayıt defteri)  
  
- Gizli dizileri depolama  
  
- Giriş doğrulanıyor  
  
- Komut dosyası teknolojileri için veri geçirme  
  
  Daha fazla bilgi için [uygulamaları güvenli hale getirme](../ide/securing-applications.md).  
  
## <a name="downloaded-code-snippets"></a>İndirilen kod parçacıkları  
 Visual Studio tarafından yüklenmiş IntelliSense kod parçacıkları kendisi içinde bir tehlike değildir. Ancak, bunlar uygulamanızda güvenlik risklerini oluşturabilirsiniz. Internet'ten indirilen kod parçacıkları gibi diğer tüm indirilen içeriği - işlemini çok dikkatli olunmalıdır.  
  
-   Yalnızca güvendiğiniz sitelerden parçacıkları indirir ve güncel virüsten yazılımı kullanın.  
  
-   Tüm indirilen kod parçacığı dosyaları Not Defteri veya Visual Studio XML düzenleyicisinde açın ve yüklemeden önce dikkatle gözden geçirin. Aşağıdaki sorunları arayın:  
  
    -   Bunu, kod parçacığı sisteminize zarar verebilir. Kaynak kodu çalıştırmadan önce dikkatle okuyun.  
  
    -   Kod parçacığı dosyasını Yardım URL'si bloğunu bir kötü amaçlı bir komut dosyası yürütme veya rahatsız edici bir Web sitesinin URL'leri içerebilir.  
  
    -   Kod parçacığı sessizce projenize eklenir ve herhangi bir yere sisteminize yüklenebilir başvuruları içerebilir. Bu başvurular bilgisayarınıza kod parçacığını indirdiğiniz gelen indirilmiş olabilir. Kod parçacığı, ardından kötü amaçlı kod yürüten başvurusunda bir yönteme bir çağrı yapabilir. Tür bir saldırıya karşı korunmak için kod parçacığı dosyasını içeri aktarmalar ve başvurular bloklarını gözden geçirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic IntelliSense kod parçacıkları](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)   
 [Uygulamalarının güvenliğini sağlama](../ide/securing-applications.md)   
 [Kod Parçacıkları](../ide/code-snippets.md)



