---
title: Python uygulamasını Azure App Service'e yayımlama
description: Linux ve IIS'ye dağıtma yayımlama Git dahil olmak üzere Azure App Service'e bir Python uygulaması dağıtın ve kapsayıcıları için seçenekleri.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 1c8c48eaa777da973f0a4b21d826bbab384b4536
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066697"
---
# <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Şu anda Python için Linux üzerinde Azure App Service'te desteklenir ve kullanan uygulamalar yayımlayabilmeniz için [Git dağıtma](#publish-to-app-service-on-linux-using-git-deploy) ve [kapsayıcıları](#publish-to-app-service-on-linux-using-containers)bu makalede açıklandığı gibi.

> [!Note]
> Windows için Azure App Service'te Python desteği resmi olarak kullanım dışı bırakılmıştır. Sonuç olarak, **Yayımla** Visual Studio'da komutu yalnızca desteklenen resmi bir [IIS hedef](#publish-to-iis), ve Azure App Service'te uzaktan hata ayıklama artık resmi olarak desteklenir.
>
> Ancak, [Windows üzerinde App Service'e yayımlama](publish-to-app-service-windows.md) özellikleri çalışmaya devam ettiğinden şimdilik, Windows üzerinde App Service'e Python uzantıları kalması gibi kullanılabilir ancak değil hizmet veya kaldırılacak güncelleştirildi.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Yayımlama Linux üzerinde App Service'e Git kullanarak dağıtma

Git dağıtımı belirli bir dala bir Git deposu için bir Linux üzerinde App Service'e bağlanır. Kodun bu dala otomatik olarak yapılıyor, App Service'e dağıtır ve App Service otomatik olarak listelenen bağımlılıkları yükler *requirements.txt*. Bu durumda, Linux üzerinde App Service'te Gunicorn web sunucusunu kullanan önceden yapılandırılmış bir kapsayıcı görüntüsü kodunuz çalışır. Bu hizmet, şu an Önizleme aşamasındadır ve üretim sırasında kullanım için desteklenmez.

Daha fazla bilgi için Azure belgelerinde aşağıdaki makalelere bakın:

- [Hızlı Başlangıç: App Service'te bir Python web uygulaması oluşturma](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) kısa sağlar git'in izlenecek yol basit bir Flask uygulaması ve dağıtım, yerel bir Git deposundan kullanarak işlem dağıtın.
- [Python yapılandırma](/azure/app-service/containers/how-to-configure-python) App Service Linux kapsayıcısı ve uygulamanız için Gunicorn başlangıç komutu özelleştirme özellikleri açıklanmaktadır.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Kapsayıcıları kullanarak Linux üzerinde App Service'e yayımlama

Linux'ta App Service ile önceden oluşturulmuş kapsayıcı üzerinde güvenmek yerine, kendi kapsayıcınızı sağlayabilirsiniz. Bu seçenek, kullandığınız hangi web sunucularını seçin ve kapsayıcının davranışını özelleştirmek için sağlar.

Oluşturun, yönetin ve kapsayıcıları anında iletme için iki seçenek vardır:

- Üzerinde açıklandığı gibi Visual Studio Code ve Docker uzantısını kullanın [Docker kapsayıcılarını kullanarak Python dağıtma](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Visual Studio Code kullanmasanız bile, makaleyi kullanarak üretime hazır uwsgi ve ngınx web sunucuları, Flask ve Django uygulamaları için kapsayıcı görüntülerini oluşturmaya yardımcı ayrıntılar sağlar. Ardından, Azure CLI kullanarak bu aynı kapsayıcı dağıtabilirsiniz.

- Üzerinde açıklandığı gibi komut satırı ve Azure CLI'yı kullanın [özel bir Docker görüntüsü kullanma](/azure/app-service/containers/tutorial-custom-docker-image) Azure belgeleri. Ancak, bu kılavuzda geneldir ve Python özgüdür.

## <a name="publish-to-iis"></a>IIS yayımlama

Visual Studio'da bir Windows sanal makine veya diğer IIS özellikli bilgisayarla yayımlayabilirsiniz **Yayımla** komutu. IIS kullanırken, oluşturmak veya değiştirmek mutlaka bir *web.config* IIS bildiren uygulama dosyasında burada Python yorumlayıcısı Bul. Daha fazla bilgi için [için IIS web uygulamalarını yapılandırma](configure-web-apps-for-iis-windows.md).
