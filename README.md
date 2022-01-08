# RedTeam Lab User
This script helps to simulate the normale day to day activities of users in computer system.

In RedTeam Lab deployement, it's more realistic to have client machines that generate network traffic and do activities such as opening files, surffing the internet, ect.

**Internet Explorer Browsing -**  Opens the default web browser to a random URL

**Mapping Shares -**  Generates a random share name, and attempts to map it to the "K" drive. Creates LLMNR traffic on the network, allowing capturing network credentials via MitM attacks (Responder).

**Opening Emails -**  Creates and Outlook COM object and iterates through any unread mail of the logged in user. Downloads and executes any attachments, and browses to any embedded links in IE.

The script can be run on a local server, or numerous remote hosts at once. For running on remote hosts, the script includes a configuration function to preconfigure Remote Desktop Users and various

### [](https://github.com/ubeeri/Invoke-UserSimulator#requirements)Requirements:

**Windows -**  The tool should work with any recent versions of Microsoft Windows (tested on Windows 7 through Server 2016). There is heavy use of PowerShell remoting, so when working with Windows 7 machines, some additional configuration will be required.

**Microsoft Office -**  When running the tool with -All or -Email flags, you'll need to have Outlook installed and configured to properly receive mail. Your users will also need to have working email addresses. If you plan on sending Macro phishing payloads, be sure the rest of the Office suite is installed as well.

### [](https://github.com/ubeeri/Invoke-UserSimulator#arguments)Arguments:

-Standalone Define if the script should run as a standalone script on the localhost or on remote systems.

-ConfigXML [filepath] The configuration xml file to use for host configuration and when running on remote hosts.

-ALL Run all script simulation functions (IE, Shares, Email).

-IE Run the Internet Explorer simulation.

-Shares Run the mapping shares simulation.

-Email Run the opening email simulation.

### [](https://github.com/ubeeri/Invoke-UserSimulator#examples)Examples:

Import the script modules:

`PS>Import-Module .\Lab-User.ps1`

Run only the Internet Explorer function on the local host:

`PS>Lab-User -StandAlone -IE`

Configure remote hosts prior to running the script remotely:

`PS>Lab-User-ConfigureHosts -ConfigXML .\config.xml`

Run all simulation functionality on remote hosts configured in the config.xml file:

`PS>Lab-User -ConfigXML .\config.xml -All`

_View the sample.xml file for an example of the file ConfigXML takes_stic
