---
title: Dış araçları yönetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf8e00635ff76e9e4ccfc4cbedbafabe8b0718dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244497"
---
# <a name="managing-external-tools"></a>Dış Araçları Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dış Araçları'ndan çağırabilirsiniz Visual Studio içinde. Birkaç varsayılan araç ulaşılabilir **Araçları** menü, ancak diğer yürütülebilir dosyaların kendi ekleyebilirsiniz.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Visual Studio Araçları menüsündeki araçları  
 Aşağıdaki araçları çağırabilirsiniz **Araçları** menüde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Adından tarafından de çağırabilirsiniz **hızlı başlatma** penceresi. GuidGen.exe çağırmak için örneğin **GUID Oluştur**.  
  
1.  GUID oluştur: bir GUID oluşturur.  
  
2.  Hata arama: girilen değerin bir hata iletisi alır. Daha fazla bilgi için [ERRLOOK başvurusu](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3.  ATL/MFC izleme aracı: hata ayıklama İzleyici iletileri ATL ve MFC kaynakları gösterir.  
  
4.  PreEmptive Dotfuscator ve analiz: tersine mühendislik karşı koruyan .NET programlar.  
  
5.  SPY ++'ta: grafik işlemleri, iş parçacıkları, windows ve pencere iletilerini görüntüler.  
  
6.  WCF Hizmeti Yapılandırma Düzenleyicisi: oluşturma ve WCF hizmetleri için yapılandırma ayarlarını değiştirmenize olanak sağlar.  
  
> [!WARNING]
>  Dış araçların farklı bir liste görebilirsiniz, hangi Visual Studio sürümü bağlı olarak, yüklediğiniz ve uyguladığınız ayarları profili. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Yeni araçları ekleme  
 Harici bir aracı için ekleyebilirsiniz **Araçları** menüsü. Açık **dış Araçlar** iletişim kutusu ve tıklatın **Ekle**, ardından bilgileri doldurun. Örneğin, Windows Explorer'ın şu anda dosya dizininde açmak için şu girdiyi Visual Studio'da Aç nedenleri:  
  
1.  Başlık: Dosya konumunu Aç  
  
2.  Komut: explorer.exe  
  
3.  Bağımsız değişkenleri: / root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Dış araçlar bağımsız değişkenleri  
 Şu bağımsız değişkenler bir dış Aracı'nı başlattığınızda, atanmış olan Visual Studio değişkenlerdir. Not Defteri'ni veya Spy ++ hakkında listelenebilir gibi dış araçlara bağlantıları **Araçları** dış Araçlar iletişim kutusunu kullanarak menüsü.  
  
> [!NOTE]
>  IDE durum çubuğu ekleme noktasını etkin Kod Düzenleyicisi'nde nerede göstermek için geçerli satır ve sütun geçerli değişkenlerini görüntüler. Geçerli metin değişkeni, bu konumda seçili kod ve metin döndürür.  
  
|Ad|Bağımsız Değişken|Açıklama|  
|----------|--------------|-----------------|  
|Öğe yolu|$(ItemPath)|Geçerli dosyanın tam dosya adı (sürücü yolu + dosya adı).|  
|Öğe dizini|$(ItemDir)|Geçerli bir dosya (sürücü + yolu) dizini.|  
|Öğe dosya adı|$(ItemFilename)|Dosya adı geçerli dosyanın (dosya adı).|  
|Öğesi uzantısı|$(ItemExt)|Geçerli dosyanın dosya adı uzantısı.|  
|Geçerli satırı|$(CurLine)|İmleci kod penceresinde geçerli satır konumu.|  
|Geçerli sütun|$(CurCol)|İmleci kod penceresinde geçerli sütun konumu.|  
|Geçerli metin|$(CurText)|Seçili metni.|  
|Hedef yolu|$(TargetPath)|Oluşturulacak öğe tam dosya adı (sürücü yolu + dosya adı).|  
|Hedef Dizin|$(TargetDir)|Oluşturulacak öğe dizini.|  
|Hedef Adı|$(TargetName)|Oluşturulacak öğe dosya adı.|  
|Hedef uzantısı|$(TargetExt)|Oluşturulacak öğesinin dosya adı uzantısı.|  
|İkili dizin|$(BinDir)|Oluşturulmakta olan ikili (sürücü + yolu tanımlanan) son konum. Örneğin:**\\... \My Documents\Visual Studio \<sürüm >\\< ProjectName\>\bin\debug**|  
|Proje dizini|$(ProjDir)|Geçerli proje (sürücü + yolu) dizini.|  
|Proje dosyası adı|$(ProjFileName)|Geçerli projenin dosya adını (sürücü yolu + dosya adı).|  
|Çözüm dizini|$(SolutionDir)|Geçerli çözüme (sürücü + yolu) dizini.|  
|Çözüm dosyası adı|$(SolutionFileName)|Geçerli çözümün dosya adını (sürücü yolu + dosya adı).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ Derleme Araçları](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)








