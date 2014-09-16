#chrome_remote_shell
===================

##Client for the Google Chrome browser's remote debugging shell.

New update replaces old api code with new - no longer compatibile with 3+ year 
old chrome, now compatible with Chrome Remote Debugging Protocol


  See <https://developer.chrome.com/devtools/docs/debugger-protocol> for details on 
  Chrome's remote debugging protocol.

This library makes it easier to communicate with the Google Chrome remote
debugging api from Python.  To enable the debugging api port, start Chrome
with this option::

    google-chrome --remote-shell-port=9222
  
  
Note that Chromecast devices also open a remote debugging port and speak
this same api, on 1) devices in development mode, and 2) which are currently
running a dev app.  

Then you can connect from Python through code like this:

#fixme new example api call
    >>> import chrome_remote_shell
    >>> shell = chrome_remote_shell.open(port=9222)
    >>> shell.request('DevToolsService', command='ping')
    {u'data': u'ok', u'command': u'ping', u'result': 0}

The protocol is composed of json messages described on the site above.

As a convenience, the shell connection object offers a method that, by
injecting JavaScript into the first tab, commands Chrome to open a URL
in a new tab::

    shell.open_url('http://www.aldaily.com/')

CHANGELOG
---------
*2014 Sept 15.* Updated to work with modern Chrome Remote Debugging protocol

*2014 Sept 15.* Package maintaince (HOPEFULLY, #FIXME) transitioned to Fred Clift

*2014 Sept 15.* Package migrated to GitHub.

*2009 Feb 26.* Added a conditional import of `simplejson` so that the
module runs under Python 2.5.

