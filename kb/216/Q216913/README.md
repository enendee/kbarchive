---
layout: page
title: "Q216913: BIOS Date Value Does Not Immediately Update on January 1, 2000"
permalink: /kb/216/Q216913/
---

## Q216913: BIOS Date Value Does Not Immediately Update on January 1, 2000

{% raw %}

	Article: Q216913
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5
	Operating System(s): 
	Keyword(s): kbYear2000 kbWinNT400sp5fix kbWinNT4sp6fix kbgraphxlinkcriticalkbbuglist kbfixlist
	Last Modified: 21-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4, 4.0 SP5 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	December 29, 1999
	
	Microsoft has determined an incompatibility exists between BIOS3-fix and Kernel-fix. For additional information on Kernel-fix, click the article number below 
	to view the article in the Microsoft Knowledge Base:
	
	  Q234557 Executable with Specially Malformed Image Header Crashes Windows
	
	Because of this incompatibility, if you have installed Kernel-fix, you should uninstall it and then reinstall BIOS3-fix. After applying BIOS3-fix, do not apply Kernel-fix. For additional information on how to remove a Hotfix, click the article number below 
	to view the article in the Microsoft Knowledge Base:
	
	  Q184305 How to Install and Remove Hotfixes with HOTFIX.EXE
	
	SYMPTOMS
	========
	
	Windows NT 4.0 Service Pack 5 addresses the following problem in Windows NT
	4.0:
	
	  When the Windows NT System Time value rolls over from the year 1999 to 2000,
	  the Century Byte value stored in the real time clock (RTC) is not changed
	  until up to one hour later when the time daemon writes out the date. This
	  issue only affects systems with older BIOSes that do not automatically update
	  the century byte on reboot (contact your hardware manufacturer for BIOS
	  details).
	  This issue may cause unexpected behavior under two conditions:
	
	- When your computer is configured using the dual boot option where another
	  operating system may not handle this situation properly. All versions of
	  MS-DOS fall into this category.
	
	- Some computer hardware BIOS configurations detect this behavior as an invalid
	  date and present a query for the correct date. This may prevent a computer
	  from restarting without user input.
	
	  NOTE: This problem only occurs if the computer is restarted during the time
	  lapse when the dates were out of synch.
	
	On August 5, 1999, Microsoft released an updated version of BIOS-fix (BIOS2-fix)
	that was originally included with Windows NT 4.0 Service Pack 5. In addition to
	the above, the latest version of this update corrects the following problems:
	
	  
	
	- If a computer is set to a time zone which does not participate in Daylight
	  Saving Time, refreshing the real time clock for the Year 2000 does not work.
	
	- The original update did not replace the multi-processor kernel if it existed.
	  The updated version does.
	
	On November 3, 1999, Microsoft released an updated version of BIOS-fix (Microsoft
	BIOS3 Y2K Update) that, in addition to fixing the above, fixes the problems
	listed below:
	
	  
	
	- In rare cirumstances where the real time clock is slightly behind the system
	  clock, refreshing the real time clock for the Year 2000 may not work.
	
	- Q241040 Daylight Saving Time Change Not Applied Immediately
	
	RESOLUTION
	==========
	
	Windows NT Server or Workstation 4.0
	------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0
	service pack. For additional information, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	For your convenience, a supported software update that corrects this problem is
	also available from Microsoft, but it has not been fully regression tested and
	should be applied only to systems experiencing this specific problem. If you are
	not severely affected by this specific problem, Microsoft recommends that you
	install the latest Windows NT service pack that contains this software update.
	
	If you are running Windows NT 4.0 Service Pack 6:
	
	The Microsoft BIOS3 Y2K Update is installed as part of Windows NT 4.0 Service
	Pack 6.
	
	If you are running Windows NT 4.0 Service Pack 4 or 5:
	
	The following files are available for download from the Microsoft Download Center
	or Microsoft's FTP site. Click the file names below to download the appropriate
	file:
	
	  x86:
	
	  Microsoft Download Center: DownloadDownload Biosfixi.exe now
	  (http://download.microsoft.com/download/winntsrv40/Update/3/NT4/EN-US/Biosfixi.exe)
	
	  FTP: DownloadDownload Biosfixi.exe now
	  (ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40/hotfixes-postSP5/Y2K/BIOS3-fix/Biosfixi.exe)
	
	  Alpha:
	
	  Microsoft Download Center: DownloadDownload Biosfixa.exe now
	  (http://download.microsoft.com/download/winntsrv40/Update/3/ALPHA/EN-US/Biosfixa.exe)
	
	  FTP: DownloadDownload Biosfixa.exe now
	  (ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40/hotfixes-postSP5/Y2K/BIOS3-fix/Biosfixa.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	Windows NT Server 4.0, Terminal Server Edition
	----------------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	The Terminal Server post-SP4 hotfix is available at:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/nt40tse/hotfixes-postsp4/y2k/bios3-fix/
	
	STATUS
	======
	
	WINDOWS NT 4.0
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. This
	problem was first corrected in Windows NT version 4.0 Service Pack 5.
	
	WINDOWS NT SERVER 4.0, TERMINAL SERVER EDITION
	
	Microsoft has confirmed this to be a problem in Windows NT Server 4.0, Terminal
	Server Edition. This problem was first corrected in Windows NT Server 4.0,
	Terminal Server Edition, Service Pack 5.
	
	Additional query words: y2k tse wts
	
	======================================================================
	Keywords          : kbYear2000 kbWinNT400sp5fix kbWinNT4sp6fix kbgraphxlinkcritical kbbuglist kbfixlist
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTW400sp3 kbWinNTW400sp2 kbWinNTW400sp1 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp5 kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServ400sp4 kbNTTermServSearch
	Version           : winnt:4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
