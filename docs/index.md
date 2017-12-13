# Storebrowse for Receiver for Windows

Storebrowse is a command-line utility tool available with Receiver for Windows that you can use to customize Receiver by scripting the storebrowse utility. This version of Storebrowse utility is supported on Receiver for Windows Version 4.4 CU5, 4.7, 4.9, 4.9 CU1 and 4.10.

Using Storebrowse utility, you can:

* Add a store
* Enumerate the desktops and apps from the configured store
* Launch the published Apps/Desktops from the configured store

**Note:**

* The current version of Storebrowse utility does not support NetScaler Gateway configuration.
* This utility is supported on StoreFront server only.


## Using the Storebrowse utility

Extract the Storebrowse.zip file downloaded from the Citrix downloads website to the desired location. The folder also contains dependent DLLs that are used along with Storebrowse.

Refer to the following table for information about the options that you can use from Storebrowse.

| Option | Description | Notes |
|---|---|---|
| `-a` | Adds new store. Execute the following command: <br> `storebrowse.exe –U <username> -P <password> -D <domain> -a <URL of Storefront>`
 | Returns the full URL of the store. If this fails, an error is reported. <br> **Note**: You can add multiple stores using the Storebrowse utility.<br> **Example**: `storebrowse.exe –U user123 –P password123 –D TestDomain –a https://my.secondexamplestore.net/Citrix/Store/discovery` |
| `-E`, `--enumerate` | Enumerates the available resources. Execute the following command:  <br> `storebrowse.exe –M 0X2000 –E or --enumerate <URL of Storefront>` | By default, the resource name, display name, and folder of the resource are displayed. Use the --details option to display additional information. <br> **Note**: The argument **-M 0X2000** is required to get the launch URL for each of the resource that are published in the Storefront <br> **Example**: `storebrowse.exe –M 0X2000 –E https://my.secondexamplestore.net/Citrix/Second/discovery` |
| `–q`, `--quicklaunch` | Specifies the name of the published resource to which you want to connect. Saves the required ICA file in the local folder where Storebrowse is running. Execute the following command: <br> `storebrowse.exe –quicklaunch <URL Of the Resource> <URL of the Storefront>` | **Note**: Executing the following command will save the ICA file in the local machine where the Storebrowse is running. The file will be saved under `%localAppData%\Citrix\storebrowse\cache` folder. <br> `Storebrowse.exe –quicklaunch <URL of the Resource> <URL of the Storefront>` <br> **Example**: `storebrowse.exe –q https://mysecondexamplestore.net/Citrix/Second/v2/v3jkjjlj9u0i0-/launch/ica  https://mysecondexamplestore.net/Citrix/Second/discovery` |
| `-d`, `--deletestore` | Unregisters a store with the Service Record daemon. Execute the following command: <br> `storebrowse.exe –d or –deletestore  <URL of Storefront>` | **Example**:  `storebrowse.exe –d http://store-url.xxx.com/Citrix/SF-Name/discovery` |

## Limitations

1. The username and password are case-sensitive and must be in upper case only.





