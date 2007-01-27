make gvim(WIN32) + cscope(Cygwin) work together

Description:

Actually this isn't a script, but a small application. If you are in the same situation as me cswrapper may help.
1. I'm using gvim Win32 version. It works perfectly in my Windows XP.
2. I tried cscope Win32 version, but it always returns 0 lines for any request.
3. I compiled a cscope(ver 15.6) in Cygwin. It works well in its own command window. But gvim freezes when creating a connection to my cscope with 'cs add cscope.out'.
I guess the reason is cscope doesn't flush its output, it causes gvim to hang up when reading from the pipe. Instead of hacking into cscope's source code, I created this wrapper. It acts as a cscope command window, reads requests from gvim, gets the result by executing cscope, then passes the result to gvim. It works well for me till now.
CSWrapper isn't a full function cscope. It only accesses the parameter '-f /path/cscope.out' and acts as a wrapper between gvim and cscope. Please use the original cscope.exe to create databases.

Install:

1. Put this program in the same directory as your cscope.exe.
2. Put this line in your _gvimrc, you may need to add the full path:
set csprg=cswrapper.exe

It should work now. If it doesn't work, run 'cswrapper -f /path/cscope.out' in a command window, then try typing a command, for example '0main', to see what happens.

