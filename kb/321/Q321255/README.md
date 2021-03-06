---
layout: page
title: "Q321255: FIX: ODBC Driver for SQL Server Incorrectly Returns SQL_SUCCESS"
permalink: /kb/321/Q321255/
---

## Q321255: FIX: ODBC Driver for SQL Server Incorrectly Returns SQL_SUCCESS

{% raw %}

	Article: Q321255
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 2.6,2.7,2000.80.194,2000.80.380,2000.81.7713.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC Driver for SQL Server 2000, versions 2000.80.194, 2000.80.380, 2000.81.7713.0, used with:
	   - Microsoft Data Access Components versions 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Microsoft SQL Server driver that is included with Microsoft
	Data Access Components (MDAC) version 2.6 or 2.7, if you call the
	SQLDescribeParam function on a connection that is busy with results for another
	statement handle, SQL_SUCCESS is returned instead of SQL_ERROR.
	
	This problem does not occur with the SQL Server driver that is included with MDAC
	version 2.5.
	
	CAUSE
	=====
	
	This problem occurs because the return code is not set to SQL_ERROR, even though
	you receive the following error message:
	
	  [Microsoft][ODBC SQL Server Driver]Connection is busy with results for
	  another hstmt
	
	RESOLUTION
	==========
	
	MDAC 2.7
	--------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Data Access Components 2.7
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix has the file attributes (or later) that are
	listed in the following table. The dates and times for these files are listed in
	coordinated universal time (UTC). When you view the file information, it is
	converted to local time. To find the difference between UTC and local time, use
	the Time Zone tab in the Date and Time tool in Control Panel.
	
	  Date         Version         Size           File Name
	  -----------------------------------------------------
	  19-Apr-2002  2000.81.8508.0  356,352 bytes  Sqlsrv32.dll
	  19-Apr-2002  2000.81.8508.0   90,112 bytes  Sqlsrv32.rll  
	  19-Apr-2002  2000.81.8508.0   24,576 bytes  Odbcbcp.dll 
	
	
	
	MDAC 2.6
	--------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Data Access Components 2.6
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix has the file attributes (or later) that are
	listed in the following table. The dates and times for these files are listed in
	coordinated universal time (UTC). When you view the file information, it is
	converted to local time. To find the difference between UTC and local time, use
	the Time Zone tab in the Date and Time tool in Control Panel.
	
	  Date         Version        Size           File Name
	  -----------------------------------------------------
	  26-Apr-2002  2000.80.617.0  475,217 bytes  Sqlsrv32.dll
	  26-Apr-2002  2000.80.617.0   90,112 bytes  Sqlsrv32.rll  
	  26-Apr-2002  2000.80.617.0   29,252 bytes  Odbcbcp.dll 
	
	
	
	
	WORKAROUND
	----------
	
	To work around this problem, use one of the following methods:
	
	- Open a server-side cursor instead of a forward-only, read-only result set to
	  avoid the "Connection is busy with results for another hstmt" error message.
	
	- Create a separate connection to execute each query to prevent this error from
	  occurring.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Start the ODBC Test utility that is included with the MDAC Software
	  Development Kit (SDK).
	
	2. On the Conn menu, click Full Connect.
	
	3. Select a data source name (DSN) to connect to your server that is running SQL
	  Server, type the correct User ID and Password, and then click OK.
	
	4. On the Stmt menu, click SQLExecDirect. Add the following query to the Stmt
	  box, and then click OK:
	
	  select * from authors
	
	5. On the Env menu, click SQLAllocHandle. Under HandleType, click
	  SQL_HANDLE_STMT=3(3.0), and then click OK.
	
	6. On the Stmt menu, click SQLPrepare. Add the following query to the Stmt box,
	  and then click OK:
	
	  select * from authors where au_lname like ?
	
	7. On the Stmt menu, click SQLDescribeParam, and then click OK. Notice that
	  SQL_SUCCESS is returned instead of SQL_ERROR.
	
	Additional query words: connection busy SQL driver 2.6/2.7
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSQLServ2000Search kbODBCSearch
	Version           : :2.6,2.7,2000.80.194,2000.80.380,2000.81.7713.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
