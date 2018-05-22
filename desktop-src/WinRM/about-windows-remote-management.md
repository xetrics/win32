---
title: About Windows Remote Management
description: Windows Remote Management is one component of the Windows Hardware Management features that manage server hardware locally and remotely.
audience: developer
author: REDMOND\\markl
manager: REDMOND\\markl
ms.assetid: 'f58add53-0746-4423-9ab8-02ba05f82fa7'
ms.prod: 'windows-server-dev'
ms.technology: 'windows-remote-management'
ms.tgt_platform: multiple
keywords: ["About Windows Remote Management", "Windows Remote Management, about"]
---

# About Windows Remote Management

Windows Remote Management is one component of the [Windows Hardware Management](http://go.microsoft.com/fwlink/p/?linkid=45204) features that manage server hardware locally and remotely. These features include a service that implements the [*WS-Management*](windows-remote-management-glossary.md#winrm-gloss-ws-management) protocol, hardware diagnosis and control through baseboard management controllers ([*BMCs*](windows-remote-management-glossary.md#winrm-gloss-bmc)), and a COM API and [scripting objects](winrm-scripting-api.md) that allow you to write applications that communicate remotely through the WS-Management protocol. For more information about the public specification for WS-Management protocol, see [Web Services for Management (WS–Management)](http://go.microsoft.com/fwlink/p/?linkid=73965).

## Components of WinRM and Hardware Management

The following is a list of components and features that are supplied by WinRM and hardware monitoring:

-   [WinRM Scripting API](winrm-scripting-api.md)

    This scripting API enables you to obtain data from remote computers using scripts that perform WS-Management protocol operations.

-   **Winrm.cmd**

    This command–line tool for system management is implemented in a Visual Basic Scripting Edition file (Winrm.vbs) written using the WinRM scripting API. This tool enables an administrator to configure WinRM and to get data or manage resources. For more information, see the online help provided by the command line **Winrm** **/?**.

-   **Winrs.exe**

    This command line tool enables administrators to remotely execute most Cmd.exe commands using the WS-Management protocol. For more information, see the online help provided by the command line **Winrs** **/?**.

-   Intelligent Platform Management Interface (IPMI) driver and WMI provider

    Hardware management through the [*Intelligent Platform Management Interface (IPMI)*](windows-remote-management-glossary.md#winrm-gloss-intelligent-platform-management-interface) provider and driver enables you to control and diagnose remote server hardware through BMCs when the operating system is not running or deployed.

    For more information, see the [IPMI Provider](https://msdn.microsoft.com/library/aa391402).

-   WMI service

    The WMI service continues to run side-by-side with WinRM and provides requested data or control through the [*WMI plug-in*](windows-remote-management-glossary.md#winrm-gloss-wmi-plug-in). You can continue to obtain data from standard WMI classes, such as [**Win32\_Process**](https://msdn.microsoft.com/library/aa394372), as well as IPMI-supplied data. For more information about configuration and installation required for WinRM, see [Hardware Management Introduction](http://go.microsoft.com/fwlink/p/?linkid=45204).

-   WS-Management protocol

    WS-Management protocol, a SOAP-based, firewall-friendly protocol, was designed for systems to locate and exchange management information. The intent of the WS-Management protocol specification is to provide interoperability and consistency for enterprise systems that have computers running on a variety of operating systems from different vendors.

    WS-Management protocol is based on the following standard web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing. For more information about the current draft of the specification, see the [Management Specifications Index Page](http://go.microsoft.com/fwlink/p/?linkid=96658).

## Working with WinRM

For more information about writing WinRM scripts, see [Using Windows Remote Management](using-windows-remote-management.md).

The following table lists topics that provide information about the WS-Management protocol, WinRM and WMI, how to specify management resources such as disk drives or processes.



| Topic                                                                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                   |
|----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Installation and Configuration for Windows Remote Management](installation-and-configuration-for-windows-remote-management.md) | The WinRM [*listener*](windows-remote-management-glossary.md#winrm-gloss-listener) requires configuration on both client and server computers.                                                                                                                                                                                                                               |
| [Windows Remote Management Architecture](windows-remote-management-architecture.md)                                             | Diagram that illustrates the components of WinRM and which components are found on client and server computers.                                                                                                                                                                                                                                                               |
| [WS-Management Protocol](ws-management-protocol.md)                                                                             | Description of the public standard WS-Management protocol for remotely sending and receiving management data to any computer device that implements the protocol.                                                                                                                                                                                                             |
| [Scripting in Windows Remote Management](scripting-in-windows-remote-management.md)                                             | The WinRM scripting API is similar to the actions of the WS-Management protocol. Data retrieved by scripts is formatted in XML, not objects.                                                                                                                                                                                                                                  |
| [Authentication for Remote Connections](authentication-for-remote-connections.md)                                               | WS-Management protocol maintains security for data transfer between computers by supporting several standard methods of authentication and message encryption.                                                                                                                                                                                                                |
| [Windows Remote Management and WMI](windows-remote-management-and-wmi.md)                                                       | Because WinRM is integrated with [Windows Management Instrumentation (WMI)](https://msdn.microsoft.com/library/aa394582), you can obtain WMI data with scripts or applications that use the [WinRM Scripting API](winrm-scripting-api.md) or through the Winrm command-line tool.                                                                                                                     |
| [Resource URIs](resource-uris.md)                                                                                               | A [*resource URI*](windows-remote-management-glossary.md#winrm-gloss-resource-uri) is an identifier for a management operation or value. For example, disk drives represent a type of resource.                                                                                                                                                                              |
| [Remote Hardware Management](remote-hardware-management.md)                                                                     | The [IPMI provider](https://msdn.microsoft.com/library/aa391402) supplies [classes](https://msdn.microsoft.com/library/aa391402) and data that describe the baseboard management controller (BMC) hardware management domain, the BMC computer systems in the domain, and the BMC sensors. Other objects represent the BMC System Event Log (SEL) and the messages in the log. |
| [Events](events.md)                                                                                                             | You cannot obtain events through WinRM scripting, but you can use the Wevtutil.exe command-line tool to view [Event Collector](http://go.microsoft.com/fwlink/p/?linkid=84396) events.                                                                                                                                                                                        |



 

 

 



