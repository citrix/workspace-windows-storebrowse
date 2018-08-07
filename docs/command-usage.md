# Storebrowse command usage

Extract the Storebrowse.zip file downloaded from the Citrix downloads website to the desired location. The folder also contains dependent DLLs that are used along with Storebrowse.

Refer to the following section for information about the options that you can use from Storebrowse.

## `-a`, `--addstore`

**Description**

Adds new store. Returns the full URL of the store. If this fails, an error is reported. 

**Note**: You can add multiple stores using the Storebrowse utility.

**Command Example on StoreFront**

```
storebrowse.exe –U <username> -P <password> -D <domain> -a <URL of Storefront>
```
```
.\storebrowse.exe –U {Username} –P {Password} –D {Domain} –a https://my.firstexamplestore.net
```

**Command Example on NetScaler Gateway**

```
storebrowse.exe –U <username> -P <password> -D <domain> -a <URL of NetScalerGateway>
```
```
.\storebrowse.exe –U {Username} –P {Password} –D {Domain} –a <https://mysecondexample.com>
```

## `/?`

**Description**

Provides details on Storebrowse usage

## `(-l)`, `--liststore` 

**Description**

Lists the stores that are added by the user.

**Command Example on StoreFront**

```
.\storebrowse.exe –l
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe –l
```

## `(-M 0x2000 -E)`

**Description**

Enumerates the available resources
**Command Example on StoreFront**

```
.\storebrowse.exe –U {Username} –P {Password} –D {Domain} –M 0x2000 –E <https://my.firstexamplestore.net/Citrix/Store/discovery>
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe –U {Username} –P {Password} –D {Domain} –M 0x2000 –E <https://my.secondexample.net>
```

## `-q`, `--quicklaunch`

**Description**

Generates the required ICA file for published apps and desktops using the Storebrowse utility. The quicklaunch option requires a launch URL as an input along with the Store URL, which can either be the StoreFront server or NetScaler Gateway URL. The ICA file is generated in the `“%LocalAppData%\Citrix\Storebrowse\cache”` directory. You can get the launch URL for any published apps and desktops by executing the following command: 

```
.\storebrowse –M 0X2000 –E https://myfirstexamplestore.net/Citrix/Second/discovery
```

A typical launch URL looks like below: 
```
'Controller.Calculator'  'Calculator'    '\' ''  http://abc-sf.xyz.com/Citrix/Stress/resources/v2/Q29udHJvbGxlci5DYWxjdWxhdG9y/launch/ica
```
**Command Example on StoreFront**

```
.\storebrowse.exe  –U {Username} –P {Password}–D {Domain} –q {Launch_URL_of_published_ apps and desktops }<https://my.firstexamplestore.net/Citrix/Store/resources/v2/Q2hJkOlmNoPQrSTV9y/launch/ica> <https://my.firstexamplestore.net/Citrix/Store/discovery>
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe  –U {Username} –P {Password} –D {Domain} –q {Launch_URL_of_published_ apps and desktops} <https://my.secondexmaplestore.com>
```


## `-L`, `--launch` 


**Description**

Generates the required ICA file for published apps and desktops using the Storebrowse utility. The launch option requires the name of the resource along with the Store URL, which can either be the StoreFront server or NetScaler Gateway URL. The ICA file is generated in the `“%LocalAppData%\Citrix\Storebrowse\cache”` directory. You can get the display name of the published apps and desktops by executing the command below:

```
.\storebrowse –M 0X2000 –E https://myfirstexamplestore.net/Citrix/Second/discovery
```

This command results in the following output: 

```
'Controller.Calculator'  'Calculator'    '\' ''  http://abc-sf.xyz.com/Citrix/Stress/resources/v2/Q29udHJvbGxlci5DYWxjdWxhdG9y/launch/ica
```

The name that is in **bold** in the above output is used as input parameter to the launch option. 

**Command Example on StoreFront**

```
.\storebrowse.exe  -U {Username} –P {Password} –D {Domain} –L “{Resource_Name} <https://my.firstexamplestore.net/Citrix/Store/discovery>
```
**Command Example on NetScaler Gateway**

```
<.\storebrowse.exe  –U {Username} –P {Password} –D {Domain} –L {Resource_Name} https://my.secondexamplestore.com>
```

## `-S`, `--sessionlaunch`

**Description**

You can add the store, enumerate the published resources (apps and desktops) and launch the resource with the single command. This option takes the following as parameters -  Username, Password, Domain, Friendly name of the resource to be launched and the store URL. However, if the user does not provide the credentials , AuthManager prompt is thrown to enter the credentials and then the resource launch will happen. 

You can get the name of the resource of published apps and desktops by executing the command below: 

```
.\storebrowse –M 0X2000 –E https://myfirstexamplestore.net/Citrix/Second/discovery
```

This command results in the following output:

```
'Controller.Calculator'  'Calculator'    '\' ''  http://abc-sf.xyz.com/Citrix/Stress/resources/v2/Q29udHJvbGxlci5DYWxjdWxhdG9y/launch/ica
```

The name that is in **bold** in the above output will be used as input parameter to the `-S` option. 

**Command Example on StoreFront**

```
.\storebrowse.exe  -U {Username} –P {Password} –D {Domain} –S “{Friendly_Resource_Name} <https://my.firstexamplestore.net/Citrix/Store/discovery >
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe  –U {Username} –P {Password} –D {Domain} –S {Friendly_Resource_Name} <https://my.secondexamplestore.com>
```

## `-f`, `--filefolder`

**Description**

Generates the required ICA file in the custom path as defined in the `–f` option for any of the published apps and desktops using the Storebrowse utility. 

The launch option requires a folder name along with name of the resource as the input with Store URL, which is either StoreFront server or NetScaler Gateway URL.

**Command Example on StoreFront**

```
`.\storebrowse.exe  –f “C:\Temp\Launch.ica” –L “Resource_Name” {Store}
```

**Command Example on NetScaler Gateway**

```
.\storebrowse.exe  –f “C:\Temp\Launch.ica” –L “Resource_Name” {NSG_URL}
```

## `-t`, `--traceauthentication`

**Description**

Generate logs for Storebrowse in-built AuthManager component. Logs are generated only if Storebrowse is using an in-built AuthManager. Logs are generated in the `%localappdata%\Citrix\Storebrowse\logs` directory.

**Note**: This option cannot be the last parameter for user’s command line.

**Command Example on StoreFront**

```
.\storebrowse.exe –t –U {UserName} –P {Password} –D {Domain} –a {StoreURL}
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe –t –U {UserName} –P {Password} –D {Domain} –a {NSG_URL}
```

## `-d`, `--deletestore`

**Description**

Deletes existing StoreFront or NetScaler Gateway store.

**Command Example on StoreFront**

```
.\storebrowse.exe –d https://my.firstexamplestore.net/Citrix/Store/discovery
```
**Command Example on NetScaler Gateway**

```
.\storebrowse.exe –d https://my.secondexmaplestore.com
```