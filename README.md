# fetchTest
Fetch Rewards Server Test

The project contains a web server that accepts a HTTP POST request containing a body with a list of email
addresses, one address per line.  The server responds with a number that represents the number of unique addresses 
in the list taking into account that the name field (before the @) must ignore multiple '.' characters and must ignore
characters after a '+'. 

Environment:
This is designed to run on Windows that has Cygwin tools (providing unix commands) installed, and has python installed
(I used Anaconda).

To Run:
Pull the project to a windows machine with the given environment. 
Make sure the script files have execute permissions.
Run this command from a powershell command window:
.\pyserver.ps1
which starts the server.  The powershell script permissions should be in bypass, or you can just run the command from a command line.
From a windows cmd window or cygwin terminal window, run
.\client.bat
This creates the POST request and takes the email data from emailfile.
The response should be "5" as the unique email addresses.

Description:
The windows curl command is used to formulate a POST with the body coming from emailfile.
emailfile has the test cases with some having . and + characters causing some to be non-unique.
The python server executes a windows batch cgi file in cgi-bin.  This references cygwin unix like commands
using full paths to avoid PATH problems. I'm assuming the cygwin installation is in the standard place, otherwise 
change the paths to suit.

Assumptions:
There may be multiple "." in the email names and all must be ignored.
There is an assumption that removing "." from the domains will not cause domains to look non-unique.
It seems unlikely that this could happen, but if that assumption is weak, then more thought needs to go into the stream editing.

