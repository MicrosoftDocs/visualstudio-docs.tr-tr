---
title: Yönetici portalında abonelikleri düzenleme | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Yöneticiler abonelik atamaları düzenleme nasıl öğrenin.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 588568521b52b6c21c93b6488829b5055d12048b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942471"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Visual Studio aboneliği atamalarını düzenlemek

Bir abonelik Yöneticisi olarak kuruluşunuzdaki kişiler için atanan abonelik için değişiklik yapabilirsiniz.  Bu makalede, değişiklikler yapabilir ve gerekli adımlar sağlanmaktadır türleri açıklanmaktadır. 

## <a name="making-changes-to-subscriber-information"></a>Abonelik bilgileri değişiklik yapma
Hataları düzeltin veya bilgileri güncelleştirmek için bir abonenin bilgileri düzenleyebilirsiniz. 

Abone düzenlemek için abonenin e-posta adresi yanındaki fareyi üzerine geldiğinizde görüntülenen üç nokta (...) seçin. Açılan bir menüde görünecektir.  Seçin **Düzenle** abonenin ayrıntılarını değiştirmek için. Abonenin satırda kılavuzunda Düzenle açmak için çift tıklayabilirsiniz.
> [!div class="mx-imgBorder"]
> ![Düzenlemek için aboneyi Seç](_img/edit-license/select-subscriber.png)

Abonenin adı, Soyadı, ülke, dil ve yükleme güncelleştirebilirsiniz. Abonenin bilgileri düzenleyin ve ardından **Kaydet**.

   > [!NOTE]
   > Bir abone için abonelik düzeyinde değiştirmeniz gerekirse, Kullanıcı Portalı'ndan silip bunları yeniden eklemeniz gerekir. Abonelik düzeylerini düzenlenebilir değil.

## <a name="editing-multiple-subscribers-using-bulk-edit"></a>Toplu düzenlemeyi kullanarak birden çok aboneyi düzenleme

Tek seferde toplu düzenleme işlemi kullanarak birden fazla aboneye düzenleyebilirsiniz. Bu özellik, öncelikle kurumsal oluşturulmak e-posta adresi değişiklikleri veya bir kuruluş yüklemeleri için erişimi kısıtlamak verdi, kuruluşlar için kullanılır. 

   > [!IMPORTANT]
   > Abonelik düzeylerini (yani, Enterprise, Professional, vb.) ve abonelik GUID'leri değiştirilemez.  Değiştirilen bu öğeler ile karşıya yükleme denemesi, karşıya yükleme başarısız olur.  

1. Aynı anda birden çok aboneyi düzenleme aboneleri sekmesine gidin. Üstteki Şeritte tıklayın **toplu düzenleme**. 

2. Toplu düzenleme abone bilgisi düzenlemeleri için bir Excel şablonu kullanır. Toplu düzenleme kutusuna tıklayın **bu excel dışarı aktarma** aboneleri tüm bunların bilgileri dahil olmak üzere geçerli listesini indirmek için. 
   > [!div class="mx-imgBorder"]
   > ![Dışarı aktarma - lisans düzenleme toplu düzenlemeler listesi](_img/edit-license/edit-license-bulk-edit-export.png)

3. Ardından, kolayca bulmak ve bunu karşıya yüklemeden önce gerekli değişiklikleri yapın dosyayı yerel olarak kaydedin. Başarılı bir karşıya yükleme emin olmak için **abonelik düzeyinde veya abonelik GUID'si düzenlemeyin** bunu yaparsanız bu nedenle karşıya yükleme başarısız olmasına neden olur. 

4. İade Visual Studio abonelikleri Yönetim Portalı ve toplu düzenleme iletişim kutusunda, tıklayın **Gözat**. Kaydettiğiniz Excel dosyasını seçin ve tıklayın **Tamam**. Ekranda, karşıya yükleme ilerleme durumunu görürsünüz.
   > [!div class="mx-imgBorder"]    
   > ![Bir lisans - düzenleme toplu düzenlemeler karşıya dosya yükleme](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Dosyayı yükledikten sonra size başarılı olduğunu bildiren bir bildirim görürsünüz. Bu noktada, yaptığınız düzenlemeleri abone bilgileri yansıtılır. 

