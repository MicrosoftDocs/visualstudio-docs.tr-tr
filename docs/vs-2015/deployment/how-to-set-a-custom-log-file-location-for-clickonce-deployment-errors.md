---
title: 'Nasıl yapılır: ClickOnce dağıtım hataları için özel günlük dosyası konumu ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e4108287e120eabb4c8fc38d1dc29f2a81ea3d47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207707"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Nasıl yapılır: ClickOnce Dağıtım Hataları için Özel Günlük Dosyası Konumu Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tüm dağıtımlar için etkinleştirme günlük dosyalarını korur. Bu günlükler yükleme ve başlatma ilgili hataları belge bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım. Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] her dağıtım etkinleştirme için tek bir günlük dosyası oluşturur. Bu, bu günlük dosyaları geçici Internet dosyaları klasöründe depolar. Bir dağıtım için günlük dosyasına bir etkinleştirme hatası oluşur ve kullanıcının'ı tıklattığında kullanıcıya görüntülenir **ayrıntıları** ortaya çıkan hata iletişim kutusunda.  
  
 Belirli bir istemci için Kayıt Defteri Düzenleyicisi'ni kullanarak bu davranışı değiştirebilirsiniz (**regedit.exe**) özel bir günlük dosyası yolunu ayarlamak için. Bu durumda, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] etkinleştirme başarı ve başarısızlık tüm dağıtımlar için tek bir dosyaya kaydeder.  
  
> [!CAUTION]
>  Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Kendi risk altında Kayıt Defteri Düzenleyicisi'ni kullanın.  
  
> [!NOTE]
>  Truncate ya da bazen çok fazla büyümesini önlemek için günlük dosyasını silmek gerekir.  
  
 Aşağıdaki yordam, tek bir istemci için özel günlük dosyası konumu ayarlama işlemi açıklanmaktadır.  
  
### <a name="to-set-a-custom-log-file-location"></a>Özel günlük dosyası konumu ayarlama  
  
1.  Açık **Regedit.exe**.  
  
2.  Düğümüne gidin `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Dize değeri ayarlamak `LogFilePath` tam yolu ve dosya adı, tercih edilen özel günlük konum.  
  
     Bu konum, kullanıcı yazma erişimi olan bir dizinde olması gerekir. Örneğin, Windows Vista, aşağıdaki klasör yapısına oluşturup `LogFilePath` C:\Users için\\< kullanıcı adı\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Sorunlarını Giderme](../deployment/troubleshooting-clickonce-deployments.md)





