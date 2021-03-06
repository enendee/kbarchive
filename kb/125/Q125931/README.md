---
layout: page
title: "Q125931: SMS Server Selection Using Appstart"
permalink: /kb/125/Q125931/
---

## Q125931: SMS Server Selection Using Appstart

{% raw %}

	Article: Q125931
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbDatabase smsdatabase
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	You can run shared applications from Systems Management Server version 1.0 by
	using the Appstart program to select an appropriate application server. There
	are three ways Appstart locates a server (in order):
	
	- Existing Share
	
	- Existing Server
	
	- Random
	
	Existing Share
	--------------
	
	If an existing connection to a needed share exists, Appstart piggy-backs or
	reuses the existing share connection. Appstart assumes that a previous attempt
	to connect was made, and, during that attempt, these same rules were followed.
	This is done to maximize load balancing on the initial connection, and minimize
	the total number of distinct connections a client makes.
	
	Existing Server
	---------------
	
	If there is already a session established with the server providing the desired
	share and a connection to the share does not already exist, Appstart connects to
	this server and share. Quite often a local connection will exist to the SMS
	Windows NT logon server (and SMS_SHR) that authenticated the logon. For this
	reason, the majority of Appstart requests will go to a Windows NT (or LAN
	Manager) domain controller local to the client computer.
	
	Random
	------
	
	If no shares or servers are connected that have the desired resources, Appstart
	will randomly pick from the list in the network accounts database (NAD).
	
	Random selection is rarely performed after either the existing share or server
	methods have been used. They are oriented to the local subnet, while the random
	method acts as a safety net. The random selection will most likely be made on
	the local subnet, but it cannot be guaranteed in SMS version 1.0. That is why
	the existing share and server methods are attempted first. To ensure a local
	connection, you can add a NET USE command to a local distribution server in the
	logon script. Then you guarantee a session because Appstart will always check
	for an existing server before choosing randomly.
	
	
	Additional query words: sms prodsms
	
	======================================================================
	Keywords          : kbnetwork kbDatabase smsdatabase 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	
	=============================================================================
	

{% endraw %}
