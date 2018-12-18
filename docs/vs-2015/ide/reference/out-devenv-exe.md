---
title: -Out (devenv.exe) | Microsoft Docs
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
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cbf9608bc4f476599676b27f12bc125fd170fc71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211009"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Depolama ve çalıştırma, derleme, yeniden oluşturun veya bir çözüm dağıtma hataları görüntülemek için dosyayı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Arguments  
 `FileName`  
 Gerekli. Bir yürütülebilir dosya oluştururken hatalar almak için dosyanın adı ve yolu.  
  
## <a name="remarks"></a>Açıklamalar  
 Dosya, var olmayan bir dosya adı belirtilirse, otomatik olarak oluşturulur. Dosya zaten varsa, dosyanın mevcut içeriğini için sonuçları eklenir.  
  
 Komut satırı derleme hataları görüntülenir **komut** penceresi ve çözüm Oluşturucusu'nu görüntülemek **çıkış** penceresi. Bu seçenek, katılımsız yapılar çalıştırıyorsanız ve sonuçları görmek gereken yararlıdır.  
  
## <a name="example"></a>Örnek  
 Bu örnek çalıştırılır `MySolution` ve hataları Yazar `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)   
 [/ Çalıştırma (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/ Derleme (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ (Devenv.exe) dağıtma](../../ide/reference/deploy-devenv-exe.md)



