---
layout: page
title: "Q129600: Large Zeroing Operations Cause Systems To Appear Hung"
permalink: /kb/129/Q129600/
---

## Q129600: Large Zeroing Operations Cause Systems To Appear Hung

{% raw %}

	Article: Q129600
	Product(s): Microsoft Windows NT
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.5 
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Large zeroing operations on Windows NT file system (NTFS) formatted drives may
	cause Windows NT to appear to hung. The hang only affects the physical drive on
	which the zeroing operation occurs. The length of the hang depend on how much
	space has to be cleared and the speed of the system.
	
	For example, if you have a 100 MB file, and an application writes one byte at
	offset 200 MB. Windows NT initializes the disk space between 100 MB to 200 MB.
	This ensures that the space is actually available on the disk. In addition, the
	space is erased so that old erased data is secure. The zeroing operation occurs
	synchronously so that any attempt to access this disk will be queued up until
	this action is complete.
	
	NOTE: This information applies only to NTFS drives.
	
	
	CAUSE
	=====
	
	The zeroing operations are being submitted synchronously.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.5. This
	problem has been corrected in the latest U.S. Service Pack for Windows NT
	version 3.5. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt wfw wfwg
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	
	=============================================================================
	

{% endraw %}
