---
title: Sunucu Gezgini 'den Azure sanal makinelerine erişme | Microsoft Docs
description: Visual Studio 'da Sunucu Gezgini Azure sanal makinelerini (VM 'Ler) oluşturma ve yönetme hakkında genel bakış alın.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 653a9be556441f5f8d5fc1c1053b144dc97dd3b2
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901876"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Sunucu Gezgini'nden Azure Sanal Makineler'e erişme

Azure tarafından barındırılan sanal makineleriniz varsa bunlara Sunucu Gezgini erişebilirsiniz. Mobil hizmetlerinizi görüntülemek için önce Azure aboneliğinizde oturum açmanız gerekir. Oturum açmak için Sunucu Gezgini Azure düğümünün kısayol menüsünü açın ve **Microsoft Azure Bağlan**' ı seçin.

1. Cloud Explorer 'da bir sanal makine seçin ve ardından Özellikler penceresini göstermek için F4 tuşunu seçin.

    Aşağıdaki tabloda kullanılabilen özellikler gösterilmektedir, ancak bunların hepsi salt okunurdur. Bunları değiştirmek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | DNS Adı |Sanal makinenin Internet adresine sahip URL. |
   | Ortam |Bir sanal makine için, bu özelliğin değeri her zaman üretime yöneliktir. |
   | Ad |Sanal makinenin adı. |
   | Boyut |Kullanılabilir bellek ve disk alanı miktarını yansıtan sanal makinenin boyutu. Daha fazla bilgi için bkz. [sanal makine boyutları](/azure/cloud-services/cloud-services-sizes-specs). |
   | Durum |Değerler, başlatma, başlatma, durdurma, durdurma ve durum alma içerir. Durum alma görünürse, geçerli durum bilinmiyor olur. Bu özelliğin değerleri, [Azure Portal](https://portal.azure.com)kullanılan değerlerden farklıdır. |
   | SubscriptionID |Azure hesabınızın abonelik KIMLIĞI. Bir aboneliğin özelliklerini görüntüleyerek [Azure Portal](https://portal.azure.com) bu bilgileri gösterebilirsiniz. |
2. Bir uç nokta düğümü seçin ve ardından **Özellikler** penceresini görüntüleyin.
3. Aşağıdaki tabloda, uç noktaların kullanılabilir özellikleri açıklanmıştır, ancak bunlar salt okunurdur. Bir sanal makineye yönelik uç noktaları eklemek veya düzenlemek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | Ad |Uç nokta için bir tanımlayıcı. |
   | Özel bağlantı noktası |Uygulamanıza iç ağ erişimi için bağlantı noktası. |
   | Protokol |Bu uç noktanın aktarım katmanının, TCP veya UDP kullandığı protokol. |
   | Genel Bağlantı Noktası |Uygulamanıza genel erişim için kullanılan bağlantı noktası. |
