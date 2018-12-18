---
title: 'Nasıl yapılır: ClickOnce dağıtım hataları için özel günlük dosyası konumu ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab6d1e1fe21d8da667963f9b54db23f303e6aee7
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079180"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Nasıl yapılır: ClickOnce dağıtım hataları için özel günlük dosyası konumu ayarlama
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm dağıtımlar için etkinleştirme günlük dosyalarını korur. Bu günlükler yükleme ve başlatma ilgili hataları belge bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım. Varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] her dağıtım etkinleştirme için tek bir günlük dosyası oluşturur. Bu, bu günlük dosyaları geçici Internet dosyaları klasöründe depolar. Bir dağıtım için günlük dosyasına bir etkinleştirme hatası oluşur ve kullanıcının'ı tıklattığında kullanıcıya görüntülenir **ayrıntıları** ortaya çıkan hata iletişim kutusunda.  
  
 Belirli bir istemci için Kayıt Defteri Düzenleyicisi'ni kullanarak bu davranışı değiştirebilirsiniz (**regedit.exe**) özel bir günlük dosyası yolunu ayarlamak için. Bu durumda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] etkinleştirme başarı ve başarısızlık tüm dağıtımlar için tek bir dosyaya kaydeder.  
  
> [!CAUTION]
>  Kayıt Defteri Düzenleyicisi'ni yanlış kullanırsanız, işletim sistemini yeniden yüklemenizi gerektirebilecek önemli sorunlara neden olabilir. Kendi risk altında Kayıt Defteri Düzenleyicisi'ni kullanın.  
  
> [!NOTE]
>  Truncate ya da bazen çok fazla büyümesini önlemek için günlük dosyasını silmek gerekir.  
  
 Aşağıdaki yordam, tek bir istemci için özel günlük dosyası konumu ayarlama işlemi açıklanmaktadır.  
  
### <a name="to-set-a-custom-log-file-location"></a>Özel günlük dosyası konumu ayarlama  
  
1.  Açık **Regedit.exe**.  
  
2.  Düğümüne gidin `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Dize değeri ayarlamak `LogFilePath` tam yolu ve dosya adı, tercih edilen özel günlük konum.  
  
     Bu konum, kullanıcı yazma erişimi olan bir dizinde olması gerekir. Örneğin, Windows Vista, aşağıdaki klasör yapısına oluşturup `LogFilePath` için *C:\Users\\\<kullanıcıadı > \Documents\Logs\ClickOnce\installation.log*.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)