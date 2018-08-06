# Known Limitations with Current StoreBrowse Utility

* HTTP Basic Authentication method has to be enabled on the StoreFront server for credential injection operations that you do with StoreBrowse utility.
* If you have HTTP store, and when you try connecting to the store using the utility for enumerating Apps/Desktops or Launch the published Apps/Desktops, then the credential injection via command line option is unsupported. As a workaround, you can use the external AuthManager module which gets triggered when you do not provide credential via command line
* StoreBrowse currently support NetScaler Gateway configured with only single store configured on the StoreFront server.
* Credential Injection in StoreBrowse will work only if NetScaler Gateway is configured with Single Factor Authentication.
* The command line options Username (`-U`), Password (`-P`) and Domain (`-D`) of the Storebrowse utility are case-sensitive and must be in upper case only.