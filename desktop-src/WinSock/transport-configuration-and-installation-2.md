---
Description: 'In order for a transport protocol to be accessible through Windows Sockets it must be properly installed on the system and registered with Windows Sockets.'
ms.assetid: '0f0b22e4-81b7-43a7-bc2f-7124fa32d925'
title: Transport Configuration and Installation
---

# Transport Configuration and Installation

In order for a transport protocol to be accessible through Windows Sockets it must be properly installed on the system and registered with Windows Sockets. When a transport service provider is installed by invoking a vendor's installation program, configuration information must be added to a configuration database to give the Ws2\_32.dll required information regarding the service provider. The Ws2\_32.dll exports several installation functions, [**WSCInstallProvider**](wscinstallprovider-2.md) and [**WSCInstallProviderAndChains**](wscinstallproviderandchains.md), for the vendor's installation program to supply the relevant information about the service provider to be installed. This information includes, for example, the name and path to the service provider DLL and a list of [**WSAPROTOCOL\_INFO**](wsaprotocol-info-2.md) structures that this provider can support. The Ws2\_32.dll also provides a function, [**WSCDeinstallProvider**](wscdeinstallprovider-2.md), for a vendor's deinstallation program to remove all the relevant information from the configuration database maintained by the Ws2\_32.dll. The exact location and format of this configuration information is private to the Ws2\_32.dll, and can only be manipulated by the above-mentioned functions.

On 64-bit platforms, there are similar functions that operate on a 32-bit and 64-bit catalogs. These functions include [**WSCInstallProvider64\_32**](wscinstallprovider64-32.md), [**WSCInstallProviderAndChains64\_32**](wscinstallproviderandchains64-32.md), and [**WSCDeinstallProvider32**](wscdeinstallprovider32.md).

The order in which transport service providers are initially installed governs the order in which they are enumerated through [**WSCEnumProtocols**](wscenumprotocols-2.md) and [**WSCEnumProtocols32**](wscenumprotocols32.md) at the service provider interface, or through [**WSAEnumProtocols**](wsaenumprotocols-2.md) at the application interface. More importantly, this order also governs the order in which protocols and service providers are considered when a client requests creation of a socket based on its address family, type, and protocol identifier. Windows Sockets 2 includes an applet called Sporder.exe that allows the catalog of installed protocols to be reordered interactively after protocols have already been installed. Windows Sockets 2 also includes an auxiliary DLL, Sporder.dll, that exports a procedural interface for reordering protocols. This procedural interface consists of a single procedure called [**WSCWriteProviderOrder**](wscwriteproviderorder-2.md).

## Installing Layered Protocols and Protocol Chains

The [**WSAPROTOCOL\_INFO**](wsaprotocol-info-2.md) structure supplied with each protocol to be installed indicates whether the protocol is a base protocol, layered protocol, or protocol chain. The value of the *ProtocolChain.ChainLen* parameter is interpreted as shown in the following table.

| Value | Meaning                                           |
|-------|---------------------------------------------------|
| 0     | Layered protocol.                                 |
| 1     | Base protocol (or chain with only one component). |
| &gt;1 | Protocol chain.                                   |



 

Installation of protocol chains can only occur after successful installation of all of the constituent components (base protocols and layered protocols). The [**WSAPROTOCOL\_INFO**](wsaprotocol-info-2.md) structure for a protocol chain uses the *ProtocolChain* parameter to describe the length of the chain and the identity of each component. The individual protocols that make up a chain are listed in order in the ProtocolChain.ChainEntries array, with the zeroth element of the array corresponding to the first layered provider. Protocols are identified by their *CatalogEntryID* values, which are assigned by the Ws2\_32.dll at protocol installation time, and can be found in the **WSAPROTOCOL\_INFO** structure for each protocol.

The values for the remaining parameters in the protocol chain's [**WSAPROTOCOL\_INFO**](wsaprotocol-info-2.md) structure should be chosen to reflect the attributes and identifiers that best characterize the protocol chain as a whole. When selecting these values, developers should bear in mind that communications over protocol chains can only occur when both endpoints have compatible protocol chains installed, and that applications must be able to recognize the corresponding **WSAPROTOCOL\_INFO** structure.

When a base protocol is installed, it is not necessary to make any entries in the *ProtocolChain.ChainEntries* array. It is implicitly understood that the sole component of this chain is already identified in the *CatalogEntryID* parameter of the same [**WSAPROTOCOL\_INFO**](wsaprotocol-info-2.md) structure. Also note that protocol chains may not include multiple instances of the same layered protocol.

 

 


