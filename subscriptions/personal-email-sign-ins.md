---
title: Kişisel e-postalar VLSC görüntülenen
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: Visual Studio abonelikleri – neden Hotmail veya Gmail adresleri My aboneleri için görüyorum?
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a9b0e02acd0c362759997938cec91983a5d48547
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335726"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Hotmail veya Gmail adresleri my aboneleri için neden görüyorum visual Studio abonelikleri –? 

Şirketler Toplu Lisanslama hizmeti Merkezi (VLSC) gelen yeni Visual Studio geçirirken [abonelikleri Yönetim Portalı](https://manage.visualstudio.com), Yöneticiler, "oturum açma e-posta adresi" bazı aboneleri için bulmak Şaşkın gösterir, Hotmail, Gmail veya Yahoo gibi e-posta adresi bir 3. taraf.  Daha fazla bilgi için kullanıma [bu videoyu](https://www.youtube.com/watch?v=1op-i1zEMfY&t=0s&list=PLReL099Y5nRfDyvvwzNDBaZe7qTxmuM2T&index=6).

## <a name="cause"></a>Sebep

Bu senaryo, eski MSDN abonesi deneyimiyle ilişkili oturum açma işlemleri nedeniyle oluşur. Kullanıcıları Toplu Lisans Hizmet Merkezi (VLSC) gelen değişiklik olmadan yeni portalı geçirildi. Yöneticiler kullanıcılar kişisel hesaplar abonelik faydaları erişmek için kullanmış haberdar olmuş olabilir. 2016'tamamlandı, Visual Studio abone geçişler önce Visual Studio Abonelik başarıyla kullanmak için gereken iki eylem vardı:
1. Yönetici "abonelik atanan işlerini kullanarak bir tek tek abone" ya da Okul e-posta adresi.
2. Abone "aboneliği etkinleştirildi".

Abone etkinleştirme işlemi sırasında: oturum açmak için bir Microsoft hesabı (MSA) gerektiriyordu. Abone iş veya Okul hesabı yapmaya çalışırsanız eşleşmedi (örneğin tasha@contoso.com) MSA, bir yeni MSA oluşturma veya mevcut bir yararlanın. Bu ","atanan için e-posta adresinden"farklı olan kullanıcıların oturum açma e-posta adresi" ile sonuçlandı.

> [!NOTE] 
> Yeni abone deneyimi [ https://my.visualstudio.com ](https://my.visualstudio.com?wt.mc_id=o~msft~docs) iş/Okul ve Microsoft hesabı (MAA) kimlik türlerini destekler.

Son olarak, yönetici geçiş VLSC adresi ile ilgili abonenin"oturum açma e-posta yeni abone yönetim deneyimi doldurmak için" dan veri sürüyor olduğundan, bu daha önce gözden kaçan kişisel hesapları nedeniyle yakın zamanda geçirilmiş admins görebilirsiniz Bu bilgiler daha görünür hale getirmek değişiklikler kullanıcı arabirimi.

## <a name="solution"></a>Çözüm

Sorunu düzeltmek için oturum açma e-posta adreslerini güncelleştirmek için abone bilgilerini düzenlemek gerekir.  Düzenlemeler, tek tek aboneleri için ya da toplu yapılabilir. Tam bilgi için lütfen ziyaret [bir abonelik](edit-license.md).  

Subscriber(s) e-posta adresleri güncelleştirdikten sonra kullanıcıların oturum açma bilgileri değişti bildirmek isteyebilirsiniz.  Bunlar, ayrıca güncelleştirilmiş bilgileri içeren bir e-posta alırsınız.   