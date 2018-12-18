---
title: 'Nasıl yapılır: özel metin işaretçileri oluştur | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac2ad16c0e6a3e0a6c76e15ff6860838fa349c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893110"
---
# <a name="how-to-create-custom-text-markers"></a>Nasıl yapılır: özel metin işaretçileri oluşturma
Vurgulamak veya kod düzenlemek için bir özel metin işaretçisi oluşturmak istiyorsanız, aşağıdaki adımları izlemelisiniz:  
  
- Diğer araçları erişebilmesi yeni metin işaretçisi kaydedin.  
  
- Varsayılan uygulama ve metin işaretçisi yapılandırılmasını sağlar.  
  
- Diğer işlemler tarafından yapmak için kullanılabilecek bir hizmet oluşturma metin işaret kullanın.  
  
  Bir bölge kodu bir metin işaretçisi uygulama hakkında daha fazla bilgi için bkz: [nasıl yapılır: metin işaretçileri kullanma](../extensibility/how-to-use-text-markers.md).  
  
## <a name="to-register-a-custom-marker"></a>Özel işaret kaydetmek için  
  
1. Gibi bir kayıt defteri girişini oluşturun:  
  
    **Hkey_local_machıne\software\microsoft\visualstudio\\\<sürüm > \Text Editor\External işaretçileri\\\<MarkerGUID >**  
  
    *\<MarkerGUID >* olduğu bir `GUID` eklenen işaret tanımlamak için kullanılan  
  
    `<Version>` sürümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], örneğin 8.0  
  
    `<PackageGUID>` VSPackage'ı GUİD'si Otomasyon nesnesi uygular.  
  
   > [!NOTE]
   >  Kök yolu **hkey_local_machıne\software\microsoft\visualstudio\\\<sürüm >** Visual Studio Kabuğu başlatıldığında daha fazla bilgi için bkz, alternatif bir kök ile geçersiz kılınabilir [Komut satırı anahtarları](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Dört değer altında oluşturma **hkey_local_machıne\software\microsoft\visualstudio\\\<sürüm > \Text Editor\External işaretçileri\\\<MarkerGUID >**  
  
   -   (Varsayılan)  
  
   -   Hizmet  
  
   -   displayName  
  
   -   Paket  
  
   -   `Default` tür REG_SZ isteğe bağlı bir girdidir. Ayarlandığında, giriş bazı yararlı tanımlayıcı bilgileri, örneğin "özel metin işaretçisi" içeren bir dize değeridir.  
  
   -   `Service` bir giriş türü REG_SZ içeren özel metin işaretçisi tarafından proffering sağlayan hizmet GUID dizesi olduğu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. {XXXXXX XXXX XXXX XXXX XXXXXXXXX} biçimindedir.  
  
   -   `DisplayName` Özel metin işaretçisi adını kaynak Kimliğini içeren bir giriş türü REG_SZ. #YYYY biçimidir.  
  
   -   `Package` Giriş türü REG_SZ içeren `GUID` hizmeti sağlayan VSPackage'nın hizmetinin altında listelenir. {XXXXXX XXXX XXXX XXXX XXXXXXXXX} biçimindedir.  
  
## <a name="to-create-a-custom-text-marker"></a>Bir özel metin işaretçisi oluşturmak için  
  
1.  Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> arabirimi.  
  
     Bu arabirim, uygulamanız özel işaretçi türünüz görünümünü ve davranışını tanımlar.  
  
     Bu arabirim aldığında çağrılan  
  
    1.  Bir kullanıcı ilk kez IDE'yi başlatır.  
  
    2.  Bir kullanıcının seçtiği **Varsayılanlara Sıfırla** düğmesini **yazı tipleri ve renkler** özellik sayfasında **ortam** klasörü sol bölmede bulunan  **Seçenekleri** iletişim kutusu öğesinden alınan **Araçları** IDE'nin menüsü.  
  
2.  Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> yöntemi, hangi belirtme `IVsPackageDefinedTextMarkerType` uygulaması döndürülmesi tabanlı işaretçisi türünde yöntem çağrısında belirtilen GUID.  
  
     Ortam bu yöntemi ilk kez özel işaretçi türünüz oluşturulur ve özel işaret türünü tanımlayan bir GUID belirtir çağırır.  
  
## <a name="to-proffer-your-marker-type-as-a-service"></a>Hizmet olarak işaretçi türünüz proffer için  
  
1.  Çağrı <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> döndürülür.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> yöntemi, özel işaret türü hizmetinizi tanımlayan ve uygulamanız için bir işaretçi sağlayan bir GUID belirterek <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> arabirimi. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Uygulama, uygulamanız için bir işaretçi döndürmelidir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> arabirimi.  
  
     Hizmetinizi döndürülür tanımlayan benzersiz bir tanımlama bilgisi. Özel işaret türü hizmetinizi çağırarak iptal etmek için bu tanımlama bilgisi daha sonra kullanabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> bu tanımlama bilgisi değeri belirterek arabirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Metin işaretçileri eski API'si ile kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: standart metin işaretçileri Ekle](../extensibility/how-to-add-standard-text-markers.md)   
 [Nasıl yapılır: uygulama, hata işaretçileri](../extensibility/how-to-implement-error-markers.md)   
 [Nasıl yapılır: metin işaretçileri kullanma](../extensibility/how-to-use-text-markers.md)