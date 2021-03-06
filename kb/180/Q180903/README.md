---
layout: page
title: "Q180903: PRB: LCK Functions Do Not Work in a Private Data Session"
permalink: /kb/180/Q180903/
---

## Q180903: PRB: LCK Functions Do Not Work in a Private Data Session

{% raw %}

	Article: Q180903
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp500 kbvfp600
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An ActiveX control (.ocx) has been written in Visual C++ that also makes use of
	the Visual FoxPro Library Construction Kit (LCK) functions. The control may work
	properly on forms that use the default DataSession but the control fails when
	the form uses a private DataSession.
	
	CAUSE
	=====
	
	Library Construction Kit function calls do not occur in the DataSession context
	of the form that made the call to the .ocx. There is only one global context in
	which the Library Construction Kit function can call into Visual FoxPro, no
	matter where the call originated.
	
	RESOLUTION
	==========
	
	If a private DataSession is necessary, write the ActiveX control completely in
	Visual C++ or Visual Basic and expose properties and methods that can be
	accessed by Visual FoxPro.
	
	If it is absolutely necessary to use some of the Visual FoxPro LCK functions in
	an .ocx that will access tables in a private DataSession, it may be possible to
	get the .ocx to work by making the private DataSession the active DataSession by
	using the SET DATASESSION TO <nDataSessionNumber> command. However, this
	approach is not recommended. Writing the functionality into the control with
	another language is a better solution.
	
	STATUS
	======
	
	This behavior is by design.
	
	
	MORE INFORMATION
	================
	
	FoxPro and Visual FoxPro have included the Library Construction Kit for many
	versions. The Library Construction Kit functions allow developers to write
	libraries in C that can be loaded by FoxPro or Visual FoxPro to extend its
	functionality by accessing the FoxPro API. Starting with Visual FoxPro version
	5.0, the Developer's Guide has included information to help developers get a
	start on creating ActiveX controls to access the Visual FoxPro API. ActiveX
	controls can make use of the LCK functions if used within the global context of
	Visual FoxPro.
	
	Library Construction Kit functions that access tables that may be open in private
	DataSessions, such as _DBRead and the other _DBxxxx functions, _Load, _FindMemo
	and _FindVar, are some of the functions to avoid in ActiveX controls that need
	to work in private DataSessions. However, depending on what the ActiveX control
	does and how it does it, other LCK functions may also fail in private
	DataSessions. A good test is to try the control in the default DataSession. If
	it works there and not a private DataSession, this article probably applies.
	
	REFERENCES
	==========
	
	Microsoft Visual FoxPro "Developer's Guide," version 5.0, pages 645-647.
	
	Examples.dbf located in the \API\Samples folder of Visual FoxPro.
	
	Microsoft Visual FoxPro Help: Library Construction Kit.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
