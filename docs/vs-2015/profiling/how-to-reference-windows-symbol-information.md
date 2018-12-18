---
title: 'Nasıl yapılır: başvuru Windows sembol bilgilerini | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c18825a27bfefdd1a6c817951983d85ac459b78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763586"
---
# <a name="how-to-reference-windows-symbol-information"></a>Nasıl yapılır: Başvuru Pencereleri Sembol Bilgileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio profil oluşturma araçları, işlev adlarını program ikili dosyalar gibi sembolik adlarını çözümlemek için Sembol (.pdb) dosyalarını kullanın. Otomatik olarak yükle ve yerel bilgisayardaki Windows sürümü için doğru .pdb dosyaları güncelleştirmek için aşağıdaki adımları izleyebilirsiniz.  
  
> [!NOTE]
>  Bu ayar, var olan raporların etkilemez. Sembol sunucusu belirttikten sonra oluşturulan raporlar sembol bilgilerini sahip olur.  
  
 Daha fazla bilgi için [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft sembol sunucusu kullanmak için  
  
1.  C:\SymbolCache gibi sembol dosyası bilgilerini içeren bir klasör oluşturun.  
  
2.  Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
     **Seçenekleri** iletişim kutusu görüntülenir.  
  
3.  Genişletin **hata ayıklama** ağaç ve ardından **sembolleri**.  
  
4.  İçinde **sembol dosyası (.pdb) konumlar**seçin **Microsoft sembol sunucuları**  
  
5.  İçinde **semboller sembol sunucusundan bu dizine önbelleğe**, örneğin, 1. adımda oluşturduğunuz klasör yolunu yazın:  
  
     **C:\SymbolCache**  
  
     Üç nokta düğmesine de tıklayabilirsiniz (**...** ) seçip bir dizinden **klasöre Gözat** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl Yapılır: Sembol Bilgilerini Seri Hale Getirme](../profiling/how-to-serialize-symbol-information.md)



