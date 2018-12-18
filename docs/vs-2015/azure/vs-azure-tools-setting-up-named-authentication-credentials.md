---
title: Adlandırılmış bir kimlik doğrulama kimlik bilgilerini ayarla | Microsoft Docs
description: Visual Studio, Visual Studio'dan azure'a uygulama yayımlama ya da mevcut bir bulut hizmetini izlemeyi azure'a isteklerinin kimliğini doğrulamak için kullanabileceğiniz kimlik bilgilerini sağlamanız öğrenin.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 6f41ea2072ef5791735fac61205f68151d5a9f7e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003698"
---
# <a name="set-up-named-authentication-credentials"></a>Adlandırılmış kimlik doğrulama bilgilerini ayarlama

Bir uygulamayı azure'a yayımlayacaksınız veya mevcut bir bulut hizmeti izlemek için Visual Studio isteklerinin Azure, Azure abonelik Kimliğinizi ve en az 2048 bit anahtar ile geçerli bir X.509 v3 sertifikası kimlik doğrulaması için kimlik bilgilerini gerektirir. Aşağıdaki yöntemlerden birini kullanarak bu kimlik bilgileri sağlayın:

- Visual Studio seçin **Görüntüle > Sunucu Gezgini**, sağ **Azure** düğümünü **Microsoft Azure aboneliğine bağlanma**ve oturum açın.
- Bir abonelik dosyası oluşturun (`.publishsettings`), bir sertifikanın ortak anahtarı içerir. Bu makalede açıklandığı gibi abonelik dosyası birden fazla aboneliğiniz için kimlik bilgileri içerebilir.

Not: Bu kimlik bilgileri Azure depolama hizmetlerine isteklerinin kimliğini doğrulamak için kullanılan kimlik bilgileri farklıdır.

## <a name="create-a-subscription-file"></a>Bir abonelik dosyası oluşturma

Sunucu Gezgini'nde sağ **Azure** düğümünü seçip alt **yönetin ve filtre abonelikleri**. Ardından **sertifikaları** sekmesine ve ardından aşağıdaki işlemlerden birini yapın:

- Seçin **alma** açmak için **alma Microsoft Azure abonelikleri** iletişim kutusu. Seçin **indirme abonelik dosyası** bağlantısını ve tarayıcıda indirilen dosyayı geçici bir konuma kaydedin. Geri iletişim kutusunda, indirme konumuna gidin ve kimlik doğrulaması kullanmak için alma.
- Etkin bir aboneliğiniz seçip **Düzenle**, kimlik doğrulaması kullanmak için mevcut bir aboneliği Düzenle iletişim kutusu açılır.
- Seçin **yeni** açmak için **yeni abonelik** iletişim kutusu ve gerekli ayrıntıları sağlar. Bulut için sertifikayı karşıya yüklemek için hizmet belirtilmiştir iletişim kutusunda, Azure portalında oturum açın, bulut hizmetinize, select gidin **Ayarları > Yönetim sertifikaları**seçin **karşıya**, ardından yolunu belirtin `.cer` dosya.

Kendiniz bir sertifika oluşturmak istiyorsanız, yönergeleri başvurabilirsiniz [oluşturma ve karşıya yükleme için Azure yönetim sertifikası](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) ve sertifikayı el ile karşıya [Azure portalında](https://portal.azure.com/).

## <a name="next-steps"></a>Sonraki adımlar

- [Web Apps'e genel bakış](https://docs.microsoft.com/azure/app-service/)
- [Uygulamanızı Azure App Service'e dağıtma](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Visual Studio kullanarak webjob'ları dağıtma](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Bir bulut hizmeti oluşturma ve dağıtma](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)