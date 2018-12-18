---
title: 'Nasıl yapılır: bir hizmet sağlamak | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2408eace3ecea447c9b49ff17c729e3f4661b5d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942562"
---
# <a name="how-to-provide-a-service"></a>Nasıl yapılır: bir hizmeti sağlama
VSPackage diğer VSPackages kullanan hizmetleri sağlar. Bir hizmeti sağlamak amacıyla bir VSPackage hizmeti Visual Studio ile kaydedin ve hizmet eklemeniz gerekir.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Sınıfı her ikisini birden uygular <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> ve <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> İsteğe bağlı hizmetler sağlayan bir geri çağırma yöntemleri içerir.  
  
 Hizmetleri hakkında daha fazla bilgi için bkz. [hizmet temel bileşenleri](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  VSPackage kaldırılmak üzere olduğunda, Visual Studio tüm istekler VSPackage sağladığı hizmetler için teslim edilinceye kadar bekler. Bu hizmetler için yeni istek izin vermez. Değil açıkça çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> kaldırma hizmet iptal için yöntemi.  
  
## <a name="implement-a-service"></a>Bir hizmet ekleme  
  
1. VSIX projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#**  >  **Genişletilebilirlik** > **VSIX projesi**).  
  
2. Bir VSPackage'ı projeye ekleyin. ' Nde proje düğümüne seçin **Çözüm Gezgini** tıklatıp **Ekle** > **yeni öğe** > **Visual C# öğeleri**  >  **Genişletilebilirlik** > **Visual Studio paket**.  
  
3. Bir hizmeti uygulamak için üç tür oluşturmanız gerekir:  
  
   - Hizmeti tanımlayan bir arabirim. Bu arabirimlerin çoğu boştur, diğer bir deyişle, bunlar hiçbir yöntemleri vardır.  
  
   - Hizmet arabirimi açıklayan bir arabirim. Bu arabirim, uygulanacak yöntemleri içerir.  
  
   - Hem hizmet hem de hizmet arabirimi uygulayan bir sınıf.  
  
     Aşağıdaki örnek, üç temel bir uygulamasını gösterir. Hizmet sınıfının oluşturucusu, hizmet sağlayıcısı ayarlamanız gerekir.  
  
   ```csharp  
   public class MyService : SMyService, IMyService  
   {  
       private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
       private string myString;  
       public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
       {  
           Trace.WriteLine(  
                  "Constructing a new instance of MyService");  
           serviceProvider = sp;  
       }  
       public void Hello()  
       {  
           myString = "hello";  
       }  
       public string Goodbye()  
       {  
          return "goodbye";  
       }  
   }  
   public interface SMyService  
   {  
   }  
   public interface IMyService  
   {  
       void Hello();  
       string Goodbye();  
   }  
  
   ```  
  
### <a name="register-a-service"></a>Bir hizmeti kaydedin  
  
1.  Bir hizmeti kaydetmek için ekleme <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> hizmeti sağlayan VSPackage'ı için. Aşağıda bir örnek verilmiştir:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Bu öznitelik kaydeder `SMyService` Visual Studio ile.  
  
    > [!NOTE]
    >  Aynı ada sahip başka bir hizmete yerini alan bir hizmeti kaydetmek için kullanın <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Not, yalnızca bir geçersiz kılma bir hizmetin izin verilir.  
  
### <a name="add-a-service"></a>Hizmet ekleme  
  
1.  VSPackage'ı Başlatıcı hizmet ekleyin ve hizmetleri oluşturmak için bir geri çağırma yöntemi ekleyin. Değişiklik yapmak için işte <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  , Oluşturma ve hizmet döndürür veya oluşturulamıyor yoksa null geri arama yöntemi uygular.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio, bir hizmet isteği reddedebilir. VSPackage'ı başka bir hizmet zaten sağlıyorsa, bunu yapar.  
  
3.  Artık hizmet alma ve onun yöntemlerini kullanın. Başlatıcı hizmetini kullanarak aşağıdaki örnekte gösterilmiştir, ancak herhangi bir hizmet kullanmak istediğiniz hizmet alabilirsiniz.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     Değerini `helloString` "Hello" olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)   
 [Hizmetleri sağlamak ve kullanın](../extensibility/using-and-providing-services.md)   
 [Hizmet temel bileşenleri](../extensibility/internals/service-essentials.md)
