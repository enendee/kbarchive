---
layout: page
title: "Q178666: BUG: Form Not Released When Focus on Grid and Modal Form Started"
permalink: /kb/178/Q178666/
---

## Q178666: BUG: Form Not Released When Focus on Grid and Modal Form Started

{% raw %}

	Article: Q178666
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b;WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbcode kbHWMAC kbvfp kbvfp300BUG kbvfp500bug kbvfp600bug
	Last Modified: 12-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A form, on which a grid has focus, remains visible after the form has been
	programmatically released and a modal form has been instantiated. The form
	containing the grid remains visible until the modal form has been released.
	
	RESOLUTION
	==========
	
	Set the visible property of the form containing the grid to False (.f.) before
	releasing the form, using the following code:
	
	     PROCEDURE closescreens
	     IF _SCREEN.FORMCOUNT > 0
	     FOR i = _SCREEN.FormCount TO 1 STEP -1
	     _SCREEN.FORMS(i).VISIBLE=.F.
	     _SCREEN.FORMS(i).RELEASE
	     ENDFOR
	     ENDIF
	     RETURN
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	This behavior is not observed when a form, containing a grid object, is
	programmatically released under the following conditions:
	
	- A grid object does not have focus.
	
	- The WindowType property of the form being instantiated, after release of the
	  form containing the grid, is set to 0 - Modeless.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form called gridfrm and place a grid object on the form.
	
	2. Create a second form called modalfrm and set its WindowType property to 1 -
	  Modal.
	
	3. Add the following code to the forms Click event:
	
	        =endjob()
	
	4. Create a program file named Norelease.prg using the following code:
	
	        CLEAR
	        SET SYSMENU TO
	        SET SYSMENU AUTOMATIC
	        DEFINE PAD modal_frm OF _MSYSMENU PROMPT "\<Modal Form" COLOR
	        SCHEME 3 ;
	        KEY ALT+M, ""
	        DEFINE PAD exit_prg OF _MSYSMENU PROMPT "E\<xit" COLOR SCHEME 3 ;
	        KEY ALT+X, ""
	        ON SELECTION PAD modal_frm OF _MSYSMENU =runmodal()
	        ON SELECTION PAD exit_prg OF _MSYSMENU =endjob()
	        USE home()+"SAMPLES\DATA\CUSTOMER"
	        DO FORM gridfrm
	        READ EVENTS
	        SET SYSMENU TO DEFAULT
	        RETURN
	
	        PROCEDURE closescreens
	        IF _SCREEN.FORMCOUNT > 0
	        FOR i = _SCREEN.FORMCOUNT TO 1 STEP -1
	        _SCREEN.FORMS(i).RELEASE
	        ENDFOR
	        ENDIF
	        RETURN
	
	        PROCEDURE runmodal
	        =closescreens()
	        DO FORM modalfrm
	        RETURN
	
	        PROCEDURE endjob
	        =closescreens()
	        CLEAR EVENTS
	        RETURN
	
	5. Run Norelease.prg.
	
	6. Click the Modal Form menu item.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbHWMAC kbvfp kbvfp300BUG kbvfp500bug kbvfp600bug 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : MACINTOSH:3.0b;WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
