---
title: Araç penceresi ekran yapılandırması | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c563888424ae4825f3e5b10fc0592029a29cb84b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736952"
---
# <a name="tool-window-display-configuration"></a>Araç penceresi ekran yapılandırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage araç penceresi, varsayılan konum, boyut, yerleştirme stilini ve diğer görünürlük bilgileri kaydedildiğinde, isteğe bağlı değerler belirtilir. Araç penceresi kayıt hakkında daha fazla bilgi için bkz. [aracı Windows kayıt defteri](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Pencere bilgilerini görüntüle  
 Bir araç penceresinin temel görüntü yapılandırma en fazla altı isteğe bağlı değerler depolanır:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|Ad|REG_SZ|"Kısa adını buraya gelecek"|Araç penceresi açıklayan kısa bir ad. Yalnızca başvuru kayıt defteri için kullanılır.|  
|kayan nokta|REG_SZ|"X1, Y1, X2, Y2"|Dört virgülle ayrılmış değerler. X1, Y1 olan araç penceresinin sol üst köşesinin koordinatı. X2, Y2 olan sağ alt köşedeki koordinatı. Ekran koordinatlarında tüm değerler.|  
|Stil|REG_SZ|"MDI"<br /><br /> "Kaydırabilirsiniz"<br /><br /> "Bağlı"<br /><br /> "Sekmeli"<br /><br /> "AlwaysFloat"|İlk belirten bir anahtar sözcüğü, araç penceresi durumunu görüntüler.<br /><br /> "MDI" = ile MDI pencere yerleştirildi.<br /><br /> "Kaydırabilirsiniz" kayan =.<br /><br /> "Bağlı" = başka bir pencere (penceresi girdisinde belirtilen) ile bağlantılı.<br /><br /> "Sekmeli" = başka bir araç penceresi ile birleştirilmiş.<br /><br /> "AlwaysFloat" = yerleştirilmiş olabilir.<br /><br /> Daha fazla bilgi için aşağıdaki Açıklamalar bölümüne bakın.|  
|Pencere|REG_SZ|*\<GUID &GT;*|Bir pencere için araç penceresi bağlı sekmeli veya GUID'si. GUID kendi windows birini ya da windows biri ait olabileceği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Yönlendirme|REG_SZ|"Sol"<br /><br /> "Sağ"<br /><br /> "Top"<br /><br /> "Alt"|Aşağıdaki Açıklamalar bölümüne bakın.|  
|DontForceCreate|REG_DWORD|0 veya 1|Bu girdiyi yok ve değeri sıfır olmadığında penceresi yüklendi ancak hemen görüntülenir.|  
  
### <a name="comments"></a>Açıklamalar  
 Yönlendirme girişi başlık çubuğunu çift tıklatıldığında burada araç penceresi noktaları konumunu tanımlar. Pencere girdisinde belirtilen pencere göre konumdur. Stil Giriş "Bağlı" olarak ayarlanırsa, yönlendirme girişi "Sol", "Hakkı", "Üst" veya "Alt" olabilir. Varsa stili Giriş "Sekmeli", "Giriş bırakılabilir" yönlendirmesini veya "Sağ" ve burada sekme eklenir belirtir. Stil Giriş "Kaydırabilirsiniz" ise, araç penceresi ilk kayar. Başlık çubuğunu çift tıklatıldığında, Yönlendirme ve pencere girişleri uygulamak ve pencerenin "Sekmeli" style kullanır. Stil Giriş "AlwaysFloat" ise, araç penceresi yerleştirilmiş olamaz. Stil Giriş "MDI" ise, araç penceresi MDI alanına bağlıdır ve pencere giriş yoksayılır.  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Aracı penceresinde görünürlük  
 İsteğe bağlı görünürlük alt değerleri, bir araç penceresinin görünürlüğü ayarları belirler. Değerleri adlarını, pencerenin görünürlük gerektiren komutlarının GUID'leri depolamak için kullanılır. IDE komut yürütülürse, araç penceresi oluşturulur ve görünür hale güvence altına alır.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Ad|Tür|Veri|Açıklama|  
|----------|----------|----------|-----------------|  
|(Varsayılan)|REG_SZ|Yok.|Boş bırakın.|  
|*\<GUID &GT;*|REG_DWORD veya REG_SZ|0 veya açıklayıcı bir dize.|İsteğe bağlı. Girişin adı görünürlük gerektiren bir komutun GUID olması gerekir. Değer, yalnızca bilgilendirici bir dize içerir. Genellikle, değeri olan bir `reg_dword` 0 olarak ayarlayın.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage'ı temel bileşenleri](../misc/vspackage-essentials.md)

