---
title: Kaynak denetimi eklentileri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4be7a1d0739b6a0c8431d588b05de58a296b809c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495706"
---
# <a name="source-control-plug-ins"></a>Kaynak Denetimi Eklentileri
Kaynak Denetimi Eklentisi SDK başvuru bölümüne ile tümleşik kaynak denetimi sistemlerini sağlayan eksiksiz arabirim belirtimi içeren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sözdizimi ve semantiği ile arabirim oluşturmak için kaynak denetimi eklentisi uygulamalıdır çeşitli işlevleri ve veri türlerini belirtir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)  
 Kaynak Denetimi Eklentisi API ile uyum sağlamak için kaynak denetimi eklentisi tarafından uygulanması gereken işlevleri listeler.  
  
 [IDE Tarafından Uygulanan Geri Çağırma İşlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Bazı komut yürütülürken IDE bilgi geçirmek için kaynak denetimi eklentisi kullanan işlevler açıklanmaktadır.  
  
 [Numaralandırıcılar](../extensibility/enumerators.md)  
 Kaynak Denetimi Eklentisi hakkında bilmeniz gereken kaynak denetimi eklentisi API Numaralandırıcı veri türlerini listeler.  
  
 [Özellik Bayrakları](../extensibility/capability-flags.md)  
 Açıklar `SCC_CAP_xxx` bir sağlayıcının özelliklerini gösteren bayrak.  
  
 [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)  
 Belirli komutları bağlamında yararlıdır bayrakları listeler.  
  
 [Hata Kodları](../extensibility/error-codes.md)  
 İşlevleri tarafından döndürülen genel hata değerlerini listeler `SCCTRN`.  
  
 [Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Kaynak denetimi eklentisi bulmak için kayıt defteri erişim tuşları açıklanmaktadır.  
  
 [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)  
 IDE için donuk bilgileri içeren, ancak sürüm denetimi içinde çözüm veya projeyi bulmak için kaynak denetimi eklentisi tarafından kullanılan bir istemci-tarafı dosya açıklar.  
  
 [Kaynak Denetimi Eklentisi Uygulamak için En İyi Yöntemler](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Kaynak Denetimi Eklentisi API uyguladığınız sırada hatırlamak önemli teknik anımsatıcılar sağlar.  
  
 [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)  
 Kaynak Denetimi Eklentisi API sınırlamaları çeşitli işlevler için kullanılan dizelerin uzunluklarının açıklar.  
  
 [Sözlük](../extensibility/source-control-plug-in-glossary.md)  
 Yararlı hüküm ve kaynak denetimi eklentisi SDK belgeleri okumak için tanımlarını sağlar.  
  
 [Nasıl Yapılır: Kaynak Denetimi Eklentileri için Uyumluluk Uyarılarını Kapatma](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Uyarıları devre dışı bırakma açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kaynak Denetimi Eklentisi örneği](https://www.microsoft.com/download/details.aspx?id=55984)  
 Kaynak Denetimi Eklentisi işlevlerini bir örnek sağlar.  
  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Kaynak denetimi eklentisi ile ilgili sınama yordamları açıklar.  
  
 [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Kaynak denetimi işlevlerini kullanırken sağlayan bir kaynak denetimi eklentisi oluşturma anlatılmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kaynak denetimi kullanıcı arabirimini (UI).  
  
 [Visual Studio SDK Başvurusu](../extensibility/visual-studio-sdk-reference.md)  
 Başvuru konuları bir listesini sunar.