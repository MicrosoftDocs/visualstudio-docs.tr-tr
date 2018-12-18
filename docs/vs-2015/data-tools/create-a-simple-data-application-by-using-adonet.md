---
title: ADO.NET kullanarak basit veri uygulaması oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4754cad05858ed48fd421301b4b0f1d2c569a926
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824288"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir veritabanındaki verileri işleyen bir uygulama oluşturduğunuzda, bu tür bağlantı dizeleri tanımlama, veri ekleme ve saklı yordamları çalıştırma temel görevleri gerçekleştirin. Bu konuyu takip ederek, Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir "veriler üzerinden formlar" Windows Forms uygulaması dahilinden bir veritabanıyla etkileşime nasıl bulabilir.  Tüm .NET veri teknolojilerini — LINQ to SQL ve Entity Framework veri kümeleri dahil olmak üzere; sonuç olarak, bu makalede gösterilen bu çok benzer adımları gerçekleştirin.  
  
 Bu makalede, çok hızlı bir şekilde bir veritabanından veri almak için basit bir yol gösterir. Uygulamanızın veri Önemsiz olmayan yollarla değiştirmek ve veritabanını güncellemek gerekiyorsa, Entity Framework ve veri kullanıcı arabirimi denetimleri için temel alınan verilerde yapılan değişiklikler otomatik olarak eşitlenecek bağlama kullanarak düşünmelisiniz.  
  
> [!IMPORTANT]
>  Kodu basit tutmak için üretime hazır özel durum işleme içermez.  
  
 **Bu konudaki**  
  
-   [Örnek veritabanı kurma](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
-   [Formlar oluşturun ve denetimler ekleme](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
-   [Bağlantı dizesi Store](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
-   [Bağlantı dizesi alma](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
-   [Formlar için kodu yazın](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
-   [Uygulamanızı test edin](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Uygulama oluşturmak için gerekir:  
  
- Visual Studio Community sürümü.  
  
- SQL Server Express LocalDB.  
  
- İçindeki adımları izleyerek oluşturduğunuz küçük örnek veritabanı [bir komut dosyası kullanarak SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md).  
  
- Bunu ayarladıktan sonra veritabanı için bağlantı dizesi. Açarak bu değeri bulabilirsiniz **SQL Server Nesne Gezgini**, veritabanı için kısayol menüsünü açarak, seçerek **özellikleri**ve ardından kaydırmayı **ConnectionString** özelliği.  
  
  Bu konuda, Visual Studio IDE temel işlevsellikle biliyor ve bir Windows Forms uygulaması oluşturma, forms düğme ve diğer denetimleri formlarda, put, bu proje için bu denetimleri ve olay özelliklerini ayarlamak ekleyin, varsayılır . Bu görevler konusunda deneyimli değilseniz, tamamlamanızı öneririz [Visual C# ve Visual Basic ile çalışmaya başlama](../ide/getting-started-with-visual-csharp-and-visual-basic.md) bu konuya başlamadan önce.  
  
##  <a name="BKMK_setupthesampledatabase"></a> Örnek veritabanı kurma  
 Bu izlenecek yol için örnek veritabanı, müşteri ve sipariş tablolarından oluşur. Tabloları başlangıçta herhangi bir veri içermez, ancak oluşturacağınız uygulamayı çalıştırdığınızda veri eklersiniz. Veritabanının beş basit saklı yordamı de var. [Bir komut dosyası kullanarak SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md) tabloları, birincil ve yabancı anahtarları, kısıtlamaları ve saklı yordamları oluşturan bir Transact-SQL betiği içerir.  
  
##  <a name="BKMK_createtheformsandaddcontrols"></a> Formlar oluşturun ve denetimler ekleme  
  
1. Bir Windows Forms uygulaması projesi oluşturun ve SimpleDataApp adlandırın.  
  
    Visual Studio projeyi ve Form1 adıyla boş bir Windows formu dahil olmak üzere birçok dosyayı oluşturur.  
  
2. Üç sahip olacak şekilde iki Windows formunu projenize ekleyin ve ardından bunları aşağıdaki adlar verin:  
  
   -   Gezinti  
  
   -   NewCustomer  
  
   -   FillOrCancel  
  
3. Her form için aşağıdaki resimlerde metin kutularını, düğmeleri ve görüntülenen diğer denetimleri ekleyin. Her denetim için tabloların açıkladığı özellikleri ayarlayın.  
  
   > [!NOTE]
   >  Grup kutusu ve etiket denetimleri netlik kazandırır ancak kodda kullanılmaz.  
  
   **Gezinti formu**  
  
   ![Gezinti iletişim kutusu](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Gezinti formu için denetimler|Özellikler|  
|--------------------------------------|----------------|  
|Düğme|Ad = btnGoToAdd|  
|Düğme|Ad = btnGoToFillOrCancel|  
|Düğme|Ad = btnExit|  
  
 **NewCustomer formu**  
  
 ![Yeni bir müşteri ekleyin ve sipariş](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|NewCustomer formu için denetimler|Özellikler|  
|---------------------------------------|----------------|  
|TextBox|Ad = txtCustomerName|  
|TextBox|Ad = Txtcustomerıd<br /><br /> Salt okunur = True|  
|Düğme|Ad = btnCreateAccount|  
|NumericUpdown|OndalıkBasamaklar = 0<br /><br /> En fazla = 5000<br /><br /> Ad = numOrderAmount|  
|DateTimePicker|Biçim = kısa<br /><br /> Ad = dtpOrderDate|  
|Düğme|Ad = btnPlaceOrder|  
|Düğme|Ad = btnAddAnotherAccount|  
|Düğme|Ad = btnAddFinish|  
  
 **FillOrCancel formu**  
  
 ![dolgu veya Sipariş İptal](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|FillOrCancel formu için denetimler|Özellikler|  
|----------------------------------------|----------------|  
|TextBox|Ad = Txtorderıd|  
|Düğme|Ad = Btnfindbyorderıd|  
|DateTimePicker|Biçim = kısa<br /><br /> Ad = dtpFillDate|  
|DataGridView|Ad = dgvCustomerOrders<br /><br /> Salt okunur = True<br /><br /> RowHeadersVisible = yanlış|  
|Düğme|Ad = btnCancelOrder|  
|Düğme|Ad = btnFillOrder|  
|Düğme|Ad = btnFinishUpdates|  
  
##  <a name="BKMK_storetheconnectionstring"></a> Bağlantı dizesi Store  
 Uygulamanız veritabanına bir bağlantı açmaya çalıştığında, uygulamanızın bağlantı dizesine erişimi olmalıdır. Dizeyi her bir formda el ile girmekten kaçınmak için uygulama yapılandırma dosyasını projenize dize depolamak ve yöntem uygulamanızdaki herhangi bir formdan çağrıldığında dizeyi döndüren bir yöntem oluşturma.  
  
 Bağlantı dizesinde bulabilirsiniz **SQL Server Nesne Gezgini** veritabanını sağ tıklatın, seçerek **özellikleri**ve ardından ConnectionString özelliği bulma. Dize seçmek için CTRL + A tuş bileşimini kullanın.  
  
1.  İçinde **Çözüm Gezgini**seçin **özellikleri** proje tıklayın ve ardından düğümünde **Settings.settings**.  
  
2.  İçinde **adı** sütun girin `connString`.  
  
3.  İçinde **türü** listesinden **(bağlantı dizesi)**.  
  
4.  İçinde **kapsam** listesinden **uygulama**.  
  
5.  İçinde **değer** sütunu (olmadan herhangi bir dış tırnak işaretleri) bağlantı dizenizi girin ve ardından değişikliklerinizi kaydedin.  
  
> [!NOTE]
>  Gerçek bir uygulamada, bağlantı dizesini açıklandığı gibi güvenli bir saklamalısınız [bağlantı dizeleri ve yapılandırma dosyalarını](http://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).  
  
##  <a name="BKMK_retrievetheconnectionstring"></a> Bağlantı dizesi alma  
  
1.  Menü çubuğunda, seçin **proje** > **Başvuru Ekle**ve ardından System.Configuration.dll dosyasına bir başvuru ekleyin.  
  
2.  Menü çubuğunda, seçin **proje** > **sınıfı Ekle** projenize bir sınıf dosyası ekleyin ve ardından dosya adı `Utility`.  
  
     Visual Studio dosyayı oluşturur ve görüntüler **Çözüm Gezgini**.  
  
3.  Yardımcı dosyada, yer tutucu kodunu aşağıdaki kodla değiştirin. Kodun bölümlerini tanımlayan numaralandırılmış açıklamalara (Util - önekiyle başlayan bulunur) dikkat edin. Kodu izleyen tablo anahtar noktaları çağırır.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    //Util-1 More namespaces.  
    using System.Configuration;   
  
    namespace SimpleDataApp  
    {  
        internal class Utility  
        {  
  
            //Get the connection string from App config file.  
            internal static string GetConnectionString()  
            {  
                //Util-2 Assume failure.  
                string returnValue = null;  
  
                //Util-3 Look for the name in the connectionStrings section.  
                ConnectionStringSettings settings =  
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];  
  
                //If found, return the connection string.  
                if (settings != null)  
                    returnValue = settings.ConnectionString;  
  
                return returnValue;  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Linq  
    Imports System.Text  
    Imports System.Threading.Tasks  
    ' Util-1 More namespaces.  
    Imports System.Configuration  
  
    Namespace SimpleDataApp  
        Friend Class Utility  
  
            ' Get connection string from App config file.  
            Friend Shared Function GetConnectionString() As String  
  
                ' Util-2 Assume failure.  
                Dim returnValue As String = Nothing  
  
                ' Util-3 Look for the name in the connectionStrings section.  
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")  
  
                ' If found, return the connection string.  
                If settings IsNot Nothing Then  
                    returnValue = settings.ConnectionString  
                End If  
  
                Return returnValue  
            End Function  
        End Class  
    End Namespace  
    ```  
  
    |Yorum|Açıklama|  
    |-------------|-----------------|  
    |Kullanımı-1|Ekleme `System.Configuration` ad alanı.|  
    |Kullanımı-2|Bir değişken tanımlayın `returnValue`ve kendisine başlatma `null` (C#) veya `Nothing` (Visual Basic).|  
    |Kullanımı-3|Girdiğiniz olsa bile `connString` bağlantı dizesinin adı olarak **özellikleri** penceresinde belirtmelisiniz `"SimpleDataApp.Properties.Settings.connString"` (C#) veya `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) kod.|  
  
##  <a name="BKMK_writethecodefortheforms"></a> Formlar için kodu yazın  
 Bu bölüm, neleri her bir form mu ve formları oluşturan kodu gösterir kısa genel bakış bilgileri içerir. Numaralandırılmış açıklamalar kod bölümlerini tanımlar.  
  
### <a name="navigation-form"></a>Gezinti formu  
 Uygulamayı çalıştırdığınızda Gezinti formu açılır. **Hesap Ekle** düğmesi NewCustomer formunu açar. **Siparişleri doldurun veya iptal** düğmesi FillOrCancel formunu açar. **Çıkış** düğmesi uygulamayı kapatır.  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti biçimini başlangıç biçimi yapın  
 C# kullanıyorsanız, **Çözüm Gezgini**, program.cs dosyasını açın ve ardından değiştirmek `Application.Run` satırını şu şekilde: `Application.Run(new Navigation());`  
  
 İçinde Visual Basic kullanıyorsanız, **Çözüm Gezgini**açın **özellikleri** penceresinde **uygulama** sekmesine tıklayın ve ardından  **SimpleDataApp.Navigation** içinde **başlangıç formu** listesi.  
  
#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma  
 Boş olay işleyici yöntemi oluşturmak için formdaki üç düğme çift tıklayın.  
  
#### <a name="create-code-for-navigation"></a>Gezinti için kod oluşturun  
 Gezinti formunda, mevcut kodu şu kodla değiştirin.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
  
namespace SimpleDataApp  
{  
    public partial class Navigation : Form  
    {  
        public Navigation()  
        {  
            InitializeComponent();  
        }  
  
        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        private void btnGoToAdd_Click(object sender, EventArgs e)  
        {  
            Form frm = new NewCustomer();  
            frm.Show();  
        }  
  
        //Open the FillorCancel form as a dialog box.  
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)  
        {  
            Form frm = new FillOrCancel();  
            frm.ShowDialog();  
        }  
  
        //Close the application, not just the Navigation form.  
        private void btnExit_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
  
Namespace SimpleDataApp  
    Partial Public Class Navigation  
        Inherits Form  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.  
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click  
            Dim frm As Form = New NewCustomer()  
            frm.Show()  
        End Sub  
  
        ' Open the FillorCancel form as a dialog box.  
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click  
            Dim frm As Form = New FillOrCancel()  
            frm.ShowDialog()  
        End Sub  
  
        ' Close the application, not just the Navigation form.  
        Private Sub btnExit_Click() Handles btnExit.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
  
```  
  
### <a name="newcustomer-form"></a>NewCustomer formu  
 Ne zaman bir müşteri adı girin ve ardından **hesabı oluştur** düğmesi NewCustomer formu bir müşteri hesabı oluşturur ve SQL Server, yeni hesap numarası olarak bir IDENTITY değeri döndürür. Ardından yeni hesap için bir miktar ve sipariş tarihi belirterek ve seçerek Sipariş **sipariş** düğmesi.  
  
#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma  
 Boş bir tıklama oluşturma formdaki her düğme için olay işleyicisi.  
  
#### <a name="create-code-for-newcustomer"></a>NewCustomer için kod oluşturun  
 NewCustomer formuna aşağıdaki kodu ekleyin. Koddan sonra numaralı açıklamaları ve tabloyu kullanarak her kod bloğu boyunca ilerleyin.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//NC-1 More namespaces.  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class NewCustomer : Form  
    {  
        //NC-2 Storage for IDENTITY values returned from database.  
        private int parsedCustomerID;  
        private int orderID;  
  
        //NC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public NewCustomer()  
        {  
            InitializeComponent();  
        }  
  
        //NC-4 Create account.  
        private void btnCreateAccount_Click(object sender, EventArgs e)  
        {  
            //NC-5 Set up and run stored procedure only if Customer Name is present.  
            if (isCustomerName())  
            {  
  
                //NC-6 Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;  
  
                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));  
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;  
  
                //NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;  
  
                //NC-10 try-catch-finally  
                try  
                {  
                    //NC-11 Open the connection.  
                    conn.Open();  
  
                    //NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery();  
  
                    //NC-13 Customer ID is an IDENTITY value from the database.   
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;  
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);  
  
                }  
                catch  
                {  
                    //NC-14 A simple catch.  
  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.");  
                }  
                finally  
                {  
                    //NC-15 Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-16 Verify that Customer Name is present.  
        private bool isCustomerName()  
        {  
            if (txtCustomerName.Text == "")  
            {  
                MessageBox.Show("Please enter a name.");  
                return false;  
            }  
            else  
            {  
                return true;  
            }  
        }  
  
        //NC-17 Place order.  
        private void btnPlaceOrder_Click(object sender, EventArgs e)  
        {  
            //NC-18 Set up and run stored procedure only if required input is present.  
            if (isPlaceOrderReady())  
            {  
                // Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //NC-19 Create SqlCommand and identify it as a stored procedure.  
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);  
                cmdNewOrder.CommandType = CommandType.StoredProcedure;  
  
                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));  
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;  
  
                //NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));  
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;  
  
                //NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));  
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;  
  
                //NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));  
                cmdNewOrder.Parameters["@Status"].Value = "O";  
  
                //NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));  
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;  
  
                //try-catch-finally  
                try  
                {  
                    //Open connection.  
                    conn.Open();  
  
                    //Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery();  
  
                    //NC-25 Display the order number.  
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;  
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("Order could not be placed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //NC-26 Verify that order data is ready.  
        private bool isPlaceOrderReady()  
        {  
            // Verify that CustomerID is present.  
            if (txtCustomerID.Text == "")  
            {  
                MessageBox.Show("Please create customer account before placing order.");  
                return false;  
            }  
  
            // Verify that Amount isn't 0.   
            else if ((numOrderAmount.Value < 1))  
            {  
                MessageBox.Show("Please specify an order amount.");  
                return false;  
            }  
            else  
            {  
                // Order can be submitted.  
                return true;  
            }  
        }  
  
        //NC-27 Reset the form for another new account.  
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)  
        {  
            this.ClearForm();  
        }  
  
        //NC-28 Clear values from controls.  
        private void ClearForm()  
        {  
            txtCustomerName.Clear();  
            txtCustomerID.Clear();  
            dtpOrderDate.Value = DateTime.Now;  
            numOrderAmount.Value = 0;  
            this.parsedCustomerID = 0;  
        }  
  
        //NC-29 Close the form.  
        private void btnAddFinish_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
  
    }  
}  
  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' NC-1 More namespaces.  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class NewCustomer  
        Inherits Form  
  
        ' NC-2 Storage for IDENTITY values returned from database.  
        Private parsedCustomerID As Integer  
        Private orderID As Integer  
  
        ' NC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' NC-4 Create account.  
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click  
  
            ' NC-5 Set up and run stored procedure only if Customer Name is present.  
            If isCustomerName() Then  
  
                ' NC-6 Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.  
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)  
                cmdNewCustomer.CommandType = CommandType.StoredProcedure  
  
                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))  
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text  
  
                ' NC-9 Add output parameter.  
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output  
  
                ' NC-10 try-catch-finally  
                Try  
                    ' NC-11 Open the connection.  
                    conn.Open()  
  
                    ' NC-12 Run the stored procedure.  
                    cmdNewCustomer.ExecuteNonQuery()  
  
                    ' NC-13 Customer ID is an IDENTITY value from the database.   
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)  
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)  
  
                Catch  
                    ' NC-14 A simple catch.  
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")  
                Finally  
                    ' NC-15 Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-16 Verify that Customer Name is present.  
        Private Function isCustomerName() As Boolean  
            If txtCustomerName.Text = "" Then  
                MessageBox.Show("Please enter a name.")  
                Return False  
            Else  
                Return True  
            End If  
        End Function  
  
        ' NC-17 Place order.  
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click  
  
            ' NC-18 Set up and run stored procedure only if necessary input is present.  
            If isPlaceOrderReady() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' NC-19 Create SqlCommand and identify it as a stored procedure.  
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)  
                cmdNewOrder.CommandType = CommandType.StoredProcedure  
  
                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))  
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID  
  
                ' NC-21 @OrderDate.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))  
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value  
  
                ' NC-22 @Amount.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))  
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value  
  
                ' NC-23 @Status. For a new order, the status is always O (open).  
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))  
                cmdNewOrder.Parameters("@Status").Value = "O"  
  
                ' NC-24 Add return value for stored procedure, which is orderID.  
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))  
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue  
  
                ' try-catch-finally  
                Try  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the stored procedure.  
                    cmdNewOrder.ExecuteNonQuery()  
  
                    ' NC-25 Display the order number.  
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)  
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")  
  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("Order could  not be placed.")  
  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' NC-26 Verify that order data is ready.  
        Private Function isPlaceOrderReady() As Boolean  
  
            ' Verify that CustomerID is present.  
            If txtCustomerID.Text = "" Then  
                MessageBox.Show("Please create customer account before placing order.")  
                Return False  
  
                ' Verify that Amount isn't 0.   
            ElseIf (numOrderAmount.Value < 1) Then  
  
                MessageBox.Show("Please specify an order amount.")  
                Return False  
            Else  
                ' Order can be submitted.  
                Return True  
            End If  
        End Function  
  
        ' NC-27 Reset the form for another new account.  
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click  
            Me.ClearForm()  
        End Sub  
  
        ' NC-28 Clear values from controls.  
        Private Sub ClearForm()  
            txtCustomerName.Clear()  
            txtCustomerID.Clear()  
            dtpOrderDate.Value = DateTime.Now  
            numOrderAmount.Value = 0  
            Me.parsedCustomerID = 0  
        End Sub  
  
        ' NC-29 Close the form.  
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click  
            Me.Close()  
        End Sub  
  
    End Class  
End Namespace  
```  
  
|Yorum|Açıklama|  
|-------------|-----------------|  
|NC-1|Ekleme `System.Data.SqlClient` ve `System.Configuration` ad alanları listesi.|  
|NC-2|Bildirme `parsedCustomerID` ve `orderID` daha sonra kullanacağınız değişkenleri.|  
|NC-3|Çağrı `GetConnectionString` uygulama yapılandırma dosyasından bağlantı dizesini alın ve değeri depolamak için yöntem `connstr` string değişkeni.|  
|NC-4|Tıklama olay işleyicisine kod ekleyin `btnCreateAccount` düğmesi.|  
|NC-5|Çağrısını sarmalamak `isCustomerName` Click olay kodunun etrafında böylece `uspNewCustomer` yalnızca bir müşteri adı bulunduğunda çalışır.|  
|NC-6|Oluşturma bir `SqlConnection` nesne (`conn`) ve bağlantı dizesini geçirin `connstr`.|  
|NC-7|Oluşturma bir `SqlCommand` nesnesi `cmdNewCustomer`.<br /><br /> -Belirtin `Sales.uspNewCustomer` olarak çalıştırmak için saklı yordam.<br />-Kullanma `CommandType` komutu bir saklı yordam olduğunu belirtmek için özellik.|  
|NC-8|Ekleme `@CustomerName` saklı yordamdan giriş parametresi.<br /><br /> -Parametre ekleyin `Parameters` koleksiyonu.<br />-Kullanma `SqlDbType` parametre türünü nvarchar(40) olarak belirtmek için sabit listesi.<br />-Belirtin `txtCustomerName.Text` kaynağı olarak.|  
|NC-9|Saklı yordamdan çıkış parametresi ekleyin.<br /><br /> -Parametre ekleyin `Parameters` koleksiyonu.<br />-Kullanma `ParameterDirection.Output` parametreyi çıktı olarak tanımlamak için.|  
|NC-10|Bağlantıyı açmak, saklı yordamı çalıştırın, özel durumları işlemek ve sonra bağlantıyı kapatmak için bir Try-Catch-Finally bloğu ekleyin.|  
|NC-11|Bağlantıyı açın (`conn`) NC-6'da oluşturduğunuz.|  
|NC-12|Kullanım `ExecuteNonQuery` yöntemi `cmdNewCustomer` çalıştırılacak `Sales.uspNewCustomer` saklı yordamı. Bu saklı yordamı çalıştığında bir `INSERT` deyimi, bu sorgu değil.|  
|NC-13|`@CustomerID` Değeri veritabanından IDENTITY değeri olarak döndürülür. Bir tamsayı olduğu için içinde görüntülemek için bir dizeye dönüştürmeniz gerekir **Müşteri Kimliği** metin kutusu.<br /><br /> -Bu, bildirilen `parsedCustomerID` NC-2.<br />-Store `@CustomerID` değerini `parsedCustomerID` daha sonra kullanmak için.<br />-Döndürülen müşteri Kimliğini bir dizeye Dönüştür ve içine Ekle `txtCustomerID.Text`.|  
|NC-14|Bu örnek, bir basit (üretim kalitesinde olmayan) catch yan tümcesi ekleyin.|  
|NC-15|Kullanmayı bitirdikten sonra böylece bağlantı havuzuna bırakılmasını her zaman bir bağlantıyı kapatın. Bkz: [SQL Server Connection Pooling (ADO.NET)](http://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|  
|NC-16|Bir müşteri adının mevcut olduğunu doğrulamak için bir yöntem tanımlayın.<br /><br /> -Metin kutusu boş ise, bir ileti görüntüler ve dönüş `false`, hesabı oluşturmak için bir ad gereklidir.<br />-Metin kutusu boş değilse, dönüş `true`.|  
|NC-17|Tıklama olay işleyicisine kod ekleyin `btnPlaceOrder` düğmesi.|  
|NC-18|Çağrısını sarmalamak `isPlaceOrderReady` etrafında `btnPlaceOrder_Click` olay kodu böylece `uspPlaceNewOrder` gerekli giriş mevcut olmadığında çalışmasın.|  
|NC-19 ila NC-25|Bu bölümler için eklediğiniz koda benzer `btnCreateAccount_Click` olay işleyicisi.<br /><br /> -NC-19. Oluşturma `SqlCommand` nesnesi `cmdNewOrder`, belirtin `Sales.uspPlaceOrder` saklı yordam olarak.<br />-NC-20 ila NC-23 saklı yordam için giriş parametreleridir.<br />-NC-24. `@RC` veritabanından oluşturulan sipariş kimliği bir dönüş değeri içerir. Bu parametrenin yönü olarak belirtilen `ReturnValue`.<br />-NC-25. Sipariş Kimliği değerini Store `orderID` NC-2 ve görüntüleme değeri bir ileti kutusu içinde bildirilen değişken.|  
|NC-26|Bir müşteri Kimliğinin var olduğunu ve bir süre içinde belirtilen doğrulamak için bir yöntem tanımlayın `numOrderAmount`.|  
|NC-27|Çağrı `ClearForm` yönteminde `btnAddAnotherAccount` tıklama olay işleyicisi.|  
|NC-28|Oluşturma `ClearForm` başka bir müşteri eklemek istiyorsanız formdan değerleri temizlemek için yöntemi.|  
|NC29|NewCustomer formunu kapatın ve gezinti formuna odak döndürür.|  
  
### <a name="fillorcancel-form"></a>FillOrCancel formu  
 FillorCancel formu siparişi bir sipariş kimliği girdiğinizde ve seçtiğiniz zaman döndürmek için bir sorgu çalıştırır **siparişi Bul** düğmesi. Döndürülen satır salt okunur verileri kılavuz çizgilerinde görüntülenir. Seçerseniz, siparişi iptal edilmiş (X) olarak işaretleyebilirsiniz **siparişi iptal et** düğme veya işaretleyebilirsiniz sırası dolu (F) seçerseniz **siparişi** düğmesi. Seçerseniz **siparişi Bul** düğmesini tekrar, güncelleştirilen satır görüntülenir.  
  
#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma  
 Boş oluşturmak form üzerindeki dört düğme için olay işleyicileri'a tıklayın.  
  
#### <a name="create-code-for-fillorcancel"></a>FillOrCancel için kod oluşturun  
 FillOrCancel formuna aşağıdaki kodu ekleyin. Numaralı açıklamaları ve kodu izleyen tabloyu kullanarak kod blokları boyunca ilerleyin.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows.Forms;  
//FC-1 More namespaces.  
using System.Text.RegularExpressions;  
using System.Data.SqlClient;  
using System.Configuration;  
  
namespace SimpleDataApp  
{  
    public partial class FillOrCancel : Form  
    {  
        //FC-2 Storage for OrderID.  
        private int parsedOrderID;  
  
        //FC-3 Specify a connection string.  
        string connstr = SimpleDataApp.Utility.GetConnectionString();  
  
        public FillOrCancel()  
        {  
            InitializeComponent();  
        }  
  
        //FC-4 Find an order.  
        private void btnFindByOrderID_Click(object sender, EventArgs e)  
        {  
            //FC-5 Prepare the connection and the command.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Define a query string that has a parameter for orderID.  
                string sql = "select * from Sales.Orders where orderID = @orderID";  
  
                //Create a SqlCommand object.  
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);  
  
                //Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;  
  
                //try-catch-finally  
                try  
                {  
                    //FC-6 Run the command and display the results.  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the command by using SqlDataReader.  
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();  
  
                    //Create a data table to hold the retrieved data.  
                    DataTable dataTable = new DataTable();  
  
                    //Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr);  
  
                    //Display the data from the data table in the data grid view.  
                    this.dgvCustomerOrders.DataSource = dataTable;  
  
                    //Close the SqlDataReader.  
                    rdr.Close();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-7 Cancel an order.  
        private void btnCancelOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                // Create command and identify it as a stored procedure.  
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;  
  
                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                // try-catch-finally  
                try  
                {  
                    // Open the connection.  
                    conn.Open();  
  
                    // Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery();  
                }  
                // A simple catch.  
                catch  
                {  
                    MessageBox.Show("The cancel operation was not completed.");  
                }  
                finally  
                {  
                    //Close connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-8 Fill an order.  
        private void btnFillOrder_Click(object sender, EventArgs e)  
        {  
            //Set up and run stored procedure only if OrderID is ready.  
            if (isOrderID())  
            {  
                //Create the connection.  
                SqlConnection conn = new SqlConnection(connstr);  
  
                //Create command and identify it as a stored procedure.  
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);  
                cmdFillOrder.CommandType = CommandType.StoredProcedure;  
  
                // Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));  
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;  
  
                //Add the second input parameter.  
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));  
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;  
  
                //try-catch-finally  
                try  
                {  
                    //Open the connection.  
                    conn.Open();  
  
                    //Run the cmdFillOrder command.  
                    cmdFillOrder.ExecuteNonQuery();  
                }  
                catch  
                {  
                    //A simple catch.  
                    MessageBox.Show("The fill operation was not completed.");  
                }  
                finally  
                {  
                    //Close the connection.  
                    conn.Close();  
                }  
            }  
        }  
  
        //FC-9 Verify that OrderID is ready.  
        private bool isOrderID()  
        {  
  
            //Check for input in the Order ID text box.  
            if (txtOrderID.Text == "")  
            {  
                MessageBox.Show("Please specify the Order ID.");  
                return false;  
            }  
  
            // Check for characters other than integers.  
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))  
            {  
               //Show message and clear input.  
                MessageBox.Show("Please specify integers only.");  
                txtOrderID.Clear();  
                return false;  
            }  
            else  
            {  
                //Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text);  
                return true;  
            }  
        }  
  
        //Close the form.  
        private void btnFinishUpdates_Click(object sender, EventArgs e)  
        {  
            this.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.ComponentModel  
Imports System.Data  
Imports System.Drawing  
Imports System.Linq  
Imports System.Text  
Imports System.Threading.Tasks  
Imports System.Windows.Forms  
' FC-1 More namespaces.  
Imports System.Text.RegularExpressions  
Imports System.Data.SqlClient  
Imports System.Configuration  
  
Namespace SimpleDataApp  
    Partial Public Class FillOrCancel  
        Inherits Form  
        ' FC-2 Storage for OrderID.  
        Private parsedOrderID As Integer  
  
        ' FC-3 Specify a connection string.  
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        ' FC-4 Find an order.  
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click  
  
            ' FC-5 Prepare the connection and the command.  
  
            If isOrderID() Then  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Define the query string that has a parameter for orderID.  
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"  
  
                ' Create a SqlCommand object.  
                Dim cmdOrderID As New SqlCommand(sql, conn)  
  
                ' Define the @orderID parameter and its value.  
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' FC-6 Run the command and display the results.  
                    ' Open connection.  
                    conn.Open()  
  
                    ' Run the command by using SqlDataReader.  
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()  
  
                    ' Create a data table to hold the retrieved data.  
                    Dim dataTable As New DataTable()  
  
                    ' Load the data from SqlDataReader into the data table.  
                    dataTable.Load(rdr)  
  
                    ' Display the data from the data table in the data grid view.  
                    Me.dgvCustomerOrders.DataSource = dataTable  
  
                    ' Close the SqlDataReader.  
                    rdr.Close()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The requested order could not be loaded into the form.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-7 Cancel an order.  
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create the command and identify it as a stored procedure.  
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)  
                cmdCancelOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdCancelOrder command.  
                    cmdCancelOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The cancel operation was not completed.")  
                Finally  
                    ' Close connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-8 Fill an order.  
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click  
  
            ' Set up and run stored procedure only if OrderID is ready.  
            If isOrderID() Then  
  
                ' Create the connection.  
                Dim conn As New SqlConnection(connstr)  
  
                ' Create command and identify it as a stored procedure.  
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)  
                cmdFillOrder.CommandType = CommandType.StoredProcedure  
  
                ' Add input parameter from the stored procedure.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))  
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID  
  
                ' Add second input parameter.  
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))  
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value  
  
                ' try-catch-finally  
                Try  
                    ' Open the connection.  
                    conn.Open()  
  
                    ' Run the cmdFillOrder command.   
                    cmdFillOrder.ExecuteNonQuery()  
                Catch  
                    ' A simple catch.  
                    MessageBox.Show("The fill operation was not completed.")  
                Finally  
                    ' Close the connection.  
                    conn.Close()  
                End Try  
            End If  
        End Sub  
  
        ' FC-9 Verify that OrderID is ready.  
        Private Function isOrderID() As Boolean  
  
            ' Check for input in the Order ID text box.  
            If txtOrderID.Text = "" Then  
                MessageBox.Show("Please specify the Order ID.")  
                Return False  
  
                ' Check for characters other than integers.  
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then  
  
                ' Show message and clear input.  
                MessageBox.Show("Please specify integers only.")  
                txtOrderID.Clear()  
                Return False  
  
            Else  
                ' Convert the text in the text box to an integer to send to the database.  
                parsedOrderID = Int32.Parse(txtOrderID.Text)  
                Return True  
  
            End If  
        End Function  
  
        ' Close the form.  
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click  
            Me.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
|Yorum|Açıklama|  
|-------------|-----------------|  
|FC-1|Ekleme `System.Data.SqlClient`, `System.Configuration`, ve `System.Text.RegularExpressions` ad alanları listesi.|  
|FC-2|Bildirme `parsedOrderID` değişkeni.|  
|FC-3|Çağrı `GetConnectionString` uygulama yapılandırma dosyasından bağlantı dizesini alın ve değeri depolamak için yöntem `connstr` string değişkeni.|  
|FC-4|Tıklama olay işleyicisine kod ekleyin `btnFindOrderByID`.|  
|FC-5|Bu görevler, bir SQL deyimi veya saklı yordam çalıştırmak denemeden önce gereklidir.<br /><br /> -Oluşturma bir `SqlConnection` nesne.<br />-SQL deyimini tanımlayın veya saklı yordamın adını belirtin. (Bu durumda, çalıştırdığınız bir `SELECT` deyimi.)<br />-Oluşturma bir `SqlCommand` nesne.<br />-SQL deyimi veya saklı yordam için tüm parametreleri tanımlayın.|  
|FC-6|Bu kod `SqlDataReader` ve `DataTable` almak ve sorgu sonucu görüntülemek için.<br /><br /> -Bağlantıyı açın.<br />-Oluşturma bir `SqlDataReader` nesnesi `rdr`, çalıştırarak `ExecuteReader` yöntemi `cmdOrderID`.<br />-Oluşturma bir `DataTable` alınan verileri tutacak nesne.<br />-Yük verileri `SqlDataReader` içine nesne `DataTable` nesne.<br />-Veri veri ızgarası görünümünü belirtilmesiyle `DataTable` olarak `DataSource` veri ızgarası görünümü.<br />-Close `SqlDataReader`.|  
|FC-7|Tıklama olay işleyicisine kod ekleyin `btnCancelOrder`. Bu kod çalışır `Sales.uspCancelOrder` saklı yordamı.|  
|FC-8|Tıklama olay işleyicisine kod ekleyin `btnFillOrder`. Bu kod çalışır `Sales.uspFillOrder` saklı yordamı.|  
|FC-9|Doğrulamak için bir yöntem oluşturma `OrderID` bir parametre olarak göndermeye hazır `SqlCommand` nesne.<br /><br /> -Olun kimlik olarak girilen emin `txtOrderID`.<br />-Kullanma `Regex.IsMatch` tamsayı olmayan karakterler için basit bir denetim tanımlamak için.<br />-Bu, bildirilen `parsedOrderID` FC-2 sırasında değişken.<br />-Giriş geçerliyse, metni bir tamsayıya dönüştürün ve değeri depolamak `parsedOrderID` değişkeni.<br />-Wrap `isOrderID` etrafında yöntemi `btnFindByOrderID`, `btnCancelOrder`, ve `btnFillOrder` tıklama olay işleyicileri.|  
  
##  <a name="BKMK_testyourapplication"></a> Uygulamanızı test edin  
 Yapı ve her Click olay işleyicisini kodladıktan sonra uygulamanızı test etmek için F5 tuşunu seçin ve yine kodlamayı bitirdikten sonra sonra.

