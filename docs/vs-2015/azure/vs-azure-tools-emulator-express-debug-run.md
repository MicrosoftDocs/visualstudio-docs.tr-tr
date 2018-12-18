---
title: Çalıştırın ve Azure bulut hizmeti yerel bir makinede hata ayıklamak için emulator Express'i kullanma | Microsoft Docs
description: Çalıştırın ve bir bulut hizmeti yerel bir makinede hata ayıklamak için emulator Express'i kullanma
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003426"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Emulator Express kullanarak Azure bulut hizmetini yerel makinede çalıştırma ve hatalarını ayıklama
Emulator Express kullanarak sınamak ve Visual Studio'yu yönetici olarak çalıştırarak olmadan bir bulut hizmeti hata ayıklama. Emulator Express veya tam öykünücü, bulut hizmetinizin gereksinimlerine bağlı olarak kullanmak üzere proje ayarlarınız ayarlayabilirsiniz. Tam öykünücü hakkında daha fazla bilgi için bkz: [işlem öykünücüsü'nde bir Azure uygulama çalıştırmak](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Visual Studio emulator Express'i kullanma
Azure SDK 2.3 veya üstü bir Azure projesi oluşturduğunuzda, Emulator Express'i otomatik olarak kullanılır. Azure SDK'ın önceki bir sürümü ile oluşturulmuş var olan projeleri için Emulator Express'i seçmek için aşağıdaki adımları kullanın:

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **özellikleri**.

1. Proje özellik sayfaları'nda seçin **Web** sekmesi.

    ![Bir Azure bulut hizmeti projesi için özellikleri](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Altında **yerel geliştirme sunucusu**seçin **IIS Express kullan seçeneği**.

1. Altında **öykünücü**seçin **kullanım Emulator Express**.
   
1. Emulator Express başlatmak için komut isteminde aşağıdaki komutu çalıştırın: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Express sınırlamaları
Emulator Express sınırlamaları aşağıdaki sorunlar bilinmektedir: 

- Emulator Express, IIS Web sunucusu ile uyumlu değil.
- Bulut hizmetinizin çoklu roller bulunabilir, ancak her rol için bir örnek sınırlıdır.
- Bağlantı noktası numaralarını 1000 aşağıda erişemez. Bir bağlantı noktası 1000 aşağıda normalde kullanan bir kimlik doğrulama sağlayıcısı kullanıyorsanız, 1000'in üzerinde bir bağlantı noktası numarası için bu değeri değiştirmeniz gerekebilir.
- Azure işlem öykünücüsü için geçerli olan sınırlamalar Emulator Express için de geçerlidir. Örneğin, dağıtım başına 50'den fazla rol örneği olamaz. Azure işlem öykünücüsü hakkında daha fazla bilgi için bkz: [işlem öykünücüsü'nde bir Azure uygulama çalıştırmak](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Sonraki adımlar
[Azure bulut hizmetlerinde hata ayıklama](https://msdn.microsoft.com/library/azure/ee405479.aspx)
