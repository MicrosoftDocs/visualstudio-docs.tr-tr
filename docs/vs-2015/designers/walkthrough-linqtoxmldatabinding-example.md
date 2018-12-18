---
title: 'İzlenecek yol: LinqToXmlDataBinding örneği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c69c69cfed53b0080614984853b3128908c2e89
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893656"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>İzlenecek yol: LinqToXmlDataBinding örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda LinqToXmlDataBinding örneği ve daha ilgi çekici, iki birincil kaynak dosyaların içeriğini, L2DBForm.xaml ve L2DBForm.xaml.cs bazıları açıklanmaktadır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzu okumadan önce derleme ve açıklandığı gibi LinqToXmlDataBinding programı çalıştırın öneririz [nasıl yapılır: oluşturma ve çalıştırma LinqToXmlDataBinding örneği](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşan bir Windows Presentation Foundation (WPF) uygulaması C# ve XAML kaynak dosyaları LinqToXmlDataBinding programdır. Kitap listesi tanımlar ve görüntüleme, ekleme, silme ve bu girişleri düzenlemek kullanıcının sağlayan gömülü bir XML belgesi içeriyor. Bunu, aşağıdaki iki birincil kaynak dosyalardan oluşur:  
  
- L2DBForm.XAML ana penceresinin kullanıcı arabirimi (UI) XAML bildirimi kodunu içerir. Ayrıca, bir veri sağlayıcısı ve kitap listeleri için katıştırılmış XML belgesi tanımlayan bir pencere kaynak bölümü içerir.  
  
- L2DBForm.xaml.cs başlatma ve kullanıcı Arabirimi ile ilişkili olay işleme yöntemleri içerir.  
  
  Ana pencereyi aşağıdaki dört dikey UI bölümlere ayrılmıştır:  
  
- **XML** ham XML kaynağını katıştırılmış kitap listesi görüntüler.  
  
- **Kitap listesi** defteri girdileri standart metin olarak görüntüler ve seçin ve tek tek girişleri silmek sağlar.  
  
- **Seçili kitap Düzenle** seçili rehberi girişiyle ilişkili değerlerini düzenlemek kullanıcının sağlar.  
  
- **Yeni kitabı ekleme** kullanıcı tarafından girilen değerleri temel alarak yeni bir kitap giriş oluşturulmasını sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[L2DBForm.xaml Kaynak Kodu](../designers/l2dbform-xaml-source-code.md)|İçeriği ve XAML kodu dosyasında L2DBForm.xaml açıklamasını içerir.|  
|[L2DBForm.xaml.cs Kaynak Kodu](../designers/l2dbform-xaml-cs-source-code.md)|İçeriği ve C# kaynak kodu dosyasında L2DBForm.xaml.cs açıklamasını içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML örneği kullanarak WPF verilerini bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Nasıl Yapılır: LinqToXmlDataBinding Oluşturma ve Çalıştırma Örneği](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)



