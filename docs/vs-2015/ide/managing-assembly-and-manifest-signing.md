---
title: Derleme ve bildirim imzalamayı yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 831fb08941e16abdb197d3a25e71f2a20fcb14cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909685"
---
# <a name="managing-assembly-and-manifest-signing"></a>Derleme ve Bildirim İmzalamayı Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tanımlayıcı ad imzalama bir yazılım bileşeni genel olarak benzersiz bir kimlik sağlar. Güçlü adlar derleme başkası tarafından görünerek edilemez olduğunu garanti ve bileşen bağımlılıklar ve yapılandırma deyimleri bileşen sürümü ve doğru bileşeni eşleme emin olmak için kullanılır.  
  
 Güçlü bir ad derlemenin kimliğinden (basit metin adından, sürüm numarası ve kültür bilgilerini) bir ortak anahtar belirteci ve dijital imza oluşur.  
  
 Visual Basic ve C# projelerinde imzalama derlemeler hakkında daha fazla bilgi için bkz: [bkz](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Visual C++ projelerinde imzalama derlemeler hakkında daha fazla bilgi için bkz: [tanımlayıcı ad derlemeleri (derleme imzalama) (C + +/ CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).  
  
## <a name="asset-types-and-signing"></a>Varlık türleri ve imzalama  
 .NET derlemelerini ve uygulama bildirimleri imzalayabilirsiniz. Bunlar aşağıdakileri içerir:  
  
- yürütülebilir dosyalar (.exe)  
  
- uygulama bildirimleri (. exe.manifest)  
  
- dağıtım bildirimleri (.application)  
  
- Paylaşılan bileşen derlemeleri (.dll)  
  
  Aşağıdaki varlık türleri oturum açmanız gerekir:  
  
1. Derlemeleri, Genel Derleme Önbelleği (GAC) bunları dağıtmak istiyorsanız.  
  
2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Uygulama ve dağıtım bildirimleri. Visual Studio, bu uygulamalar için varsayılan olarak imzalama sağlar.  
  
3. COM birlikte çalışabilirlik için kullanılan birincil birlikte çalışma derlemelerini. Birincil birlikte çalışma derlemesi bir COM tür kitaplığından oluştururken, TLBIMP yardımcı programı güçlü adlandırma zorlar.  
  
   Genel olarak yürütülebilir dosyaları kaydolma. Kesin adlandırılmış bir bileşeni uygulama ile dağıtılan kesin adlandırılmış bir bileşen başvuramaz. Visual Studio uygulama yürütülebilir dosyaları oturum açmasını sağlamayan ancak bunun yerine zayıf adlı yürütülebilir öğeye işaret uygulama bildirimini imzalar. Genellikle, imzalama, bağımlılıkları yönetmek daha zor zorlaştırabilir çünkü uygulamanıza özel bileşenler imzalama kaçınmanız gerekir.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Bir derlemeyi Visual Studio'da oturum açma  
 Bir uygulama veya bileşenin kullanarak oturum **imzalama** Proje Özellikleri penceresi için sekmesinde ('nde proje düğümüne sağ tıklayın **Çözüm Gezgini** seçip **özellikleri**, veya tür **proje özellikleri** içinde **hızlı başlatma** penceresinde ya da alt + ENTER tuşlarına basın **Çözüm Gezgini** pencere). Seçin **imzalama** sekmesine ve ardından seçin **derlemeyi imzalamayı** onay kutusu.  
  
 Bir anahtar dosyası belirtin. Yeni bir anahtar dosyası oluşturmayı seçerseniz, yeni anahtar dosyaları her zaman .pfx biçiminde oluşturulduğunu unutmayın. Yeni dosya için bir ad ve parola gerekir.  
  
> [!WARNING]
>  Anahtar dosyanızı başkası kullanmasını önlemek için bir parola ile her zaman korur. Sağlayıcıları veya sertifika depolarını kullanarak, anahtarlarınızın güvenliğini sağlayabilirsiniz.  
  
 Ayrıca, önceden oluşturduğunuz bir anahtara işaret edebilir. Anahtarları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir genel-özel anahtar çifti oluşturma](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Erişimi yalnızca ortak anahtar varsa, anahtar atama erteleneceği imzalamayı geciktirme kullanabilirsiniz. Seçerek imzalamayı geciktirme etkinleştirme **gecikme yalnızca oturum** onay kutusu. Gecikmeli imzalanmış bir proje çalışmaz ve hata ayıklaması yapılamıyor. Ancak, geliştirme sırasında doğrulama kullanarak atlayabilir [Sn.exe (tanımlayıcı ad aracı)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) ile `-Vr` seçeneği.  
  
 Bildirimleri imzalama hakkında daha fazla bilgi için bkz: [nasıl yapılır: oturum uygulama ve dağıtım bildirimlerini](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tanımlayıcı adlı derlemeler](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Tanımlayıcı Ad Derlemeleri (Derleme İmzalama) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)



