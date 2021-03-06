---
description: by using VS Code
---

# Connect to Database installed on Windows computer

{% hint style="info" %}
_To see how to connect to Database from VS Code within Windows_ 👉 [_Connect to Database locally page_](../../databases/sql/sql-server/connect-to-database-locally.md)\_\_
{% endhint %}

{% hint style="warning" %}
_**Prerequisites:**_ 

1. _Remote connection between Linux and Windows machine has to be established_
2. _VS Code has to be installed on Linux machine with:_
   1. \_\_[_SQL Server \(mssql\) extension_](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) _or_
   2. \_\_[_SQLTools - Database tools extension_](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools) __
{% endhint %}

## Steps:

### 1. Setting up Database engine on Windows for a remote connection

* Open SSMS and _**connect**_ to Database engine
* Under Object Explorer right click on the Database engine name &gt; _**Properties**_
* Under _**Security page**_ make sure for Server authentication that _**"SQL Server and Windows Authentication mode" is checked**_

![](../../.gitbook/assets/image%20%287%29%20%281%29.png)

* Under Connections page **check** _"Allow remote connection to this server"_ **checkbox** and click **OK**

![](../../.gitbook/assets/image%20%288%29.png)

* Under Object Explorer navigate to _**Security &gt; Logins**_
  * right click on targeted _**Login &gt; Properties**_
* Under _**User mapping page**_:
  * for _Users mapped to this login_ section, check _**desired Database**_
  * for _Database role membership for: master_ section, check:
    * _db\_datareader_
    * _db\_datawriter_
    * _**db\_owner**_

![](../../.gitbook/assets/image%20%281%29.png)

* Click OK.
* Now open **SQL Server Configuration Manager** from Start menu
* Navigate to _**SQL Server Network Configuration &gt; Protocols for SQLEXPRESS**_
  * right click on _**TCP/IP &gt; Enable**_
  * right click on _**TCP/IP &gt; Properties**_
    * _**IP Addresses**_ tab &gt; **IPAII**
      * leave _TCP Dynamic Port_ **empty**
      * set **TCP Port** to _**1433**_
  * _**Click OK**_

![](../../.gitbook/assets/image%20%283%29.png)

* Navigate to ****_**SQL Server Services**_ 
  * _**select SQL Server \(SQLEXPRESS\) &gt; click Restart** from the toolbar_

![](../../.gitbook/assets/image%20%286%29.png)

### 2. Setting up Windows for a remote connection

{% hint style="info" %}
Until setup has been found to authorize Linux machine to have access through Windows firewall, _**for now turn off Windows firewall**_ to be able to establish connection.
{% endhint %}

### 3. Connect from Linux by using VS Code

* Open up VS Code and navigate to _**SQL Server \(mssql\) extension**_ from the side menu
* Click on  **`+`** to _**add a connection**_
* Paste ADO.NET _**connection string**_ as:

**`SERVER=`**_`win-ip-address`_**`,1433;DATABASE=`**_`database-name`_**`;UID=`**_`login-name`_**`;PWD=`**_`your-password`_**`;`**

![](../../.gitbook/assets/image%20%285%29.png)

* On the left side menu under _**CONNECTIONS section**_ there should be added server connection
* Click on it to get connected and run a query against your database.

![](../../.gitbook/assets/image%20%284%29.png)

 

