# Storebrowse for Workspace app for Windows

Storebrowse is a lightweight command-line utility that is used to interact between the client and the server. It is used to authenticate all the operations within StoreFront and with NetScaler Gateway.

Using Storebrowse utility, administrators can automate the following day-to-day operations:

* Add a store
* Enumerate the published desktops and applications from a configured store
* Generate an ICA file by selecting any published desktop or application manually
* Generate an ICA file using the Storebrowse command-line
* Launch the published application 

The Storebrowse utility is now part of Authmanager component. After installing the Citrix Workspace, the Storebrowse utility is located in the AuthManager installation folder.

You can confirm if Storebrowse is installed along with the Authmanager component by checking the registry path in the following ways

## When Workspace is installed by administrators

**For 32 bit machine**

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Citrix\AuthManager\Install]
```

**For 64 bit machine**

```
[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Citrix\AuthManager\Install] 
```

When Workspace is installed by end-users:

**For 32 bit machine**

```
[HKEY_CURRENT_USER\SOFTWARE\Citrix\AuthManager\Install]
```

**For 64 bit machine**

```
[HKEY_CURRENT_USER\SOFTWARE\WOW6432Node\Citrix\AuthManager\Install]
```

## What’s New

### NetScaler Gateway Support

With the latest release of Storebrowse utility, you can now add a NetScaler Gateway URL. No additional configuration is required in the Storebrowse utility to communicate with NetScaler Gateway.  

### Single Sign-on Support with NetScaler Gateway:

Additional to the newly added NetScaler Gateway support, you can now use Single Sign-on with it. You can add a new store and enumerate the published resources without having to provide your user credentials.

**Note**: This feature is supported only on domain-joined machines where NetScaler Gateway is configured with the Single Sign-on authentication.

### Launch Published desktop/application 

You can now launch a resource directly from the store without having to use an ICA file.

### System Requirements

Install the Citrix Workspace app Version 18.8 for Storebrowse utility to work seamlessly between StoreFront and NetScaler Gateway.
Citrix Workspace app Version 18.8 requires a minimum of 530MB of free disk space and 2GB RAM to be installed.

## Compatibility Matrix

Storebrowse utility is compatible with the following Operating systems:

<table style="width:60%">
  <tr>
    <th>Operating System</th>
  </tr>
  <tr>
    <td> Windows 10 32-bit and 64-bit editions </td>
    </tr>
    <tr>
    <td> Windows 8.1, 32-bit and 64-bit editions </td>
    </tr>
    <tr>
    <td> Windows 7 SP1, 32-bit and 64-bit editions </td>
    </tr>
    <td>Windows Thin PC </td>
    </tr>
    <tr>
    <td>Windows Server 2016 </td>
    </tr>
    <tr>
    <td> Windows Server 2012 R2, Standard, and, Datacenter editions </td>
    </tr>
    <tr>
    <td>Windows Server 2012, Standard, and, Datacenter editions</td>
    </tr>
    <tr>
    <td>Windows Server 2008 R2, 64-bit edition</td>
    </tr>
    <tr>
    <td>Windows 10 Enterprise 2016 LTSB 1607</td>
    </tr>
</table>

## Connections

Storebrowse utility supports following type of connections:

* HTTP store
* HTTPS store
* NetScaler Gateway 11.0 and later

Note: Storebrowse does not accept credentials using command-line on an HTTP store.

## Authentication methods supported by Storebrowse utility

### StoreFront servers

StoreFront supports different authentication methods to access stores, however, not all are recommended. For security purposes, some of the authentication methods are disabled by default while creating a store.

* **Username and Password**: Users can enter their credentials and are authenticated when they access their stores. Explicit authentication is enabled by default when you create your first store. All user access methods support explicit authentication.
* **Domain Pass-through**: Users authenticate to their domain-joined Windows computers and are automatically logged on when they access their stores. In order to use this option, pass-through authentication must be enabled when Citrix Workspace app is installed on the user devices. For more information on configuring domain pass-through, see [Configuring Pass-through authentication](https://docs.citrix.com/en-us/receiver/windows/current-release/authentication/config-pass-through.html). 
* **HTTP Basic**: StoreBrowse application require HTTP Basic authentication to be enabled to communicate with StoreFront servers. This option is disabled by default on storefront server. You would need to enable HTTP Basic authentication method.

### Storebrowse

Storebrowse supports authentication methods in any of the following methods:

* Using the AuthManager that is in-built along with Storebrowse. 
Note: You must enable HTTP Basic authentication method on the StoreFront while working with Storebrowse utility. This would mean, when user provides credentials along with the StoreBrowse commands.
* External Authmanager which comes along with Citrix Workspace app is invoked which prompts to user to enter the credentials.