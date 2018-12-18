---
title: Cloud Explorer ile Azure kaynaklarını yönetme | Microsoft Docs
description: Visual Studio içinden Azure kaynaklara göz atıp yönetmek için cloud Explorer'ı kullanmayı öğrenin.
author: ghogen
manager: douge
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: feb56bb0edd66a24b8505c26587129437dd4b971
ms.sourcegitcommit: e03b7a4cab26fbc792f368e3c6b4ca4a03caa786
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52459752"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio Cloud Explorer'da Azure hizmetlerinizle ilişkilendirilmiş kaynakları yönetme

Bulut Gezgini, Azure kaynaklarını ve kaynak gruplarını görüntüleme, özelliklerini inceleme ve Visual Studio içinde temel Geliştirici tanılama eylemleri gerçekleştirmek sağlar. 

Gibi [Azure portalında](http://go.microsoft.com/fwlink/p/?LinkID=525040), Cloud Explorer, Azure Resource Manager yığını üzerinde oluşturulur. Bu nedenle, Cloud Explorer, Azure kaynak grupları gibi kaynakları ve Logic apps ve API apps gibi Azure hizmetlerinin anlar ve desteklediği [rol tabanlı erişim denetimi](/azure/role-based-access-control/role-assignments-portal) (RBAC). 

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017](https://www.visualstudio.com/downloads/) ile **Azure iş yükü** seçili veya ile Visual Studio'nun önceki bir sürümünün [.NET 2.9 için Microsoft Azure SDK'sı](https://www.microsoft.com/en-us/download/details.aspx?id=51657).
* Microsoft Azure hesabı - bir hesabınız yoksa, şunları yapabilirsiniz [ücretsiz deneme için kaydolun](http://go.microsoft.com/fwlink/?LinkId=623901) veya [Visual Studio abone Avantajlarınızı etkinleştirebilirsiniz](http://go.microsoft.com/fwlink/?LinkId=623901).

> [!NOTE]
> Cloud Explorer'ı görüntülemek için seçin **görünümü** > **Cloud Explorer** menü çubuğundaki.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Bir Azure ekleme hesabı için Cloud Explorer

Bir Azure hesabı ile ilişkili kaynakları görüntülemek için hesap için Cloud Explorer eklemeniz gerekir. 

1. İçinde **Cloud Explorer**seçin **Azure hesap ayarları**.

   ![Cloud Explorer Azure hesap ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Seçin **hesapları yönetme**. 

   ![Cloud Explorer ekleme hesabının bağlantısı](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Gözatmak istediğiniz kaynakları Azure hesabında oturum açın. 

1. Bir Azure hesabı için oturum açtıktan sonra ilgili hesapla ilişkili abonelikleri görüntüleyin. Göz atın ve ardından istediğiniz hesap aboneliklerinin onay kutularını işaretleyin **Uygula**. 

   ![Cloud Explorer: görüntülemek için Azure aboneliklerini seçin](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Kaynakları gözatmak istediğiniz abonelikleri seçtikten sonra Cloud Explorer'ın bu abonelikler ve kaynaklar görüntüler.

   ![Cloud Explorer kaynak için bir Azure hesabı listeleme](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Bir Azure hesabı bulut gezgininden Kaldır 

1. İçinde **Cloud Explorer**seçin **hesap yönetimi**.

   ![Cloud Explorer Azure hesap ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Kaldırmak istediğiniz hesabı yanındaki seçin **hesaplarını yönetme**.

   ![Cloud Explorer Azure hesap ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Seçin **Kaldır** hesabı kaldırmak için.

    ![Cloud Explorer'ı yönetme hesapları iletişim kutusu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Kaynak türleri veya kaynak grupları görüntüleyin

Azure kaynaklarınızı görüntülemek için ya da seçebilirsiniz **kaynak türleri** veya **kaynak grupları** görünümü.

1. İçinde **Cloud Explorer**, kaynağın Görünüm açılan menüyü seçin.

   ![İstenen kaynak görünümü seçmek için bulut Gezgini açılır listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Bağlam menüsünden istenen görünümü seçin: 

   * **Kaynak türleri** görünümü: kullanılan genel görünümü [Azure portalında](http://go.microsoft.com/fwlink/p/?LinkID=525040), Azure kaynaklarınızın, sanal makineler web uygulamaları ve depolama hesapları gibi türlerine göre kategorilere gösterir. 
   * **Kaynak grupları** görüntüleme - kategorilere ayıran Azure kaynakları ile bunların ilişkili Azure kaynak grubu tarafından. Bir kaynak grubu, genellikle belirli bir uygulama tarafından kullanılan Azure kaynakları paketidir. Azure kaynak grupları hakkında daha fazla bilgi edinmek için [Azure Resource Manager'a genel bakış](/azure/azure-resource-manager/resource-group-overview).

   Aşağıdaki görüntüde bir karşılaştırma iki kaynağın görünüm gösterilmektedir:

   ![Bulut Gezgini kaynak görünümlerin karşılaştırması](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Cloud Explorer'da kaynakları gitmek ve görüntülemek

Bir Azure kaynağına gidin ve bulut Gezgini'nde bilgilerini görüntülemek için öğenin türü veya ilişkili kaynak grubunu genişletin ve ardından kaynağı seçin. Bir kaynak seçtiğinizde, iki sekmelerde - bilgi görünür **eylemleri** ve **özellikleri** - Cloud Explorer'ın altındaki.

* **Eylemler** sekmesi - bulut Gezgini'nde seçili kaynak için gerçekleştirebileceğiniz eylemleri listeler. Bu seçenekler, bağlam menüsünü görüntülemek için kaynak sağ tıklayarak da görüntüleyebilirsiniz.

* **Özellikleri** sekmesi - olduğu ilişkili türü, yerel ayar ve kaynak grubu gibi kaynak özelliklerini gösterir.

Aşağıdaki görüntüde, her sekmesinde bir App Service için gördüğünüz bir örnek karşılaştırma gösterilmektedir:

  ![Cloud Explorer'ın ekran görüntüsü](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Her kaynak eylemi sahip **portalında açın**. Bu eylem öğesini seçtiğinizde, seçili kaynak Cloud Explorer görüntüler [Azure portalında](http://go.microsoft.com/fwlink/p/?LinkID=525040). **Portalında açın** özelliğidir derin şekilde iç içe geçmiş kaynaklar için gezinmek için kullanışlı.

Ek eylemleri ve özellik değerlerini de Azure kaynak tabanlı görünebilir. Örneğin, web apps ve logic apps eylemleri de **tarayıcıda aç** ve **hata ayıklayıcının** ek olarak **portalında açın**. Düzenleyiciler açmak için Eylemler, bir depolama hesabı blob, kuyruk veya tablo seçtiğinizde görünür. Azure uygulamanız **URL** ve **durumu** depolama kaynaklarını anahtar ve bağlantı dizesi özellikleri varken özellikleri.

## <a name="find-resources-in-cloud-explorer"></a>Cloud Explorer'da kaynakları bulun

Azure hesabı aboneliklerinizde belirli bir ada sahip kaynakları bulmak için adı girin. **arama** Cloud Explorer'da kutusu.

  ![Cloud Explorer'da kaynakları bulma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Karakter girerken **arama** kutusunda yalnızca bu karakterlerle eşleşen kaynakları kaynak ağaçta görünür.
